---
title: Azure Information Protection 배포 로드맵
description: 다음 단계에 따라 조직에 대해 Azure Information Protection을 준비, 구현 및 관리합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 43f99a35104ecdc3bfb422ed9f6747043e895ac7
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44149840"
---
# <a name="azure-information-protection-deployment-roadmap"></a>Azure Information Protection 배포 로드맵

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

다음 단계를 권고 사항으로 사용하여 조직에 대해 Azure Information Protection을 준비, 구현 및 관리할 수 있습니다.

그러나 프로덕션 환경에서 롤아웃하지 않고 직접 Azure Information Protection을 빠르게 시도하려는 경우 [Azure Information Protection에 대한 빠른 시작 자습서](./infoprotect-quick-start-tutorial.md)를 참조하세요.

> [!IMPORTANT]
> 다음 단계를 수행하기 전에 [Azure Information Protection 요구 사항](./requirements.md)을 검토해야 합니다.

조직에 적용 가능하고, 필요한 [구독 기능](https://azure.microsoft.com/pricing/details/information-protection/)과 일치하는 배포 로드맵을 선택합니다.

- [분류, 레이블 지정 및 보호 기능 사용](#deployment-roadmap-for-classification-labeling-and-protection)

- [데이터 보호 기능만 사용](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>분류, 레이블 지정, 및 보호에 대한 배포 로드맵

> [!NOTE]
> 이미 Azure Information Protection에서 보호 기능을 사용하고 있습니까? 이 단계를 대부분 건너뛰고 3단계와 5.1단계에 중점을 두면 됩니다.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>1단계: 구독을 확인하고 사용자 라이선스 할당
[Azure Information Protection 가격 책정](https://azure.microsoft.com/pricing/details/information-protection) 페이지에서 구독 정보 및 기능 목록을 검토하여 예상하는 기능이 포함된 구독이 조직에 있는지 확인합니다. 그런 다음 문서와 전자 메일을 분류하고, 레이블 지정하고, 보호할 조직의 각 사용자에게 이 구독의 라이선스를 할당합니다.

참고: 개인용 무료 RMS 구독에서 사용자 라이선스를 수동으로 할당하지 말고 이 라이선스를 사용하여 조직의 Azure Rights Management 서비스를 관리하지 마세요. 이러한 라이선스는 Office 365 관리 센터에 **Rights Management Adhoc**으로 표시되고, Azure AD PowerShell cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx)를 실행할 경우 **RIGHTSMANAGEMENT_ADHOC**으로 표시됩니다. 개인용 RMS 구독이 사용자에게 자동으로 부여되고 할당되는 방법에 대한 자세한 내용은 [개인용 RMS 및 Azure Information Protection](./rms-for-individuals.md)을 참조하세요.


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>2단계: Azure Information Protection을 사용하도록 테넌트 준비
Azure Information Protection 사용을 시작하기 전에 다음 준비를 수행합니다.

- 조직의 사용자 인증 및 권한 부여를 위해 Azure Information Protection에서 사용하는 사용자 계정 및 그룹이 Office 365 또는 Azure Active Directory에 있는지 확인합니다. 필요한 경우 이러한 계정 및 그룹을 만들거나 온-프레미스 디렉터리에서 동기화합니다. 자세한 내용은 [Azure Information Protection을 위한 사용자 및 그룹 준비](prepare.md)를 참조하세요.

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>3단계: 분류 및 레이블 지정 구성 및 배포

분류 전략이 아직 없는 경우 [기본 Azure Information Protection 정책](./configure-policy-default.md)을 검토하고 조직 데이터에 할당할 분류 레이블을 결정하는 기준으로 사용합니다. 비즈니스 요구 사항에 맞게 사용자 지정할 수도 있습니다. 

분류 결정을 지원하는 데 필요한 사항을 변경할 수 있도록 기본 Azure Information Protection 레이블을 다시 구성합니다. 사용자가 수동으로 레이블을 지정하기 위한 정책을 구성하고 적용할 레이블과 적용 시기에 대해 설명하는 사용자 지침을 작성합니다. 자동으로 보호를 적용하는 레이블로 기본 정책이 만들어졌으면 보호 설정을 제거하거나 레이블을 사용 하지 않도록 설정합니다. Azure Information Protection 정책을 구성하는 방법에 대한 자세한 내용은 [Azure Information Protection 정책 구성](./configure-policy.md)을 참조하세요.

그런 다음 사용자에게 Azure Information Protection 클라이언트를 배포하고 레이블을 선택하는 경우에 대한 사용자 교육 및 지침을 제공하여 지원합니다. 클라이언트를 설치 및 지원하는 방법에 대한 자세한 내용은 [Azure Information Protection 클라이언트 관리자 가이드](./rms-client/client-admin-guide.md)를 참조하세요.

시간이 지나 사용자가 자신의 문서와 전자 메일에 익숙하게 레이블을 지정할 수 있게 되면 더 많은 고급 구성을 소개합니다. 고급 구성은 다음과 같습니다.

- 기본 레이블 적용

- 하위 분류 수준을 사용하여 레이블을 선택한 경우 사용자에게 맞춤에 대해 묻는 메시지 표시

- 모든 문서와 전자 메일에 레이블 지정

- 사용자 지정된 머리글, 바닥글 또는 워터마크

- 권장 사항 및 자동 레이블 지정 지원을 위한 조건

이 단계에서 문서와 전자 메일을 보호하는 옵션을 선택하지 마세요.

### <a name="step-4-prepare-for-data-protection"></a>4단계: 데이터 보호를 위한 준비

사용자가 자신의 문서와 전자 메일에 익숙하게 레이블을 지정할 수 있게 되면 가장 중요한 데이터에 대한 데이터 보호 기능을 소개해도 됩니다. 이 단계에서는 다음 준비가 필요합니다.

1. 테넌트 키를 Microsoft에서 관리하도록 할지(기본값) 아니면 직접 생성하고 관리할지(BYOK, Bring Your Own Key라고도 함)를 결정합니다. 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)을 참조하세요.

2. 인터넷에 연결된 한 대 이상의 컴퓨터에 AADRM용 PowerShell 모듈을 설치합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [AADRM PowerShell 모듈 설치](./install-powershell.md)를 참조하세요.

3. AD RMS를 사용 중인 경우: 마이그레이션을 수행하여 키, 템플릿 및 URL을 클라우드로 이동합니다. 자세한 내용은 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

4. 문서 및 이메일 보호를 시작할 수 있도록 보호 서비스가 활성화되어 있는지 확인합니다. 단계별 배포가 필요한 경우 특정 사용자로 사용을 제한하도록 사용자 온보딩 컨트롤을 구성합니다. 자세한 내용은 [Azure Rights Management 활성화](./activate-service.md)를 참조하세요.

원하는 경우 다음 항목을 구성할 수 있습니다.

-   조직에서 기본 템플릿만으로는 부족한 경우 보호 설정을 위한 사용자 지정 템플릿을 구성합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [Azure Information Protection 템플릿 구성 및 관리](./configure-policy-templates.md)를 참조하세요.

-   조직에서 보호 서비스를 사용하는 방식을 모니터링할 수 있도록 사용 현황 로깅을 구성합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [Azure Rights Management Service의 사용 현황 로깅 및 분석](./log-analyze-usage.md)을 참조하세요.

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-data-protection"></a>5단계: 데이터 보호에 대한 Azure Information Protection 정책, 응용 프로그램 및 서비스 구성

1. Azure Information Protection 정책을 업데이트하여 데이터 보호 적용
    
    하나 이상의 레이블에 보호를 적용하도록 Azure Information Protection 정책을 수정합니다. 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](./configure-policy-protection.md)을 참조하세요.
    
    사용자가 Outlook에서 레이블을 적용하여 Exchange에서 IRM(정보 권한 관리)이 구성되지 않은 경우에도 Rights Management 보호를 적용할 수 있습니다. 하지만 Exchange가 IRM 또는 [새로운 기능을 갖춘 Office 365 메시지 암호화](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)에 대해 구성될 때까지 조직에서는 Exchange를 통한 Azure Rights Management 보호의 전체 기능을 사용할 수 없습니다. 이 추가 구성은 다음 목록에 포함되어 있습니다(Exchange Online의 경우 2단계, Exchange 온-프레미스의 경우 5단계). 

2. Office 응용 프로그램 및 서비스 구성
    
    SharePoint Online 또는 Exchange Online에서 IRM(정보 권한 관리) 기능을 지원하도록 Office 응용 프로그램 및 서비스를 구성합니다. 자세한 내용은 [Azure Rights Management에 대해 응용 프로그램 구성](./configure-applications.md)을 참조하세요.

3. 데이터 복구를 위한 슈퍼 사용자 기능 구성
    
    Azure Information Protection이 보호하는 파일을 검사해야 하는 기존 IT 서비스(DLP(데이터 손실 방지) 솔루션, CEG(콘텐츠 암호화 게이트웨이) 및 맬웨어 방지 제품)가 있는 경우 Azure Rights Management에 대한 슈퍼 사용자가 되도록 서비스 계정을 구성합니다. 자세한 내용은 [Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](./configure-super-users.md)을 참조하세요.

4. 필요에 따라 대량으로 파일 분류 및 보호
    
    파일을 분류하고 보호할 뿐만 아니라 분류 및 보호를 제거할 수 있는 PowerShell cmdlet은 Azure Information Protection 클라이언트와 함께 자동으로 설치됩니다. 자세한 내용은 관리자 가이드에서 [Azure Information Protection 클라이언트에서 PowerShell 사용](./rms-client/client-admin-guide-powershell.md)을 참조하세요.

6. 온-프레미스 서버에 대한 커넥터 배포
    
    보호 서비스에 사용하려는 온-프레미스 서비스가 있으면 Rights Management 커넥터를 설치 및 구성합니다. 자세한 내용은 [Azure Rights Management 커넥터 배포](./deploy-rms-connector.md)를 참조하세요.

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>6단계: 데이터 보호 솔루션 사용 및 모니터링
이제 데이터를 보호할 준비가 되었으므로 회사에서 구성된 레이블 및 데이터 보호를 사용하는 방식을 로깅하세요. 이 배포 단계를 지원하기 위한 추가 정보를 보려면 다음을 참조하세요.

- [사용자가 Azure Rights Management 서비스를 사용하여 파일을 보호할 수 있도록 지원](./help-users.md)

-  [Azure Rights Management 서비스의 사용 현황 로깅 및 분석](./log-analyze-usage.md)

- [클라이언트 파일 및 사용 현황 로깅](./rms-client/client-admin-guide-files-and-logging.md)

Windows 기반 파일 서버에서 파일 분류 인프라를 사용하여 파일을 자동으로 보호하는 데 관심이 있는 경우 [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](./rms-client/configure-fci.md) 항목을 참조하세요.

### <a name="step-7-administer-the-protection-service-for-your-tenant-account-as-needed"></a>7단계: 필요에 따라 테넌트 계정의 보호 서비스 관리
보호 서비스 사용을 시작하면 PowerShell을 통해 관리 변경 작업을 스크립트로 작성하거나 자동화할 수 있습니다. 자세한 내용은 [Windows PowerShell을 사용하여 Azure Rights Management 서비스](./administer-powershell.md)를 참조하세요.


## <a name="deployment-roadmap-for-data-protection-only"></a>배포 로드맵(데이터 보호만 해당)

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-the-protection-service-from-azure-information-protection"></a>1단계: Azure Information Protection의 보호 서비스를 포함하는 구독이 있는지 확인
[Azure Information Protection 가격 책정](https://azure.microsoft.com/pricing/details/information-protection) 페이지에서 구독 정보 및 기능 목록을 검토하여 예상하는 기능이 포함된 구독이 조직에 있는지 확인합니다. 그런 다음, 문서와 이메일을 보호할 조직의 각 사용자에게 이 구독의 라이선스를 할당합니다.

참고: 개인용 무료 RMS 구독에서 사용자 라이선스를 수동으로 할당하지 말고 이 라이선스를 사용하여 조직의 Azure Rights Management 서비스를 관리하지 마세요. 이러한 라이선스는 Office 365 관리 센터에 **Rights Management Adhoc**으로 표시되고, Azure AD PowerShell cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx)를 실행할 경우 **RIGHTSMANAGEMENT_ADHOC**으로 표시됩니다. 개인용 RMS 구독이 사용자에게 자동으로 부여되고 할당되는 방법에 대한 자세한 내용은 [개인용 RMS 및 Azure Information Protection](./rms-for-individuals.md)을 참조하세요.


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>2단계: Azure Information Protection을 사용하도록 테넌트 준비
Azure Information Protection에서 보호 서비스 사용을 시작하기 전에 다음 준비를 수행합니다.

1.  Office 365 테넌트에 조직의 사용자 인증 및 권한 부여를 위해 Azure Information Protection에서 사용하는 사용자 계정 및 그룹이 포함되어 있는지 확인합니다. 필요한 경우 이러한 계정 및 그룹을 만들거나 온-프레미스 디렉터리에서 동기화합니다. 자세한 내용은 [Azure Information Protection을 위한 사용자 및 그룹 준비](prepare.md)를 참조하세요.

2. 테넌트 키를 Microsoft에서 관리하도록 할지(기본값) 아니면 직접 생성하고 관리할지(BYOK, Bring Your Own Key라고도 함)를 결정합니다. 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)을 참조하세요.

3. 인터넷에 연결된 한 대 이상의 컴퓨터에 AADRM용 PowerShell 모듈을 설치합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [AADRM PowerShell 모듈 설치](./install-powershell.md)를 참조하세요.

4. AD RMS를 사용 중인 경우: 마이그레이션을 수행하여 키, 템플릿 및 URL을 클라우드로 이동합니다. 자세한 내용은 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

5. 문서 및 이메일 보호를 시작할 수 있도록 보호 서비스가 활성화되어 있는지 확인합니다. 단계별 배포가 필요한 경우 특정 사용자로 사용을 제한하도록 사용자 온보딩 컨트롤을 구성합니다. 자세한 내용은 [Azure Rights Management 활성화](./activate-service.md)를 참조하세요.

원하는 경우 다음 항목을 구성할 수 있습니다.

-   조직에서 기본 템플릿만으로는 부족한 경우 보호 설정을 위한 사용자 지정 템플릿을 구성합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [Azure Information Protection 템플릿 구성 및 관리](./configure-policy-templates.md)를 참조하세요.

- 조직에서 보호 서비스를 사용하는 방식을 모니터링할 수 있도록 사용 현황 로깅을 구성합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [Azure Rights Management Service의 사용 현황 로깅 및 분석](./log-analyze-usage.md)을 참조하세요.

### <a name="step-3-install-the-client-and-configure-applications-and-services-for-rights-management"></a>3단계: Rights Management용 클라이언트 설치 및 응용 프로그램/서비스 구성

1. Azure Information Protection 클라이언트 배포
    
    사용자가 Office 2010을 지원하고, Office 문서와 전자 메일 이외의 파일을 보호하고, 보호된 문서를 추적할 수 있게 하려면 Azure Information Protection을 설치합니다. 이 클라이언트에 대해 사용자 교육을 제공합니다. 자세한 내용은 [Windows용 Azure Information Protection 클라이언트](./rms-client/aip-client.md)를 참조하세요.

2. Office 응용 프로그램 및 서비스 구성
    
    SharePoint Online 또는 Exchange Online에서 IRM(정보 권한 관리) 기능을 지원하도록 Office 응용 프로그램 및 서비스를 구성합니다. 자세한 내용은 [Azure Rights Management에 대해 응용 프로그램 구성](./configure-applications.md)을 참조하세요.

3. 데이터 복구를 위한 슈퍼 사용자 기능 구성
    
    Azure Information Protection이 보호하는 파일을 검사해야 하는 기존 IT 서비스(DLP(데이터 손실 방지) 솔루션, CEG(콘텐츠 암호화 게이트웨이) 및 맬웨어 방지 제품)가 있는 경우 Azure Rights Management에 대한 슈퍼 사용자가 되도록 서비스 계정을 구성합니다. 자세한 내용은 [Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](./configure-super-users.md)을 참조하세요.

4. 필요에 따라 대량으로 파일 보호 
    
    여러 파일 형식을 대량으로 보호하거나 대량으로 보호를 해제하는 PowerShell cmdlet이 Azure Information Protection 클라이언트와 함께 자동으로 설치됩니다. 자세한 내용은 관리자 가이드에서 [Azure Information Protection 클라이언트에서 PowerShell 사용](./rms-client/client-admin-guide-powershell.md)을 참조하세요.

5. 온-프레미스 서버에 대한 커넥터 배포
    
    보호 서비스에 사용하려는 온-프레미스 서비스가 있으면 Rights Management 커넥터를 설치 및 구성합니다. 자세한 내용은 [Azure Rights Management 커넥터 배포](./deploy-rms-connector.md)를 참조하세요.


### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>4단계: 데이터 보호 솔루션 사용 및 모니터링
이제 데이터를 보호할 준비가 되었으며 회사에서 보호 서비스를 사용하는 방식을 기록합니다. 이 배포 단계 지원에 대한 추가 내용은 [사용자가 Azure Rights Management Service를 사용하여 파일을 보호할 수 있도록 지원](./help-users.md) 및 [Azure Rights Management Service 사용 현황 로깅 및 분석](./log-analyze-usage.md)을 참조하세요.

Windows 기반 파일 서버에서 파일 분류 인프라를 사용하여 파일을 자동으로 보호하는 데 관심이 있는 경우 [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](./rms-client/configure-fci.md) 항목을 참조하세요.

### <a name="step-5-administer-the-protection-service-for-your-tenant-account-as-needed"></a>5단계: 필요에 따라 테넌트 계정의 보호 서비스 관리
보호 서비스 사용을 시작하면 PowerShell을 통해 관리 변경 작업을 스크립트로 작성하거나 자동화할 수 있습니다. 자세한 내용은 [Windows PowerShell을 사용하여 Azure Rights Management 서비스](./administer-powershell.md)를 참조하세요.

