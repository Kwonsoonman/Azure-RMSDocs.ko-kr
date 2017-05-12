---
title: "AD RMS-Azure Information Protection 마이그레이션 - 1단계"
description: "AD RMS에서 Azure Information Protection으로 마이그레이션하는 과정의 첫 번째 단계로, AD RMS에서 Azure Information Protection으로 마이그레이션 1~3단계가 포함됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d954d3ee-3c48-4241-aecf-01f4c75fa62c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 587d24a005452874ca06b8fc179b25e91a7f0130
ms.sourcegitcommit: ed954c84c9009d205638f0ad54fdbfc02ef5b92c
ms.translationtype: HT
ms.contentlocale: ko-KR
---
# <a name="migration-phase-1---preparation"></a>마이그레이션 1단계 - 준비

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*

AD RMS에서 Azure Information Protection으로 마이그레이션 1단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 1~3단계를 설명하고 사용자에게 아무런 영향을 주지 않으면서 마이그레이션을 위한 환경을 준비합니다.


## <a name="step-1-download-the-azure-rights-management-administration-tool-and-identify-your-tenant-url"></a>1단계: Azure Rights Management 관리 도구 다운로드 및 테넌트 URL 식별

Microsoft 다운로드 센터로 이동하여 Windows PowerShell용 Azure Rights Management 관리 모듈이 포함된 [Azure Rights Management 관리 도구](https://go.microsoft.com/fwlink/?LinkId=257721)를 다운로드합니다. Azure RMS(Azure Rights Management)는 Azure Information Protection에 대한 데이터 보호를 제공하는 서비스입니다.

도구를 설치합니다. 지침은 [Azure Rights Management용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

> [!NOTE]
> 이전에 이 Windows PowerShell 모듈을 다운로드한 경우 다음 명령을 실행하여 버전 번호가 **2.9.0.0**: `(Get-Module aadrm -ListAvailable).Version` 이상인지 확인합니다.

일부 마이그레이션 지침을 완료하려면 *\<테넌트 URL\>*에 대한 참조가 있을 때 대체할 수 있도록 테넌트의 Azure Rights Management 서비스 URL을 알아야 합니다. Azure Rights Management 서비스 URL 형식은 **{GUID}.rms.[Region].aadrm.com**입니다.

예: **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

### <a name="to-identify-your-azure-rights-management-service-url"></a>Azure Rights Management 서비스 URL을 식별하려면

1. Azure Rights Management 서비스에 연결하고 메시지가 표시되면 테넌트의 전역 관리자 자격 증명을 입력합니다.
    
        Connect-AadrmService
    
2. 테넌트의 구성을 가져옵니다.
    
        Get-AadrmConfiguration
    
3. **LicensingIntranetDistributionPointUrl**에 대해 표시되는 값을 복사하고 이 문자열에서 `/_wmcs\licensing`을 제거합니다. 
    
    남은 것은 Azure Information Protection 테넌트의 Azure Rights Management 서비스 URL이며, 다음 마이그레이션 지침에 대개 *테넌트 URL*로 줄여서 표현되어 있습니다.

## <a name="step-2-prepare-for-client-migration"></a>2단계. 클라이언트 마이그레이션에 대한 준비

대부분 마이그레이션의 경우 모든 클라이언트를 한 번에 마이그레이션하는 은이 실용적이지 않으므로 클라이언트를 배치로 마이그레이션할 가능성이 높습니다. 즉, 특정 기간에 일부 클라이언트는 Azure Information Protection을 사용하게 되고 일부 클라이언트는 AD RMS를 사용하게 됩니다. 마이그레이션되기 전 사용자와 마이그레이션된 사용자를 모두 지원하려면 온보딩 컨트롤을 사용하고 마이그레이션 전 스크립트를 배포합니다. 이 단계는 아직 마이그레이션되지 않은 사용자가 이제 Azure Rights Management를 사용하고 있는, 마이그레이션된 사용자가 보호하는 콘텐츠를 사용할 수 있도록 마이그레이션 프로세스 중에 필요합니다.

1. 그룹을 만듭니다(예: **AIPMigrated**). 이 그룹은 Active Directory에서 만들어 클라우드로 동기화하거나 Office 365 또는 Azure Active Directory에서 만들 수 있습니다. 지금은 이 그룹에 아무 사용자도 할당하지 마세요. 이후 단계에서 사용자가 마이그레이션되면 그룹에 사용자를 추가하게 됩니다.

    이 그룹의 개체 ID를 기록해 둡니다. 이렇게 하려면 Azure AD PowerShell을 사용하면 됩니다. 예를 들어 모듈 버전 1.0의 경우 [Get-MsolGroup](/powershell/msonline/v1/Get-MsolGroup) 명령을 사용합니다. 또는 Azure Portal에서 그룹의 개체 ID를 복사할 수 있습니다.

2. 이 그룹의 사용자만 콘텐츠를 보호하는 데 Azure Rights Management를 사용할 수 있도록 온보딩 컨트롤에 대해 이 그룹을 구성합니다. 이렇게 하려면 PowerShell 세션에서 Azure Rights Management 서비스에 연결하고 메시지가 표시되면 전역 관리자 자격 증명을 지정합니다.

        Connect-Aadrmservice

    그런 다음 온보딩 컨트롤에 대해 이 그룹을 구성하여 그룹 개체 ID를 이 예제의 그룹 개체 ID로 대체하고 메시지가 표시되면 **Y**를 입력하여 확인합니다.

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501"

3. 클라이언트 마이그레이션 스크립트가 포함된 [다음 파일을 다운로드](https://go.microsoft.com/fwlink/?LinkId=524619)합니다.
    
    **ClientMigration.zip**
    
4. 파일 압축을 풀고 **PrepareClient.cmd**의 지침에 따라 AD RMS 클러스터 엑스트라넷 라이선스 URL에 대한 서버 이름이 포함되도록 합니다. 
    
    이 이름을 찾으려면: Active Directory Rights Management Services 콘솔에서 클러스터 이름을 클릭합니다. **클러스터 세부 정보**의 엑스트라넷 클러스터 URL 섹션에서 **라이선스** 값으로부터 서버 이름을 복사합니다. 예: **rmscluster.contoso.com**.

    > [!IMPORTANT]
    > 지침에는 **adrms.contoso.com**의 예제 주소를 해당 AD RMS 서버 주소로 바꾸는 내용이 포함되어 있습니다. 이렇게 할 때에는 주소의 앞뒤에 추가 공백이 없도록 주의해야 합니다. 추가 공백이 있으면 마이그레이션 스크립트가 중단되어 문제의 근본 원인으로 확인하기가 매우 어렵습니다. 일부 편집 도구는 텍스트를 붙여넣은 후 자동으로 공백을 추가합니다.
    >

5. 이 스크립트를 모든 Windows 컴퓨터에 배포하여 클라이언트 마이그레이션을 시작할 때 이제 Azure Rights Management 서비스를 사용하고 있는, 마이그레이션된 클라이언트에서 보호하는 콘텐츠를 사용하는 경우에도 아직 마이그레이션되지 않은 클라이언트가 계속 AD RMS와 통신하도록 합니다.

    그룹 정책 또는 다른 소프트웨어 배포 메커니즘을 사용하여 이 스크립트를 배포할 수 있습니다.

## <a name="step-3-prepare-your-exchange-deployment-for-migration"></a>3단계: 마이그레이션에 대한 Exchange 배포 준비

Exchange 온-프레미스 또는 Exchange Online을 사용하는 경우 이전에 Exchange를 AD RMS 배포와 통합했을 수 있습니다. 이 단계에서는 Azure RMS로 보호된 콘텐츠를 지원하기 위해 기존 AD RMS 구성을 사용하도록 구성합니다. 

[테넌트의 Azure Rights Management 서비스 URL](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url)을 확보하여 이 값으로 다음 명령의 *&lt;테넌트 URL&gt;*을 대체할 수 있도록 합니다. 

**Exchange Online을 AD RMS와 통합한 경우**: Exchange Online PowerShell 세션을 열고 다음 PowerShell 명령을 하나씩 또는 스크립트로 실행합니다.

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -internallicensingenabled $true 

**Exchange 온-프레미스를 AD RMS와 통합한 경우**: 각 Exchange 조직에 대해 먼저 각 Exchange 서버에 있는 레지스트리 값을 추가한 다음 PowerShell 명령을 실행합니다. 

Exchange 2013 및 Exchange 2016의 레지스트리 값:

**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://\<테넌트 URL\>/_wmcs/licensing

**데이터:** https://\<AD RMS 엑스트라넷 라이선스 URL\>/_wmcs/licensing

---

Exchange 2010의 레지스트리 값:

**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://\<테넌트 URL\>/_wmcs/licensing

**데이터:** https://\<AD RMS 엑스트라넷 라이선스 URL>/_wmcs/licensing

---

하나씩 또는 스크립트에서 실행할 PowerShell 명령

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -RefreshServerCertificates
    Set-IRMConfiguration -internallicensingenabled $true
    IISReset


이러한 명령을 Exchange Online 또는 Exchange 온-프레미스에 대해 실행한 후 AD RMS로 보호된 콘텐츠를 지원하도록 Exchange 배포가 구성된 경우 마이그레이션 후 Azure RMS로 보호된 콘텐츠도 지원합니다. Exchange 배포는 마이그레이션의 이후 단계까지 계속 AD RMS를 사용하여 보호된 콘텐츠를 지원합니다.


## <a name="next-steps"></a>다음 단계
[2단계 - 서버 쪽 구성](migrate-from-ad-rms-phase2.md)으로 이동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
