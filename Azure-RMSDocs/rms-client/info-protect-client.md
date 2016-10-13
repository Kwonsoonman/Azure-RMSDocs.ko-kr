---
title: "Azure Information Protection 클라이언트 설치 | Azure Information Protection"
description: "문서와 전자 메일용 분류 레이블을 선택할 수 있도록 Office 응용 프로그램에 Information Protection 표시줄을 추가하는 클라이언트를 설치하는 지침을 제공합니다."
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 003e76733657bb97c5447e2cdc44049d111d33fa
ms.openlocfilehash: 2892b091e300b0ef15ca09524d233474bd5de193


---

# Azure Information Protection 클라이언트 설치

>*적용 대상: Azure Information Protection*

Azure Information Protection을 사용하여 문서 및 전자 메일 메시지를 분류하려면 먼저 Azure Information Protection 클라이언트를 설치해야 합니다. 이 설치에서는 Office 응용 프로그램(Word, Excel, PowerPoint, Outlook)에 조직의 분류 레이블을 표시하고, **홈** 탭(Word, Excel, PowerPoint)에 **보호**라는 단추가 있는 **보호** 그룹을 표시하는 Information Protection 표시줄을 추가합니다.

다음 그림에서는 이 Information Protection 표시줄과 [기본 정책](../deploy-use/configure-policy-default.md)의 레이블을 보여 줍니다.

![기본 정책이 적용된 Azure Information Protection 표시줄](../media/info-protect-bar-default.png)

[Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 Azure Information Protection 클라이언트를 다운로드합니다.

클라이언트를 설치하기 전에 Information Protection 클라이언트에 필요한 운영 체제 버전 및 응용 프로그램이 있는지 확인합니다([Azure Information Protection에 대한 요구 사항](../get-started/requirements-azure-rms.md)).


## Azure Information Protection 클라이언트를 수동으로 설치하려면

1. [클라이언트를 다운로드](https://www.microsoft.com/en-us/download/details.aspx?id=53018)한 후 **AzInfoProtection.exe**를 실행하고 메시지의 지시에 따라 클라이언트를 설치합니다. 이 설치에는 로컬 관리 권한이 필요합니다.

    Office 365 또는 Azure Active Directory에 연결할 수 없지만 데모용으로 로컬 정책을 사용하여 Azure Information Protection의 클라이언트 쪽을 확인해 보려면 데모 정책을 설치하는 옵션을 선택합니다. 클라이언트에서 Azure Information Protection 서비스에 연결하면 이 데모 정책이 조직의 Azure Information Protection 정책으로 바뀝니다. 

2. Azure Information Protection 클라이언트 사용을 시작하려면: 컴퓨터에서 Office 2010을 실행하는 경우 컴퓨터를 다시 시작합니다. 다른 Office 버전의 경우 Office 응용 프로그램을 다시 시작합니다.

## 사용자를 위해 Azure Information Protection 클라이언트를 설치하려면

명령줄 옵션을 사용하여 Azure Information Protection 클라이언트 설치를 스크립트로 작성하고 자동화할 수 있습니다. 설치 옵션을 확인하려면 `AzInfoProtection.exe /help`를 실행합니다.

예를 들어 클라이언트를 자동으로 설치하려면 다음 명령을 실행합니다. `AzInfoProtection.exe /passive | quiet`

## Azure Information Protection 클라이언트를 제거하려면

다음 옵션 중 하나를 사용할 수 있습니다.

- 제어판을 사용하여 프로그램을 제거합니다. **Microsoft Azure Information Protection** > **제거**를 클릭합니다.

- **AzInfoProtection.exe**를 다시 실행하고 **설치 수정** 페이지에서 **제거**를 클릭합니다. 

- 실행 `AzInfoProtection.exe /uninstall`


## 설치 또는 연결 상태를 확인하거나 문제를 보고하려면

1. Office 응용 프로그램을 열고 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다.

2. **Microsoft Azure Information Protection** 대화 상자에서 다음을 확인합니다.

    - 클라이언트에서 조직의 Azure Information Protection 서비스에 마지막으로 연결한 시점을 식별하는 **마지막 연결** 값. 클라이언트는 서비스에 연결할 때 현재 정책이 변경된 것을 발견한 경우 최신 정책을 자동으로 다운로드합니다. 표시된 시간 이후에 정책을 변경한 경우 Office 응용 프로그램을 닫았다가 다시 엽니다.

    - Azure Information Protection에 인증하는 데 사용되는 계정을 식별하는 표시된 사용자 이름. 이 사용자 이름은 Office 365 또는 Azure Active Directory에 사용하는 계정과 일치해야 합니다.

    - Azure Information Protection 클라이언트의 버전.

    - 조사하기 위해 Information Protection 팀에 보낼 수 있는 전자 메일 메시지에 클라이언트 로그를 자동으로 첨부하는 데 사용할 수 있는 **사용자 의견 보내기** 링크.

## Azure Information Protection 표시줄을 위한 바로 가기 키

바로 가기 키를 사용하여 Azure Information Protection 표시줄에 액세스하려면 다음과 같은 키 조합을 사용합니다.

- **Ctrl** + **Shift** + **~**를 누릅니다. 

그 다음, 레이블과 표시줄에 있는 다른 컨트롤 (**레이블 숨기기** 아이콘 및 **레이블 제거** 아이콘)을 선택하려면 Tab 키를 사용하고 Enter 키를 사용하여 선택합니다.


## 파일 위치

클라이언트 파일:   

- 64비트 운영 체제: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- 32비트 운영 체제: **\Program Files\Microsoft Azure Information Protection**

클라이언트 로그 파일 및 현재 설치된 정책 파일:

- 64비트 및 32비트 운영 체제: **%localappdata%\Microsoft\MSIP**


## 다음 단계

Information Protection 표시줄의 레이블을 변경하려면 Azure Information Protection 정책을 구성해야 합니다. 자세한 내용은 [Azure Information Protection 정책 구성](../deploy-use/configure-policy.md)을 참조하세요.

기본 정책을 사용자 지정하는 방법에 대한 예제를 보려면 Office 응용 프로그램에서 결과 동작을 확인하고 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 참조하세요. 



<!--HONumber=Sep16_HO4-->


