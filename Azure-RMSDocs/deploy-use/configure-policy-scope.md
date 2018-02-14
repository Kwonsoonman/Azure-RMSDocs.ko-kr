---
title: "Azure Information Protection에 대한 범위 지정 정책 구성"
description: "특정 사용자에 대한 다양한 설정 및 레이블을 구성하려면 Azure Information Protection에 대한 범위 지정 정책을 구성해야 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: c7aa1c3aa18a246457c00a5a61c6004e55f76b4b
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>범위 지정 정책을 사용하여 특정 사용자용 Azure Information Protection 정책을 구성하는 방법

>*적용 대상: Azure Information Protection*

[Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)가 설치된 컴퓨터에 Azure Information Protection 정책을 다운로드하면 모든 사용자는 기본 정책의 설정 및 레이블을 가져오거나 전역 정책에 대해 구성한 변경 내용을 가져옵니다. 다양한 설정 및 레이블을 사용하여 특정 사용자에 대해 이러한 정책을 보완하려면 해당 사용자에 대해 구성된 **범위 지정 정책**을 만들어야 합니다.

모든 사용자는 Information Protection 표시줄 제목 및 도구 설명, 전역 설정, 전역 레이블이 포함된 전역 정책을 수신합니다. 특정 사용자에 대한 범위 지정 정책을 구성한 경우 해당 사용자는 이러한 추가 설정 및 레이블을 수신합니다. 

레이블 같은 범위 지정 정책은 Azure Portal에서 순서대로 정렬됩니다. 한 사용자가 여러 범위에 대해 구성된 경우 해당 사용자에게 효과적인 정책을 계산하여 해당 정책이 다운로드됩니다. 정책 순서에 따라 마지막 정책 설정이 적용됩니다. 사용자에게 표시되는 레이블은 전역 정책의 레이블과 사용자가 속한 범위 지정 정책의 추가 레이블입니다. 

범위 지정 정책은 항상 전역 정책의 레이블과 설정을 상속하므로 사용자가 범위 지정 정책을 만들거나 편집하면 전역 정책의 레이블이 표시됩니다. 그러나 범위 지정 정책을 편집할 때 전역 정책의 레이블을 편집할 수는 없습니다. 하지만 이처럼 상속된 레이블에 하위 레이블을 추가할 수 있습니다.

예를 들어 전역 정책에 **Confidential**이라는 레이블이 있는 경우 모든 사용자에게 이 레이블이 표시됩니다. 범위 지정 정책을 사용하여 이 레이블을 제거하거나 순서를 변경할 수 없습니다. 하지만 Confidential에 새로운 하위 레이블을 추가하는 마케팅 부서용 범위 지정 정책을 만들어서 사용자에게 **Confidential \ Promotions**이라는 레이블을 표시할 수 있습니다. Confidential에 새로운 하위 레이블을 추가하는 영업 부서용 범위 지정 정책을 만들어서 사용자에게 **Confidential \ Partners**라는 레이블을 표시할 수도 있습니다. 그런 후 여러 설정에 대해 각 하위 레이블을 구성하면 각 부서의 사용자에게만 이 하위 레이블이 표시됩니다.

Azure Information Protection에 대한 범위 지정 정책을 구성하려면:

1. 아직 구성하지 않은 경우 새 브라우저 창을 열고 보안 관리자 또는 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. 그리고 **Azure Information Protection** 블레이드로 이동합니다. 

    예를 들어 허브 메뉴에서 **더 많은 서비스**를 클릭하고, [필터] 상자에서 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다.

3. **Azure Information Protection - 범위 지정 정책** 블레이드에서 **새 정책 추가**를 선택합니다. 그러면 기존의 전역 정책을 표시하는 **정책** 블레이드가 보이는데, 이제 이 블레이드에서 새로운 범위 지정 정책을 구성할 수 있습니다.

4. Azure Portal에서 관리자에게만 보이는 정책 이름 및 설명을 지정합니다. 이름은 테넌트에서 고유해야 합니다. 그런 다음, **이 정책을 수신하는 사용자/그룹 지정**을 선택하고 후속 블레이드에서 이 정책을 적용할 사용자 및 그룹을 선택할 수 있습니다. 이 범위 지정 정책에서 구성하는 레이블 및 설정은 해당 사용자에게만 적용됩니다.
    
    성능상의 이유로 범위 지정 정책에 대한 그룹 멤버 자격이 [캐싱됩니다](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection).

5. 이제 새 레이블을 만들거나 범위 지정 정책 설정을 구성합니다. 전역 정책이 항상 첫 번째로 적용되므로 새 레이블을 사용하여 전역 정책을 보완하고 전역 설정을 재정의할 수 있습니다. 예를 들어 글로벌 정책에서 기본 레이블이 지정되지 않은 경우 특정 부서에 대한 여러 범위 지정 정책에서 다른 기본 레이블을 구성합니다.

    레이블 또는 설정 구성에 대한 도움이 필요한 경우 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션에 포함된 링크를 사용하세요.

6. 전역 정책을 편집할 때와 마찬가지로, Azure Information Protection 블레이드에서 변경 작업을 수행한 후 **저장**을 클릭하여 변경 내용을 저장하거나 **취소**를 클릭하여 마지막으로 저장된 설정으로 되돌릴 수 있습니다. 

7. 이 범위 지정 정책을 원하는 대로 변경한 후에는 처음에 나오는 **Azure Information Protection 정책 - 범위 지정 정책** 블레이드에서 이 범위 지정 정책이 적용하려는 순서대로 되어 있는지 확인합니다. 이것은 여러 범위 지정 정책에 대해 동일한 사용자를 선택할 때 중요합니다. 순서를 변경하려면 상황에 맞는 메뉴(**...** )를 선택하고 **위로 이동** 또는 **아래로 이동**을 선택합니다. 

8. 변경 내용을 배포하려면 **게시**를 클릭합니다. 

Azure Information Protection 클라이언트는 지원되는 Office 응용 프로그램이 시작되거나 파일 탐색기가 열릴 때마다 변경 내용을 확인합니다. 클라이언트는 전역 정책 또는 해당 사용자에게 적용되는 범위 지정 정책에 변경 내용을 다운로드합니다.

> [!TIP]
> 범위 지정 정책을 저장한 후 **정책** 섹션에서 **모두 - 전체 정책 보기** 옵션을 사용하여 Azure Information Protection 정책의 모든 레이블을 살펴보고 다시 구성할 수 있습니다. 이 방법은 전역 정책과 범위 지정 정책의 레이블을 간편하게 비교할 수 있는 방법을 제공합니다. 

## <a name="next-steps"></a>다음 단계

기본 정책을 사용자 지정하는 방법에 대한 예제를 살펴보고 Office 응용 프로그램에서 결과 동작을 보려면 [Azure Information Protection에 대한 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 수행하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
