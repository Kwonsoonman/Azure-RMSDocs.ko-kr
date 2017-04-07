---
title: "Azure Information Protection용 범위 지정 정책 구성"
description: "특정 사용자에 대해 다른 설정과 레이블을 구성하려면 Azure Information Protection용 범위 지정 정책을 구성해야 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 2fc0059f0cc2d7c1a0eb08d6f8ee89ea2bf4bfbd
ms.sourcegitcommit: 16fec44713c7064959ebb520b9f0857744fecce9
translationtype: HT
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>범위 지정 정책을 사용하여 특정 사용자용 Azure Information Protection 정책을 구성하는 방법

>*적용 대상: Azure Information Protection*

[Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)가 설치되어 있는 컴퓨터에 Azure Information Protection 정책을 다운로드하면 모든 사용자가 기본 정책의 설정 및 레이블 또는 글로벌 정책에 대해 구성된 변경 내용을 받게 됩니다. 특정 사용자에게 설정/레이블 변경 내용을 추가로 제공하려는 경우에는 해당 사용자용으로 구성된 **범위 지정 정책**을 만들어야 합니다.

모든 사용자는 Information Protection 표시줄 제목/도구 설명, 전역 설정, 전역 레이블이 포함된 글로벌 정책을 받게 됩니다. 특정 사용자용으로 범위 지정 정책을 구성한 경우 해당 사용자는 추가 설정과 레이블을 받습니다. 

범위 지정 정책도 레이블과 마찬가지로 Azure Portal에서 순서가 지정됩니다. 특정 사용자에게 여러 범위를 설정한 경우에는 정책을 다운로드하기 전에 해당 사용자에 대한 실제 정책을 계산합니다. 정책 순서에 따라 마지막 정책 설정이 적용됩니다. 글로벌 정책의 레이블과 사용자가 속한 범위 지정 정책의 추가 레이블이 사용자에게 표시됩니다. 

범위 지정 정책은 항상 글로벌 정책에서 레이블과 설정을 상속하므로, 범위 지정 정책을 만들거나 편집할 때는 글로벌 정책의 레이블이 표시됩니다. 범위 지정 정책을 편집할 때 글로벌 정책의 레이블을 편집할 수는 없지만 상속된 레이블에 하위 레이블을 추가할 수는 있습니다.

예를 들어 글로벌 정책에 **Confidential**이라는 레이블이 있는 경우 모든 사용자에게 이 레이블이 표시됩니다. 범위 지정 정책에서 해당 레이블을 제거하거나 순서를 변경할 수는 없습니다. 그러나 Confidential에 새 하위 레이블을 추가하는 마케팅부용 범위 지정 정책을 만들 수는 있습니다. 그러면 마케팅부의 사용자에게는 **Confidential \ Promotions**가 표시됩니다. 또한 Confidential에 새 하위 레이블을 추가하는 또 다른 범위 지정 정책을 영업부용으로 만들 수 있습니다. 그러면 영업부의 사용자에게는 **Confidential \ Partners**가 표시됩니다. 그런 후에 각 하위 레이블을 서로 다른 설정으로 구성할 수 있습니다. 이러한 하위 레이블은 개별 부서 소속 사용자에게만 표시됩니다.


Azure Information Protection용 범위 지정 정책을 구성하려면 다음을 수행합니다.

1. 새 브라우저 창에서 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. **Azure Information Protection** 블레이드로 이동합니다. 예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information Protection**을 입력합니다. 결과에서 **Azure Information Protection**을 선택합니다. 

    초기 **Azure Information Protection** 블레이드에서 **새 정책 추가**를 선택합니다. 그러면 새로 고쳐진 글로벌 정책을 표시하는 데 사용되는 두 번째 블레이드가 나타나므로 이제 새 범위 지정 정책을 구성할 수 있습니다.

3. Azure Portal에서 관리자에게만 표시되는 정책 이름과 설명을 지정합니다. 이름은 테넌트에서 고유해야 합니다. 그런 다음 **이 정책을 받을 사용자/그룹 지정**을 클릭하고 후속 블레이드에서 이 정책을 적용할 사용자와 그룹을 검색하여 선택할 수 있습니다. 이 범위 지정 정책에서 구성하는 레이블과 설정은 해당 사용자에게만 적용됩니다.

4. 이제 새 레이블을 만들거나 범위 지정 정책 설정을 구성합니다. 항상 글로벌 정책이 먼저 적용되므로 새로운 레이블로 글로벌 정책을 보완할 수 있으며 전역 설정을 재정의할 수 있습니다. 예를 들어 글로벌 정책에 기본 레이블이 지정되어 있지 않은 경우 특정 부서용의 다른 범위 지정 정책에서 다른 기본 레이블을 구성할 수 있습니다.

    레이블이나 설정 구성과 관련하여 도움이 필요한 경우 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션에 나와 있는 링크를 사용하세요.

5. Azure Information Protection 블레이드에서 변경을 수행할 때는 글로벌 정책을 편집할 때와 마찬가지로 **저장**을 클릭하여 변경 내용을 저장하거나 **취소**를 클릭하여 마지막으로 저장한 설정으로 되돌립니다. 

6. 이 범위 지정 정책에 대해 원하는 변경을 완료한 후 초기 **Azure Information Protection** 블레이드에서 이 범위 지정 정책의 적용 순서가 올바른지 확인합니다. 여러 범위 지정 정책에 대해 같은 사용자를 선택한 경우에는 정책 적용 순서가 중요합니다. 그런 후에 **게시**를 클릭합니다. 

Azure Information Protection 클라이언트는 지원되는 Office 응용 프로그램 또는 파일 탐색기가 열릴 때마다 변경 내용을 확인하여 해당 사용자에게 적용되는 글로벌 정책 또는 범위 지정 정책의 변경 내용을 다운로드합니다.

> [!TIP]
> 범위가 지정된 정책을 저장한 후에 초기 **Azure Information Protection** 블레이드의 **전체 정책 편집기**를 사용하여 Azure Information Protection 정책에서 모든 레이블을 보고 다시 구성할 수 있습니다. 이 방법을 사용하여 여러 정책(전역 정책 및 범위가 지정된 모든 정책)의 레이블을 쉽게 비교할 수 있습니다. 그러나 이 편집기에서는 레이블을 추가하거나 순서를 변경하거나, 정책 설정을 보거나 구성할 수 없습니다.

## <a name="next-steps"></a>다음 단계

기본 정책을 사용자 지정하는 방법에 대한 예제를 보려면 Office 응용 프로그램에서 결과 동작을 확인하고 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
