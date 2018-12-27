---
title: Azure Information Protection 클라이언트에 대한 사용자 지정 구성
description: Windows용 Azure Information Protection 클라이언트의 사용자 지정에 대한 정보
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/13/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 2ecb0376ac7d4d4ddd476e76a60053ff408e2bbd
ms.sourcegitcommit: db24caa96033fd0c7a0fad4e36518a816a570c94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53335543"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>관리자 가이드: Azure Information Protection 클라이언트에 대한 사용자 지정 구성

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection 클라이언트를 관리할 때 특정 시나리오 또는 사용자의 하위 집합에 대해 필요할 수 있는 고급 구성을 수행할 경우 다음 정보를 사용합니다.

경우에 따라 레지스트리를 편집해야 하는 설정도 있고 고급 설정을 사용해야 하는 경우도 있습니다. 고급 설정이 필요한 설정은 Azure Portal에서 구성한 후 클라이언트에서 다운로드할 수 있게 게시해야 합니다.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>포털에서 고급 클라이언트 구성 설정을 구성하는 방법

1. 아직 그렇게 하지 않은 경우에는, 새 브라우저 창에서 [Azure Portal에 로그인](../configure-policy.md#signing-in-to-the-azure-portal)한 다음, **Azure Information Protection** 블레이드로 이동합니다.

2. **분류** > **레이블** 메뉴 옵션에서: **정책**을 선택합니다.

3. **Azure Information Protection - 정책** 블레이드에서 고급 설정을 포함할 정책 옆에 있는 상황에 맞는 메뉴(**...**)를 선택합니다. 그런 후 **고급 설정**을 선택합니다.
    
    범위 정책 뿐만 아니라 전역 정책에 대해 고급 설정을 구성할 수 있습니다.

4. **고급 설정** 블레이드에서 고급 설정 이름 및 값을 입력한 다음 **저장 후 닫기**를 선택합니다.

5. 이 정책에 대한 사용자가 열어 놓은 모든 Office 애플리케이션을 다시 시작하는지 확인합니다.

6. 더 이상 해당 설정이 필요하지 않고 기본 동작으로 되돌리려는 경우: **고급 설정** 블레이드에서 더 이상 필요하지 않은 설정 옆에 있는 바로 가기 메뉴(**...**)를 선택하고 **삭제**를 선택합니다. 그런 다음, **저장 후 닫기**를 클릭합니다.

#### <a name="available-advanced-client-settings"></a>사용 가능한 고급 클라이언트 설정

|Setting|시나리오 및 지침|
|----------------|---------------|
|DisableDNF|[Outlook에서 전달 금지 단추 숨기기 또는 표시](#hide-or-show-the-do-not-forward-button-in-outlook)|
|EnableBarHiding|[Azure Information Protection 표시줄을 영구적으로 숨기기](#permanently-hide-the-azure-information-protection-bar)|
|EnableCustomPermissions|[사용자의 사용자 지정 권한 옵션 사용 가능 여부 지정](#make-the-custom-permissions-options-available-or-unavailable-to-users)|
|EnablePDFv2Protection|[PDF 암호화를 위한 ISO 표준을 사용하여 PDF 파일을 보호하지 않음](#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption)|
|LabelbyCustomProperty|[Secure Islands 및 기타 레이블 지정 솔루션에서 레이블 마이그레이션](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|LabelToSMIME|[Outlook에서 S/MIME 보호를 적용하도록 레이블 구성](#configure-a-label-to-apply-smime-protection-in-outlook)|
|OutlookDefaultLabel|[Outlook에 대한 다른 기본 레이블 설정](#set-a-different-default-label-for-outlook)|
|OutlookRecommendationEnabled|[Outlook에서 권장 분류 사용](#enable-recommended-classification-in-outlook)|
|PostponeMandatoryBeforeSave|[필수 레이블을 사용하는 경우 문서에 대한 “나중에” 제거](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|ProcessUsingLowIntegrity|[스캐너에 대해 낮은 무결성 수준 사용 안 함](#disable-the-low-integrity-level-for-the-scanner)|
|PullPolicy|[연결 해제된 컴퓨터 지원](#support-for-disconnected-computers)
|RemoveExternalContentMarkingInApp|[다른 레이블 지정 솔루션에서 헤더 및 바닥글 제거](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[사용자에 대한 “문제 보고” 추가](#add-report-an-issue-for-users)|
|RunPolicyInBackground|[백그라운드에서 계속해서 실행되도록 분류 켜기](#turn-on-classification-to-run-continuously-in-the-background)|
|SyncPropertyName|[기존 사용자 지정 속성을 사용하여 Office 문서에 레이블 지정](#label-an-office-document-by-using-an-existing-custom-property)|
|SyncPropertyState|[기존 사용자 지정 속성을 사용하여 Office 문서에 레이블 지정](#label-an-office-document-by-using-an-existing-custom-property)|

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>AD RMS 전용 컴퓨터의 로그인 프롬프트 방지

기본적으로 Azure Information Protection 클라이언트는 자동으로 Azure Information Protection 서비스에 연결하려 합니다. AD RMS와만 통신하는 컴퓨터의 경우 이 구성을 사용하면 불필요하게 사용자에게 로그인 프롬프트가 표시될 수 있습니다. 레지스트리를 편집하면 이 로그인 프롬프트를 방지할 수 있습니다.

 - 다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.
    
    **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

이 설정과 관계없이 Azure Information Protection 클라이언트는 표준 [RMS 서비스 검색 프로세스](client-deployment-notes.md#rms-service-discovery)에 따라 AD RMS 클러스터를 찾습니다.

## <a name="sign-in-as-a-different-user"></a>다른 사용자로 로그인

프로덕션 환경에서는 Azure Information Protection 클라이언트를 사용 중에 일반적으로 다른 사용자로 로그인할 필요가 없습니다. 그러나 관리자는 테스트 단계 동안 다른 사용자로 로그인해야 할 수 있습니다. 

**Microsoft Azure Information Protection** 대화 상자를 사용하여 현재 로그인한 계정을 확인할 수 있습니다. Office 응용 프로그램을 열고 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다. 계정 이름은 **클라이언트 상태** 섹션에 표시됩니다.

또한 표시되는 로그인 계정의 도메인 이름을 확인해야 합니다. 계정 이름은 올바르지만 잘못된 도메인으로 로그인하는 경우를 간과하기 쉽습니다. 잘못된 계정을 사용할 경우 Azure Information Protection 정책을 다운로드하지 못하거나 예상한 레이블 또는 동작이 표시되지 않을 수 있습니다.

다른 사용자로 로그인하려면 다음과 같이 합니다.

1. **%localappdata%\Microsoft\MSIP**로 이동하고 **TokenCache** 파일을 삭제합니다.

2. 열려 있는 Office 애플리케이션을 다시 시작하고 다른 사용자 계정으로 로그인합니다. Office 애플리케이션에서 Azure Information Protection 서비스에 로그인하라는 메시지가 표시되지 않는 경우 **Microsoft Azure Information Protection** 대화 상자로 돌아와 업데이트된 **클라이언트 상태** 섹션에서 **로그인**을 클릭합니다.

추가 필수 구성 요소:

- Azure Information Protection 클라이언트가 위 단계를 완료한 후에도 기존 계정으로 로그인되어 있는 경우, Internet Explorer에서 쿠키를 모두 삭제하고 1단계와 2단계를 다시 수행합니다.

- Single Sign-On을 사용하는 경우, Windows에서 로그아웃하고 토큰 파일을 삭제한 후 다른 사용자 계정으로 로그인해야 합니다. Azure Information Protection 클라이언트에서는 현재 로그인한 사용자 계정을 사용하여 자동으로 인증합니다.

- 이 솔루션은 동일한 테넌트의 다른 사용자로 로그인에 대해 지원됩니다. 이 솔루션은 다른 테넌트의 다른 사용자로 로그인에 대해 지원되지 않습니다. 여러 테넌트로 Azure Information Protection을 테스트하려면 여러 컴퓨터를 사용합니다.

- **도움말 및 피드백**의 **설정 재설정** 옵션을 사용하여 로그아웃하고 현재 다운로드한 Azure Information Protection 정책을 삭제할 수 있습니다.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>조직에 혼합 라이선스가 있을 때 보호 전용 모드 적용

조직에 Azure Information Protection에 대한 라이선스가 없지만 데이터를 보호하기 위해 Azure Rights Management 서비스가 포함된 Office 365에 대한 라이선스가 있는 경우, Windows용 Azure Information Protection 클라이언트는 자동으로 [보호 전용 모드](client-protection-only-mode.md)에서 실행됩니다.

그러나 조직에 Azure Information Protection에 대한 구독이 있는 경우 기본적으로 모든 Windows 컴퓨터에서 Azure Information Protection 정책을 다운로드할 수 있습니다. Azure Information Protection 클라이언트는 라이선스 확인 및 적용을 수행하지 않습니다. 

일부 사용자에게 Azure Information Protection에 대한 라이선스는 없지만 Azure Rights Management 서비스가 포함된 Office 365에 대한 라이선스가 있는 경우, 이러한 사용자의 컴퓨터에 있는 레지스트리를 편집하여 사용자가 Azure Information Protection의 라이선스가 없는 분류 및 레이블 지정 기능을 실행하지 못하도록 합니다.

다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

또한 이러한 컴퓨터의 **%LocalAppData%\Microsoft\MSIP** 폴더에 **Policy.msip**라는 파일이 없는지 확인합니다. 이 파일이 있는 경우 삭제합니다. 이 파일에는 Azure Information Protection 정책이 포함되어 있으며 레지스트리를 편집하기 전에 다운로드했거나, Azure Information Protection 클라이언트가 데모 옵션으로 설치되었을 수 있습니다.

## <a name="add-report-an-issue-for-users"></a>사용자에 대한 “문제 보고” 추가

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

다음 고급 클라이언트 설정을 지정하는 경우 **도움말 및 피드백** 클라이언트 대화 상자에서 선택할 수 있는 **문제 보고** 옵션이 사용자에게 표시됩니다. 링크에 대한 HTTP 문자열을 지정합니다. 예를 들어 사용자가 문제를 보고하는 사용자 지정된 웹 페이지 또는 지원 센터로 이동하는 메일 주소입니다. 

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **ReportAnIssueLink**

- Value: **\<HTTP 문자열>**

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Windows 파일 탐색기에서 [분류 및 보호] 메뉴 옵션 숨기기

다음 DWORD 값 이름(모든 값 데이터 포함)을 만듭니다.

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>연결이 끊어진 컴퓨터에 대한 지원

기본적으로 Azure Information Protection 클라이언트는 자동으로 Azure Information Protection 서비스에 연결하여 최신Azure Information Protection 정책을 다운로드합니다. 일정 기간 동안 인터넷에 연결할 수 없는 컴퓨터를 사용하는 경우 레지스트리를 편집하여 클라이언트가 서비스에 연결하지 못하도록 할 수 있습니다. 

인터넷에 연결하지 않으면 클라이언트가 조직의 클라우드 기반 키를 사용하여 보호를 적용(또는 보호를 제거)할 수 없습니다. 대신 클라이언트는 분류만 적용하는 레이블을 사용하거나 [HYOK](../configure-adrms-restrictions.md)를 활용하는 보호를 사용하도록 제한됩니다.

[고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용하여 Azure Information Protection 서비스 로그인 프롬프트를 방지할 수 있습니다. 고급 클라이언트 설정은 Azure Portal에서 구성한 다음 컴퓨터로 정책을 다운로드해야 합니다. 또는 레지스트리를 편집하여 이 로그인 프롬프트를 방지할 수도 있습니다.

- 고급 클라이언트 설정을 구성하려면:
    
    1. 다음 문자열을 입력합니다.
    
        - 키: **PullPolicy**
        
        - Value: **False**
    
    2. 이 설정으로 된 정책을 다운로드한 후 다음 지침에 따라 컴퓨터에 설치합니다.

- 레지스트리를 편집하려면:
    
    - 다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.
    
        **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 


클라이언트의 **%LocalAppData%\Microsoft\MSIP** 폴더에 **Policy.msip**라는 이름의 유효한 정책 파일이 있어야 합니다.

Azure Portal에서 전역 정책 또는 범위 지정 정책을 내보낸 다음, 내보낸 파일을 클라이언트 컴퓨터로 복사할 수 있습니다. 이 방법을 사용하여 오래된 정책 파일을 최신 정책으로 바꿀 수도 있습니다. 그러나 정책 내보내기는 사용자가 둘 이상의 범위 지정 정책에 속하는 시나리오를 지원하지 않습니다. 사용자가 [도움말 및 피드백](client-admin-guide.md#help-and-feedback-section)의 **설정 재설정** 옵션을 선택하는 경우, 정책 파일이 삭제되고 정책 파일을 수동으로 바꾸거나 클라이언트가 서비스에 연결하여 정책을 다운로드할 때까지 클라이언트가 작동 불가능하게 됩니다.

Azure Portal에서 정책을 내보내면 여러 버전의 정책이 포함된 Zip 파일이 다운로드됩니다. 이러한 정책 버전은 여러 버전의 Azure Information Protection 클라이언트에 해당됩니다.

1. 파일의 압축을 해제하고 다음 테이블을 사용하여 필요한 정책 파일을 식별합니다. 
    
    |파일 이름|해당하는 클라이언트 버전|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |버전 1.2|
    |Policy1.2.msip |버전 1.3 - 1.7|
    |Policy1.3.msip |버전 1.8 - 1.29|
    |Policy1.4.msip |버전 1.32 이상|
    
2. 식별된 파일 이름을 **Policy.msip**로 변경하고 Azure Information Protection 클라이언트가 있는 컴퓨터의 **%LocalAppData%\Microsoft\MSIP** 폴더에 복사합니다. 


## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Outlook에서 전달 금지 단추 숨기기 또는 표시

이 옵션 구성 시 권장되는 방법은 **Outlook 리본에 전달 금지 단추 추가** [정책 설정](../configure-policy-settings.md)을 사용하는 것입니다. 하지만 Azure Portal에서 구성하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용하여 이 옵션을 구성할 수도 있습니다.

이 설정을 구성하는 경우 Outlook의 리본에서 **전달 금지** 단추가 숨겨지거나 표시됩니다. 이 설정은 Office 메뉴의 전달 금지 옵션에 적용되지 않습니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **DisableDNF**

- Value: 단추를 숨기려면 **True**, 단추를 표시하려면 **False**

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>사용자의 사용자 지정 권한 옵션 사용 가능 여부 지정

이 옵션 구성 시 권장되는 방법은 **Make the custom permissions option available for users**(사용자가 사용자 지정 권한 옵션을 사용할 수 있게 허용) [정책 설정](../configure-policy-settings.md)을 사용하는 것입니다. 하지만 Azure Portal에서 구성하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용하여 이 옵션을 구성할 수도 있습니다. 

이 설정을 구성하고 사용자에게 정책을 게시하면 사용자에게 사용자 지정 권한 옵션이 표시되어 고유한 보호 설정을 선택하거나, 숨겨져서 메시지가 표시되지 않으면 사용자가 고유한 보호 설정을 선택할 수 없게 됩니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **EnableCustomPermissions**

- Value: 사용자 지정 권한 옵션을 표시하려면 **True**, 이 옵션을 숨기려면 **False**입니다.


## <a name="permanently-hide-the-azure-information-protection-bar"></a>Azure Information Protection 표시줄을 영구적으로 숨기기

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. **Display the Information Protection bar in Office apps**(Office 앱에 Information Protection 표시줄 표시) [정책 설정](../configure-policy-settings.md)이 **켜기**로 설정된 경우에만 사용하세요.

사용자를 위해 이 설정을 구성하고 정책을 게시하며, 사용자가 Office 애플리케이션에 Azure Information Protection 표시줄을 표시하지 않도록 선택하는 경우 이 표시줄은 숨겨진 상태를 유지합니다. 사용자가 **홈** 탭, **보호** 그룹, **보호** 단추에서 **표시줄 표시** 옵션을 선택 취소하면 이러한 상황이 발생합니다. **이 표시줄 닫기** 아이콘을 사용하여 표시줄을 닫으면 이 설정이 아무런 영향도 미치지 않습니다.

Azure Information Protection 표시줄은 숨겨진 상태를 유지하지만 권장되는 분류를 구성했거나 문서 또는 전자 메일에 레이블이 필요한 경우 일시적으로 표시되는 표시줄에서 레이블을 계속 선택할 수 있습니다. 

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **EnableBarHiding**

- Value: **True**


## <a name="enable-recommended-classification-in-outlook"></a>Outlook에서 권장 분류 사용

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 이 설정은 미리 보기로 제공되고 변경될 수 있습니다.

권장 분류에 대한 레이블을 구성하면 Word, Excel 및 PowerPoint에서 권장 레이블을 적용할지 또는 해제할지 묻는 메시지가 표시됩니다. 이 설정은 이 레이블 권장 사항을 확장하여 Outlook에도 표시합니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **OutlookRecommendationEnabled**

- Value: **True**


## <a name="set-a-different-default-label-for-outlook"></a>Outlook에 대한 다른 기본 레이블 설정

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

이 설정을 구성하면 Outlook에서 **기본 레이블 선택** 설정의 Azure Information Protection 정책에 구성된 기본 레이블을 적용하지 않습니다. 대신 Outlook에서 다른 기본 레이블을 적용할 수 있거나 레이블을 적용하지 않습니다.

다른 레이블을 적용하려면 레이블 ID를 지정해야 합니다. Azure Portal에서 Azure Information Protection 정책을 보거나 구성하는 경우 레이블 ID 값이 **레이블** 블레이드에 표시됩니다. 레이블이 적용된 파일의 경우 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) PowerShell cmdlet을 실행하여 레이블 ID(MainLabelId 또는 SubLabelId)를 확인할 수도 있습니다. 레이블에 하위 레이블이 있는 경우 항상 부모 레이블이 아니라 하위 레이블의 ID만 지정합니다.

따라서 Outlook에서 기본 레이블을 적용하지 않으려면 **없음**을 지정합니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **OutlookDefaultLabel**

- 값: \<**레이블 ID**> 또는 **없음**

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Outlook에서 S/MIME 보호를 적용하도록 레이블 구성

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 이 설정은 미리 보기로 제공되고 변경될 수 있습니다.

정상 작동하는 [S/MIME 배포](https://docs.microsoft.com/office365/SecurityCompliance/s-mime-for-message-signing-and-encryption)가 있고, Azure Information Protection의 Rights Management를 사용하는 대신 메일에 이 보호 방법을 자동으로 적용하는 레이블을 사용하려는 경우에만 이 설정을 사용합니다. 그 결과로 적용되는 보호는 사용자가 Outlook에서 수동으로 S/MIME 옵션을 선택한 경우와 동일합니다.

이 구성을 사용하려면 S/MIME 보호를 적용하려는 각 Azure Information Protection 레이블에서 이름이 **LabelToSMIME**인 고급 클라이언트 설정을 지정해야 합니다. 그런 다음 각 항목의 값을 다음 구문을 사용하여 설정합니다.

`[Azure Information Protection label ID];[S/MIME action]`

Azure Portal에서 Azure Information Protection 정책을 보거나 구성하는 경우 레이블 ID 값이 **레이블** 블레이드에 표시됩니다. 하위 레이블이 있는 S/MIME를 사용하려면 항상 상위 레이블이 아닌 하위 레이블의 ID를 지정해야 합니다. 하위 레이블을 지정할 때는 상위 레이블이 같은 범위 또는 전역 정책에 있어야 합니다.

S/MIME 작업은 다음이 될 수 있습니다.

- `Sign;Encrypt`: 디지털 서명과 S/MIME 암호화를 적용하려면

- `Encrypt`: S/MIME 암호화만 적용하려면

- `Sign`: 디지털 서명만 적용하려면

레이블 ID **dcf781ba-727f-4860-b3c1-73479e31912b**의 값 예시:

- 디지털 서명과 S/MIME 암호화를 적용하려면:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign;Encrypt**

- S/MIME 암호화만 적용하려면:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Encrypt**
    
- 디지털 서명만 적용하려면:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign**

이 구성의 결과로, 메일 메시지에 레이블을 적용하면 레이블의 분류에 더해 S/MIME 보호도 메일에 적용됩니다.

지정한 레이블이 Azure Portal에서 Rights Management 보호에 대해 구성된 경우, 오직 Outlook에서만 S/MIME 보호가 Rights Management 보호를 대체합니다. 레이블 지정을 지원하는 다른 모든 시나리오에서는 Rights Management 보호가 적용됩니다.

레이블이 Outlook에서만 표시되도록 하려면, **전달 금지**의 단일 사용자 정의 작업을 적용하도록 레이블을 구성합니다. 이는 [빠른 시작: 사용자가 중요한 정보가 포함된 이메일을 쉽게 보호하도록 레이블 구성](../quickstart-label-dnf-protectedemail.md)에 설명되어 있습니다.

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>필수 레이블을 사용하는 경우 문서에 대한 “나중에” 제거

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

**All documents and emails must have a label**(모든 문서와 메일에 레이블이 있어야 함)의 [정책 설정](../configure-policy-settings.md)을 사용할 경우 사용자가 Office 문서를 처음 저장할 때와 메일을 보낼 때 레이블을 선택할지 묻는 메시지가 사용자에게 표시됩니다. 문서의 경우 사용자는 **나중에**를 선택하여 일시적으로 레이블 선택 프롬프트를 무시하고 문서로 돌아갈 수 있습니다. 그러나 레이블을 지정해야 저장된 문서를 닫을 수 있습니다. 

이 설정을 구성하면 **나중에** 옵션이 제거되므로 문서가 처음 저장될 때 사용자가 레이블을 선택해야 합니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **PostponeMandatoryBeforeSave**

- Value: **False**

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>백그라운드에서 계속해서 실행되도록 분류 켜기

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 이 설정은 미리 보기로 제공되고 변경될 수 있습니다.

이 설정을 구성하면 다음과 같이 Azure Information Protection 클라이언트가 문서에 자동 및 권장 레이블을 적용하는 방식의 [기본 동작](../configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied)이 변경됩니다. 

- Word, Excel 및 PowerPoint의 경우 자동 분류가 백그라운드에서 지속적으로 실행됩니다.  

Outlook의 경우 변경되지 않습니다.

Azure Information Protection 클라이언트가 지정되는 조건 규칙에 대해 문서를 정기적으로 확인하는 경우 이 동작을 사용하면 SharePoint Online에 저장된 문서에 대한 자동 및 권장 분류 및 보호를 사용할 수 있습니다. 조건 규칙을 이미 실행했기 때문에 큰 파일도 더 신속하게 저장됩니다. 

조건 규칙은 사용자 형식으로 실시간으로 실행되지 않습니다. 대신, 문서를 수정할 때 주기적으로 백그라운드 작업으로 실행됩니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **RunPolicyInBackground**

- Value: **True**

## <a name="dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption"></a>PDF 암호화에 대해 ISO 표준을 사용하여 PDF 파일을 보호하지 않음

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

최신 버전의 Azure Information Protection 클라이언트가 PDF 파일을 보호하는 경우, 결과로 생성되는 파일 이름 확장명은 .pdf로 유지되고 PDF 암호화를 위한 ISO 표준을 준수합니다. 이 표준에 대한 자세한 내용은 [ISO 32000-1에서 파생되고](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) Adobe Systems incorporated에서 게시한 문서의 **7.6 암호화** 섹션을 참조하세요.

.ppdf 파일 이름 확장명을 사용하여 클라이언트가 보호된 PDF 파일을 보호하는 클라이언트의 이전 버전에서 동작으로 복귀해야 하는 경우 다음 문자열을 입력하여 다음과 같은 고급 설정을 사용하세요.

- 키: **EnablePDFv2Protection**

- Value: **False**

Azure Information Protection 스캐너에서 새 설정을 사용하려면 스캐너 서비스를 다시 시작해야 합니다. 또한 스캐너는 더 이상 기본적으로 PDF 문서를 보호하지 않습니다. EnablePDFv2Protection이 False로 설정된 경우 스캐너에서 PDF 문서를 보호하도록 하려면 [레지스트리를 편집](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner)해야 합니다.

새로운 PDF 암호화에 대한 자세한 내용은 블로그 게시물 [New support for PDF encryption with Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757)(Microsoft Information Protection을 사용한 새로운 PDF 암호화 지원)을 참조하세요.

### <a name="to-convert-existing-ppdf-files-to-protected-pdf-files"></a>기존의 .ppdf 파일을 보호된 .pdf 파일로 변환하려면

Azure Information Protection 클라이언트가 새 설정을 사용하여 클라이언트 정책을 다운로드한 경우 PowerShell 명령을 사용하여 기존 .ppdf 파일을 PDF 암호화에 ISO 표준을 사용하는 보호된 .pdf 파일로 변환할 수 있습니다. 

직접 보호하지 않는 파일에 다음 지침을 사용하려면 파일에서 보호를 제거하기 위한 [Rights Management 사용 권한](../configure-usage-rights.md)이 있거나 슈퍼 사용자여야 합니다. 슈퍼 사용자 기능을 사용하도록 설정하고 사용자 계정을 슈퍼 사용자로 구성하려면 [Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](../configure-super-users.md)을 참조하세요.

또한 직접 보호하지 않는 파일에 이러한 지침을 사용할 경우 [RMS 발급자](../configure-usage-rights.md#rights-management-issuer-and-rights-management-owner)가 됩니다. 이 시나리오에서 원래 문서를 보호한 사용자는 더 이상 문서를 추적하고 해지할 수 없습니다. 사용자가 보호된 PDF 문서를 추적 및 해지해야 할 경우 수동으로 제거한 후 파일 탐색기에서 마우스 오른쪽 단추를 클릭하여 레이블을 다시 적용하도록 요청합니다.

PowerShell 명령을 사용하여 기존의 .ppdf 파일을 PDF 암호화의 ISO 표준을 사용하는 보호된 .pdf 파일로 변환하려면

1. .ppdf 파일에 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)를 사용합니다. 예를 들면 다음과 같습니다.
    
        Get-AIPFileStatus -Path \\Finance\Projectx\sales.ppdf

2. 출력에서 다음 매개 변수 값을 기록해 둡니다.
    
    - **SubLabelId**의 값(GUID)(있는 경우). 이 값을 비워 두면 하위 레이블을 사용되지 않으므로 대신 **MainLabelId** 값을 기록해 둡니다.
    
    참고: **MainLabelId** 값도 없으면 파일에 레이블이 지정되지 않습니다. 이 경우 3 및 4단계의 명령 대신, [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) 명령 및 [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) 명령을 사용할 수 있습니다.
    
    - **RMSTemplateId** 값. 이 값이 **제한된 액세스**이면 사용자는 레이블에 대해 구성된 보호 설정이 아니라 사용자 지정 권한을 사용하여 파일을 보호한 것입니다. 계속하면 이러한 사용자 지정 권한은 레이블의 보호 설정으로 덮어쓰여집니다. 계속할지 또는 사용자에게 원래 사용자 지정 권한과 함께 레이블을 제거했다가 다시 적용할 것을 사용자(**RMSIssuer**에 표시되는 값)에게 요청할지를 결정합니다.

3. *RemoveLabel* 매개 변수와 함께 [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)을 사용하여 레이블을 제거합니다. [정책 설정](../configure-settings.md)으로
4. **Users must provide justification to set a lower classification label, remove a label, or remove protection**(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함)을 사용하는 경우 *Justification* 매개 변수와 근거를 지정해야 합니다. 예를 들면 다음과 같습니다. 
    
        Set-AIPFileLabel \\Finance\Projectx\sales.ppdf -RemoveLabel -JustificationMessage 'Removing .ppdf protection to replace with .pdf ISO standard'

4. 1단계에서 식별한 레이블의 값을 지정하여 원래 레이블을 다시 적용합니다. 예를 들면 다음과 같습니다.
    
        Set-AIPFileLabel \\Finance\Projectx\sales.pdf -LabelId d9f23ae3-1234-1234-1234-f515f824c57b

파일은 .pdf 파일 이름 확장명을 유지하지만 이전과 같이 분류되며, PDF 암호화의 ISO 표준을 사용하여 보호됩니다.

## <a name="support-for-files-protected-by-secure-islands"></a>Secure Islands에서 보호한 파일에 대한 지원

이 구성 옵션은 현재 미리 보기로 제공되며 변경될 예정입니다.

Secure Islands를 사용하여 문서를 보호한 경우 보호된 텍스트 및 그림 파일 및 이 보호의 결과로 일반적으로 보호된 파일이 있을 수 있습니다. 예를 들어 .ptxt, .pjpeg 또는 .pfile 파일이라는 이름 확장명의 파일입니다. 다음과 같이 레지스트리를 편집하면 Azure Information Protection은 다음과 같은 파일을 해독할 수 있습니다.


**EnableIQPFormats**의 다음 DWORD 값을 다음 레지스트리 경로에 추가하고 값 데이터를 **1**로 설정합니다.

- Windows 64비트 버전의 경우: HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\MSIP

- Windows 32비트 버전의 경우: HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\MSIP

이 레지스트리 편집의 결과로 다음과 같은 시나리오가 지원됩니다.

- Azure Information Protection 뷰어에서는 이러한 보호된 파일을 열 수 있습니다.

- Azure Information Protection 스캐너는 중요한 정보를 위해 이러한 파일을 검사할 수 있습니다.

- 파일 탐색기, PowerShell 및 Azure Information Protection 스캐너는 이러한 파일의 레이블을 지정할 수 있습니다. 그 결과, Azure Information Protection의 새 보호를 적용하거나 Secure Islands의 기존 보호를 제거하는 Azure Information Protection 레이블을 적용할 수 있습니다.

- [마이그레이션 클라이언트 사용자 지정 레이블 지정](#migrate-labels-from-secure-islands-and-other-labeling-solutions) 기능을 사용하여 이러한 보호된 파일의 Secure Islands 레이블을 Azure Information Protection 레이블로 자동으로 변환할 수 있습니다.

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Secure Islands 및 기타 레이블 지정 솔루션에서 레이블 마이그레이션

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 이 설정은 미리 보기로 제공되고 변경될 수 있습니다.

이 구성은 현재 PDF 암호화에 대해 ISO 표준을 사용하여 PDF 파일을 보호하는 새로운 기본 동작과 호환되지 않습니다. 이 시나리오에서 .ppdf 파일을 파일 탐색기, PowerShell 또는 스캐너에서 열 수 없습니다. 이를 해결하려면 [PDF 암호화에 대한 ISO 표준을 사용하지 않는](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption) 고급 클라이언트 설정을 사용합니다.

Secure Islands에서 레이블을 지정한 Office 문서 및 PDF 문서의 경우 직접 정의하는 매핑을 사용하여 이러한 문서의 레이블을 Azure Information Protection 레이블로 재지정할 수 있습니다. 또한 다른 솔루션의 레이블이 Office 문서에 있는 경우 이 방법으로 해당 레이블을 재사용할 수도 있습니다. 

> [!NOTE]
> Secure Islands로 보호되는 PDF 및 Office 문서 이외의 파일이 있는 경우 [앞의 섹션](#support-for-files-protected-by-secure-islands)에 설명된 대로 레지스트리를 편집한 후에 이러한 파일의 레이블을 재지정할 수 있습니다. 

이 구성 옵션의 결과로 새 Azure Information Protection 레이블이 Azure Information Protection 클라이언트에 의해 다음과 같이 적용됩니다.

- Office 문서의 경우: 데스크톱 앱에서 문서를 열면 새 Azure Information Protection 레이블이 설정된 대로 표시되며 문서를 저장할 때 적용됩니다.

- 파일 탐색기의 경우: Azure Information Protection 대화 상자에서 새 Azure Information Protection 레이블이 설정된 대로 표시되며 사용자가 **적용**을 선택하면 적용됩니다. 사용자 **취소**를 선택하면 새 레이블이 적용되지 않습니다.

- PowerShell의 경우: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)은 새 Azure Information Protection 레이블을 적용합니다. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)는 다른 방법으로 설정되기 전까지는 새 Azure Information Protection 레이블을 표시하지 않습니다.

- Azure Information Protection 스캐너: 검색에서 새 Azure Information Protection 레이블이 설정되는 시기를 보고하며 적용 모드를 사용하여 이 레이블을 적용할 수 있습니다.

이 구성을 사용하려면 이전 레이블에 매핑할 각 Azure Information Protection 레이블에 대해 **LabelbyCustomProperty**라는 고급 클라이언트 설정을 지정해야 합니다. 그런 다음 각 항목의 값을 다음 구문을 사용하여 설정합니다.

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Azure Portal에서 Azure Information Protection 정책을 보거나 구성하는 경우 레이블 ID 값이 **레이블** 블레이드에 표시됩니다. 하위 레이블을 지정하려면 상위 레이블이 같은 범위 또는 전역 정책에 있어야 합니다.

원하는 마이그레이션 규칙 이름을 지정합니다. 이전 레이블 지정 솔루션의 레이블 하나 이상이 Azure Information Protection 레이블에 매핑되는 방식을 식별하는 데 도움이 되는 설명이 포함된 이름을 사용합니다. 이 이름은 스캐너 보고서와 이벤트 뷰어에 표시됩니다. 

이 설정은 이전 레이블이 적용될 수 있는 시각적 표시를 제거하지 않습니다. 헤더 및 바닥글을 제거하려면 다음 섹션인 [다른 레이블 지정 솔루션에서 헤더 및 바닥글 제거](#remove-headers-and-footers-from-other-labeling-solutions)를 참조하세요.

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>예제 1: 동일한 레이블 이름의 일대일 매핑

Secure Islands 레이블이 “기밀”인 문서는 Azure Information Protection에서 레이블이 “기밀”로 재지정되어야 합니다.

이 예에서는 다음과 같습니다.

- Azure Information Protection 레이블 **기밀**의 레이블 ID는 1ace2cc3-14bc-4142-9125-bf946a70542c입니다. 

- Secure Islands 레이블은 **Classification**이라는 사용자 지정 속성에 저장됩니다.

고급 클라이언트 설정은 다음과 같습니다.

    
|이름|값|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c,"Secure Islands label is Confidential",Classification,Confidential|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>예제 2: 다른 레이블 이름의 일대일 매핑

Secure Islands에서 레이블이 “중요”로 지정된 문서는 Azure Information Protection에서 레이블이 “극비”로 재지정되어야 합니다.

이 예에서는 다음과 같습니다.

- Azure Information Protection 레이블 **극비**의 레이블 ID는 3e9df74d-3168-48af-8b11-037e3021813f입니다.

- Secure Islands 레이블은 **Classification**이라는 사용자 지정 속성에 저장됩니다.

고급 클라이언트 설정은 다음과 같습니다.

    
|이름|값|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-3168-48af-8b11-037e3021813f,"Secure Islands label is Sensitive",Classification,Sensitive|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>예제 3: 레이블 이름의 다대일 매핑

“내부”라는 단어를 포함하는 Secure Islands 레이블은 두 가지이며 이러한 Secure Islands 레이블 중 하나가 있는 문서는 Azure Information Protection에서 레이블을 “일반”으로 재지정할 수 있습니다.

이 예에서는 다음과 같습니다.

- Azure Information Protection 레이블 **일반**의 레이블 ID는 2beb8fe7-8293-444c-9768-7fdc6f75014d입니다.

- Secure Islands 레이블은 **Classification**이라는 사용자 지정 속성에 저장됩니다.

고급 클라이언트 설정은 다음과 같습니다.

    
|이름|값|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d,"Secure Islands label contains Internal",Classification,.\*Internal.\*|


## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>다른 레이블 지정 솔루션에서 헤더 및 바닥글 제거

이 구성에서는 Azure Portal에서 구성해야 하는 여러 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 이러한 설정은 미리 보기로 제공되고 변경될 수 있습니다.

이 설정을 통해 다른 레이블 지정 솔루션에서 해당 시각적 표시가 적용된 경우 문서에서 텍스트 기반 헤더 또는 바닥글을 제거하거나 바꿀 수 있습니다. 예를 들어, 이전 바닥글에는 이제 새 레이블 이름 및 고유한 바닥글이 있는 Azure Information Protection으로 마이그레이션한 이전 레이블의 이름이 포함됩니다.

클라이언트가 해당 정책에서 이 구성을 가져오면 Office 앱에서 문서를 열고 Azure Information Protection 레이블을 문서에 적용할 때 이전 헤더 및 바닥글을 제거하거나 대체합니다.

이 구성은 Outlook에 지원되지 않습니다. Word, Excel 및 PowerPoint에서 사용하는 경우 이러한 앱의 성능에 부정적인 영향을 줄 수 있습니다. 구성을 통해 애플리케이션별로 설정을 정의할 수 있습니다. 예를 들어, Word 문서의 헤더 및 바닥글에 있는 텍스트를 검색하지만 Excel 스프레드시트 또는 PowerPoint 프레젠테이션은 검색하지 않습니다.

패턴 일치가 성능에 영향을 주기 때문에 Office 애플리케이션 형식(**W**ord, **E**xcel, **P**owerPoint)을 검색되어야 하는 것으로 제한하는 것이 좋습니다.

- 키: **RemoveExternalContentMarkingInApp**

- Value: \<**Office 애플리케이션 형식 WXP**> 

예:

- Word 문서만을 검색하려면 **W**를 지정합니다.

- Word 문서 및 PowerPoint 프레젠테이션을 검색하려면 **WP**를 지정합니다.

그런 다음, 하나 이상의 고급 클라이언트 설정인 **ExternalContentMarkingToRemove**이 헤더 또는 바닥글의 내용 및 제거하거나 대체하는 방법을 지정해야 합니다.

### <a name="how-to-configure-externalcontentmarkingtoremove"></a>ExternalContentMarkingToRemove를 구성하는 방법

**ExternalContentMarkingToRemove** 키에 대한 문자열 값을 지정하는 경우 정규식을 사용하는 세 가지 옵션이 있습니다.

- 헤더 또는 바닥글의 모든 항목을 제거하는 부분 일치 항목입니다.
    
    예: 헤더 또는 바닥글에 **TEXT TO REMOVE**라는 문자열이 포함됩니다. 이러한 헤더 또는 바닥글을 완전히 제거하려고 합니다. `*TEXT*` 값을 지정합니다.

- 헤더 또는 바닥글에서 특정 단어를 제거하는 전체 일치입니다.
    
    예: 헤더 또는 바닥글에 **TEXT TO REMOVE**라는 문자열이 포함됩니다. **TEXT**라는 단어를 제거하려고 합니다. 그러면 헤더 또는 바닥글 문자열을 **TO REMOVE**로 유지합니다. `TEXT ` 값을 지정합니다.

- 헤더 또는 바닥글의 모든 항목을 제거하는 전체 일치 항목입니다.
    
    예: 헤더 또는 바닥글에 **TEXT TO REMOVE**라는 문자열이 포함됩니다. 이 문자열이 정확하게 포함된 헤더 또는 바닥글을 제거하려고 합니다. `^TEXT TO REMOVE$` 값을 지정합니다.
    

지정한 문자열에 대한 패턴 일치는 대/소문자를 구분합니다. 최대 문자열 길이는 255자입니다.

일부 문서에 보이지 않는 문자 또는 다른 종류의 공백이나 탭이 포함될 수 있으므로 구 또는 문장에 지정한 문자열은 검색되지 않을 수 있습니다. 가능하면 값에 대해 구별되는 단일 단어를 지정하고 프로덕션에 배포하기 전에 결과를 테스트해야 합니다.

- 키: **ExternalContentMarkingToRemove**

- 값: \<**일치할 문자열, 정규식으로 정의됨**> 

#### <a name="multiline-headers-or-footers"></a>여러 줄 헤더 또는 바닥글

헤더 또는 바닥글 텍스트가 단일 줄보다 크면 각 줄에 대한 키와 값을 만듭니다. 예를 들어, 다음 두 줄을 포함한 바닥글이 있습니다.

**해당 파일이 기밀로 분류됨**

**수동으로 레이블이 적용됨**

이 여러 줄 바닥글을 제거하려면 다음 두 항목을 만듭니다.

- 키 1: **ExternalContentMarkingToRemove**

- 키 값 1: **\*기밀***

- 키 2: **ExternalContentMarkingToRemove**

- 키 값 2: **\*레이블 적용됨*** 

#### <a name="optimization-for-powerpoint"></a>PowerPoint에 대한 최적화

PowerPoint의 바닥글이 도형으로 구현됩니다. 지정한 텍스트를 포함하지만 헤더나 바닥글이 아닌 도형을 제거하지 않도록 방지하려면 **PowerPointShapeNameToRemove**라는 추가 고급 클라이언트 설정을 사용합니다. 리소스를 많이 사용하는 프로세스인 모든 도형에 있는 텍스트를 확인하지 않으려면 이 설정을 사용하는 것이 좋습니다.

이 추가 고급 클라이언트 설정을 지정하지 않고 PowerPoint가 **RemoveExternalContentMarkingInApp** 키 값에 포함된 경우  **ExternalContentMarkingToRemove** 값에서 지정한 텍스트에 대한 모든 도형을 확인합니다. 

헤더 또는 바닥글을 사용하는 도형 이름을 찾으려면:

1. PowerPoint에서 다음과 같은 **선택** 창을 표시합니다. **형식** 탭 > **정렬** 그룹 > **선택 창**.

2. 헤더 또는 바닥글을 포함하는 슬라이드에서 도형을 선택합니다. 이제 **선택 영역** 창에서 선택한 도형 이름을 강조 표시합니다.

도형 이름을 사용하여 **PowerPointShapeNameToRemove** 키에 대한 문자열 값을 지정합니다. 

예: 셰이프 이름은 **fc**입니다. 이 이름을 가진 도형을 제거하려면 `fc` 값을 지정합니다.

- 키: **PowerPointShapeNameToRemove**

- Value: \<**PowerPoint 도형 이름**> 

둘 이상의 PowerPoint 도형을 제거할 경우 도형을 제거할 만큼 **PowerPointShapeNameToRemove** 키를 만듭니다. 각 항목에 대해 제거할 도형의 이름을 지정합니다.

기본적으로 헤더 및 바닥글에 대한 마스터 슬라이드만을 확인합니다. 리소스를 훨씬 더 많이 사용하는 모든 슬라이드로 이 검색을 확장하려면 **RemoveExternalContentMarkingInAllSlides**라는 추가 고급 클라이언트 설정을 사용합니다.

- 키: **RemoveExternalContentMarkingInAllSlides**

- Value: **True**

## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>기존 사용자 지정 속성을 사용하여 Office 문서에 레이블을 지정합니다.

> [!NOTE]
> 이 구성 및 [Secure Islands 및 기타 레이블 지정 솔루션에서 레이블을 마이그레이션](#migrate-labels-from-secure-islands-and-other-labeling-solutions)하는 구성을 사용하는 경우 레이블 지정 마이그레이션 설정이 우선합니다. 

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

이 설정을 구성할 때 레이블 이름 중 하나와 일치하는 값이 있는 기존 사용자 지정 속성이 있으면 Office 문서를 분류하고 선택적으로 보호할 수 있습니다. 이 사용자 지정 속성은 다른 분류 솔루션에서 설정하거나 SharePoint에서 속성으로 설정할 수 있습니다.

이 구성으로 인해 사용자가 Office 응용 프로그램에서 Azure Information Protection 레이블이 없는 문서를 열고 저장하면 해당 속성 값과 일치하는 레이블이 해당 문서에 지정됩니다. 

이 구성을 사용하려면 함께 작동하는 두 가지 고급 설정을 지정해야 합니다. 첫 번째 설정은 **SyncPropertyName**이며, 다른 분류 솔루션에서 설정한 사용자 지정 속성 이름이거나 SharePoint에서 설정한 속성입니다. 두 번째 설정은 **SyncPropertyState**이며, OneWay로 설정해야 합니다.

이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키 1: **SyncPropertyName**

- 키 1 값: \<**속성 이름**> 

- 키 2: **SyncPropertyState**

- 키 2 값: **OneWay**

이러한 키와 해당 값은 하나의 사용자 지정 속성에만 사용하세요.

예를 들어 **공용**, **일반** 및 **극비 모든 직원** 값을 포함할 수 있는 **분류**라는 SharePoint 열이 있습니다. 문서는 SharePoint에 저장되며 분류 속성의 설정된 값으로 **공용**, **일반** 또는 **극비 모든 직원**을 포함합니다.

이러한 분류 값 중 하나를 사용하여 Office 문서에 레이블을 지정하려면 **SyncPropertyName**을 **분류**로 설정하고 **SyncPropertyState**를 **OneWay**로 설정합니다. 

이제 사용자가 이러한 Office 문서 중 하나를 열고 저장할 때 Azure Information Protection 정책에 이러한 이름의 레이블이 있으면 **공용**, **일반** 또는 **극비 \ 모든 직원**이라는 레이블이 지정됩니다. 이러한 이름의 레이블이 없으면 문서에 레이블이 지정되지 않습니다.

## <a name="disable-the-low-integrity-level-for-the-scanner"></a>스캐너에 대해 낮은 무결성 수준 사용 안 함

이 구성에서는 Azure Portal에서 구성해야 하는 [고급 클라이언트 설정](#how-to-configure-advanced-client-configuration-settings-in-the-portal)을 사용합니다. 

기본적으로 Azure Information Protection 스캐너는 낮은 무결성 수준에서 실행됩니다. 이 설정은 더 높은 보안 격리를 제공하지만 성능이 저하됩니다. 이 설정이 스캐너를 실행하는 컴퓨터를 보호하는 데 도움이 되므로 권한이 있는 계정(예: 로컬 관리자 계정)으로 스캐너를 실행하는 경우 낮은 무결성 수준이 적합합니다.

그러나 스캐너를 실행하는 서비스 계정에 [스캐너 필수 구성 요소](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner)에 설명된 권한만 있는 경우 낮은 무결성 수준은 필요하지 않고 성능에 부정적인 영향을 주기 때문에 권장되지 않습니다. 

Windows 무결성 수준에 대한 자세한 내용은 [Windows 무결성 메커니즘이란?](https://msdn.microsoft.com/library/bb625957.aspx)을 참조하세요.

스캐너가 Windows에서 자동으로 할당된 무결성 수준으로 실행되도록(표준 사용자 계정은 중간 무결성 수준으로 실행됨) 이 고급 설정을 구성하려면 다음 문자열을 입력합니다.

- 키: **ProcessUsingLowIntegrity**

- Value: **False**


## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>모바일 디바이스 레이블 지정 솔루션을 위해 Exchange 메시지 분류와 통합

웹용 Outlook에서는 아직 기본적으로 Azure Information Protection 분류 및 보호를 지원하지 않지만, Exchange 메시지 분류를 사용하여 웹용 Outlook을 사용하는 모바일 사용자로 Azure Information Protection 레이블을 확장할 수 있습니다. Outlook Mobile은 Exchange 메시지 분류를 지원하지 않습니다.

이 솔루션을 활용하려면 다음을 수행합니다. 

1. [New-MessageClassification](https://technet.microsoft.com/library/bb124400) Exchange PowerShell cmdlet을 사용하여 Azure Information Protection 정책의 레이블 이름에 매핑되는 Name 속성을 포함하는 메시지 분류를 만듭니다. 

2. 각 레이블에 대해 Exchange 이메일 흐름 규칙을 만듭니다. 구성한 분류가 메시지 속성에 포함될 때 해당 규칙을 적용하고 메시지 속성을 수정하여 메시지 헤더를 설정합니다. 

     메시지 헤더에서는 Azure Information Protection 레이블을 사용하여 분류하고 보낸 메일의 인터넷 헤더를 검사하면 지정할 정보를 확인할 수 있습니다. **msip_labels** 헤더와 바로 뒤에서 세미콜론까지의 문자열(세미콜론도 포함)을 찾습니다. 예를 들면 다음과 같습니다.
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    그런 다음 규칙의 메시지 헤더에 대해 **msip_labels**를 헤더로, 이 문자열의 나머지 부분을 헤더 값으로 지정합니다. 예를 들면 다음과 같습니다.
    
    ![특정 Azure Information Protection 레이블에 대한 메시지 헤더를 설정하는 Exchange Online 메일 흐름 규칙 예제](../media/exchange-rule-for-message-header.png)
    
    참고: 레이블이 하위 레이블인 경우 헤더 값의 하위 레이블 앞에 부모 레이블도 같은 형식을 사용하여 지정해야 합니다. 예를 들어 하위 레이블의 GUID가 27efdf94-80a0-4d02-b88c-b615c12d69a9이면 값은 다음과 같을 수 있습니다. `MSIP_Label_ab70158b-bdcc-42a3-8493-2a80736e9cbd_Enabled=True;MSIP_Label_27efdf94-80a0-4d02-b88c-b615c12d69a9_Enabled=True;`

이 구성을 테스트하기 전에 메일 흐름 규칙을 만들거나 편집할 때 지연이 발생하는 경우가 종종 있습니다(예: 1시간 대기). 이제 규칙이 적용되면 사용자가 Exchange ActiveSync IRM을 지원하는 모바일 디바이스 클라이언트 또는 웹용 Outlook을 사용할 때 다음과 같은 이벤트가 발생합니다. 

- 사용자가 Exchange 메시지 분류를 선택하고 전자 메일을 보냅니다.

- Exchange 규칙이 Exchange 분류를 검색한 다음 그에 따라 메시지 헤더를 수정하여 Azure Information Protection 분류를 추가합니다.

- Azure Information Protection 클라이언트가 설치된 경우 내부 받는 사람이 Outlook에서 메일을 볼 때 할당된 Azure Information Protection 레이블이 표시됩니다. 

Azure Information Protection 레이블이 보호를 적용하는 경우 이 보호를 규칙 구성에 추가합니다. 메시지 보안을 수정하는 옵션을 선택하고 권한 보호를 적용한 다음, RMS 템플릿 또는 전달 금지 옵션을 선택합니다.

또한 역방향 매핑을 수행하도록 메일 흐름 규칙을 구성할 수 있습니다. Azure Information Protection 레이블이 검색되면 해당 Exchange 메시지 분류를 설정합니다.

- 각 Azure Information Protection 레이블의 경우: **msip_labels** 헤더에 레이블의 이름(예: **General**)이 포함될 때 적용되는 이메일 흐름 규칙을 만들고 이 레이블에 매핑되는 메시지 분류를 적용합니다.


## <a name="next-steps"></a>다음 단계
Azure Information Protection 클라이언트를 사용자 지정했으므로 다음 리소스에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)


