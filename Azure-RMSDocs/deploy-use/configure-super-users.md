---
title: "Azure 권한 관리 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성 | Azure Information Protection"
description: "Azure Rights Management에서 조직을 위해 보호하는 데이터를 권한이 있는 사용자와 서비스가 항상 읽고 검사할 수 있도록 하는 Azure Information Protection의 Azure Rights Management 서비스의 슈퍼 사용자 기능 및 이 기능을 구현하는 방법을 설명합니다. ‘데이터 추론’이라고도 하는 이 기능은 조직 데이터에 대한 통제력을 유지하는 데 필수적인 요소입니다."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: d2ae8df5895b1cf1985420be25abac36fe2689b7


---

# Azure 권한 관리 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection의 Azure Rights Management 서비스의 슈퍼 사용자 기능을 사용하면 Azure Rights Management에서 조직을 위해 보호하는 데이터를 권한이 부여된 사용자와 서비스가 항상 읽고 검사할 수 있습니다. 또한 필요한 경우 이전에 적용했던 보호를 변경하거나 제거할 수 있습니다. 슈퍼 사용자는 조직의 Azure Information Protection 테넌트에 의해 부여된 모든 사용권에 대해 항상 전체 소유자 권한을 가집니다. "데이터 추론"이라고도 하는 이 기능은 조직 데이터에 대한 통제력을 유지하는 데 필수적인 요소입니다. 예를 들어 다음과 같은 시나리오에서 이 기능을 사용할 수 있습니다.

-   퇴사한 직원이 보호했던 파일을 읽어야 하는 경우

-   IT 관리자가 파일에 대해 구성된 현재 보호 정책을 제거하고 새 보호 정책을 적용해야 하는 경우

-   Exchange Server에서 검색 작업을 위해 사서함을 인덱싱해야 하는 경우

-   이미 보호된 파일을 검사하는 데 필요한 DLP(데이터 누수 방지) 솔루션, CEG(콘텐츠 암호화 게이트웨이) 및 맬웨어 방지 제품용 기존 IT 서비스가 있는 경우

-   감사, 법률 또는 기타 준수상의 이유로 인해 대량으로 파일의 암호를 해독해야 하는 경우

기본적으로 슈퍼 사용자 기능은 사용하도록 설정되지 않으며 이 역할은 사용자에게 할당되지 않습니다. Exchange Server용 Rights Management 커넥터를 구성하는 경우에는 이 기능이 자동으로 사용하도록 설정되지만 Exchange Online, SharePoint Online 또는 SharePoint Server를 실행하는 표준 서비스에는 이 기능이 필요하지 않습니다.

슈퍼 사용자 기능을 수동으로 사용하도록 설정해야 하는 경우 Windows PowerShell cmdlet Windows PowerShell cmdlet [Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)를 사용합니다. 그런 다음 [Add-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) cmdlet 또는 [Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx) cmdlet을 사용하여 필요에 따라 사용자 또는 서비스 계정을 할당하고, 필요에 따라 이 그룹에 사용자 또는 다른 그룹을 추가합니다. 

> [!NOTE]
> [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell 모듈을 아직 설치하지 않은 경우 [Azure 권한 관리용 Windows PowerShell 설치](install-powershell.md)를 참조하세요.

슈퍼 사용자 기능에 대한 보안 모범 사례

-   Office 365 또는 Azure Information Protection 테넌트의 전역 관리자로 할당되거나 [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) cmdlet을 사용하여 GlobalAdministrator 역할이 할당된 관리자를 제한하고 모니터링합니다. 이러한 사용자는 슈퍼 사용자 기능을 사용하도록 설정하고 사용자(및 자신)를 슈퍼 사용자로 할당하며, 잠재적으로 조직에서 보호하는 모든 파일의 암호를 해독할 수 있습니다.

-   슈퍼 사용자로 할당된 사용자 및 서비스 계정을 개별적으로 확인하려면 [Get-AadrmSuperUser cmdlet](https://msdn.microsoft.com/library/azure/dn629408.aspx)을 사용합니다. 슈퍼 사용자 그룹이 구성되어 있는지 여부를 확인하려면 [Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/mt653942.aspx) cmdlet 및 표준 사용자 관리 도구를 사용하여 어느 사용자가 이 그룹의 구성원인지 확인합니다. 모든 관리 작업과 마찬가지로 슈퍼 기능을 사용하거나 사용하지 않도록 설정하는 작업 및 슈퍼 사용자를 추가하거나 제거하는 작업은 기록되며 [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) 명령을 사용하여 감사할 수 있습니다. 슈퍼 사용자가 파일의 암호를 해독하면 이 작업이 기록되고 [사용 현황 로깅](log-analyze-usage.md)을 통해 감사할 수 있습니다.

-   일상적인 서비스에 슈퍼 사용자 기능이 필요하지 않은 경우에는 필요할 때만 이 기능을 사용하도록 설정하고 [Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) cmdlet를 사용하여 다시 사용하지 않도록 설정합니다.

다음 로그 추출은 Get-AadrmAdminLog cmdlet을 사용한 일부 예제 항목을 보여 줍니다. 이 예제에서 Contoso Ltd의 관리자는 슈퍼 사용자 기능이 사용하지 않도록 설정되어 있음을 확인하고, Richard Simone을 슈퍼 사용자로 추가하고, Richard가 Azure Rights Management 서비스에 대해 구성된 유일한 슈퍼 사용자인지 확인한 다음, Richard가 현재 퇴사한 직원이 보호한 일부 파일의 암호를 해독할 수 있도록 슈퍼 사용자 기능을 사용하도록 설정합니다.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## 슈퍼 사용자에 대한 스크립팅 옵션
[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]에 대한 슈퍼 사용자 역할이 할당된 사용자가 여러 위치에서 여러 파일의 보호를 제거해야 하는 상황이 종종 발생합니다. 이 작업은 수동으로 수행할 수도 있지만 스크립트를 작성하는 것이 더 효율적이며 더욱 안정적인 경우가 많습니다. 이렇게 하려면 [RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256)을 다운로드합니다. 그런 후에 [Unprotect-RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) cmdlet 및 [Protect-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) cmdlet을 필요에 따라 사용합니다.

이러한 cmdlet에 대한 자세한 내용은 [RMS 보호 Cmdlet](https://msdn.microsoft.com/library/azure/mt433195.aspx)를 참조하세요.

> [!NOTE]
> RMS 보호 도구와 함께 제공되는 RMS 보호 PowerShell 모듈은 기본 [Azure 권한 관리용 Windows PowerShell 모듈](administer-powershell.md)과는 다르며 해당 모듈을 보완합니다. RMS 보호 모듈은 Azure Information Protection의 Azure RMS(Azure Rights Management Services) 및 AD RMS(Active Directory Rights Management Services)를 모두 지원합니다.





<!--HONumber=Sep16_HO4-->


