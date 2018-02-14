---
title: "Azure Information Protection 레이블 변경"
description: "Azure Information Protection 정책에서 구성하여 사용자가 정보 보호 표시줄에 표시하는 레이블을 변경하거나 구체화할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: f1ffd4c459f2fa194372450f5713c920422f744d
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Azure Information Protection의 기존 레이블을 변경하거나 사용자 지정하는 방법

>*적용 대상: Azure Information Protection*

Azure Information Protection 정책에서 구성하여 사용자가 정보 보호 표시줄에 표시하는 레이블을 변경하거나 구체화할 수 있습니다.

예를 들어 레이블 또는 하위 레이블 이름, 도구 설명, 색 및 순서를 변경할 수 있습니다. 레이블에 바닥글 또는 워터마크와 같은 시각적 표시를 적용할지 여부를 변경할 수 있습니다. 또한 레이블에 보호 및 권장 분류 또는 자동 분류를 적용할지 여부도 변경할 수 있습니다.

레이블을 변경하려면 다음 지침을 따릅니다.

1. 아직 변경하지 않은 경우 새 브라우저 창을 열고 보안 관리자 또는 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. 그런 다음, **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **더 많은 서비스**를 클릭하고, [필터] 상자에서 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 모든 사용자에게 적용되도록 전역 정책에서 레이블을 변경하려면, **Azure Information Protection - 전역 정책** 블레이드 및 필요에 따라 후속 블레이드에서 변경할 레이블을 선택합니다. 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에서 레이블을 변경하려면, 먼저 **정책** 메뉴 선택 항목에서 **범위 지정 정책**을 선택합니다. 그런 다음, **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

    레이블의 순서를 변경하려는 경우는 예외입니다. 정책 블레이드의 전역 정책 또는 선택한 범위 지정 정책에서 레이블을 마우스 오른쪽 단추로 클릭하거나 레이블에 대한 팝업 메뉴를 선택합니다. 그런 다음, **위로 이동** 또는 **아래로 이동** 옵션을 선택합니다.

3. 블레이드에서 변경할 때마다 해당 변경 내용을 유지하려면 해당 블레이드에서 **저장**을 클릭합니다.

4. 사용자가 변경 내용을 사용할 수 있게 하려면 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.

5. 레이블 표시 이름 또는 설명을 변경하고 이러한 항목을 추가 언어로 구성한 경우, Azure Information Protection 정책을 다시 내보내고, 새 번역을 제공한 다음, 변경 내용을 가져옵니다. 자세한 내용은 [다른 언어로 레이블을 구성하는 방법](configure-policy-languages.md)을 참조하세요.

> [!TIP]
>기본 레이블 중 하나를 기본값으로 되돌리려면 [기본 정보 보호 정책](configure-policy-default.md)의 정보를 사용합니다.

## <a name="next-steps"></a>다음 단계

레이블에 적용할 수 있는 옵션 및 Azure Information Protection 정책의 다른 설정을 구성하는 방법에 대한 자세한 내용은 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션에 있는 링크를 사용하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


