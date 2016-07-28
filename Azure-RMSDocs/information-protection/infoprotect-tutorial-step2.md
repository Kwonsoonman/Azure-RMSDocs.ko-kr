---
title: "Azure Information Protection 빠른 시작 자습서 2단계 | Azure 권한 관리"
description: "15분 이내에 완료할 수 있는 4단계를 통해 조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 2단계입니다."
author: cabailey
manager: mbaldwin
ms.date: 07/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: 463c0bc1fa86f73e2623faf5a624afeabcadeedb
ms.openlocfilehash: c6ecf22b72d862c605f8be2ab1f75fd2126f8575


---

# 2단계: Azure Information Protection 정책 구성 및 게시

*적용 대상: Azure Information Protection 미리 보기*

Azure Information Protection은 구성 없이 사용할 수 있는 기본 정책과 함께 제공되지만, 해당 정책을 살펴보고 몇 가지를 변경합니다.

1. Azure Information Protection의 이 특별 링크(https://portal.azure.com/?microsoft_azure_informationprotection=true)를 사용하여 Azure 포털에 로그인합니다.
 
2. 허브 메뉴에서 **찾아보기**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

- 이제 기본 **Azure Information Protection** 블레이드가 표시되며, 이 블레이드에는 자동으로 만들어진 기본 Information Protection 정책이 표시됩니다. 이 기본 정책은 분류를 위한 **Personal**(비공개), **Public**(공개), **Internal**(내부), **Confidential**(기밀) 및 **Secret**(비밀) 레이블을 포함합니다. 각 레이블의 용도를 이해하려면 각 레이블의 도구 설명을 읽어 보세요. **Secret**(비밀)에는 두 개의 하위 레이블 **All-Employees**(모든 직원)와 **My-Group**(내 그룹)이 있습니다. 이러한 하위 레이블은 분류가 하위 범주를 포함하는 방법의 예를 제공합니다.

- 해당 기본 설정을 통해 **Internal**(내부), **Confidential**(기밀) 및 **Secret**(비밀)에는 구성된 시각적 표시(예: 바닥글, 머리글, 워터마크)가 있으며 보호가 설정된 레이블은 없습니다. 또한 모든 문서와 메일에 레이블이 필요하지 않고, 기본 레이블이 없으며, 민감도를 낮출 때 사용자가 근거를 제공하지 않아도 되도록 세 가지 전역 설정은 설정되지 않습니다.

    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](../media/info-protect-policy.png)

이 자습서에서는 몇 가지 전역 설정의 작동 방식을 확인할 수 있도록 이러한 몇 가지 전역 설정을 변경합니다.

-  **Select the default label**(기본 레이블 선택): **Internal**(내부)로 설정합니다.

- **Users must provide justification when lowering the sensitivity level**(민감도를 낮출 때 사용자가 근거를 제공해야 함): **On**(켜기)으로 설정합니다.

이제 레이블 중 하나인 **Confidential**(기밀)의 설정을 변경합니다.

1. **Confidential**(기밀) 레이블 항목을 클릭합니다.

2. **Label: Confidential**(레이블: 기밀) 블레이드에 이제 각 레이블에 사용할 수 있는 설정이 표시됩니다. 다음과 같이 변경합니다.

    a. Azure 권한 관리를 활성화한 경우 **Select RMS template**(RMS 템플릿 선택)에 대해: 드롭다운 상자를 클릭하고 기본 템플릿 **\<조직 이름> - Confidential**(기밀)을 선택합니다. 예를 들어 경우 조직 이름이 VanArsdel, Ltd인 경우 **VanArsdel, Ltd - Confidential**(기밀)이 표시되고 이를 선택합니다. 이 기본 Azure 권한 관리 템플릿을 사용하지 않도록 설정한 경우 대체 템플릿을 선택합니다. 그러나 부서별 템플릿을 선택하는 경우 계정이 범위에 포함되는지 확인합니다.

    Azure 권한 관리를 활성화하지 않은 경우 이 옵션을 사용할 수 없습니다.

    b. **Documents with this label have a watermark**(이 레이블이 있는 문서는 워터마크를 포함함): **On**(켜기)을 클릭하고 **Text**(텍스트) 상자에 조직 이름을 입력합니다. 예를 들어 **VanArsdel, Ltd**를 입력합니다. 

    c. **Add a new condition**(새 조건 추가)을 클릭하고 **Condition**(조건) 블레이드에서 다음을 선택합니다.

    - **Choose the type of condition**(조건 유형 선택): **Built-in**(기본 제공)

    - **Select built-in**(기본 제공 선택): **Credit Card Number**(신용 카드 번호)

    - **Minimum number of occurrences**(최소 발생 횟수): **1**

    - **Save**(저장)를 클릭하여 **Label: Confidential**(레이블: 기밀) 블레이드로 돌아갑니다.

3. **Label: Confidential**(레이블: 기밀) 블레이드에 **Credit Card Number**(신용 카드 번호)가 **CONDITION NAME**(조건 이름)으로 표시되고 **OCCURRENCES**(발생 횟수)는 **1**로 표시됩니다.

4. **Select how this label is applied**(이 레이블 적용 방법 선택): **Recommended**(권장)를 그대로 둡니다.

5. **Enter notes for internal housekeeping**(내부 하우스키핑을 위한 메모 입력) 상자에 **For testing purposes only**(테스트 전용)를 입력합니다.

6. 이 **Label: Confidential**(레이블: 기밀) 블레이드에서 **Save**(저장)를 클릭하고 기본 **Azure Information Protection** 블레이드에서 다시 **Save**(저장)를 클릭합니다.

7. 이제 변경을 수행하고 저장했으므로 이러한 내용을 사용자에게 제공하기 위해 **Publish**(게시)를 클릭하고 **Yes**(예)를 클릭하여 확인합니다.

![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책 구성됨](../media/info-protect-policy-configured.png)

이 자습서를 완료한 후 Azure 포털을 닫거나, 열어 둔 채로 추가 구성 옵션을 사용해 볼 수 있습니다.

기본 정책을 살펴보고 몇 가지를 변경했으므로 다음 단계는 Azure Information Protection 클라이언트를 설치하는 것입니다.


>[!div class="step-by-step"]
[&#171; 1단계](infoprotect-tutorial-step1.md)
[3단계 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Jul16_HO3-->


