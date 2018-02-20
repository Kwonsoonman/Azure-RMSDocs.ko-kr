---
title: "새 Azure Information Protection 레이블"
description: "Azure Information Protection은 사용자 지정 가능한 기본 레이블과 함께 제공되지만 사용자의 Information Protection 표시줄에 표시되는 고유의 레이블을 만들 수도 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: cb7af6831040bb42a3c7e3a7e8ea355f72fc433c
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Azure Information Protection에 대한 새 레이블을 만드는 방법

>*적용 대상: Azure Information Protection*

Azure Information Protection은 사용자 지정 가능한 기본 레이블과 함께 제공되지만 사용자의 Information Protection 표시줄에 표시되는 고유의 레이블을 만들 수도 있습니다.

추가 수준의 분류가 필요한 경우 새 레이블 또는 새 하위 레이블을 기존 레이블에 추가할 수 있습니다. 예를 들어 [기본 정책](configure-policy-default.md)의 마지막 레이블은 하위 레이블을 포함합니다.

다음 지침을 사용하여 Azure Information Protection 정책에 새 레이블을 추가할 수 있습니다.

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 추가하려는 새 레이블이 모든 사용자를 위한 것이면 **Azure Information Protection - 전역 정책** 블레이드에 그대로 있습니다.
    
    추가하려는 새 레이블이 [범위 지정 정책](configure-policy-scope.md)의 선택한 사용자를 위한 것이면 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그런 다음 **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

3. **Azure Information Protection - 전역 정책** 블레이드 또는 **정책:\<이름>** 블레이드에서 다음 작업 중 하나를 수행합니다.
    
    - 새 레이블을 만들려면: **Add a new label**(새 레이블 추가)을 클릭합니다.
    
    - 새 하위 레이블을 만들려면: 마우스 오른쪽 단추를 클릭하거나 하위 레이블을 만들려는 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택하고 **하위 레이블 추가**를 클릭합니다.

4. **Label**(레이블) 또는 **Sub-label**(하위 레이블) 블레이드에서 이 새 레이블에 대한 옵션을 선택하고 **Save**(저장)를 클릭합니다.
    
    새 레이블에는 검은색이 자동으로 할당됩니다. 색 목록에서 고유 색을 선택하거나 색의 RGB(빨강, 녹색 및 파란색) 구성 요소에 대한 16진수 3색 코드를 입력합니다. 예: **#DAA520**. 이러한 코드에 대한 참조가 필요한 경우 MSDN 설명서의 [Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx)(이름별 색)이 유용한 시작점이며, Microsoft 그림판과 같은 여러 사진 편집 프로그램에서도 이러한 코드를 찾을 수 있습니다. Microsoft 그림판의 경우 색상표에서 사용자 지정 색을 선택하면 RGB 값이 자동으로 표시됩니다.

5. 변경 내용을 사용자에게 제공하려면 초기 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.

6. 이 새로운 레이블 이름 및 설명을 다른 언어로 표시하려면 [다른 언어로 레이블을 구성하는 방법](configure-policy-languages.md)에 나오는 절차를 따르세요. 

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

