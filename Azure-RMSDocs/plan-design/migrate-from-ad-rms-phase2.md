---
title: "AD RMS-Azure Information Protection 마이그레이션 - 2단계"
description: "AD RMS에서 Azure Information Protection으로 마이그레이션하는 과정의 두 번째 단계로, AD RMS에서 Azure Information Protection으로 마이그레이션 4~6단계가 포함됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c81d7131bfb2a5f1e0742cd8dd55d52e3a65984a
ms.sourcegitcommit: 45c23b3b353ad0e438292cb1cd8d1b13061620e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="migration-phase-2---server-side-configuration-for-ad-rms"></a>마이그레이션 2단계 - AD RMS에 대한 서버 쪽 구성

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*

AD RMS에서 Azure Information Protection으로 마이그레이션 2단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 4~6단계를 설명합니다.


## <a name="step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection"></a>4단계. AD RMS에서 구성 데이터를 내보낸 후 Azure Information Protection으로 가져오기
이 단계는 다음의 두 부분으로 이루어진 프로세스입니다.

1. TPD(트러스트된 게시 도메인)를 .xml 파일로 내보내 AD RMS에서 구성 데이터를 내보냅니다. 이 프로세스는 모든 마이그레이션에서 동일합니다.

2. 구성 데이터를 Azure Information Protection으로 가져오기 현재 AD RMS 배포 구성 및 Azure RMS 테넌트 키에 대한 기본 설정 토폴로지에 따라 이 단계의 프로세스가 다를 수 있습니다.

### <a name="export-the-configuration-data-from-ad-rms"></a>AD RMS에서 구성 데이터 내보내기

조직에 대해 보호된 콘텐츠가 있는 트러스트된 모든 게시 도메인에 대해 모든 AD RMS 클러스터에서 다음 절차를 수행합니다. 라이선스 전용 클러스터에서는 이 프로시저를 수행할 필요가 없습니다.

#### <a name="to-export-the-configuration-data-trusted-publishing-domain-information"></a>구성 데이터(트러스트된 게시 도메인 정보)를 내보내려면

1. AD RMS 관리 권한이 있는 사용자로 AD RMS 클러스터에 로그온합니다.

2. AD RMS 관리 콘솔(**Active Directory Rights Management Services**)에서 AD RMS 클러스터 이름을 확장하고, **트러스트 정책**를 확장한 후 **트러스트된 게시 도메인**을 클릭합니다.

3. 결과 창에서 트러스트된 게시 도메인을 선택하고 작업 창에서 **트러스트된 게시 도메인 내보내기**를 클릭합니다.

4. **트러스트된 게시 도메인 내보내기** 대화 상자에서 다음을 수행합니다.

    - **다른 이름으로 저장**을 클릭하고 선택한 경로와 파일 이름으로 저장합니다. 파일 이름 확장명으로 **.xml**을 지정해야 합니다. 파일 이름 확장명은 자동으로 추가되지 않습니다.

    - 강력한 암호를 지정하고 확인합니다. 나중에 구성 데이터를 Azure Information Protection으로 가져올 때 필요하므로, 이 암호를 기억해둡니다.

    - RMS 버전 1.0에서 트러스트된 도메인 파일을 저장하려면 이 확인란을 선택하지 않도록 합니다.

트러스트된 모든 게시 도메인을 내보낸 경우 이 데이터를 Azure Information Protection으로 가져오는 절차를 시작할 준비가 된 것입니다.

트러스트된 게시 도메인에는 이전에 보호된 파일을 암호 해독하는 SLC(서버 사용 허가자 인증서) 키가 포함되어 있으므로 현재 활성 도메인뿐 아니라 트러스트된 게시 도메인을 모두 내보내고 나중에 Azure로 가져와야 합니다.

예를 들어 AD RMS 서버를 암호화 모드 1에서 암호화 모드 2로 업그레이드한 경우 트러스트된 도메인이 여럿 있습니다. 마이그레이션 종료 시 암호화 모드 1을 사용하여 보관된 키를 포함하는 트러스트된 게시 도메인을 내보내고 가져오지 않는 경우 사용자가 암호화 모드 1 키로 보호된 콘텐츠를 열 수 없습니다.


### <a name="import-the-configuration-data-to-azure-information-protection"></a>구성 데이터를 Azure Information Protection으로 가져오기
이 단계의 정확한 절차는 현재 AD RMS 배포 구성 및 Azure Information Protection 테넌트 키에 대한 기본 설정 토폴로지에 따라 달라집니다.

현재 AD RMS 배포는 SLC(서버 사용 허가자 인증서) 키에 대해 다음 구성 중 하나를 사용합니다.

- AD RMS 데이터베이스의 암호 보호. 이것이 기본 구성입니다.

- Thales HSM(하드웨어 보안 모듈)을 사용한 HSM 보호.

- Thales 이외의 공급업체가 제공한 HSM(하드웨어 보안 모듈)을 사용한 HSM 보호.

- 외부 암호화 공급자를 사용하여 암호 보호.

> [!NOTE]
> AD RMS에서 하드웨어 보안 모듈을 사용하는 방법에 대한 자세한 내용은 [하드웨어 보안 모듈에서 AD RMS 사용](http://technet.microsoft.com/library/jj651024.aspx)을 참조하세요.

두 Azure Information Protection 테넌트 키 토폴로지 옵션은 Microsoft에서 테넌트 키를 관리하는 방식(**Microsoft 관리**) 또는 Azure Key Vault에서 사용자가 테넌트 키를 관리하는 방식(**고객 관리**)입니다. Azure Information Protection 테넌트 키를 자체적으로 관리하는 경우 BYOK(bring your own key)라고 합니다. 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](plan-implement-tenant-key.md) 문서를 참조하세요.

다음 테이블을 사용하여 마이그레이션에 사용할 절차를 식별하세요. 

|현재 AD RMS 배포|Azure Information Protection 테넌트 키 토폴로지 선택|마이그레이션 지침|
|-----------------------------|----------------------------------------|--------------------------|
|AD RMS 데이터베이스의 암호 보호|Microsoft 관리|이 표 다음에 나오는 **소프트웨어 보호된 키-소프트웨어 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이것은 가장 간단한 마이그레이션 경로이며, Azure Information Protection으로 구성 데이터를 전송하기만 하면 됩니다.|
|Thales nShield HSM(하드웨어 보안 모듈)을 사용한 HSM 보호 |고객 관리(BYOK)|이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이 작업을 위해서는 Azure Key Vault BYOK 도구 집합과, 온-프레미스 HSM에서 Azure Key Vault HSM으로 키를 전송한 다음, 테넌트 키를 사용하도록 Azure Information Protection의 Azure Rights Management 서비스에 권한을 부여하고, 마지막으로 구성 데이터를 Azure Information Protection으로 전송하는 세 단계가 필요합니다.|
|AD RMS 데이터베이스의 암호 보호|고객 관리(BYOK)|이 표 다음에 나오는 **소프트웨어 보호된 키-HSM 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이 작업을 위해서는 Azure Key Vault BYOK 도구 집합과, 소프트웨어 키를 먼저 추출하고 온-프레미스 HSM으로 가져온 다음, 온-프레미스 HSM의 키를 Azure Information Protection HSM으로 전송하고, Key Vault 데이터를 Azure Information Protection으로 전송하고, 마지막으로 구성 데이터를 Azure Information Protection으로 전송하는 네 단계가 필요합니다.|
|Thales 이외의 공급업체가 제공한 HSM(하드웨어 보안 모듈)을 사용한 HSM 보호 |고객 관리(BYOK)|이 HSM에서 Thales nShield HSM(하드웨어 보안 모듈)로 키를 전송하는 방법에 대한 지침은 HSM 공급업체에 문의하세요. 그런 다음 이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키** 마이그레이션 절차의 지침을 따르세요.|
|외부 암호화 공급자를 사용하여 암호 보호|고객 관리(BYOK)|Thales nShield HSM(하드웨어 보안 모듈)로 키를 전송하는 방법에 대한 지침은 암호화 공급자의 공급업체에 문의하세요. 그런 다음 이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키** 마이그레이션 절차의 지침을 따르세요.|

내보낼 수 없는 HSM 보호된 키가 있어도 AD RMS 클러스터를 읽기 전용 모드로 구성하면 Azure Information Protection으로 마이그레이션할 수 있습니다. 이 모드에서 이전에 보호된 콘텐츠는 열 수 있으나 새로 보호된 콘텐츠는 귀하(BYOK) 또는 Microsoft에서 관리하는 새로운 테넌트 키를 사용합니다. 자세한 내용은 [AD RMS에서 Azure RMS로 마이그레이션을 지원하는 새로운 Office 업데이트 사용 가능](https://support.microsoft.com/help/4023955/an-update-is-available-for-office-to-support-migrations-from-ad-rms-to)을 참조하세요.

이러한 키 마이그레이션 절차를 시작하기 전에 트러스트된 게시 도메인을 내보낼 때 만든 .xml 파일에 액세스할 수 있는지 확인하세요. 예를 들어, 이러한 파일은 AD RMS 서버에서 인터넷에 연결된 워크스테이션으로 가져오는 USB 드라이브에 저장되어 있을 수 있습니다.

> [!NOTE]
> 하지만 이 데이터에 개인 키가 포함되어 있으므로 이러한 파일을 저장한 후 최적의 보안 권장 방법으로 파일을 보호합니다.

4단계를 완료하려면 마이그레이션 경로에 대한 지침을 선택합니다. 

- [소프트웨어 보호된 키-소프트웨어 보호된 키](migrate-softwarekey-to-softwarekey.md)
- [HSM 보호된 키-HSM 보호된 키](migrate-hsmkey-to-hsmkey.md)
- [소프트웨어 보호된 키-HSM 보호된 키](migrate-softwarekey-to-hsmkey.md)

## <a name="step-5-activate-the-azure-rights-management-service"></a>5단계. Azure Rights Management 서비스 활성화

PowerShell 세션을 열고 다음 명령을 실행합니다.

1. Azure Rights Management 서비스에 연결하고 메시지가 표시되면 전역 관리자 자격 증명을 지정합니다.
    
        Connect-Aadrmservice

2. Azure Rights Management 서비스 활성화:
    
        Enable-Aadrm

**Azure Information Protection 테넌트가 이미 활성화된 경우에는 어떻게 하나요?** 조직에서 이미 Azure Rights Management 서비스가 활성화되어 있으며 마이그레이션 후 사용하려는 사용자 지정 템플릿을 만든 경우 이러한 템플릿을 내보내고 가져와야 합니다. 이 절차는 다음 단계에서 다룹니다. 

## <a name="step-6-configure-imported-templates"></a>6단계. 가져온 템플릿 구성

가져온 템플릿의 기본 상태는 **보관됨**이므로 사용자가 Azure Rights Management 서비스에서 이러한 템플릿을 사용할 수 있도록 하려면 이 상태를 **게시됨**으로 변경해야 합니다.

AD RMS에서 가져오는 템플릿은 Azure 포털에서 만들 수 있는 사용자 지정 템플릿과 모양 및 동작이 유사합니다. 가져온 템플릿을 사용자가 응용 프로그램에서 보고 선택할 수 있도록 게시하기 위해 변경하려면 [Azure Information Protection용 템플릿 구성 및 관리](../deploy-use/configure-policy-templates.md)를 참조하세요.

새로 가져온 템플릿을 게시하는 것 외에도 마이그레이션을 계속하기 전에 수행해야 하는 두 가지 중요한 템플릿 변경 사항이 있습니다. 마이그레이션 프로세스 중에 사용자에게 보다 일관된 환경을 제공하려면, 가져온 템플릿을 추가적으로 변경하지 않도록 하고, Azure Information Protection과 함께 제공되는 2개의 기본 템플릿을 게시하거나 새 템플릿을 만들지 않도록 합니다. 대신 마이그레이션 프로세스가 완료되고 AD RMS 서버 프로비전을 해제할 때까지 기다립니다.

이 단계에 대해 수행해야 하는 템플릿 변경 작업:

- 마이그레이션 전에 Azure Information Protection 사용자 지정 템플릿을 만든 경우 수동으로 내보냈다가 가져와야 합니다.

- AD RMS의 템플릿에서 **ANYONE** 그룹을 사용한 경우 조직 외부의 사용자 또는 그룹을 추가해야 할 수 있습니다. 
    
    AD RMS에서 ANYONE 그룹은 인증된 모든 사용자에게 권한을 부여합니다. 이 그룹은 Azure AD 테넌트의 모든 사용자로 자동으로 변환됩니다. 추가 사용자에게 권한을 부여할 필요가 없는 경우 추가 작업이 필요하지 않습니다. 그러나 ANYONE 그룹을 사용하여 외부 사용자를 포함한 경우 이러한 사용자와 부여하려는 권한을 수동으로 추가해야 합니다.

### <a name="procedure-if-you-created-custom-templates-before-the-migration"></a>마이그레이션 전에 사용자 지정 템플릿을 만든 경우의 프로시저

Azure Rights Management 서비스를 활성화하기 전 또는 후, 마이그레이션 전에 사용자 지정 템플릿을 만든 경우에는 템플릿이 **게시됨**으로 설정되었더라도 마이그레이션 후 사용자가 템플릿을 사용할 수 없습니다. 사용자가 사용할 수 있도록 하려면 먼저 다음을 수행해야 합니다. 

1. [Get AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate)을 실행하여 이러한 템플릿을 식별하고 해당 템플릿 ID를 기록합니다. 

2. Azure RMS PowerShell cmdlet인 [Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate)을 사용하여 템플릿을 내보냅니다.

3. Azure RMS PowerShell cmdlet인 [Import-AadrmTemplate](/powershell/aadrm/vlatest/Import-AadrmTpd)을 사용하여 템플릿을 가져옵니다.

이렇게 하면 마이그레이션 후에 만든 다른 템플릿으로 하듯이 이 템플릿을 게시하거나 보관할 수 있습니다.

### <a name="procedure-if-your-templates-in-ad-rms-used-the-anyone-group"></a>AD RMS의 템플릿에서 **ANYONE** 그룹을 사용한 경우 프로시저

AD RMS의 템플릿에서 **ANYONE** 그룹을 사용한 경우 이 그룹은 **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@\<tenant_name>.onmicrosoft.com**이라는 이름의 그룹을 사용하도록 자동으로 변환됩니다. 예를 들어 이 그룹은 Contoso에 대해 **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**과 같을 수 있습니다. 이 그룹에는 Azure AD 테넌트의 모든 사용자가 포함됩니다.

Azure Portal의 템플릿과 레이블을 관리할 때 이 그룹은 Azure AD에 테넌트의 도메인 이름으로 표시됩니다. 예를 들어 이 그룹은 Contoso에 대해 **contoso.onmicrosoft.com**과 같이 표시될 수 있습니다. 이 그룹을 추가하기 위해 옵션에 **\<조직 이름 추가> - 모든 멤버**가 표시됩니다.

AD RMS 템플릿에 ANYONE 그룹이 포함되어 있는지가 확실하지 않은 경우 다음 샘플 Windows PowerShell 스크립트를 사용하여 이러한 템플릿을 식별할 수 있습니다. AD RMS와 함께 Windows PowerShell을 사용하는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용하여 AD RMS 관리](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx)를 참조하세요.

Azure Portal에서 이러한 템플릿을 레이블로 변환할 때 외부 사용자를 템플릿에 쉽게 추가할 수 있습니다. 그런 다음 **권한 추가** 블레이드에서 **Enter details**(세부 정보 입력)를 선택하여 이러한 사용자의 메일 주소를 수동으로 지정합니다. 

이 구성에 대한 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](../deploy-use/configure-policy-protection.md)을 참조하세요.

#### <a name="sample-windows-powershell-script-to-identify-ad-rms-templates-that-include-the-anyone-group"></a>ANYONE 그룹을 포함하는 AD RMS 템플릿을 식별하기 위한 샘플 Windows PowerShell 스크립트
이 섹션에는 이전 섹션에서 설명한 것과 같이 정의된 ANYONE 그룹이 있는 AD RMS 템플릿을 식별하는 데 도움이 되는 샘플 스크립트가 포함되어 있습니다.

**고지 사항:** 이 샘플 스크립트는 Microsoft 표준 지원 프로그램 또는 서비스를 통해 지원되지 않습니다. 이 샘플 스크립트는 어떤 종류의 보증도 없이 있는 그대로 제공됩니다.

```
import-module adrmsadmin 

New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force 

$ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate

foreach($Template in $ListofTemplates) 
{ 
                $templateID=$Template.id

                $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright

     $templateName=$Template.DefaultDisplayName 

        if ($rights.usergroupname -eq "anyone")

                         {
                           $templateName = $Template.defaultdisplayname

                           write-host "Template " -NoNewline

                           write-host -NoNewline $templateName -ForegroundColor Red

                           write-host " contains rights for " -NoNewline

                           write-host ANYONE  -ForegroundColor Red
                         }
 } 
Remove-PSDrive MyRmsAdmin -force
```


## <a name="next-steps"></a>다음 단계
[3단계 - 클라이언트 쪽 구성](migrate-from-ad-rms-phase2.md)으로 이동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]