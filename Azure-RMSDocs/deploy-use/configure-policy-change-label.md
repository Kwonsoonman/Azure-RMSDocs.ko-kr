---
title: "Azure Information Protection 레이블 변경"
description: "Azure Information Protection 정책에서 구성하여 사용자의 Information Protection 표시줄에 표시되는 레이블을 변경하거나 구체화할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: 343b38caa14d3f67a932eedae37ed10c55f371ff
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Azure Information Protection에 대한 기존 레이블을 변경하거나 사용자 지정하는 방법

>*적용 대상: Azure Information Protection*

Azure Information Protection 정책에서 구성하여 사용자의 Information Protection 표시줄에 표시되는 레이블을 변경하거나 구체화할 수 있습니다.

예를 들어 바닥글 또는 워터마크와 같은 시각적 표시를 적용하든 여부에 관계없이, 그리고 Azure Rights Management 보호 및 권장 분류 또는 자동 분류를 적용하는지 여부에 관계없이 레이블 또는 하위 레이블 이름, 도구 설명, 색, 순서 등을 변경할 수 있습니다.

레이블을 변경하려면 다음 지침을 사용합니다.

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 보안 관리자 또는 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 모든 사용자에게 적용되도록 전역 정책의 레이블을 변경하려면 **Azure Information Protection - 전역 정책** 블레이드 및 필요한 경우 이후 블레이드에서 변경할 레이블을 선택합니다. 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)의 레이블을 변경하려면 먼저 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그런 다음 **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

    단, 글로벌 정책 또는 선택한 범위 지정 정책의 정책 블레이드에서 레이블의 순서를 변경하려면 해당 레이블을 마우스 오른쪽 단추로 클릭하거나 레이블에 대한 상황에 맞는 메뉴를 선택한 다음 **위로 이동** 또는 **아래로 이동** 옵션을 선택합니다.

3. 변경 내용을 유지하려는 경우 블레이드를 변경할 때마다 해당 블레이드에 대해 **Save**(저장)를 클릭합니다.

4. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

5. 레이블 이름 또는 설명을 변경했으며 추가 언어에 대해 이러한 항목을 구성한 경우 Azure Information Protection 정책을 다시 내보내고 새 번역을 제공하고 변경 내용을 가져와야 합니다. 자세한 내용은 [다른 언어에 대한 레이블을 구성하는 방법](configure-policy-languages.md)을 참조하세요.

> [!TIP]
>기본 레이블 중 하나를 기본값으로 반환하려면 [기본 Information Protection 정책](configure-policy-default.md)의 정보를 사용합니다.

## <a name="next-steps"></a>다음 단계

레이블에 적용할 수 있는 옵션 구성 및 Azure Information Protection 정책의 기타 설정에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


