---
title: "Azure RMS 및 AD RMS를 위한 환경 준비"
description: "Azure Rights Management가 있고 AD RMS가 배포되어 있는 상황에 대한 지침입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6d7a1d2ed61e1d12d6ca50db50c5b516e6e4f54e
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>AD RMS(Active Directory Rights Management Services)를 갖고 있는 경우 Azure Rights Management를 위한 환경 준비

>*적용 대상: Azure Information Protection, Office 365*

AD RMS(Active Directory Rights Management Services)를 이미 사용 중이고 다음 시나리오가 적용되는 경우 이 중요 지침을 살펴보아야 합니다.

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Azure Information Protection을 구성할 때 보호를 활성화하는 옵션이 표시됩니다.

**Azure Information Protection - 보호 활성화** 블레이드에는 Azure RMS(Azure Rights Management) 서비스를 활성화하는 옵션이 있습니다. 

AD RMS(Azure Rights Management service)도 사용하려면 **활성화** 옵션을 선택하지 마세요. AD RS가 있는 상태에서 Azure Rights Management를 활성화하면 호환되지 않습니다. 이 시나리오는 지원되지 않으며 신뢰할 수 없는 결과로 이어집니다. 따라서 지금은 Azure Rights Management를 활성화하면 안 됩니다. 

AD RMS에서 Azure Rights Management 서비스로 컴퓨터를 이동할 준비가 완료되면 마이그레이션 프로세스를 시작할 수 있습니다. 마이그레이션 단계 중에는 서비스를 활성화하는 과정이 있는데, 이 과정은 AD RMS에서 Azure Rights Management 서비스로 구성 정보를 내보낸 후에 수행합니다. 이 프로세스를 통해 AD RMS로 보호되는 문서와 이메일을 계속 열어 둘 수 있습니다.

Azure Rights Management 서비스가 활성화되지 않아도 분류에만 적용되는 레이블에 Azure Information Protection을 계속 사용할 수 있습니다. 데이터 보호를 포함하지 않는 특별한 기본 정책이 생성되며 구성 옵션은 Azure Rights Management 서비스가 활성화될 때까지 사용할 수 없습니다.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>1단계: 보호 없이 분류 및 레이블 지정에 대해서만 Azure Information Protection 정책 구성

처음에 나오는 **Azure Information Protection** 블레이드에서 **글로벌 정책**을 선택하여 데이터 보호에 대한 옵션이 포함되지 않는 기본 정책을 살펴보고 구성합니다. 자세한 내용은 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.

### <a name="step-2-start-planning-for-migration"></a>2단계: 마이그레이션 계획 수립 시작

마이그레이션 지침 [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 따릅니다.

### <a name="step-3-start-to-configure-labels-for-protection"></a>3단계: 보호에 대한 레이블 구성 시작

마이그레이션 프로세스의 일부분으로 Azure Rights Management 서비스를 활성화한 후에는 데이터 보호에 대한 레이블을 구성할 수 있습니다. 하지만 사용자를 일괄 처리로 마이그레이션하는 경우 보호를 적용하는 레이블의 [범위](configure-policy-scope.md)를 마이그레이션된 사용자로 지정해야 합니다.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


