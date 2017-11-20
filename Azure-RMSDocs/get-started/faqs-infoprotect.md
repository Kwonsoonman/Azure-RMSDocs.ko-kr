---
title: "분류 및 레이블 지정에 대한 FAQ - AIP"
description: "Azure Information Protection를 사용한 분류 및 레이블 지정에 대한 특별한 질문이 있나요? 여기에 해당 질문에 대한 대답이 있는지 확인하세요."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: 4332b37a3c89cb68d8e090e44666f2620d5b0064
ms.sourcegitcommit: fd3932ab19a00229b56efc3e301abaf9cff3f70b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Azure Information Protection에서 분류 및 레이블 지정에 대한 질문과 대답

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection에서 특별히 분류 및 레이블 지정에 대한 질문이 있나요?  여기에 해당 질문에 대한 대답이 있는지 확인하세요. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Azure Information Protection에서 분류 기능으로 수행할 수 있는 작업은 무엇인가요?

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)를 통해 몇 분 만에 이러한 기능의 작동 방식을 확인해 보세요.

추가 분류 기능 및 특징을 사용할 수 있게 되면 [Enterprise Mobility 및 보안 블로그](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) 및 [Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)에서 공지 사항을 확인하세요. 현재 릴리스에는 다음을 포함하는 몇 가지 제한이 있습니다.

- 레이블 이름 및 도구 설명은 하나의 언어로만 지원됩니다. 그러나 다국어 지원은 현재 미리 보기로 제공됩니다. 자세한 내용은 [다른 언어에 대한 레이블 및 템플릿을 구성하는 방법](../deploy-use/configure-policy-languages.md)을 참조하세요.

- 분류 및 레이블 지정을 위한 중앙 집중식 로깅은 없습니다.

- 모바일 장치(iOS 및 Android) 및 Mac 컴퓨터용 Office 앱 또는 Office Web Apps(Office Online)에는 레이블 지정 기능이 없습니다.

- 분류 및 레이블 지정 기능이 Exchange Online 또는 SharePoint Online과는 통합되지 않습니다.

Azure Information Protection의 [사용자 의견 사이트](https://msip.uservoice.com/)를 방문하여 새로운 기능을 요청하고 요청에 투표하세요.

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>분류 및 레이블을 구성하려면 전역 관리자여야 합니까?

Azure Information Protection 정책을 구성하려 할 때, 더 이상 Azure Active Directory의 전역 관리자로 Azure Portal에 로그인할 필요가 없습니다. 또한 이제는 보안 관리자 역할이 있는 계정을 사용할 수 있습니다.

[Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치할 때 데모 정책 설치 옵션을 선택하면 레이블 지정 기능을 확인하고 사용해 보기 위해 포털에 로그인하지 않아도 됩니다. 데모 정책에서는 Azure Information Protection에 대한 기본 정책을 로컬로 설치하므로 문서 및 메일에 레이블을 지정해 볼 수 있지만, Azure Portal에 로그인하지 않고서는 레이블을 변경하거나 새 레이블을 추가할 수 없습니다. 

## <a name="which-options-in-the-azure-portal-are-p2"></a>Azure Portal에서 어떤 옵션이 P2인가요?

**Azure Information Protection Premium 2**(P2) 구독이 필요한 Azure Portal의 옵션은 이제 옵션을 식별하기 위한 정보 팝업 메시지를 포함합니다. P1 및 P1 구독에 포함된 기능에 대한 자세한 내용은 Azure Information Protection 사이트의 [기능 목록](https://www.microsoft.com/cloud-platform/azure-information-protection-features)을 참조하세요.

## <a name="can-a-file-have-more-than-one-classification"></a>파일에 분류가 여러 개 있을 수 있나요?

사용자는 각 문서 또는 메일에 대해 한 번에 레이블 하나만 선택할 수 있으며, 그 결과 분류가 하나만 생깁니다. 그러나 사용자가 하위 레이블을 선택하면 실제로 두 레이블(기본 레이블 및 보조 레이블)이 동시에 적용됩니다. 하위 레이블을 사용함으로써 추가 수준의 제어에 대해 파일에 부모\자식 관계를 나타내는 두 분류가 있을 수 있습니다.

예를 들어 레이블 **기밀**은 **법률**과 **금융** 같은 하위 레이블을 포함할 수 있습니다. 서로 다른 분류 시각적 표시와 서로 다른 Rights Management 템플릿을 이러한 하위 레이블에 적용할 수 있습니다. 사용자는 **기밀** 레이블 자체만 선택할 수 없으며 **법률** 같은 하위 레이블 중 하나를 선택해야 합니다. 결과적으로 표시되는 레이블은 **기밀 \ 법률**입니다. 해당 파일의 메타데이터에는 **기밀**에 대한 사용자 지정 텍스트 속성 하나, **법률**에 대한 사용자 지정 텍스트 속성 하나, 두 값을 모두 포함하는 다른 사용자 지정 텍스트 속성(**기밀 법률**)이 포함됩니다. 

하위 레이블을 사용할 때에는 기본 레이블에 시각적 표시, 보호 및 상태를 구성하지 마세요. 하위 수준을 사용할 때에는 하위 레이블에만 이러한 설정을 구성합니다. 기본 레이블과 하위 레이블에 이러한 설정을 구성하는 경우 하위 레이블의 설정이 우선합니다.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>메일에 레이블이 지정되면 첨부 파일에 자동으로 동일한 레이블이 지정되나요?

아니요. 첨부 파일이 있는 메일 메시지에 레이블을 지정하면 해당 첨부 파일은 동일한 레이블을 상속하지 않습니다. 첨부 파일은 레이블 없이 유지되거나 별도로 적용된 레이블을 보유합니다. 그러나 메일의 레이블에 보호를 적용하는 경우 해당 보호는 첨부 파일에 적용됩니다.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>DLP 솔루션 및 다른 응용 프로그램을 Azure Information Protection과 통합하려면 어떻게 하나요?

Azure Information Protection에서는 일반 텍스트 레이블을 포함하는 영구 메타데이터를 분류에 사용하므로 DLP 솔루션 및 다른 응용 프로그램에서 이 정보를 읽을 수 있습니다. 

- Word 문서(.doc 및 .docx), Excel 스프레드시트(.xls 및 .xlsx), PowerPoint 프레젠테이션(.ppt 및 .pptx) 및 PDF 문서(.pdf)의 경우 이 메타데이터는 **MSIP_Label_\<GUID>_Enabled=True** 사용자 지정 속성에 저장됩니다.  

- 전자 메일에서 이 정보는 x- 헤더(**msip_labels: MSIP_Label_\<GUID>_Enabled=True;**)에 저장됩니다.  

레이블에 대한 GUID를 확인하려면 Azure Portal에서 Azure Information Protection 정책을 보거나 구성할 때 [레이블] 블레이드에서 레이블 ID 값을 찾습니다. 레이블이 적용된 파일의 경우 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) PowerShell cmdlet을 실행하여 GUID(MainLabelId 또는 SubLabelId)를 확인할 수도 있습니다. 레이블에 하위 레이블이 있는 경우 항상 부모 레이블이 아니라 하위 레이블의 GUID만 지정합니다.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>전자 메일에 대한 Azure Information Protection 분류와 Exchange 메시지 분류는 어떻게 다른가요?

Exchange 메시지 분류는 전자 메일을 분류할 수 있는 이전 기능으로, Azure Information Protection 분류와는 독립적으로 구현됩니다. 

그러나 사용자가 웹용 Outlook을 사용하고 일부 모바일 메일 응용 프로그램을 사용하여 메일을 분류할 때 Azure Information Protection 분류와 해당하는 레이블 표시가 자동으로 추가되도록 두 솔루션을 통합할 수 있습니다. 

웹용 Outlook 및 이러한 모바일 메일 응용 프로그램에서 레이블을 사용할 때도 이와 동일한 방법을 사용할 수 있습니다.

구성 단계에 대해서는 [모바일 장치 레이블 지정 솔루션을 위해 Azure Information protection에 Exchange 메시지 분류 통합](../rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution)합니다. 



[!INCLUDE[Commenting house rules](../includes/houserules.md)]
