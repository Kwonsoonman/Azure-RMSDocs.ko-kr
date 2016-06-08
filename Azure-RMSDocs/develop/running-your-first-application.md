---
# required metadata

title: 권한 사용 응용 프로그램 테스트 | Azure RMS
description: RMS SDK 2.1 권한 사용 응용 프로그램을 테스트하기 위해 완료해야 하는 단계를 설명합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 834B7242-31D3-4275-A892-CFE95A61E29E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** 이 SDK 콘텐츠는 현재 버전이 아닙니다. 잠시 MSDN에서 [현재 버전](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx)의 설명서를 확인해 주세요. **
# 권한 사용 응용 프로그램 테스트

이 항목에서는 권한 관리 서비스 SDK 2.1 권한 사용 응용 프로그램을 테스트하기 위해 완료해야 하는 단계를 설명합니다.

보호된 콘텐츠를 게시 및 사용하기 위해 RMS(권한 관리 서비스) 응용 프로그램은 각각 궁극적으로 Microsoft 인증 기관으로 연결되는 인증서 체인으로 구성된 여러 가지 유형의 인증서와 라이선스를 이용합니다. Microsoft는 다음과 같은 계층 구조를 제공합니다.

-   사전 프로덕션 계층 구조는 응용 프로그램 개발 및 테스트에 사용할 수 있습니다.
-   프로덕션 계층 구조는 릴리스된 응용 프로그램에서 사용해야 합니다.

응용 프로그램을 개발할 때는 사전 프로덕션 계층 구조를 사용하는 것이 좋습니다. 이렇게 하면 Microsoft와 프로덕션 사용권 계약에 서명하지 않고도 작업할 수 있습니다.

> [!IMPORTANT]
> 먼저 RMS 사전 프로덕션 환경에서 RMS 서버에 대해 RMS SDK 2.1 응용 프로그램을 테스트하는 것이 좋습니다. 그런 다음 고객이 Azure RMS 서비스와 함께 응용 프로그램을 사용할 수 있게 하려는 경우 해당 환경에서 테스트합니다. 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

 

### 필수 구성 요소

-   RMS SDK 2.1 개발 환경 설정. 자세한 내용은 [사전 프로덕션 개발 환경 설정](how-to-set-up-the-pre-production-development-environment.md)을 참조하세요.
-   예제 응용 프로그램은 [IPCHelloWorld - 예제 응용 프로그램](how-to-build-your-first-application.md)을 참조하세요.

지침

### 1단계:

권한 사용 응용 프로그램 만들기 및 빌드. 옵션은 위의 필수 조건 섹션을 참조하세요.

### 2단계: 사전 프로덕션 인증서 체인을 사용하여 응용 프로그램 매니페스트 생성

실행하기 전에 응용 프로그램에 대한 매니페스트를 생성해야 합니다.

**참고** 응용 프로그램에서 서버 API 모드(**IPC\_API\_MODE\_SERVER**)를 사용하는 경우에는 응용 프로그램 매니페스트를 사용할 필요가 없습니다. 프로덕션 AD RMS 서버에서 응용 프로그램을 테스트할 수 있으며, 프로덕션 환경으로 전환할 때 프로덕션 라이선스를 얻지 않아도 됩니다. 서버 모드 응용 프로그램에 대한 자세한 내용은 [응용 프로그램 종류](application-types.md)를 참조하세요.

 

이 프로세스를 응용 프로그램 서명이라고도 합니다. 프로덕션 인증서 체인 또는 SDK와 함께 설치된 사전 프로덕션 인증서 체인을 사용하여 매니페스트를 생성할 수 있습니다. 개발 중에는 사전 프로덕션 인증서 체인을 사용하는 것이 좋습니다.

키 및 인증서 체인에 대한 자세한 내용은 [인증서 체인 이해](understanding-certificate-chains.md)를 참조하세요.

프로덕션 인증서 체인을 사용하여 응용 프로그램에 서명하는 방법에 대한 자세한 내용은 [프로덕션 환경으로 전환](switching-to-the-production-environment.md)을 참조하세요.

사전 프로덕션 인증서 체인을 사용하여 응용 프로그램 매니페스트를 생성하려면 개발 컴퓨터에 다음 단계를 수행합니다.

1.  설치 디렉터리에 있는 다음 파일을 응용 프로그램과 동일한 폴더에 복사합니다.

    %MSIPCSdkDir%\\Tools\\Genmanifest.exe

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningprivkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningpubkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsignsdk\_client.xml

    %MSIPCSdkDir%\\bin\\YourAppName.isv.mcf

2.  응용 프로그램 폴더에서 매니페스트 구성 파일 YourAppName.isv.mcf의 이름을 .mcf 파일 이름 확장명이 추가된 사용자 응용 프로그램의 이름으로 바꿉니다. 예를 들어 사용자 응용 프로그램의 이름이 MyApp.exe이면 YourAppName.isv.mcf의 이름을 MyApp.exe.mcf로 바꿉니다.

3.  텍스트 편집기를 사용하여 매니페스트 구성 파일에 응용 프로그램을 추가합니다. 이렇게 하려면 .mcf 파일 내에 있는 모듈 목록의 &lt;YourAppName&gt;.exe 개체 틀 텍스트를 사용자 응용 프로그램의 이름(예: MyApp.exe)으로 바꿉니다.

    .mcf 파일을 수정하지 않고 사용하면 서명 프로세스에서 오류가 생성됩니다.

4.  Genmanifest.exe를 실행하여 응용 프로그램 매니페스트를 생성합니다. 이를 응용 프로그램 서명이라고도 합니다. 이 작업의 출력은 .man 파일이어야 합니다. 예를 들어 사용자 응용 프로그램의 이름이 MyApp.exe이고 매니페스트 구성 파일의 이름이 MyApp.exe.mcf이면 다음 명령을 실행합니다.

    **genmanifest.exe -chain isvtier5appsignsdk\_client.xml MyApp.exe.mcf MyApp.exe.man**

### 3단계: 응용 프로그램 실행

아무 디렉터리에서나 응용 프로그램을 실행할 수 있지만 응용 프로그램 매니페스트(MyApp.exe.man)는 실행 파일(MyApp.exe)과 동일한 디렉터리에 있어야 합니다.

-   **RMS 단일 시스템(1-Box) 환경 사용**

    RMS 단일 시스템(1-Box) 환경을 사용하여 응용 프로그램을 테스트하는 경우 응용 프로그램 실행 파일과 응용 프로그램 매니페스트를 단일 시스템(1-Box) 환경의 임의 디렉터리에 복사한 다음 응용 프로그램을 실행합니다.

    RMS 단일 시스템(1-box) 환경에 대한 자세한 내용은 [테스트 환경 설정](how-to-set-up-your-test-environment.md)을 참조하세요.

-   **사전 프로덕션 서버 구성 사용**

    사전 프로덕션용으로 구성된 RMS 서버에 대해 응용 프로그램을 테스트하는 경우 응용 프로그램을 실행할 컴퓨터(예: 개발 컴퓨터)에서 Active Directory Rights Management Services 클라이언트 2.1을 구성했는지 확인합니다. 그런 다음 응용 프로그램 실행 파일과 응용 프로그램 매니페스트가 해당 컴퓨터의 동일한 디렉터리에 있고 응용 프로그램을 실행하는지 확인합니다.

    컴퓨터에서 클라이언트를 구성하는 방법에 대한 자세한 내용은 [클라이언트 구성](how-to-configure-the-ad-rms-client-2-0.md)을 참조하세요. RMS 서버를 설치하는 방법에 대한 자세한 내용은 [서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md)을 참조하세요.

## 관련 항목

* [사용 방법](how-to-use-msipc.md)
* [클라이언트 구성](how-to-configure-the-ad-rms-client-2-0.md)
* [서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md)
* [IPCHelloWorld - 예제 응용 프로그램](how-to-build-your-first-application.md)
* [사전 프로덕션 개발 환경 설정](how-to-set-up-the-pre-production-development-environment.md)
* [프로덕션 환경으로 전환](switching-to-the-production-environment.md)
* [테스트 환경 설정](how-to-set-up-your-test-environment.md)
* [인증서 체인 이해](understanding-certificate-chains.md)
 

 





<!--HONumber=Jun16_HO1-->


