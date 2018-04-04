---
title: Azure RMS 및 AD RMS를 위한 환경 준비
description: Azure Rights Management를 AD RMS와 함께 배포한 경우 지침입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a233ddab67832e2de59b1fc0727296a8f3017db7
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>AD RMS(Active Directory Rights Management Services)도 배포했을 때 Azure Rights Management를 위한 환경 준비

>*적용 대상:[ Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

이미 AD RMS(Active Directory Rights Management Services)를 사용하고 있고 다음 시나리오 중 하나가 적용될 때 중요한 지침:

- [Azure Rights Management가 포함된 구독은 2018년 2월 중 또는 그 이후에 구매된 것입니다](#your-subscription-was-purchased-during-or-after-february-2018).

- [Azure Portal에서 Azure Information Protection 정책을 구성할 때 보호를 활성화하는 옵션이 표시됩니다.](#you-see-an-option-to activate-azure-rights-management-when-you-configure-azure-information-protection)

## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>2018년 2월 또는 그 이후에 구독을 구매했습니다.

이제 2018년 2월부터 Azure Information Protection을 포함하는 새 구독은 기본적으로 Azure Rights Management 서비스를 활성화합니다. 이 서비스가 사용자에게 자동으로 활성화되고 AD RMS(Active Directory Rights Management Services)도 사용하는 경우 이 조합은 호환되지 않습니다. 추가 단계가 없으면 일부 컴퓨터에서 Azure Rights Management 서비스를 자동으로 시작하고 AD RMS 클러스터에 연결할 수도 있습니다. 이 시나리오는 지원되지 않으며 불안정한 결과를 야기하므로 가능한 한 Azure Rights Management를 비활성화하는 것이 중요합니다. 

AD RMS에서 Azure Rights Management 서비스로 컴퓨터를 이동할 준비가 되면 마이그레이션 프로세스를 시작할 수 있습니다. 마이그레이션 단계 중 하나는 서비스를 다시 활성화하는 것이지만 AD RMS에서 Azure Rights Management 서비스로 구성 정보를 내보낸 후 이 단계를 수행합니다. 이 순서는 AD RMS로 보호되는 문서와 이메일을 여전히 열 수 있도록 합니다.

첫 번째 단계는 Azure Rights Management 서비스를 비활성화하는 것입니다.

### <a name="step-1-deactivate-azure-rights-management"></a>1단계: Azure Rights Mangement 비활성화
[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 비활성화하려면 다음 절차 중 하나를 사용하세요.

> [!TIP]
> Windows PowerShell cmdlet [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx)을 사용하여 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]를 비활성화할 수도 있습니다.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Office 365 관리 센터에서 권한 관리를 비활성화하려면

1. Office 365 관리자를 위한 [Rights Management 페이지](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx)로 이동합니다.
    
    로그인하라는 메시지가 나타나면 Office 365에 대한 전역 관리자 계정을 사용합니다.

2. **Rights Management** 페이지에서 **비활성화**를 클릭합니다.

3.  **Rights Management를 비활성화하시겠습니까?**라는 프롬프트가 표시되면 **비활성화**를 클릭합니다.

이제 **Rights Management가 활성화되지 않았습니다.** 가 표시되고 활성화 옵션이 나타납니다.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Azure 포털에서 Rights Management를 비활성화하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.
    
    이전에 Azure Information Protection 블레이드에 액세스한 적이 없는 경우 이 블레이드를 포털에 추가하기 위한 일회성 [추가 단계](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time)를 참조하세요.

2. 초기 **Azure Information Protection** 블레이드에서 **보호 활성화**를 선택합니다. 

3.  **Azure Information Protection - 보호 활성화** 블레이드에서 **비활성화**를 선택합니다. **예**를 선택하여 확인합니다.

정보 표시줄에 **비활성화가 성공적으로 완료됨**이 표시되고 **비활성화**는 이제 **활성화**로 바뀝니다. 

### <a name="step-2-start-planning-for-migration"></a>2단계: 마이그레이션 계획 시작

마이그레이션 지침: [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Azure Information Protection을 구성할 때 보호를 활성화하는 옵션이 표시됩니다.

**Azure Information Protection - 보호 활성화** 블레이드에는 Azure RMS(Azure Rights Management 서비스)를 활성화하는 옵션이 있습니다.  

AD RMS(Active Directory Rights Management Services)도 사용하는 경우 **활성화** 옵션을 선택하지 마세요. AD RS도 있는 경우 Azure Rights Management를 활성화하면 호환되지 않습니다. 이 시나리오는 지원되지 않으며 불안정한 결과를 야기하므로 지금은 Azure Rights Management를 활성화하지 않는 것이 중요합니다.  

AD RMS에서 Azure Rights Management 서비스로 컴퓨터를 이동할 준비가 되면 마이그레이션 프로세스를 시작할 수 있습니다. 마이그레이션 단계 중 하나인 서비스 활성화는 AD RMS에서 Azure Rights Management 서비스로 구성 정보를 내보낸 후 수행해야 합니다. 이 프로세스는 AD RMS로 보호되는 문서와 메일을 여전히 열 수 있도록 합니다. 

Azure Rights Management 서비스가 활성화되지 않은 경우에도 분류만 적용되는 레이블을 위해 Azure Information Protection을 사용할 수 있습니다. 데이터 보호를 포함하지 않는 특수 기본 정책이 생성되고 해당 구성 옵션은 Azure Rights Management 서비스를 활성화할 때까지 사용할 수 없는 상태를 유지합니다.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>1단계: 분류 및 레이블 지정을 위한 Azure Information Protection 정책 구성 - 보호 없음

초기 **Azure Information Protection** 블레이드에서 **글로벌 정책**을 선택하여 데이터 보호 옵션을 포함하지 않는 기본 정책을 보고 구성합니다. 자세한 내용은 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.

### <a name="step-2-start-planning-for-migration"></a>2단계: 마이그레이션 계획 시작

마이그레이션 지침: [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

### <a name="step-3-start-to-configure-labels-for-protection"></a>3단계: 보호를 위한 레이블 구성 시작

마이그레이션 프로세스의 일부로서 Azure Rights Management 서비스를 활성화한 후 데이터 보호를 위한 레이블을 구성할 수 있습니다. 하지만 사용자를 한번에 마이그레이션하는 경우 보호를 적용하는 레이블의 범위가 마이그레이션된 사용자에게만 적용되는지 확인합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

