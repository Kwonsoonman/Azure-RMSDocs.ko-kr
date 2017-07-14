---
title: "Azure Information Protection 클라이언트에 대한 사용자 지정 구성"
description: "Windows용 Azure Information Protection 클라이언트의 사용자 지정에 대한 정보"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6ab5465db1527e6236d2dca466936c36b260f03d
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2017
---
# Azure Information Protection 클라이언트에 대한 사용자 지정 구성
<a id="custom-configurations-for-the-azure-information-protection-client" class="xliff"></a>

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Azure Information Protection 클라이언트를 관리할 때 특정 시나리오 또는 사용자의 하위 집합에 대해 필요할 수 있는 고급 구성을 수행할 경우 다음 정보를 사용합니다. 

## AD RMS 전용 컴퓨터의 로그인 프롬프트 방지
<a id="prevent-sign-in-prompts-for-ad-rms-only-computers" class="xliff"></a>

기본적으로 Azure Information Protection 클라이언트는 자동으로 Azure Information Protection 서비스에 연결하려 합니다. AD RMS와만 통신하는 컴퓨터의 경우는 그 때문에 불필요하게 사용자에게 로그인 프롬프트가 표시될 수 있습니다. 레지스트리를 편집하면 이 로그인 프롬프트를 방지할 수 있습니다.

다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

이 설정에 관계 없이 Azure Information Protection 클라이언트는 표준 [RMS 서비스 검색 프로세스](../rms-client/client-deployment-notes.md#rms-service-discovery)에 따라 AD RMS 클러스터를 찾습니다.

## 다른 사용자로 로그인
<a id="sign-in-as-a-different-user" class="xliff"></a>

프로덕션 환경에서는 Azure Information Protection 클라이언트를 사용 중에 일반적으로 다른 사용자로 로그인할 필요가 없습니다. 그러나 여러 테넌트가 있는 경우에는 관리자로서 그렇게 해야 할 수 있습니다. 예를 들어 조직에서 사용하는 Office 365 또는 Azure 테넌트 외에 테스트 테넌트가 있을 수 있습니다.

**Microsoft Azure Information Protection** 대화 상자를 사용하여 현재 로그인한 계정을 확인할 수 있습니다. Office 응용 프로그램을 열고 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 의견**을 클릭합니다. 계정 이름은 **클라이언트 상태** 섹션에 표시됩니다.

특히 관리자 계정을 사용하고 있는 경우 표시된 로그인 계정의 도메인 이름을 확인해야 합니다. 예를 들어 두 개의 다른 테넌트에 "admin" 계정이 있는 경우 로그인한 계정 이름은 올바르지만 도메인은 잘못되었음을 모르기 쉽습니다. 이로 인해 Azure Information Protection 정책을 다운로드하지 못하거나 예상한 레이블 또는 동작이 표시되지 않을 수 있습니다.

다른 사용자로 로그인하려면 다음과 같이 합니다.

1. 레지스트리 편집기를 사용하여 **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**로 이동하고 **TokenCache** 값과 연결된 값 데이터를 삭제합니다.

2. 열려 있는 Office 응용 프로그램을 다시 시작하고 다른 사용자 계정으로 로그인합니다. Office 응용 프로그램에서 Azure Information Protection 서비스에 로그인하라는 메시지가 표시되지 않는 경우 **Microsoft Azure Information Protection** 대화 상자로 돌아와 업데이트된 **클라이언트 상태** 섹션에서 **로그인**을 클릭합니다.

추가 필수 구성 요소:

- Single Sign-On을 사용할 경우 Windows에서 로그아웃하고 레지스트리를 편집한 후 다른 사용자 계정으로 로그인해야 합니다. Azure Information Protection 클라이언트에서는 현재 로그인한 사용자 계정을 사용하여 자동으로 인증합니다.

- Azure 권한 관리 서비스에 대한 환경을 다시 초기화(부트스트래핑이라고도 함)하려는 경우 [RMS 분석기 도구](https://www.microsoft.com/en-us/download/details.aspx?id=46437)의 **재설정** 옵션을 사용할 수 있습니다.

- 현재 다운로드한 Azure Information Protection 정책을 삭제하려면 **%localappdata%\Microsoft\MSIP** 폴더에서 **Policy.msip** 파일을 삭제합니다.

## Windows 파일 탐색기에서 [분류 및 보호] 메뉴 옵션 숨기기
<a id="hide-the-classify-and-protect-menu-option-in-windows-file-explorer" class="xliff"></a>

Azure Information Protection 클라이언트 1.3.0.0 이상 버전을 사용하는 경우 레지스트리를 편집하여 이 고급 구성을 구성할 수 있습니다. 

다음 DWORD 값 이름(모든 값 데이터 포함)을 만듭니다.

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## 연결이 끊어진 컴퓨터에 대한 지원
<a id="support-for-disconnected-computers" class="xliff"></a>

기본적으로 Azure Information Protection 클라이언트는 자동으로 Azure Information Protection 서비스에 연결하여 최신Azure Information Protection 정책을 다운로드합니다. 일정 기간 동안 인터넷에 연결할 수 없는 컴퓨터를 사용하는 경우 레지스트리를 편집하여 클라이언트가 서비스에 연결하지 못하도록 할 수 있습니다. 다음 값 이름을 찾아서 값 데이터를 **0**으로 설정합니다.

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

클라이언트의 **%localappdata%\Microsoft\MSIP** 폴더에 **Policy.msip**라는 이름의 유효한 정책 파일이 있는지 확인합니다. 필요한 경우 Azure 포털에서 정책을 내보낼 수 있으며 클라이언트 컴퓨터에 내보내기된 파일을 복사할 수 있습니다. 또한 이러한 방법을 통해 오래된 정책 파일을 게시된 최신 정책으로 바꿀 수 있습니다.

## 모바일 장치 레이블 지정 솔루션을 위해 Exchange 메시지 분류와 통합
<a id="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution" class="xliff"></a>

웹용 Outlook에서는 아직 기본적으로 Azure Information Protection 분류 및 보호를 지원하지 않지만 Exchange 메시지 분류를 사용하여 Azure Information Protection 레이블을 모바일 사용자로 확장할 수 있습니다.

이 솔루션을 활용하려면 다음을 수행합니다. 

1. [New-MessageClassification](https://technet.microsoft.com/library/bb124400) Exchange PowerShell cmdlet을 사용하여 Azure Information Protection 정책의 레이블 이름에 매핑되는 Name 속성을 포함하는 메시지 분류를 만듭니다. 

2. 각 레이블에 대해 Exchange 전송 규칙을 만든 다음 구성된 분류가 메시지 속성에 포함될 때 해당 규칙을 적용하고 메시지 속성을 수정하여 메시지 헤더를 설정합니다. 

    메시지 헤더에서는 Azure Information Protection 레이블을 사용하여 분류하고 보낸 메일의 인터넷 헤더를 검사하면 지정할 정보를 확인할 수 있습니다. **msip_labels** 헤더와 바로 뒤에서 세미콜론까지의 문자열(세미콜론도 포함)을 찾습니다. 이전 예를 사용하면 다음과 같습니다.
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    그런 다음 규칙의 메시지 헤더에 대해 **msip_labels**를 헤더로, 이 문자열의 나머지 부분을 헤더 값으로 지정합니다. 예를 들면 다음과 같습니다.
    
    ![특정 Azure Information Protection 레이블에 대한 메시지 헤더를 설정하는 Exchange Online 전송 규칙 예제](../media/exchange-rule-for-message-header.png)

이를 테스트하기 전에 전송 규칙을 만들거나 편집할 때 지연이 발생하는 경우가 종종 있습니다(예: 1시간 대기). 규칙이 적용되면 사용자가 Rights Management 보호를 지원하는 모바일 장치 클라이언트 또는 웹용 Outlook을 사용할 때 다음과 같은 과정이 진행됩니다. 

- 사용자가 Exchange 메시지 분류를 선택하고 전자 메일을 보냅니다.

- Exchange 규칙이 Exchange 분류를 검색한 다음 그에 따라 메시지 헤더를 수정하여 Azure Information Protection 분류를 추가합니다.

- Azure Information Protection 클라이언트를 실행 중인 받는 사람이 Outlook에서 전자 메일을 볼 때 할당된 Azure Information Protection 레이블과 그에 해당하는 전자 메일 머리글, 바닥글 또는 워터마크가 표시됩니다. 

Azure Information Protection 레이블이 권한 관리 보호를 적용하는 경우에는 메시지 보안을 수정하는 옵션을 선택하여 규칙 구성에 권한 관리 보호를 추가하고, 권한 보호를 적용한 후에 RMS 템플릿 또는 전달 금지 옵션을 선택합니다.

역방향 매핑을 수행하는 전송 규칙을 구성할 수도 있습니다. Azure Information Protection 레이블이 검색되면 해당 Exchange 메시지 분류를 설정합니다. 이렇게 하려면 다음을 수행합니다.

- 각 Azure Information Protection 레이블에 대해 **msip_labels** 헤더에 레이블의 이름(예: **General**)이 포함될 때 적용되는 전송 규칙을 만들고 이 레이블에 매핑되는 메시지 분류를 적용합니다.


## 다음 단계
<a id="next-steps" class="xliff"></a>
Azure Information Protection 클라이언트를 사용자 지정했으므로 다음에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
