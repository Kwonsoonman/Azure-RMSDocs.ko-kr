---
title: 빠른 시작 - Azure Portal에서 시작
description: 조직이 Azure Information Protection을 처음 사용하는 경우 여기에서 시작하여 Azure Portal에 서비스를 추가하고, 보호 서비스가 활성화되었는지 확인하고, 정책을 봅니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 351b026429a803bf1ac74cdddd547c73a29dfa18
ms.sourcegitcommit: b4118cd75db6478f86b9994e8d84d0ada15c7f95
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52953349"
---
# <a name="quickstart-get-started-in-the-azure-portal"></a>빠른 시작: Azure Portal에서 시작

이 빠른 시작에서는 Azure Portal에 Azure Information Protection을 추가하고, 보호 서비스가 활성화되었는지 확인하고, 조직의 기본 정책을 봅니다. 

이 빠른 시작은 5분 이내에 완료할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

이 빠른 시작을 완료하려면 다음이 필요합니다.

- Azure Information Protection 플랜 1 또는 플랜 2를 포함하는 구독.
    
    이러한 구독 중 하나라도 없으면 조직을 위해 [무료](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) 계정을 만들 수 있습니다.

Azure Information Protection을 사용하기 위한 필수 구성 요소의 전체 목록을 보려면 [Azure Information Protection에 대한 요구 사항](requirements.md)을 참조하세요.

## <a name="add-azure-information-protection-to-the-azure-portal"></a>Azure Portal에 Azure Information Protection 추가

Azure Information Protection은 Azure Portal에서 자동으로 사용할 수 없습니다. 사용자가 직접 추가해야 합니다.

1. 테넌트에 대한 전역 관리자 계정을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다. 
    
    전역 관리자가 아니면 대체 역할: [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal) 링크를 사용합니다.

2. 허브 메뉴에서 **리소스 만들기**를 선택한 다음, Marketplace 검색 상자에 **Azure Information Protection**을 입력합니다. 
    
3. 결과 목록에서 **Azure Information Protection**을 선택합니다. 그런 다음, **Azure Information Protection** 블레이드에서 **만들기**를 클릭합니다.
    
    > [!TIP] 
    > 또는 다음에 포털에 로그인할 때 서비스 찾아보기 단계를 건너뛸 수 있도록 **대시보드에 고정**을 선택하여 대시보드에 **Azure Information Protection** 타일을 만듭니다.
    
    다시 **만들기**를 클릭합니다.

## <a name="confirm-the-protection-service-is-activated"></a>보호 서비스가 활성화되었는지 확인

현재, 보호 서비스는 새 테넌트에 대해 자동으로 활성화되지만 수동으로 활성화할 필요가 없는지 확인하는 것이 좋습니다. 

1. **Azure Information Protection** 블레이드에서 **관리** > **보호 활성화**를 선택합니다.

2. 테넌트에 대해 보호가 활성화되었는지가 확인합니다. 
    
    - 보호가 활성화된 경우 다음 확인이 표시됩니다.
        
        ![Azure RMS의 Azure Information Protection 상태](./media/info-protect-azurerms-activated.png)
        
    - 보호가 활성화되지 않은 경우 이 내용이 상태 정보에 반영된 것을 확인할 수 있으며 활성화할 옵션이 표시됩니다.
        
        ![Azure RMS의 Azure Information Protection 상태](./media/info-protect-azurerms-deactivated.png)

3. 보호가 활성화되지 않은 경우 **활성화**를 선택합니다. 

    활성화가 완료되면 정보 표시줄에 **활성화가 성공적으로 완료됨**이 표시됩니다.

## <a name="view-your-organizations-default-policy---labels-and-policy-settings"></a>조직의 기본 정책 보기 - 레이블 및 정책 설정

Azure Portal을 사용하여 Azure Information Protection 서비스에 처음 연결하면 테넌트에 대한 기본 정책이 만들어집니다. 기본 정책에는 있는 그대로 사용하거나 사용자 지정할 수 있는 레이블 및 설정이 포함되어 있습니다.

1. **분류** > **정책** > **전역**을 선택하여 테넌트에 대해 생성되는 기본 Azure Information Protection 정책을 표시합니다.
    
2. 몇 분간 표시되는 레이블에 친숙해지는 시간을 가집니다.
    
    - 분류 레이블: **개인**, **공개**, **일반**, **기밀** 및 **극비**. 마지막 두 개의 레이블은 확장되어 하위 레이블을 표시함으로써 분류가 하위 범주를 포함할 수 있는 방식의 예를 제공합니다.
    
    - 기본 구성을 사용하는 경우 일부 레이블에 구성된 시각적 표시가 없습니다. 시각적 표식은 바닥글, 머리글 및 워터마크입니다. 기본 정책에 따라 일부 레이블에 보호가 설정될 수도 있습니다. 예를 들면 다음과 같습니다. 
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](./media/info-protect-policy-default-labelsv2.png)
    
3. 레이블 뒤의 **Information Protection 최종 사용자에게 표시하고 적용할 설정 구성** 섹션에서 몇 가지 정책 설정을 확인할 수도 있습니다. 예를 들어 기본 레이블 집합이 없으며, 문서와 전자 메일에 레이블이 필요하지 않으며, 레이블을 변경할 때 사용자가 근거를 제공하지 않아도 됩니다.
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 기본 정책](./media/info-protect-policy-default-settings.png) 

4. 레이블 및 설정만 확인하면 되므로 열어 놓은 다른 블레이드는 닫아도 됩니다.

## <a name="next-steps"></a>다음 단계

지금까지 Azure Portal에서 레이블 및 정책 설정을 확인했으므로 다음 단계로 [정책 편집 및 Azure Information Protection에 대한 새 레이블 만들기](infoprotect-quick-start-tutorial.md) 자습서를 진행하면 유용할 것입니다.

또는 Azure Information Protection 정책의 모든 측면을 구성하기 위한 자세한 지침을 보려면 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.
