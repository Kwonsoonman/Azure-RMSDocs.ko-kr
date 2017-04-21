---
title: "Azure Information Protection을 사용하여 분류 및 보호"
description: "문서와 전자 메일을 분류하고 보호하는 방법에 대한 지침을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: f461b349440043bcf5d8624731eda86968194462
ms.sourcegitcommit: 52b7502e7049358f9fc0a418625bb460bb81479f
translationtype: HT
---
# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Azure Information Protection을 사용하여 파일이나 전자 메일 분류 및 보호

>*적용 대상: Active Directory Rights Management 서비스, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

문서와 전자 메일을 분류 및 보호하는 가장 쉬운 방법은 Office 데스크톱 앱(**Word**, **Excel**, **PowerPoint**, **Outlook**) 내에서 해당 문서 및 전자 메일을 만들거나 편집하는 것입니다. 

그러나 **파일 탐색기**를 사용하여 파일을 분류하고 보호할 수도 있습니다. 파일 탐색기는 추가적인 파일 형식을 지원하며, 여러 파일을 한 번에 편리하게 분류 및 보호할 수 있습니다. 이 방법은 Office 문서, PDF 파일, 텍스트 및 이미지 파일, 다양한 기타 파일을 보호하도록 지원합니다. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>조직 외부 사용자와 파일을 안전하게 공유

보호되는 파일은 다른 사용자와 공유해도 안전합니다. 예를 들어 파일을 전자 메일에 첨부하거나 SharePoint 사이트에서 초대를 보낼 수 있습니다.

조직 외부 사용자와 파일을 정기적으로 공유하는 경우 관리자가 이러한 사용자가 읽을 수 있도록 보호를 설정하는 레이블을 구성했을 수 있습니다. 또는 파일을 공유하기 전에 [Office 앱을 사용하여 사용자 지정 권한을 설정](#set-custom-permissions-for-a-document)하거나 [파일 탐색기를 사용하여 사용자 지정 권한을 설정](#using-file-explorer-to-classify-and-protect-files)할 수 있습니다. 

사용자 고유의 사용자 지정 권한을 설정했으며 파일이 이미 내부 사용을 위해 보호된 경우 먼저 복사본을 만들어 원래 권한을 보존할 수 있습니다. 그 후에 이 복사본을 사용하여 사용자 지정 권한을 설정합니다.  

파일에 사용자 지정 권한으로 보호되어 있으면 표준 공유 메커니즘을 사용하여 파일을 공유합니다. 파일을 함께 공유하는 이러한 사용자가 보호된 파일을 처음 받아보는 경우라면 파일을 보기 위한 지침이 필요할 수 있습니다. 이러한 사용자를 위해 다음 메시지를 복사한 후 붙여 넣을 수 있습니다. **이 파일은 Microsoft Azure Information Protection으로 보호되어 있습니다. 처음 사용할 경우 이러한 [지침](https://aka.ms/rms-signup)을 참조하세요.**


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Office 앱을 사용하여 문서와 전자 메일 분류 및 보호

Azure Information Protection 표시줄에서 자동으로 구성된 레이블 중 하나를 선택합니다. 

예를 들어 다음 그림에서는 **민감도**가 **설정되지 않음**을 표시하므로 문서에 아직 레이블이 지정되지 않았음을 보여 줍니다. 레이블(예: "내부")을 설정하려면 **내부**를 클릭합니다. 현재 문서 또는 전자 메일에 적용할 레이블을 잘 모를 경우 레이블 도구 설명을 사용하여 각 레이블에 대해 자세히 알아보고 적용해야 하는 경우를 파악합니다.

![Azure Information Protection 표시줄 예제](../media/info-protect-bar-not-set-callout.png)

레이블을 문서에 이미 적용되어 있으며 변경하려는 경우에는 다른 레이블을 선택할 수 있습니다. 레이블을 표시줄에 표시되지 않으면 먼저 현재 레이블 값 옆에 있는 **레이블 편집**을 클릭합니다.

레이블을 수동으로 선택하는 것 외에, 다음과 같은 방법으로 적용할 수도 있습니다.

- 관리자가 기본 레이블을 구성했으며 사용자가 유지하거나 변경할 수 있습니다.

- 중요한 데이터가 검색되면 특정 레이블을 선택하라는 권장 메시지를 표시하도록 관리자가 구성했습니다. 권장 사항을 수락(레이블이 적용됨)하거나, 거부(권장 레이블이 적용되지 않음)할 수 있습니다.

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Azure Information Protection 표시줄에 대한 예외 사항 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Office 앱에 이 Information Protection 표시줄이 표시되지 않나요?

- Azure Information Protection 클라이언트를 [설치](install-client-app.md)하지 않았거나 클라이언트가 [보호 전용 모드](client-protection-only-mode.md)로 실행되고 있습니다.
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>표시줄에 예상된 레이블이 표시되지 않나요? 

- 관리자가 최근에 새 레이블을 구성했으면 모든 Office 앱을 닫았다가 다시 열어보세요. 이 작업은 레이블의 변경 내용이 있는지 확인합니다.

- 누락된 레이블이 보호를 적용하는 경우 Rights Management 보호 적용을 지원하지 않는 Office 버전이 있을 수 있습니다. 이를 확인하려면 **보호** > **도움말 및 피드백**을 클릭하고 **클라이언트 상태**에 **이 클라이언트에 Office Professional Plus에 대한 사용 허가가 없습니다.**라는 메시지가 표시되는지 확인합니다. 

- 이 레이블은 계정에 포함되지 않는 정책 범위에 해당될 수 있습니다. 기술 지원 팀 또는 관리자에게 문의하세요.

### <a name="set-custom-permissions-for-a-document"></a>문서에 대한 사용자 지정 권한 설정

선택한 레이블에 관리자가 포함한 보호를 사용하지 않고 직접 문서 보호 설정을 지정할 수 있습니다.

1. **홈** 탭의 **보호** 그룹에서 **보호** > **사용자 지정 권한**을 클릭합니다.

    ![사용자 지정 권한 옵션](../media/custom-permissions-callout.png)
    
    지정하는 사용자 지정 권한은 선택된 레이블에 대해 관리자가 정의했을 수 있는 보호 설정을 보완하지 않고 대신합니다.  

2. **Microsoft Azure Information Protection** 대화 상자에서 다음을 지정합니다.

    - **사용자 지정 권한으로 보호**: 사용자 지정 권한을 지정하고 적용할 수 있도록 이 옵션이 선택되어 있는지 확인합니다. 사용자 지정 권한을 제거하려면 이 옵션을 선택 취소합니다.
    
    - **사용 권한 선택**: 자기만 액세스할 수 있도록 파일을 보호하려면 **Only for me**(나만)를 선택합니다. 그렇지 않은 경우는 사람들에게 지정할 액세스 레이블을 선택합니다.

    - **사용자, 그룹 또는 조직 선택**: 하나 이상의 파일에 대해 선택한 권한을 소유해야 하는 사용자를 지정합니다. 조직의 모든 사용자에 대한 전체 메일 주소, 그룹 메일 주소 또는 조직 도메인 이름을 입력합니다. 개인 메일 주소는 현재 지원되지 않습니다.
        
    - **액세스 만료**: 특정 기간에만 제공해야 하는 파일에 한해 이 옵션을 선택합니다. 그러면 지정한 사용자가 지정된 날짜 이후로는 선택한 하나 이상의 파일을 열 수 없습니다. 원본 파일은 계속 열 수 있지만 현재 표준 시간대로 선택한 날짜의 자정이 지나면 지정된 사용자는 파일을 열 수 없습니다.

5. **적용**을 클릭하고 **사용자 지정 권한 적용됨** 메시지가 표시되기를 기다립니다. 그런 다음 **닫기**를 클릭합니다.


### <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Azure Information Protection 표시줄을 위한 바로 가기 키

바로 가기 키를 사용하여 Azure Information Protection 표시줄에 액세스하려면 다음과 같은 키 조합을 사용합니다.

- **Ctrl** + **Shift** + **~**를 누릅니다. 

그 다음, 레이블과 표시줄에 있는 다른 컨트롤 (**레이블 숨기기** 아이콘 및 **레이블 삭제** 아이콘)을 선택하려면 Tab 키를 사용하고 Enter 키를 사용하여 선택합니다.

## <a name="using-file-explorer-to-classify-and-protect-files"></a>파일 탐색기를 사용하여 파일 분류 및 보호

파일 탐색기를 사용할 때는 파일 하나/여러 개 또는 폴더를 빠르게 분류하고 보호할 수 있습니다. 

폴더를 선택하면 해당 폴더의 모든 파일 및 하위 폴더가 설정된 분류 및 보호 옵션을 사용하도록 자동으로 선택됩니다. 그러나 해당 폴더 또는 하위 폴더에서 새로 만드는 파일의 경우 이러한 옵션으로 자동 구성되지 않습니다.

파일 탐색기를 사용하여 파일을 분류하고 보호할 때 하나 이상의 레이블이 흐리게 표시되면 선택한 파일이 분류를 지원하지 않는 것입니다. 관리자가 보호를 적용하도록 레이블을 구성한 경우에만 이러한 파일에 대해 레이블을 선택할 수 있습니다. 또는 보호 설정을 직접 지정할 수 있습니다. 

일부 파일은 변경할 경우 PC 실행을 중지할 수 있으므로 분류 및 보호에서 자동으로 제외됩니다. 이러한 파일을 선택할 수 있지만 제외된 폴더 또는 파일로서 건너뛰어집니다. 예제에는 실행 파일 및 Windows 폴더가 포함됩니다.

관리자 가이드 [Azure Information Protection 클라이언트에서 지원하는 파일 형식](client-admin-guide-file-types.md)에 지원되는 파일 형식의 전체 목록과 자동으로 제외된 파일 및 폴더 목록이 포함됩니다.


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>파일 탐색기를 사용하여 파일을 분류 및 보호하려면

1. 파일 탐색기에서 파일 하나/여러 개 또는 폴더를 선택합니다. 마우스 오른쪽 단추를 클릭하고 **분류 및 보호**를 선택합니다. 예를 들면 다음과 같습니다.
    
    ![Azure Information Protection을 사용한 파일 탐색기 오른쪽 클릭 메뉴 분류 및 보호](../media/right-click-classify-protect-folder.png)

2. **분류 및 보호 - Azure Information Protection** 대화 상자에서 Office 응용 프로그램에서와 같이 레이블을 사용합니다. 그러면 관리자가 정의한 분류와 보호가 설정됩니다. 

    - 이러한 레이블을 선택할 수 없는 경우(흐리게 표시): 선택한 파일이 분류를 지원하지 않지만 사용자 지정 권한으로 보호할 수 있습니다(3단계). 예를 들면 다음과 같습니다.

    ![분류 및 보호 - Azure Information Protection** 대화 상자에서 사용할 수 있는 레이블이 없음](../media/info-protect-dialog-labels-dimmed.png)
    
    - 이 대화 상자에 레이블은 표시되지 않지만 **회사의 미리 정의된 보호** 옵션은 표시됨: 클라이언트가 [보호 전용 모드](client-protection-only-mode.md)에서 실행되고 있습니다. 관리자가 사용자를 위해 구성한 보호를 적용하기 위해 템플릿을 선택하거나, **사용자 지정 권한**을 선택하여 자체 보호 설정을 지정한 후 4단계로 이동합니다.
    
    ![분류 및 보호 - Azure Information Protection** 대화 상자에 레이블이 없음](../media/info-protect-dialog-labels-protection-only.png)
    
3. 선택된 레이블에 관리자가 포함했을 수 있는 보호 설정을 사용하지 않고 고유의 보호 설정을 지정하려면 **사용자 지정 권한으로 보호**를 선택합니다.
    
    지정하는 사용자 지정 권한은 선택된 레이블에 대해 관리자가 정의했을 수 있는 보호 설정을 보완하지 않고 대신합니다.  

4. 사용자 지정 권한 옵션을 선택한 경우 다음 항목을 지정하세요.

    - **권한 선택**: 선택한 하나 이상의 파일을 보호할 때 사용자에게 제공할 액세스 권한 수준을 선택합니다.
    
    - **사용자 선택**: 하나 이상의 파일에 대해 선택한 권한을 소유해야 하는 사용자를 지정합니다. 조직의 모든 사용자에 대한 전체 메일 주소, 그룹 메일 주소 또는 조직 도메인 이름을 입력합니다. 개인 메일 주소는 현재 지원되지 않습니다.
        
    - **액세스 만료**: 특정 기간에만 제공해야 하는 파일에 한해 이 옵션을 선택합니다. 그러면 지정한 사용자가 지정된 날짜 이후로는 선택한 하나 이상의 파일을 열 수 없습니다. 원본 파일은 계속 열 수 있지만 현재 표준 시간대로 선택한 날짜의 자정이 지나면 지정된 사용자는 파일을 열 수 없습니다.

5. **적용**을 클릭하고 **작업 완료** 메시지가 표시될 때까지 기다린 후 결과를 확인합니다. 그런 다음 **닫기**를 클릭합니다.

이제 선택한 하나 이상의 파일이 선택한 옵션에 따라 분류 및 보호됩니다. 경우에 따라(보호를 추가하면 파일 이름 확장명이 바뀌는 경우) 파일 탐색기의 원본 파일이 Azure Information Protection 잠금 아이콘이 있는 새 파일로 대체됩니다. 예를 들면 다음과 같습니다.

![Azure Information Protection 잠금 아이콘이 있는 보호된 파일](../media/Pfile.png)

분류 및 보호 설정을 변경하려는 경우 또는 나중에 설정을 수정해야 하는 경우 새 설정을 사용하여 이 프로세스를 반복하면 됩니다.

지정한 분류 및 보호 설정은 파일을 전자 메일로 보내거나 다른 위치에 저장하더라도 계속 적용된 상태로 유지됩니다. 파일을 보호한 경우에는 사용자가 해당 파일을 사용하는 방식을 추적할 수 있으며 필요에 따라 파일 액세스 권한을 해지할 수 있습니다. 자세한 내용은 [Azure Information Protection 사용 시 보호된 문서 추적 및 액세스 권한 해지](client-track-revoke.md)를 참조하세요. 


## <a name="other-instructions"></a>기타 지침
Azure Information Protection 사용자 가이드의 사용 방법 지침:

-   [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
