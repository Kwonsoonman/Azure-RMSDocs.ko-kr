---
title: "Azure Information Protection에 대한 요구 사항 | Azure Information Protection"
description: "Azure Information Protection을 조직에 배포하기 위한 필수 구성 요소를 식별합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/13/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 55895dd6fd0e106c33914a232e2d00d98e8a154a
ms.openlocfilehash: bb74ea0e88430cfb784b3f88bd3e6fd75373b9a2


---

# <a name="requirements-for-azure-information-protection"></a>Azure Information Protection에 대한 요구 사항

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection을 조직에 배포하기 전에 다음 필수 구성 요소가 준비되어 있는지 확인하세요. 

|요구 사항|추가 정보|
|---------------|--------------------|
|Azure Information Protection 구독|Azure Information Protection 사이트에서 [구독 정보](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) 및 [기능 목록](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features)을 검토하여 조직의 구독에 사용하려는 Azure Information Protection 기능이 포함되어 있는지 확인하세요.|
|Azure Active Directory|Azure Information Protection에 대해 사용자 인증을 지원하려면 조직에 Azure AD(Azure Active Directory)가 있어야 합니다. 또한 온-프레미스 디렉터리(AD DS)의 사용자 계정을 사용하려는 경우 디렉터리 통합도 구성해야 합니다.<br /><br />MFA(Multi-Factor Authentication)는 필수 클라이언트 소프트웨어 및 올바르게 구성된 MFA 지원 인프라가 있는 경우 Azure Information Protection에서 지원됩니다.<br /><br />자세한 내용은 [Azure Information Protection에 대한 Azure Active Directory 요구 사항](requirements-azure-ad.md)을 참조하세요.|
|클라이언트 장치|사용자에게 Azure Information Protection을 지원하는 운영 체제를 실행하는 클라이언트 장치(컴퓨터 또는 모바일 장치)가 있어야 합니다.<br /><br />다음은 사용자가 Office 문서 및 메일을 분류하여 레이블링할 수 있도록 Azure Information Protection 클라이언트를 지원하는 장치입니다.<br /><br />- Windows 10(x86, x64)<br /><br />- Windows 8.1(x86, x64)<br /><br />- Windows 8(x86, x64)<br /><br />- Windows 7 서비스 팩 1(x86, x64)<br /><br />이 클라이언트에서 Azure Rights Management 서비스를 통해 데이터를 보호하는 경우 Azure Rights Management 서비스를 지원하는 동일한 장치(Windows, Mac, iOS, Android)에서 이 클라이언트를 사용할 수 있습니다. <br /><br />Azure Rights Management 서비스를 지원하는 장치에 대한 자세한 내용은 [Azure Rights Management 데이터 보호를 지원하는 클라이언트 장치](../get-started/requirements-client-devices.md)를 참조하세요.|
|응용 프로그램|Azure Information Protection 클라이언트는 다음 Office 제품군의 Office 응용 프로그램인 **Word**, **Excel**, **PowerPoint** 및 **Outlook**을 사용하여 파일 및 메일의 레이블을 지정하고 보호할 수 있습니다.<br /><br /> - Office 365 ProPlus(2016 앱 또는 2013 앱 포함)(간편 실행 또는 Windows Installer 기반 설치)<br /><br />- Office Professional Plus 2016<br /><br />- Office Professional Plus 2013 서비스 팩 1<br /><br />- Office Professional Plus 2010<br /><br />데이터 보호 서비스를 지원하는 Office 버전에 대한 자세한 내용은 [Azure Rights Management 데이터 보호를 지원하는 응용 프로그램](requirements-applications.md)을 참조하세요.|
|인터넷 및 종속된 클라우스 서비스 연결을 지원하는 인프라|특정 연결을 허용하기 위해 구성해야 하는 방화벽 또는 유사한 중개 네트워크 장치가 있는 경우 Office 문서 [Office 365 URL 및 IP 주소 범위](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)의 [Office 365 포털 및 공유](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US#bkmk_portal-identity) 섹션에 있는 **Azure RMS(권한 관리)** 정보를 참조하세요.<br /><br />이 Office 문서의 지침에 따라 RSS 피드를 구독하여 이 정보에 대한 최신 변경 내용을 확인하세요.<br /><br />Office 문서의 정보 외에 Azure Information Protection과 관련하여 다음 사항에 유의하세요.<br /><br />- TCP 443에서 **api.informationprotection.azure.com**으로의 HTTPS 트래픽을 허용합니다.<br /><br />- TLS 클라이언트-서비스 연결을 종료하지 마세요(예를 들어 패킷 수준 조사를 수행하려는 경우). 연결을 종료하면 Azure RMS와의 통신 보안 유지를 위해 Microsoft에서 관리하는 CA와 함께 RMS 클라이언트가 사용하는 인증서 고정이 끊어집니다.<br /><br />- 인증이 필요한 웹 프록시를 사용하는 경우 사용자의 Active Directory 로그온 자격 증명으로 통합된 Windows 인증을 사용하도록 구성해야 합니다.|

온-프레미스 서버에서 Azure Information Protection의 Azure Rights Management 서비스를 사용하려는 경우에 지원되는 제품은 다음과 같습니다.

-   Exchange Server

-   SharePoint Server

-   파일 분류 인프라를 지원하는 Windows Server 파일 서버

이 시나리오에 대한 추가 요구 사항에 대한 자세한 내용은 [Azure Rights Management 데이터 보호를 지원하는 온-프레미스 서버](requirements-servers.md)를 참조하세요.

> [!IMPORTANT]
> 다음 배포 시나리오는 AD RMS 보호를 Azure Information Protection("hold your own key" 또는 HYOK 구성)과 함께 사용하는 경우에만 지원됩니다.
> 
> -   [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)에 설명된 대로, 마이그레이션 중인 경우를 제외하고 같은 조직에서 AD RMS와 Azure RMS를 함께 실행하는 경우.
> 
> [AD RMS에서 Azure Information Protection으로](http://technet.microsoft.com/library/Dn858447.aspx), [Azure Information Protection에서 AD RMS로](http://msdn.microsoft.com/library/azure/dn629429.aspx)의 지원되는 마이그레이션 경로가 있습니다. Azure Information Protection을 배포한 후 이 클라우드 서비스를 더 이상 사용하지 않겠다고 결정한 경우 [Azure Information Protection 서비스 해제 및 비활성화](../deploy-use/decommission-deactivate.md)를 참조하세요.

## <a name="comments"></a>설명

[!INCLUDE[Commenting house rules](../includes/houserules.md)]





<!--HONumber=Dec16_HO2-->


