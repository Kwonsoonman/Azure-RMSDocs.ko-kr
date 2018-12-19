---
title: Azure Information Protection 정책에 대해 레이블을 추가 또는 제거 - AIP
description: 모든 사용자에 대한 전역 정책 또는 사용자 하위 집합에 대한 범위 지정 정책에 대해 Azure Information Protection 레이블을 추가하거나 제거합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: 367426324af487cbdf0ddaac53eb86aa89c168b7
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304860"
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Azure Information Protection 정책에 대해 레이블을 추가 또는 제거

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection 레이블을 만든 후에 사용자가 사용할 수 있도록 이 레이블을 정책에 추가할 수 있습니다. 모든 사용자에 대한 레이블인 경우 전역 정책에 레이블을 추가합니다. 사용자 하위 집합에 대한 레이블인 경우 범위 지정 정책에 레이블을 추가합니다. 현재 레이블은 하나의 정책에만 추가할 수 있습니다. 하위 레이블을 추가하려면 부모 레이블이 동일한 정책 또는 전역 정책에 포함되어야 합니다.

정책에 포함되어 있는 레이블의 경우 정책에서 해당 레이블을 제거할 수 있습니다. 이 동작은 레이블을 삭제하지 않습니다. 다른 정책에서 사용 가능하도록 남아 있습니다.

아직 레이블을 만들지 않은 경우 [Azure Information Protection에 대한 새 레이블을 만드는 방법](configure-policy-new-label.md)을 참조하세요.

레이블이 사용자 하위 집합에 적용되도록 범위 지정 정책을 만들어야 하는 경우 [범위 지정 정책을 사용하여 특정 사용자용 Azure Information Protection 정책을 구성하는 방법](configure-policy-scope.md)을 참조하세요.

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>정책에 대해 레이블을 추가하거나 제거하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **분류** > **정책** 메뉴 옵션에서: 추가하거나 제거할 레이블이 모든 사용자에게 적용되는 경우 **Azure Information Protection** - **정책** 블레이드에서 **글로벌**을 선택합니다.

    추가하거나 제거할 레이블이 사용자 하위 집합에 적용될 경우에는 범위 지정 정책을 선택합니다.

3. **정책** 블레이드에서 **레이블 추가 또는 제거**를 선택합니다.

4. **정책: 레이블 추가 또는 제거** 블레이드에 확인란이 선택된 모든 레이블(이미 정책에 포함된 경우)이 표시되고 **정책** 열에 해당 정책 이름이 표시됩니다.
     
    하위 레이블은 들여쓰기로 표시됩니다. 전역 정책에서 상속된 레이블은 범위 지정 정책에서 사용할 수 없음으로 표시됩니다.
    
    다음 동작 중 하나 이상을 수행한 다음, **확인**을 클릭합니다.
    
    - 레이블을 추가하기 위해 선택하면 선택된 확인란이 추가됩니다.
    
    - 레이블을 제거하려면 해당 확인란의 선택을 취소합니다.
  
5. 변경 내용을 저장하려면 **Save**(저장)를 클릭합니다.
   
    변경 내용은 사용자 및 서비스에 자동으로 제공됩니다. 더 이상 별도의 게시 옵션이 없습니다.


## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

