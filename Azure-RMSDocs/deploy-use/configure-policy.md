---
title: "Azure Information Protection 정책 구성"
description: "분류, 레이블 지정 및 보호를 구성하려면 Azure Information Protection 정책을 구성해야 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7f3b64e5e4b0dfbccf694a986a85f1c207580915
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2017
---
# <a name="configuring-azure-information-protection-policy"></a>Azure Information Protection 정책 구성

>*적용 대상: Azure Information Protection*

분류, 레이블 지정 및 보호를 구성하려면 Azure Information Protection 정책을 구성해야 합니다. 이 정책은 [Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치한 컴퓨터에 다운로드됩니다.

## <a name="subscription-support"></a>구독 지원

Azure Information Protection 정책은 다음과 같은 다양한 수준의 구독을 지원합니다.

- Azure Information Protection P2: 분류, 레이블 지정 및 보호 기능을 지원합니다.

- Azure Information Protection P1: 대부분의 분류, 레이블 지정 및 보호 기능을 지원하지만 자동 분류 또는 HYOK는 지원하지 않습니다.

- Azure 권한 관리 서비스를 포함하는 Office 365: 보호 기능을 지원하지만 분류 및 레이블 지정은 지원하지 않습니다.

Azure Information Protection P2 구독을 필요로 하는 옵션은 이제 포털에서 확인할 수 있습니다.

테넌트에 대해 다양한 사용자 구독이 있는 경우 사용자가 다운로드하는 Azure Information Protection 정책에 해당 계정에 사용이 허가되지 않은 구성 옵션이 포함되어 있지 않은지 반드시 확인해야 합니다. 일부 사용자에게만 라이선스가 있는 옵션을 구성할 때는 범위 정책을 사용하여 해당 사용자를 라이선스가 있는 기능을 사용하도록 구성합니다.

구독에 대한 자세한 내용은 [Azure Information Protection을 사용하려면 어떤 구독이 필요하며, 포함된 기능은 무엇인가요?](../get-started/faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)를 참조하세요.

범위 정책을 구성하는 방법에 대한 자세한 내용은 [범위 지정 정책을 사용하여 특정 사용자에 대한 정책을 구성하는 방법](configure-policy-scope.md)을 참조하세요.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Azure Information Protection 정책을 구성하는 방법

1. 새 브라우저 창에서 보안 관리자나 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. **Azure Information Protection** 블레이드로 이동합니다. 예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information Protection**을 입력합니다. 결과에서 **Azure Information Protection**을 선택합니다. 
    
    서비스에 처음 연결하면 **Azure Information Protection - 빠른 시작** 블레이드가 자동으로 열립니다. 모든 사용자가 받는 정책을 구성하려면 **정책** 메뉴 선택에서 **전역 정책**을 선택하여 **Azure Information Protection - 전역 정책** 블레이드를 엽니다. 이 블레이드는 나중에 서비스에 다시 연결되면 자동으로 열리므로 모든 사용자에게 적용되는 전역 정책을 보고 편집할 수 있습니다. 
    
    이 Azure Information Protection 정책에는 구성할 수 있는 다음 요소가 포함됩니다.
    
    - 문서 및 전자 메일을 분류할 수 있는 레이블.
    
    - 사용자의 Office 응용 프로그램에 표시되는 Information Protection 표시줄의 제목 및 도구 설명.
    
    - 사용자가 문서를 저장하고 전자 메일을 보낼 때 분류를 적용할 수 있는 옵션.
    
    - 문서 및 전자 메일을 분류하기 위한 시작점으로 기본 레이블을 설정할 수 있는 옵션.
    
    - 원래보다 민감도 수준이 낮은 레이블을 선택한 경우 이유를 제공하라는 메시지를 사용자에게 표시할 수 있는 옵션.
    
    - 첨부 파일에 따라 메일 메시지에 자동으로 레이블을 지정할 수 있는 옵션.
    
    - 사용자를 위한 사용자 지정 도움말 링크를 제공하는 옵션.

Azure Information Protection은 5개의 기본 레이블을 포함하는 [기본 정책](configure-policy-default.md)과 함께 제공됩니다. 이러한 레이블은 조직에서 일반적으로 만들고 저장하는 최저 분류인 개인 데이터부터 최고 분류인 극비 데이터에 이르기까지 전체 범위의 데이터와 함께 사용할 수 있습니다. 

기본 레이블을 변경하지 않고 사용하거나, 이를 사용자 지정하거나, 삭제하고 새 레이블을 만들 수 있습니다. 다음 섹션의 링크에서 관련 옵션을 찾아 구성하는 방법을 자세히 확인할 수 있습니다. 

Azure Information Protection 블레이드를 변경한 경우 **Save**(저장)를 클릭하여 변경 내용을 저장하거나 **Discard**(취소)를 클릭하여 마지막으로 저장된 설정으로 되돌립니다.

원하는 변경 작업을 마쳤으면 **Publish**(게시)를 클릭합니다. 

Azure Information Protection 클라이언트는 지원되는 Office 응용 프로그램이 시작될 때마다 변경 내용을 확인하여 해당 최신 Azure Information Protection 정책으로 변경 내용을 다운로드합니다. 클라이언트에서 정책을 새로 고치는 추가 트리거:

- 마우스 오른쪽 단추를 클릭하여 파일 또는 폴더 분류 및 보호.

- 레이블 지정 및 보호를 위한 [PowerShell cmdlets](../rms-client/client-admin-guide-powershell.md) 실행(Get-AIPFileStatus, Set-AIPFileClassification 및 Set-AIPFileLabel)

- 24시간마다.

>[!NOTE]
>클라이언트가 정책을 다운로드하면 정책이 완벽하게 작동하는 데 몇 분 정도 걸립니다. 실제 시간은 정책 구성의 크기 및 복잡도, 네트워크 연결 등 여러 요소에 따라 다릅니다. 레이블의 결과 작업이 최근 변경 내용과 일치하지 않는 경우에는 최대 15분 정도 기다렸다 다시 시도하세요.

### <a name="configuring-your-organizations-policy"></a>조직의 정책 구성

다음 정보를 사용하여 Azure Information Protection 정책을 구성할 수 있습니다.

- [기본 Information Protection 정책](configure-policy-default.md)

- [정책 설정을 구성하는 방법](configure-policy-settings.md)

- [새 레이블을 만드는 방법](configure-policy-new-label.md)

- [레이블을 삭제하거나 순서를 변경하는 방법](configure-policy-delete-reorder.md)

- [기존 레이블을 변경하거나 사용자 지정하는 방법](configure-policy-change-label.md)

- [보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)

- [시각적 표시를 적용하도록 레이블을 구성하는 방법](configure-policy-markings.md)

- [자동 및 권장 분류에 대한 조건을 구성하는 방법](configure-policy-classification.md)

- [범위 지정 정책을 사용하여 특정 사용자에 대한 정책을 구성하는 방법](configure-policy-scope.md)

- [템플릿을 구성 및 관리하는 방법](configure-policy-templates.md)

- [다른 언어에 대해 레이블을 구성하는 방법](configure-policy-languages.md)

## <a name="next-steps"></a>다음 단계

기본 정책을 사용자 지정하는 방법에 대한 예제를 보려면 Office 응용 프로그램에서 결과 동작을 확인하고 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
