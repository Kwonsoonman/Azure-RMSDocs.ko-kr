---
title: "AIP에 대한 Azure Active Directory 요구 사항"
description: "사용자가 정상적으로 인증할 수 있도록, Azure Information Protection을 사용하는 데 필요한 Azure AD 요구 사항을 파악합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 729d66e8d55d045b74ac5c794cf83ddcc2848d35
ms.sourcegitcommit: 1671466a42e7e00e1cc2702b1f609fb112aac7db
translationtype: HT
---
# <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Azure Information Protection에 대한 Azure Active Directory 요구 사항

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection을 사용하려면 Azure AD 디렉터리가 있어야 합니다. Azure 클래식 포털에 로그인하려면 이 디렉터리의 조직 계정을 사용합니다. Azure 클래식 포털에서는 Rights Management 템플릿을 구성 및 관리하는 등의 작업을 할 수 있습니다.

조직에 아직 Azure 구독이 없는 경우 무료 평가판을 신청하여 사용해 볼 수 있습니다. 이렇게 하려면 [Azure 시작하기](https://account.windowsazure.com/organization) 페이지로 이동하여 지침을 따릅니다.

자세한 내용은 Azure Active Directory 문서에서 다음 리소스를 참조하세요.

-   [Azure AD 디렉터리란?](/active-directory/active-directory-whatis)

-   [Azure 구독과 Azure Active Directory의 연관 관계](/active-directory/active-directory-how-subscriptions-associated-directory)

Azure AD 디렉터리를 온-프레미스 AD 포리스트와 통합하려면 [Azure Active Directory와 온-프레미스 ID 통합](/active-directory/active-directory-aadconnect)을 참조하세요.

### <a name="scenarios-that-have-specific-requirements"></a>특정 요구 사항이 있는 시나리오 

Office 2010을 실행하는 컴퓨터: 

- 이러한 컴퓨터는 Azure Information Protection과 해당 데이터 보호 서비스인 Azure Rights Management에서 인증을 받기 위해 [Azure Information Protection 클라이언트](../rms-client/aip-client.md)(권장) 또는 [Windows용 Rights Management 공유 응용 프로그램](../rms-client/sharing-app-windows.md)이 필요합니다.

- AD FS를 사용하는 경우와 같이 사용자 계정이 페더레이션된 경우 해당 계정은 Windows 통합 인증을 사용해야 합니다. 이 시나리오에서 양식 기반 인증은 Azure Information Protection에 사용자를 인증하지 못합니다.

CBA(인증서 기반 인증) 지원:

- Android용 Azure Information Protection 앱에서는 최소 버전인 Android 5.0 이상을 사용하는 경우 인증서 기반 인증을 지원합니다. 인증서 기반 인증을 구성하는 방법에 대한 지침은 [Get started with certificate-based authentication in Azure Active Directory](/active-directory/active-directory-certificate-based-authentication-get-started)(Azure Active Directory에서 인증서 기반 인증 시작)를 참조하세요.

AD FS 또는 이와 동등한 인증 공급자를 사용하여 온-프레미스 인증을 수행하는 모바일 장치나 Mac 컴퓨터:

- **Windows Server 2012 R2** 이상의 서버 버전이나 OAuth 2.0 프로토콜을 지원하는 다른 인증 공급자에서 AD FS를 사용해야 합니다.

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>MFA(Multi-Factor Authentication) 및 Azure Information Protection
Azure Information Protection으로 MFA(Multi-Factor Authentication)를 사용하려면 다음 중 하나 이상이 필요합니다.

-   Office 2013(최소 버전)

    -   Office 2013이 있는 경우 ADAL(Active Directory 인증 라이브러리)을 지원하려면 추가 업데이트를 설치해야 합니다. 예를 들어 [Office 2013용 2015년 6월 9일 업데이트(KB3054853)](https://support.microsoft.com/kb/3054853)를 설치해야 합니다. 이 업데이트 및 최신 인증이 Office 2013에 ADAL(Active Directory 인증 라이브러리) 기반 로그인을 제공하는 방식에 대한 자세한 내용은 Office 블로그에서 [발표된 Office 2013 최신 인증 공개 미리 보기](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)를 참조하세요.

- Azure Information Protection 클라이언트:

    - Windows용 및 iOS/Android용 [Azure Information Protection 클라이언트](../rms-client/aip-client.md)에는 항상 지원되는 MFA가 있으며 최소 버전은 지정할 필요가 없습니다. 

-   Windows용 권한 관리 공유 응용 프로그램:

    -   제어판, 프로그램 및 기능을 사용하여 확인할 수 있는 1.0.1908.0의 최소 버전을 설치해야 합니다. Rights Management 공유 응용 프로그램은 이제 Azure Information Protection 클라이언트로 대체됩니다. 공유 응용 프로그램에 대한 자세한 내용은 [Windows용 Rights Management 공유 응용 프로그램](../rms-client/sharing-app-windows.md)을 참조하세요.

-   모바일 장치 및 Mac 컴퓨터에 대한 Rights Management 공유 앱:

    -   설치된 최신 버전이 있는지 확인하세요. MFA 지원은 RMS 공유 앱의 2015년 9월 릴리스에 들어있습니다.

그런 다음 MFA 솔루션을 구성합니다.

-   Microsoft에서 관리하는 테넌트의 경우입니다.(Azure Active Directory 또는 Office 365 보유)

    -   Azure MFA를 구성하여 사용자에 MFA를 적용합니다. 지침은 Multi-Factor Authentication 설명서에서 [클라우드에서 Azure Multi-Factor Authentication 시작](/multi-factor-authentication/multi-factor-authentication-get-started-cloud)을 참조하세요.

        Azure MFA에 대한 자세한 내용은 [Azure Multi-Factor Authentication 정의](/multi-factor-authentication/multi-factor-authentication)를 참조하세요.

-   페더레이션된 테넌트의 경우입니다.(사용자가 페더레이션 서버 온-프레미스 동작)

    -   Azure Active Directory 또는 Office 365에 페더레이션 서버를 구성합니다. 예를 들어 AD FS를 사용하는 경우 TechNet에서 [AD FS에 대한 추가 인증 방법 구성](https://technet.microsoft.com/library/dn758113.aspx)을 참조하세요.

        이 시나리오에 대한 자세한 내용은 Office 블로그에서 [Office 365로 작동 - 이제 간소화된 ID 프로그램](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/)을 참조하세요.

## <a name="next-steps"></a>다음 단계
기타 요구 사항을 확인하려면 [Azure Information Protection에 대한 요구 사항](requirements-azure-rms.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
