---
title: "Azure Information Protection에 대한 시각적 표시용 레이블을 구성하는 방법 | Azure Rights Management"
description: "문서 또는 전자 메일 메시지에 레이블을 할당하는 경우 선택한 분류를 쉽게 볼 수 있도록 몇 가지 옵션을 선택할 수 있습니다. 이러한 시각적 표시는 머리글, 바닥글 및 워터마크입니다."
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: c73b6e3fe114625c16a7c2e799162902ba26e4cf


---

# Azure Information Protection에 대한 시각적 표시용 레이블을 구성하는 방법

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

문서 또는 전자 메일 메시지에 레이블을 할당하는 경우 선택한 분류를 쉽게 볼 수 있도록 몇 가지 옵션을 선택할 수 있습니다. 이러한 시각적 표시는 머리글, 바닥글 및 워터마크입니다.

시각적 표시는 레이블이 적용될 때 및 문서가 저장될 때 Word, Excel 및 PowerPoint 문서에 적용됩니다. 전자 메일 메시지의 경우 시각적 표시는 전자 메일 메시지가 전송될 때 적용됩니다.

이러한 시각적 표식에 대한 추가 정보:

- 머리글 및 바닥글은 Word, Excel, PowerPoint 및 Outlook에 적용됩니다.

- 워터마크는 Word, Excel 및 PowerPoint에 적용됩니다.

    - Excel: 페이지 레이아웃 및 인쇄 미리 보기 모드에 있을 때와 인쇄할 때만 워터마크가 표시됩니다.

    - PowerPoint: 마스터 슬라이드에 배경 이미지로 워터마크가 적용됩니다.

- 텍스트 문자열을 지정할 수도 있고, [변수](#using-variables-in-the-text-string)를 사용하여 머리글, 바닥글 또는 워터마크를 적용할 때 텍스트 문자열을 동적으로 만들 수도 있습니다. 

다음 지침을 사용하여 레이블에 대한 시각적 표시를 구성할 수 있습니다.

1. 아직 로그인하지 않은 경우 [Azure 포털](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **찾아보기**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **Azure Information Protection** 블레이드에서 시각적 표시에 대해 구성할 레이블을 선택합니다.

3. **Label**(레이블) 블레이드의 **Set visual marking (such as header or footer)**(시각적 표시(예: 머리글 또는 바닥글) 설정) 섹션에서 원하는 시각적 표식에 대한 설정을 구성한 다음 **Save**(저장)를 클릭합니다.

    - 머리글을 구성하려면: **Documents with this label have a header**(이 레이블이 있는 문서에 머리글 있음)에서 머리글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **On**(켜기)을 선택한 경우 머리글 텍스트, 크기, 색 및 맞춤을 지정합니다.
    
    - 바닥글을 구성하려면: **Documents with this label have a footer**(이 레이블이 있는 문서에 바닥글 있음)에서 바닥글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **On**(켜기)을 선택한 경우 바닥글 텍스트, 크기, 색 및 맞춤을 지정합니다.
    
    - 워터마크를 구성하려면: **Documents with this label have a watermark**(이 레이블이 있는 문서에 바닥글 있음)에서 워터마크를 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **On**(켜기)을 선택한 경우 워터마크 텍스트, 크기, 색 및 레이아웃을 지정합니다. 

4. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## 텍스트 문자열에 변수 사용

머리글, 바닥글 또는 워터마크에 대한 텍스트 문자열에 다음 변수를 사용할 수 있습니다.

- `${Item.Label}` - 선택한 레이블 예: 내부

- `${Item.Name}` - 파일 이름 또는 메일 제목 예: JulySales.docx

- `${Item.Location}` - 문서의 경우 경로 및 파일 이름, 메일의 경우 메일 제목 예: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` - 문서 또는 메일의 소유자, Windows 로그인 사용자 이름별 예: rsimone

- `${User.PrincipalName}` - 문서 또는 메일의 소유자, Azure Information Protection 클라이언트 로그인 메일 주소(UPN)별 예: rsimone@vanarsdelltd.com

- `${Event.DateTime}` - 선택한 레이블을 설정한 날짜 및 시간 예: 2016년 8월 16일 오후 1시 30분
    
예: 비밀 레이블 바닥글에 대해 `Document: ${item.name}  Classification: ${item.label}` 문자열을 지정하는 경우 문서화된 명명된 project.docx에 적용되는 바닥글 텍스트는 **Document: project.docx  Classification: Secret**입니다.

## 다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organization-s-policy) 섹션의 링크를 사용하세요.  





<!--HONumber=Aug16_HO4-->


