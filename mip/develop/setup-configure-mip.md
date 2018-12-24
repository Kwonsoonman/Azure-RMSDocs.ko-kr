---
title: MIP(Microsoft Information Protection) SDK 설정 및 구성
description: Microsoft Azure Information Protection SDK에서 빌드한 응용 프로그램을 사용하기 위한 설정 및 구성 전제 조건을 제공합니다.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 2790c64095a6fca4a33f70aeada68fa0c6668020
ms.sourcegitcommit: bdce88088f7a575938db3848dce33e7ae24fdc26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52386732"
---
# <a name="microsoft-information-protection-mip-sdk-setup-and-configuration"></a>MIP(Microsoft Information Protection) SDK 설정 및 구성 

빠른 시작 및 자습서 문서는 MIP SDK 라이브러리 및 API를 사용하는 응용 프로그램 빌드를 중점적으로 설명합니다. 이 문서에서는 SDK 사용을 준비하면서 Office 365 구독 및 클라이언트 워크스테이션을 설정하고 구성하는 방법을 보여 줍니다.

MIP SDK는 다음 플랫폼에서 지원됩니다.  

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

## <a name="prerequisites"></a>필수 구성 요소

시작하기 전에 다음 항목을 검토하세요.

- [Office 365 보안 및 준수 센터란?](https://docs.microsoft.com/office365/securitycompliance/security-and-compliance)
- [Azure Information Protection이란?](/azure/information-protection/understand-explore/what-is-information-protection)
- [Azure Information Protection에서 보호가 작동하는 방식](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

> [!IMPORTANT]
> **사용자 개인 정보를 보호 하기 위해 자동 로깅을 사용 하도록 설정 하기 전에 동의 요청 해야 합니다.** 다음 예제는 Microsoft에서 로깅 알림에 사용 하는 표준 메시지:
>
> *오류 및 성능 로깅을 설정함으로써 Microsoft에 오류 및 성능 데이터를 보내는 것에 동의하게 됩니다. Microsoft는 인터넷을 통해 오류 및 성능 데이터(“데이터”)를 수집합니다. Microsoft는 이 데이터를 사용하여 Microsoft 제품 및 서비스의 품질, 보안 및 무결성을 제공하고 향상합니다. 예를 들어, Microsoft는 사용하는 기능, 기능의 응답 속도, 디바이스 성능, 사용자 인터페이스 조작, 제품에서 발생하는 문제 등 성능 및 안정성을 분석합니다. 데이터에는 현재 실행 중인 소프트웨어, IP 주소처럼 소프트웨어의 구성에 대한 정보도 포함됩니다.*

## <a name="sign-up-for-an-office-365-subscription"></a>Office 365 구독 등록

많은 SDK 예제에는 Office 365 구독에 대한 액세스 권한이 필요합니다. 아직 등록하지 않은 경우 다음 구독 유형 중 하나를 등록해야 합니다.

| 이름 | 등록 |
|------|---------|
| Office 365 Enterprise E3 평가판(30일 평가판) | https://go.microsoft.com/fwlink/p/?LinkID=403802 |
| Office 365 Enterprise E3 또는 E5 | https://products.office.com/business/office-365-enterprise-e3-business-software |
| Enterprise Mobility + Security E3 또는 E5 | https://www.microsoft.com/cloud-platform/enterprise-mobility-security |
| Azure Information Protection Premium P1 또는 P2 | https://azure.microsoft.com/pricing/details/information-protection/ |
| Microsoft 365 E3, E5 또는 F1 | https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans | 

## <a name="configure-sensitivity-labels"></a>민감도 레이블 구성

사용자는 현재 사용 중인 Azure Information Protection 레이블과 Office 365 보안 및 규정 준수 센터를 마이그레이션해야 합니다. 이 프로세스에 대한 자세한 내용은 [Azure Information Protection 레이블을 Office 365 보안 및 준수 센터로 마이그레이션하는 방법](/azure/information-protection/configure-policy-migrate-labels)을 참조하세요. 

## <a name="configure-your-client-workstation"></a>클라이언트 워크스테이션 구성

다음 단계를 완료하여 클라이언트 컴퓨터가 올바르게 설정 및 구성되도록 합니다.

1. Windows 10 워크스테이션을 사용하는 경우:

   - Windows 업데이트를 사용하여 머신을 Windows 10 Fall Creators Update(버전 1709) 이상으로 업데이트합니다. 현재 버전을 확인하려면:
     - 왼쪽 아래에서 Windows 아이콘을 클릭합니다.
     - “PC 정보”를 입력하고 “Enter” 키를 누릅니다.
     - 아래로 스크롤하여 **Windows 사양**으로 이동한 후 **버전**의 내용을 확인합니다.

   - 워크스테이션에서 “개발자 모드”를 사용하도록 설정되어 있는지 확인합니다.
     - 왼쪽 아래에서 Windows 아이콘을 클릭합니다.
     - “개발자 기능 사용”을 입력하고 **개발자 기능 사용** 항목이 표시되면 “Enter” 키를 누릅니다.
     - **설정** 대화 상자에서 **개발자용** 탭의 “개발자 기능 사용” 아래에서 **개발자 모드** 옵션을 선택합니다.
     - **설정** 대화 상자를 닫습니다.

2. 다음과 같은 워크로드 및 선택적 구성 요소와 함께 [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/)을 설치합니다.
   - **유니버설 Windows 플랫폼 개발** Windows 워크로드 및 다음과 같은 선택적 구성 요소:
     - **C++ 유니버설 Windows 플랫폼 도구**
     - **Windows 10 SDK 10.0.16299.0 SDK** 이상(기본적으로 포함되지 않은 경우)
   - **C++를 포함하는 데스크톱 개발** Windows 워크로드 및 다음과 같은 선택적 구성 요소:
     - **Windows 10 SDK 10.0.16299.0 SDK** 이상(기본적으로 포함되지 않은 경우) 

     [![Visual Studio 설치](media/setup-mip-client/visual-studio-install.png)](media/setup-mip-client/visual-studio-install.png#lightbox)

3. [ADAL.PS PowerShell 모듈](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2)을 설치합니다. 

   - 모듈을 설치하려면 관리자 권한이 필요하므로 먼저 다음 중 하나를 수행해야 합니다.

     - 관리자 권한이 있는 계정으로 컴퓨터에 로그인합니다.
     - 관리자 권한으로 Windows PowerShell 세션을 실행합니다.

   - 그런 후 `install-module -name adal.ps` cmdlet을 실행합니다.

     ```powershell
     PS C:\WINDOWS\system32> install-module -name adal.ps

     Untrusted repository
     You are installing the modules from an untrusted repository. If you trust this repository, change its
     InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
     'PSGallery'?
     [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): A

     PS C:\WINDOWS\system32>
     ```

4. GitHub에서 SDK 예제 다운로드 

   - [GitHub 프로필](https://github.com/join)이 아직 없으면 만듭니다.
   - 그런 다음, 최신 버전의 [Software Freedom Conservancy Git 클라이언트 도구(Git Bash)](https://git-scm.com/download/)를 설치합니다.
   - Git Bash를 사용하여 다음과 같이 원하는 샘플을 다운로드합니다.
     - 쿼리 https://github.com/Azure-Samples?utf8=%E2%9C%93&q=MipSdk를 사용하여 리포지토리를 봅니다. 
     - Git Bash를 사용하고 `git clone https://github.com/azure-samples/<repo-name>`을 사용하여 각 샘플 리포지토리를 다운로드합니다.

5. SDK 이진 및 헤더 파일 다운로드

   모든 플랫폼에 대해 SDK 이진 파일 및 헤더가 포함된 .zip 파일을 https://aka.ms/mipsdkbinaries에서 찾을 수 있습니다. 이 .zip에는 각 플랫폼 및 API에 하나씩 여러 개의 추가 .zip 파일이 들어 있습니다. 파일 이름은 다음과 같이 지정됩니다. 여기서 \<API\> = `file`, `protection` 또는 `upe`이고, \<OS\> = 플랫폼: `mip_sdk_<API>_<OS>_1.0.0.0.zip (or .tar.gz)`입니다.

   예를 들어, Debian의 보호 API 이진 파일 및 헤더에 대한 .zip은 `mip_sdk_protection_debian9_1.0.0.0.tar.gz`입니다.

   각 .zip 또는 tarball에는 다음 세 개의 디렉터리가 있습니다.

   - **Bins:** 해당되는 경우 각 플랫폼 아키텍처의 컴파일된 이진 파일
   - **Include:** Microsoft Information Protection SDK 헤더 파일
   - **Samples:** 샘플 응용 프로그램의 소스 코드

   Visual Studio 개발을 수행하는 경우 NuGet 패키지 관리자 콘솔을 통해 SDK를 설치할 수도 있습니다.

    ```console
    Install-Package Microsoft.InformationProtection.File
    Install-Package Microsoft.InformationProtection.Policy
    Install-Package Microsoft.InformationProtection.Protection
    ```  
    
6. SDK 이진 파일[동적 연결 라이브러리(.dll)]의 경로를 PATH 환경 변수에 추가합니다. PATH 변수를 사용하면 클라이언트 응용 프로그램이 런타임에 종속 DLL을 찾을 수 있습니다.
   - 왼쪽 아래에서 Windows 아이콘을 클릭합니다.
   - “경로”를 입력하고 **시스템 환경 변수 편집** 항목이 표시되면 “Enter” 키를 누릅니다.
   - **시스템 속성** 대화 상자에서 **환경 변수**를 클릭합니다.
   - **환경 변수** 대화 상자에서 **\<사용자\>의 사용자 변수** 아래의 **Path** 변수 행을 클릭한 다음, **편집...** 을 클릭합니다.
   - **환경 변수 편집** 대화 상자에서 새 편집 가능 행을 만드는 **새로 만들기**를 클릭합니다. 각 `file\bins\debug\amd64` , `protection\bins\debug\amd64` 및 `upe\bins\debug\amd64` 하위 디렉터리의 전체 경로를 사용하여 각각에 대해 새 행을 추가합니다. SDK 디렉터리는 `<API>\bins\<target>\<platform>` 형식으로 저장됩니다. 여기서 다음이 적용됩니다.
     - \<API\> = `file`, `protection`, `upe`
     - \<target\> = `debug`, `release`
     - \<platform\> = `amd64` (aka: x64), `x86` 등
   
   - **Path** 변수 업데이트가 완료되면 **확인**을 클릭합니다. 그런 다음, **환경 변수** 대화 상자로 돌아가면 **확인**을 클릭합니다.

## <a name="register-a-client-application-with-azure-active-directory"></a>Azure Active Directory에 클라이언트 응용 프로그램 등록

Office 365 구독 프로비저닝 프로세스의 일부로, 연결된 Azure AD 테넌트가 만들어집니다. Azure AD 테넌트는 Office 365 ‘사용자 계정’ 및 ‘응용 프로그램 계정’에 대한 ID와 액세스 관리를 제공합니다. 보안 API에 액세스해야 하는 응용 프로그램(예: MIP API)에는 응용 프로그램 계정이 필요합니다.

런타임 시 인증 및 권한 부여를 위해 계정은 계정 ID 정보에서 파생된 ‘보안 주체’로 표시됩니다. 응용 프로그램 계정을 나타내는 보안 주체를 [*서비스 주체*](/azure/active-directory/develop/developer-glossary#service-principal-object)라고 합니다. 

빠른 시작 및 MIP SDK 샘플에서 사용하기 위해 응용 프로그램 계정을 Azure AD에 등록하려면:

  > [!IMPORTANT] 
  > 계정을 만들기 위해 Azure AD 테넌트 관리에 액세스하려면 [구독에서 “소유자” 역할](/azure/billing/billing-add-change-azure-subscription-administrator)의 멤버인 사용자 계정으로 Azure Portal에 로그인해야 합니다. 테넌트의 구성에 따라 [응용 프로그램을 등록](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps)하려면 “전역 관리자” 디렉터리 역할의 멤버여야 할 수도 있습니다.
  > 제한된 계정으로 테스트하는 것이 좋습니다. 계정에 필요한 SCC 엔드포인트에 액세스할 수 있는 권한만 있는지 확인합니다. 명령줄을 통해 전달된 일반 텍스트 암호를 로깅 시스템에서 수집할 수 있습니다.

1. [Azure Active Directory와 응용 프로그램 통합, 응용 프로그램 추가 섹션](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#adding-an-application)의 단계를 따릅니다. 테스트를 위해, 가이드 단계를 진행할 때 지정된 속성에 대해 다음 값을 사용합니다. 
    - **응용 프로그램 유형** - SDK에서 설명하는 응용 프로그램은 기본적으로 설치되는 콘솔 응용 프로그램이므로 “네이티브”를 선택합니다. 네이티브 응용 프로그램은 보안 방식으로 응용 프로그램 자격 증명을 저장/사용할 수 없으므로 OAuth2에서 “공용” 클라이언트로 간주됩니다. 자체 자격 증명으로 등록되는 웹 응용 프로그램과 같은 “기밀” 서버 기반 응용 프로그램과는 다릅니다. 
    - **리디렉션 URI** - SDK는 단순 콘솔 클라이언트 응용 프로그램을 사용하므로 `<app-name>://authorize` 형식의 URI를 사용합니다.

2. 완료되면 새 응용 프로그램 등록을 위해 **등록된 앱** 페이지로 돌아갑니다. 빠른 시작에 필요하므로 GUID를 복사한 후 **응용 프로그램 ID** 필드에 저장합니다. 

3. 그런 다음, **설정**을 클릭하여 클라이언트가 액세스해야 하는 API 및 권한을 추가합니다. **설정** 페이지에서 **필요한 권한**을 클릭합니다.

4. 이제 런타임에 응용 프로그램에 필요한 MIP API 및 권한을 추가합니다.
   - **필요한 권한** 페이지에서 **추가**를 클릭합니다. 
   - **API 액세스 추가** 페이지에서 **API 선택**을 클릭합니다.
   - **API 선택** 페이지에서 “ **Microsoft Rights Management Services**” API를 클릭하고 **선택**을 클릭합니다.
   - API의 사용 가능한 권한에 대한 **액세스 사용** 페이지에서 “**사용자의 보호된 콘텐츠 만들기 및 액세스**”를 클릭하고 **선택**을 클릭한 후 **완료**를 클릭합니다.

5. 4단계를 반복하되 이번에는 **API 선택** 페이지에서 API를 검색해야 합니다.
   - **API 선택** 페이지의 검색 상자에 “**Microsoft Information Protection Sync Service**”를 입력하고 API를 클릭한 후 **선택**을 클릭합니다.
   - API의 사용 가능한 권한에 대한 **액세스 사용** 페이지에서 “**Read all unified policies a user has access to**(사용자에게 액세스 권한이 있는 모든 통합 정책 읽기)”를 클릭하고 **선택**을 클릭한 후 **완료**를 클릭합니다.

6. **필요한 권한** 페이지로 다시 돌아가면 **권한 부여**를 클릭하고 **예**를 클릭합니다. 이 단계에서는 지정된 권한으로 API에 액세스하기 위해 이 등록을 사용하는 응용 프로그램에 대한 사전 동의를 제공합니다. 전역 관리자로 로그인한 경우, 응용 프로그램을 실행하는 테넌트의 모든 사용자의 동의가 기록됩니다. 그렇지 않으면 사용자 계정에만 적용됩니다. 

완료되면 응용 프로그램 등록 및 API 권한은 다음 예제와 유사합니다.

   [![Azure AD 앱 등록](media/setup-mip-client/aad-app-registration.png)](media/setup-mip-client/aad-app-registration.png#lightbox)


등록에 API 및 권한을 추가하는 방법에 대한 자세한 내용은 [응용 프로그램 업데이트, 웹 API 섹션에 액세스하도록 클라이언트 응용 프로그램 구성](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#updating-an-application)을 참조하세요. 여기에서 클라이언트 응용 프로그램에 필요한 API 및 권한을 추가하는 방법에 대한 정보를 확인할 수 있습니다.  

## <a name="request-an-information-protection-integration-agreement-ipia"></a>IPIA(정보 보호 통합 계약) 요청

MIP를 사용 하 여 개발한 응용 프로그램을 릴리스할 수 있습니다, 전에 적용 하 고 Microsoft와의 공식 계약을 완료 해야 합니다.

1. 다음 정보가 포함된 전자 메일을 [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Requesting%20IPIA%20for%20<company-name>)으로 보내 IPIA를 완료합니다.

   **제목:** *회사 이름*의 IPIA 요청

   전자 메일의 본문에서 다음을 포함합니다.
   - 응용 프로그램 또는 제품 이름
   - 요청자의 성과 이름
   - 요청자의 메일 주소

2. Microsoft는 IPIA 요청을 받으면 양식(Word 문서)을 보내드립니다. IPIA 약관을 검토하고 다음 정보를 기입하여 해당 양식을 [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=IPIA%20Response%20for%20<company-name>)으로 다시 보내세요.

   - 회사의 상호
   - 회사가 있는 시/도 또는 국가
   - 회사 URL
   - 담당자의 전자 메일 주소
   - 회사의 추가 주소(선택 사항)
   - 회사 응용 프로그램의 이름
   - 응용 프로그램에 대한 간략한 설명
   - *Azure 테넌트 ID*
   - 응용 프로그램의 *앱 ID*
   - 급한 상황에 연락할 수 있는 회사 연락처, 전자 메일 및 전화 번호

3. 양식이 다시 수신되면 디지털 서명을 위해 최종 IPIA 링크를 보내드립니다. 귀하께서 서명하시면 해당 Microsoft 담당자가 서명을 하게 되고 이로써 계약이 완료됩니다.

### <a name="already-have-a-signed-ipia"></a>서명된 IPIA가 이미 있나요?

서명된 IPIA가 이미 있으며 릴리스할 응용 프로그램에 대해 새 *앱 ID*를 추가하려는 경우에는 [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Updating%20IPIA%20for%20<company-name>)에 전자 메일을 보내 다음과 같은 정보를 제공하세요.

- 회사 응용 프로그램의 이름
- 응용 프로그램에 대한 간략한 설명
- Azure 테넌트 ID(이전에 동일한 ID가 있어도 필요함)
- 응용 프로그램의 앱 ID
- 급한 상황에 연락할 수 있는 회사 연락처, 전자 메일 및 전화 번호

전자 메일을 보내신 후에 승인이 수신될 때까지 최대 72시간이 소요될 수 있습니다.

## <a name="next-steps"></a>다음 단계

- MIP SDK는 거의 완전히 비동기식으로 디자인되므로 빠른 시작 섹션을 시작하기 전에 [MIP SDK의 관찰자](concept-async-observers.md)에 대한 내용을 읽어야 합니다.
- SDK에 대한 실무 경험을 진행할 준비가 되면 [빠른 시작: 클라이언트 응용 프로그램 초기화(C++)](quick-app-initialization-cpp.md)로 시작합니다.


