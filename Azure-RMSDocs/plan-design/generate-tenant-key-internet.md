---
title: "인터넷을 통해 테넌트 키 생성 및 전송 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1bff9b06-8c5a-4b1d-9962-6668219210e6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7a9c8b531ec342e7d5daf0cbcacd6597a79e6a55
ms.openlocfilehash: 20cfa722f7008c52f4fbc219a4de04c50ee3548d


---


# 인터넷을 통해 테넌트 키 생성 및 전송

*적용 대상: Azure 권한 관리, Office 365*

[고유한 테넌트 키를 관리](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok-)하기로 결정했으며 직접 테넌트 키를 전송하기 위해 Microsoft 본사로 가지 않고 인터넷을 통해 테넌트 키를 전송하려는 경우 다음 절차를 사용하세요.


## 인터넷에 연결된 워크스테이션 준비
인터넷에 연결된 워크스테이션을 준비하려면 다음 3단계를 수행하세요.

-   [1단계: Azure Rights Management용 Windows PowerShell 설치](#step-1-install-windows-powershell-for-azure-rights-management)

-   [2단계: Azure Active Directory 테넌트 ID 얻기](#step-2-get-your-azure-active-directory-tenant-id)

-   [3단계: BYOK 도구 집합 다운로드](#step-3-download-the-byok-toolset)

### 1단계: Azure Rights Management용 Windows PowerShell 설치
인터넷에 연결된 워크스테이션에서 Azure Rights Management용 Windows PowerShell 모듈을 다운로드 및 설치합니다.

> [!NOTE]
> 이전에 이 Windows PowerShell 모듈을 다운로드한 경우 다음 명령을 실행하여 버전 번호가 2.1.0.0인지 확인하세요. `(Get-Module aadrm -ListAvailable).Version`

설치 지침은 [Azure 권한 관리용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

### 2단계: Azure Active Directory 테넌트 ID 얻기
**관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작한 후 다음 명령을 실행합니다.

-   [Connect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629415.aspx) cmdlet을 사용하여 Azure RMS 서비스에 연결합니다.

    ```
    Connect-AadrmService
    ```
    메시지가 표시되면 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 테넌트 관리자 자격 증명을 입력합니다(일반적으로 Azure Active Directory 또는 Office 365에 대한 전역 관리자 계정 사용).

-   [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet을 사용하여 테넌트 구성을 표시합니다.

    ```
    Get-AadrmConfiguration
    ```
    출력의 첫 번째 줄(BPOSId)에서 GUID를 저장합니다. 이것이 Azure Active Directory 테넌트 ID이며, 이 ID는 나중에 업로드를 위해 테넌트 키를 준비할 때 필요합니다.

-   [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet을 사용하여 키를 업로드할 준비가 될 때까지 Azure RMS 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

Windows PowerShell 창을 닫지 마세요.

### 3단계: BYOK 도구 집합 다운로드
Microsoft 다운로드 센터로 이동하여 해당 지역의 [BYOK 도구 집합을 다운로드](http://go.microsoft.com/fwlink/?LinkId=335781) 합니다.

|지역|패키지 이름|
|----------|----------------|
|북아메리카|AzureRMS-BYOK-tools-UnitedStates.zip|
|Europe|AzureRMS-BYOK-tools-Europe.zip|
|아시아|AzureRMS-BYOK-tools-AsiaPacific.zip|
이 도구 집합에는 다음이 포함되어 있습니다.

-   이름이 **BYOK-KEK-pkg-**로 시작하는 KEK(키 교환 키) 패키지

-   이름이 **BYOK-SecurityWorld-pkg-**로 시작하는 보안 권역 패키지

-   이름이 **verifykeypackage.py**인 Python 스크립트

-   이름이 **KeyTransferRemote.exe**인 명령줄 실행 파일, 이름이 **KeyTransferRemote.exe.config**인 메타데이터 파일 및 연결된 DDL

-   이름이 **vcredist_x64.exe**인 Visual C++ 재배포 가능 패키지

패키지를 USB 드라이브 또는 기타 휴대용 저장소에 복사합니다.

## 연결이 끊어진 워크스테이션 준비
네트워크(인터넷 또는 내부 네트워크)에 연결되지 않은 워크스테이션을 준비하려면 다음 2단계를 수행하세요.

-   [1단계: Thales HSM을 사용하여 연결이 끊어진 워크스테이션 준비](#step-1-prepare-the-disconnected-workstation-with-thales-hsm)

-   [2단계: 연결이 끊어진 워크스테이션에 BYOK 도구 집합 설치](#step-2-install-the-byok-toolset-on-the-disconnected-workstation)

### 1단계: Thales HSM을 사용하여 연결이 끊어진 워크스테이션 준비
연결이 끊어진 워크스테이션에서 Windows 컴퓨터에 nCipher(Thales) 지원 소프트웨어를 설치한 후 해당 컴퓨터에 Thales HSM을 연결합니다.

Thales 도구가 경로(**%nfast_home%\bin** 및 **%nfast_home%\python\bin**)에 있는지 확인합니다. 예를 들어 다음과 같이 입력합니다.

```
set PATH=%PATH%;”%nfast_home%\bin”;”%nfast_home%\python\bin”
```
자세한 내용은 Thales HSM에 포함되어 있는 사용자 가이드를 참조하거나, Azure RMS용 Thales 웹 사이트( [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud))를 방문하여 확인하세요.

### 2단계: 연결이 끊어진 워크스테이션에 BYOK 도구 집합 설치
USB 드라이브 또는 기타 휴대용 저장소에서 BYOK 도구 집합 패키지를 복사한 후 다음을 수행합니다.

1.  다운로드한 패키지에서 임의 폴더로 파일을 추출합니다.

2.  해당 폴더에서 vcredist_x64.exe를 실행합니다.

3.  지침에 따라 Visual Studio 2012용 Visual C++ 런타임 구성 요소를 설치합니다.

## 테넌트 키 생성
연결이 끊어진 워크스테이션에서 다음 3단계를 수행하여 고유 테넌트 키를 생성합니다.

-   [1단계: 보안 권역 만들기](#step-1-create-a-security-world)

-   [2단계: 다운로드한 패키지 유효성 검사](#step-2-validate-the-downloaded-package)

-   [3단계: 새 키 생성](#step-3-create-a-new-key)

### 1단계: 보안 권역 만들기
명령 프롬프트를 시작하고 Thales new-world 프로그램을 실행합니다.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
이 프로그램은 %NFAST_KMDATA%\local\world(C:\ProgramData\nCipher\Key Management Data\local 폴더에 해당)에 **보안 권역** 파일을 만듭니다. 쿼럼에 다른 값을 사용할 수 있지만 이 예에서는 각각에 대해 3개의 빈 카드와 핀을 입력하라는 메시지가 나타납니다. 어떤 카드이든 두 카드에는 보안 권역(지정된 쿼럼)에 대한 관리자 권한이 있어야 합니다.  이러한 카드는 새 보안 권역의 **관리자 카드 집합** 이 됩니다. 이 단계에서 각 ACS 카드에 대한 암호 또는 PIN을 지정하거나 명령을 사용하여 나중에 추가할 수 있습니다.

> [!TIP]
> `nkminfo` 명령을 사용하여 HSM의 현재 구성 상태를 확인할 수 있습니다.

그리고 다음을 수행합니다.

1.  Thales 문서에 설명된 대로 Thales CNG 공급자를 설치하고 새 보안 권역을 사용하도록 구성합니다.

2.  **%nfast_kmdata%\local**에서 권역 파일을 백업합니다. 권역 파일, 관리자 카드 및 해당 핀을 보호하고 둘 이상의 카드에 대한 액세스 권한을 가지는 사용자가 없도록 합니다.

### 2단계: 다운로드한 패키지 유효성 검사
이 단계는 선택 사항이지만 다음의 유효성을 검사할 수 있도록 수행하는 것이 좋습니다.

-   도구 집합에 포함된 키 교환 키가 정품 Thales HSM에서 생성되었습니다.

-   도구 집합에 포함된 Azure RMS 보안 권역의 해시가 정품 Thales HSM에서 생성되었습니다.

-   키 교환 키를 내보낼 수 없습니다.

> [!NOTE]
> 다운로드한 패키지의 유효성을 검사하려면 HSM이 연결되어 있고 전원이 켜져 있으며 보안 권역을 포함하고 있어야 합니다(방금 만든 보안 권역처럼).

#### 다운로드한 패키지의 유효성을 검사하려면

1.  해당 지역에 따라 다음 중 하나를 입력하여 verifykeypackage.py 스크립트를 실행합니다.

    -   북아메리카의 경우:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-NA-1 -w BYOK-SecurityWorld-pkg-NA-1
        ```

    -   유럽의 경우:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-EU-1 -w BYOK-SecurityWorld-pkg-EU-1
        ```

    -   아시아의 경우:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-AP-1 -w BYOK-SecurityWorld-pkg-AP-1
        ```

    > [!TIP]
    > Thales 소프트웨어는 %NFAST_HOME%\python\bin에 Python 인터프리터를 포함하고 있습니다.

2.  다음이 표시되는지 확인합니다(유효성 검사 성공을 나타냄). **결과:  SUCCESS**

이 스크립트는 서명자가 Thales 루트 키까지 체이닝되는지를 확인합니다. 이 루트 키의 해시는 스크립트에 포함되어 있으며 해당 값은 **59178a47 de508c3f 291277ee 184f46c4 f1d9c639**여야 합니다. [Thales 웹 사이트](http://www.thalesesec.com/)를 방문하여 별도로 이 값을 확인할 수도 있습니다.

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
cngimport --import -M --key=contosokey --appname=simple contosokey
```
이 명령을 실행할 때 다음 지침을 사용하세요.

-   *contosokey*를 *테넌트 키 생성* 섹션의 [1단계: 보안 권역 만들기](#step-1-create-a-security-world)에서 지정한 값과 동일한 값으로 바꿉니다.

-   키가 이 시나리오에 적합하도록 **-M** 옵션을 사용합니다. 이 옵션을 사용하지 않으면 결과 키가 현재 사용자의 사용자별 키가 됩니다.

-   **appname** 옵션은 키 파일에 보고된 앱 이름입니다. 이러한 지침에 따라 새 키를 만든 경우 명령에 표시된 것처럼 간단한 값을 사용했습니다. 그러나 AD RMS-Azure RMS 마이그레이션을 위해 기존 HSM 보호된 키를 마이그레이션하는 경우 이 명령과 뒤에 나오는 명령(appname 옵션을 사용하는 경우)에 기존 이름을 지정합니다.

이 명령을 실행하면 %NFAST_KMDATA%\local 폴더에 이름이 **key_caping`_`**으로 시작하고 뒤에 SID가 붙은 토큰화된 키 파일이 생성됩니다. 예: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. 이 파일에는 암호화된 키가 들어 있습니다.

> [!TIP]
> `nkminfo –k` 명령을 사용하여 키의 현재 구성 상태를 확인할 수 있습니다.

이 토큰화된 키 파일을 안전한 위치에 백업합니다.

> [!IMPORTANT]
> 나중에 키를 Azure RMS로 전송할 때 Microsoft는 이 키를 다시 사용자에게 내보낼 수 없으므로 키와 보안 권역을 안전하게 백업하는 것이 매우 중요합니다. 키 백업에 대한 지침과 모범 사례는 Thales에 문의하세요.

이제 테넌트 키를 Azure RMS로 전송할 준비가 되었습니다.

## 테넌트 키 전송 준비
연결이 끊어진 워크스테이션에서 다음 4단계를 수행하여 고유 테넌트 키를 준비합니다.

-   [1단계: 권한이 낮춰진 키 복사본 만들기](#step-1-create-a-copy-of-your-key-with-reduced-permissions)

-   [2단계: 키의 새 복사본 검사](#step-2-inspect-the-new-copy-of-the-key)

-   [3단계: Microsoft 키 교환 키를 사용하여 키 암호화](#step-3-encrypt-your-key-by-using-microsoft-s-key-exchange-key)

-   [4단계: 인터넷에 연결된 워크스테이션에 키 전송 패키지 복사](#step-4-copy-your-key-transfer-package-to-the-internet-connected-workstation)

### 1단계: 권한이 낮춰진 키 복사본 만들기
테넌트 키에 대한 권한을 낮추려면 다음을 수행합니다.

-   명령 프롬프트에서 해당 지역에 따라 다음 중 하나를 실행합니다.

    -   북아메리카의 경우:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1
        ```

    -   유럽의 경우:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1
        ```

    -   아시아의 경우:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1
        ```

이 명령을 실행할 때 *contosokey*를 *테넌트 키 생성* 섹션의 [1단계: 보안 권역 만들기](#step-1-create-a-security-world)에서 지정한 값과 동일한 값으로 바꿉니다.

보안 권역 ACS 카드를 연결하고, 지정된 경우 암호 또는 PIN을 요청하는 메시지가 표시됩니다.

명령이 완료되면 **Result: SUCCESS**가 표시되고 권한이 낮춰진 테넌트 키의 복사본이 key_xferacId_*&lt;contosokey&gt;*라는 파일에 포함됩니다.

### 2단계: 키의 새 복사본 검사
선택적으로, Thales 유틸리티를 실행하여 새 테넌트 키에 대한 최소 권한을 확인합니다.

-   aclprint.py:

    ```
    "%nfast_home%\bin\preload.exe" -m 1 -A xferacld -K contosokey "%nfast_home%\python\bin\python" "%nfast_home%\python\examples\aclprint.py"
    ```

-   kmfile-dump.exe:

    ```
    "%nfast_home%\bin\kmfile-dump.exe" "%NFAST_KMDATA%\local\key_xferacld_contosokey"
    ```

이 명령을 실행할 때 *contosokey*를 *테넌트 키 생성* 섹션의 [1단계: 보안 권역 만들기](#step-1-create-a-security-world)에서 지정한 값과 동일한 값으로 바꿉니다.

### 3단계: Microsoft 키 교환 키를 사용하여 키 암호화
해당 지역에 따라 다음 명령 중 하나를 실행합니다.

-   북아메리카의 경우:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   유럽의 경우:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   아시아의 경우:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

이 명령을 실행할 때 다음 지침을 사용하세요.

-   *contosokey*를 *테넌트 키 생성* 섹션의 [1단계: 보안 권역 만들기](#step-1-create-a-security-world)에서 키를 생성하는 데 사용한 식별자로 바꿉니다.

-   *GUID*를 *인터넷에 연결된 워크스테이션 준비* 섹션의 [2단계: Azure Active Directory 테넌트 ID 얻기](#step-2-get-your-azure-active-directory-tenant-id)에서 검색한 Azure Active Directory 테넌트 ID로 바꿉니다.

-   *ContosoFirstKey* 를 출력 파일 이름에 사용할 레이블로 바꿉니다.

이 작업이 성공적으로 완료되면 **Result: SUCCESS**가 표시되고 현재 폴더에 TransferPackage-*ContosoFirstkey*.byok라는 이름을 가진 새 파일이 포함됩니다.

### 4단계: 인터넷에 연결된 워크스테이션에 키 전송 패키지 복사
USB 드라이브 또는 기타 휴대용 저장소를 사용하여 이전 단계의 출력 파일(KeyTransferPackage-*ContosoFirstkey*.byok)을 인터넷에 연결된 워크스테이션에 복사합니다.

> [!NOTE]
> 이 파일은 사용자의 개인 키를 포함하기 때문에 보안 방법을 사용해서 보호해야 합니다.

## Azure RMS로 테넌트 키 전송
인터넷에 연결된 워크스테이션에서 다음 3단계를 수행하여 새 테넌트 키를 Azure RMS로 전송합니다.

-   [1단계: Azure RMS에 연결](#step-1-connect-to-azure-rms)

-   [2단계: 키 패키지 업로드](#step-2-upload-the-key-package)

-   [3단계: 테넌트 키 열거(필요한 경우)](#step-3-enumerate-your-tenant-keys-as-needed)

### 1단계: Azure RMS에 연결
Windows PowerShell 창으로 돌아가 다음과 같이 입력합니다.

1.  [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 서비스에 다시 연결합니다.

    ```
    Connect-AadrmService
    ```

2.  [Get-AadrmKeys](http://msdn.microsoft.com/library/windowsazure/dn629420.aspx) cmdlet을 사용하여 현재 테넌트 키 구성을 확인합니다.

    ```
    Get-AadrmKeys
    ```

### 2단계: 키 패키지 업로드
[Add-AadrmKey](http://msdn.microsoft.com/library/windowsazure/dn629418.aspx) cmdlet을 사용하여 연결이 끊어진 워크스테이션에서 복사한 키 전송 패키지를 업로드합니다.

```
Add-AadrmKey –KeyFile <PathToPackageFile> -Verbose
```
> [!WARNING]
> 이 작업을 확인하는 메시지가 나타납니다. 이 작업은 실행 취소할 수 없음을 이해하는 것이 중요합니다. 테넌트 키를 업로드하면 이 키가 자동으로 조직의 기본 테넌트 키가 되고 사용자가 문서와 파일을 보호할 때 이 테넌트 키를 사용하기 시작합니다.

업로드에 성공하면 다음과 같은 메시지가 표시됩니다. **Rights Management 서비스에서 키를 추가했습니다.**

변경 내용이 모든 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 데이터 센터로 전파될 때까지 복제 지연이 발생합니다.

### 3단계: 테넌트 키 열거(필요한 경우)
테넌트 키의 변경 내용을 확인하거나 테넌트 키 목록을 확인하고 싶을 때마다 Get-AadrmKeys cmdlet을 다시 사용합니다. 표시되는 테넌트 키에는 Microsoft가 고객을 위해 생성한 초기 테넌트 키와 추가된 모든 테넌트 키가 포함됩니다.

```
Get-AadrmKeys
```
**활성** 으로 표시된 테넌트 키는 조직에서 현재 문서와 파일을 보호하는 데 사용 중인 테넌트 키입니다.

이제 인터넷을 통한 BYOK(Bring Your Own Key)에 필요한 모든 단계를 완료했으므로 테넌트 키 계획 및 구현의 다음 단계로 이동할 수 있습니다.


> [!div class="button"]
[다음 단계 >>](plan-implement-tenant-key.md#next-steps)





<!--HONumber=Jun16_HO4-->


