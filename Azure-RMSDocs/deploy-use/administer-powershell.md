---
title: "PowerShell을 사용하여 Azure Rights Management 관리 - AIP"
description: "Azure Information Protection의 Azure Rights Management 서비스(AADRM)용 PowerShell 모듈을 사용하여 조직에 대해 이 서비스를 관리하는 방법에 대해 알아봅니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 085dc82fcb9632bfdf4fb1b14ca5c632846e81d0
ms.lasthandoff: 02/24/2017


---

# <a name="administering-the-azure-rights-management-service-by-using-windows-powershell"></a>Windows PowerShell을 사용하여 Azure Rights Management 서비스 관리

>*적용 대상: Azure Information Protection, Office 365*

PowerShell을 사용하여 Azure Information Protection에 대한 Azure Rights Management 서비스를 관리해야 하나요? 전역 관리자인 경우 이러한 작업이 필요하지 않을 수 있으며 이 서비스에 대해 필요한 구성은 활성화(또는 비활성화)하고 Rights Management 템플릿을 구성하는 것입니다.

그러나 더 많은 고급 구성을 수행하려면 PowerShell을 사용해야 하며 전역 관리자가 아니고 전역 관리자가 서비스를 관리할 수 있는 권한을 부여한 경우에도 PowerShell을 사용해야 합니다. 보다 효율적인 명령줄 제어 및 스크립팅을 위해 PowerShell을 사용하려고 할 수도 있습니다.

다음 섹션에 제공된 표에는 PowerShell을 사용하는 몇 가지 고급 구성 시나리오가 나와 있습니다. PowerShell을 사용하지 않고도 구성을 완료할 수 있으며 이 정보는 표에도 나와 있습니다.

사용 가능한 cmdlet의 전체 목록과 각 cmdlet에 대한 자세한 내용은 [Azure 권한 관리 cmdlet](http://msdn.microsoft.com/library/azure/dn629398.aspx)을 참조하세요.

> [!NOTE]
> PowerShell 모듈을 설치해야 하려면 [Azure Rights Management용 Windows PowerShell 설치](install-powershell.md)를 참조하세요.

Azure Information Protection 클라이언트는 이 서비스 쪽 PowerShell 모듈 외에도 보조 PowerShell 모듈인 **AzureInformationProtection**을 설치합니다. 이 클라이언트 모듈은 여러 파일을 분류하고 보호하므로 예를 들어 폴더의 모든 파일을 대량으로 보호할 수 있습니다. 자세한 내용은 관리자 가이드에서 [Azure Information Protection 클라이언트에서 PowerShell 사용](../rms-client/client-admin-guide-powershell.md)을 참조하세요.

## <a name="cmdlets-grouped-by-administration-task"></a>관리 작업별로 그룹화된 Cmdlet

|수행할 작업|사용할 cmdlet|
|-------------------|------------------------------|
|온-프레미스 Rights Management(AD RMS 또는 Windows RMS)에서 Azure Information Protection으로 마이그레이션|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|조직의 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 서비스에 연결/서비스 연결 끊기|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|직접 테넌트 키 생성/관리 - BYOK(Bring Your Own Key) 시나리오|[Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|조직의 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 서비스 활성화/비활성화<br /><br />관리 포털에서 이러한 작업을 수행할 수도 있습니다. 자세한 내용은 [Azure Rights Management 서비스 활성화](activate-service.md)를 참조하세요.|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Azure Information Protection에 대한 문서 추적 사이트를 사용하도록 설정하거나 사용하지 않도록 설정합니다.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Azure Rights Management 서비스의 단계적 배포를 위해 온보딩 컨트롤을 구성합니다.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|조직의 Rights Management 템플릿을 만들고 관리합니다.<br /><br />PowerShell에서는 좀 더 세부적인 제어 기능을 제공하지만 이러한 작업 대부분을 Azure 클래식 포털에서 수행할 수도 있습니다. 자세한 내용은 [Azure Rights Management 서비스용 사용자 지정 템플릿 구성](configure-custom-templates.md)을 참조하세요.|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Export-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Import-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|조직에서 보호하는 콘텐츠 최대 일 수를 구성하면 인터넷 연결 없이 액세스될 수 있습니다.(사용 라이선스 유효 기간)|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|조직의 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 슈퍼 사용자 기능 관리|[Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629405.aspx)<br /><br />[Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx)<br /><br />[Get-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653942.aspx)<br /><br />[Clear-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653944.aspx)|
|조직의 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 서비스 관리 권한이 있는 사용자 및 그룹 관리|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629424.aspx)|
|조직의 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 관리 작업 로그 가져오기|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]의 사용 현황 로깅 기록 및 분석|[Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx)|
|조직의 현재 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 서비스 구성 표시|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Azure Information Protection에서 온-프레미스 AD RMS 배포로 조직 마이그레이션|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



