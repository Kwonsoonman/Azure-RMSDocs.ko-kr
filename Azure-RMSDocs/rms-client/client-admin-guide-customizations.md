---
title: "Azure Information Protection 클라이언트에 대한 사용자 지정 구성"
description: "Windows용 Azure Information Protection 클라이언트의 사용자 지정에 대한 정보"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: d5345f794fb69ddbfb4d6ffcddfcffd41ecacff5
ms.sourcegitcommit: ff2fadacf9ef4c6ee27d9d08c4c455ffd48f21f8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2017
---
# <a name="custom-configurations-for-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에 대한 사용자 지정 구성

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection 클라이언트를 관리할 때 특정 시나리오 또는 사용자의 하위 집합에 대해 필요할 수 있는 고급 구성을 수행할 경우 다음 정보를 사용합니다.

경우에 따라 레지스트리를 편집해야 하는 설정도 있고 고급 설정을 사용해야 하는 경우도 있습니다. 고급 설정이 필요한 설정은 Azure Portal에서 구성한 후 클라이언트에서 다운로드할 수 있게 게시해야 합니다.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>포털에서 고급 클라이언트 구성 설정을 구성하는 방법

1. 아직 그렇게 하지 않은 경우에는, 새 브라우저 창에서 보안 관리자나 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다.

2. 초기 Azure Information Protection 블레이드에서 **범위 정책**을 선택합니다.

3. **Azure Information Protection - 범위 정책** 블레이드에서 고급 설정을 포함할 정책 옆에 있는 상황에 맞는 메뉴(**...**)를 선택합니다. 그런 후 **고급 설정**을 선택합니다.
    
    범위 정책 뿐만 아니라 전역 정책에 대해 고급 설정을 구성할 수 있습니다.

4. **고급 설정** 블레이드에서 고급 설정 이름 및 값을 입력한 다음 **저장 후 닫기**를 선택합니다.

5. **게시**를 클릭하고 이 정책에 대한 사용자가 열어 놓은 모든 Office 응용 프로그램을 다시 시작하는지 확인합니다.

6. 더 이상 해당 설정이 필요하지 않으며 기본 동작으로 되돌리려면 **고급 설정** 블레이드에서 더 이상 필요하지 않은 설정 옆에 있는 상황에 맞는 메뉴(**...**)를 선택하고 **삭제**를 선택합니다. **저장 후 닫기**를 클릭하고 수정된 정책을 다시 게시합니다.

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>AD RMS 전용 컴퓨터의 로그인 프롬프트 방지

기본적으로 Azure Information Protection 클라이언트는 자동으로 Azure Information Protection 서비스에 연결하려 합니다. AD RMS와만 통신하는 컴퓨터의 경우 이 구성을 사용하면 불필요하게 사용자에게 로그인 프롬프트가 표시될 수 있습니다. 레지스트리를 편집하면 이 로그인 프롬프트를 방지할 수 있습니다.

다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

이 설정에 관계 없이 Azure Information Protection 클라이언트는 표준 [RMS 서비스 검색 프로세스](../rms-client/client-deployment-notes.md#rms-service-discovery)에 따라 AD RMS 클러스터를 찾습니다.

## <a name="sign-in-as-a-different-user"></a>다른 사용자로 로그인

프로덕션 환경에서는 Azure Information Protection 클라이언트를 사용 중에 일반적으로 다른 사용자로 로그인할 필요가 없습니다. 그러나 관리자는 테스트 단계 동안 다른 사용자로 로그인해야 할 수 있습니다. 

**Microsoft Azure Information Protection** 대화 상자를 사용하여 현재 로그인한 계정을 확인할 수 있습니다. Office 응용 프로그램을 열고 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 의견**을 클릭합니다. 계정 이름은 **클라이언트 상태** 섹션에 표시됩니다.

또한 표시되는 로그인 계정의 도메인 이름을 확인해야 합니다. 계정 이름은 올바르지만 잘못된 도메인으로 로그인하는 경우를 간과하기 쉽습니다. 잘못된 계정을 사용할 경우 Azure Information Protection 정책을 다운로드하지 못하거나 예상한 레이블 또는 동작이 표시되지 않을 수 있습니다.

다른 사용자로 로그인하려면 다음과 같이 합니다.

1. **%localappdata%\Microsoft\MSIP**로 이동하고 **TokenCache** 파일을 삭제합니다.

2. 열려 있는 Office 응용 프로그램을 다시 시작하고 다른 사용자 계정으로 로그인합니다. Office 응용 프로그램에서 Azure Information Protection 서비스에 로그인하라는 메시지가 표시되지 않는 경우 **Microsoft Azure Information Protection** 대화 상자로 돌아와 업데이트된 **클라이언트 상태** 섹션에서 **로그인**을 클릭합니다.

추가 필수 구성 요소:

- 이 솔루션은 동일한 테넌트의 다른 사용자로 로그인에 대해 지원됩니다. 이 솔루션은 다른 테넌트의 다른 사용자로 로그인에 대해 지원되지 않습니다. 여러 테넌트로 Azure Information Protection을 테스트하려면 여러 컴퓨터를 사용합니다.

- Single Sign-On을 사용할 경우 Windows에서 로그아웃하고 레지스트리를 편집한 후 다른 사용자 계정으로 로그인해야 합니다. Azure Information Protection 클라이언트에서는 현재 로그인한 사용자 계정을 사용하여 자동으로 인증합니다.

- **도움말 및 피드백**의 **설정 재설정** 옵션을 사용하여 로그아웃하고 현재 다운로드한 Azure Information Protection 정책을 삭제할 수 있습니다.

## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>조직에 혼합 라이선스가 있을 때 보호 전용 모드 적용

조직에 Azure Information Protection에 대한 라이선스가 없지만 데이터 보호에 대한 Azure Rights Management 서비스가 포함된 Office 365에 대한 라이선스가 있는 경우, Windows용 Azure Information Protection 클라이언트는 자동으로 [보호 전용 모드](../rms-client/client-protection-only-mode.md)에서 실행됩니다.

그러나 조직에 Azure Information Protection에 대한 구독이 있는 경우 기본적으로 모든 Windows 컴퓨터에서 Azure Information Protection 정책을 다운로드할 수 있습니다. Azure Information Protection 클라이언트는 라이선스 확인 및 적용을 수행하지 않습니다. 

일부 사용자에게 Azure Information Protection에 대한 라이선스는 없지만 Azure Rights Management 서비스가 포함된 Office 365에 대한 라이선스가 있는 경우, 이러한 사용자의 컴퓨터에 있는 레지스트리를 편집하여 사용자가 Azure Information Protection의 라이선스가 없는 분류 및 레이블 지정 기능을 실행하지 못하도록 합니다.

다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

또한 이러한 컴퓨터의 **%LocalAppData%\Microsoft\MSIP** 폴더에 **Policy.msip**라는 파일이 없는지 확인합니다. 이 파일이 있는 경우 삭제합니다. 이 파일에는 Azure Information Protection 정책이 포함되어 있으며 레지스트리를 편집하기 전에 다운로드했거나, Azure Information Protection 클라이언트가 데모 옵션으로 설치되었을 수 있습니다.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Windows 파일 탐색기에서 [분류 및 보호] 메뉴 옵션 숨기기

다음 DWORD 값 이름(모든 값 데이터 포함)을 만듭니다.

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>연결이 끊어진 컴퓨터에 대한 지원

기본적으로 Azure Information Protection 클라이언트는 자동으로 Azure Information Protection 서비스에 연결하여 최신Azure Information Protection 정책을 다운로드합니다. 일정 기간 동안 인터넷에 연결할 수 없는 컴퓨터를 사용하는 경우 레지스트리를 편집하여 클라이언트가 서비스에 연결하지 못하도록 할 수 있습니다. 

다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

클라이언트의 **%LocalAppData%\Microsoft\MSIP** 폴더에 **Policy.msip**라는 이름의 유효한 정책 파일이 있는지 확인합니다. 필요한 경우 Azure 포털에서 정책을 내보낼 수 있으며 클라이언트 컴퓨터에 내보내기된 파일을 복사할 수 있습니다. 또한 이러한 방법을 통해 오래된 정책 파일을 게시된 최신 정책으로 바꿀 수 있습니다.

정책을 내보낼 때 이 작업은 여러 다른 버전의 Azure Information Protection 클라이언트에 해당하는 여러 버전의 정책이 있는 압축된 파일을 다운로드합니다.

1. 파일의 압축을 해제하고 다음 테이블을 사용하여 필요한 정책 파일을 식별합니다. 
    
    |파일 이름|해당하는 클라이언트 버전|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |버전 1.2|
    |Policy1.2.msip |버전 1.3 - 1.7|
    |Policy1.3.msip |버전 1.8 이상|
    
2. 식별된 파일 이름을 **Policy.msip**로 변경하고 Azure Information Protection 클라이언트가 있는 컴퓨터의 **%LocalAppData%\Microsoft\MSIP** 폴더에 복사합니다. 


## <a name="hide-the-do-not-forward-button-in-outlook"></a>Outlook에서 전달 금지 단추 숨기기

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다.

이 설정을 구성하는 경우 Outlook의 리본에서 **전달 금지** 단추가 숨겨집니다. Office 메뉴에서는 이 옵션이 숨겨지지 않습니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **DisableDNF**

- 값: **True**

## <a name="make-the-custom-permissions-options-unavailable-to-users"></a>사용자 지정 권한 옵션을 사용자가 사용할 수 없음

> [!IMPORTANT]
> 현재 미리 보기 버전의 클라이언트를 사용하지 않는 한 Word, Excel, PowerPoint 및 파일 탐색기의 사용자 정의 권한에 대해 구성된 레이블이 있는 경우 이 옵션을 사용하지 마세요. 이 옵션을 사용할 경우 레이블이 적용되면 사용자 지정 권한을 구성하라는 메시지가 사용자에게 표시되지 않습니다. 결과는 문서에 레이블이 지정되지만, 문서가 의도한 대로 보호되지 않습니다.

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

이 설정을 구성하고 사용자에게 정책을 게시하는 경우 사용자는 다음 위치의 사용자 지정 권한 옵션을 선택할 수 없게 됩니다.

- Office 응용 프로그램: **홈** 탭 > **보호** 그룹 > **보호** > **사용자 지정 권한**

- 파일 탐색기: 마우스 오른쪽 단추 클릭 > **분류 및 보호** > **사용자 지정 권한**

이 설정은 Office 메뉴 옵션에서 구성할 수 있는 사용자 지정 권한에는 적용되지 않습니다. 

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **EnableCustomPermissions**

- 값: **False**

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Azure Information Protection 표시줄을 영구적으로 숨기기

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

사용자를 위해 이 설정을 구성하고 정책을 게시하며, 사용자가 Office 응용 프로그램에 Azure Information Protection 표시줄을 표시하지 않도록 선택하는 경우 이 표시줄은 숨겨진 상태를 유지합니다. 사용자가 **홈** 탭, **보호** 그룹, **보호** 단추에서 **표시줄 표시** 옵션을 선택 취소하면 이러한 상황이 발생합니다. **이 표시줄 닫기** 아이콘을 사용하여 표시줄을 닫으면 이 설정이 아무런 영향도 미치지 않습니다.

Azure Information Protection 표시줄은 숨겨진 상태를 유지하지만 권장되는 분류를 구성했거나 문서 또는 전자 메일에 레이블이 필요한 경우 일시적으로 표시되는 표시줄에서 레이블을 계속 선택할 수 있습니다. 이 설정은 수동 또는 자동 분류, 기본 레이블 설정과 같이 사용자 또는 다른 사용자가 구성하는 레이블에도 영향을 주지 않습니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **EnableBarHiding**

- 값: **True**


## <a name="enable-recommended-classification-in-outlook"></a>Outlook에서 권장 분류 사용

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다.

권장 분류에 대한 레이블을 구성하면 Word, Excel 및 PowerPoint에서 권장 레이블을 적용할지 또는 해제할지 묻는 메시지가 표시됩니다. 이 설정은 이 레이블 권장 사항을 확장하여 Outlook에도 표시합니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **OutlookRecommendationEnabled**

- 값: **True**


## <a name="set-a-different-default-label-for-outlook"></a>Outlook에 대한 다른 기본 레이블 설정

이 구성 옵션은 현재 미리 보기 상태이며, 미리 보기 버전의 클라이언트가 필요합니다.

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

이 설정을 구성하면 Outlook에서 **기본 레이블 선택** 설정의 Azure Information Protection 정책에 구성된 기본 레이블을 적용하지 않습니다. 대신 Outlook에서 다른 레이블을 적용할 수 있거나 레이블이 적용되지 않습니다.

다른 레이블을 적용하려면 레이블 ID를 지정해야 합니다. Azure Portal에서 Azure Information Protection 정책을 보거나 구성하는 경우 레이블 ID 값이 **레이블** 블레이드에 표시됩니다. 레이블이 적용된 파일의 경우 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) PowerShell cmdlet을 실행하여 레이블 ID(MainLabelId 또는 SubLabelId)를 확인할 수도 있습니다. 레이블에 하위 레이블이 있는 경우 항상 부모 레이블이 아니라 하위 레이블의 ID만 지정합니다.

따라서 Outlook에서 기본 레이블을 적용하지 않으려면 **없음**을 지정합니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **OutlookDefaultLabel**

- 값: \<**레이블 ID**> 또는 **없음**


## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>모바일 장치 레이블 지정 솔루션을 위해 Exchange 메시지 분류와 통합

웹용 Outlook에서는 아직 기본적으로 Azure Information Protection 분류 및 보호를 지원하지 않지만 Exchange 메시지 분류를 사용하여 Azure Information Protection 레이블을 모바일 사용자로 확장할 수 있습니다.

이 솔루션을 활용하려면 다음을 수행합니다. 

1. [New-MessageClassification](https://technet.microsoft.com/library/bb124400) Exchange PowerShell cmdlet을 사용하여 Azure Information Protection 정책의 레이블 이름에 매핑되는 Name 속성을 포함하는 메시지 분류를 만듭니다. 

2. 각 레이블에 대해 Exchange 전송 규칙을 만든 다음 구성된 분류가 메시지 속성에 포함될 때 해당 규칙을 적용하고 메시지 속성을 수정하여 메시지 헤더를 설정합니다. 

    메시지 헤더에서는 Azure Information Protection 레이블을 사용하여 분류하고 보낸 메일의 인터넷 헤더를 검사하면 지정할 정보를 확인할 수 있습니다. **msip_labels** 헤더와 바로 뒤에서 세미콜론까지의 문자열(세미콜론도 포함)을 찾습니다. 이전 예를 사용하면 다음과 같습니다.
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    그런 다음 규칙의 메시지 헤더에 대해 **msip_labels**를 헤더로, 이 문자열의 나머지 부분을 헤더 값으로 지정합니다. 예를 들면 다음과 같습니다.
    
    ![특정 Azure Information Protection 레이블에 대한 메시지 헤더를 설정하는 Exchange Online 전송 규칙 예제](../media/exchange-rule-for-message-header.png)

이 구성을 테스트하기 전에 전송 규칙을 만들거나 편집할 때 지연이 발생하는 경우가 종종 있습니다(예: 1시간 대기). 규칙이 적용되면 사용자가 Rights Management 보호를 지원하는 모바일 장치 클라이언트 또는 웹용 Outlook을 사용할 때 다음과 같은 이벤트가 진행됩니다. 

- 사용자가 Exchange 메시지 분류를 선택하고 전자 메일을 보냅니다.

- Exchange 규칙이 Exchange 분류를 검색한 다음 그에 따라 메시지 헤더를 수정하여 Azure Information Protection 분류를 추가합니다.

- 받는 사람이 Outlook에서 전자 메일을 보며 Azure Information Protection 클라이언트를 설치한 경우 할당된 Azure Information Protection 레이블과 그에 해당하는 전자 메일 머리글, 바닥글 또는 워터마크가 표시됩니다. 

Azure Information Protection 레이블이 권한 관리 보호를 적용하는 경우에는 메시지 보안을 수정하는 옵션을 선택하여 규칙 구성에 권한 관리 보호를 추가하고, 권한 보호를 적용한 후에 RMS 템플릿 또는 전달 금지 옵션을 선택합니다.

또한 역방향 매핑을 수행하도록 전송 규칙을 구성할 수 있습니다. Azure Information Protection 레이블이 검색되면 해당 Exchange 메시지 분류를 설정합니다.

- 각 Azure Information Protection 레이블에 대해 **msip_labels** 헤더에 레이블의 이름(예: **General**)이 포함될 때 적용되는 전송 규칙을 만들고 이 레이블에 매핑되는 메시지 분류를 적용합니다.


## <a name="next-steps"></a>다음 단계
Azure Information Protection 클라이언트를 사용자 지정했으므로 다음 리소스에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
