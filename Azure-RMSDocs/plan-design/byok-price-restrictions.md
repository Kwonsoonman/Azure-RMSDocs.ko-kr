---
title: "BYOK 가격 및 제한 사항 - Azure Information Protection"
description: "BYOK(&quot;Bring Your Own Key&quot;)라고도 하는 고객 관리 키를 Azure RMS에서 사용할 때의 제한 사항에 대해 알아봅니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: c05521faed2cd8a7f9d32d81cd6899161e858153
ms.lasthandoff: 02/24/2017


---

# <a name="byok-pricing-and-restrictions"></a>BYOK 가격 및 제한 사항

>*적용 대상: Azure Information Protection, Office 365*


Azure Information Protection을 포함하는 구독이 있는 조직은 Azure Information Protection 테넌트를 구성하여 추가 요금 없이 고객 관리 키(BYOK)를 사용하고 [사용 현황을 기록](../deploy-use/log-analyze-usage.md)할 수 있습니다. 

키는 Azure Key Vault에 저장해야 합니다. Azure Key Vault는 유료(또는 평가판) Azure 구독이 필요하며, Azure Key Vault Premium 서비스 계층을 사용하여 HSM 보호된 키를 지원해야 합니다. Azure Key Vault의 HSM 보호된 키를 사용하면 월별 요금이 발생합니다. 자세한 내용은 [Azure Key Vault Pricing(Azure 주요 자격 증명 모음 가격)](https://azure.microsoft.com/en-us/pricing/details/key-vault/) 페이지를 참조하세요.

Azure Information Protection 테넌트 키에 대해 Azure Key Vault를 사용하는 경우, Azure Rights Management Service에서만 사용할 수 있도록 전용 구독과 함께 이 키에 대한 전용 Key Vault를 사용하는 것이 좋습니다. 

## <a name="benefits-of-using-azure-key-vault"></a>Azure Key Vault를 사용할 경우의 이점

Azure Information Protection 사용 현황 로깅 사용과 함께, Azure Rights Management Service에서만 이 키를 사용하고 있음을 독립적으로 모니터링하기 위해 [Azure Key Vault 로깅](https://azure.microsoft.com/documentation/articles/key-vault-logging/)을 사용하여 상호 참조할 수 있습니다. 필요한 경우 Key Vault에 대한 권한을 제거하여 키에 대한 액세스 권한을 즉시 취소할 수 있습니다.

Azure Information Protection 테넌트 키에 대해 Azure Key Vault를 사용하는 기타 이점은 다음과 같습니다.

- Azure Key Vault는 여러 클라우드 기반 서비스 및 암호화를 사용하는 온-프레미스 서비스에 대해 일관된 관리 솔루션을 제공하는 중앙 집중식 키 관리 솔루션을 제공합니다.

- Azure Key Vault는 PowerShell, CLI, REST API, Azure Portal 등 키 관리에 대해 여러 기본 제공 인터페이스를 지원합니다. 모니터링처럼 특정 작업에 최적화된 기능을 제공하기 위해 다른 서비스 및 도구가 Key Vault와 통합되었습니다. 예를 들어 Operations Management Suite의 로그 분석을 통해 키 사용량 로그를 분석하고, 지정한 기준을 충족할 경우 경고를 설정하는 등 여러 가지 작업을 할 수 있습니다.

- Azure Key Vault는 최상의 보안 방법으로써 역할 구분을 제공합니다. Azure Information Protection 관리자는 데이터 분류 및 보호 관리에 집중할 수 있으며, Azure Key Vault 관리자는 암호화 키 관리 및 보안이나 준수를 요구하는 특별한 정책 관리에 집중할 수 있습니다.

- 일부 조직에는 마스터 키가 있어야 하는 제한 사항이 있습니다. Azure Key Vault는 서비스가 여러 Azure 지역에서 제공되기 때문에 마스터 키를 저장하는 높은 수준의 제어를 제공합니다. 현재 28개 Azure 지역 중에서 선택할 수 있으며 이 숫자는 계속 늘어나고 있습니다. 자세한 내용은 Azure 사이트의 [지역별 사용 가능한 제품](https://azure.microsoft.com/regions/services/) 페이지를 참조하세요.

키 관리 외에도 Azure Key Vault는 보안 관리자에게 암호화를 사용하는 다른 서비스 및 응용 프로그램의 인증서 및 암호를 저장하고 액세스하고 관리하는 동일한 관리 환경을 제공합니다. 

Azure Key Vault에 대한 자세한 내용은 [Azure Key Vault란?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/)을 참조하고, 최신 정보는 [Azure Key Vault 팀 블로그](https://blogs.technet.microsoft.com/kv/)를 방문하여 다른 서비스에서 이 기술을 어떻게 사용하는지 알아보세요.


## <a name="restrictions-when-using-byok"></a>BYOK 사용 시 제한 사항

개인용 RMS를 사용하여 무료 계정에 등록한 사용자가 있는 경우 이 구성에는 이러한 기능을 구성할 테넌트 관리자가 없기 때문에 BYOK 또는 사용 현황 로깅을 사용할 수 없습니다.


> [!NOTE]
> 개인용 RMS에 대한 자세한 내용은 [개인용 RMS 및 Azure 권한 관리](../understand-explore/rms-for-individuals.md)를 참조하세요.

![BYOK에서는 Exchange Online을 지원하지 않습니다.](../media/RMS_BYOK_noExchange.png)

BYOK 및 사용 현황 로깅 기능은 Azure Information Protection에서 사용하는 Azure RMS 서비스(Azure RMS)와 통합된 모든 응용 프로그램에서 원활하게 작동합니다. 이러한 응용 프로그램으로는 SharePoint Online과 같은 클라우드 서비스, Exchange 및 SharePoint를 실행하고 RMS 커넥터를 통해 Azure RMS와 작동하는 온-프레미스 서버, Office 2016 및 Office 2013과 같은 클라이언트 응용 프로그램이 있습니다. Azure RMS에 대한 요청을 만드는 응용 프로그램에 관계없이 키 사용 현황 로그를 얻을 수 있습니다.

그러나 한 가지 예외가 있습니다. 현재 **Azure RMS BYOK는 Exchange Online과 호환되지 않습니다**. Exchange Online을 사용하려는 경우 Microsoft가 키를 생성 및 관리하는 기본 키 관리 모드에서 Azure RMS를 배포하는 것이 좋습니다. 예를 들어 Exchange Online이 Azure RMS BYOK를 지원하는 경우 나중에 BYOK를 이동하는 옵션이 제공됩니다. 그러나 이 옵션이 표시될 때까지 기다릴 수 없는 경우 다른 방법은 BYOK를 사용하여 Azure RMS를 배포하는 것입니다. 이 경우 Exchange Online에 대한 RMS 기능이 감소합니다(보호되지 않는 메일 및 보호되지 않는 첨부 파일은 그대로 완전하게 기능함).

-   Outlook Web Access의 보호된 메일 또는 보호된 첨부 파일은 표시할 수 없습니다.

-   Exchange ActiveSync IRM을 사용하는 모바일 장치의 보호된 메일은 표시할 수 없습니다.

-   전송 암호 해독(예: 맬웨어 검사) 및 저널 암호 해독은 가능하지 않으므로 보호된 메일 및 보호된 첨부 파일이 생략됩니다.

-   IRM 정책을 적용하는 전송 보호 규칙 및 DLP(데이터 손실 방지)는 가능하지 않으므로 이러한 방법을 사용하여 RMS 보호를 적용할 수 없습니다.

-   보호된 메일에 대한 서버 기반 검색은 가능하지 않으므로 보호된 메일이 생략됩니다.

Exchange Online에 대한 RMS 기능이 축소되는 Azure RMS BYOK를 사용할 경우 RMS는 Windows 및 Mac에서 Outlook의 메일 클라이언트 및 Exchange ActiveSync IRM을 사용하지 않는 다른 메일 클라이언트에서 작동합니다.

AD RMS에서 Azure RMS로 마이그레이션하는 경우 TPD(트러스트된 게시 도메인)로서 Exchange Online으로 키를 가져왔을 것입니다(Azure 주요 자격 증명 모음 BYOK와는 별도로 Exchange 용어로는 BYOK로 지칭). 이 시나리오에서는 템플릿 및 정책 충돌을 피하기 위해 Exchange Online에서 TPD를 제거해야 합니다. 자세한 내용은 Exchange Online cmdlet 라이브러리의 [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx)을 참조하세요.

경우에 따라 Exchange Online에 대한 Azure RMS BYOK 예외가 실제로 문제가 되지 않습니다. 예를 들어 BYOK 및 로깅 기능이 필요한 조직은 온-프레미스에서 데이터 응용 프로그램(Exchange, SharePoint, Office)을 실행하고 온-프레미스 AD RMS에서 쉽게 사용할 수 없는 기능(예: 다른 회사와의 공동 작업 및 모바일 클라이언트로부터의 액세스)에 Azure RMS를 사용하기 때문입니다. BYOK와 로깅 기능 모두 이 시나리오에서 잘 작동하므로 조직은 Azure RMS 구독에 대한 완전한 제어권을 가질 수 있습니다.

## <a name="next-steps"></a>다음 단계

고유한 키를 관리하기로 결정한 경우 [Azure 권한 관리 테넌트 키 구현](plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key)으로 이동합니다.

Microsoft에서 테넌트 키를 관리하는 기본 구성을 유지하기로 결정한 경우 Azure 권한 관리 테넌트 키 계획 및 구현 문서에서 [다음 단계](plan-implement-tenant-key.md#next-steps) 섹션을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

