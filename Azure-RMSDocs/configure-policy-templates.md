---
title: Azure Information Protection의 템플릿 구성 및 관리 - AIP
description: Azure Portal에서 권한 관리 템플릿을 구성하고 관리합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/29/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8301aabb-047d-4892-935c-7574f6af8813
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 1571939554e64459acd7ec0b7c32e9d40f7bd7eb
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024317"
---
# <a name="configuring-and-managing-templates-for-azure-information-protection"></a>Azure Information Protection의 템플릿 구성 및 관리

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Rights Management 템플릿이라고도 하는 보호 템플릿은 Azure Information Protection에 대한 관리자 정의 보호 설정의 그룹입니다. 이러한 설정에는 권한이 있는 사용자에 대해 선택한 [사용 권한](configure-usage-rights.md), 만료 및 오프라인 액세스에 대한 액세스 제어 등이 포함됩니다. 이러한 템플릿은 Azure Information Protection 정책과 통합됩니다. 

**분류, 레이블 지정 및 보호(Azure Information Protection P1 또는 P2)를 포함하는 구독이 있는 경우:**

- 테넌트의 레이블과 통합되지 않는 템플릿이 **Azure Information Protection - 레이블** 블레이드의 레이블 다음에 **보호 템플릿** 섹션에 표시됩니다. 이 블레이드로 이동하려면 **분류** > **레이블** 메뉴 옵션을 선택합니다. 이러한 템플릿을 레이블로 변환하거나 레이블에 대한 보호를 구성할 때 레이블에 연결할 수 있습니다. 

**보호만 포함하는 구독(Azure 권한 관리 서비스를 포함하는 Office 365 구독)이 있는 경우:**

- 테넌트의 템플릿이 **Azure Information Protection - 레이블** 블레이드의 **보호 템플릿** 섹션에 표시됩니다. 이 블레이드로 이동하려면 **분류** > **레이블** 메뉴 옵션을 선택합니다. 레이블이 표시되지 않습니다. 분류 및 레이블링에 특정한 구성 설정도 표시되지만, 이러한 설정이 템플릿에 영향을 미치지 않거나 구성할 수 없습니다. 

>[!NOTE]
>일부 응용 프로그램 및 서비스에서는 [전달 금지](configure-usage-rights.md#do-not-forward-option-for-emails) 및 [암호화 전용](configure-usage-rights.md#encrypt-only-option-for-emails)(또는 **암호화**)이 템플릿으로 표시될 수 있습니다. 이러한 템플릿은 편집하거나 삭제할 수 없지만 기본적으로 Exchange 서비스와 함께 제공되는 옵션입니다.

## <a name="default-templates"></a>기본 템플릿

Azure Information Protection의 구독 또는 Azure Rights Management 서비스를 포함하는 Office 365 구독을 얻을 때, 두 개의 기본 템플릿이 테넌트용으로 자동 생성됩니다. 이러한 템플릿은 조직에서 권한 있는 사용자만 액세스할 수 있도록 제한합니다. 이러한 템플릿을 만드는 경우 [Azure Rights Management에 대한 사용 권한 구성](configure-usage-rights.md#rights-included-in-the-default-templates) 설명서에 나열되어 있는 사용 권한을 갖게 됩니다.

또한 템플릿은 7일간 오프라인 액세스를 허용하도록 구성되며 만료 날짜가 없습니다.

>[!NOTE]
> 이러한 설정과 기본 템플릿의 이름 및 설명을 변경할 수 있습니다. 이 기능은 Azure 클래식 포털에서는 사용할 수 없었으며 PowerShell에는 계속 지원되지 않습니다.

이러한 기본 템플릿을 사용하면 사용자 및 다른 사용자가 조직의 중요한 데이터 보호를 즉시 쉽게 시작할 수 있습니다. 이러한 템플릿은 Azure Information Protection 레이블과 함께 사용하거나 Rights Management 템플릿을 사용할 수 있는 [응용 프로그램과 서비스](applications-support.md)에서 단독으로 사용할 수 있습니다.

사용자 지정 템플릿을 직접 만들 수도 있습니다. 대체로 몇 개의 템플릿만 필요하지만 Azure에는 최대 500개의 사용자 지정 템플릿이 저장되어 있을 수 있습니다.


### <a name="default-template-names"></a>기본 템플릿 이름

최근에 구독을 얻은 경우 기본 템플릿은 다음과 같은 이름으로 만들어집니다.

- **Confidential \ All Employees** - 보호된 콘텐츠의 읽기 및 수정 권한이 있습니다.

- **Highly Confidential \ All Employees** - 보호된 콘텐츠의 읽기 전용 권한이 있습니다.

최근에 구독을 얻은 경우 기본 템플릿은 다음과 같은 이름으로 만들어집니다.

- **\<조직 이름> - 기밀** - 보호된 콘텐츠의 읽기 및 수정 권한이 있습니다.

- **\<조직 이름> - 기밀 보기 전용** - 보호된 콘텐츠의 읽기 전용 권한이 있습니다. 

Azure Portal을 사용할 경우 이러한 기본 템플릿의 이름을 바꾸고 다시 구성할 수 있습니다.

>[!NOTE]
>**Azure Information Protection - 레이블** 블레이드에 기본 템플릿이 표시되지 않으면 레이블로 변환되었거나 레이블에 연결된 것입니다. 레이블은 템플릿으로 여전히 존재하지만 Azure Portal에서는 클라우드 키의 보호 설정을 포함하는 레이블 구성의 일부로 표시됩니다. [AADRM PowerShell 모듈](administer-powershell.md)에서 [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)을 실행하여 항상 테넌트에 있는 템플릿을 확인할 수 있습니다.
>
>다음 섹션 [템플릿을 레이블로 변환](#to-convert-templates-to-labels)에 설명된 대로 템플릿을 수동으로 변환한 다음 원하는 경우 이름을 바꿀 수 있습니다. 또는 최근에 기본 Azure Information Protection 정책을 만들었거나 해당 시기에 사용자 테넌트에 대해 Azure Rights Management 서비스를 활성화한 경우 템플릿이 자동으로 변환됩니다.

보관된 템플릿은 **Azure Information Protection - 레이블** 블레이드에서 사용 불가능으로 표시됩니다. 이러한 템플릿은 레이블용으로 선택할 수 없지만 레이블로 전환할 수는 있습니다.

## <a name="considerations-for-templates-in-the-azure-portal"></a>Azure Portal의 템플릿 고려 사항

이러한 템플릿을 편집하거나 레이블로 변환하기 전에 다음 변경 사항과 고려 사항을 인지하고 있는지 확인합니다. 구현이 변경되었으므로, Azure 클래식 포털에서 이전에 템플릿을 관리한 경우 다음 목록이 특히 중요합니다.

- 템플릿을 편집하거나 변환하고 Azure Information Protection 정책을 저장한 후에 원래 [사용 권한](configure-usage-rights.md)이 다음과 같이 변경됩니다. 필요한 경우 Azure Portal을 사용하여 개별 사용 권한을 추가하거나 제거할 수 있습니다. 또는 [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) 및 [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet과 함께 PowerShell을 사용합니다.
    
    - **매크로 허용**(일반 이름)이 자동으로 추가됩니다. 이 사용 권한은 Office 앱의 Azure Information Protection 표시줄에 필요합니다.

- **게시됨** 및 **보관됨** 설정은 **레이블** 블레이드에서 각각 **사용**: **설정** 및 **사용**: **해제**로 표시됩니다. 유지하고 싶지만 사용자나 서비스에 표시되지 않는 템플릿의 경우 해당 템플릿을 **사용**: **끄기**로 설정합니다.

- Azure 포털에서 템플릿을 복사하거나 삭제할 수 없습니다. 템플릿이 레이블로 변환되면 **이 레이블을 포함하는 문서와 메일의 권한 설정** 옵션을 **구성되지 않음**으로 선택하여 템플릿 사용을 중지하도록 레이블을 구성할 수 있습니다. 또는 레이블을 삭제할 수 있습니다. 그러나 이 두 시나리오에서는 모두 템플릿이 삭제되지 않고 보관된 상태로 남아 있습니다.
    
    이제 PowerShell [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) cmdlet을 사용하여 템플릿을 삭제할 수 있습니다. 또한 레이블로 변환되지 않은 템플릿에 대해 이 PowerShell cmdlet을 사용할 수 있습니다. 그러나 콘텐츠를 보호하는 데 사용한 템플릿을 삭제하는 경우 해당 콘텐츠를 더 이상 열 수 없습니다. 확실히 프로덕션에서 문서 또는 메일을 보호하는 데 사용되지 않는 경우에만 템플릿을 삭제합니다. 예방 조치로서 [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate) cmdlet을 사용하여 템플릿을 먼저 백업으로 내보내는 것을 고려할 수 있습니다. 

- 현재, 부서별 템플릿을 편집하고 저장하면 범위 구성이 제거됩니다. Azure Information Protection 정책에서 범위가 지정된 템플릿은 [범위 정책](configure-policy-scope.md)입니다. 템플릿을 레이블로 변환하는 경우 기존 범위를 선택할 수 있습니다.
    
    또한 Azure Portal을 사용하여 부서별 템플릿에 대한 응용 프로그램 호환성 설정을 지정할 수 없습니다. 필요한 경우 [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet 및 *EnableInLegacyApps* 매개 변수를 사용하여 이 응용 프로그램 호환성 설정을 지정할 수 있습니다.

- 템플릿을 레이블로 변환하거나 연결하면 다른 레이블에서 더 이상 사용할 수 없습니다. 또한 이 템플릿은 더 이상 **보호 템플릿** 섹션에 표시되지 않습니다. 

- **보호 템플릿** 섹션에서 새 템플릿을 만들지 않습니다. 대신 **보호** 설정이 있는 레이블을 만들고 **보호** 블레이드에서 사용 권한과 설정을 구성합니다. 전체 지침은 [새 템플릿을 만들려면](#to-create-a-new-template)을 참조하세요.

## <a name="to-configure-the-templates-in-the-azure-information-protection-policy"></a>Azure Information Protection 정책에서 템플릿을 구성하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. 그런 다음, **Azure Information Protection - 레이블** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 **보호 템플릿**을 확장한 다음, 구성하려는 템플릿을 찾습니다.
    
3. 템플릿을 선택하고 **레이블** 블레이드에서 필요한 경우 **레이블 표시 이름** 및 **설명**을 편집하여 템플릿 이름 및 설명을 변경할 수 있습니다. 그런 다음 **Azure(클라우드 키)** 의 값이 있는 **보호**를 선택하여 **보호** 블레이드를 엽니다.

4. **보호** 블레이드에서 권한, 콘텐츠 만료 및 오프라인 액세스 설정을 변경할 수 있습니다. 보호 설정 구성에 대한 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.
    
    **확인**을 클릭하여 변경 내용을 유지하고 **레이블** 블레이드에서 **저장**을 클릭합니다.
    
> [!NOTE]
> 미리 정의된 템플릿을 사용하도록 레이블을 구성한 경우 **보호** 블레이드에 있는 **템플릿 편집** 단추를 사용하여 템플릿을 편집할 수도 있습니다. 다른 레이블을 제공하지 않아도 선택한 템플릿이 사용되며, 이 단추는 템플릿을 레이블로 변환하고 사용자를 5단계로 이동시킵니다. 템플릿이 레이블로 변환되면 발생하는 일에 대한 자세한 내용은 다음 섹션을 참조하세요.

## <a name="to-convert-templates-to-labels"></a>템플릿을 레이블로 변환하려면

분류, 레이블 지정 및 보호를 포함하는 구독이 있는 경우 템플릿을 레이블로 변환할 수 있습니다. 템플릿을 변환하는 경우 원본 템플릿은 유지되지만 Azure Portal에서 템플릿이 새 레이블에 포함된 것으로 표시됩니다.

예를 들어 마케팅 그룹에 대한 사용 권한을 부여하는 **Marketing**이라는 레이블을 변환하는 경우 Azure Portal에서 같은 보호 설정이 지정된 **Marketing**이라는 레이블로 표시됩니다. 새로 생성된 레이블에서 보호 설정을 변경하면 템플릿에서 변경을 수행하는 것이므로 이 템플릿을 사용하는 모든 사용자 또는 서비스는 다음 번에 템플릿을 새로 고칠 때 새 보호 설정이 적용됩니다. 

모든 템플릿을 레이블로 변환해야 하는 것은 아니지만 이렇게 하는 경우 보호 설정이 레이블의 전체 기능과 완전히 통합되므로 설정을 따로 유지 관리할 필요가 없습니다.

템플릿을 레이블로 변환하려면 해당 템플릿을 마우스 오른쪽 단추로 클릭하고 **레이블로 변환**을 선택합니다. 또는 상황에 맞는 메뉴를 사용하여 이 옵션을 선택합니다. 

보호를 위한 레이블과 미리 정의된 템플릿을 구성할 때 **템플릿 편집** 단추를 사용하여 템플릿을 레이블로 변환할 수도 있습니다. 

템플릿을 레이블로 변환할 경우:

- 템플릿의 이름이 새 레이블 이름으로 변환되고 템플릿 설명이 레이블 도구 설명으로 변환됩니다. 

- 템플릿의 상태가 게시되면 이 설정은 레이블에 대한 **사용**: **설정**으로 매핑됩니다. 그러면 다음 번에 Azure Information Protection 정책을 게시할 때 사용자에게 이 레이블로 표시됩니다. 템플릿의 상태가 보관된 경우 이 설정은 레이블에 대해 **사용**: **해제**로 매핑되며 사용자에게 사용 가능한 레이블로 표시되지 않습니다.

- 보호 설정은 유지되며, 필요한 경우 이러한 설정을 편집할 수 있고 시각적 표식 및 조건 같은 기타 레이블 설정을 추가할 수도 있습니다.

- 원본 템플릿이 더 이상 **보호 템플릿**에 표시되지 않으므로 레이블에 보호를 구성할 때 미리 정의된 템플릿으로 선택할 수 없습니다. Azure 포털에서 이 템플릿을 편집하기 위해 이제 템플릿을 변환할 때 만든 레이블을 편집합니다. 템플릿은 Azure 권한 관리 서비스에 계속 사용할 수 있으며 [PowerShell 명령](administer-powershell.md)을 사용하여 계속 관리할 수 있습니다.  

## <a name="to-create-a-new-template"></a>새 템플릿을 만들려면

**Azure(클라우드 키)** 의 보호 설정을 사용하여 새 레이블을 만들 경우 이 동작은 내부적으로 Rights Management 템플릿과 통합되는 서비스 및 응용 프로그램에서 액세스할 수 있는 새 사용자 지정 템플릿을 만듭니다.

1. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 **새 블레이드 추가**를 선택합니다.

2. **레이블** 블레이드에서 기본값인 **사용**: **켜기**를 유지한 다음, 템플릿 이름 및 설명으로 레이블 이름과 설명을 입력합니다.

3. **이 레이블을 포함하는 문서 및 메일에 대한 권한 설정**에서 **보호**를 선택하고 **보호**를 선택합니다.
    
     ![Azure Information Protection 레이블에 대한 보호 구성](./media/info-protect-protection-bar-configured.png)

4. **보호** 블레이드에서 권한, 콘텐츠 만료 및 오프라인 액세스 설정을 변경할 수 있습니다. 이러한 보호 설정 구성에 대한 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.
    
    **확인**을 클릭하여 변경 내용을 유지하고 **레이블** 블레이드에서 **저장**을 클릭합니다.
    
    이제 **Azure Information Protection - 레이블** 블레이드의 **보호** 열에 새 레이블이 표시되어 보호 설정을 포함한다는 것을 나타냅니다. 이러한 보호 설정은 Azure Rights Management 서비스를 지원하는 응용 프로그램 및 서비스에 템플릿으로 표시됩니다.
    
    기본적으로 레이블을 사용하도록 설정되어 있지만, 템플릿은 보관됩니다. 그러므로 응용 프로그램 및 서비스에서 템플릿을 사용하여 문서 및 메일을 보호하고, 마지막 단계를 완료하여 템플릿을 게시할 수 있습니다.

5. **분류** > **정책** 메뉴 옵션에서 새 보호 설정을 포함하는 정책을 선택합니다. 그런 다음, **레이블 추가 또는 제거**를 선택합니다. **정책: 레이블 추가 또는 제거** 블레이드에서 보호 설정을 포함하는 새로 만든 레이블을 선택하고 **확인**을 선택한 다음, **저장**을 선택합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 클라이언트를 실행하는 컴퓨터에서 이러한 변경된 설정을 가져오려면 최대 15분이 걸릴 수 있습니다. 컴퓨터 및 서비스가 템플릿을 다운로드하고 새로 고치는 방법에 대한 자세한 내용은 [사용자 및 서비스를 위한 템플릿 새로 고침](refresh-templates.md)을 참조하세요.

템플릿을 만들고 관리하기 위해 Azure 포털에서 구성할 수 있는 모든 사항은 PowerShell을 사용하여 수행할 수 있습니다. 또한 PowerShell에서는 포털에서 사용할 수 없는 추가 옵션을 제공합니다. 자세한 내용은 [보호 템플릿에 관한 PowerShell 참조](configure-templates-with-powershell.md)를 확인하세요. 

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

