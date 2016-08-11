---
title: "Azure Information Protection에 대한 시각적 표시용 레이블을 구성하는 방법 | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 9f2d28e4f162891497a7b0518322338628118b9d


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

다음 지침을 사용하여 레이블에 대한 시각적 표시를 구성할 수 있습니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
 
2. 허브 메뉴에서 **찾아보기**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

3. **Azure Information Protection** 블레이드에서 시각적 표시에 대해 구성할 레이블을 선택합니다.

4. **Label**(레이블) 블레이드의 **Set visual marking (such as header or footer)**(시각적 표시(예: 머리글 또는 바닥글) 설정) 섹션에서 원하는 시각적 표식에 대한 설정을 구성한 다음 **Save**(저장)를 클릭합니다.

    - 머리글을 구성하려면: **Documents with this label have a header**(이 레이블이 있는 문서에 머리글 있음)에서 머리글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **On**(켜기)을 선택한 경우 머리글 텍스트, 크기, 색 및 맞춤을 지정합니다.

    - 바닥글을 구성하려면: **Documents with this label have a footer**(이 레이블이 있는 문서에 바닥글 있음)에서 바닥글을 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **On**(켜기)을 선택한 경우 바닥글 텍스트, 크기, 색 및 맞춤을 지정합니다.

    - 워터마크를 구성하려면: **Documents with this label have a watermark**(이 레이블이 있는 문서에 바닥글 있음)에서 워터마크를 원하는 경우 **On**(켜기)을 선택하고 그렇지 않은 경우 **Off**(끄기)를 선택합니다. **On**(켜기)을 선택한 경우 워터마크 텍스트, 크기, 색 및 레이아웃을 지정합니다.

5. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## 다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organization-s-policy) 섹션의 링크를 사용하세요.  





<!--HONumber=Jul16_HO5-->


