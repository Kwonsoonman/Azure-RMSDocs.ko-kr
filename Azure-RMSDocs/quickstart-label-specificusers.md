---
title: 빠른 시작 - 특정 사용자를 위해 새 Azure Information Protection 레이블 만들기
description: 범위가 지정된 정책을 사용하여 특정 사용자의 문서 및 이메일을 분류하는 새 레이블을 만들고 구성합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 921b1343e533b4643d97098350c34f5a69bfcf3e
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51027058"
---
# <a name="quickstart-create-a-new-azure-information-protection-label-for-specific-users"></a>빠른 시작: 특정 사용자를 위해 새 Azure Information Protection 레이블 만들기

이 빠른 시작에서는 특정 사용자만 볼 수 있고 해당 문서 및 이메일을 분류하고 보호하기 위해 적용하는 새 레이블을 만듭니다.

이 구성은 범위가 지정된 정책을 사용합니다.

이 구성은 10분 이내에 완료할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

이 빠른 시작을 완료하려면 다음이 필요합니다.

1. Azure Information Protection 플랜 1 또는 플랜 2를 포함하는 구독.
    
    이러한 구독 중 하나라도 없으면 조직을 위해 [무료](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) 계정을 만들 수 있습니다.

2. Azure Portal에 Azure Information Protection 블레이드를 추가하고 보호 서비스가 활성화되었는지 확인했습니다.

    이러한 작업에 대해 도움이 필요한 경우 [빠른 시작: Azure Portal에서 시작](quickstart-viewpolicy.md)을 참조하세요.

3. 새 레이블을 보고 적용하는 사용자가 포함된 Azure AD의 이메일 지원 그룹입니다.
    
    적절한 그룹이 없으면 이름이 **Sales Team**인 그룹을 만들고 한 명 이상의 사용자를 추가합니다.

4. 새 레이블을 테스트하려면 사용자의 컴퓨터에 Azure Information Protection 클라이언트가 설치되어 있어야 합니다. 
    
    레이블을 직접 지정하려면 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)로 이동한 후 Azure Information Protection 페이지에서 **AzInfoProtection.exe**를 다운로드하여 클라이언트를 설치할 수 있습니다.

Azure Information Protection을 사용하기 위한 필수 구성 요소의 전체 목록을 보려면 [Azure Information Protection에 대한 요구 사항](requirements.md)을 참조하세요.
    
## <a name="create-a-new-label"></a>새 레이블 만들기

먼저 새 레이블을 만듭니다.

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 **새 블레이드 추가**를 클릭합니다.

3. **레이블** 블레이드에서 적어도 다음을 지정합니다.
    
    - **레이블 표시 이름**: 사용자에게 표시되며 콘텐츠의 분류를 식별하는 새 레이블의 이름입니다. 예: `Sales - Restricted`.
    
    - **설명**: 이 새 레이블을 선택해야 하는 경우를 식별하는 데 도움이 되는 도구 설명입니다. 예를 들어 `Business data that is restricted to the Sales Team.`를 구성할 수 있습니다.

4. **사용**이 **켜짐**(기본값)으로 설정되어 있는지 확인한 후 **저장**을 선택합니다.

## <a name="add-the-label-to-a-new-scoped-policy"></a>범위가 지정된 새 정책에 레이블 추가

이제 범위가 지정된 새 정책에 새로 만든 레이블을 추가합니다.

1. **분류** > **정책** 메뉴 옵션에서: **Azure Information Protection - 정책** 블레이드에서 **새 정책 추가**를 선택합니다. 

2. **정책** 블레이드에서 **정책 이름** 상자에 새로 만든 레이블을 공개할 사용자 그룹을 식별하는 이름을 입력합니다. 정의합니다(예: `Sales`).

3. **이 정책을 가져올 사용자 또는 그룹을 선택합니다.** 옵션을 선택합니다.

4. **AAD 사용자 및 그룹** 블레이드에서 **사용자/그룹**을 선택합니다. 그런 후 새 **사용자/그룹** 블레이드에서 필수 구성 요소에서 식별한 그룹을 찾아 선택합니다. **Sales Team**을 예로 들 수 있습니다. 해당 블레이드에서 **선택**을 클릭하고 **확인**을 클릭합니다.

5. **정책** 블레이드로 돌아가 **레이블 추가 또는 제거**를 선택합니다.

6. **정책: 레이블 추가 또는 제거** 블레이드에서 만든 레이블(예: **Sales - Restricted**)를 선택한 후 **확인**을 선택합니다.

7. **정책** 블레이드로 돌아가서 **저장**을 선택합니다. 

이제 새 레이블이 사용자가 지정한 그룹의 구성원에게만 게시됩니다. 

## <a name="test-your-new-label"></a>새 레이블 테스트

Azure Information Protection 클라이언트는 동일한 컴퓨터에서 여러 사용자를 지원하지 않으므로 이 레이블을 테스트하려면 최소 두 대의 컴퓨터가 필요합니다.

 - 첫 번째 컴퓨터에서 Sales Team 그룹의 구성원으로 로그인합니다. Word를 열고 새 레이블을 볼 수 있는지 확인합니다. Word가 이미 열려 있으면 다시 시작하여 정책을 새로 고칩니다.

- 두 번째 컴퓨터에서 Sales Team 그룹의 멤버가 아닌 사용자로 로그인합니다. Word를 열고 새 레이블을 볼 수 없는지 확인합니다. 이전과 마찬가지로, Word가 이미 열려 있으면 다시 시작합니다.

## <a name="clean-up-resources"></a>리소스 정리

이 레이블 및 범위가 지정된 정책을 유지하지 않으려는 경우 다음을 수행합니다.

1. **분류** > **정책** 메뉴 옵션의 **Azure Information Protection - 정책** 블레이드에서 방금 만든 범위가 지정된 정책에 대한 상황에 맞는 메뉴(**...**)를 선택합니다. **Sales**를 예로 들 수 있습니다.

2. **정책 삭제**를 선택하고 확인하라는 메시지가 표시되면 **확인**을 선택합니다.

3. **분류** > **레이블** 메뉴 옵션의 **Azure Information Protection - 레이블** 블레이드에서 방금 만든 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택합니다.  **Sales - Restricted**를 예로 들 수 있습니다.

4.  **이 레이블 삭제**를 선택하고 확인하라는 메시지가 표시되면 **확인**을 선택합니다.


## <a name="next-steps"></a>다음 단계

이 빠른 시작에는 특정 사용자에 대한 새 레이블을 신속하게 만들 수 있도록 최소 옵션을 포함합니다. 전체 지침을 보려면 다음 문서를 참조하세요.

- [새 레이블을 만드는 방법](configure-policy-new-label.md)

- [범위 지정 정책을 사용하여 특정 사용자에 대한 정책을 구성하는 방법](configure-policy-scope.md)

또한 Sales Team 구성원만 열 수 있도록 콘텐츠에 레이블을 지정하여 보호하려면 보호를 적용하도록 레이블을 구성해야 합니다. 지침을 보려면 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.

