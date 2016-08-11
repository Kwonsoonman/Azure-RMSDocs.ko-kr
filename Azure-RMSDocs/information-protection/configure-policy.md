---
title: "Azure Information Protection 정책 구성 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/22/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: d4b0685176407fe3a0ff14408a1381e960033afe


---

# Azure Information Protection 정책 구성

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

분류, 레이블 지정 및 보호를 구성하려면 Azure Information Protection 정책을 구성해야 합니다. 이 정책은 [Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치한 컴퓨터에 다운로드됩니다.

Azure Information Protection의 미리 보기 릴리스에서 Azure Information Protection 정책을 구성하려면

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.

2. 허브 메뉴에서 **찾아보기**를 클릭하고 필터 상자에 **Information Protection**을 입력하기 시작합니다. 결과에서 **Azure Information Protection**을 선택합니다. 

    그러면 다음 요소를 포함하여 Azure Information Protection 정책을 구성할 수 있는 **Azure Information Protection** 블레이드가 표시됩니다.

    - 사용자의 Office 응용 프로그램에 표시되는 Information Protection 표시줄의 제목 및 도구 설명.

    - 문서 및 전자 메일을 분류할 수 있는 레이블.

    - 사용자가 문서를 저장하고 전자 메일을 보낼 때 분류를 적용할 수 있는 옵션.

    - 문서 및 전자 메일을 분류하기 위한 시작점으로 기본 레이블을 설정할 수 있는 옵션.

    - 원래보다 민감도 수준이 낮은 레이블을 선택한 경우 이유를 제공하라는 메시지를 사용자에게 표시할 수 있는 옵션.


Azure Information Protection은 **Personal**(개인), **Public**(공개), **Internal**(내부), **Confidential**(기밀) 및 **Secret**(비밀) 레이블을 포함하는 [기본 정책](configure-policy-default.md)과 함께 제공됩니다. 기본 레이블을 변경하지 않고 사용하거나, 이를 사용자 지정하거나, 삭제하고 새 레이블을 만들 수 있습니다.

Azure Information Protection 블레이드를 변경한 경우 **Save**(저장)를 클릭하여 변경 내용을 저장하거나 **Discard**(취소)를 클릭하여 마지막으로 저장된 설정으로 되돌립니다. 

원하는 변경 작업을 마쳤으면 **Publish**(게시)를 클릭합니다. 

Azure Information Protection 클라이언트는 지원되는 Office 응용 프로그램이 시작될 때마다 변경 내용을 확인하여 해당 Azure Information Protection 정책으로 변경 내용을 다운로드합니다.

## 조직의 정책 구성

다음 정보를 사용하여 Azure Information Protection 정책을 구성할 수 있습니다.

- [기본 Information Protection 정책](configure-policy-default.md)

- [전역 정책 설정을 구성하는 방법](configure-policy-settings.md)

- [새 레이블을 만드는 방법](configure-policy-new-label.md)

- [레이블을 삭제하거나 순서를 변경하는 방법](configure-policy-delete-reorder.md)

- [기존 레이블을 변경하거나 사용자 지정하는 방법](configure-policy-change-label.md)

- [보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)

- [시각적 표시를 적용하도록 레이블을 구성하는 방법](configure-policy-markings.md)

- [자동 및 권장 분류에 대한 조건을 구성하는 방법](configure-policy-classification.md)

## 다음 단계

기본 정책을 사용자 지정하는 방법에 대한 예제를 보려면 Office 응용 프로그램에서 결과 동작을 확인하고 [Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)를 참조하세요.




<!--HONumber=Jul16_HO5-->


