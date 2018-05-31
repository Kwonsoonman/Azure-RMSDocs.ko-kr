---
title: BYOK 가격 및 제한 사항 - Azure Information Protection
description: BYOK(“Bring Your Own Key”)라고도 하는 고객 관리 키를 Azure Information Protection에서 사용할 때의 제한 사항에 대해 알아봅니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/18/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f5380dc364255fd085c82fd9c0a834afea368c97
ms.sourcegitcommit: 10f530fa1a43928581da4830a32f020c96736bc8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2018
ms.locfileid: "34402152"
---
# <a name="byok-pricing-and-restrictions"></a>BYOK 가격 및 제한 사항

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Azure Information Protection을 포함하는 구독이 있는 조직은 Azure Information Protection 테넌트를 구성하여 고객 관리 키(BYOK)를 사용하고 [사용 현황을 기록](../deploy-use/log-analyze-usage.md)할 수 있습니다. 

키는 Azure 구독이 필요한 Azure Key Vault에 저장해야 합니다. HSM 보호 키를 사용하려면 Azure Key Vault 프리미엄 서비스 계층을 사용해야 합니다. Azure 주요 자격 증명 모음의 키를 사용하면 월별 요금이 발생합니다. 자세한 내용은 [Azure Key Vault Pricing(Azure 주요 자격 증명 모음 가격)](https://azure.microsoft.com/pricing/details/key-vault/) 페이지를 참조하세요.

Azure Information Protection 테넌트 키에 대해 Azure Key Vault를 사용하는 경우, Azure Rights Management Service에서만 사용할 수 있도록 이 키에 대한 전용 Key Vault를 사용하는 것이 좋습니다. 이 구성은 다른 서비스의 호출이 Azure Rights Management 서비스에 대한 응답 시간을 단축시킬 수 있는 키 자격 증명 모음에 대한 [서비스 제한](/azure/key-vault/key-vault-service-limits)을 초과하지 않도록 합니다.  

또한 일반적으로 Azure Key Vault를 사용하는 각 서비스마다 키 관리 요구 사항이 다르기 때문에 잘못 구성하지 않도록 이 키 자격 증명 모음에 대해 별도로 Azure 구독에 가입하는 것이 좋습니다. 

그러나 Azure Key Vault를 사용하는 다른 서비스와 Azure 구독을 공유하려는 경우 구독이 공통된 관리자 집합을 공유하는지 확인하세요. 이 주의 사항은 구독을 사용하는 관리자가 액세스할 수 있는 모든 키를 잘 이해하고 있기 때문에 잘못 구성할 가능성이 낮음을 의미합니다. 예를 들어 Azure Information Protection 테넌트 키 관리자가 Office 365 고객 키 및 CRM 온라인에 대한 키를 관리하는 사람과 동일한 경우 Azure 구독을 공유합니다. 그러나 고객 키 또는 CRM 온라인에 대한 키를 관리하는 관리자가 Azure Information Protection 테넌트 키를 관리하는 사람과 다른 경우 Azure Information Protection를 위해 Azure 구독을 공유하지 않는 것이 좋습니다.

## <a name="benefits-of-using-azure-key-vault"></a>Azure Key Vault를 사용할 경우의 이점

Azure Information Protection 사용 현황 로깅 사용과 함께, Azure Rights Management Service에서만 이 키를 사용하고 있음을 독립적으로 모니터링하기 위해 [Azure Key Vault 로깅](https://azure.microsoft.com/documentation/articles/key-vault-logging/)을 사용하여 상호 참조할 수 있습니다. 필요한 경우 Key Vault에 대한 권한을 제거하여 키에 대한 액세스 권한을 즉시 취소할 수 있습니다.

Azure Information Protection 테넌트 키에 대해 Azure Key Vault를 사용하는 기타 이점은 다음과 같습니다.

- Azure Key Vault는 여러 클라우드 기반 서비스 및 암호화를 사용하는 온-프레미스 서비스에 대해 일관된 관리 솔루션을 제공하는 중앙 집중식 키 관리 솔루션을 제공합니다.

- Azure Key Vault는 PowerShell, CLI, REST API, Azure Portal 등 키 관리에 대해 여러 기본 제공 인터페이스를 지원합니다. 모니터링처럼 특정 작업에 최적화된 기능을 제공하기 위해 다른 서비스 및 도구가 Key Vault와 통합되었습니다. 예를 들어 Operations Management Suite의 로그 분석을 통해 키 사용량 로그를 분석하고, 지정한 기준을 충족할 경우 경고를 설정하는 등 여러 가지 작업을 할 수 있습니다.

- Azure Key Vault는 최상의 보안 방법으로써 역할 구분을 제공합니다. Azure Information Protection 관리자는 데이터 분류 및 보호 관리에 집중할 수 있으며, Azure Key Vault 관리자는 암호화 키 관리 및 보안이나 준수를 요구하는 특별한 정책 관리에 집중할 수 있습니다.

- 일부 조직에는 마스터 키가 있어야 하는 제한 사항이 있습니다. Azure Key Vault는 서비스가 여러 Azure 지역에서 제공되기 때문에 마스터 키를 저장하는 높은 수준의 제어를 제공합니다. 현재 28개 Azure 지역 중에서 선택할 수 있으며 이 숫자는 계속 늘어나고 있습니다. 자세한 내용은 Azure 사이트의 [지역별 사용 가능한 제품](https://azure.microsoft.com/regions/services/) 페이지를 참조하세요.

키 관리 외에도 Azure Key Vault는 보안 관리자에게 암호화를 사용하는 다른 서비스 및 응용 프로그램의 인증서 및 암호를 저장하고 액세스하고 관리하는 동일한 관리 환경을 제공합니다. 

Azure Key Vault에 대한 자세한 내용은 [Azure Key Vault란?](/azure/key-vault/key-vault-whatis)을 참조하고, 최신 정보는 [Azure Key Vault 팀 블로그](https://cloudblogs.microsoft.com/kv/)를 방문하여 다른 서비스에서 이 기술을 어떻게 사용하는지 알아보세요.

## <a name="restrictions-when-using-byok"></a>BYOK 사용 시 제한 사항

BYOK 및 사용 현황 로깅 기능은 Azure Information Protection에서 사용하는 Azure Rights Management 서비스와 통합된 모든 응용 프로그램에서 원활하게 작동합니다. 여기에는 SharePoint Online과 같은 클라우드 서비스, RMS 커넥터를 사용하여 Azure Rights Management 서비스를 사용하는 Exchange 및 SharePoint를 실행하는 온-프레미스 서버 및 Office 2016 및 Office 2013과 같은 클라이언트 응용 프로그램이 있습니다. 어느 응용 프로그램이 Azure Rights Management 서비스에 요청을 하든 관계없이 키 사용 로그를 갖게 됩니다.

이전에 Azure RMS에서 TPD(트러스트된 게시 도메인)를 가져와서 Exchange Online IRM을 사용하도록 설정한 경우, [Azure Information Protection을 기반으로 구축된 새로운 Office 365 메시지 암호화 기능 설정](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)의 지침에 따라 Azure Information Protection용 BYOK 사용을 지원하는 Exchange Online의 새로운 기능을 사용하도록 설정하십시오.

## <a name="next-steps"></a>다음 단계

고유한 키를 관리하기로 한 경우 [Azure Information Protection 테넌트 키 구현](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key)으로 이동하세요.

Microsoft에서 테넌트 키를 관리하는 기본 구성을 유지하기로 한 경우 Azure Information Protection 테넌트 키 계획 및 구현 문서에서 [다음 단계](plan-implement-tenant-key.md#next-steps) 섹션을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
