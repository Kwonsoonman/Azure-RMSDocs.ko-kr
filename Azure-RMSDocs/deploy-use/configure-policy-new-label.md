---
title: 새 Azure Information Protection 레이블
description: Azure Information Protection은 사용자 지정 가능한 기본 레이블과 함께 제공되지만 사용자의 Information Protection 표시줄에 표시되는 고유의 레이블을 만들 수도 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: 5cfacba692cfd2c0e27981e8c41e45e4d9dcb3a3
ms.sourcegitcommit: 1bc4c9d6e773809893d02a6abb09aeb4ae28cb03
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2018
ms.locfileid: "34562588"
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Azure Information Protection에 대한 새 레이블을 만드는 방법

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection은 사용자 지정 가능한 기본 레이블과 함께 제공되지만 고유한 레이블을 만들 수도 있습니다.

추가 수준의 분류가 필요한 경우 새 레이블 또는 새 하위 레이블을 기존 레이블에 추가할 수 있습니다. 예를 들어 [기본 정책](configure-policy-default.md)의 마지막 레이블은 하위 레이블을 포함합니다.

레이블에 대한 첫 번째 하위 레이블을 만들 때 사용자는 더 이상 원래 부모 레이블을 선택할 수 없습니다. 필요한 경우 사용자가 동일한 설정을 적용할 수 있도록 부모 레이블 설정을 다시 만드는 새 하위 레이블을 만듭니다.

다음 지침을 사용하여 Azure Information Protection 정책에 추가할 수 있는 새 레이블을 추가합니다.

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 다음 작업 중 하나를 수행합니다.
    
    - 새 레이블을 만들려면: **Add a new label**(새 레이블 추가)을 클릭합니다.
    
    - 새 하위 레이블을 만들려면: 마우스 오른쪽 단추를 클릭하거나 하위 레이블을 만들려는 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택하고 **하위 레이블 추가**를 클릭합니다.

4. **Label**(레이블) 또는 **Sub-label**(하위 레이블) 블레이드에서 이 새 레이블에 대한 옵션을 선택하고 **Save**(저장)를 클릭합니다.
    
    표시 이름을 지정할 때 일부 문자(백슬래스, 앰퍼샌드 등)를 지정하지 못합니다. Azure Information Protection을 사용하는 일부 서비스와 응용 프로그램에서 이러한 문자를 지원할 수 없기 때문입니다. 차단된 문자 외에 **#** 문자를 지정하지 마세요.    
    
    새 레이블에는 검은색이 자동으로 할당됩니다. 색 목록에서 고유 색을 선택하거나 색의 RGB(빨강, 녹색 및 파란색) 구성 요소에 대한 16진수 3색 코드를 입력합니다. 예: **#DAA520**. 이러한 코드를 참조하려면 MSDN 설명서의 [Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx)(이름별 색)이 유용하며 Microsoft Paint와 같은 여러 사진 편집 프로그램에서도 이러한 코드를 찾을 수 있습니다. Microsoft Paint의 경우 색상표에서 사용자 지정 색을 선택하면 RGB 값이 자동으로 표시됩니다.

5. 사용자가 새 레이블을 사용할 수 있도록 하려면 **분류** >   **정책** 메뉴 옵션에서 새 레이블을 포함하는 정책을 선택합니다. **레이블 추가 또는 제거**를 선택합니다. **정책: 레이블 추가 또는 제거** 블레이드에서 **확인**을 선택하고 **저장**을 선택합니다.
    
    >[!TIP]
    >새 레이블의 경우 먼저 테스트에 사용하는 범위 지정 정책에 추가하는 것이 좋습니다. 결과에 만족하면 이 테스트 범위에서 레이블을 제거한 다음, 프로덕션에서 사용하는 정책에 레이블을 추가합니다.     
    
    레이블 추가에 대한 자세한 내용은 [레이블 추가 또는 제거 방법](configure-policy-add-remove-label.md)을 참조하세요.
    
    변경 내용은 사용자 및 서비스에 자동으로 제공됩니다. 더 이상 별도의 게시 옵션이 없습니다.

6. 사용자를 위해 이 새로운 레이블 이름 및 설명을 다른 언어로 표시하려면: [다른 언어로 레이블을 구성하는 방법](configure-policy-languages.md)에 나오는 절차를 따르세요. 

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

