---
title: "AD RMS-Azure Information Protection 마이그레이션 - 4단계"
description: "AD RMS에서 Azure Information Protection으로 마이그레이션하는 과정의 네 번째 단계로, AD RMS에서 Azure Information Protection으로 마이그레이션 8~9단계가 포함됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 51a689248834f2578655d62752c19b7a387068a5
ms.sourcegitcommit: 237ce3a0cc4921da5a08ed5753e6491403298194
translationtype: HT
---
# <a name="migration-phase-4---supporting-services-configuration"></a>마이그레이션 4단계 - 지원 서비스 구성

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*


AD RMS에서 Azure Information Protection으로 마이그레이션 4단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 8-9단계를 설명합니다.



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>8단계: Exchange Online에 대한 IRM 통합 구성

이전에 AD RMS에서 Exchange Online으로 TDP를 가져온 경우 Azure Information Protection으로 마이그레이션한 후에 템플릿 및 정책 충돌을 방지하기 위해 이 TDP를 제거해야 합니다. 이렇게 하려면 Exchange Online에서 [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) cmdlet을 사용합니다.

Azure Information Protection 테넌트 키 토폴로지로 **Microsoft 관리**를 선택한 경우

1. [Office 365: 클라이언트 및 온라인 서비스 구성](../deploy-use/configure-office365.md) 문서에서 [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration) 섹션의 지침을 사용합니다. 이 섹션에는 Exchange Online 서비스에 연결하고, Azure Information Protection에서 테넌트 키를 가져오고, Exchange Online에 대해 IRM 기능을 사용하도록 설정하는 일반적인 명령이 포함되어 있습니다. 이러한 단계를 완료한 후에 Exchange Online에서 전체 Azure Rights Management 보호 기능을 사용할 수 있게 됩니다.

2. Exchange Online에 대해 IRM을 사용하도록 설정하기 위한 표준 구성 외에 다음 PowerShell 명령을 실행하여 사용자가 AD RMS 보호를 사용하여 전송된 메일을 읽을 수 있도록 합니다.

    *\<yourcompany.domain>*을 조직 도메인 이름으로 대체합니다.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation
        $list += "https://adrms.<yourcompany.domain>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list
        Set-IRMConfiguration -internallicensingenabled $false
        Set-IRMConfiguration -internallicensingenabled $true


Azure Information Protection 테넌트 키 토폴로지로 **고객 관리(BYOK)**를 선택한 경우

-   [BYOK 가격 및 제한 사항](byok-price-restrictions.md) 문서에 설명된 대로 Exchange Online에서 사용할 수 있는 Rights Management 보호 기능이 줄어듭니다.


## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>9단계: Exchange Server 및 SharePoint Server에 대한 IRM 통합 구성

AD RMS를 통해 Exchange Server 또는 SharePoint Server의 IRM(정보 권한 관리) 기능을 사용한 경우 온-프레미스 서버와 Azure Information Protection의 보호 서비스 사이에서 통신 인터페이스(릴레이) 역할을 하는 Rights Management(RMS) 커넥터를 배포해야 합니다.

이 단계에서는 커넥터를 설치 및 구성하고, Exchange 및 SharePoint에 대해 IRM을 사용하지 않도록 설정하고, 커넥터를 사용하도록 이러한 서버를 구성하는 방법을 설명합니다. 마지막으로, AD RMS 데이터 구성 파일(.xml)을 메일 메시지를 보호하는 데 사용된 Azure Information Protection으로 가져온 경우 모든 트러스트된 게시 도메인 URL을 RMS 커넥터로 리디렉션하도록 Exchange Server 컴퓨터의 레지스트리를 수동으로 편집해야 합니다.

> [!NOTE]
> 시작하기 전에 [Azure RMS를 지원하는 온-프레미스 서버](../get-started/requirements-servers.md)에서 Azure Rights Management 서비스가 지원하는 온-프레미스 서버 버전을 확인합니다.

### <a name="install-and-configure-the-rms-connector"></a>RMS 커넥터 설치 및 구성

[Azure Rights Management 커넥터 배포](../deploy-use/deploy-rms-connector.md) 문서의 지침을 사용하여 1~4단계를 수행합니다. 커넥터 지침에서 아직 5단계는 시작하지 마세요. 

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Exchange Server에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성 제거

1.  각 Exchange Server에서 **\ProgramData\Microsoft\DRM\Server\S-1-5-18** 폴더를 찾아 해당 폴더의 항목을 모두 삭제합니다.

2. Exchange Server 중 하나에서 다음 PowerShell 명령을 실행하여 사용자가 Azure Rights Management로 보호되는 메일을 읽을 수 있게 합니다.

    이러한 명령을 실행하기 전에 *\<테넌트 URL>*을 해당 Azure Rights Management 서비스 URL로 대체합니다.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation 
        $list + "<Your Tenant URL>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list

3.  이제 내부 받는 사람에게 전송되는 메시지에 대해 IRM 기능을 사용하지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

4. 그런 다음 같은 cmdlet을 사용하여 Microsoft Office Outlook Web App 및 Microsoft Exchange ActiveSync에서 IRM을 사용하지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  마지막으로 동일한 cmdlet을 사용하여 캐시된 모든 인증서를 지웁니다.

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  예를 들어 각 Exchange Server에서 관리자 권한으로 명령 프롬프트를 실행하고 **iisreset**을 입력하여 IIS를 초기화합니다.

### <a name="disable-irm-on-sharepoint-servers-and-remove-ad-rms-configuration"></a>SharePoint Server에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성 제거

1.  RMS로 보호된 라이브러리에서 체크 아웃된 문서가 없는지 확인합니다. 체크 아웃된 문서가 있는 경우 이 절차가 끝나면 액세스할 수 없게 됩니다.

2.  Sharepoint 중앙 관리 웹 사이트의 **빠른 실행** 섹션에서 **보안**을 클릭합니다.

3.  **보안** 페이지의 **정보 정책** 섹션에서 **정보 권한 관리 구성**을 클릭합니다.

4.  **정보 권한 관리** 페이지의 **정보 권한 관리** 섹션에서 **이 서버에서 IRM 사용 안 함**을 선택하고 **확인**을 클릭합니다.

5.  각 SharePoint Server 컴퓨터에서 \ProgramData\Microsoft\MSIPC\Server\\<*SharePoint Server를 실행하는 계정의 SID>* 폴더의 내용을 삭제합니다.

### <a name="configure-exchange-and-sharepoint-to-use-the-connector"></a>커넥터를 사용하도록 Exchange 및 SharePoint 구성

1. RMS 커넥터를 배포하기 위한 지침: [5단계: RMS 커넥터를 사용하도록 서버 구성](../deploy-use/configure-servers-rms-connector.md)으로 돌아갑니다.

    SharePoint Server만 있는 경우 바로 [다음 단계](#next-steps)로 이동하여 마이그레이션을 계속합니다. 

2. 각 Exchange Server에서 가져온 각 구성 데이터 파일(.xml)에 대한 다음 섹션에서 레지스트리 키를 수동으로 추가하여 트러스트된 게시 도메인 URL을 RMS 커넥터로 리디렉션합니다. 이러한 레지스트리 항목은 마이그레이션에만 관련되며 Microsoft RMS 커넥터용 서버 구성 도구를 통해 추가되지 않습니다.

    이와 같이 레지스트리를 편집할 때는 다음 지침을 따르세요.

    -   *커넥터 FQDN*을 DNS에서 커넥터에 대해 정의한 이름으로 바꿉니다. **rmsconnector.contoso.com**을 예로 들 수 있습니다.

    -   온-프레미스 서버와 통신하는 데 HTTP 또는 HTTPS 중 어느 것을 사용하도록 커넥터를 구성했는지에 따라 커넥터 URL에 대해 HTTP 또는 HTTPS 접두사를 사용합니다.

#### <a name="registry-edits-for-exchange"></a>Exchange에 대한 레지스트리 편집

모든 Exchange Server의 경우 준비 단계 중에 LicenseServerRedirection에 대해 추가한 레지스트리 값을 제거합니다. 이러한 값은 다음 경로에 추가되었습니다.

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection


Exchange 2013 및 Exchange 2016의 경우 - 레지스트리 편집 1:


**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://\<AD RMS 인트라넷 라이선스 URL\>/_wmcs/licensing

**데이터**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://\<커넥터 FQDN\>/_wmcs/licensing

- https://\<커넥터 FQDN\>/_wmcs/licensing


---

Exchange 2013의 경우 - 레지스트리 편집 2:

**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 

**형식:** Reg_SZ

**값:** https://\<AD RMS 엑스트라넷 라이선스 URL\>/_wmcs/licensing

**데이터**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://\<커넥터 FQDN\>/_wmcs/licensing

- https://\<커넥터 FQDN\>/_wmcs/licensing

---

Exchange 2010의 경우 - 레지스트리 편집 1:


**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://\<AD RMS 인트라넷 라이선스 URL\>/_wmcs/licensing

**데이터**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://\<커넥터 FQDN\>/_wmcs/licensing

- https://\<커넥터 이름\>/_wmcs/licensing


---

Exchange 2010의 경우 - 레지스트리 편집 2:


**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://\<AD RMS 엑스트라넷 라이선스 URL\>/_wmcs/licensing

**데이터**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://\<커넥터 FQDN\>/_wmcs/licensing

- https://\<커넥터 FQDN\>/_wmcs/licensing

---


## <a name="next-steps"></a>다음 단계
마이그레이션을 계속하려면 [5단계 - 마이그레이션 후 작업](migrate-from-ad-rms-phase5.md)으로 이동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]