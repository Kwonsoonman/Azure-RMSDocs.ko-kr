---
title: PowerShell을 사용하여 Azure Rights Management 관리 - AIP
description: Azure Information Protection의 Azure Rights Management 서비스(AADRM)용 PowerShell 모듈을 사용하여 조직에 대해 이 서비스를 관리하는 방법에 대해 알아봅니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/13/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: de522b734b923927972d6491d922651f26196440
ms.sourcegitcommit: c1274d6d7ab486590dcd2a4e6aca3dcd3d284c1b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168729"
---
# <a name="administering-the-azure-rights-management-service-by-using-windows-powershell"></a>Windows PowerShell을 사용하여 Azure Rights Management 서비스 관리

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

PowerShell을 사용하여 Azure Information Protection에 대한 Azure Rights Management 서비스를 관리해야 하나요? Azure Portal이나 Office 365 포털에서 모든 구성을 수행할 필요가 없을 수도 있습니다. 그러나 일부 고급 구성에는 PowerShell을 사용해야 하고 보다 효율적인 명령줄 제어 및 스크립팅을 위해 PowerShell을 사용하는 것을 선호할 수도 있습니다.

다음 섹션에 제공된 표에는 PowerShell을 사용하는 몇 가지 고급 구성 시나리오가 나와 있습니다. PowerShell을 사용하지 않고도 구성을 완료할 수 있으며 이 정보는 표에도 나와 있습니다.

이 모듈에 대해 사용 가능한 cmdlet의 전체 목록과 각 cmdlet에 대한 자세한 내용은 [AADRM](/powershell/module/aadrm/?view=azureipps#aadrm)을 참조하세요.

> [!NOTE]
> 이 PowerShell 모듈을 설치하려면 [AADRM PowerShell 모듈 설치](install-powershell.md)를 참조하세요.

Azure Information Protection 클라이언트는 이 서비스 쪽 PowerShell 모듈 외에도 보조 PowerShell 모듈인 **AzureInformationProtection**을 설치합니다. 이 클라이언트 모듈은 여러 파일을 분류하고 보호하므로 예를 들어 폴더의 모든 파일을 대량으로 보호할 수 있습니다. 자세한 내용은 관리자 가이드에서 [Azure Information Protection 클라이언트에서 PowerShell 사용](./rms-client/client-admin-guide-powershell.md)을 참조하세요.

## <a name="cmdlets-grouped-by-administration-task"></a>관리 작업별로 그룹화된 Cmdlet

|수행할 작업|사용할 cmdlet|
|-------------------|------------------------------|
|온-프레미스 Rights Management(AD RMS 또는 Windows RMS)에서 Azure Information Protection으로 마이그레이션|[Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd)<br /><br />[Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)|
|조직에서 Rights Management 서비스 간에 연결 설정 또는 끊기|[Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice)<br /><br />[Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice)|
|직접 테넌트 키 생성/관리 - BYOK(Bring Your Own Key) 시나리오|[Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)<br /><br />[Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey)<br /><br />[Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys)|
|조직에서 Rights Management 서비스 활성화 또는 비활성화<br /><br />관리 포털에서 이러한 작업을 수행할 수도 있습니다. 자세한 내용은 [Azure Rights Management 서비스 활성화](activate-service.md)를 참조하세요.|[Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm)<br /><br />[Disable-Aadrm](/powershell/aadrm/vlatest/disable-aadrm)|
|Azure Information Protection에 대한 문서 추적 사이트를 관리합니다.|[Disable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/disable-aadrmdocumenttrackingfeature)<br /><br />[Enable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/enable-aadrmdocumenttrackingfeature)<br /><br />[Get-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/get-aadrmdocumenttrackingfeature)<br /><br />[Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/set-aadrmdonottrackusergroup)<br /><br />[Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup)<br /><br />[Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup)<br /><br />[Get-AadrmTrackingLog](/powershell/module/aadrm/Get-AadrmTrackingLog)<br /><br />[Get-AadrmDocumentLog](/powershell/module/aadrm/Get-AadrmDocumentLog)|
|Azure Rights Management 서비스의 단계적 배포를 위해 온보딩 컨트롤을 구성합니다.|[Get-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/get-aadrmonboardingcontrolpolicy)<br /><br />[Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy)|
|조직의 Rights Management 템플릿을 만들고 관리합니다.<br /><br />PowerShell에서는 좀 더 세부적인 제어 기능을 제공하지만 이러한 작업 대부분을 Azure 포털에서 수행할 수도 있습니다. 자세한 내용은 [Azure Information Protection 템플릿 구성 및 관리](configure-policy-templates.md)를 참조하세요.|[Add-AadrmTemplate](/powershell/aadrm/vlatest/add-aadrmtemplate)<br /><br />[Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate)<br /><br />[Get-AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate)<br /><br />[Get-AadrmTemplateProperty](/powershell/aadrm/vlatest/get-aadrmtemplateproperty)<br /><br />[Import-AadrmTemplate](/powershell/aadrm/vlatest/import-aadrmtemplate)<br /><br />[New-AadrmRightsDefinition](/powershell/aadrm/vlatest/new-aadrmrightsdefinition)<br /><br />[Remove-AadrmTemplate](/powershell/aadrm/vlatest/remove-aadrmtemplate)<br /><br />[Set-AadrmTemplateProperty](/powershell/aadrm/vlatest/set-aadrmtemplateproperty)|
|조직에서 보호하는 콘텐츠 최대 일 수를 구성하면 인터넷 연결 없이 액세스될 수 있습니다.(사용 라이선스 유효 기간)|[Get-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/get-aadrmmaxuselicensevaliditytime)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime)|
|조직에서 Rights Management의 슈퍼 사용자 기능 관리|[Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature)<br /><br />[Disable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/disable-aadrmsuperuserfeature)<br /><br />[Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser)<br /><br />[Get-AadrmSuperUser](/powershell/aadrm/vlatest/get-aadrmsuperuser)<br /><br />[Remove-AadrmSuperUser](/powershell/aadrm/vlatest/remove-aadrmsuperuser)<br /><br />[Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup)<br /><br />[Get-AadrmSuperUserGroup](/powershell/aadrm/vlatest/get-aadrmsuperusergroup)<br /><br />[Clear-AadrmSuperUserGroup](/powershell/aadrm/vlatest/clear-aadrmsuperusergroup)|
|조직에서 Rights Management 서비스 관리 권한이 있는 사용자 및 그룹 관리|[Add-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/add-aadrmrolebasedadministrator)<br /><br />[Get-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/get-aadrmrolebasedadministrator)<br /><br />[Remove-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/remove-aadrmrolebasedadministrator)|
|조직의 Rights Management 관리 작업 로그 가져오기|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Rights Management의 사용량 로깅 기록 및 분석|[Get-AadrmUserLog](/powershell/aadrm/vlatest/get-aadrmuserlog)|
|조직에서 현재 Rights Management 서비스 구성 표시|[Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)|
|Azure Information Protection에서 온-프레미스 AD RMS 배포로 조직 마이그레이션|[Set-AadrmMigrationUrl](/powershell/aadrm/vlatest/set-aadrmmigrationurl)<br /><br />[Get-AadrmMigrationUrl](/powershell/aadrm/vlatest/get-aadrmmigrationurl)|

