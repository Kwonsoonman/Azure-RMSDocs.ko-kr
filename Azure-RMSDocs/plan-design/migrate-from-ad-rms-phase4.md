---
title: AD RMS-Azure Information Protection 마이그레이션 - 4단계
description: AD RMS에서 Azure Information Protection으로 마이그레이션하는 과정의 네 번째 단계로, AD RMS에서 Azure Information Protection으로 마이그레이션 8~9단계가 포함됩니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 7aaec205863bf855cc68887f3eafed27386ee49f
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="migration-phase-4---supporting-services-configuration"></a>마이그레이션 4단계 - 지원 서비스 구성

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


AD RMS에서 Azure Information Protection으로 마이그레이션 4단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 8-9단계를 설명합니다.



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>8단계: Exchange Online에 대한 IRM 통합 구성

> [!IMPORTANT]
> 마이그레이션된 사용자가 보호된 이메일에 대해 선택하는 받는 사람을 제어할 수 없으므로 조직의 모든 사용자와 메일 사용이 가능한 그룹은 Azure Information Protection을 통해 사용할 수 있는 Azure AD 계정이 있습니다. [추가 정보](prepare.md)

선택한 Azure Information Protection 테넌트 키 토폴로지와 별개로 다음을 수행하세요.

1. 사용자가 AD RMS 보호를 사용하여 전송된 이메일을 읽을 수 있는지 확인하려면 AD RMS 클러스터에 대한 DNS SRV 레코드가 있는지 확인합니다. 7단계에서 클라이언트 재구성에 대한 DNS SRV 레코드를 만들지 않은 경우 이제 Exchange Online을 지원하도록 이 레코드를 만듭니다. [지침](migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection)

2. Exchange Online [Get-IRMConfiguration](https://technet.microsoft.com/library/dd776120(v=exchg.160\).aspx) 명령을 실행합니다. 이 명령을 실행하기 위해 도움말이 필요한 경우 [Exchange Online: IRM 구성](/..deploy-use/configure-office365.md#exchange-online-irm-configuration)에서 단계별 지침을 참조하세요.
    
    출력에서 **AzureRMSLicensingEnabled**를 **True**로 설정했는지 확인합니다.
    
    - AzureRMSLicensingEnabled를 **True**로 설정하면 이 단계에서 추가 구성이 필요하지 않습니다. 
    
    - AzureRMSLicensingEnabled를 **False**로 설정하면 [Azure Information Protection을 기반으로 구축된 새로운 Office 365 메시지 암호화 기능 설정](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)에서 명령을 실행하세요. 

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
        $list += "<Your Tenant URL>/_wmcs/licensing"
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