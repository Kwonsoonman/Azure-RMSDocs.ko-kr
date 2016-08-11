---
title: "Azure Information Protection에 대한 요구 사항 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: aa4353e5-c5b0-47f6-a6f9-87d13e8f075f
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fe19726959bc16384120b610183c392031519813
ms.openlocfilehash: ff322e4ff0914ca29c7fe937a41936cb15d9a913


---

# Azure Information Protection에 대한 요구 사항

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

Azure Information Protection의 미리 보기 릴리스를 평가하려면 다음 필수 구성 요소가 있어야 합니다. 

|요구 사항|추가 정보|
|---------------|--------------------|
|Azure RMS를 포함하는 클라우드 구독|조직에 권한 관리를 지원하는 클라우드 구독이 있어야 합니다.<br /><br />무료 평가판에 대한 자세한 내용과 무료 평가판 링크는 [Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하세요.|
|Azure AD 디렉터리|Azure RMS 및 Azure Information Protection에 대해 사용자 인증을 지원하려면 조직에 Azure AD 디렉터리가 있어야 합니다. 또한 온-프레미스 디렉터리(AD DS)의 사용자 계정을 사용하려는 경우 디렉터리 통합도 구성해야 합니다.<br /><br />MFA(Multi-Factor Authentication)는 필수 클라이언트 소프트웨어 및 올바르게 구성된 MFA 지원 인프라가 있는 경우 Azure RMS에서 지원됩니다.<br /><br />자세한 내용은 [Azure AD 디렉터리](../get-started/requirements-azure-ad.md)를 참조하세요. 여기서 Azure RMS에 대한 정보는 Azure Information Protection에도 적용됩니다.|
|클라이언트 장치|이 미리 보기에 대해서는 다음 클라이언트 장치가 지원됩니다.<br /><br />- Windows 10(x86, x64)<br /><br />- Windows 8.1(x86, x64)<br /><br />- Windows 8(x86, x64)<br /><br />- Windows 7 서비스 팩 1(x86, x64)<br /><br />데이터를 보호할 경우 Azure 권한 관리를 지원하는 장치와 같은 장치(Windows, Mac, iOS, Android)에서 데이터를 이용할 수 있습니다. 이러한 장치 및 지원되는 버전에 대한 자세한 내용은 [Azure RMS 요구 사항: Azure RMS를 지원하는 클라이언트 장치](../get-started/requirements-client-devices.md)를 참조하세요.|
|응용 프로그램|미리 보기 릴리스의 경우 및 GA(일반 공급) 시, Azure Information Protection에서는 다음 Office 제품군의 Office 응용 프로그램인 **Word**, **Excel**, **PowerPoint** 및 **Outlook**에서 만들어진 파일과 메일의 레이블 지정 및 보호를 지원합니다.<br /><br />- Office Professional Plus 2016<br /><br />- Office Professional Plus 2013 서비스 팩 1<br /><br />- Office Professional Plus 2010<br /><br />일반 공급 후, Azure Information Protection에서 PDF, 오디오, 비디오 및 이미지 파일과 같은 추가 파일 형식을 지원하게 되는 때에 대해서는 [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services)(Enterprise Mobility 및 보안 블로그)의 공지를 확인하세요.|
|인터넷 및 종속된 클라우스 서비스 연결을 지원하는 인프라|특정 연결을 허용하기 위해 구성해야 하는 방화벽 또는 유사한 중개 네트워크 장치가 있는 경우 Office 문서 [Office 365 URL 및 IP 주소 범위](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)의 [Office 365 포털 및 공유](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) 섹션에 있는 **Azure RMS(권한 관리)** 정보를 참조하세요.<br /><br />또한,<br /><br />- TCP 443에서 **rmsibizaapiprod.cloudapp.net**에 대한 HTTPS 트래픽을 허용합니다.<br /><br />- TLS 클라이언트-서비스 연결을 종료하지 마세요(예를 들어 패킷 수준 조사를 수행하려는 경우). <br /><br />- 인증이 필요한 웹 프록시를 사용하는 경우 사용자의 Active Directory 로그온 자격 증명으로 통합된 Windows 인증을 사용하도록 구성해야 합니다.|

## 다음 단계

이러한 요구 사항을 충족하면 [Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)의 자가 주도형 데모를 통해 Azure Information Protection을 직접 구성하고 경험해 보세요.




<!--HONumber=Jul16_HO5-->


