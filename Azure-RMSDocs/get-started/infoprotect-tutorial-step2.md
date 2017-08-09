---
title: "빠른 시작 자습서 2단계 - AIP"
description: "Azure Information Protection를 빠르게 사용해 보기 위한 소개 자습서 2단계 - 정책 구성"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: 86857d9fe744ee8b8949bdf247a360492ceb8165
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2017
---
# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>2단계: Azure Information Protection 정책 구성 및 게시

>*적용 대상: Azure Information Protection*

Azure Information Protection은 구성 없이 사용할 수 있는 기본 정책과 함께 제공되지만, 해당 정책을 살펴보고 몇 가지를 변경합니다.

1. 새 브라우저 창에서 사용 중인 테넌트에 대한 전역 관리자나 보안 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 허브 메뉴에서 **새로 만들기**를 클릭한 다음 **MARKETPLACE** 목록에서 **보안 + ID**를 클릭합니다. **보안 + ID** 블레이드의 **추천 앱** 목록에서 **Azure Information Protection**을 선택합니다. **Azure Information Protection** 블레이드에서 **만들기**를 클릭합니다.

    그러면 테넌트에 대한 서비스가 활성화되고, **Azure Information Protection** 블레이드가 생성되며, 다음에 포털에 로그인할 때 허브 **추가 서비스** 목록에서 서비스를 선택할 수 있습니다. 

    > [!TIP] 
    > 다음에 포털에 로그인할 때 서비스 찾아보기 단계를 건너뛸 수 있도록 **대시보드에 고정**을 선택하여 대시보드에 **Azure Information Protection** 타일을 만듭니다.

3. 서비스에 처음으로 연결할 때 자동으로 열리는 **빠른 시작** 페이지의 정보를 확인하세요. 나중에 이 페이지로 돌아올 수 있습니다. 이 자습서에서는 **전역 정책**을 클릭하여 **정책: 전역** 블레이드를 엽니다. 이 블레이드는 나중에 서비스에 다시 연결되면 자동으로 열리며 테넌트에 대해 자동으로 생성되는 기본 Information Protection 정책을 표시합니다.
    
    - 분류 레이블: **개인**, **공개**, **일반**, **기밀** 및 **극비**. 마지막 두 개의 레이블이 확장되고 **모든 직원** 및 **모든 사람(보호되지 않음)**을 포함하는 하위 레이블을 표시하여, 분류가 하위 범주를 포함할 수 있는 방식의 예를 제공합니다.
    
       > [!NOTE]
       > 기본 정책은 이 자습서의 기본 정책과 약간 다르게 보일 수 있습니다. 예를 들어 **일반** 대신 **내부** 레이블이, **극비** 대신 **비밀**이 있을 수 있습니다. 또는 **받는 사람만**이라는 추가 하위 레이블이 있습니다. 테넌트용으로 작성된 시기에 따라 기본 정책의 버전이 달라지기 때문입니다. 또는 자습서를 시작하기 전에 직접 레이블을 편집했을 수 있습니다.
       > 
       > 기본 정책이 다르게 보이는 경우에도 여전히 이 자습서를 사용할 수 있지만, 뒤에 나오는 지침과 그림을 사용할 때 이러한 변경 내용을 인식해야 합니다. 현재 기본 정책과 일치하도록 기본 정책을 수정하려면 [기본 Azure Information Protection 정책](../deploy-use/configure-policy-default.md)을 참조하세요.

    - 기본 구성을 사용하는 경우 일부 레이블에 구성된 시각적 표시(예: 바닥글, 머리글, 워터마크)가 없습니다. 기본 정책에 따라 일부 레이블에 보호가 설정되거나 설정되지 않을 수 있습니다. 예를 들면 다음과 같습니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](../media/info-protect-policy-default-labelsv2.png)
    
    또한 일부 정책 설정은 설정되지 않습니다. 모든 문서 및 메일에 레이블이 필요하지 않고, 기본 레이블이 없으며, 사용자가 레이블을 변경할 때 근거를 제공하지 않아도 되는 경우입니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>기본 레이블 및 근거에 대한 프롬프트 설정 변경

이 자습서에서는 몇 가지 정책 설정의 작동 방식을 확인할 수 있도록 이러한 설정을 변경합니다.

1. **기본 레이블 선택**에서 **일반**으로 설정합니다. 

    이전 버전의 정책을 사용하고 있어 이 레이블이 없는 경우 같은 레이블로 **내부**를 선택합니다.

2. **Users must provide justification to set a lower classification label, remove a label, or remove protection**(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함)에서 **On**(켜기)으로 설정합니다.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>보호를 위한 레이블, 워터마크 및 분류를 위한 프롬프트 조건 구성

이제 **기밀** 기본 레이블에서 하위 레이블 중 하나인 **모든 직원**의 설정을 변경합니다. 

이전 버전의 정책을 사용하고 있어 **기밀** 레이블에 하위 레이블이 없는 경우 대신 **기밀** 레이블을 사용할 수 있습니다. 구성 단계는 같지만 레이블 블레이드의 이름은 **모든 직원**이 아닌 **기밀**이 됩니다.

1. **기밀** 레이블이 확장되어 하위 레이블이 표시되는지 확인한 다음 **모든 직원** 레이블에 대해 **Azure RMS**이 **보호** 열에 표시되는지 기록합니다. 표시되는 경우 최신 기본 정책이 있으며 이 레이블의 보호가 자동으로 구성됩니다. 이 열이 비어 있으면 이후 단계에서 보호를 구성해야 합니다.

    새 **레이블: 모든 직원** 블레이드에서 이 **모든 직원** 하위 레벨을 선택하면, 이제 각 레이블에 사용할 수 있는 설정이 표시됩니다. 

2. 이 레이블에 대한 **설명** 텍스트를 읽습니다. 이 텍스트는 선택한 레이블의 용도를 설명하고 사용자에게 도구 설명으로 표시되어 사용자가 선택할 레이블을 결정하는 데 도움을 줍니다.

3. 레이블에 보호가 이미 구성되어 있으면 5단계로 이동합니다.
    
    레이블에 대해 보호가 구성되어 있지 않으면 **이 레이블을 포함하는 문서와 메일의 권한 설정** 섹션을 찾습니다. **보호**를 선택한 다음 **보호** 표시줄을 선택합니다.
    
    ![Azure Information Protection 레이블에 대해 구성된 보호](../media/info-protect-protection-bar-configured.png) 
    
4. **보호** 블레이드에서 **Azure RMS**와 **미리 정의된 템플릿 선택**이 선택되어 있는지 확인합니다. 드롭다운 상자를 클릭하고 조직의 모든 사용자가 보호된 콘텐츠를 보고 편집할 수 있는 기본 템플릿을 선택합니다. 
    
    최근에 구독한 경우 이 템플릿 이름은 **Confidential \ All Employees**입니다. 
    
    한동안 구독하지 않은 경우 기본 템플릿 이름이 **\<your organization name> - Confidential**일 수 있습니다. 예를 들어 조직 이름이 VanArsdel, Ltd인 경우 **VanArsdel, Ltd - 기밀**이 표시되고 이를 선택합니다. 
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 | Azure RMS 보호 설정](../media/step2-select-rms-template.png)
    
    이 기본 Azure 권한 관리 템플릿을 사용하지 않도록 설정한 경우 대체 템플릿을 선택합니다. 그러나 부서별 템플릿을 선택하는 경우 계정이 범위에 포함되는지 확인합니다.
    
4. **확인**을 클릭하여 변경 내용을 저장합니다. 그러면 **보호** 블레이드가 닫힙니다. **레이블: 모든 직원** 블레이드에서 보호 표시줄이 업데이트되어 표시됩니다. 예를 들면 다음과 같습니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - Azure RMS 보호 구성됨](../media/protection-bar-configured.png)
    
5. 이제 **레이블: 모든 직원** 블레이드에서 **시각적 표시 설정** 섹션을 찾습니다.
    
    **Documents with this label have a watermark**(이 레이블이 있는 문서는 워터마크를 포함함) 설정에서 **On**(켜기)을 클릭하고 **Text**(텍스트) 상자에 조직 이름을 입력합니다. 예를 들어 **VanArsdel, Ltd**를 입력합니다. 
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 | Azure RMS 보호 설정](../media/step2-configure-watermark.png)
    
    워터마크의 크기, 색, 레이아웃을 변경할 수는 있지만 지금은 이러한 설정을 기본값 그대로 유지하겠습니다.
    
6. **Configure conditions for automatically applying this label**(이 레이블을 자동으로 적용하기 위한 조건 구성) 섹션으로 이동합니다.
    
    **Add a new condition**(새 조건 추가)을 클릭하고 **Condition**(조건) 블레이드에서 다음을 선택합니다.
    
    a. **Choose the type of condition**(조건 유형 선택): 기본값을 **Built-in**(기본 제공)으로 유지합니다.
    
    b. **기본 제공 선택**: 드롭다운에서 **신용 카드 번호**를 선택합니다.
    
    c. **Minimum number of occurrences**(최소 발생 횟수): 기본값을 **1**로 유지합니다.
    
    d. **Count occurrences with unique values only**(고유 값이 있는 발생만 계산): 기본값을 **Off**(끄기)로 유지합니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 신용 카드 조건 구성](../media/step2-configure-condition.png)
    
    **저장**을 클릭하여 **레이블: 모든 직원** 블레이드로 돌아갑니다.

7. **레이블: 모든 직원** 블레이드에서 **신용 카드 번호**가 **조건 이름**으로 표시되고 **OCCURRENCES**(발생 빈도)는 **1**로 표시됩니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 신용 카드 조건 구성](../media/step2-see-condition.png)

8. **Select how this label is applied**(이 레이블 적용 방법 선택)에서 기본값을 **Recommended**(권장)로 유지합니다. 기본 정책 팁을 변경하지 마세요.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 권장 분류](../media/step2-keep-recommendedv2.png)

9. **Enter notes for internal housekeeping**(내부 하우스키핑을 위한 메모 입력) 상자에 **For testing purposes only**(테스트 전용)를 입력합니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 형식 참고 사항](../media/step2-type-notes.png)

10. 이 **레이블: 모든 직원** 블레이드에서 **저장**을 클릭합니다. 그런 다음 **정책:글로벌** 블레이드에서 **저장**을 다시 클릭합니다.
    
    보호를 적용하도록 레이블을 구성한 경우 이제 Azure RMS 보호를 표시하도록 레이블이 업데이트됩니다.

    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책 구성됨](../media/info-protect-policy-configuredv2.png)
    
    또한 설정은 기본 레이블 및 근거에 대한 변경 내용으로 구성됩니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 설정 구성됨](../media/info-protect-settings-configuredv2.png)
    
11. 이제 변경을 수행하고 변경 내용을 저장했으므로 이러한 내용을 사용자에게 제공하기 위해 초기 **Azure Information Protection** 블레이드에서 **게시**와 **예**를 클릭하여 게시를 확인합니다.

    ![Azure Information Protection 빠른 시작 자습서 3단계 - 구성된 정책 게시](../media/info-protect-publish.png)

이 자습서를 완료한 후 Azure 포털을 닫거나, 열어 둔 채로 추가 구성 옵션을 사용해 볼 수 있습니다.

기본 정책을 살펴보고 몇 가지를 변경했으므로 다음 단계는 Azure Information Protection 클라이언트를 설치하는 것입니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|정책에 대한 구성 옵션 정보|[Azure Information Protection 정책 구성](../deploy-use/configure-policy.md)|
|기본 정책의 구성 설정|[기본 Azure Information Protection 정책](../deploy-use/configure-policy-default.md)|


>[!div class="step-by-step"]
[&#171; 1단계](infoprotect-tutorial-step1.md)
[3단계 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]