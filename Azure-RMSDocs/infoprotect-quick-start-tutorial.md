---
title: '자습서: Azure Information Protection 정책 편집 및 새 레이블 만들기 - AIP'
description: 조직을 위한 Microsoft Azure Information Protection 정책을 편집하는 소개 자습서로, 약 15분이면 완료할 수 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: tutorial
ms.service: information-protection
ms.openlocfilehash: a619a05607f5061f51bae93d97cfd44086cefd55
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024181"
---
# <a name="tutorial-edit-the-azure-information-protection-policy-and-create-a-new-label"></a>자습서: Azure Information Protection 정책 편집 및 새 레이블 만들기

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.
> [!div class="checklist"]
> * 정책 설정 구성
> * 새 레이블 만들기 
> * 시각적 표시, 권장 분류 및 보호에 대한 레이블 구성
> * 작동 중인 설정 및 레이블 보기

이 구성으로 인해 사용자는 새 문서 또는 이메일을 만들 때 기본 레이블이 적용되는 것을 볼 수 있습니다. 그러나 신용 카드 정보가 감지되면 새 레이블을 적용하라는 메시지가 표시됩니다. 새 레이블이 적용되면 콘텐츠는 다시 분류되고 해당 바닥글 및 워터마크를 사용해서 보호됩니다. 

이 자습서는 약 15분 정도 진행할 수 있습니다.

## <a name="prerequisites"></a>전제 조건 

이 자습서를 완료하려면 다음이 필요합니다.

1. Azure Information Protection 플랜 2를 포함하는 구독.
    
    Azure Information Protection 플랜 2를 포함하는 구독이 없으면 조직을 위해 [무료](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) 계정을 만들 수 있습니다.

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

Azure Portal을 사용하여 먼저 일부 정책 설정을 변경한 후 새 레이블을 만듭니다.

### <a name="edit-the-policy-settings"></a>정책 설정 편집

1. 새 브라우저 창을 열고 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. 그런 후 **Azure Information Protection**로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.
    
    전역 관리자가 아니면 대체 역할: [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal) 링크를 사용합니다.

2. **분류** > **정책** > **전역**을 선택하여 **정책: 전역** 블레이드를 엽니다. 

3. 레이블 뒤의 **설정을 구성하여 Information Protection 최종 사용자에게 표시하고 적용** 섹션에서 정책 설정을 찾습니다. 
    
    현재 설정이 구성된 방식을 기록해 둡니다. 특히, **기본 레이블 선택** 및 **분류 레이블 낮추기, 레이블 제거 또는 보호 제거를 설정하려면 근거를 제공해야 합니다.** 설정 예를 들면 다음과 같습니다.
    
    ![Azure Information Protection 자습서 - 변경할 정책 설정](./media/info-protect-policy-default-settings.png)
    
    이 자습서의 뒷부분에서 작동 중인 정책 설정을 볼 때 사용하게 됩니다.

4. **기본 레이블 선택**에서 **일반**을 선택합니다. 

    이전 버전의 정책을 사용하고 있어 이 레이블이 없는 경우 같은 레이블로 **내부**를 선택합니다.

5. **분류 레이블 낮추기, 레이블 제거 또는 보호 제거를 설정하려면 근거를 제공해야 합니다.** 옵션을 **설정** 으로 설정합니다(아직 설정하지 않은 경우).

6. 또한 **Office 앱에 Information Protection 표시줄을 표시합니다.**가 **설정**으로 설정되어 있는지 확인합니다.

7. 이 **정책: 전역** 블레이드에서 **저장**을 선택하고, 작업을 확인하라는 메시지가 표시되는 경우 **확인**을 선택합니다. 이 블레이드를 닫습니다.

### <a name="create-a-new-label-for-protection-visual-markers-and-a-condition-to-prompt-for-classification"></a>보호를 위한 새 레이블, 시각적 표식 및 분류를 위한 메시지 표시 조건 만들기

이제 **기밀**에 대한 새 하위 레이블을 만듭니다.

1. **분류** > **레이블** 메뉴 옵션에서 **기밀** 레이블을 마우스 오른쪽 단추로 클릭하고, **하위 레이블 추가**를 선택합니다.
    
    **기밀**이라는 레이블이 없는 경우 다른 레이블을 선택하거나 대신 새 레이블을 만들고 약간의 차이는 있지만 계속 자습서를 따를 수 있습니다.

2. **하위 레이블** 블레이드에서 레이블 이름을 **금융**으로 지정하고 **직원으로만 제한되는 금융 정보를 포함하는 기밀 데이터**라는 설명을 추가합니다.
    
    이 텍스트는 선택한 레이블의 용도를 설명하고 사용자에게 도구 설명으로 표시되어 사용자가 선택할 레이블을 결정하는 데 도움을 줍니다.

3. **이 레이블을 포함하는 문서 및 메일에 대한 권한 설정**에서 **보호**를 선택하고 **보호**를 선택합니다.
    
    ![보호를 위해 Azure Information Protection 레이블 구성](./media/info-protect-protection-bar-configured.png) 
    
4. **보호** 블레이드에서 **Azure(클라우드 키)** 가 선택되었는지 확인합니다. 이 옵션은 Azure Rights Management 서비스를 사용하여 문서 및 전자 메일을 보호합니다. 또한 **권한 설정** 옵션이 선택되어 있는지 확인합니다. 그런 다음 **권한 추가**를 선택합니다.

5. **권한 추가** 블레이드에서 **\<조직 이름> 추가 - 모든 멤버**를 선택합니다. 예를 들어 조직 이름이 VanArsdel Ltd인 경우 선택할 다음 옵션이 표시됩니다.
    
    ![모든 멤버에게 Azure Information Protection 레이블에 대한 보호 권한 부여](./media/info-protect-protection-all-members.png) 
    
    이 옵션을 선택하면, 권한을 부여할 수 있는 조직의 모든 사용자가 자동으로 선택됩니다. 그러나 테넌트에서 그룹 또는 사용자를 찾아보고 검색할 수 있는 다른 옵션에서 볼 수 있습니다. 또는 **세부 정보 입력** 옵션을 선택하면 개별 메일 주소 또는 다른 조직의 모든 사용자도 지정할 수 있습니다.

6. 권한의 경우 미리 설정된 옵션 중에서 **검토자**를 선택합니다. 이 권한 수준에서 자동으로 모든 권한이 아니라 나열된 일부 권한을 부여하는 방식을 볼 수 있습니다.
    
    ![공동 작성자에게 Azure Information Protection 레이블에 대한 보호 권한 부여](./media/info-protect-protection-reviewer.png)
    
    다른 권한 수준을 선택하거나 **사용자 지정** 옵션을 사용하여 개별 사용 권한을 지정할 수 있습니다. 그러나 이 자습서에서는 **검토자** 옵션을 유지합니다. 나중에 다른 권한으로 실험하고 해당 권한에서 지정된 사용자가 보호된 문서 또는 메일에서 수행할 수 있는 작업을 제한하는 방법을 읽을 수 있습니다.

7. **확인**을 클릭하여 이 **권한 추가** 블레이드를 닫으면 **보호** 블레이드가 구성을 반영하도록 업데이트되는 방법을 볼 수 있습니다. 예를 들면 다음과 같습니다.
    
     ![Azure Information Protection 레이블에 대한 권한 구성을 보여 주는 보호 블레이드](./media/info-protect-protection-configured.png)
    
    **권한 추가**를 선택하면 **권한 추가** 블레이드가 다시 열려 더 많은 사용자를 추가하고 이들에게 서로 다른 권한을 부여할 수 있습니다. 예를 들어 특정 그룹에는 대한 보기 권한만 부여합니다. 그러나 이 자습서에서는 모든 사용자에 대해 하나의 권한 집합을 유지합니다.

8. 콘텐츠 만료 및 오프라인 액세스에 대한 기본값을 검토하고 유지한 다음 **확인**을 클릭하여 이 **보호** 블레이드를 저장하고 닫습니다.

8. **하위 레이블** 블레이드로 돌아가서 **시각적 표시 설정** 섹션을 찾습니다.
    
    **이 레이블이 포함된 문서에는 바닥글이 있습니다.** 설정에 대해 **설정**를 클릭한 다음 **텍스트** 상자에 **기밀로 분류됨**을 입력합니다. 
    
    **이 레이블이 포함된 문서에는 워터마크가 있습니다.** 설정에서 **설정**을 클릭하고 **워터마크 텍스트** 상자에 조직 이름을 입력합니다. 예를 들어 **VanArsdel, Ltd**를 입력합니다. 
    
    이러한 시각적 표식의 모양을 변경할 수는 있지만, 지금은 이러한 설정을 기본값으로 그대로 유지합니다.
    
9. **자동으로 이 레이블을 적용하기 위한 조건 구성** 섹션으로 이동합니다.
    
    **새 조건 추가**를 클릭한 다음 **조건** 블레이드에서 다음을 선택합니다.
    
    a. **조건 형식 선택**: **정보 유형**의 기본값을 유지합니다.
    
    b. **산업 선택**: 기본값인 **모두**를 유지합니다.
    
    c. **정보 유형 선택** 검색 상자에 **신용 카드 번호**를 입력합니다. 그런 다음 검색 결과에서 **신용 카드 번호**를 선택합니다.
    
    d. **최소 발생 횟수**: 기본값을 **1**로 유지합니다.
    
    e. **고유 값이 포함된 발생 수만 계산**: 기본값을 **끄기**로 유지합니다.
    
    ![Azure Information Protection 자습서 - 신용 카드 조건 구성](./media/step2-configure-condition.png)
    
    **저장**을 클릭하여 **하위 레이블** 블레이드로 돌아갑니다.

10. **하위 레이블** 블레이드에서 **신용 카드 번호**가 **조건 이름**으로 표시되고 **발생 빈도**가 **1**로 표시됩니다.
    
    ![Azure Information Protection 자습서 - 신용 카드 조건 구성](./media/step2-see-condition.png)

11. **이 레이블이 적용되는 방법 선택**의 경우: 기본값 **권장**을 유지하고 기본 정책 팁을 변경하지 않습니다. 

12. **관리자 사용을 위한 메모 추가** 상자에 **테스트 전용**을 입력합니다.

13. 이 **하위 레이블** 블레이드에서 **저장**을 클릭합니다. 확인하라는 메시지가 표시되면 **확인**을 클릭합니다. 새 레이블이 생성되고 저장되지만, 아직 정책에 추가되지는 않습니다.

14. **분류** > **정책** 메뉴 옵션에서 **글로벌**을 다시 선택한 다음, 레이블 뒤에서 **레이블 추가 또는 제거** 링크를 선택합니다.

15. **정책: 레이블 추가 또는 제거** 블레이드에서 방금 만든 레이블과 **재무**라는 하위 레이블을 선택한 다음, **확인**을 클릭합니다.

16. **정책: 전역** 블레이드에서 이제 시각적 표시 및 보호에 대해 구성된 전역 정책의 새 하위 레이블을 확인합니다. 예를 들면 다음과 같습니다.

    ![Azure Information Protection 자습서 - 새 하위 레이블](./media/info-protect-policy-configuredv2.png)
    
    또한 설정은 기본 레이블 및 근거로 구성됩니다.
    
    ![Azure Information Protection 자습서 - 설정이 구성됨](./media/info-protect-settings-configuredv2.png)
    

17. 이 **정책: 전역** 블레이드에서 **저장**을 클릭합니다. 이 작업을 확인하라는 메시지가 표시되면 **확인**을 클릭합니다.

이 자습서를 완료한 후 Azure Portal을 닫거나, 열어 둔 채로 추가 구성 옵션을 사용해 볼 수 있습니다.

변경 결과를 확인해 볼 수 있습니다.

## <a name="see-classification-labeling-and-protection-in-action"></a>작동 중인 분류, 레이블 지정 및 보호 확인 

수행한 정책 변경 내용과 만든 새 레이블이 Word, Excel, PowerPoint 및 Outlook에 적용됩니다. 하지만 이 자습서에서는 Word를 사용하여 작동 중인 해당 항목을 확인합니다. 

Word에서 새 문서를 엽니다. Azure Information Protection 클라이언트가 설치되어 있으므로 다음이 표시됩니다.

![Azure Information Protection 자습서 - 클라이언트가 설치됨](./media/word2016-calloutsv2.png)

- **홈** 탭의 **보호** 그룹(**보호** 단추가 포함됨)
    
    **보호** > **도움말 및 피드백**을 클릭하고 **Microsoft Azure Information Protection** 대화 상자에서 클라이언트 상태를 확인합니다. **연결 방식**과 사용자 이름이 표시됩니다. 또한 마지막 연결의 최근 시간 및 날짜와 Information Protection 정책이 다운로드된 시기도 표시됩니다. 표시된 사용자 이름이 테넌트에 대해 올바른지 확인합니다.

- 리본 아래에 새로운 표시줄인 Information Protection 표시줄이 표시됩니다. 여기에는 Azure Portal에서 봤던 **민감도** 제목과 레이블이 표시됩니다.

### <a name="to-manually-change-our-default-label"></a>수동으로 기본 레이블을 변경하려면

1. Information Protection 표시줄에서 마지막 레이블을 선택하면 하위 레이블이 표시되는 방식이 나타납니다.
    
    ![Azure Information Protection 자습서 - 하위 레이블 보기](./media/info-protect-sub-labelsv2.png)

2. 이러한 하위 레이블 중 하나를 선택하면 이 문서에 대한 레이블을 선택했으므로 표시줄에서 다른 레이블이 표시되는 방식을 더 이상 볼 수 없습니다. **민감도** 값이 레이블 및 하위 레이블 이름을 표시하도록 변경되며 레이블 색도 그에 맞게 변경됩니다. 예를 들면 다음과 같습니다.
    
    ![Azure Information Protection 자습서 - 하위 레이블이 선택됨](./media/info-protect-sub-label-selectedv2.png)

3. Information Protection 표시줄에서 현재 선택된 레이블 값 옆에 있는 **레이블 편집** 아이콘을 클릭합니다.
    
    ![Azure Information Protection 자습서 - 레이블 편집 아이콘](./media/info-protect-edit-label-selectedv2.png)
    
    이 작업을 수행하면 사용 가능한 레이블이 다시 표시됩니다.

4. 이제 첫 번째 레이블 **개인**을 선택합니다. 이 문서에 대해 이전에 선택한 레이블보다 낮은 분류 수준에 있는 레이블을 선택했으므로 분류 수준을 낮춘 이유를 제시하라는 메시지가 표시됩니다.
    
    ![Azure Information Protection 자습서 - 낮추는 이유를 확인하는 메시지](./media/info-protect-lower-justification.png)
    
    **이전 레이블이 더 이상 적용 안됨**을 선택하고 **확인**을 클릭합니다. **민감도** 값이 **개인**으로 변경되고 다른 레이블은 다시 숨겨집니다.

### <a name="to-remove-the-classification-completely"></a>분류를 완전히 제거하려면

1. Information Protection 표시줄에서 **레이블 편집** 아이콘을 다시 클릭합니다. 그러나 레이블 중 하나를 선택하는 대신 **레이블 삭제** 아이콘을 클릭합니다.
    
    ![Azure Information Protection 자습서 - 삭제 아이콘](./media/delete-icon-from-personalv2.png)
    
2. 이번에는 확인 메시지가 표시되면 “이 문서는 분류할 필요가 없습니다.”를 입력하고 **확인**을 클릭합니다.  
    
    **민감도** 값에 **설정 안 함**이 표시되며, 이는 기본 레이블을 정책 설정으로 설정하지 않은 경우 새 문서에 대해 사용자에게 처음에 표시되는 내용입니다.

### <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>레이블 지정 및 자동 보호에 대한 권장 메시지를 확인하려면

1. Word 문서에서 유효한 신용 카드 번호(예: **4242-4242-4242-4242**)를 입력합니다. 

2. 원하는 파일 이름으로 문서를 로컬에 저장합니다. 

3. 이제 신용 카드 번호가 감지될 경우 보호를 위해 구성한 레이블을 적용하기 위한 프롬프트가 표시됩니다. 권장 사항에 동의하지 않은 경우 정책 설정에서는 **해제**를 선택하여 거부할 수 있게 합니다. 권장 사항을 제공하되, 사용자가 권장 사항을 재정의할 수 있게 하면 자동 분류 사용 시 가양성을 줄이는 데 도움이 됩니다. 이 자습서에서는 **지금 변경**을 클릭합니다.

    ![Azure Information Protection 자습서 - 권장 메시지](./media/change-nowv2.png)

    이제 문서에서 구성된 레이블이 적용(예: **기밀 \ 금융**)된 것을 볼 수 있을 뿐만 아니라 페이지에 걸쳐 조직 이름의 워터마크를 즉시 볼 수 있으며 **기밀로 분류됨** 바닥글도 적용된 것을 볼 수 있습니다. 

    또한 문서는 이 레이블에 지정한 권한으로 보호됩니다. **파일** 탭을 클릭하고 **문서 보호**에 대한 정보를 확인하여 문서가 보호되는지 확인할 수 있습니다. 문서가 **기밀 \ 금융**으로 보호되는 것과 레이블 설명을 확인할 수 있습니다. 
    
    레이블의 보호 구성 때문에 직원만 문서를 열 수 있으며 직원의 일부 작업이 제한됩니다. 예를 들어 인쇄 권한과 콘텐츠 복사 및 추출 권한이 없으므로 문서를 인쇄하거나 문서에서 복사할 수 없습니다. 이러한 제한은 데이터 손실을 방지하는 데 도움이 됩니다. 문서의 소유자는 문서를 인쇄하고 복사할 수 있습니다. 그러나 조직의 다른 사용자에게 문서를 메일로 보내는 경우 받는 사용자는 이러한 작업을 수행할 수 없습니다.

4. 이제 이 문서를 닫을 수 있습니다.

## <a name="clean-up-resources"></a>리소스 정리

이 자습서에서 변경한 내용을 유지하지 않으려는 경우 다음을 수행합니다.

1. **분류** > **정책** > **전역**을 선택하여 **정책: 전역** 블레이드를 엽니다.

2. 정책 설정을 기록해 둔 원래 값으로 되돌린 후 **저장**을 선택합니다. 

3. 분류 > 레이블 메뉴 옵션의 Azure Information Protection - 레이블 블레이드에서 만든 재무 레이블에 대한 상황에 맞는 메뉴(**...**)를 선택합니다.

4. **이 레이블 삭제**를 선택하고 확인하라는 메시지가 표시되면 **확인**을 선택합니다.

Word를 다시 시작하여 이러한 변경 사항을 다운로드합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책을 편집하는 방법에 대한 자세한 내용은 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.

레이블 지정 활동이 로깅되는 위치에 대한 자세한 내용은 [Azure Information Protection 클라이언트에 대한 사용 현황 로깅](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client)을 참조하세요.

