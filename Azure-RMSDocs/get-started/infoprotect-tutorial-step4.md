---
title: "빠른 시작 자습서 4단계 | Azure Rights Management"
description: "조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 4단계로 약 30분 만에 완료해야 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: a8bfb3be9b19718cc8a94755e19b8d2521dde323
ms.openlocfilehash: 59639e9c90c5a55d8eda44bbcc2f9efbc5b9ffb5


---

# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>4단계: 실제 분류, 레이블 지정 및 보호 작동 방식 확인 

>*적용 대상: Azure Information Protection*

설치된 Azure Information Protection 클라이언트로 연 Word 문서가 있으므로 구성한 정책을 사용하여 문서에 레이블을 지정하고 문서를 보호하기가 얼마나 쉬운지 확인할 준비가 되었습니다.

분류와 보호는 문서를 저장할 때 수행되지만, 그 전에 저장되지 않은 문서를 사용하여 레이블을 적용하고 변경하기가 얼마나 쉬운지 확인합니다.

## <a name="to-manually-change-our-default-label"></a>수동으로 기본 레이블을 변경하려면

Information Protection 표시줄에서 **Personal**(비공개) 레이블을 선택합니다. 그러면 분류 수준을 낮추는 이유를 선택하는 메시지가 표시됩니다.

![Azure Information Protection 빠른 시작 자습서 4단계 - 낮추는 이유를 확인하는 메시지가 표시됨](../media/info-protect-lower-justification.png)

**The previous label no longer applies**(이전 레이블이 더 이상 적용 안 됨)를 선택하고 **Confirm**(확인)을 클릭합니다. **Sensitivity**(민감도) 값이 **Personal**(비공개)로 변경되는 것을 확인할 수 있습니다.

## <a name="to-remove-the-classification-completely"></a>분류를 완전히 제거하려면

Information Protection 표시줄에서 **Personal(비공개)** 옆에 있는 **Edit label(레이블 편집)** 아이콘을 클릭합니다. 사용 가능한 레이블이 표시됩니다. 그러나 이번에는 레이블 중 하나를 선택하는 대신 **Remove label(레이블 제거)** 아이콘을 클릭합니다. **OK**(확인)를 클릭하여 확인하고 이 작업에 대한 근거를 제공합니다.  

**Sensitivity**(민감도) 값에 **Not set**(설정 안 함)이 표시되며, 이는 기본 레이블을 설정하지 않은 경우 사용자에게 처음에 표시되는 내용입니다.

![Azure Information Protection 빠른 시작 자습서 4단계 - 분류 제거](../media/sensitivity-not-set.png)


## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>레이블 지정 및 자동 보호에 대한 권장 메시지를 확인하려면

1. Word 문서에서 유효한 신용 카드 번호(예: **4242-4242-4242-4242**)를 입력합니다. 

2. 문서를 저장합니다(원하는 파일 이름, 원하는 위치 사용). 

3. 이제 **It is recommended to label this file as Confidential**(이 파일을 기밀로 레이블을 지정하는 것이 좋습니다.) 메시지가 표시됩니다. **Change now**(지금 변경)를 클릭합니다.

    ![Azure Information Protection 빠른 시작 자습서 4단계 - 권장 메시지](../media/change-now.png)

    기밀로 설정하는 레이블이 있는 문서 외에도 즉시 **Sensitivity: Confidential**(민감도: 기밀) 바닥글과, 페이지에 걸쳐 조직 이름의 워터마크가 적용되는 것을 볼 수 있습니다. 

    문서는 지정한 Azure 권한 관리 템플릿으로도 보호되며, 이는 **파일** 탭을 클릭하고 **문서 보호**에 대한 정보를 보고 확인할 수 있습니다. 기본 기밀 템플릿을 사용한 경우 문서는 내부 사용자로 제한되고(조직 외부의 사용자는 문서를 열 수 없음) 해당 내용을 복사하거나 인쇄할 수 없다는 정보가 표시됩니다. 문서의 소유자는 문서에서 복사하고 문서를 인쇄할 수 있지만, 조직의 다른 사용자에게 문서를 메일로 보내는 경우 해당 사용자는 이러한 작업을 수행할 수 없습니다.

지금까지 분류, 레이블 지정 및 보호 작업 방식에 대해 살펴보았으므로 이제 다른 조직의 다른 사용자와 문서를 공유할 때 보호하는 방법에 대해 확인해 보겠습니다. 문서의 사용 방식과 액세스에 대한 취소 방식을 추적할 수도 있습니다.

>[!div class="step-by-step"]
[&#171;3단계](infoprotect-tutorial-step3.md)
[5단계 &#187;](infoprotect-tutorial-step5.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


