---
title: "데이터 보호 서비스, Azure Information Protection의 Azure Rights Management 서비스 질문과 대답 | Azure Information Protection"
description: "데이터 보호 서비스인 Azure Information Protection의 Azure Rights Management 서비스(Azure RMS)의 몇 가지 질문과 대답입니다."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad2d3d7962ab8f8422f4682e4ecd24a7cff3b239
ms.openlocfilehash: 1840954addbf7b3ad603c05b0c55f8bf99ccacfb


---

# Azure Information Protection에서 데이터 보호에 대한 질문과 대답

>*적용 대상: Azure Information Protection, Office 365*

데이터 보호 서비스인 Azure Information Protection의 Azure Rights Management 서비스에 대해 질문이 있나요? 여기에 해당 질문에 대한 대답이 있는지 확인하세요. 

## 파일을 Azure Rights Management에서 보호하려면 해당 파일이 클라우드에 있어야 하나요?
아니요. 이것은 일반적인 오해입니다. Azure Rights Management 서비스(및 Microsoft)가 데이터를 정보 보호 프로세스의 일부로 보거나 저장하지 않는다는 것입니다. 보호하는 정보는 Azure에 명시적으로 저장하거나 Azure에 정보를 저장하는 다른 클라우드 서비스를 사용하지 않는 한, Azure로 전송되거나 Azure에 저장되지 않습니다. 

[Azure RMS는 어떤 방식으로 작동하나요? 기본적인 이해](../understand-explore/how-does-it-work.md)를 참조하여 온-프레미스에서 생성 및 저장된 콜라 비밀 제조법이 Azure Rights Management 서비스를 통해 어떻게 보호되고 온-프레미스에 유지되는지를 확인할 수 있습니다.

## 내 온-프레미스 서버와 Azure Rights Management 서비스를 통합할 수 있나요?
예. Exchange Server, SharePoint 및 Windows 파일 서버와 같은 온-프레미스 서버에 Azure Rights Management를 통합할 수 있습니다. 이렇게 하려면 [Rights Management 커넥터](../deploy-use/deploy-rms-connector.md)를 사용합니다. 또는 Windows Server에서 FCI(파일 분류 인프라)를 사용하려는 경우 [RMS 보호 cmdlet](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx)을 사용할 수 있습니다. [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)등을 통해, 더 원활한 인증 환경을 위해 Active Directory 도메인 컨트롤러를 동기화 및 페더레이션할 수도 있습니다.

Azure Rights Management는 필요에 따라 XrML 인증서를 자동으로 생성하여 관리하므로 온-프레미스 PKI를 사용하지 않습니다. Azure Rights Management에서 인증서를 사용하는 방식에 대한 자세한 내용은 [Azure RMS 작동 방식](../understand-explore/how-does-it-work.md) 문서에서 [Azure RMS 작동 방식 연습: 첫 번째 사용, 콘텐츠 보호, 콘텐츠 소비](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) 섹션을 참조하세요.

## Azure RMS와 통합하는 타사 솔루션에 대한 정보는 어디서 찾을 수 있나요?

많은 소프트웨어 공급 업체들은 이미 Azure Rights Management와 통합하는 솔루션을 보유하고 있거나 이러한 솔루션을 구현하고 있으며, 그 목록은 매우 빨리 증가되고 있습니다. [Enterprise Mobility and Security Blog(Enterprise Mobility 및 보안 블로그)](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services)를 확인하고 Twitter의 [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy)에서 최신 업데이트를 구하면 유용할 수 있습니다. 그러나 특정 질문이 있으면 메일 메시지를 정보 보호 팀 askipteam@microsoft.com으로 보내 주세요.

## RMS 커넥터에 대한 관리 팩이나 유사한 모니터링 메커니즘이 있나요?

Rights Management 커넥터에서 정보, 경고 및 오류 메시지를 이벤트 로그에 기록하긴 하지만, 이러한 이벤트에 대한 모니터링을 포함하는 관리 팩은 없습니다. 그러나 이벤트 목록과 해당 설명이 정정 작업을 할 수 있도록 돕는 자세한 정보와 함께 [Azure Rights Management 커넥터 모니터링](../deploy-use/monitor-rms-connector.md)에 정리되어 있습니다.

## Azure RMS를 구성하려면 전역 관리자여야 하나요? 또는, 다른 관리자에게 위임할 수 있나요?

분명 Office 365 테넌트 또는 Azure AD 테넌트에 대한 전역 관리자는 Azure Rights Management 서비스에 대한 모든 관리 작업을 실행할 수 있습니다. 하지만, 관리 권한을 다른 사용자에게 할당하려는 경우에는 Azure RMS PowerShell cmdlet [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx)을 사용하여 그렇게 할 수 있습니다. 이 관리 역할은 사용자 계정 또는 그룹별로 할당할 수 있습니다. **전역 관리자**와 **커넥터 관리자**, 이렇게 두 개의 역할을 사용할 수 있습니다. 

이 역할 이름에서 알 수 있듯이, 첫 번째 역할은 Azure Rights Management에 대한 모든 관리 작업을 권한을 실행하는 권한을 부여하고(다른 클라우드 서비스에 대한 전역 관리자로 만들지 않고도), 두 번째 역할은 RMS(Rights Management) 커넥터만 실행하는 권한을 부여합니다.

몇 가지 참고 사항:

- Office 365에 대한 전역 관리자와 Azure AD에 대한 전역 관리자만 관리 포털(Office 365 관리 센터 또는 Azure 클래식 포털)을 사용하여 Azure RMS를 구성할 수 있습니다. Azure RMS에 대한 전역 관리자 역할을 할당받는 사용자는 Azure RMS PowerShell 명령을 사용하여 Azure RMS를 구성해야 합니다. 특정 작업에 대한 올바른 cmdlet을 찾는 데 도움이 필요하면 [Windows PowerShell을 사용하여 Azure 권한 관리 관리](../deploy-use/administer-powershell.md) 항목을 참조하세요.

- [온보딩 컨트롤](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구성한 경우, 이것은 RMS 커넥터를 제외하고 Azure RMS를 관리하는 기능에 영향을 주지 않습니다. 예를 들어 콘텐츠를 보호하는 기능을 "IT 부서" 그룹으로 제한하도록 온보딩 컨트롤을 구성했으면 RMS 커넥터를 설치하고 구성하는 데 사용하는 계정은 해당 그룹의 구성원이어야 합니다. 

- Azure RMS에 대한 관리자(테넌트의 전역 관리자 또는 Azure RMS 전역 관리자)는 Azure RMS로 보호된 문서나 메일에서 보호를 자동으로 제거할 수 없습니다. Azure RMS에 대한 슈퍼 사용자로 할당된 사용자만 그렇게 할 수 있으며, 이것도 슈퍼 사용자 기능을 활성화되어 있을 때 가능합니다. 그러나 테넌트의 전역 관리자와 Azure RMS 전역 관리자는 자신의 계정을 포함하여 사용자를 슈퍼 사용자로 할당할 수 있습니다. 이들은 슈퍼 사용자 기능을 활성화할 수도 있습니다. 이러한 작업은 Azure RMS 관리자 로그에 기록됩니다. 자세한 내용은 [Azure 권한 관리 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](../deploy-use/configure-super-users.md)의 보안 모범 사례 섹션을 참조하세요. 


## Exchange Online의 사용자와 Exchange Server 서버의 다른 사용자로 구성된 Exchange의 하이브리드 배포입니다. Azure RMS에서 지원되나요?
물론입니다. 사용자가 두 Exchange 배포에서 보호되는 전자 메일과 첨부 파일을 원활하게 보호하고 소비할 수 있습니다. 이 구성을 사용하려면 [Azure RMS를 활성화](../deploy-use/activate-service.md)하고 [Exchange Online에 IRM을 사용하도록 설정](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)한 다음 Exchange Server용 [RMS 커넥터를 배포 및 구성](../deploy-use/deploy-rms-connector.md)합니다.

## 이 보호를 프로덕션 환경에서 사용할 경우 회사가 솔루션에 갇히거나, Azure RMS로 보호한 콘텐츠를 액세스할 수 없게 되나요?
아니요. 항상 데이터를 제어하고 지속적으로 액세스할 수 있습니다. 더 이상 Azure Rights Management 서비스를 사용하지 않아도 마찬가지입니다. 자세한 내용은 [Azure 권한 관리 서비스 해제 및 비활성화](../deploy-use/decommission-deactivate.md)를 참조하세요.

그러나 Azure RMS 배포를 해제하기 전에 그런 판단을 내리게 된 이유를 알고 싶습니다. Azure Rights Management 보호가 비즈니스 요구 사항에 부합하지 않을 경우 가까운 시일 내에 새로운 기능이 예정되어 있거나 대안이 있는지 확인해 보시기 바랍니다. 기술 및 비즈니스 요구 사항에 대한 논의는 [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) 로 전자 메일 메시지를 보내 주시면 됩니다.

## Azure RMS를 사용하여 콘텐츠를 보호할 수 있는 사용자를 제어할 수 있나요?
예. Azure Rights Management 서비스에는 이 시나리오에 대한 사용자 온보딩 컨트롤이 있습니다. 자세한 내용은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md) 문서에서 [단계별 배포에 대한 온보딩 컨트롤 구성](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) 섹션을 참조하세요.

## 사용자가 보호된 문서를 특정 조직과 공유하지 못하게 할 수 있나요?
데이터 보호용 Azure Rights Management 서비스의 가장 큰 이점 중 하나는 Azure AD가 인증을 처리하기 때문에 각 파트너 조직에 대한 명시적 트러스트를 구성할 필요 없이 비즈니스 간 공동 작업을 지원한다는 점입니다.

사용자가 특정 조직과 안전하게 문서를 공유하지 못하게 하는 관리 옵션은 없습니다. 신뢰하지 않거나 경쟁 사업을 진행하는 조직을 차단하고 싶은 경우를 예로 들 수 있습니다. Azure Rights Management 서비스에서 이러한 조직의 사용자에게 보호된 문서를 보내지 못하게 하면 사용자가 보호되지 않은 상태로 문서를 공유하게 되므로 원치 않는 결과가 나타날 수 있습니다. 따라서 이 방법은 적절하지 않습니다. 예를 들어 누가 이러한 조직의 어떤 사용자와 회사 기밀 문서를 공유하는지, 문서(또는 메일)가 Azure Rights Management 서비스를 통해 보호될 때 어떤 작업을 수행할 수 있는지를 알 수 없게 됩니다.

## 보호되는 문서를 회사 외부의 누군가와 공유할 때 해당 사용자를 어떻게 인증하나요?
Azure Rights Management 서비스는 기업 간 공동 작업에서의 관리자 편의를 위해 항상 Azure Active Directory 계정과, 연결된 전자 메일 주소를 사용자 인증에 사용합니다. 다른 조직에서 Azure 서비스를 사용한다면 온-프레미스에서 만들어져 관리되며 Azure에 동기화되는 계정이더라도 사용자에게 이미 Azure Active Directory 계정이 있을 것입니다.  해당 조직에 Office 365가 있다면 바탕에서는 사용자 계정에 Azure Active Directory를 사용하고 있습니다. 사용자 조직이 Azure에서 계정을 관리하지 않은 경우 [개인용 RMS](../understand-explore/rms-for-individuals.md)에 등록할 수 있습니다. 그러면 해당 사용자의 계정이 있는 조직에 대해 관리되지 않는 Azure 테넌트와 디렉터리가 생성되어 해당 사용자(및 후속 사용자)를 Azure Rights Management 서비스에 인증할 수 있게 됩니다.

이러한 계정에 대한 인증 방법은 다른 조직의 관리자가 Azure Active Directory 계정을 어떻게 구성했느냐에 따라 달라질 수 있습니다. 예를 들어, 이 계정에 대해 만든 암호, 다단계 인증(MFA), 페더레이션 또는 Active Directory 도메인 서비스에서 생성된 후 Azure Active Directory에 동기화된 암호 등을 사용할 수 있습니다.

## 회사 외부의 사용자를 사용자 지정 템플릿에 추가할 수 있나요?
예. 최종 사용자(및 관리자)가 응용 프로그램에서 선택할 수 있는 사용자 지정 템플릿을 만들면 지정한 사전 정의 정책을 통해 정보 보호를 쉽고 빠르게 적용할 수 있습니다. 템플릿의 설정 중 하나는 콘텐츠에 액세스할 수 있는 사용자이며, 조직 내의 사용자 및 그룹과 조직 외부의 사용자를 지정할 수 있습니다.

조직 외부에서 사용자를 지정하려면 템플릿을 구성할 때 Azure 클래식 포털에서 선택하는 그룹에 연락처로 추가합니다. 또는 [Azure 권한 관리용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 사용합니다.

-   **권한 정의 개체를 사용하여 템플릿을 생성하거나 업데이트**합니다.    권한 정의 개체에서 외부 전자 메일 주소 및 해당 권한을 지정한 다음 템플릿을 만들거나 업데이트할 때 사용합니다. [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) cmdlet을 통해 변수를 만든 다음 [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) cmdlet(새 템플릿의 경우) 또는 [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) cmdlet(기존 템플릿을 수정하는 경우)을 통해 이 변수를 -RightsDefinition 매개 변수에 제공하여 권한 정의 개체를 지정합니다. 그러나 기존 템플릿에 이러한 사용자를 추가하는 경우 외부 사용자뿐 아니라 템플릿의 기존 그룹에 대해 권한 정의 개체를 정의해야 합니다.

사용자 지정 템플릿에 대한 자세한 내용은 [Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

## Azure AD의 동적 그룹에서 Azure RMS가 작동하나요?
Azure AD Premium 기능을 사용하면 [특성 기반 규칙](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)을 지정하여 그룹에 대한 동적 멤버 자격을 구성할 수 있습니다. Azure AD에서 보안 그룹을 만드는 경우 이 그룹 유형은 동적 멤버 자격을 지원하지만 메일 주소를 지원하지 않으므로 Azure Rights Management 서비스와 함께 사용할 수 없습니다. 그러나 이제 동적 멤버 자격과 메일 사용을 둘 다 지원하는 새 그룹 유형을 Azure AD에서 만들 수 있습니다. Azure 클래식 포털에서 새 그룹을 추가하는 경우 **그룹 유형**으로 **Office 365 "미리 보기"**를 선택할 수 있습니다. 이 그룹은 메일 사용이 가능하므로 Azure Rights Management 보호와 함께 사용할 수 있습니다.

옵션 이름에서 알 수 있듯이 이 새로운 그룹 유형은 미리 보기 상태이므로 추가 기능과 새 설명서가 제공될 것입니다. 그와 함께 Azure Rights Management 보호와 함께 이 새로운 그룹 유형을 사용할 수 있다는 것을 확인하고 싶었습니다.


## Azure RMS에서는 어떤 장치 및 파일 형식을 지원하나요?
Azure Rights Management 서비스를 지원하는 장치 목록은 [Azure RMS 요구 사항: Azure RMS를 지원하는 클라이언트 장치](../get-started/requirements-client-devices.md)를 참조하세요. 현재는 지원 장치 중 일부만 모든 Rights Management 기능을 지원하기 때문에 같은 항목의 [Azure RMS 요구 사항: 응용 프로그램](../get-started/requirements-applications.md)도 확인해야 합니다.

Azure Rights Management 서비스는 모든 형식의 파일을 지원할 수 있습니다. 텍스트, 이미지, Microsoft Office(Word, Excel, PowerPoint) 파일, .pdf 파일 및 일부 기타 응용 프로그램 파일 형식의 경우 Azure Rights Management는 권한 적용 및 암호화를 모두 포함하는 기본 보호 기능을 제공합니다. 기타 모든 응용 프로그램 및 파일 형식의 경우 일반적인 보호를 통해 사용자가 파일을 열 권한이 있는지 확인하는 인증 및 파일 캡슐화 기능을 제공합니다.

Azure Rights Management에서 기본적으로 지원하는 파일 이름 확장명 목록은 [Rights Management 공유 응용 프로그램 관리자 가이드](../rms-client/sharing-app-admin-guide.md)에서 [지원되는 파일 형식 및 파일 이름 확장명](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) 섹션을 참조하세요. 여기에 나열되지 않은 파일 이름 확장명은 해당 파일에 일반 보호를 자동 적용하는 RMS 공유 응용 프로그램을 통해 지원됩니다.

## RMS로 보호된 Office 문서를 열면 연결된 임시 파일도 RMS로 보호되나요?

아니요. 이 시나리오에서는 연결된 임시 파일에 원래 문서의 데이터가 포함되지 않고 대신 파일이 열려 있는 동안 사용자가 입력하는 내용만 포함됩니다. 원본 파일과 달리 임시 파일은 명시적으로 공유를 위해 설계되지 않았으며 로컬 보안 컨트롤(예: BitLocker 및 EFS)로 보호되는 장치에 있습니다.

## Azure Information Protection에 BYOK를 정말 사용하고 싶은데, Exchange Online과 호환되지 않는다고 합니다. 어떻게 해야 하나요?
Azure Information Protection의 Azure Rights Management 서비스를 사용하여 이 현재 제한이 지연되지 않게 하세요. 기존 Exchange Online에서 BYOK를 사용하려는 경우 Microsoft가 키를 생성 및 관리하는 기본 키 관리 모드에서 Azure Information Protection을 배포하는 것이 좋습니다. 이런 방식으로 중요 파일과 전자 메일을 즉시 보호하는 장점을 지금 활용하고 나중에 BYOK로 이동할 수 있습니다(예: Exchange Online에서 BYOK를 지원하게 될 때). BYOK 방식으로 전환하는 경우 보관된 키를 사용하여 이전에 보호했던 문서와 전자 메일에 계속 액세스할 수 있습니다.

그러나 회사 정책에서 하드웨어 보안 모듈(HSM)의 사용을 요구하고 이러한 모듈이 Azure Information Protection 배포를 차단하는 경우, Exchange용 Rights Management 보호 기능을 축소한 상태로 지금 BYOK로 Azure Information Protection을 배포할 수도 있습니다. 자세한 내용은 [Azure 권한 관리 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)에서 [BYOK 가격 및 제한 사항](../plan-design/byok-price-restrictions.md)을 참조하세요.

## SharePoint 보호 라이브러리에서 작동하지 않는 것 같은 기능이 있습니다. 이 기능에 대한 지원이 예정되어 있나요?
현재, SharePoint는 사용자 지정 템플릿, 문서 추적 및 일부 다른 기능을 지원하지 않는 IRM 보호 라이브러리를 사용하여 Rights Management 보호 문서를 지원합니다. 자세한 내용은 [Office 응용 프로그램 및 서비스](../understand-explore/office-apps-services-support.md) 문서에서 [SharePoint Online 및 SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) 섹션을 참조하세요.

아직 지원되지 않는 특정 기능에 관심이 있는 경우 [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services)(Enterprise Mobility 및 보안 블로그)의 공지에 관심을 기울이시기 바랍니다.

## 사용자가 회사 내부와 외부의 사람들과 파일을 안전하게 공유할 수 있게, SharePoint Online에서 One Drive for Business를 어떻게 구성하나요?
기본적으로 이것은 Office 365 관리자가 구성하는 것이 아니라 사용자가 구성합니다.

SharePoint 사이트 관리자가 자신이 소유한 SharePoint 라이브러리에 IRM을 활성화 및 구성하듯이 비즈니스용 OneDrive는 사용자가 본인이 보유한 비즈니스용 OneDrive 라이브러리를 활성화 및 구성할 수 있게 디자인되었습니다.  그러나 이러한 사용자를 위해 PowerShell을 사용하여 이 작업을 수행할 수 있습니다. 지침은 [Office 365: 클라이언트 및 온라인 서비스 구성](../deploy-use/configure-office365.md) 문서에서 [SharePoint Online 및 비즈니스용 OneDrive: IRM 구성](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) 섹션을 참조하세요.

## 배포 성공을 위한 팁이나 요령이 있나요?
많은 배포를 감독하고 고객, 파트너, 컨설턴트와 지원 엔지니어의 이야기를 들어본 결과, 경험을 바탕으로 전달할 수 있는 가장 중요한 팁 중 하나는 **단순한 권한 정책을 디자인 및 배포**하라는 것입니다.

Azure Information Protection는 모든 사용자와 안전하게 공유할 수 있도록 하므로 데이터 보호 범위에 욕심을 부려도 좋습니다. 그러나 권한 정책에 대해서는 보수적인 견해를 견지하세요. 많은 조직에서 비즈니스에 대한 영향력이 가장 큰 것은 조직의 사용자에 대한 액세스를 제한하는 기본 권한 정책 템플릿을 적용하여 데이터 누출을 방지하는 것입니다. 물론, 사용자의 인쇄나 편집 등을 방지해야 하는 경우 훨씬 더 세분화할 수도 있습니다.  그러나 더 세분화된 제한은 정말로 높은 수준의 보안이 필요한 문서에 대한 예외로 유지하고, 처음부터 이러한 더 제한적인 정책을 구현하지는 말고 보다 단계적인 방법을 계획하세요.

## 이제 조직을 떠난 직원이 보호하던 파일에 대한 액세스는 어떻게 확보하나요?
인증된 사용자에게 조직의 RMS 테넌트사용 라이선스에 대한 전체 권한을 제공하는 Azure RMS의 슈퍼 사용자 기능을 사용합니다. 이 기능은 권한이 있는 서비스가 필요에 따라 파일을 인덱스 및 검사할 수 있도록 합니다.

자세한 내용은 [Azure 권한 관리 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](../deploy-use/configure-super-users.md)을 참조하세요.

## Rights Management 기능을 사용하면 화면을 캡처할 수 없나요?
Rights Management는 **복사** [사용 권한](../deploy-use/configure-usage-rights.md)을 부여하지 않으므로 Windows 플랫폼(Windows 7, Windows 8.1, Windows 10, Windows Phone) 및 Android에서 일반적으로 사용되는 화면 캡처 도구에서 화면 캡처를 방지할 수 있습니다. 그러나 iOS 및 Mac 장치에서 화면 캡처를 보호하도록 모든 앱을 허용하지 않으므로 브라우저(예: Outlook Web App 및 Office Online과 함께 사용하는 경우)에서도 화면 캡처를 막을 수 없습니다.

화면 캡처를 차단하면 실수나 부주의로 인한 기밀 또는 중요한 정보 공개를 방지할 수 있습니다. 그러나 사용자가 화면에 표시되는 데이터를 공유할 수 있는 방법은 여러 가지가 있으며 스크린 샷을 만드는 것은 한 가지 방법에 불과합니다. 예를 들어 표시되는 정보를 공유하려는 사용자가 휴대폰 카메라로 사진을 찍거나 데이터를 다시 입력하거나, 누군가에게 구두로 전달할 수도 있습니다.

이 예제에서 보여주듯이 모든 플랫폼과 모든 소프트웨어에서 화면 캡처를 차단하기 위해 Rights Management API를 지원했더라도 기술만으로 사용자가 하지 않아야 하는 데이터 공유를 항상 방지할 수 있는 것은 아닙니다. Rights Management는 권한 부여 및 사용 정책을 사용하여 중요한 데이터를 보호하는 데 도움이 될 수 있지만 이러한 엔터프라이즈 권한 관리 솔루션을 다른 제어 기능과 함께 사용해야 합니다. 예를 들어 물리적 보안을 구현하고, 조직 데이터에 액세스할 수 있도록 허가된 사람들을 신중하게 모니터링하고, 공유해서는 안 되는 데이터를 이해하도록 사용자를 교육하는 데 투자해야 합니다.

## 전달 금지로 메일을 보호하는 사용자와 전달 권한이 없는 템플릿 간의 차이점은 무엇입니까?

이름 및 모양에도 불구하고, **전달 금지**는 전달 권한의 반대도 아니고, 템플릿도 아닙니다. 실제로 메일 전달 제한 외에도, 첨부 파일 복사, 인쇄 및 저장 제한이 포함된 권한 집합입니다. 권한은 선택한 수신자를 통해 사용자에게 동적으로 적용되며, 관리자가 권한을 정적으로 할당하지 않습니다. 자세한 내용은 [Azure 권한 관리에 대한 사용 권한 구성](../deploy-use/configure-usage-rights.md) 항목의 [메일에 대한 전달 금지 옵션](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) 섹션을 참조하세요.






<!--HONumber=Sep16_HO4-->

