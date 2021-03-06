---
title: RMS 공유 앱의 대화 상자 옵션 - AIP
description: RMS 공유 응용 프로그램의 보호 추가 대화 상자 또는 보호된 항목 공유 대화 상자에서 옵션을 지정하는 방법을 설명합니다. 공유하는 파일을 보호하거나 준비된 파일을 보호하고 사용자 지정 권한을 선택하면 이 대화 상자가 표시됩니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f6e84919653d68fb4f09671b233ccdc31bf1a82f
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024283"
---
# <a name="dialog-box-options-for-the-rights-management-sharing-application"></a>Rights Management 공유 응용 프로그램에 대한 대화 상자 옵션

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

이 정보를 사용하여 RMS 공유 응용 프로그램 **보호 추가** 대화 상자 또는 **보호된 항목 공유** 대화 상자에서 옵션을 지정하게 합니다. [공유하는 파일을 보호](sharing-app-protect-by-email.md)하거나 [준비된 파일을 보호](sharing-app-protect-in-place.md)하고 사용자 지정 권한을 선택하면 이 대화 상자가 표시됩니다.

> [!IMPORTANT]
> 표시되는 옵션이 여기서 설명하는 것과 다른 경우 아마도 설치된 공유 응용 프로그램의 최신 버전이 필요하지 않습니다. 최신 버전을 [Microsoft Rights Management](https://go.microsoft.com/fwlink/?LinkId=303970) 페이지에서 다운로드할 수 있습니다.
> 
> 최신 버전을 사용하는지 어떻게 알 수 있을까요? 프로그램 및 기능에 나열된 **Microsoft Rights Management 공유 응용 프로그램** 을 검색하고 해당 버전 번호를 확인합니다. 테이블에서 옵션을 확인하고 사용하려면 적어도 **1.0.1770.0**버전이어야 합니다. 다운로드 페이지에서 최신 버전 번호를 확인할 수 있습니다.

선택할 수 있는 옵션 외에도 다음이 궁금할 수도 있습니다.

-   [자동으로 만들어지는 .ppdf 파일이란 무엇인가요?](#whats-the-ppdf-file-thats-automatically-created)

-   [일반 보호와 기본 제공(네이티브) 보호 간의 차이점은 무엇인가요?](#whats-the-difference-between-generic-protection-and-built-in-native-protection)

|옵션|설명|
|----------|---------------|
|**사용자**|Outlook에서 전자 메일 주소를 미리 지정하지 않은 경우 파일을 열려는 사용자의 전자 메일 주소를 입력합니다.<br /><br />RMS 공유 앱은 일부 메일 주소를 지원하지 않습니다.<br /><br />조직이 Rights Management(AD RMS)의 온-프레미스 버전을 사용하는 경우 지정할 수 있는 전자 메일 주소는 조직 내의 사람을 제한합니다. 이를 적용할 때 외부 전자 메일 주소를 지정하는 경우 회사의 구성을 사용하면 회사 내에서 보호된 콘텐츠를 공유할 수 있다는 메시지가 표시됩니다. <br /><br /> 조직에서 Azure RMS를 사용하는 경우 해당 조직 내 사용자나 다른 조직의 사용자에 대한 메일 주소를 지정할 수 있습니다.<br /><br />예를 들면 다음과 같습니다. **janetm@contoso.com, p.dover@fabrikam.com**<br /><br />개인 메일 주소는 RMS 공유 앱에서 현재 지원되지 않습니다.|
|**일반 보호**|이 옵션을 선택하면 선택한 파일을 고유하게 보호할 수 없다는 것을 의미합니다. 자세한 내용은 다음을 참조하세요. 이 페이지의 [일반 보호와 기본 제공(네이티브) 보호 간의 차이점은 무엇인가요?](#whats-the-difference-between-generic-protection-and-built-in-native-protection)|
|**뷰어 – 보기 전용**<br /><br />**검토자 – 보기 및 편집**<br /><br />**공동 저자 - 보기, 편집, 복사 및 인쇄**<br /><br />**공동 저자 - 모든 사용 권한**<br /><br />참고: 이러한 옵션은 모두 이름 앞에 둥근 아이콘이 있으며 이는 지구본을 나타냅니다. 이 아이콘은 일반적으로 사용할 수 있으므로 다른 조직의 누군가에게 첨부 파일을 보낼 때 이러한 옵션 중 하나를 선택합니다.|보호된 문서에 대한 권한을 정의하려면 이러한 옵션 중 하나를 선택합니다. 각 옵션을 클릭하여 설명을 봅니다.<br /><br />이러한 옵션 중 하나를 선택하면 **사용자** 에서 지정한 사람만이 지정한 권리가 있어서 문서를 열고 사용합니다. 예를 들어 그들이 다른 사람에게 전달하는 경우 문서가 열리지 않습니다.|
|관리자가 구성한 정책 템플릿입니다.<br /><br />예를 들어 회사 이름이 Contoso, Ltd이면 **Contoso, Ltd - 기밀 보기 전용**입니다.<br /><br />참고: 이러한 옵션은 모두 이름 앞에 네모난 아이콘이 있으며 이는 사무실 건물을 나타냅니다. 이 아이콘은 일반적으로 사용할 수 있으므로 사용자의 조직의 누군가에게 첨부 파일을 보낼 때 이러한 옵션 중 하나를 선택합니다.|조직에서 일하는 사람과 문서를 공유하면 관리자가 구성한 사용 가능한 정책 템플릿을 참조합니다. 조직 외부의 문서를 공유하지 않아야 하는 경우 다음 중 하나를 선택합니다.<br /><br />이러한 옵션 중 하나를 선택하면 관리자는 문서에 대한 권한 및 열 수 있는 사람을 정의합니다.|
|**이러한 문서 만료**|선택한 사용자는 지정한 날짜 이후에 열 수 없는 시간에 민감한 파일에 대해서만 이 옵션을 선택합니다. 여전히 원래 파일을 열 수 있지만 지정한 날의 (현재 표준 시간대)자정 이후에 다른 사람은 파일을 열 수 없습니다.<br /><br />이 옵션은 관리자가 구성하는 정책 템플릿을 선택하는 경우 사용할 수 없습니다.|
|**누군가가 이 문서를 열려고 하면 내게 메일을 보냅니다.**|참고: 이 옵션은 현재 미리 보기로 제공됩니다.<br /><br />사용자가 보호하려는 문서를 누군가가 열려고 할 때마다 전자 메일 알림을 수신하려는 경우 이 옵션을 선택합니다. 전자 메일 메시지는 파일을 열려고 시도한 사람, 시기 및 성공 여부를 알려줍니다.<br /><br />조직에서 Azure Information Protection을 사용하는 경우 이 옵션을 사용할 수 있습니다. 조직에서 Rights Management(AD RMS)의 온-프레미스 버전을 사용하는 경우이 옵션이 표시되지 않습니다.|
|**이러한 문서에 대한 액세스를 즉시 취소할 수 있도록 허용합니다.**|사이트를 추적하는 문서를 사용하여 나중에 문서에 대한 액세스를 취소해야 하는 경우 이 옵션을 선택하고 해지를 즉시 적용해야 합니다. 그러나 옵션을 설정하면 문서가 해지되지 않은 동안 사용자는 액세스할 때마다 문서를 읽기 위해 항상 인터넷 연결이 필요하게 됩니다. 사용자가 장치를 인터넷에 연결할 수 없고 사용자가 의도한 대로 문서를 읽을 수 없는 일부 시나리오가 있습니다.<br /><br />이 옵션을 선택하지 않으면 사이트를 추적하는 문서를 사용하여 나중에 문서를 해지할 수 있습니다. 그러나 사용자가 문서를 읽기 위해 인터넷 연결이 필요하기 때문에 문서가 해지된 것을 즉시 알 수 없고 Azure RMS로 다음에 인증할 때까지 계속 읽을 수 있습니다. 기본적으로 누군가가 해지한 보호된 문서를 계속 읽을 수 없는 최대 일 수는 30일이지만 관리자는 이 값을 30일 보다 더 적거나 크게 변경할 수 있습니다.<br /><br />조직에서 Azure Information Protection을 사용하는 경우 이 옵션을 사용할 수 있습니다. 조직에서 Rights Management(AD RMS)의 온-프레미스 버전을 사용하는 경우이 옵션이 표시되지 않습니다.|

## <a name="whats-the-difference-between-generic-protection-and-built-in-native-protection"></a>일반 보호와 기본 제공(네이티브) 보호 간의 차이점은 무엇인가요?

-   **일반적으로 파일을 보호**할 때 권한 없는 사람은 파일을 열 수 없습니다. 인증된 사용자가 파일을 연 다음 다른 사람에게 보호되지 않은 상태로 전달하거나 다른 사용자가 액세스할 수 있는 위치에 저장할 수 있었습니다. 그러나 파일에 대해 어떤 권한이 있는지를 알려주는 메시지가 표시되고 이를 적용하도록 요청하지만 이 보호는 강제로 적용할 수 없습니다. 또한 일반적으로 파일을 보호하는 경우 권한 부여 이상의 사용 권한을 제한할 수 없습니다. 예를 들어 콘텐츠를 보기 전용으로 제한할 수 없거나 인쇄하지 않습니다.

    > [!NOTE]
    > 일반적으로 보호된 파일은 항상 **.pfile**이라는 파일 이름 확장명을 가집니다.

-   반면 이를 지원하는 응용 프로그램으로 Rights Management의 **기본 제공(기본) 보호**를 사용하는 경우(예: Office 파일) 파일이 다른 사람에게 전송되거나 다른 위치에 저장되더라도 파일에 보호가 적용됩니다. 그리고 이러한 파일을 보호하는 경우 읽기 전용과 같은 제한적 사용 권한 또는 편집하지만 인쇄하거나 복사할 수 없는 사용 권한을 사용할 수 있습니다. 예를 들어 **뷰어 – 보기 전용**을 선택하면 콘텐츠를 편집, 인쇄 또는 복사할 수 없습니다.

추가 기술 정보는 [Rights Management 공유 응용 프로그램 관리자 가이드](sharing-app-admin-guide.md)에서 [보호 수준 – 기본 및 일반](sharing-app-admin-guide-technical.md#levels-of-protection--native-and-generic) 섹션을 참조하세요.

## <a name="whats-the-ppdf-file-thats-automatically-created"></a>자동으로 만들어지는 .ppdf 파일이란 무엇인가요?

-   전자 메일을 통해 보호된 파일을 공유하는 경우(보호된 공유) RMS 공유 응용 프로그램은 자동으로 Word, Excel, PowerPoint, 또는 PDF 파일의 **.ppdf** 버전을 만듭니다. 권한 있는 사람만 열 수있는 파일의 읽기 전용 보호된 버전이며 기본적으로 Rights Management를 지원하는 응용 프로그램이 없는 모바일 장치를 사용하더라도 받는 사람은 항상 첨부 파일을 읽을 수 있습니다. 이러한 사용자를 제공하여 RMS 공유 앱을 설치하고 첨부 파일을 읽을 수 있습니다.

    이 시나리오에서 일반적으로 보호된 파일과 달리 사용 제한을 적용합니다. 받는 사람은 이 버전의 파일을 저장할 수 없고 다른 사람에게 첨부 파일을 전달하는 경우 원래 제약 조건이 문서에 남습니다. 보호된 문서에 대한 권한이 부여된 사람만 열 수 있게 됩니다.

    > [!NOTE]
    > 보호된 항목을 공유할 때(전자 메일로 공유함) .ppdf 파일이 자동으로 만들어지지만 준비되어 보호할 때 만들어지지 않습니다.

## <a name="examples-and-other-instructions"></a>예제 및 기타 지침
예를 들어 Rights Management 공유 응용 프로그램 및 방법 지침을 사용하는 방법에 대한 예는 Rights Management 공유 응용 프로그램 사용자 가이드에서 다음 섹션을 참조하세요.

-   [RMS 공유 응용 프로그램 사용 예제](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [원하는 옵션을 선택하](sharing-app-user-guide.md#what-do-you-want-to-do)세요.

## <a name="see-also"></a>참고 항목
[Rights Management 공유 응용 프로그램 사용자 가이드](sharing-app-user-guide.md)

