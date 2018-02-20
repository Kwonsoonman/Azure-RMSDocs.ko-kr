---
title: "Azure Information Protection의 보호 전용 모드"
description: "보호 전용 모드에서 Azure Information Protection 클라이언트를 실행하는 사용자를 위한 정보입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/14/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 201415526b57d691d999ddba6af2451df4d36de4
ms.sourcegitcommit: 2733b1df2ebdda02b60d9471db29e545552f99ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2018
---
# <a name="user-guide-protection-only-mode-for-the-azure-information-protection-client"></a>사용자 가이드: Azure Information Protection 클라이언트에 대한 보호 전용 모드

Azure Information Protection 클라이언트에 문서 및 메일을 분류하는 레이블이 없는 경우 **보호 전용** 모드에서 실행됩니다. 예를 들어 이 모드에서 Windows 파일 탐색기를 사용하는 경우 마우스 오른쪽 단추로 **분류 및 보호**를 클릭하면 다음이 표시될 수 있습니다.

![보호 전용 모드](../media/protection-only-mode.png)

보호 전용 모드는 다음 시나리오에서 실행됩니다.

- 조직에 분류 및 레이블 지정 기능이 포함되는 Azure Information Protection에 대한 구독이 없으나 Azure Rights Management 서비스를 사용하는 데이터 보호를 포함하는 Office 365에 대한 구독이 있습니다. 
    
    - Azure Information Protection 클라이언트를 사용하여 파일을 보호하고 보호된 파일을 볼 수 있습니다. 문서 및 메일을 분류하거나 레이블을 지정할 수 없습니다.

- 조직에 다음 사용자 하위 집합 전용의 Azure Information Protection 구독이 있습니다.
    
    - 이 혼합 구독의 경우 사용자 하위 집합만 분류 및 레이블 지정 기능을 사용할 수 있도록 하는 것은 관리자의 책임입니다. 나머지 사용자는 보호 전용 모드에서 Azure Information Protection 클라이언트를 실행해야 합니다. 

- 조직은 Azure Information Protection에 대한 구독을 보유하지만 어떤 레이블도 구성되어 있지 않습니다.
    
    - 이는 글로벌 정책의 모든 레이블이 비활성화되고 사용자의 계정이 범위 지정 정책에 추가되지 않은 경우에 발생할 수 있습니다. 이는 IT 부서에서 Azure Information Protection을 롤아웃했지만 문서 및 이메일을 분류하기 위한 레이블을 아직 제공하지 않았기 때문일 수 있습니다. 당분간은 Azure Information Protection 클라이언트를 사용하여 파일을 보호하고 보호된 파일을 볼 수 있습니다.

- 조직에 Azure Information Protection에 대한 구독이 있으나 Azure Information Protection 정책을 다운로드할 수 없습니다. 
    
    - 이 문제는 구성이 잘못되었거나 로그인이 실패했기 때문에 발생할 수 있습니다. 기술 지원 팀 또는 관리자에게 문의해야 하지만 당분간은 Azure Information Protection 클라이언트를 사용하여 파일을 보호하고 보호된 파일을 볼 수 있습니다.

- 조직에서는 AD RMS(Active Directory Rights Management Services)만을 사용합니다. 


## <a name="limitations-for-protection-only-mode"></a>보호 전용 모드에 대한 제한 사항

- Office 앱에서 Azure Information Protection 표시줄이 표시되지 않습니다. **보호** > **표시줄 표시**를 클릭할 때 이 메뉴 옵션을 사용할 수 없습니다.

- 파일 탐색기에서 **분류 및 보호 - Azure Information Protection** 대화 상자를 사용하면 분류용 레이블이 표시되지 않습니다. 대신 이전 그림과 같이 RMS(Rights Management) 템플릿을 선택하기 위한 옵션이 표시됩니다. 

## <a name="supported-tasks-for-protection-only-mode"></a>보호 전용 모드에 대한 지원 작업

- Office IRM(정보 권한 관리) 기능을 사용하여 Office 앱 내에서 문서 및 전자 메일 보호(및 보호 해제): 예제: **파일** > **정보** > **문서 보호** > **액세스 제한**을 클릭합니다. 자세한 내용은 [Office 365, Office 2016 또는 Office 2013에서 정보 보호 기능 사용](../deploy-use/help-users.md)을 참조하세요.

- Windows 파일 탐색기를 사용하여 파일 보호(및 보호 해제): 파일을 마우스 오른쪽 단추로 클릭하고 파일 또는 폴더 > **분류 및 보호**를 클릭합니다. 관리자가 구성한 보호를 적용하려면 **분류 및 보호 - Azure Information Protection** 대화 상자에서 **템플릿 선택**을 클릭하고 사용 가능한 템플릿 중 하나를 선택합니다.

- Azure Information Protection 뷰어를 사용하여 보호된 파일 보기

- Office 앱에서 문서 추적 사이트에 액세스합니다. 그러나 이 사이트에서 문서를 추적하고 해지하려면 유효한 구독이 있어야 합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
