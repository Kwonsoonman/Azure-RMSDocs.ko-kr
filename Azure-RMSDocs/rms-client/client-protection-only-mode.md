---
title: "Azure Information Protection 클라이언트에 대한 보호 전용 모드"
description: "보호 전용 모드에서 Azure Information Protection 클라이언트를 실행하는 사용자를 위한 정보입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ffed64826982756072456be18cced0226b6bb6cc
ms.openlocfilehash: bc81b8587e999e6cbb036942e1c5d37e1e2b319b


---

# <a name="protection-only-mode-for-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에 대한 보호 전용 모드

Azure Information Protection 정책 없이 Azure Information Protection 클라이언트를 실행하면 **보호 전용** 모드로 표시됩니다. 예를 들어 Windows 파일 탐색기를 사용하는 경우 마우스 오른쪽 단추로 **분류 및 보호**를 클릭합니다.

![보호 전용 모드](../media/protection-only-mode.png)

 이 모드는 다음 시나리오에서 실행됩니다.

- 조직에 Azure Information Protection에 대한 구독(데이터의 분류 및 보호용)이 없으나 Azure Rights Management 서비스에 대한 구독(Office 365를 사용한 데이터 보호용)이 있습니다. 
    - 이것은 지원되는 시나리오이며, Azure Information Protection 클라이언트를 사용하여 파일을 보호하고 보호된 파일을 볼 수 있습니다.

- 조직에 Azure Information Protection에 대한 구독이 있으나 Azure Information Protection 정책을 다운로드할 수 없습니다. 
    - 이 문제는 구성이 잘못되었거나 로그인이 실패했기 때문에 발생할 수 있습니다. 기술 지원 팀 또는 관리자에게 문의해야 하지만 당분간은 Azure Information Protection 클라이언트를 사용하여 파일을 보호하고 보호된 파일을 볼 수 있습니다.

## <a name="limitations-for-protection-only-mode"></a>보호 전용 모드에 대한 제한 사항

- Office 앱에서 Azure Information Protection 표시줄이 표시되지 않습니다. **보호** > **표시줄 표시**를 클릭할 때 이 메뉴 옵션을 사용할 수 없습니다.

- 파일 탐색기에서 **분류 및 보호 - Azure Information Protection** 대화 상자를 사용하면 분류용 레이블이 표시되지 않습니다. 대신 이전 그림과 같이 RMS(Rights Management) 템플릿을 선택하기 위한 옵션이 표시됩니다. 

## <a name="supported-tasks-for-protection-only-mode"></a>보호 전용 모드에 대한 지원 작업

- Office IRM(정보 권한 관리) 기능을 사용하여 Office 앱 내에서 문서 및 전자 메일 보호(및 보호 해제): 예제: **파일** > **정보** > **문서 보호** > **액세스 제한**을 클릭합니다. 자세한 내용은 [Office 365, Office 2016 또는 Office 2013에서 정보 보호 기능 사용](../deploy-use/help-users.md)을 참조하세요.

- Windows 파일 탐색기를 사용하여 파일 보호(및 보호 해제): 파일을 마우스 오른쪽 단추로 클릭하고 파일 또는 폴더 > **분류 및 보호**를 클릭합니다. 관리자가 구성한 보호를 적용하려면 **분류 및 보호 - Azure Information Protection** 대화 상자에서 **템플릿 선택**을 클릭하고 사용 가능한 템플릿 중 하나를 선택합니다.

- Azure Information Protection 뷰어를 사용하여 보호된 파일 보기

- Office 앱에서 문서 추적 사이트에 액세스합니다. 그러나 이 사이트에서 문서를 추적하고 해지하려면 유효한 구독이 있어야 합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  



<!--HONumber=Feb17_HO2-->


