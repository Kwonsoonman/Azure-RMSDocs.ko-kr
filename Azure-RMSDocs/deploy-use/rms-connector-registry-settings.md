---
title: "Rights Management 커넥터에 대한 레지스트리 설정 - AIP"
description: "RMS 커넥터를 사용하는 서버의 레지스트리 설정에 대한 정보를 제공합니다. 이러한 설정을 구성할 때는 Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 것이 좋습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: b894be1ef3d41a9faf6c3fd3b3fd8c5b94a62517
ms.lasthandoff: 02/24/2017


---


# <a name="registry-setting-for-the-rights-management-connector"></a>Rights Management 커넥터에 대한 레지스트리 설정

>*적용 대상: Azure Information Protection, Office 365*


Exchange, SharePoint 또는 Windows Server를 실행하는 서버에서 수동으로 레지스트리 설정을 추가하거나 확인하려는 경우에만 다음 섹션의 표를 사용하세요([RMS 커넥터](deploy-rms-connector.md)를 사용하도록 서버가 구성됨). 이 서버를 구성하려면 Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 것이 좋습니다.

다음 설정을 사용할 경우의 지침:

-   *MicrosoftRMSURL* 은 조직의 Microsoft RMS 서비스 URL입니다. 이 값을 찾으려면:

    1.  Azure RMS에 대해 [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet을 실행합니다. Azure RMS용 Windows PowerShell 모듈을 아직 설치하지 않은 경우 [Azure 권한 관리용 Windows PowerShell 설치](install-powershell.md)를 참조하세요.

    2.  출력에서 **LicensingIntranetDistributionPointUrl** 값을 식별합니다.

        예: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  값에서 이 문자열의 **/_wmcs/licensing**을 제거합니다. 나머지 문자열이 Microsoft RMS URL입니다. 이 예에서 Microsoft RMS URL 값은 다음과 같습니다.

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

-   *ConnectorFQDN*은 DNS에서 커넥터에 대해 정의한 부하 분산 이름입니다. **rmsconnector.contoso.com**을 예로 들 수 있습니다.

-   온-프레미스 서버와 통신하는 데 HTTPS를 사용하도록 커넥터를 구성한 경우 커넥터 URL에 HTTPS 접두사를 사용합니다. 자세한 내용은 기본 지침의 [HTTPS를 사용하도록 RMS 커넥터 구성](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https) 섹션을 참조하세요. Microsoft RMS URL에는 항상 HTTPS가 사용됩니다.


## <a name="exchange-2016-or-exchange-2013-registry-settings"></a>Exchange 2016 또는 Exchange 2013 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**형식:** Reg_SZ

**값:** https://*MicrosoftRMSURL*


**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://*MicrosoftRMSURL*


**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*


## <a name="exchange-2010-registry-settings"></a>Exchange 2010 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값

**데이터:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**형식:** Reg_SZ

**값:** https://*MicrosoftRMSURL*

**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**형식:** Reg_SZ

**값:** https://*MicrosoftRMSURL*

**데이터:** Exchange Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*


## <a name="sharepoint-2016-or-sharepoint-2013-registry-settings"></a>SharePoint 2016 또는 SharePoint 2013 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**형식:** Reg_SZ

**값:** https://*MicrosoftRMSURL*/_wmcs/licensing


**데이터:** SharePoint Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*ConnectorFQDN*/_wmcs/licensing

- https://*ConnectorFQDN*/_wmcs/licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**형식:** Reg_SZ

**값:** 기본값

**데이터:** SharePoint Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*ConnectorFQDN*/_wmcs/certification

- https://*ConnectorFQDN*/_wmcs/certification

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값


**데이터:** SharePoint Server에서 RMS 커넥터로의 연결에 HTTP를 사용하는지 또는 HTTPS를 사용하는지에 따라 다음 중 하나:

- http://*ConnectorFQDN*/_wmcs/licensing

- https://*ConnectorFQDN*/_wmcs/licensing




## <a name="file-server-and-file-classification-infrastructure-registry-settings"></a>파일 서버 및 파일 분류 인프라 레지스트리 설정

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**형식:** Reg_SZ

**값:** 기본값

**데이터:** http://*ConnectorFQDN*/_wmcs/licensing

---

**레지스트리 경로:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**형식:** Reg_SZ

**값:** 기본값

**데이터:** http://*ConnectorFQDN*/_wmcs/certification


[Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)로 돌아갑니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
