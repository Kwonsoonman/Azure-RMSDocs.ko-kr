---
title: "빠른 시작 자습서 1단계 | Azure Information Protection"
description: "조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 2단계로 약 30분 만에 완료해야 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: bce1682624b040545d30ca1cc426e4e2f8c38018
ms.openlocfilehash: 7ba1566a81ca9a3ac45f340f69d3c9e933f015ff


---

# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>2단계: Azure Information Protection 정책 구성 및 게시

>*적용 대상: Azure Information Protection*

Azure Information Protection은 구성 없이 사용할 수 있는 기본 정책과 함께 제공되지만, 해당 정책을 살펴보고 몇 가지를 변경합니다.

1. 새 브라우저 창에서 사용 중인 테넌트에 대한 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. 허브 메뉴에서 **새로 만들기**를 클릭한 다음 **MARKETPLACE** 목록에서 **보안 + ID**를 클릭합니다. **보안 + ID** 블레이드의 **추천 앱** 목록에서 **Azure Information Protection**을 선택합니다. **Azure Information Protection** 블레이드에서 **만들기**를 클릭합니다.

    **Azure Information Protection** 블레이드가 생성되며, 다음에 포털에 로그인할 때 허브 **추가 서비스** 목록에서 서비스를 선택할 수 있습니다. 

    > [!TIP] 
    > 다음에 포털에 로그인할 때 서비스 찾아보기 단계를 건너뛸 수 있도록 **대시보드에 고정**을 선택하여 대시보드에 **Azure Information Protection** 타일을 만듭니다.

3.  자동으로 만들어진 기본 Information Protection 정책이 표시되는 기본 **Azure Information Protection** 블레이드를 탐색합니다.
    
    - 분류 레이블: **Personal**(비공개), **Public**(공개), **Internal**(내부), **Confidential**(기밀) 및 **Secret**(비밀) 각 레이블의 용도를 이해하려면 각 레이블의 도구 설명을 읽어 보세요. **Secret**(비밀)에는 두 개의 하위 레이블 **All-Employees**(모든 직원)와 **My-Group**(내 그룹)이 있습니다. 이러한 하위 레이블은 분류가 하위 범주를 포함하는 방법의 예를 제공합니다.

    - 기본 설정을 통해 **Internal**(내부), **Confidential**(기밀) 및 **Secret**(비밀) 레이블에는 구성된 시각적 표시(예: 바닥글, 머리글, 워터마크)가 있으며 보호가 설정된 레이블은 없습니다. 또한 모든 문서와 메일에 레이블이 필요하지 않고, 기본 레이블이 없고, 사용자가 레이블을 변경할 때 근거를 제공하지 않아도 되며, 클라이언트에 사용자 지정 도움말 링크가 구성되지 않도록 네 가지 전역 설정은 설정되지 않습니다.

    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](../media/info-protect-policy.png)

## <a name="changing-the-global-settings-for-a-default-template-and-prompt-for-justification"></a>맞춤에 대한 기본 템플릿 및 프롬프트 전역 설정 변경

이 자습서에서는 몇 가지 전역 설정의 작동 방식을 확인할 수 있도록 이러한 몇 가지 전역 설정을 변경합니다.

1. **Select the default label**(기본 레이블 선택)에서 **Internal**(내부)로 설정합니다.

2. **Users must provide justification to set a lower classification label, remove a label, or remove protection**(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함)에서 **On**(켜기)으로 설정합니다.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>보호를 위한 레이블, 워터마크 및 분류를 위한 프롬프트 조건 구성

이제 레이블 중 하나인 **Confidential**(기밀)의 설정을 변경합니다.

1. **Confidential**(기밀) 레이블을 클릭합니다. 
    
    새 **Label: Confidential**(레이블: 기밀) 블레이드에 이제 각 레이블에 사용할 수 있는 설정이 표시됩니다. 

2. **Label: Confidential**(레이블: 기밀) 블레이드의 **Set RMS template for protecting documents and emails containing this label**(이 레이블을 포함하는 문서 및 전자 메일을 보호하도록 RMS 템플릿 설정) 섹션으로 이동합니다.
    
    **Select RMS template from**(RMS 템플릿 선택) 옵션에서 기본값 **Azure RMS**를 유지합니다. 그런 다음 **Select RMS template**(RMS 템플릿 선택)에서 드롭다운 상자를 클릭하고 기본 템플릿 **\<조직 이름> - Confidential**(기밀)을 선택합니다. 
    
    예를 들어 경우 조직 이름이 VanArsdel, Ltd인 경우 **VanArsdel, Ltd - Confidential**(기밀)이 표시되고 이를 선택합니다. 
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 | Azure RMS 보호 설정](../media/step2-select-rms-template.png)
    
    이 기본 Azure 권한 관리 템플릿을 사용하지 않도록 설정한 경우 대체 템플릿을 선택합니다. 그러나 부서별 템플릿을 선택하는 경우 계정이 범위에 포함되는지 확인합니다.
    
3. **Set visual marking**(시각적 표시 설정) 섹션으로 이동합니다.
    
    **Documents with this label have a watermark**(이 레이블이 있는 문서는 워터마크를 포함함) 설정에서 **On**(켜기)을 클릭하고 **Text**(텍스트) 상자에 조직 이름을 입력합니다. 예를 들어 **VanArsdel, Ltd**를 입력합니다. 
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 | Azure RMS 보호 설정](../media/step2-configure-watermark.png)
    
    워터마크의 크기, 색, 레이아웃을 변경할 수는 있지만 지금은 기본값 그대로 유지하겠습니다.
    
4. **Configure conditions for automatically applying this label**(이 레이블을 자동으로 적용하기 위한 조건 구성) 섹션으로 이동합니다.
    
    **Add a new condition**(새 조건 추가)을 클릭하고 **Condition**(조건) 블레이드에서 다음을 선택합니다.
    
    a. **Choose the type of condition**(조건 유형 선택): 기본값을 **Built-in**(기본 제공)으로 유지합니다.
    
    b. **Select built-in**(기본 제공 선택): 드롭다운에서 **Credit Card Number**(신용 카드 번호)를 선택합니다.
    
    c. **Minimum number of occurrences**(최소 발생 횟수): 기본값을 **1**로 유지합니다.
    
    d. **Count occurrences with unique values only**(고유 값이 있는 발생만 계산): 기본값을 **Off**(끄기)로 유지합니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 신용 카드 조건 구성](../media/step2-configure-condition.png)
    
    **Save**(저장)를 클릭하여 **Label: Confidential**(레이블: 기밀) 블레이드로 돌아갑니다.

5. **Label: Confidential**(레이블: 기밀) 블레이드에 **Credit Card Number**(신용 카드 번호)가 **CONDITION NAME**(조건 이름)으로 표시되고 **OCCURRENCES**(발생 횟수)는 **1**로 표시됩니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 신용 카드 조건 구성](../media/step2-see-condition.png)

6. **Select how this label is applied**(이 레이블 적용 방법 선택)에서 기본값을 **Recommended**(권장)로 유지합니다. 기본 정책 팁을 변경하지 마세요.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 권장 분류](../media/step2-keep-recommended.png)

7. **Enter notes for internal housekeeping**(내부 하우스키핑을 위한 메모 입력) 상자에 **For testing purposes only**(테스트 전용)를 입력합니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 형식 참고 사항](../media/step2-type-notes.png)

8. **Label: Confidential**(레이블: 기밀) 블레이드에서 **Save**(저장)를 클릭합니다. 그런 다음 **Azure Information Protection** 블레이드에서 **Save**(저장)를 다시 클릭합니다.

9. 이제 변경을 수행하고 저장했으므로 이러한 내용을 사용자에게 제공하기 위해 **Publish**(게시)를 클릭하고 **Yes**(예)를 클릭하여 확인합니다.

![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책 구성됨](../media/info-protect-policy-configured.png)

이 자습서를 완료한 후 Azure 포털을 닫거나, 열어 둔 채로 추가 구성 옵션을 사용해 볼 수 있습니다.

기본 정책을 살펴보고 몇 가지를 변경했으므로 다음 단계는 Azure Information Protection 클라이언트 및 Rights Management 공유 응용 프로그램을 설치하는 것입니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|정책에 대한 구성 옵션 정보|[Azure Information Protection 정책 구성](../deploy-use/configure-policy.md)|


>[!div class="step-by-step"]
[&#171; 1단계](infoprotect-tutorial-step1.md)
[3단계 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Nov16_HO3-->


