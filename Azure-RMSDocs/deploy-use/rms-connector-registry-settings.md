---
title: Rights Management 커넥터에 대한 레지스트리 설정 - AIP
description: RMS 커넥터를 사용하는 서버의 레지스트리 설정에 대한 정보를 제공합니다. 이러한 설정을 구성할 때는 Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 것이 좋습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9334a781378ffdbe76dd9fe9d78f5db5913766d1
ms.sourcegitcommit: 373e05ff0c411d29cc5b61c36edaf5a203becc14
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="registry-setting-for-the-rights-management-connector"></a>Rights Management 커넥터에 대한 레지스트리 설정

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*


Exchange, SharePoint 또는 Windows Server를 실행하는 서버에서 수동으로 레지스트리 설정을 추가하거나 확인하려는 경우에만 다음 섹션의 표를 사용하세요. 이러한 레지스트리 설정은 [RMS 커넥터](deploy-rms-connector.md)를 사용하도록 서버를 구성합니다. 이 서버를 구성하려면 Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 것이 좋습니다.

다음 설정을 사용할 경우의 지침:

-   *\<YourTenantURL>* 은 Azure Information Protection 테넌트의 Azure Rights Management 서비스 URL입니다. 이 값을 찾으려면:

    1.  Azure Rights Management 서비스의 [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet을 실행합니다. Azure RMS용 Windows PowerShell 모듈을 아직 설치하지 않은 경우 [AADRM PowerShell 모듈 설치](install-powershell.md)를 참조하세요.

    2.  출력에서 **LicensingIntranetDistributionPointUrl** 값을 식별합니다.

        예: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  값에서 이 문자열의 **/_wmcs/licensing**을 제거합니다. 나머지 문자열은 Azure Rights Management 서비스 URL입니다. 이 예에서 Azure Rights Management 서비스 URL의 값은 다음과 같습니다.

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**
        
        다음 PowerShell 명령을 실행하여 올바른 값이 있는지 확인할 수 있습니다.
        
            (Get-AadrmConfiguration).LicensingIntranetDistributionPointUrl -match "https:\/\/[0-9A-Za-z\.-]*" | Out-Null; $matches[0]

-   *\<ConnectorFQDN>* 은 DNS에서 커넥터에 대해 정의한 부하 분산 이름입니다. **rmsconnector.contoso.com**을 예로 들 수 있습니다.

-   온-프레미스 서버와 통신하는 데 HTTPS를 사용하도록 커넥터를 구성한 경우 커넥터 URL에 HTTPS 접두사를 사용합니다. 자세한 내용은 기본 지침의 [HTTPS를 사용하도록 RMS 커넥터 구성](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https) 섹션을 참조하세요. Azure Rights Management 서비스 URL에서는 항상 HTTPS를 사용합니다.


## <a name="exchange-2016-or-exchange-2013-registry-settings"></a>Exchange 2016 또는 Exchange 2013 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*\<YourTenantURL>*/_wmcs/certification

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*\<YourTenantURL>*/_wmcs/Licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**형식:** Reg_SZ

**값:** https://*\<YourTenantURL>*


**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://*<\YourTenantURL>*


**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*


## <a name="exchange-2010-registry-settings"></a>Exchange 2010 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*<\YourTenantURL>*/_wmcs/certification

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*<\YourTenantURL>*/_wmcs/Licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**형식:** Reg_SZ

**값:** https://*<\YourTenantURL>*

**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://*<\YourTenantURL>*

**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*


## <a name="sharepoint-2016-or-sharepoint-2013-registry-settings"></a>SharePoint 2016 또는 SharePoint 2013 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**형식:** Reg_SZ

**값:** https://*<\YourTenantURL>*/_wmcs/licensing


**데이터:** SharePoint Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*<\ConnectorFQDN>*/_wmcs/licensing

- https://*<\ConnectorFQDN>*/_wmcs/licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**형식:** Reg_SZ

**값:** 기본값

**데이터:** SharePoint Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*<\ConnectorFQDN>*/_wmcs/certification

- https://*<\ConnectorFQDN>*/_wmcs/certification

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값


**데이터:** SharePoint Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*<\ConnectorFQDN>*/_wmcs/licensing

- https://*<\ConnectorFQDN>*/_wmcs/licensing




## <a name="file-server-and-file-classification-infrastructure-registry-settings"></a>파일 서버 및 파일 분류 인프라 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값

**데이터:** http://*<\ConnectorFQDN>*/_wmcs/licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**형식:** Reg_SZ

**값:** 기본값

**데이터:** http://*<\ConnectorFQDN>*/_wmcs/certification


[Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)로 돌아갑니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]