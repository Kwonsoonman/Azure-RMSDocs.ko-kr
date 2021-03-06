---
title: Azure Information Protection이란? - AIP
description: Azure Information Protection 서비스에 대해 간략하게 설명합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
ms.openlocfilehash: 9c7fd9070e6cc07a7b16043dd480addd2d0a4313
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024344"
---
# <a name="what-is-azure-information-protection"></a>Azure Information Protection이란?

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection(AIP라고도 함)은 클라우드 기반 솔루션으로서 조직에서 문서와 메일을 분류하고, 레이블을 적용하여 선택적으로 문서와 메일을 보호하는 데 도움이 됩니다. 레이블은 규칙 및 조건을 정의하는 관리자가 자동으로 적용하거나, 사용자가 수동으로 적용할 수 있으며, 사용자가 권장 사항을 제공받은 경우에는 자동 또는 수동으로 적용할 수 있습니다. 

다음 그림은 사용자의 컴퓨터에서 Azure Information Protection의 실제 작동 방식 예를 보여 줍니다. 관리자는 중요한 데이터를 검색하는 규칙을 사용하여 레이블을 구성했으며, 이 예에서는 신용 카드 정보입니다. 신용 카드 정보가 포함된 Word 문서를 저장할 때 관리자가 구성한 레이블을 권장하는 사용자 지정 도구 설명이 나타납니다. 이 레이블은 문서를 분류하고 보호합니다. 

![Azure Information Protection에 권장되는 분류 예](./media/info-protect-recommend-calloutsv2.png)

콘텐츠가 분류되고 나면(경우에 따라 보호됨) 해당 콘텐츠를 추적하고 제어할 수 있습니다. 데이터 흐름을 분석하여 비즈니스 통찰력을 얻고, 위험 행동을 검색하여 수정 작업을 수행하고, 문서에 대한 액세스를 추적하고, 데이터가 누출되거나 잘못 사용되지 않게 할 수 있습니다.

## <a name="how-labels-apply-classification"></a>레이블에서 분류를 적용하는 방법

Azure Information Protection 레이블을 사용하여 문서와 전자 메일을 분류할 수 있습니다. 이 작업을 수행하면 데이터가 저장된 위치나 데이터를 공유한 사용자가 누구인지와 관계없이 분류를 식별할 수 있게 됩니다. 이러한 레이블은 머리글, 바닥글, 워터마크 등의 시각적 표시를 포함할 수 있습니다. 메타데이터는 일반 텍스트로 파일 및 메일 머리글에 추가됩니다. 일반 텍스트는 다른 서비스(예: 데이터 손실 방지 솔루션)에서 분류를 식별하고 적절한 조치를 취할 수 있도록 합니다. 

예를 들어 다음 메일 메시지는 "일반"으로 분류되었습니다. 레이블은 메일 메시지에 “민감도: 일반”의 바닥글을 추가했습니다. 이 바닥글을 통해 모든 받는 사람은 메시지가 조직 외부로 전송되면 안 되는 일반적인 비즈니스 데이터용임을 시각적으로 쉽게 구별할 수 있습니다. 이 레이블은 메일 서비스에서 이 값을 검사하여 감사 항목을 만들거나 조직 외부로 전송되지 않도록 메일 머리글에 포함됩니다.

![Azure Information Protection 분류를 보여 주는 머리글 및 바닥글 예](./media/example-email-footerv2.png)


## <a name="how-data-is-protected"></a>데이터를 보호하는 방법

보호 기술에서는 *Azure Rights Management*(종종 Azure RMS로 축약됨)를 사용합니다. 이 기술은 다른 Microsoft 클라우드 서비스 및 응용 프로그램(Office 365, Azure Active Directory 등)과 통합되었습니다. 또한 기간 업무 응용 프로그램 및 소프트웨어 공급 업체의 정보 보호 솔루션이 온-프레미스에 있는지 아니면 클라우드에 있는지와 상관없이 해당 응용 프로그램 및 솔루션과 함께 사용할 수 있습니다.

이 보호 기술은 암호화, ID 및 권한 부여 정책을 사용합니다. 적용되는 레이블과 마찬가지로 Rights Management를 사용하여 적용된 보호 기능은 조직, 네트워크, 파일 서버, 응용 프로그램 내/외의 위치에 관계없이 문서와 전자 메일에 계속 적용됩니다. 이 정보 보호 솔루션은 데이터를 다른 사용자와 공유하는 경우에도 데이터에 대한 제어를 유지할 수 있도록 합니다.

예를 들어 조직 내의 사용자만 액세스할 수 있도록 보고서 문서 또는 판매 예측 스프레드시트를 구성할 수도 있고 해당 문서의 편집 가능 여부를 제어하거나, 읽기 전용으로 제한하거나 문서 인쇄를 차단할 수도 있습니다. 마찬가지로 메일을 구성할 수 있으며 전체 회신 옵션 사용 또는 메일 전달을 차단할 수도 있습니다. 

이러한 보호 설정은 레이블 구성의 일부가 될 수 있으므로 사용자는 단순히 레이블을 적용하여 문서와 전자 메일을 분류하고 보호할 수 있습니다. 그러나 보호를 지원하지만 레이블링을 지원하지 않는 응용 프로그램 및 서비스에서 동일한 보호 설정을 사용할 수도 있습니다. 이러한 응용 프로그램과 서비스의 경우 보호 설정은 *Rights Management 템플릿*으로 제공됩니다.

### <a name="rights-management-templates"></a>Rights Management 템플릿

Azure Rights Management 서비스를 활성화하는 즉시 조직 내 사용자에 대한 데이터 액세스를 제한하는 두 가지 기본 템플릿을 사용할 수 있습니다. 이러한 템플릿을 사용하여 즉시 조직에서 데이터가 누출되는 것을 방지할 수 있습니다. 또한 제한이 강화된 컨트롤을 적용하는 자체 보호 설정을 구성하여 이러한 기본 템플릿을 보완할 수도 있습니다.

내부적으로 보호 설정이 포함된 Azure Information Protection에 대해 레이블을 만드는 경우 이 작업은 해당 Rights Management 템플릿을 만듭니다. 그런 다음 Azure Rights Management를 지원하는 응용 프로그램 및 서비스로 해당 템플릿을 사용할 수도 있습니다.

예를 들어 Exchange 관리 센터에서 Exchange Online 메일 흐름 규칙을 구성하여 이들 템플릿을 사용할 수 있습니다.

![Exchange Online용 템플릿을 선택하는 예](./media/templates-exchangeonline-callouts.png)

Azure Rights Management 보호에 대한 자세한 내용은 [Azure Rights Management란?](what-is-azure-rms.md)을 참조하세요.

## <a name="integration-with-end-user-workflows-for-documents-and-emails"></a>문서 및 메일에 대한 최종 사용자 워크플로와 통합

Azure Information Protection 클라이언트가 설치되면 Azure Information Protection은 최종 사용자의 기존 워크플로와 통합됩니다. 이 클라이언트는 Word에 Information Protection 표시줄이 표시된 첫 번째 그림에서 살펴본 대로 Office 응용 프로그램에 이 표시줄을 설치합니다. 동일한 Information Protection 표시줄이 Excel, PowerPoint 및 Outlook에 추가됩니다. 예를 들면 다음과 같습니다.

![Excel에서 Azure Information Protection 표시줄의 예](./media/excel2016-infoprotect-barv2.png)

이 Information Protection 표시줄을 사용하면 최종 사용자가 올바른 분류를 위해 레이블을 선택하기가 쉽습니다. 필요한 경우 사용자에 대한 추측을 제거하거나 조직의 정책을 준수하기 위해 레이블을 자동으로 적용할 수도 있습니다.

추가 파일 형식을 분류 및 보호하고 한 번에 여러 파일을 지원하려면 Windows 파일 탐색기에서 파일 또는 폴더를 마우스 오른쪽 단추로 클릭합니다.

![Azure Information Protection을 사용한 파일 탐색기 오른쪽 클릭 메뉴 분류 및 보호](./media/right-click-classify-protect-folder.png)

사용자는 파일 탐색기에서 **분류 및 보호** 메뉴 옵션을 선택하면 Office 데스크톱 앱에서 Information Protection 표시줄을 사용하는 경우와 비슷한 방식으로 레이블을 선택할 수 있습니다. 필요한 경우 자체 사용자 지정 권한을 설정할 수도 있습니다.

고급 사용자(및 관리자)는 여러 파일에 대해 분류 및 보호를 관리하고 설정하는 데 PowerShell 명령이 더 효율적이라는 사실을 알 수 있을 것입니다. PowerShell 모듈은 개별적으로 설치할 수 있지만 이 작업을 수행하기 위한 PowerShell 명령은 클라이언트에 자동으로 포함됩니다.

문서가 보호되면 사용자와 관리자는 문서 추적 사이트를 사용하여 문서에 액세스하는 사용자와 액세스하는 시간을 모니터링할 수 있습니다. 잘못 사용하는 것으로 판단되면 이 문서에 대한 액세스를 취소할 수도 있습니다.

![문서 추적 사이트의 해지 액세스 아이콘](./media/tracking-site-revoke-access-icon.png)

### <a name="additional-integration-for-email"></a>메일에 대한 추가 통합

Azure Information Protection을 Exchange Online과 함께 사용하는 경우 추가 이점이 있습니다. 즉, 보호된 메일을 모든 사용자에게 보내 사용자가 원하는 장치에서 읽을 수 있도록 할 수 있습니다.

예를 들어 사용자가 **Gmail**, **Hotmail** 또는 **Microsoft** 계정을 사용하는 개인 이메일 주소나 Office 365 또는 Azure AD의 계정이 없는 사용자에게 중요한 정보를 보내야 한다고 가정합니다. 이러한 메일은 미사용 시와 전송 중에 암호화해야 하고 원래 받는 사람만 읽어야 합니다.

이 시나리오에서는 [Office 365 메시지 암호화의 새로운 기능](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)이 필요합니다. 받은 사람이 기본 메일 클라이언트에서 보호된 메일을 열 수 없는 경우 일회성 암호를 사용하여 브라우저에서 중요한 정보를 읽을 수 있습니다.

예를 들어 Gmail 사용자의 이메일 메시지에는 다음이 표시됩니다.

![OME 및 AIP에 대한 Gmail 받은 사람 환경](./media/ome-message.png)

메일을 보내는 사용자의 워크플로는 자신의 조직에 속한 사용자에게 보호된 메일을 보낼 때와 다르지 않습니다. 예를 들어 Azure Information Protection 클라이언트가 Outlook 리본에 추가할 수 있는 **전달 금지** 단추를 선택할 수 있습니다. 또는 이 전달 금지 기능을 사용자가 선택하는 레이블에 통합하여 메일도 보호되는 항목으로 분류되도록 할 수 있습니다.

![전달 금지가 구성된 레이블 선택](./media/recipients-only-label.png)

또는 권한 보호를 적용하는 메일 흐름 규칙을 사용하여 사용자에 대한 보호를 자동으로 제공할 수도 있습니다. 

이러한 메일에 Office 문서를 첨부하면 해당 문서도 자동으로 보호됩니다.

## <a name="classifying-and-protecting-existing-documents"></a>기존 문서 분류 및 보호

이상적으로 문서와 메일은 처음 생성될 때 레이블이 지정됩니다. 그러나 데이터 저장소에 기존 문서가 많이 있고 이러한 문서도 분류하고 보호하려고 합니다. 이러한 데이터 저장소는 온-프레미스 또는 클라우드일 수 있습니다.

온-프레미스 데이터 저장소의 경우 Azure Information Protection 스캐너를 사용하여 로컬 폴더, 네트워크 공유 및 SharePoint Server 사이트와 라이브러리에서 문서를 검색, 분류 및 보호합니다. 스캐너는 Windows Server에서 서비스로 실행됩니다. 정책에서 동일한 규칙을 사용하여 중요한 정보를 검색하고 특정 레이블을 문서에 적용할 수 있습니다. 또는 파일 콘텐츠를 검사하지 않고 데이터 리포지토리의 모든 문서에 기본 레이블을 적용할 수 있습니다. 스캐너를 보고 모드에서만 사용하여 사용자가 모를 수 있는 중요한 정보를 검색할 수도 있습니다. 

스캐너 배포 및 사용에 대한 자세한 내용은 [Azure Information Protection 스캐너를 배포하여 자동으로 파일 분류 및 보호](deploy-aip-scanner.md)를 참조하세요.

클라우드 데이터 저장소의 경우 Microsoft Cloud App Security를 사용하여 Box, SharePoint Online 및 비즈니스용 OneDrive의 문서에 레이블을 적용합니다. 자세한 내용은 [Azure Information Protection 분류 레이블 자동 적용](/cloud-app-security/use-case-information-protection) 및 [Azure Information Protection 통합](/cloud-app-security/azip-integration)을 참조하세요.


## <a name="resources-for-azure-information-protection"></a>Azure Information Protection에 대한 리소스

- 무료 평가판: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- 구독 옵션 및 가격: [Azure Information Protection 가격](https://azure.microsoft.com/pricing/details/information-protection)

- 클라이언트 다운로드: [Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- 사용자 지정 가능한 사용자 가이드 다운로드: [Azure Information Protection 최종 사용자 채택 가이드](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

- FAQ: [Azure Information Protection 질문과 대답](faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/AskIPTeam)

추가 리소스: [Azure Information Protection에 대한 정보 및 지원](information-support.md)

### <a name="microsoft-ignite"></a>Microsoft Ignite

Microsoft Ignite 2018 in Orlando에는 [Azure Information Protection](https://myignite.techcommunity.microsoft.com/sessions?q=Azure%2520Information%2520Protection)이라는 태그가 지정된 세션이 많이 있었습니다. 모든 세션이 기록되었기 때문에 세션에 가입할 수 없더라도 나중에 세션을 계속해서 볼 수 있습니다. 권장되는 상위 5개 세션은 다음과 같습니다.

- [BRK2006 - MIP(Microsoft Information Protection)를 사용하여 수명 주기 전체에서 위치에 상관없이 중요한 데이터 보호](https://myignite.techcommunity.microsoft.com/sessions/64297) - [YouTube 비디오](https://youtu.be/gmHVF-1cLXA) 보기
 
- [BRK3002 - 장치, 앱 및 서비스 전반에서 중요한 정보를 보호하기 위해 Microsoft Information Protection 기능이 함께 작동하는 방식 이해하기](https://myignite.techcommunity.microsoft.com/sessions/64299) - [YouTube 비디오](https://youtu.be/kL9Y7NGTyQQ) 보기

- [BRK3009 - Microsoft Information Protection 솔루션의 배포 및 채택 가속화](https://myignite.techcommunity.microsoft.com/sessions/64283) - [YouTube 비디오](https://www.youtube.com/watch?v=JsCyIVyQJmE) 보기

- [BRK3397 - Office 365 메시지 암호화를 사용해 중요한 메일 보호 및 관리](https://myignite.techcommunity.microsoft.com/sessions/64327) - [YouTube 비디오](https://www.youtube.com/watch?v=Ld4b4pFua0g) 보기

- [THR2003 - Microsoft Information Protection을 사용해 모든 데이터에 대한 데이터 검색, 사용량 보고 및 분석](https://myignite.techcommunity.microsoft.com/sessions/64301) - [YouTube 비디오](https://www.youtube.com/watch?v=nzDIXd0XaeA) 보기

이번 Ignite에서 발표된 내용에 대해 자세히 알아보려면 블로그 게시물 [Announcing availability of information protection capabilities to help protect your sensitive data](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967)(중요한 데이터 보호를 위한 정보 보호 기능의 출시 발표)를 참조하세요.


## <a name="next-steps"></a>다음 단계

[빠른 시작](quickstart-viewpolicy.md) 및 [자습서](infoprotect-quick-start-tutorial.md)를 통해 Azure Information Protection을 스스로 구성하고 확인하세요. 또는 조직에 이 서비스를 배포할 준비가 되면 [일반적인 시나리오에 대한 방법 가이드](how-to-guides.md)를 진행하세요.