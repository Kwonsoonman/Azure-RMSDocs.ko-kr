---
title: Azure Information Protection 레이블에 대한 시각적 표시 구성 - AIP
description: 문서 또는 메일 메시지에 레이블을 할당하는 경우 선택한 분류를 쉽게 볼 수 있도록 몇 가지 옵션을 선택할 수 있습니다. 이러한 시각적 표시는 머리글, 바닥글 및 워터마크입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: 3f94e9b1993573e8fe392dc75bcf999452bab626
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023977"
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Azure Information Protection에 대한 시각적 표시용 레이블을 구성하는 방법

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

문서 또는 메일 메시지에 레이블을 할당하는 경우 선택한 분류를 쉽게 볼 수 있도록 몇 가지 옵션을 선택할 수 있습니다. 이러한 시각적 표시는 머리글, 바닥글 및 워터마크입니다. 

이러한 시각적 표시에 대한 추가 정보:

- 머리글 및 바닥글은 Word, Excel, PowerPoint 및 Outlook에 적용됩니다.

- 워터마크는 Word, Excel 및 PowerPoint에 적용됩니다.

    - Excel: 페이지 레이아웃 및 인쇄 미리 보기 모드에 있을 때와 인쇄할 때만 워터마크가 표시됩니다.
    
    - PowerPoint: 마스터 슬라이드에 배경 이미지로 워터마크가 적용됩니다. **보기** 탭, **슬라이드 마스터**에서 **배경 그래픽 숨기기** 확인란이 선택되어 있지 않은지 확인합니다.

- Word, Excel, PowerPoint의 워터마크와 헤더 및 바닥글에서 여러 줄이 지원됩니다. Outlook에서 적용된 레이블의 헤더 또는 바닥글에 여러 줄을 지정하면 한 줄로 결합됩니다. 이 경우에는 [Word, Excel, PowerPoint, Outlook에 대해 서로 다른 시각적 표시를 설정하는](##setting-different-visual-markings-for-word-excel-powerpoint-and-outlook) 구성을 사용하세요.

- 최대 문자열 길이:
    
    - 헤더 및 바닥글에 입력할 수 있는 최대 문자열 길이는 1024자입니다. 그러나 Excel에서는 헤더 및 바닥글을 총 255자로 제한됩니다. Excel에서 헤더 및 바닥글에 긴 문자열을 입력하면 이 텍스트는 255자 이하로 잘릴 수 있습니다.
    
    - 워터마크에 입력할 수 있는 최대 문자열 길이는 255자입니다.

- 텍스트 문자열을 지정할 수도 있고, [변수](#using-variables-in-the-text-string)를 사용하여 머리글, 바닥글 또는 워터마크를 적용할 때 텍스트 문자열을 동적으로 만들 수도 있습니다.

- Word, PowerPoint, Outlook에 더해 이제 Excel에서도 다양한 색상의 시각적 표시가 지원됩니다.

- 시각적 표시는 한 언어만 지원합니다.

## <a name="when-visual-markings-are-applied"></a>시각적 표시가 적용되는 경우

메일 메시지의 경우 시각적 표시는 메일 메시지가 Outlook에서 전송될 때 적용됩니다.

문서의 경우 시각적 표시는 다음과 같이 적용됩니다.

- Office 앱에서 레이블의 시각적 표시는 레이블이 적용될 때 적용됩니다. 또한 시각적 표시는 레이블이 지정된 문서가 열리고 문서가 처음으로 저장될 때 적용됩니다.  

- 파일 탐색기, PowerShell 또는 Azure Information Protection 스캐너를 사용하여 문서의 레이블이 지정되는 경우 시각적 표시는 즉시 적용되지 않지만 해당 문서가 Office 앱에서 열리고 문서가 처음으로 저장될 때 Azure Information Protection 클라이언트에 의해 적용됩니다.
    
    SharePoint Online, OneDrive 또는 비즈니스용 OneDrive에 저장된 파일에 대해 Office 2016에서 [자동 저장](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5)을 사용하는 경우 예외: 자동 저장이 켜져 있으면 [고급 클라이언트 설정](./rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background)을 구성하여 백그라운드에서 계속해서 실행되도록 분류를 켜지 않으면 시각적 표시가 적용되지 않습니다. 

## <a name="to-configure-visual-markings-for-a-label"></a>레이블에 대해 시각적 표시를 구성하려면

다음 지침을 사용하여 레이블에 대한 시각적 표시를 구성할 수 있습니다.

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 추가하거나 변경할 시각적 표시가 포함된 레이블을 선택합니다.

3. **레이블** 블레이드의 **Set visual marking (such as header or footer)**(시각적 표시(예: 머리글 또는 바닥글) 설정) 섹션에서 원하는 시각적 표시에 대한 설정을 구성한 다음, **저장**을 클릭합니다.
    
    - 머리글을 구성하려면: **Documents with this label have a header**(이 레이블이 있는 문서에 머리글 있음)에서 머리글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **설정**을 선택한 경우 머리글에 대한 텍스트, 크기, [글꼴](#setting-the-font-name), [색](#setting-the-font-color) 및 맞춤을 지정합니다.
    
    - 바닥글을 구성하려면: **Documents with this label have a footer**(이 레이블이 있는 문서에 바닥글 있음)에서 바닥글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **설정**을 선택한 경우 바닥글에 대한 텍스트, 크기, [글꼴](#setting-the-font-name), [색](#setting-the-font-color) 및 맞춤을 지정합니다.
    
    - 워터마크를 구성하려면: **Documents with this label have a watermark**(이 레이블이 있는 문서에 바닥글 있음)에서 워터마크를 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **설정**을 선택한 경우 워터마크에 대한 텍스트, 크기, [글꼴](#setting-the-font-name), [색](#setting-the-font-color) 및 맞춤을 지정합니다.
    
**저장**을 클릭하면 변경 내용이 사용자 및 서비스에 자동으로 제공됩니다. 더 이상 별도의 게시 옵션이 없습니다.


## <a name="using-variables-in-the-text-string"></a>텍스트 문자열에 변수 사용

머리글, 바닥글 또는 워터마크에 대한 텍스트 문자열에 다음 변수를 사용할 수 있습니다.

- `${Item.Label}` - 선택한 레이블 예: 일반

- `${Item.Name}` - 파일 이름 또는 메일 제목 예: JulySales.docx

- `${Item.Location}` - 문서의 경우 경로 및 파일 이름, 메일의 경우 메일 제목 예: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` - 문서 또는 메일의 소유자, Windows 로그인 사용자 이름별 예: rsimone

- `${User.PrincipalName}` - 문서 또는 메일의 소유자, Azure Information Protection 클라이언트 로그인 메일 주소(UPN)별 예를 들어 rsimone@vanarsdelltd.com를 구성할 수 있습니다.

- `${Event.DateTime}` - 선택한 레이블을 설정한 날짜 및 시간 예: 2016년 8월 16일 오후 1시 30분

예: **일반** 레이블 바닥글에 대해 `Document: ${item.name}  Classification: ${item.label}` 문자열을 지정하는 경우 문서화된 명명된 project.docx에 적용되는 바닥글 텍스트는 **Document: project.docx  Classification: General**이 됩니다.

>[!TIP]
> 문서 또는 템플릿에 [레이블 이름을 삽입할 때도 필드 코드](faqs-infoprotect.md#can-i-create-a-document-template-that-automatically-includes-the-classification)를 사용합니다.

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Word, Excel, PowerPoint 및 Outlook에서 다양한 시각적 표시 설정

기본적으로 지정한 시각적 표시는 Word, Excel, PowerPoint 및 Outlook에서 적용됩니다. 그러나 텍스트 문자열에서 "If.App" 변수 문을 사용하는 경우 Office 응용 프로그램 형식마다 시각적 표시를 지정하고 **Word**, **Excel**, **PowerPoint** 또는 **Outlook** 값을 사용하여 응용 프로그램 형식을 식별할 수 있습니다. 또한 이러한 값을 축약할 수 있습니다. 이 작업은 동일한 If.App 문에서 하나 이상을 지정하려는 경우에 필요합니다.

다음 구문을 사용합니다.

    ${If.App.<application type>}<your visual markings text> ${If.End}

이 문의 이 구문은 대/소문자를 구분합니다.

예:

- **Word 문서에서만 헤더 텍스트를 설정합니다.**
    
    `${If.App.Word}This Word document is sensitive ${If.End}`
    
    레이블은 Word 문서 헤더에서만 "이 Word 문서는 중요합니다."라는 헤더 텍스트를 적용합니다. 헤더 텍스트는 다른 Office 응용 프로그램에 적용되지 않습니다.

- **Word, Excel, Outlook에 바닥글 텍스트를 설정하고 PowerPoint에 다른 바닥글 텍스트를 설정합니다.**
    
    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`
    
    Word, Excel 및 Outlook에서 레이블은 "이 콘텐츠는 기밀입니다."라는 바닥글 텍스트를 적용합니다. PowerPoint에서 레이블은 "이 프리젠테이션은 기밀입니다."라는 바닥글 텍스트를 적용합니다.

- **Word 및 PowerPoint에 대한 특정 워터마크 텍스트 및 Word, Excel 및 PowerPoint에 대한 워터마크 텍스트를 설정합니다.**
    
    `${If.App.WP}This content is ${If.End}Confidential`
    
    Word 및 PointPoint에서 레이블은 "이 콘텐츠는 기밀입니다."라는 워터마크 텍스트를 적용합니다. Excel에서 레이블은 "기밀"이라는 워터마크 텍스트를 적용합니다. 시각적 표시인 워터마크가 Outlook에 지원되지 않으므로 Outlook에서 레이블은 워터마크 텍스트를 사용하지 않습니다.

### <a name="setting-the-font-name"></a>글꼴 이름 설정

굴림은 머리글, 바닥 글 및 워터마크 텍스트에 대한 기본 글꼴입니다. 대체 글꼴 이름을 지정하는 경우 시각적 표시를 적용할 클라이언트 장치에서 사용할 수 있는지 확인합니다. 

지정된 글꼴을 사용할 수 없는 경우 클라이언트는 Calibri 글꼴을 사용하도록 대체합니다.

### <a name="setting-the-font-color"></a>글꼴 색 설정

사용 가능한 색 목록에서 선택하거나 색의 RGB(빨강, 녹색 및 파랑) 구성 요소에 대한 16진수 3자리 코드를 입력하여 사용자 지정 색을 지정할 수 있습니다. 예: **#DAA520**. 

이러한 코드에 대한 참조가 필요하면 MSDN 설명서의 [Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx)(이름별 색)이 유용한 시작점입니다. 또한 그림을 편집할 수 있는 많은 응용 프로그램에서 이러한 코드를 찾을 수 있습니다. 예를 들어 Microsoft 그림판을 사용하면 색상표에서 사용자 지정 색을 선택할 수 있으며 RGB 값이 자동으로 표시됩니다. 그런 다음 해당 색을 복사하면 됩니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

