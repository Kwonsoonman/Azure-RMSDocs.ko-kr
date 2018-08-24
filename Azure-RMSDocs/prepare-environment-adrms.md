---
title: Azure RMS 및 AD RMS를 위한 환경 준비
description: Azure Rights Management를 AD RMS와 함께 배포한 경우 지침입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/29/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 76367f00369dd239cc6b21a50a08dab736b77941
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804653"
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>AD RMS(Active Directory Rights Management Services)도 배포했을 때 Azure Rights Management를 위한 환경 준비

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> AD RMS(Active Directory Rights Management Services)를 사용하는 경우 지침

Azure Rights Management 서비스가 활성화되어 있는데 AD RMS도 사용하는 경우 이 조합은 호환되지 않습니다. 추가 단계가 없으면 일부 컴퓨터에서 Azure Rights Management 서비스를 자동으로 시작하고 AD RMS 클러스터에 연결할 수도 있습니다. 이 시나리오는 지원되지 않으며 불안정한 결과를 초래하므로 추가 단계를 수행하는 것이 중요합니다. 

**AD RMS를 배포했는지 확인하려면:**

1. 선택 사항이지만 대부분의 AD RMS 배포는 도메인 컴퓨터가 AD RMS 클러스터를 검색할 수 있도록 Active Directory에 SCP(서비스 연결 지점)를 게시합니다. 
    
    ADSI 편집을 사용하여 다음과 같이 Active Directory에 SCP가 게시되어 있는지 여부를 확인합니다. `CN=Configuration [server name], CN=Services, CN=RightsManagementServices, CN=SCP`

2. SCP를 사용하지 않는 경우 다음과 같이 Windows 레지스트리를 사용하여 AD RMS 클러스터에 연결하는 Windows 컴퓨터를 클라이언트 쪽 서비스 검색 또는 라이선스 리디렉션에 대해 구성해야 합니다. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation` 또는 `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`
    
    이러한 레지스트리 구성에 대한 자세한 내용은 [Windows 레지스트리를 사용하여 클라이언트 쪽 서비스 검색 사용](./rms-client/client-deployment-notes.md#enabling-client-side-service-discovery-by-using-the-windows-registry) 및 [라이선스 서버 트래픽 리디렉션](./rms-client/client-deployment-notes.md#redirecting-licensing-server-traffic)을 참조하세요.   

조직에 AD RMS가 배포된 경우 Azure Information Protection으로 마이그레이션할 수 있는지 여부를 고려하세요. Azure Information Protection은 AD RMS에 비교해 많은 이점이 있습니다. 예를 들어 모바일 장치에 대한 향상된 지원을 제공하는 것은 물론, Office 365 서비스, Exchange Server 및 SharePoint Server와의 통합이 향상되었습니다. 자세한 내용은 [Azure Information Protection 및 AD RMS 비교](compare-on-premise.md)를 참조하세요.

Azure Information Protection으로 마이그레이션하면 이전에 보호된 콘텐츠에 대한 액세스 권한을 잃지 않으므로 콘텐츠의 보호를 해제하거나 다시 보호할 필요가 없습니다. AD RMS로 보호된 문서 및 메일은 AD RMS의 프로비전을 해제한 후에도 여전히 열 수 있습니다.

Azure Information Protection으로 마이그레이션하기로 결정했거나 현재 AD RMS 배포를 사용할 때의 제한 사항을 받아들이기로 한 경우 먼저, Azure Rights Management 서비스가 비활성화되어 있는지 확인해야 합니다. 자세한 지침은 다음 중 해당하는 시나리오의 단계를 따르세요.

- [Azure Rights Management가 포함된 구독을 2018년 2월 중 또는 그 이후에 구매했습니다](#your-subscription-was-purchased-during-or-after-february-2018).

- [구독을 2018년 2월 이전 또는 2월 중에 구매했으며, Exchange Online을 사용하고 있습니다](#your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online).

- [Azure Portal에서 Azure Information Protection 정책을 구성할 때 보호를 활성화하는 옵션이 표시됩니다.](#you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection)


## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>2018년 2월 또는 그 이후에 구독을 구매했습니다.

이제 2018년 2월부터 Azure Information Protection을 포함하는 새 구독은 기본적으로 Azure Rights Management 서비스를 활성화합니다. 이 서비스가 자동으로 활성화되는데 AD RMS(Active Directory Rights Management Services)도 사용하는 경우 이 조합은 호환되지 않으므로 가능한 한 빨리 Azure Rights Management 서비스를 비활성화하는 것이 중요합니다. 

### <a name="step-1-deactivate-azure-rights-management"></a>1단계: Azure Rights Mangement 비활성화
Azure Rights Management를 비활성화하려면 다음 절차 중 하나를 사용하세요.

> [!TIP]
> 또한 Windows PowerShell cmdlet, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm)을 사용하여 Azure Rights Management 서비스를 비활성화할 수도 있습니다.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Office 365 관리 센터에서 권한 관리를 비활성화하려면

1. Office 365 관리자를 위한 [Rights Management 페이지](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx)로 이동합니다.
    
    로그인하라는 메시지가 나타나면 Office 365에 대한 전역 관리자 계정을 사용합니다.

2. **Rights Management** 페이지에서 **비활성화**를 클릭합니다.

3.  **Rights Management를 비활성화하시겠습니까?** 라는 프롬프트가 표시되면 **비활성화**를 클릭합니다.

이제 **Rights Management가 활성화되지 않았습니다.** 가 표시되고 활성화 옵션이 나타납니다.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Azure 포털에서 Rights Management를 비활성화하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.
    
    이전에 Azure Information Protection 블레이드에 액세스한 적이 없는 경우 이 블레이드를 포털에 추가하기 위한 일회성 [추가 단계](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time)를 참조하세요.

2. 메뉴 옵션에서 **보호 활성화**를 선택합니다. 

3.  **Azure Information Protection - 보호 활성화** 블레이드에서 **비활성화**를 선택합니다. **예**를 선택하여 확인합니다.

정보 표시줄에 **비활성화가 성공적으로 완료됨**이 표시되고 **비활성화**는 이제 **활성화**로 바뀝니다. 

### <a name="step-2-start-planning-for-migration"></a>2단계: 마이그레이션 계획 시작

마이그레이션 지침: [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.


## <a name="your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online"></a>구독을 2018년 2월 이전 또는 2월 중에 구매했으며, Exchange Online을 사용하고 있습니다.

Microsoft가 Azure Rights Management 또는 Azure Information Protection이 포함된 구독에 대해 Azure Rights Management 서비스를 활성화하기 시작했으며, 테넌트가 Exchange Online을 사용하고 있습니다. 이러한 테넌트의 경우 2018년 8월 1일에 자동 활성화가 롤아웃되기 시작합니다.

서비스가 자동으로 활성화되었는데 AD RMS도 사용하는 경우 이 조합은 호환되지 않으므로 테넌트가 자동 서비스 업데이트에서 옵트아웃되는 것이 중요합니다. 

### <a name="step-1-opt-out-from-the-automatic-service-update"></a>1단계: 자동 서비스 업데이트에서 옵트아웃

다음 [Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration) Exchange Online PowerShell 명령을 사용합니다. `Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false`

[추가 정보](https://support.office.com/article/protection-features-in-azure-information-protection-rolling-out-to-existing-office-365-tenants-7ad6f58e-65d7-4c82-8e65-0b773666634d) 

### <a name="step-2-start-planning-for-migration"></a>2단계: 마이그레이션 계획 시작

마이그레이션 지침: [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.


## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Azure Information Protection을 구성할 때 보호를 활성화하는 옵션이 표시됩니다.

**Azure Information Protection - 보호 활성화** 블레이드에는 Azure Rights Management 서비스를 활성화하는 옵션이 있습니다.  

AD RMS도 사용하는 경우 **활성화** 옵션을 선택하지 않아야 합니다. Azure Rights Management 서비스가 활성화되지 않은 경우에도 분류만 적용되는 레이블을 위해 Azure Information Protection을 사용할 수 있습니다. 데이터 보호를 포함하지 않는 특수 기본 정책이 생성되고 해당 구성 옵션은 Azure Rights Management 서비스를 활성화할 때까지 사용할 수 없는 상태를 유지합니다.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>1단계: 분류 및 레이블 지정을 위한 Azure Information Protection 정책 구성 - 보호 없음

**Azure Information Protection - 레이블** 블레이드에서 데이터 보호 옵션이 포함되지 않은 레이블을 확인하고 구성합니다. 레이블 및 정책 설정을 구성하는 방법에 대한 자세한 내용은 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.

### <a name="step-2-start-planning-for-migration"></a>2단계: 마이그레이션 계획 시작

마이그레이션 지침: [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

### <a name="step-3-configure-labels-for-protection"></a>3단계: 보호를 위한 레이블 구성

마이그레이션 프로세스의 일부로서 Azure Rights Management 서비스를 활성화한 후 데이터 보호를 위한 레이블을 구성할 수 있습니다. 하지만 사용자를 한번에 마이그레이션하는 경우 보호를 적용하는 레이블의 범위가 마이그레이션된 사용자에게만 적용되는지 확인합니다.


