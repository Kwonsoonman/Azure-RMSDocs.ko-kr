---
title: "Azure RMS 및 AD RMS를 위한 환경 준비"
description: "Azure Rights Management를 AD RMS와 함께 배포한 경우 지침입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b20bbc1fe0de90b9b0151098e1b77d3c7a98c431
ms.sourcegitcommit: e9a24fc5303b21f5eeebf16afed44db0d163ac77
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2017
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>AD RMS(Active Directory Rights Management Services)도 배포했을 때 Azure Rights Management를 위한 환경 준비

>*적용 대상: Azure Information Protection, Office 365*

이미 AD RMS(Active Directory Rights Management Services)를 사용 중이고 다음 시나리오가 적용될 때 중요한 지침:

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Azure Information Protection을 구성할 때 보호를 활성화하는 옵션이 표시됩니다.

**Azure Information Protection - 보호 활성화** 블레이드에는 Azure RMS(Azure Rights Management 서비스)를 활성화하는 옵션이 있습니다. 

AD RMS(Active Directory Rights Management Services)도 사용하는 경우 **활성화** 옵션을 선택하지 마세요. AD RS도 있는 경우 Azure Rights Management를 활성화하면 호환되지 않습니다. 이 시나리오는 지원되지 않으며 불안정한 결과를 야기하므로 지금은 Azure Rights Management를 활성화하지 않는 것이 중요합니다. 

AD RMS에서 Azure Rights Management 서비스로 컴퓨터를 이동할 준비가 되면 마이그레이션 프로세스를 시작할 수 있습니다. 마이그레이션 단계 중 하나인 서비스 활성화는 AD RMS에서 Azure Rights Management 서비스로 구성 정보를 내보낸 후 수행해야 합니다. 이 프로세스는 AD RMS로 보호되는 문서와 메일을 여전히 열 수 있도록 합니다.

Azure Rights Management 서비스가 활성화되지 않은 경우에도 분류만 적용되는 레이블을 위해 Azure Information Protection을 사용할 수 있습니다. 데이터 보호를 포함하지 않는 특수 기본 정책이 생성되고 해당 구성 옵션은 Azure Rights Management 서비스를 활성화할 때까지 사용할 수 없는 상태를 유지합니다.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>1단계: 분류 및 레이블 지정을 위한 Azure Information Protection 정책 구성 - 보호 없음

초기 **Azure Information Protection** 블레이드에서 **글로벌 정책**을 선택하여 데이터 보호 옵션을 포함하지 않는 기본 정책을 보고 구성합니다. 자세한 내용은 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.

### <a name="step-2-start-planning-for-migration"></a>2단계: 마이그레이션 계획 시작

마이그레이션 지침 수행: [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>3단계: 보호를 위한 레이블 구성 시작

마이그레이션 프로세스의 일부로서 Azure Rights Management 서비스를 활성화한 후 데이터 보호를 위한 레이블을 구성할 수 있습니다. 하지만 사용자를 한 번에 마이그레이션하는 경우 보호를 적용하는 레이블 [범위](configure-policy-scope.md)가 마이그레이션된 사용자로 한정되도록 해야 합니다.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


