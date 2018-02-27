---
title: "Azure Information Protection 레이블에 대한 시각적 표시 구성"
description: "문서 또는 메일 메시지에 레이블을 할당하는 경우 선택한 분류를 쉽게 볼 수 있도록 몇 가지 옵션을 선택할 수 있습니다. 이러한 시각적 표시는 머리글, 바닥글 및 워터마크입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: 03e7e2a4e2fc6dc75bd6c56c117c627e0c854f98
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Azure Information Protection에 대한 시각적 표시용 레이블을 구성하는 방법

>*적용 대상: Azure Information Protection*

문서 또는 메일 메시지에 레이블을 할당하는 경우 선택한 분류를 쉽게 볼 수 있도록 몇 가지 옵션을 선택할 수 있습니다. 이러한 시각적 표시는 머리글, 바닥글 및 워터마크입니다.

이러한 시각적 표식에 대한 추가 정보:

- 머리글 및 바닥글은 Word, Excel, PowerPoint 및 Outlook에 적용됩니다.

- 워터마크는 Word, Excel 및 PowerPoint에 적용됩니다.

    - Excel: 페이지 레이아웃 및 인쇄 미리 보기 모드에 있을 때와 인쇄할 때만 워터마크가 표시됩니다.
    
    - PowerPoint: 마스터 슬라이드에 배경 이미지로 워터마크가 적용됩니다.
    
    - 여러 줄의 텍스트를 사용할 수 있습니다.

- 텍스트 문자열을 지정할 수도 있고, [변수](#using-variables-in-the-text-string)를 사용하여 머리글, 바닥글 또는 워터마크를 적용할 때 텍스트 문자열을 동적으로 만들 수도 있습니다.

- 시각적 표식은 한 언어만 지원합니다.

## <a name="when-visual-markings-are-applied"></a>시각적 표시가 적용되는 경우

메일 메시지의 경우 시각적 표시는 메일 메시지가 Outlook에서 전송될 때 적용됩니다.

문서의 경우 시각적 표시는 다음과 같이 적용됩니다.

- Office 앱에서 레이블의 시각적 표시는 레이블이 적용될 때 적용됩니다. 또한 시각적 표시는 레이블이 지정된 문서가 열리고 문서가 처음으로 저장될 때 적용됩니다.  

- 파일 탐색기 또는 PowerShell을 사용하여 문서의 레이블이 지정되는 경우 시각적 표시는 즉시 적용되지 않지만 해당 문서가 Office 앱에서 열리고 문서가 처음으로 저장될 때 적용됩니다.

## <a name="to-configure-visual-markings-for-a-label"></a>레이블에 대해 시각적 표시를 구성하려면

다음 지침을 사용하여 레이블에 대한 시각적 표시를 구성할 수 있습니다.

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 레이블을 모든 사용자에게 적용하려는 경우 **Azure Information Protection - 전역 정책** 블레이드에 그대로 있습니다.
    
    구성하려는 레이블이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그런 다음 **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

3. **Label**(레이블) 블레이드의 **Set visual marking (such as header or footer)**(시각적 표시(예: 머리글 또는 바닥글) 설정) 섹션에서 원하는 시각적 표식에 대한 설정을 구성한 다음 **Save**(저장)를 클릭합니다.
    
    - 머리글을 구성하려면: **Documents with this label have a header**(이 레이블이 있는 문서에 머리글 있음)에서 머리글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **설정**을 선택한 경우 머리글에 대한 텍스트, 크기, [글꼴](#setting-the-font-name), [색](#setting-the-font-color) 및 맞춤을 지정합니다.
    
    - 바닥글을 구성하려면: **Documents with this label have a footer**(이 레이블이 있는 문서에 바닥글 있음)에서 바닥글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **설정**을 선택한 경우 바닥글에 대한 텍스트, 크기, [글꼴](#setting-the-font-name), [색](#setting-the-font-color) 및 맞춤을 지정합니다.
    
    - 워터마크를 구성하려면: **Documents with this label have a watermark**(이 레이블이 있는 문서에 바닥글 있음)에서 워터마크를 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **설정**을 선택한 경우 워터마크에 대한 텍스트, 크기, [글꼴](#setting-the-font-name), [색](#setting-the-font-color) 및 맞춤을 지정합니다.

4. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## <a name="using-variables-in-the-text-string"></a>텍스트 문자열에 변수 사용

머리글, 바닥글 또는 워터마크에 대한 텍스트 문자열에 다음 변수를 사용할 수 있습니다.

- `${Item.Label}` - 선택한 레이블 예: 내부

- `${Item.Name}` - 파일 이름 또는 메일 제목 예: JulySales.docx

- `${Item.Location}` - 문서의 경우 경로 및 파일 이름, 메일의 경우 메일 제목 예: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` - 문서 또는 메일의 소유자, Windows 로그인 사용자 이름별 예: rsimone

- `${User.PrincipalName}` - 문서 또는 메일의 소유자, Azure Information Protection 클라이언트 로그인 메일 주소(UPN)별 예를 들어 rsimone@vanarsdelltd.com를 구성할 수 있습니다.

- `${Event.DateTime}` - 선택한 레이블을 설정한 날짜 및 시간 예: 2016년 8월 16일 오후 1시 30분

예: **일반** 레이블 바닥글에 대해 `Document: ${item.name}  Classification: ${item.label}` 문자열을 지정하는 경우 문서화된 명명된 project.docx에 적용되는 바닥글 텍스트는 **Document: project.docx  Classification: General**이 됩니다.

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Word, Excel, PowerPoint 및 Outlook에서 다양한 시각적 표시 설정

이 설정은 현재 미리 보기로 제공되며 Azure Information Protection 클라이언트의 미리 보기 버전이 필요합니다.

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

이 설정은 현재 미리 보기로 있습니다.

굴림은 머리글, 바닥 글 및 워터마크 텍스트에 대한 기본 글꼴입니다. 대체 글꼴 이름을 지정하는 경우 시각적 표식을 적용할 클라이언트 장치에서 사용할 수 있는지 확인합니다. 그렇지 않으면 사용할 글꼴이 명확하지 않습니다. 

Azure Information Protection 클라이언트의 미리 보기 버전이 설치되어 있고 지정된 글꼴을 사용할 수 없는 경우 클라이언트는 Calibri 글꼴을 사용하도록 대체합니다.

### <a name="setting-the-font-color"></a>글꼴 색 설정

사용 가능한 색 목록에서 선택하거나 색의 RGB(빨강, 녹색 및 파랑) 구성 요소에 대한 16진수 3자리 코드를 입력하여 사용자 지정 색을 지정할 수 있습니다. 예: **#DAA520**. 

이러한 코드에 대한 참조가 필요하면 MSDN 설명서의 [Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx)(이름별 색)이 유용한 시작점입니다. 또한 그림을 편집할 수 있는 많은 응용 프로그램에서 이러한 코드를 찾을 수 있습니다. 예를 들어 Microsoft 그림판을 사용하면 색상표에서 사용자 지정 색을 선택할 수 있으며 RGB 값이 자동으로 표시됩니다. 그런 다음 해당 색을 복사하면 됩니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
