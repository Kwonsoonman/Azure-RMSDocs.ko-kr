---
title: 분류 및 레이블 지정에 대한 FAQ - AIP
description: Azure Information Protection를 사용한 분류 및 레이블 지정에 대한 특별한 질문이 있나요? 여기에 해당 질문에 대한 대답이 있는지 확인하세요.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/27/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: a4aa5b1a6375655b9b6ab20f092a7def47187225
ms.sourcegitcommit: ff77e4da1f7c7cf2262c208f8e58b85cfdb54903
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52421048"
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Azure Information Protection에서 분류 및 레이블 지정에 대한 질문과 대답

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection에서 특별히 분류 및 레이블 지정에 대한 질문이 있나요?  여기에 해당 질문에 대한 대답이 있는지 확인하세요. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Azure Information Protection에서 분류 기능으로 수행할 수 있는 작업은 무엇인가요?

[정책 편집 및 새 레이블 만들기](infoprotect-quick-start-tutorial.md) 자습서를 진행하면 이러한 작업을 몇 분 만에 확인할 수 있습니다.

추가 분류 기능 및 특징을 언제 사용할 수 있는지는 [Enterprise Mobility + Security 블로그](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity/label-name/Azure%20Information%20Protection) 및 [Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)에서 공지 사항을 확인하세요. 현재 릴리스에는 다음을 포함하는 몇 가지 제한이 있습니다.

- Office Web Apps(Office Online)에는 레이블 지정 기능이 없습니다.

- 분류 및 레이블 지정 기능이 Exchange Online 또는 SharePoint Online과는 통합되지 않습니다.

> [!NOTE]
> **현재 미리 보기로 제공되는 기능**:
> - 분류 및 레이블 지정을 위한 중앙 집중식 보고. 자세한 내용은 [Azure Information Protection의 중앙 보고](reports-aip.md)를 참조하세요.
> - [Office Insider 프로그램](https://support.office.com/article/what-is-office-insider-f4208185-b63a-4b68-9c7a-9a32d2411c16)에 옵트인(opt in)한 고객을 위한 모바일 장치(iOS 및 Android) 및 Mac 컴퓨터용 Office 앱 레이블 지정 기능 자세한 내용은 [Office 내의 문서 및 전자 메일에 민감도 레이블 적용](https://aka.ms/officemipdocs)을 참조하세요.


Azure Information Protection의 [UserVoice 사이트](https://msip.uservoice.com/)를 방문하여 새로운 기능을 요청하고 요청에 투표하세요.

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>분류 및 레이블을 구성하려면 전역 관리자여야 합니까?

새로 도입된 Information Protection 관리자 역할을 통해 이제 이 질문에 대한 답변은 기본 FAQ 페이지에 제공됩니다. [Azure Information Protection을 구성하려면 전역 관리자여야 하나요? 또는 다른 관리자에게 위임할 수 있나요?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

[Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치할 때 데모 정책 설치 옵션을 선택하면 레이블 지정 기능을 확인하고 사용해 보기 위해 포털에 로그인하지 않아도 됩니다. 데모 정책에서는 Azure Information Protection에 대한 기본 정책을 로컬로 설치하므로 문서 및 메일에 레이블을 지정해 볼 수 있지만, Azure Portal에 로그인하지 않고서는 레이블을 변경하거나 새 레이블을 추가할 수 없습니다. 

## <a name="can-a-file-have-more-than-one-classification"></a>파일에 분류가 여러 개 있을 수 있나요?

사용자는 각 문서 또는 메일에 대해 한 번에 레이블 하나만 선택할 수 있으며, 그 결과 분류가 하나만 생깁니다. 그러나 사용자가 하위 레이블을 선택하면 실제로 두 레이블(기본 레이블 및 보조 레이블)이 동시에 적용됩니다. 하위 레이블을 사용함으로써 추가 수준의 제어에 대해 파일에 부모\자식 관계를 나타내는 두 분류가 있을 수 있습니다.

예를 들어, **기밀** 레이블은 **법률**과 **금융** 같은 하위 레이블을 포함할 수 있습니다. 서로 다른 분류 시각적 표시와 서로 다른 Rights Management 템플릿을 이러한 하위 레이블에 적용할 수 있습니다. 사용자는 **기밀** 레이블 자체만 선택할 수 없으며 **법률** 같은 하위 레이블 중 하나를 선택해야 합니다. 결과적으로 표시되는 레이블은 **기밀 \ 법률**입니다. 해당 파일의 메타데이터에는 **기밀**에 대한 사용자 지정 텍스트 속성 하나, **법률**에 대한 사용자 지정 텍스트 속성 하나, 두 값을 모두 포함하는 다른 사용자 지정 텍스트 속성(**기밀 법률**)이 포함됩니다. 

하위 레이블을 사용할 때에는 기본 레이블에 시각적 표시, 보호 및 상태를 구성하지 마세요. 하위 수준을 사용할 때에는 하위 레이블에만 이러한 설정을 구성합니다. 기본 레이블과 하위 레이블에 이러한 설정을 구성하는 경우 하위 레이블의 설정이 우선합니다.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>다른 사용자가 레이블을 제거하거나 변경하지 않도록 방지하려면 어떻게 할까요?

사용자가 분류 레이블을 낮추거나 보호를 제거하는 이유를 설명해야 하는 [정책 설정](configure-policy-settings.md)이 있지만 이 설정으로 인해 이러한 작업이 방해되지는 않습니다. 사용자가 레이블을 제거하거나 변경하지 않도록 방지하려면 콘텐츠를 미리 보호하고 보호 권한에서 사용자에게 내보내기 또는 모든 권한 [사용 권한](configure-usage-rights.md)을 부여하지 않습니다. 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>메일에 레이블이 지정되면 첨부 파일에 자동으로 동일한 레이블이 지정되나요?

아니요. 첨부 파일이 있는 메일 메시지에 레이블을 지정하면 해당 첨부 파일은 동일한 레이블을 상속하지 않습니다. 첨부 파일은 레이블 없이 유지되거나 별도로 적용된 레이블을 보유합니다. 그러나 메일의 레이블이 보호를 적용하는 경우 해당 보호는 Office 첨부 파일에 적용됩니다.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>DLP 솔루션 및 다른 응용 프로그램을 Azure Information Protection과 통합하려면 어떻게 하나요?

Azure Information Protection에서는 일반 텍스트 레이블을 포함하는 영구 메타데이터를 분류에 사용하므로 DLP 솔루션 및 다른 응용 프로그램에서 이 정보를 읽을 수 있습니다. 

이 메타데이터를 Exchange Online 메일 흐름 규칙에 사용하는 방법에 대한 자세한 내용 및 예제는 [Azure Information Protection 레이블에 대한 Exchange Online 메일 흐름 규칙 구성](configure-exo-rules.md)을 참조하세요.

## <a name="can-i-create-a-document-template-that-automatically-includes-the-classification"></a>분류를 자동으로 포함하는 문서 템플릿을 만들 수 있나요?

예. [레이블 이름을 포함하는 헤더 또는 바닥글을 적용하도록](configure-policy-markings.md) 레이블을 구성할 수 있습니다. 또는 원하는 서식을 갖는 문서 템플릿을 만들고 분류를 필드 코드로 추가할 수 있습니다. 

예를 들어, 문서의 헤더에 분류를 표시하는 표를 포함할 수 있습니다. 또는 문서의 분류를 참조하는 소개에 특정 단어를 사용할 수 있습니다.

문서에 이러한 필드 코드를 추가하려면:

1. 문서에 레이블을 지정하고 저장합니다. 이렇게 하면 필드 코드에 사용할 수 있는 새로운 메타데이터 필드가 생성됩니다.

2. 문서에서 레이블의 분류를 추가할 위치에 커서를 두고 **삽입** 탭에서 **텍스트** > **빠른 문서 요소** > **필드**를 선택합니다.

3. **필드** 대화 상자의 **범주** 드롭다운에서 **문서 정보**를 선택합니다. 그런 다음, **필드 이름** 드롭다운에서 **DocProperty**를 선택합니다.

4. **속성** 드롭다운에서 **Sensitivity**를 선택하고 **확인**을 선택합니다.

현재 레이블의 분류가 문서에 표시되고, 문서를 열거나 템플릿을 사용할 때마다 이 값이 자동으로 업데이트됩니다. 따라서 레이블이 변경되면 이 필드 코드에 대해 표시되는 분류가 문서에서 자동으로 업데이트됩니다.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>전자 메일에 대한 Azure Information Protection 분류와 Exchange 메시지 분류는 어떻게 다른가요?

Exchange 메시지 분류는 전자 메일을 분류할 수 있는 이전 기능으로, Azure Information Protection 분류와는 독립적으로 구현됩니다. 

그러나 사용자가 웹용 Outlook을 사용하고 일부 모바일 메일 응용 프로그램을 사용하여 메일을 분류할 때 Azure Information Protection 분류와 해당하는 레이블 표시가 자동으로 추가되도록 두 솔루션을 통합할 수 있습니다. 

웹용 Outlook 및 이러한 모바일 메일 응용 프로그램에서 레이블을 사용할 때도 이와 동일한 방법을 사용할 수 있습니다.

구성 단계에 대해서는 [모바일 장치 레이블 지정 솔루션을 위해 Azure Information protection에 Exchange 메시지 분류 통합](./rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution)합니다. 



