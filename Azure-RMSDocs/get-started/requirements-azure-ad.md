---
title: "Azure RMS 요구 사항&#58; Azure AD 디렉터리 | Azure RMS"
description: "Azure 권한 관리(Azure RMS)를 사용하려면 Azure AD 디렉터리가 있어야 합니다. Azure 클래식 포털에 로그인하려면 이 디렉터리의 조직 계정을 사용합니다. Azure 클래식 포털에서는 Rights Management 템플릿을 구성 및 관리하는 등의 작업을 할 수 있습니다."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 8083c2f7e4cfdbf65748007ae21a48a49a56599f


---

# Azure RMS 요구 사항: Azure AD 디렉터리

>*적용 대상: Azure 권한 관리, Office 365*


Azure 권한 관리(Azure RMS)를 사용하려면 Azure AD 디렉터리가 있어야 합니다. Azure 클래식 포털에 로그인하려면 이 디렉터리의 조직 계정을 사용합니다. Azure 클래식 포털에서는 Rights Management 템플릿을 구성 및 관리하는 등의 작업을 할 수 있습니다.

조직에서 아직 Azure를 구독하지 않은 경우 무료 평가판을 신청하여 사용해 볼 수 있습니다. [Azure 시작](https://account.windowsazure.com/organization) 페이지로 이동하여 지침을 따르세요.

자세한 내용은 Azure Active Directory 문서에서 다음 리소스를 참조하세요.

-   [Azure AD 디렉터리란?](/active-directory/active-directory-whatis)

-   [Azure 구독과 Azure Active Directory의 연관 관계](/active-directory/active-directory-how-subscriptions-associated-directory)

Azure AD 디렉터리를 온-프레미스 AD 포리스트와 통합하려면 [Azure Active Directory와 온-프레미스 ID 통합](/active-directory/active-directory-aadconnect)을 참조하세요.

> [!NOTE]
> AD FS 또는 이와 동등한 인증 공급자를 사용하여 온-프레미스를 인증하는 모바일 장치나 Mac 컴퓨터를 사용하는 경우
> 
> -   **Windows Server 2012 R2** 이상의 서버 버전이나 OAuth 2.0 프로토콜을 지원하는 다른 인증 공급자에서 AD FS를 사용해야 합니다.

## Multi-Factor Authentication(MFA) 및 Azure RMS
Azure RMS로 Multi-Factor Authentication(MFA)를 사용하려면 다음 중 하나 이상이 필요합니다.

-   Office 2013(최소 버전)

    -   Office 2013을 사용하는 경우 [Office 2013 2015년 6월 9일 업데이트(KB3054853)](https://support.microsoft.com/kb/3054853)도 설치해야 합니다. 이 업데이트 및 최신 인증이 Office 2013에 ADAL(Active Directory 인증 라이브러리) 기반 로그인을 제공하는 방식에 대한 자세한 내용은 Office 블로그에서 [발표된 Office 2013 최신 인증 공개 미리 보기](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)를 참조하세요.

-   Windows용 권한 관리 공유 응용 프로그램:

    -   제어판, 프로그램 및 기능을 사용하여 확인할 수 있는 1.0.1908.0의 최소 버전을 설치해야 합니다. 공유 응용 프로그램에 대한 자세한 내용은 [Windows용 권한 관리 공유 응용 프로그램](../rms-client/sharing-app-windows.md)을 참조하세요.

-   모바일 장치 및 Mac 컴퓨터에 대한 Rights Management 공유 앱:

    -   설치된 최신 버전이 있는지 확인하세요. MFA 지원은 RMS 공유 앱의 2015년 9월 릴리스에 들어있습니다.

그런 다음 MFA 솔루션을 구성합니다.

-   Microsoft에서 관리하는 테넌트의 경우입니다.(Azure Active Directory 또는 Office 365 보유)

    -   Azure MFA를 구성하여 사용자에 MFA를 적용합니다. 지침은 Multi-Factor Authentication 설명서에서 [클라우드에서 Azure Multi-Factor Authentication 시작](/multi-factor-authentication/multi-factor-authentication-get-started-cloud)을 참조하세요.

        Azure MFA에 대한 자세한 내용은 [Azure Multi-Factor Authentication 정의](/multi-factor-authentication/multi-factor-authentication)를 참조하세요.

-   페더레이션된 테넌트의 경우입니다.(사용자가 페더레이션 서버 온-프레미스 동작)

    -   Azure Active Directory 또는 Office 365에 페더레이션 서버를 구성합니다. 예를 들어 AD FS를 사용하는 경우 TechNet에서 [AD FS에 대한 추가 인증 방법 구성](https://technet.microsoft.com/library/dn758113.aspx)을 참조하세요.

        이 시나리오에 대한 자세한 내용은 Office 블로그에서 [Office 365로 작동 - 이제 간소화된 ID 프로그램](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/)을 참조하세요.

## 다음 단계
기타 요구 사항을 확인하려면 [Azure 권한 관리 요구 사항](requirements-azure-rms.md)을 참조하세요.




<!--HONumber=Aug16_HO4-->


