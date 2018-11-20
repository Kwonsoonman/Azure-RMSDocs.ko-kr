---
title: 빠른 시작 - 사용자가 중요한 정보가 포함된 이메일을 쉽게 보호하도록 레이블 구성
description: 전달 금지 보호를 자동으로 적용하여 사용자를 위해 이메일을 보호하는 레이블을 구성합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 793c3ff3b68de66dce5876c25cb4ba5455d19c33
ms.sourcegitcommit: ad37950f6a747c86f6496c6de859e18446f9b03f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51644695"
---
# <a name="quickstart-configure-a-label-for-users-to-easily-protect-emails-that-contain-sensitive-information"></a>빠른 시작: 사용자가 중요한 정보가 포함된 이메일을 쉽게 보호하도록 레이블 구성

이 빠른 시작에서는 전달 금지 보호 설정을 자동으로 적용하도록 기존 레이블을 구성합니다.

현재 Azure Information Protection 정책에는 이 구성은 갖는 다음과 같은 두 가지 레이블이 이미 포함되어 있습니다.

- **Confidential \ Recipients Only**

- **Highly Confidential \ Recipients Only**

그러나 정책이 오래되었거나 조직의 정책이 만들어졌을 때 보호가 활성화되지 않은 경우 이러한 레이블이 없습니다. 

이 구성은 5분 이내에 완료할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

이 빠른 시작을 완료하려면 다음이 필요합니다.

1. Azure Information Protection 플랜 1 또는 플랜 2를 포함하는 구독.
    
    이러한 구독 중 하나라도 없으면 조직을 위해 [무료](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) 계정을 만들 수 있습니다.

2. Azure Portal에 Azure Information Protection 블레이드를 추가하고 보호 서비스가 활성화되었는지 확인했습니다.

    이러한 작업에 대해 도움이 필요한 경우 [빠른 시작: Azure Portal에서 시작](quickstart-viewpolicy.md)을 참조하세요.

3. 구성할 기존 Azure Information Protection 레이블. 
    
    기본 레이블 또는 사용자가 만든 레이블 중 하나를 사용할 수 있습니다. 새 레이블을 만드는 데 도움이 필요한 경우 [빠른 시작: 특정 사용자를 위해 새 Azure Information Protection 레이블 만들기](quickstart-label-specificusers.md)를 참조하세요.

4. 새 레이블을 테스트하려면 사용자의 컴퓨터에 Azure Information Protection 클라이언트가 설치되어 있어야 합니다. 
    
    레이블을 직접 지정하려면 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)로 이동한 후 Azure Information Protection 페이지에서 **AzInfoProtection.exe**를 다운로드하여 클라이언트를 설치할 수 있습니다.

5. 새 레이블을 테스트하려면 Windows(Windows 7 서비스 팩 1 이상)를 실행하는 컴퓨터가 필요합니다. 이 컴퓨터에서는 다음 범주 중 하나에서 Office 앱에 로그인합니다.
    
    - Office 365(Office 2016 앱 포함)(최소 버전 1805, 빌드 9330.2078) 이 옵션을 사용하려면 계정에 Azure Rights Management용 라이선스를 할당해야 합니다. 이 라이선스는 Azure Information Protection 구독에 포함되어 있습니다.
    
    - Office 365 ProPlus(2016 앱 또는 2013 앱 포함)(간편 실행 또는 Windows Installer 기반 설치)
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 서비스 팩 1
    
    - Office Professional Plus 2010 서비스 팩 2

Azure Information Protection을 사용하기 위한 필수 구성 요소의 전체 목록을 보려면 [Azure Information Protection에 대한 요구 사항](requirements.md)을 참조하세요.

## <a name="configure-an-existing-label-to-apply-the-do-not-forward-protection"></a>전달 금지 보호를 적용하도록 기존 레이블 구성

1. 새 브라우저 창을 열고 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. 그런 후 **Azure Information Protection**로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.
    
    전역 관리자가 아니면 대체 역할: [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal) 링크를 사용합니다.

2. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 보호를 적용하도록 구성하려는 레이블을 선택합니다. 

3. **레이블** 블레이드에서 **Set permissions for documents and emails containing this label**(이 레이블을 포함하는 문서 및 메일에 대한 사용 권한 설정)을 찾습니다. **보호**를 선택한 후 **보호**를 선택합니다.
    
    ![Azure Information Protection 레이블에 대한 보호 구성](./media/info-protect-protection-bar-configured.png).

4. **보호** 블레이드에서 **Azure(클라우드 키)** 가 선택되었는지 확인합니다.
    
5. **사용자 정의 권한 설정(미리 보기)** 을 선택합니다.

6. **Outlook에서 전달 금지 적용** 옵션이 선택되어 있는지 확인합니다.

7. 선택하면 다음 옵션의 선택을 취소합니다. **Word, Excel, PowerPoint 및 파일 탐색기에서 사용자에게 사용자 지정 권한을 확인하는 메시지 표시**

8. **보호** 블레이드에서 **확인**을 클릭한 후 **레이블** 블레이드에서 **저장**을 클릭합니다.

레이블은 이제 Outlook에만 표시되고 이메일에 전달 금지 보호를 적용하도록 구성됩니다.

## <a name="test-your-new-label"></a>새 레이블 테스트

구성된 레이블은 Outlook에만 표시되며, Exchange Online이 [Office 365 메시지 암호화의 새 기능](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)에 맞게 구성될 경우 조직 외부의 모든 받는 사람에게 전송되는 이메일에 적합합니다.

1. 컴퓨터에서 Outlook을 열고 새 이메일 메시지를 만듭니다. Outlook이 이미 열려 있으면 다시 시작하여 정책을 새로 고칩니다.

2. 받는 사람, 이메일 메시지에 대한 일부 텍스트를 지정한 후 방금 만든 레이블을 적용합니다. 
    
    이메일 메시지는 레이블 이름에 따라 분류되며 전달 금지 제한으로 보호됩니다.

3. 이메일을 보냅니다. 

이에 따라 받는 사람은 이메일을 전달하거나, 인쇄하거나, 복사하거나, 첨부 파일을 저장하거나, 다른 이름으로 저장할 수 없습니다. 보호된 이메일 메시지를 모든 장치의 모든 사용자가 읽을 수 있습니다.

## <a name="clean-up-resources"></a>리소스 정리

이 구성을 유지하지 않고 보호를 적용하지 않은 상태로 레이블을 되돌리려면 다음을 수행합니다.

1. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 구성한 레이블을 선택합니다. 

3. **레이블** 블레이드에서 **이 레이블을 포함하는 문서 및 메일에 대한 사용 권한 설정**을 찾은 후 **구성 안 함** 및 **저장**을 차례로 선택합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에는 레이블을 빠르게 구성하여 사용자가 이메일을 쉽게 구성할 수 있도록 하는 최소 옵션이 포함되어 있습니다. 그러나 구성이 너무 제한적이거나 충분히 제한적이지 않으면 다른 예제 구성을 참조하세요.

- [전달 금지보다 적은 권한 제한을 지원하는 보호된 메일의 레이블](configure-policy-protection.md#example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward)

- [콘텐츠를 암호화하지만, 콘텐츠에 액세스할 수 있는 사용자를 제한하지 않는 레이블](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)

보호를 적용하는 레이블을 구성하는 방법에 대한 전체 지침을 보려면 [Rights Management 보호에 대해 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요. 
