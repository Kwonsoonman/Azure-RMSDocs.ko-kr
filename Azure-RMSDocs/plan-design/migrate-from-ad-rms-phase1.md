---
title: "AD RMS에서 Azure 권한 관리로 마이그레이션 - 1단계 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/23/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: defe008a9b78026ccac584bb06762228456a2916


---

# 마이그레이션 1단계 - AD RMS에 대한 서버 쪽 구성

*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*

AD RMS에서 Azure 권한 관리(Azure RMS)로 마이그레이션 1단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure 권한 관리로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 1-4단계를 설명합니다.


## 1단계: Azure 권한 관리의 관리 도구 다운로드
Microsoft 다운로드 센터로 이동하여 Windows PowerShell용 Azure RMS 관리 모듈이 포함된 [Azure Rights Management 관리 도구를 다운로드](http://go.microsoft.com/fwlink/?LinkId=257721)합니다.

도구를 설치합니다. 지침은 [Azure 권한 관리용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

## 2단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기
이 단계는 다음의 두 부분으로 이루어진 프로세스입니다.

1.  TPD(트러스트된 게시 도메인)를 .xml 파일로 내보내 AD RMS에서 구성 데이터를 내보냅니다. 이 프로세스는 모든 마이그레이션에서 동일합니다.

2.  구성 데이터를 Azure RMS로 가져옵니다. 현재 AD RMS 배포 구성 및 Azure RMS 테넌트 키에 대한 기본 설정 토폴로지에 따라 이 단계의 프로세스가 다를 수 있습니다.

### AD RMS에서 구성 데이터 내보내기
조직에 대해 보호된 콘텐츠가 있는 트러스트된 모든 게시 도메인에 대해 모든 AD RMS 클러스터에서 다음 절차를 수행합니다. 라이선스 전용 클러스터에서는 이 작업을 수행할 필요가 없습니다.

> [!NOTE]
> Windows Server 2003 Rights Management를 사용하는 경우 이러한 지침 대신 [Windows RMS에서 다른 인프라의 AD RMS로 마이그레이션](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) 문서에 있는 [SLC, TUD, TPD 및 RMS 개인 키 내보내기](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) 절차를 따릅니다.

#### 구성 데이터(트러스트된 게시 도메인 정보)를 내보내려면

1.  AD RMS 관리 권한이 있는 사용자로 AD RMS 클러스터에 로그온합니다.

2.  AD RMS 관리 콘솔(**Active Directory Rights Management Services**)에서 AD RMS 클러스터 이름을 확장하고, **트러스트 정책**를 확장한 후 **트러스트된 게시 도메인**을 클릭합니다.

3.  결과 창에서 트러스트된 게시 도메인을 선택하고 작업 창에서 **트러스트된 게시 도메인 내보내기**를 클릭합니다.

4.  **트러스트된 게시 도메인 내보내기** 대화 상자에서 다음을 수행합니다.

    -   **다른 이름으로 저장** 을 클릭하고 선택한 경로와 파일 이름으로 저장합니다. 파일 이름 확장명으로 **.xml**을 지정해야 합니다. 파일 이름 확장명은 자동으로 추가되지 않습니다.

    -   강력한 암호를 지정하고 확인합니다. 나중에 구성 데이터를 Azure RMS로 가져올 때 필요하므로, 이 암호를 기억해둡니다.

    -   RMS 버전 1.0에서 트러스트된 도메인 파일을 저장하려면 이 확인란을 선택하지 않도록 합니다.

트러스트된 모든 게시 도메인을 내보냈으면 이 데이터를 Thales에서 Azure RMS HSM(하드웨어 보안 모듈)로 가져오는 절차를 시작할 준비가 되었습니다. 자세한 내용은 

### 구성 데이터를 Azure RMS로 가져오기
이 단계의 정확한 절차는 현재 AD RMS 배포 구성 및 Azure RMS 테넌트 키에 대한 기본 설정 토폴로지에 따라 달라집니다.

현재 AD RMS 배포는 SLC(서버 사용 허가자 인증서) 키에 대해 다음 구성 중 하나를 사용합니다.

-   AD RMS 데이터베이스의 암호 보호. 이것이 기본 구성입니다.

-   Thales HSM(하드웨어 보안 모듈)을 사용한 HSM 보호.

-   Thales 이외의 공급업체가 제공한 HSM(하드웨어 보안 모듈)을 사용한 HSM 보호.

-   외부 암호화 공급자를 사용하여 암호 보호.

> [!NOTE]
> AD RMS에서 하드웨어 보안 모듈을 사용하는 방법에 대한 자세한 내용은 [하드웨어 보안 모듈에서 AD RMS 사용](http://technet.microsoft.com/library/jj651024.aspx)을 참조하세요.

두 Azure RMS 테넌트 키 토폴로지 옵션은 Microsoft에서 테넌트 키를 관리하는 방식(**Microsoft 관리**) 또는 사용자가 테넌트 키를 관리하는 방식(**고객 관리**)입니다. 자체 Azure RMS 테넌트 키를 관리할 경우를 BYOK("bring your own key")라고도 하며, Thales의 HSM(하드웨어 보안 모듈)이 필요합니다. 자세한 내용은 [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md) 문서를 참조하세요.

> [!IMPORTANT]
> Exchange Online은 현재 Azure RMS BYOK와 호환되지 않습니다.  마이그레이션 후에 BYOK를 사용하고 Exchange Online을 사용하려는 경우 이 구성에서 Exchange Online에 대한 IRM 기능이 축소되는 방식을 이해해야 합니다. [BYOK 가격 및 제한 사항](byok-price-restrictions.md)에 제공된 정보를 검토하여 마이그레이션에 가장 적합한 Azure RMS 테넌트 키 토폴로지를 선택합니다.

다음 테이블을 사용하여 마이그레이션에 사용할 절차를 식별하세요. 목록에 없는 조합은 지원되지 않습니다.

|현재 AD RMS 배포|선택한 Azure RMS 테넌트 키 토폴로지|마이그레이션 지침|
|-----------------------------|----------------------------------------|--------------------------|
|AD RMS 데이터베이스의 암호 보호|Microsoft 관리|이 표 다음에 나오는 **소프트웨어 보호된 키-소프트웨어 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이것은 가장 간단한 마이그레이션 경로이며, Azure RMS로 구성 데이터를 전송하기만 하면 됩니다.|
|Thales nShield HSM(하드웨어 보안 모듈)을 사용한 HSM 보호|고객 관리(BYOK)|이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이 작업을 위해서는 BYOK 도구 집합과, 온-프레미스 HSM의 키를 Azure RMS HSM으로 전송한 다음 구성 데이터를 Azure RMS으로 전송하는 두 단계가 필요합니다.|
|AD RMS 데이터베이스의 암호 보호|고객 관리(BYOK)|이 표 다음에 나오는 **소프트웨어 보호된 키-HSM 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이 작업을 위해서는 BYOK 도구 집합과, 소프트웨어 키를 먼저 추출하고 온-프레미스 HSM으로 가져온 다음, 온-프레미스 HSM의 키를 Azure RMS HSM으로 전송하고, 마지막으로 구성 데이터를 Azure RMS로 전송하는 세 단계가 필요합니다.|
|Thales 이외의 공급업체가 제공한 HSM(하드웨어 보안 모듈)을 사용한 HSM 보호|고객 관리(BYOK)|이 HSM에서 Thales nShield HSM(하드웨어 보안 모듈)로 키를 전송하는 방법에 대한 지침은 HSM 공급업체에 문의하세요. 그런 다음 이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키** 마이그레이션 절차의 지침을 따르세요.|
|외부 암호화 공급자를 사용하여 암호 보호|고객 관리(BYOK)|Thales nShield HSM(하드웨어 보안 모듈)로 키를 전송하는 방법에 대한 지침은 암호화 공급자의 공급업체에 문의하세요. 그런 다음 이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키** 마이그레이션 절차의 지침을 따르세요.|
이러한 절차를 시작하기 전에 트러스트된 게시 도메인을 내보낼 때 만든 .xml 파일에 액세스할 수 있는지 확인하세요. 예를 들어, 이러한 파일은 AD RMS 서버에서 인터넷에 연결된 워크스테이션으로 가져오는 USB 드라이브에 저장되어 있을 수 있습니다.

> [!NOTE]
> 하지만 이 데이터에 개인 키가 포함되어 있으므로 이러한 파일을 저장한 후 최적의 보안 권장 방법으로 파일을 보호합니다.


2단계를 완료하려면 마이그레이션 경로에 대한 지침을 선택합니다. 


- [소프트웨어 키-소프트웨어 키](migrate-softwarekey-to-softwarekey.md)
- [HSM 키-HSM 키](migrate-hsmkey-to-hsmkey.md)
- [소프트웨어 키-HSM 키](migrate-softwarekey-to-hsmkey.md)


## 3단계. RMS 테넌트 활성화
이 단계에 대한 지침은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md) 문서에 자세히 나와 있습니다.


> [!TIP]
> Office 365 구독이 있는 경우 Office 365 관리 센터 또는 Azure 클래식 포털에서 Azure RMS를 활성화할 수 있습니다. 이 관리 포털을 사용하여 다음 단계를 완료하게 되므로 Azure 클래식 포털을 사용하는 것이 좋습니다.

**Azure RMS 테넌트가 이미 활성화되어 있으면 어떻게 되나요?** 조직에 대해 Azure RMS 서비스가 이미 활성화된 경우 사용자는 이미 Azure RMS를 사용하여 AD RMS의 기존 키(및 템플릿) 대신 자동으로 생성된 테넌트 키(및 기본 템플릿)로 콘텐츠를 보호하고 있을 수 있습니다. 인트라넷에서 잘 관리되는 컴퓨터는 AD RMS 인프라에 대해 자동으로 구성되므로 여기에 해당되지 않을 수 있습니다. 하지만 작업 그룹 컴퓨터 또는 인트라넷에 자주 연결되지 않는 컴퓨터는 여기에 해당될 수 있습니다. 아쉽게도 이러한 컴퓨터를 식별하는 것은 어려운 일이므로 AD RMS에서 구성 데이터를 가져오기 전에 서비스를 활성화하지 않는 것이 좋습니다.

5단계에서 설명한 대로 Azure RMS 테넌트가 이미 활성화되어 있고 이러한 컴퓨터를 식별할 수 있으면 이러한 컴퓨터에서 CleanUpRMS_RUN_Elevated.cmd 스크립트를 실행해야 합니다. 이 스크립트를 실행하면 사용자 환경이 강제로 다시 초기화되므로 업데이트된 테넌트 키와 가져온 템플릿을 다운로드합니다.

또한 마이그레이션 후 사용하고 싶은 사용자 지정 템플릿을 만든 경우 이 템플릿을 내보냈다가 가져와야 합니다. 이 절차는 다음 단계에서 다룹니다. 

## 4단계. 가져온 템플릿 구성
가져온 템플릿의 기본 상태는 **보관됨**이므로 사용자가 Azure RMS에서 이러한 템플릿을 사용할 수 있도록 하려면 이 상태를 **게시됨** 으로 변경해야 합니다.

AD RMS에서 가져오는 템플릿은 Azure 클래식 포털에서 만들 수 있는 사용자 지정 템플릿과 모양 및 동작이 유사합니다. 가져온 템플릿을 사용자가 응용 프로그램에서 보고 선택할 수 있도록 게시하기 위해 변경하려면 [Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

새로 가져온 템플릿을 게시하는 것 외에도 마이그레이션을 계속하기 전에 수행해야 하는 두 가지 중요한 템플릿 변경 사항이 있습니다. 마이그레이션 프로세스 중에 사용자에게 보다 일관된 환경을 제공하려면, 가져온 템플릿을 추가적으로 변경하지 않도록 하고, Azure RMS와 함께 제공되는 2개의 기본 템플릿을 게시하거나 새 템플릿을 만들지 않도록 합니다. 대신 마이그레이션 프로세스가 완료되고 AD RMS 서버를 서비스 해제할 때까지 기다립니다.

이 단계에 대해 수행해야 하는 템플릿 변경 작업:

- 마이그레이션 전에 Azure RMS에서 사용자 지정 템플릿을 만든 경우 수동으로 내보냈다가 가져와야 합니다.

- AD RMS의 템플릿에서 **ANYONE** 그룹을 사용한 경우에는 해당 그룹 및 권한을 수동으로 추가해야 합니다.

## 마이그레이션 전에 사용자 지정 템플릿을 만든 경우의 프로시저

Azure RMS를 활성화하기 전 또는 후, 마이그레이션 전에 사용자 지정 템플릿을 만든 경우에는 템플릿이 **게시됨**으로 설정되었더라도 마이그레이션 후 사용자가 템플릿을 사용할 수 없습니다. 사용자가 사용할 수 있도록 하려면 먼저 다음을 수행해야 합니다. 

1. [Get AadrmTemplate](https://msdn.microsoft.com/library/dn727079.aspx)을 실행하여 이러한 템플릿을 식별하고 해당 템플릿 ID를 기록합니다. 

2. Azure RMS PowerShell cmdlet인 [Export-AadrmTemplate](https://msdn.microsoft.com/library/dn727078.aspx)을 사용하여 템플릿을 내보냅니다.

3. Azure RMS PowerShell cmdlet인 [Import-AadrmTemplate](https://msdn.microsoft.com/library/dn727077.aspx)을 사용하여 템플릿을 가져옵니다.

이렇게 하면 마이그레이션 후에 만든 다른 템플릿으로 하듯이 이 템플릿을 게시하거나 보관할 수 있습니다.


## AD RMS의 템플릿에서 **ANYONE** 그룹을 사용한 경우 프로시저

AD RMS의 템플릿이 **ANYONE** 그룹을 사용하는 경우 이 그룹은 Azure RMS에 템플릿을 가져올 때 자동으로 제거됩니다. 따라서 가져온 템플릿에 해당 그룹 또는 사용자와 동일한 권한을 수동으로 추가해야 합니다. Azure RMS에 해당하는 그룹의 이름은 **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@<tenant_name>.onmicrosoft.com**입니다. 예를 들어 Contoso에 대한 이 그룹은 **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**과 같을 수 있습니다.

AD RMS 템플릿에 ANYONE 그룹이 포함되어 있는지 여부가 확실하지 않은 경우 다음의 샘플 Windows PowerShell 스크립트를 사용하여 이러한 템플릿을 식별할 수 있습니다. AD RMS와 함께 Windows PowerShell을 사용하는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용하여 AD RMS 관리](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx)를 참조하세요.

Azure 클래식 포털에서 기본 권한 정책 템플릿 중 하나를 복사하고 **권한** 페이지에서 **사용자 이름**을 확인하면 조직에서 자동으로 생성된 그룹을 볼 수 있습니다. 그러나 Azure 클래식 포털을 사용하여 이 그룹을 수동으로 만들거나 가져온 템플릿에 추가할 수는 없습니다. 대신에 다음과 같은 Azure RMS PowerShell 옵션 중 하나를 사용해야 합니다.

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) PowerShell cmdlet을 사용하여 "AllStaff" 그룹 및 권한을 권한 정의 개체로 정의하고, ANYONE 그룹 외에도 원래 템플릿의 각 그룹 또는 권한이 이미 부여된 사용자에 대해 이 명령을 다시 실행합니다. 그런 다음 [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) cmdlet을 사용하여 이러한 모든 권한 정의 개체를 템플릿에 추가합니다.

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet을 사용하여 "AllStaff" 그룹 및 권한을 기존 그룹 및 권한에 추가할 수 있도록 편집할 수 있는 .XML 파일에 템플릿을 내보낸 다음 [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) cmdlet을 사용하여 이 변경 내용을 Azure RMS로 다시 가져옵니다.

> [!NOTE]
> "AllStaff"의 이러한 동등한 그룹이 AD RMS의 ANYONE 그룹과 정확히 동일하지는 않습니다. "AllStaff" 그룹에는 Azure 테넌트의 모든 사용자가 포함되지만 ANYONE 그룹에는 조직의 외부에 있을 수 있는 인증된 모든 사용자가 포함됩니다.
> 
> 두 그룹 간의 이러한 차이 때문에 "AllStaff" 그룹뿐 아니라 외부 사용자도 추가해야 할 수 있습니다. 그룹에 대한 외부 전자 메일 주소는 현재 지원되지 않습니다.


### ANYONE 그룹을 포함하는 AD RMS 템플릿을 식별하기 위한 샘플 Windows PowerShell 스크립트
이 섹션에는 이전 섹션에서 설명한 것과 같이 정의된 ANYONE 그룹이 있는 AD RMS 템플릿을 식별하는 데 도움이 되는 샘플 스크립트가 포함되어 있습니다.

**고지 사항:** 이 샘플 스크립트는 Microsoft 표준 지원 프로그램 또는 서비스를 통해 지원되지 않습니다. 이 샘플 스크립트는 어떤 종류의 보증도 없이 있는 그대로 제공됩니다.*

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


## 다음 단계
[2단계 - 클라이언트 쪽 구성](migrate-from-ad-rms-phase2.md)으로 이동합니다.




<!--HONumber=Jul16_HO3-->


