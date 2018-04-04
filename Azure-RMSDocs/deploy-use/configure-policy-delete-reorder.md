---
title: Azure Information Protection 레이블 삭제 또는 순서 변경
description: Azure Information Protection 정책에서 구성하여 사용자의 Information Protection 표시줄에 표시되는 레이블을 삭제하거나 순서를 변경할 수 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: c24cd0bb9aae5b3a6b830151579d70561d56f7e0
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Azure Information Protection에 대한 레이블을 삭제하거나 순서를 변경하는 방법

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection 정책에서 이러한 작업을 선택하여 사용자의 Information Protection 표시줄에 표시되는 레이블을 삭제하거나 순서를 변경할 수 있습니다.

![Azure Information Protection 정책에서 레이블 삭제 또는 순서 변경](../media/info-protect-contextmenu.png)

문서 및 메일에 적용된 레이블을 삭제하고 Azure Information Protection 정책을 게시하면 다음에 Azure Information Protection 클라이언트에서 열 때 해당 레이블이 이러한 문서 또는 메일에서 자동으로 제거됩니다.

그러나 레이블이 보호를 적용한 경우 해당 보호는 제거되지 않습니다. 레이블의 보호 설정은 유지되고 **보호 템플릿**에 표시됩니다. 이 템플릿을 새 레이블로 변환하거나 레이블에 연결할 수 있습니다. 이 템플릿이 유지되는 동안 삭제한 레이블과 이름이 같은 새 레이블을 만들 수 없습니다. 그렇게 하려면 다음과 같은 옵션이 있습니다.

- 템플릿을 레이블로 변환합니다. 
    
    필요한 경우 템플릿의 이름을 변경하고 보호 설정을 수정할 수 있으므로 이 작업을 수행하는 것이 좋습니다.

- PowerShell을 사용하여 템플릿의 이름을 바꾸거나 삭제합니다.
    
    이러한 작업을 수행하기 전에 다른 관리자나 서비스가 템플릿을 사용하고 있는지, 현재 이름으로 템플릿을 식별하는지 고려하세요. 템플릿으로 보호된 문서나 전자 메일을 열 필요가 없는 경우에만 템플릿을 삭제하십시오.

보호 템플릿 관리에 대한 자세한 내용은 [Azure Information Protection의 템플릿 구성 및 관리](configure-policy-templates.md)를 참조하세요.

레이블을 삭제하기 전에 사용하지 않도록 설정할지를 고려하세요. 문서 및 이메일에 적용된 레이블을 사용하지 않도록 설정하면 적용된 레이블이 이러한 문서와 이메일에서 제거되지 않지만 더 이상 사용자가 정보 보호 모음에서 선택할 수 있는 레이블로 표시되지 않습니다. 또한 레이블을 사용하지 않도록 설정했다가, 사용자가 나중에 레이블을 선택할 수 있게 하려는 경우에 간단히 다시 사용하도록 설정하여 원래 구성을 유지할 수 있습니다.

사용자가 Information Protection 표시줄에서 논리적 진행률을 볼 수 있도록 레이블의 순서를 지정합니다. 예를 들어 민감도 수준이 가장 낮은 레이블이 처음에 표시되고 민감도 수준이 가장 높은 레이블이 마지막에 표시되도록 민감도 오름차순으로 레이블을 정렬합니다. [기본 정책](configure-policy-default.md)에서는 이 구성을 사용하고 레이블 이름에 민감도 오름차순을 반영합니다.

> [!IMPORTANT]
>둘 이상의 레이블에 적용될 수 있는 레이블에 대한 [조건](configure-policy-classification.md)을 구성한 경우 민감도 오름차순으로 레이블을 정렬해야 합니다. 이렇게 순서를 지정하면 조건을 평가할 때 민감도가 가장 높은 레이블이 적용됩니다.


이와 같이 변경하려면 다음 지침을 사용합니다.

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 레이블을 모든 사용자에게 적용하려는 경우 **Azure Information Protection - 전역 정책** 블레이드에 그대로 있습니다.
    
    구성하려는 레이블이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그런 다음 **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

3. **Azure Information Protection - 전역 정책** 블레이드 또는 **정책:\<이름>** 블레이드에서 다음 작업 중 하나 이상을 수행합니다. 

    - 레이블을 삭제하려면: 마우스 오른쪽 단추를 클릭하거나 삭제할 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택하고 **Delete this label**(이 레이블 삭제)을 클릭한 다음 **Yes**(예)를 클릭하여 확인합니다. 그런 다음 **Save**(저장)를 클릭합니다. 

    - 레이블을 사용하지 않도록 설정하려면: 사용하지 않도록 설정할 레이블을 선택합니다. **Label**(레이블) 블레이드에서 **Enabled**(사용)에 대해 **Off**(끄기)를 클릭한 다음 **Save**(저장)를 클릭합니다.

    - 레이블 순서를 변경하려면: 마우스 오른쪽 단추를 클릭하거나 순서를 변경할 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택하고 레이블이 원하는 순서대로 정렬될 때까지 **위로 이동** 또는 **아래로 이동**을 클릭합니다. 그런 다음 **Save**(저장)를 클릭합니다. 

4. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

