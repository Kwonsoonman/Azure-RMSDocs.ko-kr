---
title: 자습서 - 문서 및 메일을 분류하는 데 도움이 되도록 Azure Information Protection 정책 설정 구성 - AIP
description: 조직의 문서와 이메일을 분류하는 데 도움이 되도록 Azure Information Protection 정책 설정을 구성하는 과정을 안내하는 소개 자습서입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: tutorial
ms.service: information-protection
ms.openlocfilehash: 0341ba1b232551f89e1ee43f77a3425b8c6e8ffb
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024368"
---
# <a name="tutorial-configure-azure-information-protection-policy-settings-that-work-together"></a>자습서: 함께 작동하는 Azure Information Protection 정책 설정 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.
> [!div class="checklist"]
> * 함께 작동하는 정책 설정 구성
> * 작동 중인 설정 보기

사용자가 문서 및 이메일에 수동으로 레이블을 지정하도록 하는 대신, 정책 설정을 사용하여 다음을 수행할 수 있습니다.

- 새 콘텐츠 및 편집된 콘텐츠에 대해 기본 수준 분류 유지

- 사용자에게 레이블 교육을 제공하고 올바른 레이블을 쉽게 적용하도록 지원

이 자습서는 약 15분 정도 진행할 수 있습니다.

## <a name="prerequisites"></a>전제 조건 

이 자습서를 완료하려면 다음이 필요합니다.

1. Azure Information Protection 플랜 1 또는 플랜 2를 포함하는 구독.
    
    이러한 플랜을 포함하는 구독이 없으면 조직을 위해 [무료](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) 계정을 만들 수 있습니다.

2. Azure Portal에 Azure Information Protection 블레이드를 추가하고 보호 서비스가 활성화되었는지 확인했습니다.

    이러한 작업을 수행하는 데 도움이 필요한 경우 [빠른 시작: Azure Portal에 Azure Information Protection 추가 및 정책 보기](quickstart-viewpolicy.md)를 참조하세요.

3. Azure Information Protection 클라이언트가 컴퓨터에 설치되어 있습니다. 
    
    클라이언트를 설치하려면 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)로 이동한 후 Azure Information Protection 페이지에서 **AzInfoProtection.exe**를 다운로드합니다.

4. Windows(Windows 7 서비스 팩 1 이상)를 실행하는 컴퓨터와 이 컴퓨터에서는 다음 범주 중 하나에서 Office 앱에 로그인합니다.
    
    - Office 365(Office 2016 앱 포함)(최소 버전 1805, 빌드 9330.2078) 이 옵션을 사용하려면 계정에 Azure Rights Management용 라이선스를 할당해야 합니다. 이 라이선스는 Azure Information Protection 구독에 포함되어 있습니다.
    
    - Office 365 ProPlus(2016 앱 또는 2013 앱 포함)(간편 실행 또는 Windows Installer 기반 설치)
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 서비스 팩 1
    
    - Office Professional Plus 2010 서비스 팩 2

Azure Information Protection을 사용하기 위한 필수 구성 요소의 전체 목록을 보려면 [Azure Information Protection에 대한 요구 사항](requirements.md)을 참조하세요.

이제 시작하겠습니다.

## <a name="edit-the-azure-information-protection-policy"></a>Azure Information Protection 정책 편집

사용자가 문서 및 이메일에 수동으로 레이블을 지정하도록 하는 대신, 일부 정책 설정을 사용하여 기본 분류 수준을 유지하도록 할 수 있습니다. 

Azure Portal을 사용하여 전역 정책을 편집하여 모든 사용자의 정책 설정을 변경합니다.

1. 새 브라우저 창을 열고 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. 그런 후 **Azure Information Protection**로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.
    
    전역 관리자가 아니면 대체 역할: [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal) 링크를 사용합니다.

2. **분류** > **정책** > **전역**을 선택하여 **정책: 전역** 블레이드를 엽니다. 

3. 레이블 뒤의 **Information Protection 최종 사용자에게 표시하고 적용할 설정 구성** 섹션에서 정책 설정을 찾습니다. 설정이 다음에 표시된 값과 다를 수 있습니다.
    
    ![Azure Information Protection 자습서 - 기본 설정](./media/defaultsettings-aip.png)

4. 다음 표의 값과 일치하도록 설정을 변경하세요. 이 자습서를 완료한 후에 내용을 다시 원래대로 변경하려면 변경하는 설정을 기록해 둡니다. 

    |Setting|값|정보 산업|
    |-------|-----|-----|
    |**기본 레이블 선택**|**일반**|**일반**이라는 레이블이 없는 경우 드롭다운 목록에서 다른 레이블을 선택합니다. 레이블이 지정되지 않은 문서와 이메일에는 기본 분류로 이 레이블이 자동으로 적용됩니다. 그러나 사용자는 선택한 레이블을 다른 레이블로 변경할 수 있습니다.|
    |**All documents and emails must have a label**(모든 문서 및 메일에 레이블이 있어야 함)|**On**(켜짐)|이 설정은 사용자가 레이블이 지정되지 않은 문서를 저장하거나 이메일을 전송하지 못하게 하므로 필수 레이블 지정이라고도 합니다. 문서 및 이메일에는 기본 레이블과 함께 사용자가 설정한 기본 레이블 또는 선택한 레이블이 지정됩니다.
    |**For email messages with attachments, apply a label that matches the highest classification of those attachments**(첨부 파일이 있는 메일 메시지의 경우 해당 첨부 파일의 최고 분류와 일치하는 레이블 적용)|**권장됨**|이 설정은 사용자가 선택한 기본 레이블보다 더 높은 수준의 분류를 갖는 문서를 첨부할 때 이메일에 대해 더 높은 분류 레이블을 선택하라는 메시지를 표시합니다.
    |**Display the Information Protection bar in Office apps**(Office 앱에 Information Protection 표시줄 표시)|**On**(켜짐)|Information Protection 표시줄을 표시하여 사용자가 기본 레이블을 보다 쉽게 보고 변경할 수 있도록 합니다.
    
    해당 설정은 다음과 같습니다.
    
    ![Azure Information Protection 자습서 - 기본 설정이 변경됨](./media/defaultsettings-aip-changed.png)

5. 이 **Policy: Global**(정책: 전역) 블레이드에서 **저장**을 선택하고, 작업을 확인하라는 메시지가 표시되는 경우 **확인**을 선택합니다. 

## <a name="see-your-policy-settings-in-action"></a>작동 중인 정책 설정 보기 

이 자습서에서는 Word 및 Outlook을 사용하여 작동 중인 정책 변경을 확인합니다. 이러한 앱이 정책 설정을 변경하기 전에 이미 로드된 경우 다시 시작하여 변경 사항을 다운로드합니다.

### <a name="default-label-and-the-information-protection-bar"></a>기본 레이블 및 Information Protection 표시줄

Word에서 새 문서를 엽니다. 사용자가 레이블을 선택하도록 하지 않고 문서에 **일반** 레이블이 자동으로 지정됩니다. 

Information Protection 표시줄이 표시되고 사용 가능한 레이블이 표시되므로 사용자는 현재 선택된 레이블을 쉽게 확인하고, 기본 레이블 적절하지 않을 경우 변경할 수 있습니다.

![Azure Information Protection 자습서 - 기본 레이블이 있는 새 문서](./media/defaultlabel-word.png)

레이블을 변경하는 대신, Information Protection 표시줄을 닫고 표시줄이 없을 때의 환경을 비교합니다.

![Azure Information Protection 자습서 - 기본 레이블이 있는 새 문서](./media/infoprotect-bar-close.png)

**일반** 레이블이 계속 선택되어 있지만 훨씬 덜 명확합니다. 또한 다른 레이블을 선택하는 방법도 덜 명확합니다. 다른 레이블을 선택하려면 **보호** 단추를 선택해야 합니다.

![Azure Information Protection 자습서 - 보호 단추를 선택함](./media/infoprotect-protectbutton-pulldown.png)

이제, 풀다운 메뉴에서 **일반** 레이블 옆에 확인 표시가 있으므로 선택되었는지 알 수 있습니다. 현재 선택한 레이블을 변경하기 위해 목록에서 다른 레이블을 선택할 수 있습니다. 사용자가 레이블을 처음 지정해보는 경우 매번 **보호** 단추를 선택해야 한다는 것을 기억하기 어려울 수 있습니다. 또한 다른 레이블을 선택할 수 있다는 것도 알지 못할 수 있습니다.

Information Protection 표시줄을 다시 표시하려면 풀다운 메뉴에서 **표시줄 표시**를 선택합니다.

> [!TIP]
> [고급 클라이언트 설정](./rms-client/client-admin-guide-customizations.md#set-a-different-default-label-for-outlook)을 구성하여 Outlook에 대해 다른 기본 레이블을 선택할 수 있습니다.

### <a name="mandatory-labeling"></a>필수 레이블 지정

현재 선택된 **일반** 레이블을 다른 레이블로 변경할 수 있지만 제거할 수는 없습니다. **All documents and emails must have a label**(모든 문서 및 메일에 레이블이 있어야 함)을 **On**(켜짐)으로 변경했으므로 Information Protection 표시줄에서 **레이블 삭제** 아이콘을 사용할 수 없습니다. 

해당 설정을 변경하지 않은 경우 Information Protection 표시줄에 다음 아이콘이 표시됩니다.

![Azure Information Protection 자습서 - 보호 단추를 선택함](./media/infoprotect-deletelabel-icon.png)

기본 레이블과 함께 필수 레이블 지정을 사용하면 신규 및 편집한 문서(및 이메일)에 사용자가 선택한 기본 분류가 적용됩니다. 

필수 레이블 설정을 사용하여 기본 레이블을 설정하지 않은 경우, 레이블이 지정되지 않은 문서를 저장하거나 레이블이 지정되지 않은 메일을 전송할 때 레이블을 선택하라는 메시지가 항상 표시됩니다. 계속 표시되는 이러한 메시지에 당황한 많은 사용자가 레이블을 정확하지 않게 지정할 수도 있습니다. 문서 작업 또는 메일 작성을 마쳤을 때 레이블을 선택하라는 메시지가 표시되면 워크플로가 중단됩니다. 이때 사용자는 아무 레이블이나 임의로 선택하여 다음 작업으로 넘어갈까 하는 유혹에 빠집니다.

### <a name="recommendations-for-emails-with-attachments"></a>첨부 파일이 있는 이메일에 대한 권장 사항

열려 있는 Word 문서에 대해 **일반**보다 높은 수준의 분류가 지정된 레이블을 선택합니다. 예를 들어, **기밀** 아래의 하위 레이블 중 하나[예: **기밀 - 모든 사람(보호되지 않음)**]를 선택합니다. 문서를 로컬로 저장하고 이름을 지정합니다. 

Outlook을 시작하고 새 이메일 메시지를 만듭니다. Word에서 확인한 것처럼 새 이메일 메시지에는 자동으로 **일반** 레이블이 지정되며 Information Protection 표시줄이 표시됩니다.

방금 레이블을 지정한 Word 문서를 이메일 메시지에 첨부 파일로 추가합니다. Word 첨부 파일과 일치하도록 이메일 레이블을 **기밀** 레이블로 변경할지 묻는 메시지가 표시됩니다. 사용자는 권장 사항을 수락하거나 해제할 수 있습니다.

![Azure Information Protection 자습서 - 레이블이 지정된 첨부 파일과 일치하도록 이메일의 레이블을 다시 지정하라는 메시지](./media/infoprotect-matchemail-label.png)

**해제**를 클릭하면 새 레이블이 적용되지 않지만 이전에 구성한 기본 레이블인 **일반**이 이메일에 레이블로 계속 사용되는 것을 볼 수 있습니다. 사용 가능한 레이블은 계속 표시되므로 대안으로 선택할 수 있습니다.

**지금 변경**을 선택하면 이메일에 **기밀** 하위 레이블이 다시 지정됩니다. 그러나 사용자는 레이블 편집을 선택하여 이메일을 보내기 전에 레이블을 변경할 수 있습니다.

![Azure Information Protection 자습서 - 레이블이 지정된 첨부 파일과 일치하도록 이메일의 레이블을 다시 지정하라는 메시지](./media/infoprotect-editlabel-icon.png)

Information Protection 표시줄이 다시 표시되므로 대체 레이블을 선택할 수 있습니다.

이메일을 전송하기 전에 레이블을 선택했으므로 이 정책 설정이 작동하는 방식을 확인하기 위해 실제로 이메일을 전송할 필요는 없습니다. 이메일을 보내거나 저장하지 않고 닫아도 됩니다.

그러나 이 연습 과정을 반복하면서 더 높은 수준의 분류(**극비** 레이블의 하위 레이블)가 지정된 다른 문서를 첨부할 수 있습니다. 그런 다음, 더 높은 수준의 분류 레이블을 적용하라고 메시지가 변경되는 것을 확인할 수 있습니다.

## <a name="clean-up-resources"></a>리소스 정리

이 자습서에서 변경한 내용을 유지하지 않으려는 경우 다음을 수행합니다.

1. **분류** > **정책** > **전역**을 선택하여 **정책: 전역** 블레이드를 엽니다.

2. 정책 설정을 기록해 둔 원래 값으로 되돌린 후 **저장**을 선택합니다.

Word 및 Outlook 앱을 다시 시작하여 이러한 변경 내용을 다운로드합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 설정 편집에 대한 자세한 내용은 [Azure Information Protection에 대한 정책 설정을 구성하는 방법](configure-policy-settings.md)을 참조하세요.

변경한 정책 설정은 분류의 기본 수준을 보장하고 사용자에게 적절한 레이블을 선택하도록 하는 데 도움이 되었습니다. 다음 단계는 문서 및 이메일의 내용을 검사하고 적절한 레이블을 권장하거나 자동으로 적용하여 이러한 전략을 보완하는 것입니다. 조건에 맞게 레이블을 구성하여 이 작업을 수행합니다. 자세한 내용은 [Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법](configure-policy-classification.md)을 참조하세요.
