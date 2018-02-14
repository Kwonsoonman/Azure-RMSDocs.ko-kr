---
title: "Azure Information Protection의 템플릿 구성 및 관리"
description: "Azure Portal에서 Rights Management 템플릿을 구성 및 관리합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 671d1d5d706225fcd5c680ddc8687aa889b59b59
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Azure Information Protection의 템플릿 구성 및 관리

>*적용 대상: Azure Information Protection*

>[!NOTE]
>이 기능은 Azure 클래식 포털의 사용자 지정 템플릿 구성을 대체합니다. 클래식 포털은 사용 중지되었으며, 따라서 Azure Portal을 사용해야 합니다. 방법을 신속하게 매핑하려면 [Azure 클래식 포털과 관련된 작업](migrate-portal.md)을 참조하세요.


Rights Management 템플릿은 이제 Azure Information Protection 정책과 통합되었습니다. 

**분류, 레이블 지정 및 보호가 포함된 구독(Azure Information Protection P1 또는 P2)을 갖고 있는 경우:**

- 테넌트에 대한 레이블과 통합되지 않은 Rights Management 템플릿은 **Azure Information Protection - 전역 정책** 블레이드에서 레이블 뒤에 있는 **보호 템플릿** 섹션에 표시됩니다. 이러한 템플릿을 레이블로 변환하거나, 레이블에 대한 보호를 구성할 때 템플릿에 연결할 수 있습니다. 

**보호만 포함된 구독(Azure Rights Management 서비스를 포함하는 Office 365 구독)을 갖고 있는 경우:**

- 테넌트에 대한 Rights Management 템플릿은 **Azure Information Protection - 글로벌 정책** 블레이드의 **보호 템플릿** 섹션에 표시됩니다. 레이블은 표시되지 않습니다. 분류 및 레이블 지정과 관련된 구성 설정도 표시되지만, 이러한 설정은 템플릿에 영향을 주지 않거나 구성할 수 없습니다. 

## <a name="default-templates"></a>기본 템플릿

Azure Rights Management 서비스를 포함하는 Azure Information Protection 또는 Office 365 구독에 대한 구독을 받을 때 테넌트에 대한 두 개의 기본 템플릿이 자동으로 생성됩니다. 이러한 템플릿은 액세스를 조직의 권한 있는 사용자로 제한합니다. 생성된 템플릿은 [Azure Rights Management에 대한 사용 권한 구성](configure-usage-rights.md#rights-included-in-the-default-templates) 설명서에 나열된 권한을 갖습니다.

또한 7일간 오프라인 액세스를 허용하도록 구성되며 만료 날짜가 없습니다.

>[!NOTE]
> 이러한 설정과 기본 템플릿의 이름 및 설명을 변경할 수 있습니다. 이 기능은 Azure 클래식 포털에서는 불가능했으며 PowerShell에서는 여전히 지원되지 않습니다.

이러한 기본 템플릿을 사용하면 손쉽게 조직의 중요한 데이터를 즉시 보호할 수 있습니다. 이러한 템플릿을 Azure Information Protection 레이블과 함께 사용할 수도 있고, Rights Management 템플릿을 사용할 수 있는 [응용 프로그램 및 서비스](../understand-explore/applications-support.md)와 함께 단독으로 사용할 수도 있습니다.

개발자 고유의 사용자 지정 템플릿을 만들 수도 있습니다. 템플릿이 아주 많이 필요하지는 않겠지만, 최대 500개의 사용자 지정 템플릿을 Azure에 저장할 수 있습니다.

### <a name="default-template-names"></a>기본 템플릿 이름

최근에 구독을 획득한 경우 다음과 같은 이름의 기본 템플릿이 생성됩니다.

- **Confidential \ All Employees** - 보호되는 콘텐츠에 대한 읽기 및 수정 권한을 부여합니다.

- **Highly Confidential \ All Employees** - 보호되는 콘텐츠에 대한 읽기 전용 권한을 부여합니다.

얼마 전에 구독을 획득한 경우 다음과 같은 이름의 기본 템플릿이 생성됩니다.

- **\<organization name> - Confidential** - 보호되는 콘텐츠에 대한 읽기 및 수정 권한을 부여합니다.

- **\<organization name> - Confidential View Only** - 보호되는 콘텐츠에 대한 읽기 전용 권한을 부여합니다. 

Azure Portal을 사용할 때 이러한 기본 템플릿의 이름을 변경(그리고 다시 구성)할 수 있습니다.

>[!NOTE]
>**Azure Information Protection - 전역 정책** 블레이드에 기본 템플릿이 보이지 않으면 레이블로 변환되었거나 레이블에 연결된 것입니다. 여전히 템플릿으로 존재하지만, Azure Portal에서는 Azure RMS 보호를 포함하는 레이블 구성의 일부로 보입니다. 언제든지 [AADRM PowerShell 모듈](administer-powershell.md)에서 [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)을 실행하여 테넌트의 템플릿을 확인할 수 있습니다.
>
>뒤에 나오는 [템플릿을 레이블로 변환하려면](#to-convert-templates-to-labels) 섹션의 설명에 따라 수동으로 템플릿을 변환한 후 원하는 대로 이름을 변경할 수 있습니다. 또는 기본 Azure Information Protection 정책이 최근에 만들어졌고 테넌트에 대한 Azure Rights Management 서비스가 해당 시점에 활성화된 경우 템플릿이 자동으로 변환됩니다.

보관된 템플릿은 **Azure Information Protection - 전역 정책** 블레이드에서 사용할 수 없는 것으로 표시됩니다. 이러한 템플릿은 레이블에 대해 선택할 수 없지만 레이블로 변환할 수 있습니다.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Azure Portal에서 템플릿에 대해 고려할 사항

이러한 템플릿을 편집하거나 레이블로 변환하기 전에 다음과 같은 변경 내용 및 고려 사항을 숙지해야 합니다. 구현 변경으로 인해 이전에 Azure 클래식 포털에서 템플릿을 관리한 경우 다음 목록이 특히 중요합니다.

- 템플릿을 편집 또는 변환하고 Azure Information Protection 정책을 저장하면 다음과 같은 변경 내용이 원래 [사용 권한](configure-usage-rights.md)에 적용됩니다. 필요한 경우 Azure Portal을 사용하여 개별 사용 권한을 추가 또는 제거할 수 있습니다. 또는 [New-AadrmRightsDefinition](/powershell/module/aadrm/set-aadrmtemplateproperty) 및 [Set-AadrmTemplateProperty](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet과 함께 PowerShell을 사용합니다.
    
    - **Allow Macros**(일반 이름)가 자동으로 추가됩니다. 이 사용 권한은 Office 앱의 Azure Information Protection 표시줄에 필요합니다.

- **게시된** 설정과 **보관된** 설정은 각각 **레이블** 블레이드에서 **사용**: **켜짐** 및 **사용**: **꺼짐**으로 표시됩니다. 템플릿을 계속 유지하되, 사용자 또는 서비스에서 볼 수 없게 하려면 **사용**: **꺼짐**으로 설정합니다.

- Azure Portal에서는 템플릿을 복사 또는 삭제할 수 없습니다. 템플릿이 레이블로 변환되면 **이 레이블을 포함하는 문서 및 이메일에 대한 권한 설정** 옵션으로 **구성되지 않음**을 선택하여 템플릿 사용을 중지하도록 레이블을 구성할 수 있습니다. 또는 레이블을 삭제할 수 있습니다. 그러나 두 시나리오 모두 템플릿이 삭제되지 않고 보관된 상태로 유지됩니다.
    
    이제 PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) cmdlet을 사용하여 템플릿을 삭제할 수 있습니다. 또한 레이블로 변환되지 않은 템플릿에 이 PowerShell cmdlet을 사용할 수 있습니다. 그러나 콘텐츠 보호에 사용된 템플릿을 삭제하면 해당 콘텐츠를 더 이상 열 수 없습니다. 템플릿이 프로덕션 환경에서 문서 또는 이메일을 보호하는 데 사용되지 않은 것이 확실한 경우에만 템플릿을 삭제하세요. 예방 조치로, [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) cmdlet을 사용하여 우선 템플릿을 백업으로 내보내는 방안을 고려해 볼 수 있습니다. 

- 부서별 템플릿(범위에 대해 구성된 템플릿)은 전역 정책에 표시됩니다. 현재는 부서별 템플릿을 편집하고 저장하면 범위 구성이 제거됩니다. Azure Information Protection에서 범위 지정 템플릿에 해당하는 것은 [범위 지정 정책](configure-policy-scope.md)입니다. 템플릿을 레이블로 변환하면 기존 범위를 선택할 수 있습니다.
    
    또한 현재는 부서별 템플릿에 대한 응용 프로그램 호환성 설정을 지정할 수 없습니다. 필요한 경우 [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet 및 *EnableInLegacyApps* 매개 변수를 사용하여 응용 프로그램 호환성 설정을 지정할 수 있습니다.

- 템플릿을 변환하거나 레이블에 연결하면 더 이상 다른 레이블에서 사용할 수 없습니다. 또한 이 템플릿은 더 이상 **보호 템플릿** 섹션에 표시되지 않습니다. 

- **보호 템플릿** 섹션에서 새 템플릿을 만들지 마세요. 그 대신, **보호** 설정이 있는 레이블을 만들고, **보호** 블레이드에서 사용 권한 및 설정을 구성하세요. 전체 지침은 [새 템플릿 만들기](#to-create-a-new-template)를 참조하세요.

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Azure Information Protection 정책에서 템플릿을 구성하려면

1. 아직 구성하지 않은 경우 새 브라우저 창을 열고 보안 관리자 또는 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. 그리고 **Azure Information Protection** 블레이드로 이동합니다.     
    
    예를 들어 허브 메뉴에서 **더 많은 서비스**를 클릭하고, [필터] 상자에서 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 템플릿이 모든 사용자에게 적용되는 경우 **Azure Information Protection - 전역 정책** 블레이드에 그대로 있습니다.
    
    구성하려는 템플릿이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그런 다음, **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

3. **Azure Information Protection - 전역 정책** 블레이드 또는 **정책:\<이름>** 블레이드에서 구성하려는 템플릿을 찾습니다.
    
    - 분류, 레이블 지정 및 보호가 포함된 구독을 갖고 있는 경우 레이블 뒤에서 **보호 템플릿**을 확장합니다.
    
    - 보호만 포함된 구독을 갖고 있는 경우 템플릿이 레이블로 표시됩니다.

4. 템플릿을 선택하고, 필요한 경우 **레이블** 블레이드에서 **레이블 표시 이름** 및 **설명**을 편집하여 템플릿 이름 및 설명을 변경할 수 있습니다. 그런 다음, **Azure(클라우드 키)** 값이 있는 **보호**를 선택하여 **보호** 블레이드를 엽니다.

5. **보호** 블레이드에서 권한, 콘텐츠 만료 및 오프라인 액세스 설정을 변경할 수 있습니다. 보호 설정 구성에 대한 자세한 내용은 [Rights Management 보호에 대해 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.
    
    **확인**을 클릭하여 변경 내용을 유지하고, **레이블** 블레이드에서 **저장**을 클릭합니다.

6. 변경 내용을 사용자 응용 프로그램 및 서비스에 제공하려면 초기 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.

> [!NOTE]
> 또한 미리 정의된 템플릿을 사용하도록 레이블을 구성한 경우 **보호** 블레이드에서 **템플릿 편집** 단추를 사용하여 템플릿을 편집할 수 있습니다. 선택한 템플릿을 사용하는 다른 레이블이 없는 경우 이 단추는 템플릿을 레이블로 변환하고, 5단계로 이동합니다. 템플릿이 레이블로 변환될 때 발생하는 일에 대한 자세한 내용은 다음 섹션을 참조하세요.

## <a name="to-convert-templates-to-labels"></a>템플릿을 레이블로 변환하려면

분류, 레이블 지정 및 보호가 포함된 구독을 갖고 있는 경우 템플릿을 레이블로 변환할 수 있습니다. 템플릿을 변환하면 원래 템플릿은 유지되기는 하지만, 이제부터는 Azure Portal에서 새 레이블에 포함된 것으로 표시됩니다.

예를 들어 마케팅 그룹에 사용 권한을 부여하는 **마케팅**이라는 레이블을 변환하면 Azure Portal에서 동일한 보호 설정을 갖고 있는 **마케팅**이라는 레이블로 표시됩니다. 새로 생성된 레이블에서 보호 설정을 변경하면 템플릿에서도 변경되고, 이 템플릿을 사용하는 사용자 또는 서비스는 다음 번 새로 고침 때 새로운 보호 설정을 가져오게 됩니다. 

모든 템플릿을 레이블로 변환할 필요는 없지만, 이렇게 하면 보호 설정이 레이블의 전체 기능과 완전히 통합되므로 설정을 별도로 유지할 필요가 없습니다.

템플릿을 레이블로 변환하려면 템플릿을 마우스 오른쪽 단추로 클릭하고 **레이블로 변환**을 선택합니다. 또는 상황에 맞는 메뉴를 사용하여 이 옵션을 선택합니다. 

보호할 레이블과 미리 정의된 템플릿을 구성할 때 **템플릿 편집** 단추를 사용하여 템플릿을 레이블로 변환할 수도 있습니다. 

템플릿을 레이블로 변환하면:

- 템플릿 이름이 새 레이블 이름으로 변환되고, 템플릿 설명은 레이블 도구 설명으로 변환됩니다. 

- 템플릿 상태가 게시된 경우 이 설정이 레이블의 **사용**: **켜짐**으로 매핑되고, 다음에 Azure Information Protection 정책을 게시할 때 사용자에게 이 레이블로 표시됩니다. 템플릿 상태가 보관된 경우 이 설정은 레이블의 **사용**: **꺼짐**으로 매핑되고, 사용자에게 사용 가능한 레이블로 표시되지 않습니다.

- 보호 설정이 유지되며, 필요한 경우 보호 설정을 편집하고 시각적 표식 및 조건 같은 다른 레이블을 추가할 수도 있습니다.

- 원본 템플릿은 더 이상 **보호 템플릿**에 표시되지 않으며, 레이블에 대한 보호를 구성할 때 미리 정의된 템플릿으로 선택할 수 없습니다. Azure Portal에서 이 템플릿을 편집하려면 템플릿을 변환할 때 생성된 레이블을 편집합니다. 템플릿은 Azure Rights Management 서비스에 계속 사용할 수 있으며, [PowerShell 명령](administer-powershell.md)을 사용하여 계속 관리할 수 있습니다.  

## <a name="to-create-a-new-template"></a>새 템플릿을 만들려면

**Azure RMS** 또는 **Azure(클라우드 키)**의 보호 설정을 사용하여 새 레이블을 만들면 내부에서는 Rights Management 템플릿과 통합되는 서비스 및 응용 프로그램에서 액세스할 수 있는 새 사용자 지정 템플릿이 생성됩니다.

1. 새 템플릿이 모든 사용자에게 적용되는 경우 **Azure Information Protection - 전역 정책** 블레이드에 그대로 있습니다.
    
     새 템플릿이 선택한 사용자에게만 적용되는 부서별 템플릿인 경우 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그리고 **Azure Information Protection - 범위 지정 정책** 블레이드에서 [범위 지정 정책](configure-policy-scope.md)을 만들거나 선택합니다.

2. **Azure Information Protection - 전역 정책** 블레이드 또는 **정책:\<이름>** 블레이드에서 **새 레이블 추가**를 클릭합니다.

3. **레이블** 블레이드에서, 이 새 템플릿을 게시하려면 기본값인 **사용**: **켜짐**을 그대로 유지하고, 보관되는 템플릿으로 만들려면 이 설정을 **꺼짐**으로 변경합니다. 그리고 템플릿 이름 및 설명에 대한 레이블 이름 및 설명을 입력합니다.

4. **이 레이블을 포함하는 문서 및 이메일에 대한 권한 설정**에서 **보호**를 선택하고 다시 **보호**를 선택합니다.
    
     ![Azure Information Protection 레이블에 대한 보호 구성](../media/info-protect-protection-bar-configured.png)

5. **보호** 블레이드에서 권한, 콘텐츠 만료 및 오프라인 액세스 설정을 변경할 수 있습니다. 이러한 보호 설정 구성에 대한 자세한 내용은 [Rights Management 보호에 대해 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.
    
    **확인**을 클릭하여 변경 내용을 유지하고, **레이블** 블레이드에서 **저장**을 클릭합니다.

6. 이러한 템플릿을 사용자 응용 프로그램 및 서비스에 제공하려면 초기 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.


## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책의 모든 변경 내용과 마찬가지로, Azure Information Protection 클라이언트를 실행하는 컴퓨터가 템플릿 다운로드를 완료할 때까지 최대 15분이 걸릴 수 있습니다. 컴퓨터와 서비스에서 템플릿을 다운로드하고 새로 고치는 방법에 대한 자세한 내용은 [사용자 및 서비스를 위한 템플릿 새로 고침](refresh-templates.md)을 참조하세요.

템플릿을 만들고 관리하기 위해 Azure Portal에서 구성할 수 있는 모든 작업은 PowerShell을 사용하여 수행할 수 있습니다. 또한 PowerShell은 포털에 없는 옵션을 제공합니다. 자세한 내용은 [보호 템플릿에 대한 PowerShell 참조](configure-templates-with-powershell.md)를 참조하세요. 

Azure Information Protection 정책을 구성하는 방법에 대한 자세한 내용은 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션에 있는 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
