---
title: "Azure 권한 관리 요구 사항 | Azure RMS"
description: "조직에 Microsoft Azure 권한 관리(Azure RMS)를 배포하려면 다음과 같은 필수 조건을 충족해야 합니다. 그런 다음 Azure 권한 관리 배포 로드맵을 사용하여 조직에 대한 권한 관리를 배포할 수 있습니다."
author: cabailey
manager: mbaldwin
ms.date: 07/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7b194493073bcd76fa7a7d06bb31a7811e8cc3e
ms.openlocfilehash: d56eb077ef76e1869c7d90141f1b35c1bdbfe9fa


---

# Azure 권한 관리 요구 사항

>*적용 대상: Azure 권한 관리, Office 365*


조직에 Microsoft Azure 권한 관리(Azure RMS)를 배포하려면 다음과 같은 필수 조건을 충족해야 합니다. 그런 다음 [Azure 권리 관리 배포 로드맵](../plan-design/deployment-roadmap.md)을 사용하여 조직에 대한 권한 관리를 배포할 수 있습니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|RMS 클라우드 구독|조직에 RMS를 지원하는 클라우드 구독이 있어야 합니다.<br /><br />라이선스 정보는 [Azure RMS를 지원하는 클라우드 구독](requirements-subscriptions.md)을 참조하세요.|
|Azure AD 디렉터리|RMS에 대해 사용자 인증을 지원하려면 조직에 Azure AD 디렉터리가 있어야 합니다. 또한 온-프레미스 디렉터리(AD DS)의 사용자 계정을 사용하려는 경우 디렉터리 통합도 구성해야 합니다.<br /><br />MFA(Multi-Factor Authentication)는 필수 클라이언트 소프트웨어 및 올바르게 구성된 MFA 지원 인프라가 있는 경우 Azure RMS에서 지원됩니다.<br /><br />자세한 내용은 [Azure AD 디렉터리](requirements-azure-ad.md)를 참조하세요.|
|클라이언트 장치|사용자에게 RMS를 지원하는 운영 체제를 실행하는 클라이언트 장치(컴퓨터 또는 모바일 장치)가 있어야 합니다.<br /><br />자세한 내용은 [Azure RMS를 지원하는 클라이언트 장치](requirements-client-devices.md)를 참조하세요.|
|응용 프로그램|사용자는 RMS를 지원하는 응용 프로그램을 실행해야 합니다.<br /><br />자세한 내용은 [Azure RMS를 지원하는 응용 프로그램](requirements-applications.md)을 참조하세요.|
|인터넷 및 종속된 클라우스 서비스 연결을 지원하는 인프라|특정 연결을 허용하기 위해 구성해야 하는 방화벽 또는 유사한 중개 네트워크 장치가 있는 경우 Office 문서 [Office 365 URL 및 IP 주소 범위](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)의 [Office 365 포털 및 공유](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) 섹션에 있는 **Azure RMS(권한 관리)** 정보를 참조하세요.<br /><br />이 Office 문서의 지침에 따라 RSS 피드를 구독하여 이 정보에 대한 최신 변경 내용을 확인하세요.<br /><br />Office 문서의 정보 외에 Azure RMS와 관련하여 다음 사항에 유의하세요.<br /><br />- TLS 클라이언트-서비스 연결을 종료하지 마세요(예를 들어 패킷 수준 조사를 수행하려는 경우). 연결을 종료하면 Azure RMS와의 통신 보안 유지를 위해 Microsoft에서 관리하는 CA와 함께 RMS 클라이언트가 사용하는 인증서 고정이 끊어집니다.<br /><br />- 인증이 필요한 웹 프록시를 사용하는 경우 사용자의 Active Directory 로그온 자격 증명으로 통합된 Windows 인증을 사용하도록 구성해야 합니다.|

온-프레미스 서버에 Azure RMS를 사용하려는 경우 다음 제품이 지원됩니다.

-   Exchange Server

-   SharePoint Server

-   파일 분류 인프라를 지원하는 Windows Server 파일 서버

이 시나리오에 대한 추가 Azure RMS 요구 사항에 대한 자세한 내용은 [Azure RMS를 지원하는 온-프레미스 서버](requirements-servers.md)를 참조하세요.

> [!IMPORTANT]
> 다음 배포 시나리오는 지원되지 않습니다.
> 
> -   [AD RMS에서 Azure 권한 관리로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)에 설명된 대로, 마이그레이션 중인 경우를 제외하고 같은 조직에서 AD RMS와 Azure RMS를 함께 실행하는 경우.
> 
> [AD RMS에서 Azure RMS로](http://technet.microsoft.com/library/Dn858447.aspx), 그리고 [Azure RMS에서 AD RMS로](http://msdn.microsoft.com/library/azure/dn629429.aspx) 지원되는 마이그레이션 경로가 있습니다. Azure RMS를 배포한 후 이 클라우드 서비스를 더 이상 사용하지 않겠다고 결정한 경우 [Azure 권한 관리 서비스 해제 및 비활성화](../deploy-use/decommission-deactivate.md)를 참조하세요.






<!--HONumber=Aug16_HO4-->


