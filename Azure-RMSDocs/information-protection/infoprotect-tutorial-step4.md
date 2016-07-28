---
title: "Azure Information Protection 빠른 시작 자습서 4단계 | Azure 권한 관리"
description: "15분 이내에 완료할 수 있는 4단계를 통해 조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 4단계입니다."
author: cabailey
manager: mbaldwin
ms.date: 07/15/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: e80ea074fb1f6e571b846969b15c08cf7108b11c
ms.openlocfilehash: dcb34eb8bfee6232d32245634dc56f717257b644


---

# 4단계: 실제 분류, 레이블 지정 및 보호 작동 방식 확인 

*적용 대상: Azure Information Protection 미리 보기*

설치된 Azure Information Protection 클라이언트로 연 Word 문서가 있으므로 구성한 정책을 사용하여 문서에 레이블을 지정하고 문서를 보호하기가 얼마나 쉬운지 확인할 준비가 되었습니다.

분류와 보호는 문서를 저장할 때 수행되지만, 그 전에 저장되지 않은 문서를 사용하여 레이블을 적용하고 변경하기가 얼마나 쉬운지 확인합니다.

### 수동으로 기본 레이블을 변경하려면:

- Information Protection 표시줄에서 **Internal**(내부) 옆에 있는 Edit label(레이블 편집) 아이콘을 클릭합니다. 사용 가능한 레이블이 표시됩니다. **Personal**(비공개)을 선택합니다. 그러면 분류 수준을 낮추는 이유를 선택하는 메시지가 표시됩니다. **This file no longer requires that classification**(이 파일에 더 이상 해당 분류가 필요하지 않음)을 선택하고 **Confirm**(확인)을 클릭합니다.  

    **Sensitivity**(민감도) 값이 **Personal**(비공개)로 변경되는 것을 확인할 수 있습니다.

    ![Azure Information Protection 빠른 시작 자습서 4단계 - 낮추는 이유를 확인하는 메시지가 표시됨](../media/confirm-lowering.png)

### 분류를 완전히 제거하려면:

- Information Protection 표시줄에서 **Personal**(비공개) 옆에 있는 Edit label(레이블 편집) 아이콘을 클릭합니다. 사용 가능한 레이블이 표시됩니다. 그러나 이번에는 레이블 중 하나를 선택하는 대신 Remove label(레이블 제거) 아이콘을 클릭합니다. **OK**(확인)를 클릭하여 확인하고 이 작업에 대한 근거를 제공합니다.  

    **Sensitivity**(민감도) 값에 **Not set**(설정 안 함)이 표시되며, 이는 기본 레이블을 설정하지 않은 경우 사용자에게 처음에 표시되는 내용입니다.

    ![Azure Information Protection 빠른 시작 자습서 4단계 - 분류 제거](../media/sensitivity-not-set.png)


### 레이블 지정 및 자동 보호에 대한 권장 메시지를 확인하려면:

1. Word 문서에서 유효한 신용 카드 번호(예: **4242-4242-4242-4242**)를 입력합니다. 

2. 문서를 저장합니다(원하는 파일 이름, 원하는 위치 사용). 

3. 이제 **It is recommended to label this file as Confidential**(이 파일을 기밀로 레이블을 지정하는 것이 좋습니다.) 메시지가 표시됩니다. **Change now**(지금 변경)를 클릭합니다.

    ![Azure Information Protection 빠른 시작 자습서 4단계 - 권장 메시지](../media/change-now.png)

    즉시 **Sensitivity: Confidential**(민감도: 기밀) 바닥글 외에 페이지에 걸쳐 조직 이름의 워터마크가 표시되는 것을 볼 수 있습니다. 

    RMS 템플릿을 적용하는 옵션을 선택한 경우 문서는 지정한 Azure 권한 관리 템플릿으로도 보호되며, 이는 **파일** 탭을 클릭하고 **문서 보호**에 대한 정보를 보고 확인할 수 있습니다. 기본 기밀 템플릿을 사용한 경우 문서는 내부 사용자로 제한되고(조직 외부의 사용자는 문서를 열 수 없음) 해당 내용을 복사하거나 인쇄할 수 없다는 정보가 표시됩니다. 문서의 소유자는 문서에서 복사하고 문서를 인쇄할 수 있지만, 조직의 다른 사용자에게 문서를 메일로 보내는 경우 해당 사용자는 이러한 작업을 수행할 수 없습니다.

> [!NOTE]
>이러한 단계를 완료하는 데 문제가 있는 경우 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다. 
>
>**Microsoft Azure Information Protection** 대화 상자에서 **Send feedback**(의견 보내기)을 클릭합니다. 그러면 Information Protection 팀에 메일이 전송되고 자동으로 PC에서 로그 파일이 첨부되어 문제 진단에 도움을 줍니다.

##  다음 단계

이제 기본 Azure Information Protection 정책, 이러한 정책의 사용자 지정 방법 및 Word 문서에 대해 레이블 지정이 작동하는 방식을 확인했으므로, 다른 설정을 사용해 보고 Azure Information Protection을 지원하는 다른 Office 프로그램(Excel, PowerPoint, Outlook)에서 이러한 설정이 작동하는 방식을 확인해 보세요. Azure Information Protection 클라이언트를 설치할 때 이러한 응용 프로그램이 열려 있었던 경우에는 이러한 응용 프로그램을 닫았다가 다시 연 후 Azure Information Protection에서 이러한 응용 프로그램을 사용해 보세요.

예를 들어 Information Protection 표시줄의 기본 제목인 **Sensitivity**(민감도)를 원하는 제목으로 변경할 수 있습니다. 도구 설명, 레이블 색, 레이블 순서 및 레이블 이름을 변경할 수 있습니다. 새 레이블을 만들고 고유한 자동 규칙을 정의할 수 있습니다. 크기, 색을 구성하여 워터마크를 미세 조정하고 대각선에서 가로로 변경할 수 있습니다.

Excel에서 워터마크를 사용하는 경우 워터마크는 페이지 레이아웃 및 인쇄 미리 보기 모드와 인쇄 시에만 표시됩니다.

Azure 포털에서 Information Protection 정책에 대한 설정을 변경할 때마다 정책을 **저장**한 다음 **게시**해야 합니다. 여러 블레이드에서 변경할 수 있으므로 모든 블레이드에 **저장** 단추가 활성화된 상태(저장되지 않은 변경 내용이 있다는 의미)로 표시되지 않는지 확인하는 것이 좋습니다. 새 변경 내용을 게시할 때 Office 응용 프로그램이 열려 있었던 경우 응용 프로그램을 닫았다가 다시 열어 최신 정책을 다운로드합니다.

테스트를 마쳤으면 [Azure Information Protection 질문과 대답](faq.md)을 살펴보는 것이 좋습니다.




<!--HONumber=Jul16_HO3-->


