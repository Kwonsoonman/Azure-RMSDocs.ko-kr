---
title: "Azure Information Protection 정책의 템플릿 구성 및 관리"
description: "현재 미리 보기로 제공되지만, 이제 Azure Information Protection 정책에서 권한 관리 템플릿을 구성하고 관리할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 1f41aad2d132e087e9122b2683be4b45185527de
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-and-managing-templates-in-the-azure-information-protection-policy"></a>Azure Information Protection 정책의 템플릿 구성 및 관리

>*적용 대상: Azure Information Protection*

>[!NOTE]
>이 기능은 현재 미리 보기로 제공되며 자주 변경될 수 있습니다.
>
>Azure 클래식 포털에서 만든 사용자 지정 템플릿을 사용하여 이 미리 보기 기능을 테스트하기 전에 템플릿의 최신 백업이 있는지 확인하는 것이 좋습니다. [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) PowerShell cmdlet을 사용하여 사용자 지정 템플릿을 백업할 수 있으며 필요한 경우 [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate)을 사용하여 복원할 수 있습니다.
>
>구현의 차이 때문에, Azure 클래식 포털 및 Azure Portal에서 동일한 템플릿을 관리하는 것은 권장되지 않습니다.


권한 관리 템플릿은 이제 Azure Information Protection 정책과 통합됩니다. 

**분류, 레이블 지정 및 보호(Azure Information Protection P1 또는 P2)를 포함하는 구독이 있는 경우:**

- 테넌트에 대한 권한 관리 템플릿은 레이블 다음의 새 **템플릿** 섹션에 표시됩니다. 이러한 템플릿을 레이블로 변환하거나 계속해서 별도 템플릿으로 관리하고 레이블에 대한 보호를 구성할 때 연결할 수 있습니다. 

**보호만 포함하는 구독(Azure 권한 관리 서비스를 포함하는 Office 365 구독)이 있는 경우:**

- 테넌트에 대한 권한 관리 템플릿은 레이블로 표시되며, 현재 분류 및 레이블 지정에 관련된 구성 설정도 사용할 수 있습니다. 


## <a name="considerations-for-templates-in-the-azure-portal"></a>Azure Portal의 템플릿 고려 사항

이러한 템플릿을 편집하거나 Azure Portal에서 레이블로 변환하기 전에 Azure 클래식 포털에서 템플릿을 관리할 때와는 달라진 다음과 같은 구현 방식을 이해해야 합니다. 미리 보기 동안 다음과 같은 몇 가지 제한 사항이 해결될 것으로 예상됩니다.

- 템플릿을 편집하거나 변환하고 Azure Information Protection 정책을 저장한 후에 원래 [사용 권한](configure-usage-rights.md)이 다음과 같이 변경됩니다. 필요한 경우 PowerShell에서 [New-aadrmrightsdefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) 및 [Set-aadrmtemplateproperty](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet을 사용하여 개별 사용 권한을 추가하거나 제거할 수 있습니다.
    
    - **다른 이름으로 저장, 내보내기**(일반 이름)이 제거되었습니다. Azure Portal에서는 이 사용 권한을 수동으로 지정할 수 없으며, 해당되는 경우 추가할 수 있는 모든 권한 사용 권한에 포함되어 있습니다.
    
    - **매크로 허용**(일반 이름)이 자동으로 추가됩니다. 이 사용 권한은 Office 앱의 Azure Information Protection 표시줄에 필요합니다.
    
- 현재 기본 템플릿이 표시되지만 편집하거나 변환할 수 없습니다. 

- 템플릿을 복사하거나 삭제할 수 없습니다. 템플릿을 제거하려면 PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) cmdlet을 사용합니다. 

- 현재, Azure 클래식 포털 또는 PowerShell을 사용하여 언어에 대해 구성된 템플릿은 이름 및 설명을 해당 언어로 표시하지 않고 그대로 유지됩니다.

- **게시됨** 및 **보관됨** 설정은 **레이블** 블레이드에서 각각 **사용**: **설정** 및 **사용**: **해제**로 표시됩니다.

- 부서별 템플릿(범위별로 구성된 템플릿)은 전역 정책에 표시됩니다. 현재, 부서별 템플릿을 편집하고 저장하면 범위 구성이 제거됩니다. Azure Information Protection 정책에서 범위가 지정된 템플릿은 [범위 정책](configure-policy-scope.md)입니다. 템플릿을 레이블로 변환하는 경우 기존 범위를 선택할 수 있습니다.
    
    또한 현재는 부서별 템플릿에 대한 응용 프로그램 호환성 설정을 지정할 수 없습니다. 필요한 경우 PowerShell에서 [Set-aadrmtemplateproperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet을 사용하여 이 설정을 지정할 수 있습니다.

- **템플릿** 컨테이너에서 새 템플릿을 만들지 않도록 하고, 대신 **보호** 설정이 있는 레이블을 만들고 **보호** 블레이드에서 사용 권한 및 설정을 구성합니다. 전체 지침은 [새 템플릿을 만들려면](#to-create-a-new-template)을 참조하세요.

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Azure Information Protection 정책에서 템플릿을 구성하려면

1. 새 브라우저 창에서 보안 관리자나 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. **Azure Information Protection** 블레이드로 이동합니다. 예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information Protection**을 입력합니다. 결과에서 **Azure Information Protection**을 선택합니다. 

2. 구성하려는 템플릿을 모든 사용자에게 적용하려는 경우 **Azure Information Protection** 블레이드에서 **Global**을 선택합니다. 그러나 구성하려는 템플릿이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 대신 해당 범위 지정 정책을 선택합니다.

3. 정책 블레이드에서 구성하려는 템플릿을 찾습니다.
    
    - 분류, 레이블 지정 및 보호를 포함하는 구독이 있는 경우 레이블 다음에 있는 **템플릿**을 확장합니다.
    
    - 보호만 포함된 구독이 있는 경우에는 템플릿이 레이블로 표시됩니다.

4. 템플릿을 선택하고 **레이블** 블레이드에서 필요한 경우 **레이블 이름** 및 **설명**합니다을 편집하여 템플릿 이름 및 설명을 변경할 수 있습니다. 그런 다음 값이 **Azure RMS**인 **보호**를 선택하여 **보호** 블레이드를 엽니다.

5. **보호** 블레이드에서 권한, 콘텐츠 만료 및 오프라인 액세스 설정을 변경할 수 있습니다. 보호 설정 구성에 대한 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.
    
    **확인**을 클릭하여 변경 내용을 유지하고 **레이블** 블레이드에서 **저장**을 클릭합니다.

6. 사용자 응용 프로그램 및 서비스에 변경 내용을 적용하려면 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.

## <a name="to-convert-templates-to-labels"></a>템플릿을 레이블로 변환하려면

분류, 레이블 지정 및 보호를 포함하는 구독이 있는 경우 템플릿을 레이블로 변환할 수 있습니다. 이 작업을 수행하는 경우 원본 템플릿은 유지되지만 Azure Portal에서 템플릿이 새 레이블에 포함된 것으로 표시됩니다.

예를 들어 마케팅 그룹에 대한 사용 권한을 부여하는 **Marketing**이라는 레이블을 변환하는 경우 Azure Portal에서 같은 보호 설정이 지정된 **Marketing**이라는 레이블로 표시됩니다. 새로 생성된 레이블에서 보호 설정을 변경하면 템플릿에서 변경을 수행하는 것이므로 이 템플릿을 사용하는 모든 사용자 또는 서비스는 다음 번에 템플릿을 새로 고칠 때 새 보호 설정이 적용됩니다. 

모든 템플릿을 레이블로 변환해야 하는 것은 아니지만 이렇게 하는 경우 보호 설정이 레이블의 전체 기능과 완전히 통합되므로 설정을 따로 유지 관리할 필요가 없습니다.

템플릿을 레이블로 변환하려면 해당 템플릿을 마우스 오른쪽 단추로 클릭하고 **레이블로 변환**을 선택합니다. 또는 상황에 맞는 메뉴를 사용하여 이 옵션을 선택합니다.

템플릿을 레이블로 변환할 경우:

- 템플릿의 이름이 새 레이블 이름으로 변환되고 템플릿 설명이 레이블 도구 설명으로 변환됩니다. 

- 템플릿의 상태가 게시되면 이 설정은 레이블에 대한 **사용**: **설정**으로 매핑됩니다. 그러면 다음 번에 Azure Information Protection 정책을 게시할 때 사용자에게 이 레이블로 표시됩니다. 템플릿의 상태가 보관된 경우 이 설정은 레이블에 대해 **사용**: **해제**로 매핑되며 사용자에게 사용 가능한 레이블로 표시되지 않습니다.

- 보호 설정은 유지되며, 필요한 경우 이러한 설정을 편집할 수 있고 시각적 표식 및 조건 같은 기타 레이블 설정을 추가할 수도 있습니다.

- 원본 템플릿은 더 이상 **템플릿** 아래에 표시되지 않으며, Azure Portal에서 편집하려는 경우 생성된 레이블을 편집해야 합니다. 템플릿은 Azure 권한 관리 서비스에 계속 사용할 수 있으며 [PowerShell 명령](administer-powershell.md)을 사용하여 계속 관리할 수 있습니다.  

## <a name="to-create-a-new-template"></a>새 템플릿을 만들려면

보호 설정 **Azure RMS**를 사용하여 새 레이블을 만들 경우 내부적으로 새 사용자 지정 템플릿이 만들어진 다음 권한 관리 템플릿과 통합되는 서비스 및 응용 프로그램에서 액세스될 수 있습니다.

1. 만들려는 새 템플릿이 모든 사용자에게 적용될 경우 **정책: 글로벌** 블레이드에서 **새 레이블 추가**를 클릭합니다.
    
     만들려는 새 템플릿을 선택한 사용자에게만 적용되는 부서별 템플릿인 경우 초기 **Azure Information Protection** 블레이드에서 해당 범위 정책을 먼저 선택하거나 만듭니다.

2. **레이블** 블레이드에서 이 새 템플릿을 게시하려면 기본값인 **사용**: **설정**을 그대로 두고, 템플릿을 보관된 상태로 만들려면 **해제**로 변경합니다. 그런 후 템플릿 이름 및 설명으로 레이블 이름과 설명을 입력합니다.

3. **이 레이블을 포함하는 문서 및 메일에 대한 권한 설정**에서 **보호**를 선택하고 **보호**를 선택합니다.
    
     ![Azure Information Protection 레이블에 대한 보호 구성](../media/info-protect-protection-bar.png)

4. **보호** 블레이드에서 권한, 콘텐츠 만료 및 오프라인 액세스 설정을 변경할 수 있습니다. 이러한 보호 설정 구성에 대한 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.
    
    **확인**을 클릭하여 변경 내용을 유지하고 **레이블** 블레이드에서 **저장**을 클릭합니다.

5. 이러한 템플릿을 사용자 응용 프로그램 및 서비스에서 사용할 수 있게 하려면 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.


## <a name="next-steps"></a>다음 단계

모든 Azure Information Protection 정책 변경과 마찬가지로, Azure Information Protection 클라이언트를 실행하는 컴퓨터에서 이러한 템플릿의 다운로드를 완료하는 데 최대 15분이 걸릴 수 있습니다. 컴퓨터 및 서비스가 템플릿을 다운로드하고 새로 고치는 방법에 대한 자세한 내용은 [사용자 및 서비스를 위한 템플릿 새로 고침](refresh-templates.md)을 참조하세요.

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
