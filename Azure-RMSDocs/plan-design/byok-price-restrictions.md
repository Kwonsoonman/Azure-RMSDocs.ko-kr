---
# required metadata

title: BYOK 가격 및 제한 사항 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# BYOK 가격 및 제한 사항

IT에서 관리하는 Azure 구독이 있는 조직은 추가 요금 없이 BYOK를 사용하고 사용 현황을 기록할 수 있습니다. 개인용 RMS를 사용하는 조직은 BYOK 및 로깅 기능을 사용할 수 없는데, 이러한 조직에는 이러한 기능을 구성하는 테넌트 관리자가 없기 때문입니다.


> [!NOTE]
> 개인용 RMS에 대한 자세한 내용은 [개인용 RMS 및 Azure 권한 관리](../understand-explore/rms-for-individuals.md)를 참조하세요.

![](../media/RMS_BYOK_noExchange.png)

BYOK 및 로깅 기능은 Azure RMS와 통합된 모든 응용 프로그램에서 원활하게 작동합니다. 이러한 응용 프로그램으로는 SharePoint Online과 같은 클라우드 서비스, Exchange 및 SharePoint를 실행하고 RMS 커넥터를 통해 Azure RMS와 작동하는 온-프레미스 서버 및 Office 2013과 같은 클라이언트 응용 프로그램이 있습니다. Azure RMS에 대한 요청을 만드는 응용 프로그램에 관계없이 키 사용 현황 로그를 얻을 수 있습니다.

그러나 한 가지 예외가 있습니다. 현재 **Azure RMS BYOK는 Exchange Online과 호환되지 않습니다**.  Exchange Online을 사용하려는 경우 Microsoft가 키를 생성 및 관리하는 기본 키 관리 모드에서 Azure RMS를 배포하는 것이 좋습니다. 예를 들어 Exchange Online이 Azure RMS BYOK를 지원하는 경우 나중에 BYOK를 이동하는 옵션이 제공됩니다. 그러나 이 옵션이 표시될 때까지 기다릴 수 없는 경우 다른 방법은 BYOK를 사용하여 Azure RMS를 배포하는 것입니다. 이 경우 Exchange Online에 대한 RMS 기능이 감소합니다(보호되지 않는 전자 메일 및 보호되지 않는 첨부 파일은 그대로 완전하게 기능함).

-   Outlook Web Access의 보호된 전자 메일 또는 보호된 첨부 파일은 표시할 수 없습니다.

-   Exchange ActiveSync IRM을 사용하는 모바일 장치의 보호된 전자 메일은 표시할 수 없습니다.

-   전송 암호 해독(예: 맬웨어 검사) 및 저널 암호 해독은 가능하지 않으므로 보호된 전자 메일 및 보호된 첨부 파일이 생략됩니다.

-   IRM 정책을 적용하는 전송 보호 규칙 및 DLP(데이터 손실 방지)는 가능하지 않으므로 이러한 방법을 사용하여 RMS 보호를 적용할 수 없습니다.

-   보호된 전자 메일에 대한 서버 기반 검색은 가능하지 않으므로 보호된 전자 메일이 생략됩니다.

Exchange Online에 대한 RMS 기능이 축소되는 Azure RMS BYOK를 사용할 경우 RMS는 Windows 및 Mac에서 Outlook의 전자 메일 클라이언트 및 Exchange ActiveSync IRM을 사용하지 않는 다른 전자 메일 클라이언트에서 작동합니다.

AD RMS에서 Azure RMS로 마이그레이션하는 경우 TPD(신뢰할 수 있는 게시 도메인)로서 Exchange Online으로 키를 가져왔을 것입니다(Azure RMS BYOK와는 별도로 Exchange 용어로는 BYOK로 지칭). 이 시나리오에서는 템플릿 및 정책 충돌을 피하기 위해 Exchange Online에서 TPD를 제거해야 합니다. 자세한 내용은 Exchange Online cmdlet 라이브러리의 [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx)을 참조하세요.

경우에 따라 Exchange Online에 대한 Azure RMS BYOK 예외가 실제로 문제가 되지 않습니다. 예를 들어 BYOK 및 로깅 기능이 필요한 조직은 온-프레미스에서 데이터 응용 프로그램(Exchange, SharePoint, Office)을 실행하고 온-프레미스 AD RMS에서 쉽게 사용할 수 없는 기능(예: 다른 회사와의 공동 작업 및 모바일 클라이언트로부터의 액세스)에 Azure RMS를 사용하기 때문입니다. BYOK와 로깅 기능 모두 이 시나리오에서 잘 작동하므로 조직은 Azure RMS 구독에 대한 완전한 제어권을 가질 수 있습니다.

## 다음 단계

고유한 키를 관리하기로 결정한 경우 [Azure 권한 관리 테넌트 키 구현](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key)으로 이동합니다.

Microsoft에서 테넌트 키를 관리하는 기본 구성을 유지하기로 결정한 경우 Azure 권한 관리 테넌트 키 계획 및 구현 문서에서 [다음 단계](plan-implement-tenant-key.md#next-steps) 섹션을 참조하세요.



<!--HONumber=Apr16_HO3-->

