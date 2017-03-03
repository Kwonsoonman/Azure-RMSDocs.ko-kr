---
title: "Azure Information Protection이란?"
description: "Azure Information Protection 서비스에 대해 간략하게 설명합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 7d5c759a6b7e206f30588926a8d480b50be20bc4
ms.lasthandoff: 02/24/2017


---

# <a name="what-is-azure-information-protection"></a>Azure Information Protection이란?

>*적용 대상: Azure Information Protection*

Azure Information Protection은 클라우드 기반 솔루션으로 조직에서 문서와 전자 메일을 분류하고 레이블을 지정하며 보호하는 데 도움이 됩니다. 이 기능은 규칙 및 조건을 정의하는 관리자는 자동으로, 사용자는 수동으로 수행할 수 있으며, 사용자가 권장 사항을 제공받은 경우에는 자동 또는 수동으로 수행할 수 있습니다. 

다음 그림은 Azure Information Protection의 실제 작동 방식 예를 보여 줍니다. 관리자는 중요한 데이터를 검색하는 데 필요한 규칙을 정의했습니다(이 경우 신용 카드 정보). 신용 카드 정보가 포함된 Word 문서를 저장할 때 관리자가 구성한 특정 레이블을 적용하여 문서를 분류하고, 선택적으로 보호하도록 권장하는 사용자 지정 도구 설명이 나타납니다. 

![Azure Information Protection에 권장되는 분류 예](../media/info-protect-recommend-callouts.png)

콘텐츠가 분류되고 나면(경우에 따라 보호됨) 해당 콘텐츠를 추적하고 제어할 수 있습니다. 데이터 흐름을 분석하여 비즈니스 통찰력을 얻고, 위험 행동을 검색하여 수정 작업을 수행하고, 문서에 대한 액세스를 추적하고, 데이터가 누출되거나 잘못 사용되지 않게 할 수 있습니다.

## <a name="how-labels-apply-classification"></a>레이블에서 분류를 적용하는 방법

Azure Information Protection 레이블을 사용하여 문서와 전자 메일을 분류할 수 있습니다. 이 작업을 수행하면 데이터가 저장된 위치나 데이터를 공유한 사용자가 누구인지와 관계없이 항상 분류를 식별할 수 있게 됩니다. 영구 레이블로는 머리글, 바닥글, 워터마크 등의 시각적 표시가 있습니다. 다른 서비스(예: 데이터 손실 방지 솔루션)에서 분류를 식별하고 적절한 조치를 취할 수 있도록 파일 및 전자 메일 머리글에 메타데이터가 일반 텍스트로 추가됩니다. 

예를 들어 다음 전자 메일 메시지는 “내부용"으로 분류됩니다. 이 레이블은 내부 사용을 위한 것으로 조직 외부로 전송하면 안 된다는 점을 받는 사람 모두에게 알리는 시각적 표시기로, 전자 메일 메시지에 바닥글로 추가됩니다. 이 레이블은 전자 메일 서비스에서 이 값을 검사하여 감사 항목을 만들거나 조직 외부로 전송되지 않도록 전자 메일 머리글에도 포함됩니다.

![Azure Information Protection 분류를 보여 주는 머리글 및 바닥글 예](../media/example-email-footer-header.png)


## <a name="how-data-is-protected"></a>데이터를 보호하는 방법

보호 기술에서는 *Azure Rights Management*(종종 Azure RMS로 축약됨)를 사용합니다. 이 기술은 다른 Microsoft 클라우드 서비스 및 응용 프로그램(Office 365, Azure Active Directory 등)과 통합되었습니다. 또한 기간 업무 응용 프로그램 및 소프트웨어 공급 업체의 정보 보호 솔루션이 온-프레미스에 있는지 아니면 클라우드에 있는지와 상관없이 해당 응용 프로그램 및 솔루션과 함께 사용할 수 있습니다.

이 보호 기술은 암호화, ID 및 권한 부여 정책을 사용합니다. 영구 레이블과 마찬가지로 Rights Management를 사용하여 적용된 보호 기능은 조직, 네트워크, 파일 서버, 응용 프로그램 내/외의 위치에 관계없이 문서와 전자 메일에 계속 적용됩니다. 이 정보 보호 솔루션은 데이터를 다른 사용자와 공유하는 경우에도 데이터에 대한 제어를 유지할 수 있도록 합니다.

예를 들어 조직 내의 사용자만 액세스할 수 있도록 보고서 문서 또는 판매 예측 스프레드시트를 구성할 수도 있고 해당 문서의 편집 가능 여부를 제어하거나, 읽기 전용으로 제한하거나 문서 인쇄를 차단할 수도 있습니다. 마찬가지로 전자 메일도 구성할 수 있으며 전체 회신 옵션 사용 또는 전자 메일 전달을 차단할 수 있습니다. *권한 관리 템플릿*을 사용하면 이러한 보호 작업을 단순화하고 간소화할 수 있습니다.

### <a name="rights-management-templates"></a>권한 관리 템플릿

Azure Rights Management 서비스를 활성화하면 바로&2;개의 기본 템플릿이 만들어져 데이터 액세스를 조직에 있는 사용자로 제한할 수 있습니다. 이러한 템플릿을 사용하여 즉시 조직에서 데이터가 누출되는 것을 방지할 수 있습니다. 또한 제한이 강화된 컨트롤을 적용하는 사용자 고유의 사용자 지정 템플릿을 구성하여 이러한 기본 템플릿을 보완할 수도 있습니다.

이러한 템플릿은 레이블 구성에 포함되어 특정 레이블이 문서(또는 전자 메일 메시지)에 적용되면 데이터는 모두 분류되며 자동으로 보호됩니다. 또한 Azure Rights Management를 지원하는 제품과 서비스에서 사용자나 관리자가 선택할 수도 있습니다.

이 예제에서는 Azure Portal에서 Azure Information Protection 정책을 구성할 때 레이블에 대한 템플릿을 선택하는 방법을 보여 줍니다.

![Azure Portal에서 템플릿을 선택하는 예](../media/info-protect-template-callout.png)

Exchange 관리 센터에서 동일한 템플릿을 선택하여 Azure Rights Management 기술을 지원하는 Exchange Online 전자 메일 흐름 규칙을 구성할 수 있습니다.

![Exchange Online용 템플릿을 선택하는 예](../media/templates-exchangeonline-callouts.png)

Azure Rights Management 보호에 대한 자세한 내용은 [Azure Rights Management란?](what-is-azure-rms.md)을 참조하세요.

## <a name="integration-with-end-user-workflows"></a>최종 사용자 워크플로와 통합

Azure Information Protection 클라이언트가 설치되면 Azure Information Protection은 최종 사용자의 기존 워크플로와 통합됩니다. 이 클라이언트는 첫 번째 그림에서 살펴본 대로 Office 응용 프로그램에 Information Protection 표시줄을 설치합니다. 동일한 표시줄이 Excel, PowerPoint 및 Outlook에도 추가됩니다. 예를 들면 다음과 같습니다.

![Excel에서 Azure Information Protection 표시줄의 예](../media/excel2016-infoprotect-bar.png)

이 Information Protection 표시줄을 사용하면 최종 사용자가 올바른 분류로 레이블을 쉽게 선택할 수 있으며 필요한 경우 이 레이블이 자동으로 문서와 전자 메일을 보호할 수도 있습니다.

추가 파일 형식을 분류 및 보호하고 한 번에 여러 파일을 지원하려면 Windows 파일 탐색기에서 파일 또는 폴더를 마우스 오른쪽 단추로 클릭합니다.

![Azure Information Protection을 사용한 파일 탐색기 오른쪽 클릭 메뉴 분류 및 보호](../media/right-click-classify-protect-folder.png)

사용자는 파일 탐색기에서 **분류 및 보호** 메뉴 옵션을 선택하면 Office 데스크톱 앱에서 Information Protection 표시줄을 사용하는 경우와 비슷한 방식으로 레이블을 선택할 수 있습니다. 필요한 경우 자체 사용자 지정 권한을 설정할 수도 있습니다.

고급 사용자(및 관리자)는 여러 파일에 대해 분류 및 보호를 관리하고 설정하는 데 PowerShell 명령이 더 효율적이라는 사실을 알 수 있을 것입니다. PowerShell 모듈은 개별적으로 설치할 수 있지만 이 작업을 수행하기 위한 PowerShell 명령은 클라이언트에 자동으로 포함됩니다.

문서가 보호되면 사용자와 관리자는 문서 추적 사이트를 사용하여 문서에 액세스하는 사용자와 액세스하는 시간을 모니터링할 수 있습니다. 잘못 사용하는 것으로 판단되면 이 문서에 대한 액세스를 취소할 수도 있습니다.

![문서 추적 사이트의 해지 액세스 아이콘](../media/tracking-site-revoke-access-icon.png)


## <a name="resources-for-azure-information-protection"></a>Azure Information Protection에 대한 리소스

- 알림: [Azure Information Protection is now Generally Available](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/04/azure-information-protection-is-now-generally-available/)(Azure Information Protection 출시)

- 무료 평가판: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- 클라이언트 다운로드: [Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- FAQ: [Azure Information Protection 질문과 대답](../get-started/faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)

- 비디오 개요

    <iframe width="560" height="315" src="https://www.youtube.com/embed/N9Ip0m6d3G0" frameborder="0" allowfullscreen></iframe>

    또한 Microsoft Ignite 2016에서는 Azure Information Protection에 대한 다음과 같은 여러 주문형 세션을 제공합니다.

    - [BRK2127: Adopt a comprehensive identity-driven solution for protecting and sharing data securely](https://myignite.microsoft.com/videos?q=BRK2127)(BRK2127: 데이터를 안전하게 보호 및 공유하기 위한 포괄적인 ID 기반 솔루션 채택)
    
    - [THR2107: Collaborate securely using Azure Information Protection](https://myignite.microsoft.com/videos?q=THR2107)(THR2107: Azure Information Protection을 사용하여 안전하게 공동 작업)
    
    - [THR2108: Ensure comprehensive protection of your data with Azure Information Protection](https://myignite.microsoft.com/videos?q=THR2108)(THR2108: Azure Information Protection으로 데이터에 대한 포괄적인 보호 보장)
    
    - [BRK3095: Learn how classification, labeling, and protection delivers persistent data protection](https://myignite.microsoft.com/videos?q=BRK3095)(BRK3095: 분류, 레이블 지정 및 보호를 통해 지속적인 데이터 보호를 제공하는 방법 알아보기)
    
    - [BRK2128: Send secure email to anyone with the power of Microsoft Office 365 and Azure Information Protection](https://myignite.microsoft.com/videos?q=BRK2128)(BRK2128: Microsoft Office 365 및 Azure Information Protection의 기능을 통해 모든 사용자에게 보안 메일 보내기)


## <a name="next-steps"></a>다음 단계

5단계의 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 통해 Azure Information Protection을 스스로 구성하고 확인하세요.

Azure Information Protection 또는 Azure Rights Management를 다른 이름으로 알고 계신가요? [서비스에 대한 대체 조건의 목록](azure-rms-aka.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
