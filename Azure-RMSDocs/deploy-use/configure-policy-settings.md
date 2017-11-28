---
title: "Azure Information Protection 정책 설정 구성"
description: "모든 사용자와 모든 장치에 적용되는 Azure Information Protection 정책의 설정을 구성하는 방법을 설명합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: f651a621b961bfba63ad43e5372eec9a68c170d4
ms.sourcegitcommit: f1d0b899e6d79ebef3829f24711f947316bca8ef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2017
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Azure Information Protection에 대한 정책 설정을 구성하는 방법

>*적용 대상: Azure Information Protection*

Azure Information Protection 정책에는 Information Protection 표시줄 제목과 도구 설명 외에 레이블에서 독립적으로 구성할 수 있는 다음과 같은 몇 가지 설정이 있습니다.

![Azure Information Protection 정책 전역 설정](../media/info-protect-policy-default-settingsv3.png)

Azure Information Protection에 대한 구독을 구매한 시기에 따라 정책 설정의 기본값이 다를 수 있습니다. 일부 설정은 [사용자 지정 클라이언트 설정](../rms-client/client-admin-guide-customizations.md)으로 설정할 수도 있습니다.

이러한 설정을 구성하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창에서 보안 관리자 또는 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 설정을 모든 사용자에게 적용하려는 경우 **Azure Information Protection - 전역 정책** 블레이드에 그대로 있습니다.
    
    구성하려는 설정이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그런 다음 **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

3. **Azure Information Protection - 전역 정책** 블레이드 또는 **정책:\<이름>** 블레이드에서 설정을 구성합니다.
    
    - **Select the default label**(기본 레이블 선택): 이 옵션을 설정한 경우 레이블이 없는 문서와 메일에 할당할 레이블을 선택합니다. 하위 레이블이 있는 경우에는 레이블을 기본값으로 설정할 수 없습니다. 
        
    - **All documents and emails must have a label**(모든 문서와 메일에 레이블이 있어야 함):이 옵션을 **On**(켜기)으로 설정하면 저장되는 모든 문서 및 전송되는 모든 메일에 레이블이 적용되어야 합니다. 레이블 지정은 사용자에 의해 수동으로 할당되거나, [조건](configure-policy-classification.md)의 결과로 자동으로 할당되거나, 기본적으로 할당(**Select the default label**(기본 레이블 선택) 옵션을 설정하여)될 수 있습니다.
        
        사용자가 문서를 저장하거나 메일을 보낼 때 레이블이 할당되지 않은 경우에는 레이블을 선택하라는 메시지가 표시됩니다. 예를 들면 다음과 같습니다.
        
        ![레이블 지정이 적용된 경우의 Azure Information Protection 프롬프트](../media/info-protect-enforce-labelv2.png)
        
    - **Users must provide justification to set a lower classification label, remove a label, or remove protection**(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함): 이 옵션을 **켜기**로 설정하고 이러한 작업 중 하나를 수행하면(예: **공용** 레이블을 **개인**으로 변경) 이 작업에 대한 설명을 제공하라는 메시지가 표시됩니다. 예를 들어 사용자는 문서에 더 이상 민감한 정보가 포함되어 있지 않다고 설명할 수 있습니다. 작업 및 해당 근거는 사용자의 로컬 Windows 이벤트 로그 **응용 프로그램 및 서비스 로그** > **Azure Information Protection**에 기록됩니다.  
        
        ![새 분류가 하위 수준인 경우의 Azure Information Protection 프롬프트](../media/info-protect-lower-justification.png)
        
        이 옵션은 하위 레이블에 적용되지 않습니다.
        
    - **For email messages with attachments, apply a label that matches the highest classification of those attachments**(첨부 파일이 있는 메일 메시지의 경우 해당 첨부 파일의 최고 분류와 일치하는 레이블 적용): 이 옵션을 **권장**으로 설정한 경우 메일 메시지에 레이블을 적용하라는 메시지가 표시됩니다. 첨부 파일에 적용된 분류 레이블에 따라 레이블이 동적으로 선택되고 최고 분류 레이블이 선택됩니다. 첨부 파일은 실제 파일이어야 하며 파일에 대한 링크일 수 없습니다(예를 들어 SharePoint 또는 비즈니스용 OneDrive의 파일에 대한 링크). 사용자는 권장 사항을 수락하거나 해제할 수 있습니다. 이 옵션을 **켜기**로 설정한 경우 레이블이 자동으로 적용되지만, 사용자가 메일을 보내기 전에 레이블을 제거하거나 다른 레이블을 선택할 수 있습니다.  
    
    - **Display the Information Protection bar in Office apps**(Office 앱에 Information Protection 표시줄 표시): 이 설정이 꺼져 있으면 사용자가 Word, Excel, PowerPoint 및 Outlook의 표시줄에서 레이블을 선택할 수 없습니다. 대신, 사용자는 리본에 있는 **보호** 단추에서 레이블을 선택해야 합니다. 이 설정이 켜져 있으면 사용자가 표시줄이나 단추에서 레이블을 선택할 수 있습니다.
    
    이 설정이 켜져 있으면 고급 클라이언트 설정과 함께 사용할 수 있으므로 사용자가 표시줄을 표시하지 않도록 선택할 경우 [Azure Information Protection 표시줄을 영구적으로 숨기기](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar)를 지정할 수 있습니다. **보호** 단추에서 **표시줄 표시** 옵션을 선택 해제하면 됩니다.
    
    - **Outlook 리본에 전달 금지 단추 추가**: 이 설정이 켜져 있으면 사용자가 Outlook 메뉴에서 **전달 금지** 옵션을 선택할 수 있을 뿐만 아니라 Outlook 리본의 **보호** 그룹에서 이 단추를 선택할 수 있습니다. 사용자가 메일을 분류하고 보호하도록 하려면 이 단추를 추가하는 대신 [보호용 레이블을 구성](configure-policy-protection.md)하고 Outlook에 대한 사용자 정의 권한을 구성하는 것이 좋습니다. 이 보호 설정은 기능적으로 **전달 금지** 단추를 선택하는 것과 동일하지만 레이블에 이 기능이 포함되어 있으면 메일이 분류 및 보호됩니다.
    
    고급 클라이언트 설정을 사용하여 이 정책 설정을 [클라이언트 사용자 지정](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook)으로 구성할 수도 있습니다.
    
    - **Make the custom permissions option available to users**(사용자에게 사용자 지정 권한 옵션 제공): 이 설정이 켜져 있으면 사용자가 사용자 지정 보호 설정을 지정하고 레이블 구성에 포함된 정책 설정을 재정의할 수 있습니다. 이 설정이 꺼져 있으면 사용자가 사용자 지정 권한 옵션을 선택할 수 없습니다.
        
        > [!IMPORTANT]
        > 현재 미리 보기 버전의 클라이언트를 사용하지 않는 한 Word, Excel, PowerPoint 및 파일 탐색기의 사용자 정의 권한에 대해 구성된 레이블이 있는 경우 **끄기** 설정을 사용하지 마세요. 이 옵션을 사용할 경우 레이블이 적용되면 사용자 지정 권한을 구성하라는 메시지가 사용자에게 표시되지 않습니다. 결과는 문서에 레이블이 지정되지만, 문서가 의도한 대로 보호되지 않습니다.
        
        이 정책 설정은 Office 메뉴 옵션에서 구성할 수 있는 사용자 지정 권한에는 적용되지 않습니다. 하지만 고급 클라이언트 설정을 사용하여 이 정책 설정을 [클라이언트 사용자 지정](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users)으로 구성할 수도 있습니다.
        
        사용자 지정 권한 옵션은 다음과 같은 위치에 있습니다.
        
        - Office 응용 프로그램: 리본에서 **홈** 탭 > **보호** 그룹 > **보호** > **사용자 지정 권한**
        
        - 파일 탐색기: 마우스 오른쪽 단추 클릭 > **분류 및 보호** > **사용자 지정 권한**
    
    - **Azure Information Protection 클라이언트 "추가 정보" 웹 페이지에 대한 사용자 지정 URL 제공**: 사용자가 Office 응용 프로그램의 **홈** 탭에서 **보호** > **도움말 및 피드백**을 선택할 때 **Microsoft Azure Information Protection** 대화 상자의 **도움말 및 피드백** 섹션에 이 링크가 표시됩니다. 기본적으로 이 링크를 누르면 [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection) 웹 사이트로 이동됩니다. 이 링크로 다른 웹 페이지로 이동하려면 HTTP 또는 HTTPS(권장) URL을 입력할 수 있습니다. 입력한 사용자 URL이 액세스 가능하거나 모든 장치에 올바로 표시되는지 확인하는 작업은 수행되지 않습니다.
        
        예를 들어 지원 센터의 경우 클라이언트 설치 및 사용 방법에 대한 정보(**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) 또는 릴리스 버전 정보(**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**)를 포함하는 Microsoft 설명서 페이지를 입력할 수 있습니다. 또는 사용자가 지원 센터에 문의할 때 필요한 정보를 포함하는 자체 웹 페이지나 구성한 레이블을 사용하는 방법을 단계별로 안내하는 비디오를 게시할 수 있습니다.

3. 변경 내용을 저장하려면 **Save**(저장)를 클릭합니다.

4. 변경 내용을 사용자에게 제공하려면 초기 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
