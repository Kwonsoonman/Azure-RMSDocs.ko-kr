---
title: "Azure Information Protection에 대한 요구 사항 - 전체 문서"
description: "Azure Information Protection을 조직에 배포하기 위한 필수 구성 요소를 식별합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 10cf9371-a61b-495f-9d42-898448806994
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9fc5560381cc8ff3e3b8b1780c97ab88f3dda44a
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2017
---
# <a name="requirements-for-azure-information-protection"></a>Azure Information Protection에 대한 요구 사항

>*적용 대상: Azure Information Protection, Office 365*


Azure Information Protection을 조직에 배포하기 전에 다음 필수 구성 요소가 준비되어 있는지 확인하세요. 

|요구 사항|추가 정보|
|---------------|--------------------|
|Azure Information Protection 구독|Azure Information Protection 사이트에서 [구독 정보](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) 및 [기능 목록](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features)을 검토하여 조직의 구독에 사용하려는 Azure Information Protection 기능이 포함되어 있는지 확인하세요.|
|Azure Active Directory|Azure Information Protection에 대해 사용자 인증을 지원하려면 조직에 Azure AD(Azure Active Directory)가 있어야 합니다. 또한 온-프레미스 디렉터리(AD DS)의 사용자 계정을 사용하려는 경우 디렉터리 통합도 구성해야 합니다.<br /><br />계정이 페더레이션된 경우(예를 들어 AD FS를 사용하는 경우) Windows 통합 인증을 사용해야 합니다. Azure Information Protection에는 양식 기반 인증이 지원되지 않습니다.<br /><br />MFA(Multi-Factor Authentication)는 필수 클라이언트 소프트웨어 및 올바르게 구성된 MFA 지원 인프라가 있는 경우 Azure Information Protection에서 지원됩니다.<br /><br />자세한 내용은 [Azure Information Protection에 대한 Azure Active Directory 요구 사항](requirements-azure-ad.md)을 참조하세요.|
|클라이언트 장치|사용자에게 Azure Information Protection을 지원하는 운영 체제를 실행하는 클라이언트 장치(컴퓨터 또는 모바일 장치)가 있어야 합니다.<br /><br />다음은 사용자가 Office 문서 및 메일을 분류하여 레이블링할 수 있도록 Azure Information Protection 클라이언트를 지원하는 장치입니다.<br /><br />- Windows 10(x86, x64)<br /><br />- Windows 8.1(x86, x64)<br /><br />- Windows 8(x86, x64)<br /><br />- Windows 7 서비스 팩 1(x86, x64)<br /><br />이 클라이언트에서 Azure Rights Management 서비스를 통해 데이터를 보호하는 경우 Azure Rights Management 서비스를 지원하는 동일한 장치(Windows, Mac, iOS, Android)에서 이 클라이언트를 사용할 수 있습니다. <br /><br />Azure Rights Management 서비스를 지원하는 장치에 대한 자세한 내용은 [Azure Rights Management 데이터 보호를 지원하는 클라이언트 장치](../get-started/requirements-client-devices.md)를 참조하세요.|
|응용 프로그램|Azure Information Protection 클라이언트에서는 다음 Office 제품군의 Office 응용 프로그램인 **Word**, **Excel**, **PowerPoint** 및 **Outlook**에서 만들어진 파일과 메일의 레이블 지정 및 보호를 지원합니다.<br /><br />- Office Professional Plus 2016<br /><br />- Office Professional Plus 2013 서비스 팩 1<br /><br />- Office Professional Plus 2010<br /><br />Azure Rights Management 서비스를 지원하는 응용 프로그램에 대한 자세한 내용은 [Azure Rights Management 데이터 보호를 지원하는 응용 프로그램](requirements-applications.md)을 참조하세요.|
|인터넷 및 종속된 클라우스 서비스 연결을 지원하는 인프라|특정 연결을 허용하기 위해 구성해야 하는 방화벽 또는 유사한 중개 네트워크 장치가 있는 경우 Office 문서 [Office 365 URL 및 IP 주소 범위](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)의 [Office 365 포털 및 공유](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) 섹션에 있는 **Azure RMS(Rights Management)** 정보를 참조하세요.<br /><br />이 Office 문서의 지침에 따라 RSS 피드를 구독하여 이 정보에 대한 최신 변경 내용을 확인하세요.<br /><br />Office 문서의 정보 외에 Azure Information Protection과 관련하여 다음 사항에 유의하세요.<br /><br />- TCP 443에서 **api.informationprotection.azure.com**으로의 HTTPS 트래픽을 허용합니다.<br /><br />- TLS 클라이언트-서비스 연결을 종료하지 마세요(예를 들어 패킷 수준 조사를 수행하려는 경우). 연결을 종료하면 Azure RMS와의 통신 보안 유지를 위해 Microsoft에서 관리하는 CA와 함께 RMS 클라이언트가 사용하는 인증서 고정이 끊어집니다.<br /><br />- 인증이 필요한 웹 프록시를 사용하는 경우 사용자의 Active Directory 로그온 자격 증명으로 통합된 Windows 인증을 사용하도록 구성해야 합니다.|

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

## <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Azure Information Protection에 대한 Azure Active Directory 요구 사항

Azure Information Protection을 사용하려면 Azure AD 디렉터리가 있어야 합니다. Azure 클래식 포털에 로그인하려면 이 디렉터리의 조직 계정을 사용합니다. Azure 클래식 포털에서는 Rights Management 템플릿을 구성 및 관리하는 등의 작업을 할 수 있습니다.

조직에서 아직 Azure를 구독하지 않은 경우 무료 평가판을 신청하여 사용해 볼 수 있습니다. [Azure 시작](https://account.windowsazure.com/organization) 페이지로 이동하여 지침을 따르세요.

자세한 내용은 Azure Active Directory 문서에서 다음 리소스를 참조하세요.

-   [Azure AD 디렉터리란?](/active-directory/active-directory-whatis)

-   [Azure 구독과 Azure Active Directory의 연관 관계](/active-directory/active-directory-how-subscriptions-associated-directory)

Azure AD 디렉터리를 온-프레미스 AD 포리스트와 통합하려면 [Azure Active Directory와 온-프레미스 ID 통합](/active-directory/active-directory-aadconnect)을 참조하세요.

> [!NOTE]
> AD FS 또는 이와 동등한 인증 공급자를 사용하여 온-프레미스를 인증하는 모바일 장치나 Mac 컴퓨터를 사용하는 경우
> 
> -   **Windows Server 2012 R2** 이상의 서버 버전이나 OAuth 2.0 프로토콜을 지원하는 다른 인증 공급자에서 AD FS를 사용해야 합니다.

### <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>MFA(Multi-Factor Authentication) 및 Azure Information Protection
Azure Information Protection으로 MFA(Multi-Factor Authentication)를 사용하려면 다음 중 하나 이상이 필요합니다.

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

        이 시나리오에 대한 자세한 내용은 Office 블로그에서 [The Works with Office 365 - Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/)(Office 365로 작동 - 이제 간소화된 ID 프로그램)를 참조하세요.

## <a name="client-devices-that-support-azure-rights-management-data-protection"></a>Azure Rights Management 데이터 보호를 지원하는 클라이언트 장치

Azure Information Protection에 대한 데이터 보호를 제공하는 Azure Rights Management 서비스를 지원하는 장치를 식별하려면 다음 섹션을 참조하세요.

### <a name="computers"></a>컴퓨터
Azure Rights Management 서비스를 지원하는 컴퓨터 운영 체제는 다음과 같습니다.

-   **Windows 7**(x86, x64)

-   **Windows 8**(x86, x64)

-   **Windows 8.1**(x86, x64)

-   **Windows 10**(x86, x64)

-   **Mac OS X**: Mac OS X 10.8(Mountain Lion) 버전 이상

### <a name="mobile-devices"></a>모바일 장치
Azure Rights Management 서비스를 지원하는 모바일 장치 운영 체제는 다음과 같습니다.

-   **Windows Phone**: Windows Phone 8.1

-   **Android 휴대폰 및 태블릿**: 최소 Android 4.0.3 버전 이상

-   **iPhone 및 iPad**: 최소 iOS 7.0 버전 이상

-   **Windows 태블릿**: Windows 10 Mobile 및 Windows 8.1 RT

## <a name="applications-that-support-azure-rights-management-data-protection"></a>Azure Rights Management 데이터 보호를 지원하는 응용 프로그램

Azure Information Protection에 대한 데이터 보호를 제공하는 Azure RMS(Azure Rights Management 서비스)를 기본적으로 지원하는 응용 프로그램을 식별하려면 다음 표를 참조하세요. 

이러한 응용 프로그램의 경우 Rights Management API를 통해 사용 제한을 지원하여 Rights Management 서비스를 강력히 통합합니다. 이러한 응용 프로그램을 RMS 지원이라고도 합니다.

별도의 설명이 없으면 지원되는 기능은 Azure RMS와 AD RMS 둘 다에 적용됩니다. 또한 iOS, Android, OS X 및 Windows Phone 8.1에서 AD RMS를 지원하려면 [Active Directory Rights Management Services 모바일 장치 확장](https://technet.microsoft.com/library/dn673574.aspx)이 필요합니다.

테이블 열에 대한 정보:

-   **보호된 PDF**: 파일 이름 확장명이 .ppdf이고 RMS 공유 응용 프로그램을 사용하여 Office 파일 및 PDF 파일을 메일로 공유할 때 자동으로 생성되는 파일입니다. RMS 공유 응용 프로그램 및 iOS 및 Android 용 Azure Information Protection 앱에는 보호되는 PDF 파일에 대한 판독기가 포함되어 있습니다. 이전에 Azure RMS 또는 AD RMS를 사용하여 보호된 PDF 파일을 만든 경우 Foxit Reader 및 Nitro Pro를 사용하여 Windows, iOS 및 Android 장치에서 해당 파일을 계속 읽을 수 있습니다.

-   **메일:** 나열된 메일 클라이언트는 메일 메시지 자체를 보호할 수 있으므로 첨부된 파일도 자동으로 보호됩니다. 이 시나리오에서 클라이언트의 미리 보기 기능은 권한 있는 받는 사람에게 보호된 콘텐츠(메시지 및 첨부 파일)를 표시할 수 있습니다. 그러나 메일 메시지 자체가 보호되지 않고 첨부 파일만 보호되면, 클라이언트의 미리 보기 기능이 권한 있는 받는 사람에게 보호된 첨부 파일을 표시할 수 없습니다.

-   **기타 파일 형식**: 텍스트 및 이미지 파일에는 파일 이름 확장명이 .txt, .xml, .jpg, .jpeg와 같은 파일이 포함됩니다. 이러한 파일은 Rights Management의 기본 보호를 통해 읽기 전용으로 바뀌면 파일 이름 확장명이 변경됩니다. 기본 보호를 적용할 수 없는 파일은 Rights Management의 일반적인 보호를 받으며 파일 이름 확장명으로 .pfile이 지정됩니다. 자세한 내용은 [Rights Management 공유 응용 프로그램 관리자 가이드](../rms-client/sharing-app-admin-guide.md)를 참조하세요.


|**장치 운영 체제**|Word, Excel, PowerPoint|보호된 PDF|메일|다른 파일 형식|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Mobile 앱(Azure RMS에만 해당) [[1]](#footnote-1)<br /><br />Office Online [[2]](#footnote-2)|Gaaiho 문서<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS 공유 앱|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />OWA(Outlook Web App) [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4)|Windows용 RMS 공유 응용 프로그램: 텍스트, 이미지, pfile<br /><br />Siemens JT2Go: JT 파일(Windows 10에만 해당)|
|**iOS**|iPad 및 iPhone용 Office [[5]](#footnote-5)<br /><br />Office Online [[2]](#footnote-2)<br /><br />TITUS Docs|Azure Information Protection 앱 [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />TITUS Docs|Azure Information Protection 앱 [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />iPad 및 iPhone용 Outlook [[4]](#footnote-4)<br /><br />iOS용 OWA [[3]](#footnote-3)<br /><br />TITUS Mail|Azure Information Protection 앱 [[1]](#footnote-1): 텍스트, 이미지<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online [[2]](#footnote-2)<br /><br />Office Mobile(Azure RMS에만 해당) [[1]](#footnote-1)|Azure Information Protection 앱 [[1]](#footnote-1)<br /><br />GigaTrust App for Android<br /><br />Foxit Reader<br /><br />RMS 공유 앱 [[1]](#footnote-1)|9Folders [[4]](#footnote-4)<br /><br />Azure Information Protection 앱 [[1]](#footnote-1)<br /><br />GigaTrust App for Android [[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Android용 Outlook [[4]](#footnote-4)<br /><br />Android용 OWA [[3]](#footnote-3) 및 [[7]](#footnote-7)<br /><br />Samsung Email(S3 이상) [[7]](#footnote-7)<br /><br />TITUS Classification for Mobile|Azure Information Protection 앱 [[1]](#footnote-1): 텍스트, 이미지|
|**OS X**|Office 2011(AD RMS만 해당)<br /><br />Mac용 Office 2016<br /><br />Office Online [[2]](#footnote-2)|Foxit Reader<br /><br />RMS 공유 앱 [[1]](#footnote-1)|Outlook 2011(AD RMS만 해당)<br /><br />Mac용 Outlook 2016<br /><br />Outlook for Mac|RMS 공유 앱 [[1]](#footnote-1): 텍스트, 이미지, pfile|
|**Windows 10 Mobile**|Office Mobile 앱(Azure RMS에만 해당) [[1]](#footnote-1)|지원되지 않음|Citrix WorxMail [[6]](#footnote-6)<br /><br />Outlook 메일|지원되지 않음|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[2]](#footnote-2)|지원되지 않음|Outlook 2013 RT<br /><br />Windows용 메일 앱<br /><br />Windows Mail [[4]](#footnote-4)|Siemens JT2Go: JT 파일|
|**Windows Phone 8.1**|Office Mobile(AD RMS만 해당)|RMS 공유 앱 [[1]](#footnote-1)|Outlook Mobile [[4]](#footnote-4)|RMS 공유 앱 [[1]](#footnote-1): 텍스트, 이미지, pfile|
|**Blackberry 10**|지원되지 않음|지원되지 않음|Blackberry 메일 [[4]](#footnote-4)|지원되지 않음|


##### <a name="footnote-1"></a>각주 1
사용권 계약에 따라 보호하는 콘텐츠 보기를 지원합니다.

##### <a name="footnote-2"></a>각주 2 
SharePoint Online 및 비즈니스용 OneDrive에서 보호되지 않은 문서를 보호된 라이브러리로 업로드하는 경우 보호된 문서 보기를 지원합니다. 

##### <a name="footnote-3"></a>각주 3
받는 사람이 보호된 메일을 수신하고 Exchange를 메일 서버로 사용하지 않거나 보내는 사람이 다른 조직에 속하는 경우, 이 콘텐츠는 Outlook과 같은 서식 있는 메일 클라이언트에서만 열 수 있습니다. 이 콘텐츠는 Outlook Web Access에서 열 수 없습니다.

##### <a name="footnote-4"></a>각주 4
Exchange 관리자가 사용하도록 설정해야 하는 Exchange ActiveSync IRM을 사용합니다. 사용자는 보호된 메일 메시지를 보기, 회신 및 전체 회신할 수 있지만 사용자는 새 메일 메시지 자체를 보호할 수 없습니다.

받는 사람이 보호된 메일을 수신하고 Exchange를 메일 서버로 사용하지 않거나 보내는 사람이 다른 조직에 속하는 경우, 이 콘텐츠는 Outlook과 같은 서식 있는 메일 클라이언트에서만 열 수 있습니다. 이 콘텐츠는 Exchange Active Sync IRM을 사용하여 모바일 메일 클라이언트 또는 Outlook Web Access에서 열 수 없습니다.

##### <a name="footnote-5"></a>각주 5
보호된 문서 보기 및 편집을 지원합니다. 자세한 내용은 Office 블로그에서 [iPad 및 iPhone용 Office에 Azure 권한 관리 지원 제공](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) 게시물을 참조하세요.

##### <a name="footnote-6"></a>각주 6
자세한 내용은 Citrix [WorxMail에 대한 제품 설명서](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html)를 참조하세요.

##### <a name="footnote-7"></a>각주 7
자세한 내용은 Office 블로그에서 [이제 일부 선택된 장치에서 Android용 OWA를 사용할 수 있음](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) 게시물을 참조하세요.

## <a name="more-information-about-azure-rms-support-for-office"></a>Office에 대한 Azure RMS 지원과 관련된 자세한 내용

Azure RMS는 Word, Excel, PowerPoint 및 Outlook 앱에 긴밀하게 통합되어 있으며, 이러한 앱에서 이 기능은 종종 IRM(정보 권한 관리)이라고 불립니다. 다음 Office 클라이언트 버전은 Azure RMS를 사용하여 파일 및 메일 보호를 지원합니다.

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Office 2007을 제외하고 모든 버전의 Office에서 보호된 콘텐츠를 사용할 수 있습니다.

Office Professional Plus 2010 또는 Office Professional 2010을 사용하는 Azure RMS:

- Windows용 Rights Management 공유 응용 프로그램이 필요

- Windows 10에서는 지원되지 않음

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>iOS 및 Android용 Azure Information Protection 앱에 대한 자세한 내용

iOS 및 Android용 Azure Information Protection 앱은 이러한 장치에 대한 RMS 공유 앱을 대체합니다. 동일한 기능을 제공하고 SharePoint Online에서 권한으로 보호되는 메일 메시지와 권한으로 보호되는 PDF 파일을 지원합니다.

Microsoft Intune에서 iOS 및 Android 장치를 등록하는 경우 정책 관리 앱을 사용하여 이 앱을 배포 및 관리할 수 있습니다. 자세한 내용은 Intune 설명서에서 [Microsoft Intune 콘솔에서 모바일 응용 프로그램 관리 정책 구성 및 배포](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)를 참조하세요. 이 Intune 설명서에서 2단계에서는 정책 관리 앱 게시 지침을 사용합니다.

자세한 내용은 [iOS 및 Android용 Microsoft Azure Information Protection 앱에 대한 FAQ](../rms-client/mobile-app-faq.md)를 참조하세요.


### <a name="more-information-about-the-rights-management-sharing-application"></a>Rights Management 공유 응용 프로그램에 대한 자세한 내용

Windows용 Rights Management 공유 응용 프로그램에 대한 자세한 내용은 다음 리소스를 참조하세요.

-   [Rights Management 공유 응용 프로그램 관리자 가이드](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management 공유 응용 프로그램 사용자 가이드](../rms-client/sharing-app-user-guide.md)

모바일 플랫폼용 Rights Management 공유 응용 프로그램에 대한 자세한 내용은 다음 리소스를 참조하세요.

-   [Microsoft Rights Management 페이지](http://go.microsoft.com/fwlink/?LinkId=303970)의 링크를 사용하여 관련 앱 다운로드

-   [모바일 플랫폼용 Microsoft Rights Management 공유 응용 프로그램 FAQ](https://technet.microsoft.com/dn451248)

> [!NOTE]
> 이제 iOS 및 Android용 RMS 공유 앱은 Azure Information Protection 앱으로 대체됩니다.

### <a name="more-information-about-other-applications-that-support-azure-rms"></a>Azure RMS를 지원하는 다른 응용 프로그램에 대한 자세한 내용

표에 있는 응용 프로그램뿐 아니라 RMS API를 Azure RMS와 통합할 수 있도록 지원하는 모든 응용 프로그램이며, 다음이 포함됩니다.

- RMS SDK를 사용하여 사내에서 작성한 LOB(기간 업무) 응용 프로그램

- 소프트웨어 공급업체에서 RMS SDK를 사용하여 작성한 응용 프로그램

SDK에 대한 자세한 내용은 [Microsoft Rights Management SDK](../develop/developers-guide.md)를 참조하세요.

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Azure RMS에서 지원되지 않는 응용 프로그램

Azure RMS에서 현재 지원되지 않는 응용 프로그램은 다음과 같습니다.

-   Microsoft Office for Mac 2011

-   SharePoint Server 2013에 대한 Microsoft 비즈니스용 OneDrive

-   XPS 뷰어
 
또한 RMS 공유 응용 프로그램에는 다음과 같은 제한이 있습니다.

-   Windows 컴퓨터의 경우: 최소 Windows 7 서비스 팩 1 이상 버전이 필요합니다.

## <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Azure Rights Management 데이터 보호를 지원하는 온-프레미스 서버

Azure Rights Management 커넥터를 사용할 때 Azure Information Protection에서 지원되는 온-프레미스 서버 제품은 다음과 같습니다. 이 커넥터는 Azure Information Protection에서 Office 문서 및 메일을 보호하는 데 사용되는 온-프레미스 서버와 Azure Rights Management 서비스 간의 통신 인터페이스(릴레이) 역할을 합니다. 

이 커넥터를 사용하려면 Active Directory 포리스트와 Azure Active Directory 간의 디렉터리 동기화를 구성해야 합니다.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Windows Server를 실행하고 FCI(파일 분류 인프라)를 사용하는 파일 서버**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Windows Server 2008 R2를 실행하는 파일 서버에는 Rights Management 보호를 적용하는 기본 제공 파일 관리 작업 동작이 없으므로 이 시나리오에는 Rights Management 커넥터를 사용할 수 없습니다. 그러나 Azure RMS를 사용하여 파일을 보호할 수 있는 사용자 지정 파일 관리 작업(실행 파일 또는 스크립트를 실행)을 구성하는 경우 이러한 운영 체제에서 파일 분류 인프라 및 Azure RMS를 사용할 수 있습니다. 예를 들어 [RMS 보호 cmdlet](https://msdn.microsoft.com/library/azure/mt433195.aspx)을 사용하는 Windows PowerShell 스크립트입니다.
    > 
    > 또한 이러한 cmdlet이 모든 파일 형식을 보호할 수 있다는 혜택을 가진 이후 버전의 Windows Server를 실행하는 서버로 이러한 cmdlet를 사용할 수 있습니다. RMS 커넥터는 Office 파일만을 보호합니다. 방법 지침은 [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](../rms-client/configure-fci.md)를 참조하세요.

Rights Management 커넥터는 Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2에서 지원됩니다.

이러한 온-프레미스 서버에 대해 Rights Management 커넥터를 구성하는 방법에 대한 자세한 내용은 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
