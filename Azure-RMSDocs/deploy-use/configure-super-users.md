---
title: "Azure Rights Management에 대한 슈퍼 사용자 구성 - AIP"
description: "권한 있는 사용자와 서비스가 Azure Rights Management로 보호되는 조직의 데이터를 언제든지 읽고 검사할 수 있도록 Azure Information Protection에서 제공하는 Azure Rights Management 서비스의 슈퍼 사용자 기능을 이해하고 구현합니다. 이 기능은 '데이터를 통한 추론'이라고도 하며 조직 데이터의 제어권을 유지하는 데 필수적인 요소입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a134d6619f67bfc3d26cb1726fe07e8ffca403cd
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="configuring-super-users-for-azure-rights-management-and-discovery-services-or-data-recovery"></a>Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection에서 제공하는 Azure Rights Management 서비스의 슈퍼 사용자 기능은 권한 있는 사용자와 서비스가 Azure Rights Management로 보호되는 조직의 데이터를 언제든지 읽고 검사할 수 있도록 보장합니다. 필요한 경우 보호를 제거하거나 이전에 적용한 보호를 변경할 수 있습니다. 

슈퍼 사용자는 언제나 조직의 Azure Information Protection 테넌트로 보호되는 문서 및 이메일에 대한 Rights Management 전체 제어 [사용 권한을](configure-usage-rights.md) 갖습니다. 이 기능은 “데이터를 통한 추론”이라고도 하며 조직 데이터의 제어권을 유지하는 데 필수적인 요소입니다. 예를 들어 다음과 같은 시나리오에 이 기능을 사용할 수 있습니다.

- 직원이 퇴사하고 그 직원이 보호하던 파일을 읽어야 합니다.

- IT 관리자는 파일에 대해 구성된 현재 보호 정책을 제거하고 새 보호 정책을 적용해야 합니다.

- 검색 작업을 위해 Exchange Server에서 사서함을 인덱싱해야 합니다.

- DLP(데이터 손실 방지) 솔루션, CEG(콘텐츠 암호화 게이트웨이) 및 이미 보호되고 있는 파일을 검사해야 하는 맬웨어 방지 제품을 위한 기존 IT 서비스를 보유하고 있습니다.

- 감사, 법률적 이유 또는 기타 규정 준수 상의 이유로 파일을 대량으로 암호 해독해야 합니다.

슈퍼 사용자 기능은 기본적으로 사용되지 않으며 어떤 사용자도 이 역할에 할당되지 않습니다. Exchange에 대해 Rights Management 커넥터를 구성하면 자동으로 슈퍼 사용자 기능을 사용하도록 설정되며, Exchange Online, SharePoint Online 또는 SharePoint Server를 실행하는 표준 서비스에는 필요하지 않습니다.

슈퍼 사용자 기능을 수동으로 설정해야 하는 경우 PowerShell cmdlet [Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature)를 사용한 후 [Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser) cmdlet 또는 [Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup) cmdlet을 사용하여 필요한 대로 사용자(또는 서비스 계정)를 할당하고, 필요한 대로 이 그룹에 사용자(또는 다른 그룹)를 추가합니다. 

슈퍼 사용자에 그룹을 사용하면 좀 더 쉽게 관리할 수 있지만, 성능상의 이유로 Azure Rights Management가 [그룹 멤버 자격을 캐싱](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection)한다는 사실을 기억해야 합니다. 슈퍼 사용자가 되어 콘텐츠를 즉시 암호 해독할 수 있는 새 사용자를 할당해야 하는 경우 Set-AadrmSuperUserGroup을 사용하여 구성한 기존 그룹에 사용자를 추가하지 말고 Add-AadrmSuperUser를 사용하여 사용자를 추가해야 합니다.

> [!NOTE]
> 아직 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell 모듈을 설치하지 않은 경우 [Azure Rights Management용 Windows PowerShell 설치](install-powershell.md)를 참조하세요.

슈퍼 사용자 기능에 대한 보안 모범 사례:

- Office 365 또는 Azure Information Protection 테넌트의 전역 관리자로 할당된 관리자 또는 GlobalAdministrator 역할이 할당된 관리자를 [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) cmdlet을 사용하여 제한하고 모니터링합니다. 이러한 사용자는 슈퍼 사용자 기능을 사용하도록 설정하고, 사용자(및 자신)을 슈퍼 사용자로 할당하고, 조직에서 보호하는 모든 파일을 암호 해독할 수 있습니다.

- 개별적으로 슈퍼 사용자로 할당된 사용자 및 서비스 계정을 보려면 [Get-AadrmSuperUser cmdlet](/powershell/module/aadrm/get-aadrmsuperuser)을 사용합니다. 슈퍼 사용자 그룹이 구성되어 있는지 확인하려면 [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperusergroup) cmdlet 및 표준 사용자 관리 도구를 사용하여 어떤 사용자가 이 그룹의 구성원인지 확인합니다. 모든 관리 작업이 그렇듯이, 슈퍼 기능을 사용하도록 또는 사용하지 않도록 설정하고 슈퍼 사용자를 추가 또는 제거하는 작업은 기록되며 [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) 명령을 사용하여 감사할 수 있습니다. 슈퍼 사용자가 파일을 암호 해독하면 이 작업이 기록되고 [사용 현황 로깅](log-analyze-usage.md)을 사용하여 감사할 수 있습니다.

- 일상적인 서비스에는 슈퍼 사용자 기능이 필요 없는 경우 필요할 때만 설정하고 [Disable-AadrmSuperUserFeature](/powershell/module/aadrm/disable-aadrmsuperuserfeature) cmdlet을 사용하여 다시 해제하면 됩니다.

다음 로그 추출물은 Get-AadrmAdminLog cmdlet을 사용할 때의 예제 항목을 보여줍니다. 이 예제에서 Contoso Ltd의 관리자는 슈퍼 사용자 기능이 해제된 것을 확인하고, Richard Simone을 슈퍼 사용자로 추가하고, Azure Rights Management 서비스에 대해 구성된 유일한 슈퍼 사용자가 Richard라는 것을 확인한 다음, 퇴사한 직원이 보호하던 일부 파일을 이제부터 Richard가 암호 해독할 수 있도록 슈퍼 사용자 기능을 활성화합니다.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## <a name="scripting-options-for-super-users"></a>슈퍼 사용자에 대한 스크립팅 옵션
[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]에 대한 슈퍼 사용자로 할당된 사용자가 여러 위치에서 여러 파일의 보호를 제거해야 하는 경우가 종종 있습니다. 이 작업을 수동으로 할 수는 있지만, 스크립팅하는 것이 좀 더 효율적(그리고 종종 더 안정적)입니다. 이렇게 하려면 필요에 따라 [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) cmdlet 및 [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) cmdlet을 사용합니다. 

분류 및 보호를 사용하는 경우 [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)을 사용하여 보호를 적용하지 않는 새 레이블을 적용하거나 보호를 적용한 레이블을 제거할 수 있습니다. 

이러한 cmdlet에 대한 자세한 내용은 Azure Information Protection 클라이언트 관리 가이드의 [Azure Information Protection 클라이언트에서 PowerShell 사용](../rms-client/client-admin-guide-powershell.md)을 참조하세요.

> [!NOTE]
> AzureInformationProtection 모듈은 RMS 보호 도구와 함께 설치된 RMS 보호 PowerShell 모듈을 대체합니다. 이러한 두 모듈은 주 [Azure Rights Management용 Windows PowerShell 모듈](administer-powershell.md)과 다르며 보완해줍니다. AzureInformationProtection 모듈은 Azure Information Protection, Azure Information Protection용 Azure RMS(Azure Rights Management) 서비스, AD RMS(Active Directory Rights Management Services)를 지원합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

