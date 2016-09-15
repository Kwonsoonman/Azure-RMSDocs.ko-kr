---
title: "Azure Information Protection에 대한 전역 정책 설정을 구성하는 방법 | Azure Information Protection"
description: "Azure Information Protection 정책에는 모든 사용자 및 모든 장치에 적용되는 세 가지 설정이 있습니다."
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: 6bbac611f9c8bba96fbbba69e8044e494134d792
ms.openlocfilehash: 872ea7da6f3b72a355a73c8b0589beda86ded20d


---

# Azure Information Protection에 대한 전역 정책 설정을 구성하는 방법

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

Azure Information Protection 정책에는 모든 사용자 및 모든 장치에 적용되는 세 가지 설정이 있습니다.

![Azure Information Protection 정책 전역 설정](../media/info-protect-policy-settings.png)


이러한 설정을 구성하려면

1. 아직 로그인하지 않은 경우 [Azure 포털](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **찾아보기**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **Azure Information Protection** 블레이드에서 다음 전역 설정을 구성합니다.

    - **All documents and emails must have a label**(모든 문서와 메일에 레이블이 있어야 함):이 옵션을 **On**(켜기)으로 설정하면 저장되는 모든 문서 및 전송되는 모든 전자 메일에 레이블이 적용되어야 합니다. 레이블 지정은 사용자에 의해 수동으로 할당되거나, [조건](configure-policy-classification.md)의 결과로 자동으로 할당되거나, 기본적으로 할당(**Select the default label**(기본 레이블 선택) 옵션을 설정하여)될 수 있습니다. 

    사용자가 문서를 저장하거나 전자 메일을 보낼 때 레이블이 할당되지 않은 경우에는 레이블을 선택하라는 메시지가 표시됩니다.

    ![새 분류가 하위 수준인 경우의 Azure Information Protection 프롬프트](../media/info-protect-enforce-label.png)

    - **Select the default label**(기본 레이블 선택): 이 옵션을 설정한 경우 레이블이 없는 문서와 전자 메일에 할당할 레이블을 선택합니다. 하위 레이블이 있는 경우에는 레이블을 기본값으로 설정할 수 없습니다. 

    - **Users must provide justification to set a lower classification label, remove a label, or remove protection**(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함): 이 옵션을 **On**(켜기)으로 설정하고 이러한 작업 중 하나를 수행하면(예: **Secret**(비밀) 레이블을 **Personal**(개인)로 변경) 해당 작업에 대한 설명을 제공하라는 메시지가 표시됩니다. 예를 들어 사용자는 문서에 더 이상 민감한 정보가 포함되어 있지 않다고 설명할 수 있습니다. 작업 및 해당 근거는 사용자의 로컬 Windows 이벤트 로그 **응용 프로그램** > **Microsoft Azure Information Protection**에 기록됩니다.  

    ![새 분류가 하위 수준인 경우의 Azure Information Protection 프롬프트](../media/info-protect-lower-justification.png)

    이 옵션은 하위 레이블에 적용되지 않습니다.

3. 변경 내용을 저장하려면 **Save**(저장)를 클릭합니다.

4. 변경 내용을 사용자에게 제공하려면 **Publish**(게시)를 클릭합니다.

## 다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organization-s-policy) 섹션의 링크를 사용하세요.  












<!--HONumber=Sep16_HO1-->


