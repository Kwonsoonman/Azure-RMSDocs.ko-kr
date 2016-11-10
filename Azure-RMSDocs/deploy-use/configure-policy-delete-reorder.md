---
title: "레이블을 삭제하거나 순서를 변경하는 방법 | Azure Information Protection"
description: "Azure Information Protection 정책에서 구성하여 사용자의 Information Protection 표시줄에 표시되는 레이블을 삭제하거나 순서를 변경할 수 있습니다."
manager: mbaldwin
ms.date: 11/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
translationtype: Human Translation
ms.sourcegitcommit: d5b3f3fc473661022a4f17b6587d58a252d07d1a
ms.openlocfilehash: 0ecc8f58179ea71f3faf4d4816ca7dbf4087826a


---

# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Azure Information Protection에 대한 레이블을 삭제하거나 순서를 변경하는 방법

>*적용 대상: Azure Information Protection*

Azure Information Protection 정책에서 구성하여 사용자의 Information Protection 표시줄에 표시되는 레이블을 삭제하거나 순서를 변경할 수 있습니다.

![Azure Information Protection 정책에서 레이블 삭제 또는 순서 변경](../media/info-protect-contextmenu.png)

레이블 구성을 유지하되, Information Protection 표시줄에 표시되지 않도록 하려는 경우 레이블을 삭제하는 대신 사용하지 않도록 설정할 수 있습니다.

사용자가 Information Protection 표시줄에서 논리적 진행률을 볼 수 있도록 레이블의 순서를 지정합니다. 예를 들어 민감도 수준이 가장 낮은 레이블이 처음에 표시되고 민감도 수준이 가장 높은 레이블이 마지막에 표시되도록 민감도 오름차순으로 레이블을 정렬합니다. [기본 정책](configure-policy-default.md)에서는 이 구성을 사용합니다.

> [!IMPORTANT]
>둘 이상의 레이블에 적용될 수 있는 레이블에 대한 [조건](configure-policy-classification.md)을 구성한 경우 민감도 오름차순으로 레이블을 정렬해야 합니다. 이렇게 순서를 지정하면 조건을 평가할 때 민감도가 가장 높은 레이블이 적용됩니다.


이와 같이 변경하려면 다음 지침을 사용합니다.

1. 아직 그렇게 하지 않은 경우에는, 새 브라우저 창에서 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **Azure Information Protection** 블레이드에서 레이블을 삭제할지, 사용하지 않도록 설정할지 또는 순서를 변경할지에 따라 다음 작업 중 하나를 수행합니다.

    - 레이블을 삭제하려면: 마우스 오른쪽 단추를 클릭하거나 삭제할 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택하고 **Delete this label**(이 레이블 삭제)을 클릭한 다음 **Yes**(예)를 클릭하여 확인합니다. 그런 다음 **Save**(저장)를 클릭합니다. 

    - 레이블을 사용하지 않도록 설정하려면: 사용하지 않도록 설정할 레이블을 선택합니다. **Label**(레이블) 블레이드에서 **Enabled**(사용)에 대해 **Off**(끄기)를 클릭한 다음 **Save**(저장)를 클릭합니다.

    - 레이블 순서를 변경하려면: 마우스 오른쪽 단추를 클릭하거나 순서를 변경할 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택하고 레이블이 원하는 순서대로 정렬될 때까지 **Move up**(위로 이동) 또는 **Move down**(아래로 이동)을 클릭합니다. 그런 다음 **Save**(저장)를 클릭합니다. 

3. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  





<!--HONumber=Nov16_HO1-->


