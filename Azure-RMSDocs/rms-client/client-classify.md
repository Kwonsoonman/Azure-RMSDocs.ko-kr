---
title: Azure Information Protection을 사용하여 파일 및 전자 메일 분류
description: 문서와 전자 메일을 분류하는 방법에 대한 지침을 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/31/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: d65c7690-fab7-4823-845c-8c73903e9c79
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e49cd5da0c34c8dd6fa537bca3d90ba56c32e690
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44150231"
---
# <a name="user-guide-classify-a-file-or-email-by-using-azure-information-protection"></a>사용자 가이드: Azure Information Protection을 사용하여 파일이나 전자 메일 분류

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

> [!NOTE]
> 이러한 지침을 사용하여 문서와 전자 메일을 분류할 수 있도록 합니다(보호하지 않음). 문서와 전자 메일을 보호해야 하는 경우 [분류 및 보호 지침](client-classify-protect.md)을 참조하세요. 사용할 일련의 지침이 확실하지 않은 경우 관리자 또는 지원 센터에 확인하세요.

문서와 전자 메일을 분류하는 가장 쉬운 방법은 Office 데스크톱 앱(**Word**, **Excel**, **PowerPoint**, **Outlook**) 내에서 해당 문서 및 전자 메일을 만들거나 편집하는 것입니다. 

그러나 **파일 탐색기**를 사용하여 파일을 분류할 수도 있습니다. 이 메서드는 추가 파일 유형을 지원하며, 여러 파일을 한 번에 분류하는 편리한 방법입니다. 

## <a name="using-office-apps-to-classify-your-documents-and-emails"></a>Office 앱을 사용하여 문서와 전자 메일 분류

Azure Information Protection 표시줄에서 자동으로 구성된 레이블 중 하나를 선택합니다. 

예를 들어 다음 그림에서는 **민감도**가 **설정되지 않음**을 표시하므로 문서에 아직 레이블이 지정되지 않았음을 보여 줍니다. "일반"과 같은 레이블을 설정하려면 **일반**을 클릭합니다. 현재 문서 또는 전자 메일에 적용할 레이블을 잘 모를 경우 레이블 도구 설명을 사용하여 각 레이블에 대해 자세히 알아보고 적용해야 하는 경우를 파악합니다. 

![Azure Information Protection 표시줄 예제](../media/info-protect-bar-not-set-callout.png)

레이블을 문서에 이미 적용되어 있으며 변경하려는 경우에는 다른 레이블을 선택할 수 있습니다. 레이블을 표시줄에 표시되지 않으면 먼저 현재 레이블 값 옆에 있는 **레이블 편집**을 클릭합니다.

> [!TIP]
> **파일** 탭의 **보호** 단추에서 레이블을 선택할 수도 있습니다.

레이블을 수동으로 선택하는 것 외에, 다음과 같은 방법으로 적용할 수도 있습니다.

- 관리자가 기본 레이블을 구성했으며 사용자가 유지하거나 변경할 수 있습니다.

- 중요한 데이터가 검색되면 특정 레이블을 선택하라는 권장 메시지를 표시하도록 관리자가 구성했습니다. 권장 사항을 수락(레이블이 적용됨)하거나, 거부(권장 레이블이 적용되지 않음)할 수 있습니다.

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Azure Information Protection 표시줄에 대한 예외 사항 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Office 앱에 이 Information Protection 표시줄이 표시되지 않나요?

- Azure Information Protection 클라이언트가 컴퓨터에 [설치](install-client-app.md)되지 않았습니다.

- 클라이언트가 설치되어 있지만 관리자가 표시줄을 표시하지 않는 설정을 구성했습니다. 대신, Office 리본에 있는 **파일** 탭의 **보호** 단추에서 레이블을 선택하세요. 

##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>표시줄에 예상된 레이블이 표시되지 않나요? 

- 관리자가 최근에 새 레이블을 구성했으면 모든 Office 앱을 닫았다가 다시 열어보세요. 이 작업은 레이블의 변경 내용이 있는지 확인합니다.

- 이 레이블은 계정에 포함되지 않는 정책 범위에 해당될 수 있습니다. 기술 지원 팀 또는 관리자에게 문의하세요.


## <a name="using-file-explorer-to-classify-files"></a>파일 탐색기를 사용하여 파일 분류

파일 탐색기를 사용할 때는 파일 하나/여러 개 또는 폴더를 빠르게 분류할 수 있습니다. 

폴더를 선택하면 해당 폴더의 모든 파일 및 하위 폴더가 설정된 분류를 사용하도록 자동으로 선택됩니다. 그러나 해당 폴더 또는 하위 폴더에서 새로 만드는 파일의 경우 자동으로 분류되지 않습니다.

파일 탐색기를 사용하여 파일을 분류할 때 하나 이상의 레이블이 흐리게 표시되면 선택한 파일이 해당 파일의 보호 없이 분류를 지원하지 않는 것입니다.

관리자 가이드에는 보호 없이 분류를 지원하는 파일 형식의 전체 목록이 포함됩니다. [분류 목적으로만 지원되는 파일 형식](client-admin-guide-file-types.md#file-types-supported-for-classification-only)

### <a name="to-classify-a-file-by-using-file-explorer"></a>파일 탐색기를 사용하여 파일을 분류하려면

1. 파일 탐색기에서 파일 하나/여러 개 또는 폴더를 선택합니다. 마우스 오른쪽 단추를 클릭하고 **분류 및 보호**를 선택합니다. 예를 들면 다음과 같습니다.
    
    ![Azure Information Protection을 사용한 파일 탐색기 오른쪽 클릭 메뉴 분류 및 보호](../media/right-click-classify-protect-folder.png)

2. **분류 및 보호 - Azure Information Protection** 대화 상자에서 Office 응용 프로그램에서와 같이 레이블을 사용합니다. 그러면 관리자가 정의한 분류가 설정됩니다. 
    
    이러한 레이블을 선택할 수 없는 경우(흐리게 표시): 선택한 파일이 분류를 지원하지 않습니다. 예를 들면 다음과 같습니다.
    
    ![분류 및 보호 - Azure Information Protection** 대화 상자에서 사용할 수 있는 레이블이 없음](../media/info-protect-dialog-labels-dimmed.png)

3. 분류를 지원하지 않는 파일을 선택한 경우 **닫기**를 클릭합니다. 또한 이 파일을 보호하지 않고 분류할 수 없습니다.
    
    레이블을 선택한 경우 **적용**을 클릭하고 **작업 완료** 메시지가 표시될 때까지 기다린 후 결과를 확인합니다. 그런 다음 **닫기**를 클릭합니다.

선택한 레이블을 변경하려면 이 프로세스를 반복하고 다른 레이블을 선택하면 됩니다.

지정한 분류 설정은 파일을 전자 메일로 보내거나 다른 위치에 저장하더라도 계속 적용된 상태로 유지됩니다. 
## <a name="other-instructions"></a>기타 지침
Azure Information Protection 사용자 가이드의 사용 방법 지침:

- [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

## <a name="additional-information-for-administrators"></a>관리자용 추가 정보    
[Azure Information Protection 정책 구성](../configure-policy.md)을 참조하세요.

