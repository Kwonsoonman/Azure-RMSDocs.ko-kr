---
title: AIP에 대한 Azure Active Directory 요구 사항
description: 사용자가 정상적으로 인증할 수 있도록, Azure Information Protection을 사용하는 데 필요한 Azure AD 요구 사항을 파악합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 53d9d9b25ab71c91275bf770a6038eccbaa2659c
ms.sourcegitcommit: f4a97427d61e4b539c91c49c952658aa2dc729ce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2018
---
# <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Azure Information Protection에 대한 Azure Active Directory 요구 사항

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection을 사용하려면 Azure AD 디렉터리가 있어야 합니다. 예를 들어 Azure Information Protection 레이블과 Rights Management 템플릿을 구성하고 관리할 수 있는 Azure Portal에 로그인하려면 이 디렉터리의 계정을 사용합니다.

Azure Information Protection 또는 Azure Rights Management가 포함된 구독이 있는 경우 필요에 따라 Azure AD 디렉터리가 자동으로 만들어집니다.  

Azure AD에 대한 자세한 내용은 [Azure Active Directory란?](/active-directory/active-directory-whatis)을 참조하세요.

Azure AD 디렉터리를 온-프레미스 AD 포리스트와 통합하려면 [Azure Active Directory와 온-프레미스 ID 통합](/active-directory/active-directory-aadconnect)을 참조하세요.

### <a name="scenarios-that-have-specific-requirements"></a>특정 요구 사항이 있는 시나리오 

Office 2010을 실행하는 컴퓨터: 

- 이러한 컴퓨터는 Azure Information Protection과 해당 데이터 보호 서비스인 Azure Rights Management에서 인증을 받기 위해 [Azure Information Protection 클라이언트](../rms-client/aip-client.md)(권장) 또는 [Windows용 Rights Management 공유 응용 프로그램](../rms-client/sharing-app-windows.md)이 필요합니다.

- AD FS를 사용하는 경우와 같이 사용자 계정이 페더레이션된 경우 해당 계정은 Windows 통합 인증을 사용해야 합니다. 이 시나리오에서 양식 기반 인증은 Azure Information Protection에 대한 사용자를 인증하지 못합니다.

CBA(인증서 기반 인증) 지원:

- iOS 및 Android용 Azure Information Protection 앱은 인증서 기반 인증을 지원합니다. 인증서 기반 인증을 구성하는 방법에 대한 지침은 [Get started with certificate-based authentication in Azure Active Directory](/azure/active-directory/active-directory-certificate-based-authentication-get-started)(Azure Active Directory에서 인증서 기반 인증 시작)를 참조하세요.

사용자의 UPN 값이 메일 주소와 일치하지 않는 경우:

- 권장 구성이 아닙니다. UPN 값을 변경할 수 없는 경우 사용자의 대체 로그인 ID를 구성하고 이 대체 로그인 정보로 Office에 로그인하는 방법을 알려주세요. 자세한 내용은 [대체 로그인 ID 구성](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) 및 [Office applications periodically prompt for credentials to SharePoint Online, OneDrive, and Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online)(Office 응용 프로그램에서 주기적으로 SharePoint Online, OneDrive 및 Lync Online의 자격 증명 요구)을 참조하세요.
    
    UPN 값에 있는 도메인이 테넌트에 대해 확인된 도메인인 경우는 사용자의 UPN 값을 Azure AD proxyAddresses 특성에 대한 다른 메일 주소로 추가합니다. 이렇게 하면 사용 권한을 부여할 때 사용자의 UPN 값이 지정되어 있을 경우 사용자에게 Azure Rights Management에 대한 사용 권한을 부여할 수 있습니다. 여기에 대한 자세한 내용과 사용자 계정에 권한을 부여하는 방법은 [Azure Information Protection을 위한 사용자 및 그룹 준비](../plan-design/prepare.md)를 참조하세요.

AD FS 또는 이와 동등한 인증 공급자를 사용하여 온-프레미스 인증을 수행하는 모바일 장치나 Mac 컴퓨터:

- **Windows Server 2012 R2** 이상의 서버 버전이나 OAuth 2.0 프로토콜을 지원하는 다른 인증 공급자에서 AD FS를 사용해야 합니다.

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>MFA(Multi-Factor Authentication) 및 Azure Information Protection
Azure Information Protection으로 MFA(Multi-Factor Authentication)를 사용하려면 다음 중 하나 이상이 필요합니다.

-   Office 2013(최소 버전)

    -   Office 2013이 있는 경우 ADAL(Active Directory 인증 라이브러리)을 지원하려면 추가 업데이트를 설치해야 합니다. 예를 들어 [Office 2013용 2015년 6월 9일 업데이트(KB3054853)](https://support.microsoft.com/kb/3054853)를 설치해야 합니다. 이 업데이트 및 최신 인증이 Office 2013에 ADAL(Active Directory 인증 라이브러리) 기반 로그인을 제공하는 방식에 대한 자세한 내용은 Office 블로그에서 [Office 2013 modern authentication public preview announced](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)(발표된 Office 2013 최신 인증 공개 미리 보기)를 참조하세요.

- Azure Information Protection 클라이언트:

    - Windows용 및 iOS/Android용 [Azure Information Protection 클라이언트](../rms-client/aip-client.md)에는 항상 지원되는 MFA가 있으며 최소 버전은 지정할 필요가 없습니다. 

-   Windows용 권한 관리 공유 응용 프로그램:

    - 제어판 > 프로그램 및 기능을 사용하여 확인할 수 있는 최소 버전 1.0.1908.0을 설치해야 합니다. Rights Management 공유 응용 프로그램은 이제 Azure Information Protection 클라이언트로 대체됩니다. 공유 응용 프로그램에 대한 자세한 내용은 [Windows용 Rights Management 공유 응용 프로그램](../rms-client/sharing-app-windows.md)을 참조하세요.

-   모바일 장치 및 Mac 컴퓨터에 대한 Rights Management 공유 앱:

    -   설치된 최신 버전이 있는지 확인하세요. MFA 지원은 RMS 공유 앱의 2015년 9월 릴리스에 들어있습니다.

그런 다음 MFA 솔루션을 구성합니다.

-   Microsoft에서 관리하는 테넌트의 경우입니다.(Azure Active Directory 또는 Office 365 보유)

    - Azure MFA를 구성하여 사용자에 MFA를 적용합니다. 지침은 Multi-Factor Authentication 설명서에서 [클라우드에서 Azure Multi-Factor Authentication 시작](/multi-factor-authentication/multi-factor-authentication-get-started-cloud)을 참조하세요.

        Azure MFA에 대한 자세한 내용은 [Azure Multi-Factor Authentication 정의](/multi-factor-authentication/multi-factor-authentication)를 참조하세요.

- 페더레이션된 테넌트의 경우입니다.(사용자가 페더레이션 서버 온-프레미스 동작)

    - Azure Active Directory 또는 Office 365에 페더레이션 서버를 구성합니다. 예를 들어 AD FS를 사용하는 경우 TechNet에서 [AD FS에 대한 추가 인증 방법 구성](https://technet.microsoft.com/library/dn758113.aspx)을 참조하세요.

        이 시나리오에 대한 자세한 내용은 Office 블로그에서 [Office 365로 작동 - 이제 간소화된 ID 프로그램](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/)을 참조하세요.

Rights Management 커넥터와 Azure Information Protection 스캐너는 MFA를 지원하지 않습니다. 커넥터 또는 스캐너를 배포하는 경우 다음 계정에 MFA가 필요하지 않아야 합니다.

- 커넥터를 설치하고 구성하는 계정

- 커넥터가 만드는 Azure AD의 서비스 주체 계정 **Aadrm_S-1-7-0**
 
- 스캐너를 실행하는 서비스 계정

## <a name="next-steps"></a>다음 단계
기타 요구 사항을 확인하려면 [Azure Information Protection에 대한 요구 사항](requirements-azure-rms.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
