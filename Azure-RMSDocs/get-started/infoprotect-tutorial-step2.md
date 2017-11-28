---
title: "빠른 시작 자습서 2단계 - AIP"
description: "Azure Information Protection를 빠르게 사용해 보기 위한 소개 자습서 2단계 - 정책 구성"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/17/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: 0e10a1809aaf792ac8c5960e30917aabd5c44548
ms.sourcegitcommit: 0ef66a8479b4105c00bf1b1df46d2ddf044b7670
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2017
---
# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>2단계: Azure Information Protection 정책 구성 및 게시

>*적용 대상: Azure Information Protection*

Azure Information Protection은 구성 없이 사용할 수 있는 기본 정책과 함께 제공되지만, 해당 정책을 살펴보고 몇 가지를 변경합니다.

1. [1단계](infoprotect-tutorial-step1.md)에 이어서 계속 Azure Portal에서 **전역 정책**을 선택하여 **정책: 전역** 블레이드를 엽니다. 이 블레이드는 나중에 서비스에 다시 연결되면 자동으로 열리며 테넌트에 대해 생성되는 기본 Information Protection 정책을 표시합니다.

2. 몇 분간 표시되는 레이블에 친숙해지는 시간을 가집니다.
    
    - 분류 레이블: **개인**, **공개**, **일반**, **기밀** 및 **극비**. 마지막 두 개의 레이블은 확장되어 하위 레이블을 표시함으로써 분류가 하위 범주를 포함할 수 있는 방식의 예를 제공합니다.
    
       > [!NOTE]
       > 기본 정책은 이 자습서의 기본 정책과 약간 다르게 보일 수 있습니다. 예를 들어 **일반** 대신 **내부** 레이블이, **극비** 대신 **비밀**이 있을 수 있습니다. **받는 사람만**이라는 하위 레이블은 없을 수도 있으며, 레이블이 전혀 없을 수도 있습니다. 이러한 변경 내용은 테넌트용으로 작성된 시기에 따라 기본 정책의 버전이 달라지기 때문입니다. 또는 자습서를 시작하기 전에 직접 레이블을 편집했을 수 있습니다.
       > 
       > 기본 정책이 다르게 보이는 경우에도 여전히 이 자습서를 사용할 수 있지만, 뒤에 나오는 지침과 그림을 사용할 때 이러한 변경 내용을 인식해야 합니다. 현재 기본 정책과 일치하도록 기본 정책을 수정하려면 [기본 Azure Information Protection 정책](../deploy-use/configure-policy-default.md)을 참조하세요.
    
    - 기본 구성을 사용하는 경우 일부 레이블에 구성된 시각적 표시가 없습니다. 시각적 표식은 바닥글, 머리글 및 워터마크입니다. 기본 정책에 따라 일부 레이블에 보호가 설정될 수도 있습니다. 예를 들면 다음과 같습니다. 
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](../media/info-protect-policy-default-labelsv2.png)
    
3. 또한 일부 정책 설정이 있음도 알 수 있습니다. 예를 들어 기본 레이블 집합이 없으며, 문서와 전자 메일에 레이블이 필요하지 않으며, 레이블을 변경할 때 사용자가 근거를 제공하지 않아도 됩니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>기본 레이블 및 근거에 대한 프롬프트 설정 변경

이 자습서에서는 몇 가지 정책 설정의 작동 방식을 확인할 수 있도록 이러한 설정을 변경합니다.

1. **기본 레이블 선택**에서 **일반**을 선택합니다. 

    이전 버전의 정책을 사용하고 있어 이 레이블이 없는 경우 같은 레이블로 **내부**를 선택합니다.

2. **분류 레이블 낮추기, 레이블 제거 또는 보호 제거를 설정하려면 근거를 제공해야 합니다.**에서 이 옵션을 **켜기**로 설정합니다.

## <a name="creating-a-new-label-for-protection-visual-markers-and-a-condition-to-prompt-for-classification"></a>보호를 위한 새 레이블, 시각적 표식 및 분류를 위한 메시지 표시 조건 만들기

이제 **기밀**에 대한 새 하위 레이블을 만듭니다.

1. **기밀**을 마우스 오른쪽 단추로 클릭하고 **하위 레이블 추가**를 선택합니다.
    
    **기밀**이라는 레이블이 없는 경우 다른 레이블을 선택하거나 대신 새 레이블을 만들고 약간의 차이는 있지만 계속 자습서를 따를 수 있습니다.

2. **하위 레이블** 블레이드에서 레이블 이름을 **금융**으로 지정하고 **직원으로만 제한되는 금융 정보를 포함하는 기밀 데이터**라는 설명을 추가합니다.
    
    이 텍스트는 선택한 레이블의 용도를 설명하고 사용자에게 도구 설명으로 표시되어 사용자가 선택할 레이블을 결정하는 데 도움을 줍니다.

3. **이 레이블을 포함하는 문서 및 메일에 대한 권한 설정**에서 **보호**를 선택하고 **보호**를 선택합니다.
    
    ![Azure Information Protection 레이블에 대해 구성된 보호](../media/info-protect-protection-bar-configured.png) 
    
4. **보호** 블레이드에서 **Azure(클라우드 키)**가 선택되었는지 확인합니다. 이 옵션은 Azure Rights Management 서비스를 사용하여 문서 및 전자 메일을 보호합니다. 또한 **사용 권한 설정**도 선택되었는지 확인합니다. 그런 다음 **권한 추가**를 선택합니다.

5. **권한 추가** 블레이드에서 **\<조직 이름> 추가 - 모든 멤버**를 선택합니다. 예를 들어 조직 이름이 VanArsdel Ltd인 경우 선택할 다음 옵션이 표시됩니다.
    
    ![모든 멤버에게 Azure Information Protection 레이블에 대한 보호 권한 부여](../media/info-protect-protection-all-members.png) 
    
    이 옵션을 선택하면, 권한을 부여할 수 있는 조직의 모든 사용자가 자동으로 선택됩니다. 그러나 테넌트에서 그룹 또는 사용자를 찾아보고 검색할 수 있는 다른 옵션에서 볼 수 있습니다. 또는 **세부 정보 입력** 옵션을 선택하면 개별 메일 주소 또는 다른 조직의 모든 사용자도 지정할 수 있습니다.

6. 권한의 경우 미리 설정된 옵션 중에서 **검토자**를 선택합니다. 이 권한 수준에서 자동으로 모든 권한이 아니라 나열된 일부 권한을 부여하는 방식을 볼 수 있습니다.
    
    ![공동 작성자에게 Azure Information Protection 레이블에 대한 보호 권한 부여](../media/info-protect-protection-reviewer.png)
    
    다른 권한 수준을 선택하거나 **사용자 지정** 옵션을 사용하여 개별 사용 권한을 지정할 수 있습니다. 그러나 이 자습서에서는 **검토자** 옵션을 유지합니다. 나중에 다른 권한으로 실험하고 해당 권한에서 지정된 사용자가 보호된 문서 또는 메일에서 수행할 수 있는 작업을 제한하는 방법을 읽을 수 있습니다.

7. **확인**을 클릭하여 이 **권한 추가** 블레이드를 닫으면 **보호** 블레이드가 구성을 반영하도록 업데이트되는 방법을 볼 수 있습니다. 예를 들면 다음과 같습니다.
    
     ![Azure Information Protection 레이블에 대한 권한 구성을 보여 주는 보호 블레이드](../media/info-protect-protection-configured.png)
    
    **권한 추가**를 선택하면 **권한 추가** 블레이드가 다시 열려 더 많은 사용자를 추가하고 이들에게 서로 다른 권한을 부여할 수 있습니다. 예를 들어 특정 그룹에는 대한 보기 권한만 부여합니다. 그러나 이 자습서에서는 모든 사용자에 대해 하나의 권한 집합을 유지합니다.

8. 콘텐츠 만료 및 오프라인 액세스에 대한 기본값을 검토하고 유지한 다음 **확인**을 클릭하여 이 **보호** 블레이드를 저장하고 닫습니다.

8. **하위 레이블** 블레이드로 돌아가서 **시각적 표시 설정** 섹션을 찾습니다.
    
    **이 레이블이 포함된 문서에는 바닥글이 있습니다.** 설정에 대해 **켜기**를 클릭한 다음 **텍스트** 상자에 **기밀로 분류됨**을 입력합니다. 
    
    **Documents with this label have a watermark**(이 레이블이 있는 문서는 워터마크를 포함함) 설정에서 **On**(켜기)을 클릭하고 **Text**(텍스트) 상자에 조직 이름을 입력합니다. 예를 들어 **VanArsdel, Ltd**를 입력합니다. 
    
    이러한 시각적 표식의 모양을 변경할 수는 있지만, 지금은 이러한 설정을 기본값으로 그대로 유지합니다.
    
9. **Configure conditions for automatically applying this label**(이 레이블을 자동으로 적용하기 위한 조건 구성) 섹션으로 이동합니다.
    
    **새 조건 추가**를 클릭한 다음 **조건** 블레이드에서 다음을 선택합니다.
    
    a. **조건 형식 선택**: **정보 유형**의 기본값을 유지합니다.
    
    b. **정보 유형 선택** 검색 상자에 **신용 카드 번호**를 입력합니다. 그런 다음 검색 결과에서 **신용 카드 번호**를 선택합니다.
    
    c. **Minimum number of occurrences**(최소 발생 횟수): 기본값을 **1**로 유지합니다.
    
    d. **Count occurrences with unique values only**(고유 값이 있는 발생만 계산): 기본값을 **Off**(끄기)로 유지합니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 신용 카드 조건 구성](../media/step2-configure-condition.png)
    
    **저장**을 클릭하여 **하위 레이블** 블레이드로 돌아갑니다.

10. **하위 레이블** 블레이드에서 **신용 카드 번호**가 **조건 이름**으로 표시되고 **발생 빈도**가 **1**로 표시됩니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 신용 카드 조건 구성](../media/step2-see-condition.png)

11. **이 레이블이 적용되는 방법 선택**의 경우: 기본값 **권장**을 유지하고 기본 정책 팁을 변경하지 않습니다. 

12. **Enter notes for internal housekeeping**(내부 하우스키핑을 위한 메모 입력) 상자에 **For testing purposes only**(테스트 전용)를 입력합니다.

13. 이 **하위 레이블** 블레이드에서 **저장**을 클릭합니다. 그런 다음 **정책:글로벌** 블레이드에서 **저장**을 다시 클릭합니다.
    
    이제 시각적 표시 및 보호에 대해 구성된 새 하위 레이블을 볼 수 있습니다. 예를 들면 다음과 같습니다.

    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책 구성됨](../media/info-protect-policy-configuredv2.png)
    
    또한 설정은 기본 레이블 및 근거에 대한 변경 내용으로 구성됩니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 설정 구성됨](../media/info-protect-settings-configuredv2.png)
    
14. 변경을 수행하고 저장했으므로 이러한 내용을 사용자에게 제공하기 위해 **게시**를 클릭하고 **예**를 클릭하여 확인합니다.

    ![Azure Information Protection 빠른 시작 자습서 3단계 - 구성된 정책 게시](../media/info-protect-publish.png)

이 자습서를 완료한 후 Azure 포털을 닫거나, 열어 둔 채로 추가 구성 옵션을 사용해 볼 수 있습니다.

기본 정책을 살펴보고 몇 가지를 변경했으므로 다음 단계는 Azure Information Protection 클라이언트를 설치하는 것입니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|기본 정책 및 다양한 버전에 대한 정보|[기본 Azure Information Protection 정책](../deploy-use/configure-policy-default.md)|
|정책에 대한 구성 옵션 정보|[Azure Information Protection 정책 구성](../deploy-use/configure-policy.md)|
|보호를 위한 레이블 구성에 대한 자세한 지침|[Rights Management 보호에 대해 레이블을 구성하는 방법](../deploy-use/configure-policy-protection.md)|
|권한에 대한 자세한 정보|[Azure Rights Management에 대한 사용 권한 구성](../deploy-use/configure-usage-rights.md)|



>[!div class="step-by-step"]
[&#171; 1단계](infoprotect-tutorial-step1.md)
[3단계 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]