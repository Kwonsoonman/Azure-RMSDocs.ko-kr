---
title: Azure Information Protection에 대한 FAQ
description: Azure Information Protection과, 데이터 보호 서비스인 Azure Rights Management(Azure RMS)에 대한 몇 가지 질문과 대답입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 04cafed6317bd17f08e6b09a7f0b42b2cb2e20c7
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51026675"
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Azure Information Protection 질문과 대답

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection 또는 Rights Management 보호(Azure RMS)에 대해 질문이 있나요? 여기에 해당 질문에 대한 대답이 있는지 확인하세요.

이 FAQ 페이지는 정기적으로 업데이트되며, 새로 추가된 내용은 [Azure Information Protection 기술 블로그](https://aka.ms/AIPblog)의 월간 설명서 업데이트 공지에 등록됩니다.

## <a name="whats-the-difference-between-azure-information-protection-and-microsoft-information-protection"></a>Azure Information Protection과 Microsoft Information Protection 간의 차이는 무엇인가요?

Azure Information Protection과 달리 Microsoft Information Protection은 구입 가능한 구독 또는 제품이 아닙니다. 대신, Microsoft Information Protection은 조직의 중요한 정보를 보호하도록 지원하는 제품 및 통합 기능을 위한 프레임워크입니다.

- 이 프레임워크의 개별 제품에는 Azure Information Protection, Office 365 Information Protection(예: Office 365 DLP), Windows Information Protection 및 Microsoft Cloud App Security가 있습니다. 

- 이 프레임워크의 통합된 기능에는 통합 레이블 관리, Office 앱을 기반으로 한 최종 사용자 레이블 지정 환경, Windows에서 통합 레이블을 이해하고 데이터에 보호를 적용하는 기능, Microsoft Information Protection SDK와 레이블이 지정된 PDF 및 보호된 PDF를 보는 Adobe Acrobat Reader의 새로운 기능이 포함됩니다.

자세한 내용은 [중요한 데이터를 보호하기 위해 사용 가능한 정보 보호 기능 발표](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967)를 참조하세요.

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Azure Information Protection과 Azure Rights Management의 차이는 무엇인가요?

Azure Information Protection은 조직의 문서와 메일을 분류하고, 레이블 지정하고, 보호하는 기능을 제공합니다. Azure Rights Management는 보호 기술에서 사용됩니다. 즉 Azure Information Protection의 구성 요소입니다.

## <a name="what-is-the-role-of-identity-management-for-azure-information-protection"></a>Azure Information Protection에서 ID 관리는 어떤 역할을 하나요?

사용자는 Azure Information Protection으로 보호되는 콘텐츠에 액세스하기 위해 유효한 사용자 이름과 암호가 있어야 합니다. Azure Information Protection이 데이터 보호에 어떻게 도움을 주는지 알아보려면 [데이터 보안 유지에서 Azure Information Protection의 역할](/enterprise-mobility-security/solutions/azure-information-protection-securing-data)을 참조하세요. 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Azure Information Protection을 사용하려면 어떤 구독이 필요하며, 포함된 기능은 무엇인가요?
[Azure Information Protection 가격 책정](https://azure.microsoft.com/en-us/pricing/details/information-protection) 페이지에서 구독 정보 및 기능 목록을 참조하세요. 

Azure Rights Management 데이터 보호를 포함하는 Office 365 구독이 있는 경우 [Azure Information Protection 라이선싱 데이터시트](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)를 다운로드하세요. 여기에는 라이선스에 대한 질문과 대답도 포함됩니다.

## <a name="ive-just-got-my-azure-information-protection-subscriptionhow-do-i-get-going"></a>방금 Azure Information Protection 구독을 구입했습니다. 이제 어떻게 해야 하나요?

Azure Information Protection을 처음 사용하며 좀 더 빠르게 익숙해지고 싶은 경우 먼저 [빠른 시작](quickstart-viewpolicy.md)으로 가서 [일반적인 시나리오에 대한 방법 가이드](how-to-guides.md)를 검토하세요.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Azure Information Protection 클라이언트는 분류 및 레이블이 포함된 구독에만 사용할 수 있나요?

아니요. Azure Information Protection 클라이언트에서 본 대부분의 프레젠테이션과 데모에는 분류 및 레이블을 지원하는 방법이 표시되어 있지만, Azure Rights Management 서비스만으로 데이터를 보호하는 구독에도 이 클라이언트를 사용할 수 있습니다.

Windows용 Azure Information Protection 클라이언트가 설치되어 있고 Azure Information Protection 정책이 없는 경우는 클라이언트가 자동으로 [보호 전용 모드](./rms-client/client-protection-only-mode.md)에서 작동합니다. 이 모드에서 사용자는 Rights Management 템플릿과 사용자 지정 권한을 쉽게 적용할 수 있습니다. 나중에 분류 및 레이블 지정이 포함된 구독을 구입하면 Azure Information Protection 정책을 다운로드할 때 클라이언트가 자동으로 표준 모드로 전환됩니다.

현재 Windows용 Rights Management 공유 응용 프로그램을 사용하고 있다면 이 응용 프로그램을 Azure Information Protection 클라이언트로 교체하는 것이 좋습니다. 공유 응용 프로그램에 대한 지원은 2019년 1월 31일에 종료됩니다. 전환에 관한 도움말은 [RMS 공유 응용 프로그램으로 수행해왔던 작업](./rms-client/upgrade-client-app.md)을 참조하세요.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Azure Information Protection을 구성하려면 전역 관리자여야 하나요? 또는 다른 관리자에게 위임할 수 있나요?

분명 Office 365 테넌트 또는 Azure AD 테넌트에 대한 전역 관리자는 Azure Information Protection에 대한 모든 관리 작업을 실행할 수 있습니다. 그러나 다른 사용자에게 관리 권한을 할당하려는 경우 다음 옵션을 사용할 수 있습니다.

- **Information Protection 관리자**: 이 Azure Active Directory 관리자 역할을 통해 관리자는 Azure Information Protection의 모든 측면을 구성할 수 있지만 다른 서비스는 구성할 수 없습니다. 이 역할을 가진 관리자는 Azure Rights Management 보호 서비스를 활성화 및 비활성화하고 보호 설정 및 레이블을 구성하며 Azure Information Protection 정책을 구성할 수 있습니다. 또한 이 역할을 가진 관리자는 모든 [Azure Information Protection 클라이언트](./rms-client/client-admin-guide-powershell.md) 및 [AADRM 모듈](administer-powershell.md)의 PowerShell cmdlet을 모두 실행할 수 있습니다. 
    
    사용자에게 이 관리 역할을 할당하려면 [Azure Active Directory에서 사용자에게 관리자 역할 할당](/azure/active-directory/active-directory-users-assign-role-azure-portal)을 참조하세요.

- **보안 관리자**: 이 Azure Active Directory 관리자 역할을 통해 관리자는 Azure Portal에서 Azure Information Protection의 모든 측면을 구성하고 다른 Azure 서비스의 일부 측면을 구성할 수 있습니다. 이 역할을 가진 관리자는 [AADRM 모듈의 PowerShell cmdlet](administer-powershell.md)을 실행할 수 없습니다.
    
    사용자에게 이 관리 역할을 할당하려면 [Azure Active Directory에서 사용자에게 관리자 역할 할당](/azure/active-directory/active-directory-users-assign-role-azure-portal)을 참조하세요. 이 역할이 있는 사용자에게 어떤 다른 권한이 있는지 보려면 Azure Active Directory 설명서의 [사용 가능한 역할](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) 섹션을 참조하세요.

- Azure Rights Management **전역 관리자** 및 **커넥터 관리자**: 이러한 Azure Rights Management 관리자 역할의 경우, 첫 번째 역할은 다른 클라우드 서비스의 전역 관리자가 되지 않고 모든 [AADRM 모듈의 PowerShell cmdlet](administer-powershell.md)을 실행할 권한을 사용자에게 부여하고 두 번째 역할은 RMS(Rights Management) 커넥터만 실행하는 권한을 부여합니다. 이러한 관리 역할은 관리 콘솔에 대한 권한을 부여하거나 문서 추적 사이트에서 관리자 모드를 사용하도록 권한을 부여하지 않습니다.

    이러한 관리 역할 중 하나를 할당하려면 AADRM PowerShell cmdlet, [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator)를 사용합니다.

몇 가지 참고 사항:

- [온보딩 컨트롤](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구성한 경우, 이 구성은 RMS 커넥터를 제외하고 Azure Information Protection을 관리하는 기능에 영향을 주지 않습니다. 예를 들어 콘텐츠를 보호하는 기능을 "IT 부서" 그룹으로 제한하도록 온보딩 컨트롤을 구성했으면 RMS 커넥터를 설치하고 구성하는 데 사용하는 계정은 해당 그룹의 구성원이어야 합니다. 

- 관리 역할이 할당된 사용자는 Azure Information Protection에 의해 보호된 문서나 이메일에서 보호를 자동으로 제거할 수 없습니다. 슈퍼 사용자로 할당된 사용자만 그렇게 할 수 있으며, 이것도 슈퍼 사용자 기능을 활성화되어 있을 때 가능합니다. 그러나 Azure Information Protection에 관리 권한을 할당한 사용자는 자신의 계정을 포함하여 사용자를 슈퍼 사용자로 할당할 수 있습니다. 이들은 슈퍼 사용자 기능을 활성화할 수도 있습니다. 이러한 작업은 관리자 로그에 기록됩니다. 자세한 내용은 [Azure 권한 관리 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](configure-super-users.md)의 보안 모범 사례 섹션을 참조하세요. 

- Azure Information Protection 레이블을 Office 365로 마이그레이션하는 경우 레이블 마이그레이션 설명서에서 [관리 역할에 대한 중요한 정보](configure-policy-migrate-labels.md#important-information-about-administrative-roles) 섹션을 참조하세요.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Azure Information Protection에서는 온-프레미스 및 하이브리드 시나리오를 지원하나요?

예. Azure Information Protection은 클라우드 기반 솔루션이지만 클라우드 뿐 아니라 온-프레미스에 저장된 문서 및 전자 메일을 분류, 레이블 지정 및 보호할 수 있습니다.

Exchange Server, SharePoint Server 및 Windows 파일 서버가 있는 경우 [Rights Management 커넥터](deploy-rms-connector.md)를 배포하여 이러한 온-프레미스 서버가 Azure Rights Management 서비스를 통해 전자 메일 및 문서를 보호하도록 할 수 있습니다. [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)등을 통해, 더 원활한 인증 환경을 위해 Active Directory 도메인 컨트롤러를 동기화 및 페더레이션할 수도 있습니다.

Azure Rights Management 서비스는 필요에 따라 XrML 인증서를 자동으로 생성하여 관리하므로 온-프레미스 PKI를 사용하지 않습니다. Azure Rights Management에서 인증서를 사용하는 방식에 대한 자세한 내용은 [Azure RMS 작동 방식](./how-does-it-work.md) 문서에서 [Azure RMS 작동 방식 연습: 첫 번째 사용, 콘텐츠 보호, 콘텐츠 소비](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) 섹션을 참조하세요.

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Azure Information Protection은 어떤 형식의 데이터를 분류하고 보호할 수 있나요?

Azure Information Protection은 온-프레미스 또는 클라우드에 있는 이메일 메시지 및 문서를 분류하고 보호할 수 있습니다. 이러한 문서에는 Word 문서, Excel 스프레드시트, PowerPoint 프레젠테이션, PDF 문서, 텍스트 기반 파일 및 이미지 파일이 포함됩니다. 지원되는 문서 형식 목록은 관리자 가이드의 [지원되는 파일 형식](./rms-client/client-admin-guide-file-types.md) 목록을 참조하세요.

Azure Information Protection은 데이터베이스 파일, 일정 항목, PowerBI 보고서, Yammer 게시물, Sway 콘텐츠 및 OneNote 전자 필기장과 같은 구조화된 데이터는 분류하고 보호할 수 없습니다.

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Azure Information Protection이 조건부 액세스를 위한 사용 가능한 클라우드 앱으로 나열되어 있습니다. 작동 방법은 무엇인가요?

예, 이제 공개 미리 보기용으로 Azure Information Protection에 대한 Azure AD의 조건부 액세스를 구성할 수 있습니다.

이제 사용자가 Azure Information Protection에서 보호하는 문서를 열 때 관리자는 표준 조건부 액세스 제어에 따라 해당 테넌트의 사용자에게 액세스 권한을 부여할 수 있습니다. MFA(Multi-Factor Authentication)는 가장 공통적으로 요청되는 조건 중 하나입니다. 다른 한 가지 조건은 장치가 [Intune 정책을 준수](/intune/conditional-access-intune-common-ways-use)해야 한다는 점입니다. 예를 들어 모바일 장치가 암호 요구 사항 및 최소 운영 체제 버전을 충족하고 컴퓨터가 도메인에 가입되어 있어야 합니다.

자세한 내용과 연습 예제는 다음 블로그 게시물을 참조하세요. [Azure Information Protection에 대한 조건부 액세스 정책](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/)

추가 정보:

- Windows 컴퓨터의 경우: 현재 미리 보기 릴리스에서 [사용자 환경이 초기화될](./how-does-it-work.md#initializing-the-user-environment) 때와 이후 30일마다 Azure Information Protection에 대한 조건부 액세스 정책을 평가합니다(이 프로세스는 부트스트팹이라고도 함).

- 조건부 액세스 정책을 평가하는 빈도를 세밀하게 조정할 수 있습니다. 토큰 수명을 구성하여 이 작업을 수행할 수 있습니다. 자세한 내용은 [Azure Active Directory에서 구성 가능한 토큰 수명](/azure/active-directory/active-directory-configurable-token-lifetimes)을 참조하세요.

- 이러한 계정은 Azure Portal에서 Azure Information Protection 블레이드에 액세스할 수 없기 때문에 관리자 계정을 조건부 액세스 정책에 추가하지 않는 것이 좋습니다.

- 다른 조직(B2B)과 공동으로 작업하기 위해 조건부 액세스 정책에서 MFA를 사용하는 경우 [Azure AD B2B 공동 작업](/active-directory/b2b/what-is-b2b)을 사용하고 다른 조직에서 공유할 사용자의 게스트 계정을 만들어야 합니다.

- 조건부 액세스에 많은 클라우드 앱을 사용하면 선택할 목록에 **Microsoft Azure Information Protection**이 표시되지 않을 수 있습니다. 이 경우에 목록 맨 위에 있는 검색 상자를 사용합니다. "Microsoft Azure Information Protection"을 입력하여 사용할 수 있는 앱을 필터링합니다. 지원되는 구독을 제공하면 선택할 **Microsoft Azure Information Protection**이 표시됩니다. 

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>Azure Information Protection의 레이블과 Office 365의 레이블 간 차이는 무엇인가요?

최근까지 Office 365는 해당 콘텐츠가 Office 365 서비스에 있는 경우 감사 및 보존을 위해 문서와 메일을 분류할 수 있는 [보존 레이블](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30)만 제공했습니다. 반면에, Azure Information Protection의 레이블을 사용하면 문서와 메일이 온-프레미스에 있든 클라우드에 있든 상관없이 일관성 있는 분류 및 보호 정책을 적용할 수 있습니다.

Microsoft Ignite 2018에서 발표된 것처럼, 이제 Office 365 보안 및 준수 센터에서 보존 레이블 외에 [민감도 레이블](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)을 생성 및 구성하는 옵션도 제공됩니다. 또한 이제 미리 보기에서 기존 Azure Information Protection 레이블을 새로운 통합 레이블 저장소로 마이그레이션할 수 있습니다. 

통합 레이블 관리와 이러한 레이블 지원 방식에 대한 자세한 내용은 블로그 게시물, [Announcing availability of information protection capabilities to help protect your sensitive data](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967)(중요한 데이터를 보호하기 위한 사용 가능한 정보 보호 기능 발표)를 참조하세요.

기존 레이블 마이그레이션에 대한 자세한 내용은 [Azure Information Protection 레이블을 Office 365 보안 및 준수 센터로 마이그레이션하는 방법](configure-policy-migrate-labels.md)을 참조하세요.

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>Windows Server FCI와 Azure Information Protection 스캐너의 차이점은 무엇인가요?

과거에는 Windows Server File Classification Infrastructure를 사용하여 서류를 분류한 후 [Rights Management 커넥터](deploy-rms-connector.md)(Office 문서만 해당) 또는 [PowerShell 스크립트](./rms-client/configure-fci.md)(모든 파일 형식)를 사용하여 분류된 문서를 보호할 수 있었습니다. 

이제는 [Azure Information Protection 스캐너](deploy-aip-scanner.md)를 사용하는 것을 추천합니다. 이 스캐너는 Azure Information Protection 클라이언트 및 Azure Information Protection 정책을 사용하여 문서(모든 파일 형식)에 레이블을 지정하여 이러한 문서가 분류되고 선택적으로 보호되도록 합니다.

이러한 두 솔루션의 주요 차이점은 다음과 같습니다.

|Windows Server FCI|Azure Information Protection 스캐너|
|--------------------------------|-------------------------------------|
|지원되는 데이터 저장소: <br /><br />- Windows Server의 로컬 폴더|지원되는 데이터 저장소: <br /><br />- Windows Server의 로컬 폴더<br /><br />- Windows 파일 공유 및 네트워크 연결 저장소<br /><br />- SharePoint Server 2016 및 SharePoint Server 2013 [이 버전의 SharePoint에 대한 지원을 확장](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010)한 고객의 경우 SharePoint Server 2010도 지원됩니다.|
|작동 모드: <br /><br />- 실시간|작동 모드: <br /><br />- 데이터 저장소를 체계적으로 탐색하고 이 주기를 한 번 또는 반복적으로 실행할 수 있습니다.|
|파일 형식에 대한 지원: <br /><br />- 기본적으로 모든 파일 형식이 보호됩니다. <br /><br />- 레지스트리를 편집하여 특정 파일 형식을 보호에서 제외할 수 있습니다.|파일 형식에 대한 지원: <br /><br />- 기본적으로 Office 파일 형식이 보호됩니다. <br /><br />- 레지스트리를 편집하여 특정 파일 형식을 보호에 포함할 수 있습니다.|

현재 로컬 폴더 또는 네트워크 저장소에서 보호되는 파일에 대한 [Rights Management 소유자](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner)를 설정할 때는 차이점이 있습니다. 기본적으로 두 솔루션 모두에서 Rights Management 소유자는 파일을 보호하는 계정으로 설정되지만 이 설정을 재정의할 수 있습니다.

- Windows Server FCI: Rights Management 소유자를 모든 파일에 대한 단일 계정으로 설정하거나 각 파일에 대한 Rights Management 소유자를 동적으로 설정할 수 있습니다. Rights Management 소유자를 동적으로 설정하려면 **-OwnerMail [Source File Owner Email]** 매개 변수 및 값을 사용합니다. 이 구성은 파일의 Owner 속성에 있는 사용자 계정 이름을 사용하여 Active Directory에서 해당 사용자의 이메일 주소를 검색합니다.

- Azure Information Protection 스캐너: Rights Management 소유자를 지정된 데이터 저장소에서 모든 파일에 대한 단일 계정으로 설정할 수 있지만 각 파일에 대한 Rights Management 소유자를 동적으로 설정할 수는 없습니다. 계정을 설정하려면 [데이터 리포지토리 프로필](/powershell/module/azureinformationprotection/Set-AIPScannerRepository?view=azureipps#optional-parameters)에 **-DefaultOwner** 매개 변수를 지정합니다.

스캐너가 SharePoint 사이트 및 라이브러리의 파일을 보호하는 경우 SharePoint 작성자 값을 사용하여 각 파일의 Rights Management 소유자가 동적으로 설정됩니다.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>곧 새 릴리스가 Azure Information Protection용으로 나올 예정이라고 들었습니다. 언제 나오나요?

기술 설명서에는 예정된 릴리스에 대한 정보가 없습니다. 이러한 종류의 정보와 릴리스 발표에 대해서는 [Enterprise Mobility and Security Blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services)(Enterprise Mobility 및 보안 블로그)를 확인하고 Twitter의 [Microsoft Mobility@MSFTMobility](https://twitter.com/MSFTMobility)에서 최신 업데이트를 받으세요. 관심이 있는 Office 릴리스의 경우에는 [Office 365 블로그](https://techcommunity.microsoft.com/t5/Office-365-Blog/bg-p/Office365Blog) 및 [Office 앱 블로그](https://techcommunity.microsoft.com/t5/Office-Apps-Blog/bg-p/OfficeAppsBlog)도 꼭 확인하세요.

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Azure Information Protection이 내 국가에 적합한가요?

국가마다 다양한 요구 사항 및 규정이 있습니다. 조직에 대한 이 질문에 대답하려면 [다양한 국가의 적합성](./compliance.md#suitability-for-different-countries)을 참조하세요.

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>GDPR에서 Azure Information Protection을 활용하려면 어떻게 하나요?

GDPR(일반 데이터 보호 규정)을 충족하기 위한 Azure Information Protection의 활용 방법을 확인하려면 비디오에서 [Microsoft 365에서는 GDPR에 도움이 되는 Information Protection 전략을 제공합니다.](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr) 블로그 게시물 공지를 참조하세요.

## <a name="where-can-i-find-supporting-information-for-azureinformation-protectionsuch-as-legal-compliance-and-slas"></a>법적 정보, 규정 준수, SLA 등의 Azure Information Protection 관련 지원 정보는 어디서 찾을 수 있나요?
[Azure Information Protection에 대한 규정 준수 및 지원 정보](./compliance.md)를 참조하세요.

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Azure Information Protection에 대한 문제를 보고하거나 의견을 보낼 수 있나요?

기술 지원에 대해서는 표준 지원 채널을 사용하거나 [Microsoft 지원에 문의](information-support.md#to-contact-microsoft-support)하세요.

향상된 기능 또는 새 기능에 대한 제안과 같은 피드백을 보내려면 Office 응용 프로그램의 **홈** 탭에 있는 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다. **Microsoft Azure Information Protection** 대화 상자에서 **피드백 보내기**를 클릭합니다. 이 옵션을 통해 Information Protection 팀으로 보낼 메일 메시지가 열립니다.

또한 엔지니어링 팀과 의견을 나눌 수 있게 [Azure Information Protection Yammer 사이트](https://www.yammer.com/askipteam/)에 여러분을 초대합니다. 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>내 문의 내용이 여기 없다면 어떻게 하나요?

먼저 분류 및 레이블 지정 또는 데이터 보호와 관련된 다음 질문과 대답을 검토합니다. Azure RMS(Azure Rights Management 서비스)에서는 Azure Information Protection에 대한 데이터 보호 기술을 제공합니다. Azure RMS는 분류 및 레이블 지정 또는 단독으로 사용될 수 있습니다. 

- [분류 및 레이블 지정에 대한 FAQ](faqs-infoprotect.md)

- [데이터 보호에 대한 FAQ](faqs-rms.md)

질문에 대한 대답이 되지 않으면 [Azure Information Protection에 대한 정보 및 지원](information-support.md)에 나열된 링크와 리소스를 사용합니다.

최종 사용자를 위한 FAQ도 있습니다.

- [iOS 및 Android용 Azure Information Protection 앱 FAQ](./rms-client/mobile-app-faq.md)

- [Mac 컴퓨터 및 Windows Phone용 RMS 공유 앱에 대 한 FAQ](https://technet.microsoft.com/dn451248)

- [FAQ for Rights Management Sharing Application for Windows](https://technet.microsoft.com/dn467883)(Windows용 Rights Management 공유 응용 프로그램 FAQ)



