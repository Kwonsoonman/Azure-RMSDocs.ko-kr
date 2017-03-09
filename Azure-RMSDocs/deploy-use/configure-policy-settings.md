---
title: "Azure Information Protection 정책 설정 구성"
description: "모든 사용자와 모든 장치에 적용되는 Azure Information Protection 정책의 설정을 구성하는 방법을 설명합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: f91e7c322688a562a0060031896bce0827b328a0
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Azure Information Protection에 대한 정책 설정을 구성하는 방법

>*적용 대상: Azure Information Protection*

Azure Information Protection 정책에는 Information Protection 표시줄 제목과 도구 설명 외에 모든 사용자 및 모든 장치에 적용되는 다음의 네 가지 설정이 있습니다.

![Azure Information Protection 정책 전역 설정](../media/info-protect-policy-settings.png)


이러한 설정을 구성하려면

1. 아직 그렇게 하지 않은 경우에는, 새 브라우저 창에서 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 이와 같은 설정이 모든 사용자에게 적용되는 경우 **정책:글로벌** 블레이드에서 다음의 전역 설정을 구성합니다.

    - **All documents and emails must have a label**(모든 문서와 메일에 레이블이 있어야 함):이 옵션을 **On**(켜기)으로 설정하면 저장되는 모든 문서 및 전송되는 모든 메일에 레이블이 적용되어야 합니다. 레이블 지정은 사용자에 의해 수동으로 할당되거나, [조건](configure-policy-classification.md)의 결과로 자동으로 할당되거나, 기본적으로 할당(**Select the default label**(기본 레이블 선택) 옵션을 설정하여)될 수 있습니다. 

    사용자가 문서를 저장하거나 메일을 보낼 때 레이블이 할당되지 않은 경우에는 레이블을 선택하라는 메시지가 표시됩니다.

    ![새 분류가 하위 수준인 경우의 Azure Information Protection 프롬프트](../media/info-protect-enforce-label.png)

    - **Select the default label**(기본 레이블 선택): 이 옵션을 설정한 경우 레이블이 없는 문서와 메일에 할당할 레이블을 선택합니다. 하위 레이블이 있는 경우에는 레이블을 기본값으로 설정할 수 없습니다. 

    - **Users must provide justification to set a lower classification label, remove a label, or remove protection**(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함): 이 옵션을 **On**(켜기)으로 설정하고 이러한 작업 중 하나를 수행하면(예: **Secret**(비밀) 레이블을 **Personal**(개인)로 변경) 해당 작업에 대한 설명을 제공하라는 메시지가 표시됩니다. 예를 들어 사용자는 문서에 더 이상 민감한 정보가 포함되어 있지 않다고 설명할 수 있습니다. 작업 및 해당 근거는 사용자의 로컬 Windows 이벤트 로그 **응용 프로그램** > **Microsoft Azure Information Protection**에 기록됩니다.  

    ![새 분류가 하위 수준인 경우의 Azure Information Protection 프롬프트](../media/info-protect-lower-justification.png)

    이 옵션은 하위 레이블에 적용되지 않습니다.

    - **Azure Information Protection 클라이언트 "추가 정보" 웹 페이지에 대한 사용자 지정 URL 제공**: 사용자가 Office 응용 프로그램의 **홈** 탭에서 **보호** > **도움말 및 피드백**을 선택할 때 **Microsoft Azure Information Protection** 대화 상자의 **도움말 및 피드백** 섹션에 이 링크가 표시됩니다. 기본적으로 이 링크를 누르면 [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection) 웹 사이트로 이동됩니다. 이 링크로 다른 웹 페이지로 이동하려면 HTTP 또는 HTTPS(권장) URL을 입력할 수 있습니다. 입력한 사용자 URL이 액세스 가능하거나 모든 장치에 올바로 표시되는지 확인하는 작업은 수행되지 않습니다.
        
        예를 들어 지원 센터의 경우 클라이언트 설치 및 사용 방법에 대한 정보(**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) 또는 릴리스 버전 정보(**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**)를 포함하는 Microsoft 설명서 페이지를 입력할 수 있습니다. 또는 사용자가 지원 센터에 문의할 때 필요한 정보를 포함하는 자체 웹 페이지나 구성한 레이블을 사용하는 방법을 단계별로 안내하는 비디오를 게시할 수 있습니다.
        
     [범위 지정 정책](configure-policy-scope.md)을 만든 경우에는 지정한 사용자에 대해 이러한 설정을 덮어쓸 수 있습니다. 범위 지정 정책에서 이러한 설정을 구성하려면 초기 **Azure Information Protection** 블레이드에서 해당 범위 지정 정책을 먼저 선택합니다.

3. 변경 내용을 저장하려면 **Save**(저장)를 클릭합니다.

4. 변경 내용을 사용자에게 제공하려면 초기 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

