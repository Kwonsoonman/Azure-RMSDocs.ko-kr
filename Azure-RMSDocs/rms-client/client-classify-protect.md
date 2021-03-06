---
title: Azure Information Protection을 사용하여 파일 및 전자 메일 분류 및 보호
description: 문서와 전자 메일을 분류하고 보호하는 방법에 대한 지침을 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/17/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 355d71f844d64fb26898c482d2414ca388ac38be
ms.sourcegitcommit: ea8207da513f61bc0691c952da1f8b61ceb10887
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45696520"
---
# <a name="user-guide-classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>사용자 가이드: Azure Information Protection을 사용하여 파일이나 전자 메일 분류 및 보호

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

> [!NOTE]
> 이러한 지침을 사용하여 문서와 전자 메일을 분류하고 보호할 수 있도록 합니다. 문서와 전자 메일을 분류하기만 하고 보호하지 않아야 하는 경우 [분류 전용 지침](client-classify.md)을 참조하세요. 사용할 일련의 지침이 확실하지 않은 경우 관리자 또는 지원 센터에 확인하세요.

문서와 전자 메일을 분류 및 보호하는 가장 쉬운 방법은 Office 데스크톱 앱(**Word**, **Excel**, **PowerPoint**, **Outlook**) 내에서 해당 문서 및 전자 메일을 만들거나 편집하는 것입니다. 

그러나 **파일 탐색기**를 사용하여 파일을 분류하고 보호할 수도 있습니다. 이 메서드는 추가 파일 유형을 지원하며, 여러 파일을 한 번에 분류하고 보호하는 편리한 방법입니다. 이 방법은 Office 문서, PDF 파일, 텍스트 및 이미지 파일, 다양한 기타 파일을 보호하도록 지원합니다. 

레이블에서 문서에 보호를 적용하면 보호된 문서는 SharePoint 또는 OneDrive에서 저장하는 데 적합하지 않습니다. 이러한 위치에서는 보호된 파일에 대해 공동 작성, Office Online, 검색, 문서 미리 보기, 썸네일 및 eDiscovery를 지원하지 않습니다. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>조직 외부 사용자와 파일을 안전하게 공유

보호되는 파일은 다른 사용자와 공유해도 안전합니다. 예를 들어, 보호된 문서를 메일에 첨부합니다.

조직 외부 사용자와 파일을 공유하기 전에 지원 센터 또는 관리자에게 문의하여 외부 사용자의 파일을 보호하는 방법을 확인합니다.

예를 들어, 조직에서 다른 조직의 사용자와 정기적으로 통신하는 경우, 관리자는 이러한 사용자가 보호된 문서를 읽고 사용할 수 있도록 보호를 설정하는 레이블을 구성했을 수 있습니다. 그런 다음, 이러한 레이블을 선택하여 공유할 문서를 분류하고 보호합니다.

또는 외부 사용자가 [B2B(business-to-business) 계정](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)을 만든 경우에는 [사용자 지정 권한을 설정하는 데 Office 앱](#set-custom-permissions-for-a-document)을 사용하거나 공유하기 전에 문서에 대한 [사용자 지정 권한을 설정하는 데 파일 탐색기](#using-file-explorer-to-classify-and-protect-files)를 사용할 수 있습니다. 고유한 사용자 지정 권한을 설정하고 파일이 이미 내부용으로 보호된 경우, 먼저 복사본을 만들어 원래 권한을 보존할 수 있습니다. 그 후에 이 복사본을 사용하여 사용자 지정 권한을 설정합니다.


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Office 앱을 사용하여 문서와 전자 메일 분류 및 보호

Azure Information Protection 표시줄 또는 리본의 **보호** 단추를 사용하여 자동으로 구성된 레이블 중 하나를 선택합니다. 

예를 들어 다음 그림에서는 Azure Information Protection 표시줄의 **민감도**가 **설정되지 않음**을 표시하므로 문서에 아직 레이블이 지정되지 않았음을 보여 줍니다. "일반"과 같은 레이블을 설정하려면 **일반**을 클릭합니다. 현재 문서 또는 전자 메일에 적용할 레이블을 잘 모를 경우 레이블 도구 설명을 사용하여 각 레이블에 대해 자세히 알아보고 적용해야 하는 경우를 파악합니다. 

![Azure Information Protection 표시줄 예제](../media/info-protect-bar-not-set-callout.png)

레이블을 문서에 이미 적용되어 있으며 변경하려는 경우에는 다른 레이블을 선택할 수 있습니다. 레이블을 표시줄에 표시되지 않으면 먼저 현재 레이블 값 옆에 있는 **레이블 편집**을 클릭합니다.

레이블을 수동으로 선택하는 것 외에, 다음과 같은 방법으로 적용할 수도 있습니다.

- 관리자가 기본 레이블을 구성했으며 사용자가 유지하거나 변경할 수 있습니다.

- 중요한 데이터가 검색되면 특정 레이블을 선택하라는 권장 메시지를 표시하도록 관리자가 구성했습니다. 권장 사항을 수락(레이블이 적용됨)하거나, 거부(권장 레이블이 적용되지 않음)할 수 있습니다.

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Azure Information Protection 표시줄에 대한 예외 사항 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Office 앱에 이 Information Protection 표시줄이 표시되지 않나요?

가능한 원인:

- Azure Information Protection 클라이언트가 컴퓨터에 [설치](install-client-app.md)되지 않았습니다.

- 클라이언트가 설치되어 있지만 관리자가 표시줄을 표시하지 않는 설정을 구성했습니다. 대신, Office 리본에 있는 **파일** 탭의 **보호** 단추에서 레이블을 선택하세요. 

- 클라이언트가 [보호 전용 모드](client-protection-only-mode.md)에서 실행 중입니다.
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed"></a>예상된 레이블이 표시되지 않나요? 

가능한 원인:

- 관리자가 최근에 새 레이블을 구성했으면 모든 Office 앱을 닫았다가 다시 열어보세요. 이 작업은 레이블의 변경 내용이 있는지 확인합니다.

- 누락된 레이블이 보호를 적용하는 경우 Rights Management 보호 적용을 지원하지 않는 Office 버전이 있을 수 있습니다. 확인하려면 **보호** > **도움말 및 피드백**을 클릭합니다. 대화 상자에서 **클라이언트 상태** 섹션에 **이 클라이언트에 Office Professional Plus에 대한 사용 허가가 없습니다**라는 메시지가 표시되는지 확인합니다. 
    
    최소 버전 1805, 빌드 9330.2078의 Office 2016 앱이 있으며 계정에 Azure Rights Management(Office 365용 Azure Information Protection라고도 함)의 라이선스가 지정된 경우 Office Professional Plus가 필요하지 않습니다.

- 이 레이블은 계정에 포함되지 않는 정책 범위에 해당될 수 있습니다. 기술 지원 팀 또는 관리자에게 문의하세요.

### <a name="set-custom-permissions-for-a-document"></a>문서에 대한 사용자 지정 권한 설정

관리자가 허용한 경우 선택한 레이블에 관리자가 포함한 보호를 사용하지 않고 직접 문서 보호 설정을 지정할 수 있습니다. 이 옵션은 문서에 특정되고, Outlook에서 지원되지 않습니다.

1. **홈** 탭의 **보호** 그룹에서 **보호** > **사용자 지정 권한**을 클릭합니다.

    ![사용자 지정 권한 옵션](../media/custom-permissions-callout.png)
    
    **사용자 지정 권한**이 표시되지 않는 경우 관리자가 이 옵션을 사용하도록 허용하지 않은 것입니다.
    
    지정하는 사용자 지정 권한은 선택된 레이블에 대해 관리자가 정의했을 수 있는 보호 설정을 보완하지 않고 대신합니다.  

2. **Microsoft Azure Information Protection** 대화 상자에서 다음을 지정합니다.

    - **사용자 지정 권한으로 보호**: 사용자 지정 권한을 지정하고 적용할 수 있도록 이 옵션이 선택되어 있는지 확인합니다. 사용자 지정 권한을 제거하려면 이 옵션을 선택 취소합니다.
    
    - **사용 권한 선택**: 자기만 액세스할 수 있도록 파일을 보호하려면 **Only for me**(나만)를 선택합니다. 그렇지 않은 경우 사람들에게 부여할 액세스 레이블을 선택합니다.
    
    - **사용자, 그룹 또는 조직 선택**: 하나 이상의 파일에 대해 선택한 권한을 소유해야 하는 사용자를 지정합니다. 조직의 모든 사용자에 대한 전체 메일 주소, 그룹 메일 주소 또는 조직 도메인 이름을 입력합니다. 
        
        주소록 아이콘을 사용하여 Outlook 주소록에서 사용자 또는 그룹을 선택할 수도 있습니다.
    
    - **액세스 만료**: 특정 기간에만 제공해야 하는 파일에 한해 이 옵션을 선택합니다. 그러면 지정한 사용자가 설정한 날짜 이후로는 선택한 하나 이상의 파일을 열 수 없습니다. 원본 파일은 계속 열 수 있지만 현재 표준 시간대로 설정한 날짜의 자정이 지나면 지정된 사용자는 파일을 열 수 없습니다.

5. **적용**을 클릭하고 **사용자 지정 권한 적용됨** 메시지가 표시되기를 기다립니다. 그런 다음 **닫기**를 클릭합니다.

### <a name="safely-sharing-by-email"></a>전자 메일로 안전하게 공유하기

전자 메일로 Office 문서를 공유할 때 보호하는 전자 메일에 문서를 첨부할 수 있으며 해당 문서는 전자 메일에 적용되는 것과 동일한 제한 사항으로 자동으로 보호됩니다. 

하지만 문서를 먼저 보호한 다음 전자 메일에 첨부하는 것이 좋습니다. 전자 메일 메시지에 중요한 정보가 포함되어 있으면 전자 메일도 보호하십시오. 문서를 전자 메일에 첨부하기 전에 보호하는 두 가지 이점:

- 추적할 수 있고 필요한 경우 전자 메일을 보낸 후에 문서를 취소할 수 있습니다.

- 문서에 전자 메일 메시지와 다른 권한을 적용할 수 있습니다.

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
    
3. 관리자에 의해 허용된 경우 선택한 레이블에 관리자가 포함한 보호를 사용하지 않고 직접 보호 설정을 지정할 수 있습니다. 그러려면 **사용자 지정 권한으로 보호**를 선택합니다.
    
    **사용자 지정 권한으로 보호**가 표시되지 않는 경우 관리자가 이 옵션을 사용하도록 허용하지 않은 것입니다.
    
    지정하는 사용자 지정 권한은 선택된 레이블에 대해 관리자가 정의했을 수 있는 보호 설정을 보완하지 않고 대신합니다.  

4. 사용자 지정 권한 옵션을 선택한 경우 다음 항목을 지정하세요.

    - **권한 선택**: 선택한 하나 이상의 파일을 보호할 때 사용자에게 제공할 액세스 권한 수준을 선택합니다.
    
    - **사용자, 그룹 또는 조직 선택**: 하나 이상의 파일에 대해 선택한 권한을 소유해야 하는 사용자를 지정합니다. 조직의 모든 사용자에 대한 전체 메일 주소, 그룹 메일 주소 또는 조직 도메인 이름을 입력합니다. 
    
    또는 주소록 아이콘을 사용하여 Outlook 주소록에서 사용자 또는 그룹을 선택할 수 있습니다.
        
    - **액세스 만료**: 지정한 다른 사용자가 선택된 파일을 설정된 날짜 후에 열 수 없도록 하기 위해 시간이 중요한 파일에 대해서만 이 옵션을 선택합니다. 사용자 본인은 원본 파일을 여전히 열 수 있지만 설정한 날짜의 자정(현재 표준 시간대) 이후에는 지정한 다른 사용자가 해당 파일을 열 수 없게 됩니다.
    
    이전에 Office 2010 앱의 사용자 지정 권한을 사용해서 이 설정을 구성한 경우 이 대화 상자에 지정된 만료 날짜가 표시되지 않지만 만료 날짜는 여전히 설정된 상태입니다. 이것은 Office 2010에서 만료 날짜를 구성한 경우에만 나타나는 표시 문제입니다.

5. **적용**을 클릭하고 **작업 완료** 메시지가 표시될 때까지 기다린 후 결과를 확인합니다. 그런 다음 **닫기**를 클릭합니다.

이제 선택한 하나 이상의 파일이 선택한 옵션에 따라 분류 및 보호됩니다. 경우에 따라(보호를 추가하면 파일 이름 확장명이 바뀌는 경우) 파일 탐색기의 원본 파일이 Azure Information Protection 잠금 아이콘이 있는 새 파일로 대체됩니다. 예를 들면 다음과 같습니다.

![Azure Information Protection 잠금 아이콘이 있는 보호된 파일](../media/Pfile.png)

분류 및 보호 설정을 변경하려는 경우 또는 나중에 설정을 수정해야 하는 경우 새 설정을 사용하여 이 프로세스를 반복하면 됩니다.

지정한 분류 및 보호 설정은 파일을 전자 메일로 보내거나 다른 위치에 저장하더라도 계속 적용된 상태로 유지됩니다. 파일을 보호한 경우에는 사용자가 해당 파일을 사용하는 방식을 추적할 수 있으며 필요에 따라 파일 액세스 권한을 해지할 수 있습니다. 자세한 내용은 [Azure Information Protection 사용 시 보호된 문서 추적 및 액세스 권한 해지](client-track-revoke.md)를 참조하세요. 


## <a name="other-instructions"></a>기타 지침
Azure Information Protection 사용자 가이드의 사용 방법 지침:

-   [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

## <a name="additional-information-for-administrators"></a>관리자용 추가 정보    
**사용자에게 사용자 지정 권한 옵션 제공** 정책 설정을 사용하도록 설정하는 구성 지침은 [Azure Information Protection 정책 구성 설정](../configure-policy-settings.md)을 참조하세요.

기타 구성 지침: [Azure Information Protection 정책 구성](../configure-policy.md)

