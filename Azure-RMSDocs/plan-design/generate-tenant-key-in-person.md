---
# required metadata

title: 직접 테넌트 키 생성 및 전송 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3281e45e-cf69-4dc5-946b-3029851d3152

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 직접 테넌트 키 생성 및 전송

*적용 대상: Azure 권한 관리, Office 365*


[고유한 테넌트 키를 관리](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok-)하기로 결정했으며 인터넷을 통해 테넌트 키를 전송하지 않고 직접 테넌트 키를 전송하려는 경우 다음 절차를 사용하세요.

## 테넌트 키 생성
테넌트 키를 생성하려면 다음 3단계를 수행합니다.

-   [1단계: Thales HSM을 사용하여 워크스테이션 준비](#step-1-prepare-a-workstation-with-thales-hsm)

-   [2단계: 보안 권역 만들기](#step-2-create-a-security-world)

-   [3단계: 새 키 생성](#step-3-create-a-new-key)

### 1단계: Thales HSM을 사용하여 워크스테이션 준비
Windows 컴퓨터에 nCipher(Thales) 지원 소프트웨어를 설치합니다. 해당 컴퓨터에 Thales HSM을 연결합니다. Thales 도구가 경로에 있는지 확인합니다. 자세한 내용은 Thales HSM에 포함되어 있는 사용자 가이드를 참조하거나, Azure RMS용 Thales 웹 사이트( [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud))를 방문하여 확인하세요..

### 2단계: 보안 권역 만들기
명령 프롬프트를 시작하고 Thales new-world 프로그램을 실행합니다.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
이 프로그램은 %NFAST_KMDATA%\local\world(C:\ProgramData\nCipher\Key Management Data\local 폴더에 해당)에 **보안 권역** 파일을 만듭니다. 쿼럼에 다른 값을 사용할 수 있지만 이 예에서는 각각에 대해 3개의 빈 카드와 핀을 입력하라는 메시지가 나타납니다. 그러면 임의의 두 카드는 보안 권역에 대한 모든 권한을 제공합니다.  이러한 카드는 새 보안 권역의 **관리자 카드 집합** 이 됩니다.

그리고 다음을 수행합니다.

1.  Thales 문서에 설명된 대로 Thales CNG 공급자를 설치하고 새 보안 권역을 사용하도록 구성합니다.

2.  권역 파일을 백업합니다. 권역 파일, 관리자 카드 및 해당 핀을 보호하고 둘 이상의 카드에 대한 액세스 권한을 가지는 사용자가 없도록 합니다.

이제 RMS 테넌트 키가 될 새 키를 만들 준비가 되었습니다.

### 3단계: 새 키 생성
Thales **generatekey** 및 **cngimport** 프로그램을 사용하여 CNG 키를 생성합니다.

다음 명령을 실행하여 키를 생성합니다.

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
이 명령을 실행할 때 다음 지침을 사용하세요.

-   표시된 대로 **protect** 매개 변수를 **module** 값으로 설정해야 합니다. 이렇게 하면 모듈 보호된 키가 생성됩니다. BYOK 도구 집합은 OCS 보호된 키를 지원하지 않습니다.

-   키 크기의 경우 2048을 사용하는 것이 좋지만, 1024비트 RSA 키를 가지고 있고 Azure RMS로 마이그레이션하려는 기존 AD RMS 고객을 위해 1024비트 RSA 키도 지원됩니다.

-   *ident* 및 **plainname** 의 **contosokey** 값을 임의의 문자열 값으로 바꿉니다. 관리 오버헤드를 최소화하고 오류 발생 위험을 줄이기 위해 ident와 plainname에 동일한 값을 사용하고 모두 소문자를 사용하는 것이 좋습니다.

-   이 예에서는 pubexp를 비워 뒀지만(기본값) 특정 값을 지정할 수 있습니다. 자세한 내용은 Thales 문서를 참조하세요.

그리고 나서 다음 명령을 실행하여 키를 CNG로 가져옵니다.

```
cngimport --import –M --key=contosokey --appname=simple contosokey
```
이 명령을 실행할 때 다음 지침을 사용하세요.

-   *contosokey* 를 1단계에서 지정한 값과 동일한 값으로 바꿉니다.

-   키가 이 시나리오에 적합하도록 **-M** 옵션을 사용합니다. 이 옵션을 사용하지 않으면 결과 키가 현재 사용자의 사용자별 키가 됩니다.

이 명령을 실행하면 %NFAST_KMDATA%\local 폴더에 이름이 **key_caping`_`**으로 시작하고 뒤에 SID가 붙은 토큰화된 키 파일이 생성됩니다. 예: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. 이 파일에는 암호화된 키가 들어 있습니다.

이 토큰화된 키 파일을 안전한 위치에 백업합니다.

> [!IMPORTANT]
> 나중에 키를 Azure RMS로 전송할 때 Microsoft는 키의 복구할 수 없는 복사본을 가지게 됩니다. 즉, Microsoft HSM에서 아무도 고객의 키를 검색할 수 없습니다. 따라서 고객은 테넌트 키에 대한 독점적인 제어권을 유지할 수 있습니다. 그러므로 키와 보안 권역을 안전하게 백업하는 것이 매우 중요합니다. 키 백업에 대한 지침과 모범 사례는 Thales에 문의하세요.

이제 테넌트 키를 Azure RMS로 전송할 준비가 되었습니다.

## Azure RMS로 테넌트 키 전송
키를 생성하고 나서는 키를 사용하기 전에 Azure RMS로 전송해야 합니다. 최고 수준의 보안을 위해 이 전송은 고객이 직접 미국 워싱턴주의 Redmond에 있는 Microsoft 본사로 가야 하는 수동 프로세스입니다. 이 프로세스를 완료하려면 다음 단계를 수행합니다.

-   [1단계: Microsoft로 키 가져오기](#step-1-bring-your-key-to-microsoft)

-   [2단계: Azure RMS 보안 권역으로 키 전송](#step-2-transfer-your-key-to-the-azure-rms-security-world)

-   [3단계: 절차 끝내기](#step-3-closing-procedures)

### 1단계: Microsoft로 키 가져오기

-   Microsoft CSS(고객 지원 서비스)에 문의하여 Azure RMS의 키 전송 약속을 예약합니다. Redmond의 Microsoft 본사로 다음을 가져옵니다.

    -   관리자 카드의 쿼럼. [2단계: 보안 권역 만들기](#step-2-create-a-security-world)의 이전 지침을 따랐다면 이는 세 카드 중 임의의 두 카드에 해당합니다.

    -   관리자 카드와 핀(일반적으로 2개, 카드당 하나)을 가져올 책임자

    -   USB 드라이브에 저장된 보안 권역 파일(%NFAST_KMDATA%\local\world)

    -   USB 드라이브에 저장된 토큰화된 키 파일

### 2단계: Azure RMS 보안 권역으로 키 전송

1.  키를 전송하기 위해 Microsoft 본사에 도착하면 다음과 같은 상황이 발생합니다.

    -   Microsoft가 Thales HSM이 연결되어 있고, Thales 소프트웨어가 설치되어 있으며, C:\Temp\Destination 폴더에 Azure RMS 보안 권역 파일이 미리 로드되어 있는 오프라인 워크스테이션을 제공합니다.

    -   이 워크스테이션에서 USB 드라이브에 저장되어 있는 보안 권역 파일 및 토큰화된 키 파일을 C:\Temp\Source 폴더에 로드합니다.

    -   Azure RMS 운영자가 Thales 유틸리티를 사용하여 키를 Azure RMS 보안 권역으로 안전하게 전송합니다.

    이 프로세스는 다음과 유사합니다. 여기서 이 예의 key-xfer-im 마지막 매개 변수는 토큰화된 키 파일 이름으로 바뀝니다.

    **C:\&gt; mk-reprogram.exe --owner c:\Temp\Destination add c:\Temp\Source**

    **C:\&gt; key-xfer-im.exe c:\Temp\Source c:\Temp\Destination --module c:\Temp\Source\key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**

2.  Mk-reprogram이 고객과 Azure RMS 운영자에게 각각 관리자 카드와 핀을 연결하라는 메시지를 표시합니다. 이러한 명령은 Azure RMS 보안 권역에서 보호되는 키를 포함하는 C:\Temp\Destination에 토큰화된 키 파일을 출력합니다.

### 3단계: 절차 끝내기

-   고객이 있는 상태에서 Azure RMS 운영자가 다음을 수행합니다.

    -   Microsoft가 Thales와 협력하여 개발한 두 가지 권한(키를 복구하는 권한과 권한을 변경하는 권한) 제거 도구를 실행합니다. 이 도구를 실행하고 나면 키의 이 복사본이 Azure RMS 보안 권역으로 잠깁니다. Thales HSM에서는 Azure RMS 운영자가 관리자 카드를 사용하여 키의 일반 텍스트 복사본을 복구하는 것을 허용하지 않습니다.

    -   나중에 Azure RMS 서비스에 업로드할 결과 키 파일을 USB 드라이브에 복사합니다.

    -   HSM을 공장 기본 설정으로 복원하고 워크스테이션을 깨끗하게 지웁니다.

이제 고유한 키를 직접 가져오는 데 필요한 지침을 완료했으므로 테넌트 키 계획 및 구현의 다음 단계를 위해 조직으로 돌아갈 수 있습니다.

> [!div class="button"]
[다음 단계 >>](plan-implement-tenant-key.md#next-steps)





<!--HONumber=Apr16_HO4-->


