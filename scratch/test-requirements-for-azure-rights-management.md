---
title: 테스트 Azure 권한 관리 요구 사항
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: TEST
author: Cabailey
---
# 이전: Azure 권한 관리 요구 사항
조직에 Microsoft Azure 권한 관리(Azure RMS)를 배포하려면 다음과 같은 필수 조건을 충족해야 합니다. 그런 다음 [Azure 권리 관리 배포 로드맵](deployment-roadmap.md)을 사용하여 조직에 대한 권한 관리를 배포할 수 있습니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|RMS 클라우드 구독|조직에 RMS를 지원하는 클라우드 구독이 있어야 합니다.<br /><br />라이선스 정보는 이 항목에서 [Azure RMS를 지원하는 클라우드 구독](requirements-azure-rms.md#BKMK_SupportedSubscriptions) 섹션을 참조하세요.|
|Azure AD 디렉터리|RMS에 대해 사용자 인증을 지원하려면 조직에 Azure AD 디렉터리가 있어야 합니다. 또한 온-프레미스 디렉터리(AD DS)의 사용자 계정을 사용하려는 경우 디렉터리 통합도 구성해야 합니다.<br /><br />Multi-factor authentication(MFA)은 필요한 클라이언트 소프트웨어 및 올바르게 구성된 MFA 지원 인프라를 필요로 하는 경우 Azure RMS로 지원됩니다.<br /><br />자세한 내용은 이 항목에서 [Azure AD 디렉터리](requirements-azure-rms.md#BKMK_AzureADTenant) 섹션을 참조하세요.|
|클라이언트 장치|사용자에게 RMS를 지원하는 운영 체제를 실행하는 클라이언트 장치(컴퓨터 또는 모바일 장치)가 있어야 합니다.<br /><br />자세한 내용은 이 항목에서 [Azure RMS를 지원하는 클라이언트 장치](requirements-azure-rms.md#BKMK_SupportedDevices) 섹션을 참조하세요.|
|응용 프로그램|사용자는 RMS를 지원하는 응용 프로그램을 실행해야 합니다.<br /><br />자세한 내용은 이 항목에서 [Azure RMS를 지원하는 응용 프로그램](requirements-azure-rms.md#BKMK_SupportedApplications) 섹션을 참조하세요.|
|인터넷 및 종속된 클라우스 서비스 연결을 지원하는 인프라|특정 연결을 허용하기 위해 구성해야 하는 방화벽 또는 유사한 중개 네트워크 장치가 있는 경우 [Office 365 URL 및 IP 주소 범위](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)를 참조하세요.<br /><br />**Office 365 포털 및 ID** 섹션의 URL 및 IP 주소 목록은 Office 365 포털, Azure Active Directory 리소스 및 Azure 권한 관리에 적용됩니다. 이 문서의 지침에 따라 RSS 피드를 구독하여 이 정보에 대한 최신 변경 내용을 확인하세요.<br /><br />Office 문서의 정보 외에 Azure RMS와 관련하여 다음 사항에 유의하세요.<br /><br />TLS 클라이언트-서비스 연결을 종료하지 마세요(예를 들어 패킷 수준 조사를 수행하려는 경우). 연결을 종료하면 Azure RMS와의 통신 보안 유지를 위해 Microsoft에서 관리하는 CA와 함께 RMS 클라이언트가 사용하는 인증서 고정이 끊어집니다.<br /><br />사용자를 대신하여 인증하는 웹 프록시 구성을 사용하지 마세요.|

온-프레미스 서버에 Azure RMS를 사용하려는 경우 다음 제품이 지원됩니다.

-   Exchange Server

-   SharePoint Server

-   파일 분류 인프라를 지원하는 Windows Server 파일 서버

이 시나리오에 대한 추가 Azure RMS 요구 사항에 대한 자세한 내용은 이 항목에서 [Azure RMS를 지원하는 온-프레미스 서버](requirements-azure-rms.md#BKMK_SupportedServers) 섹션을 참조하세요.

> [!IMPORTANT]
> 다음 배포 시나리오는 지원되지 않습니다.
> 
> -   [AD RMS에서 Azure 권한 관리로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)에 설명된 대로, 마이그레이션 중인 경우를 제외하고 같은 조직에서 AD RMS와 Azure RMS를 함께 실행하는 경우.
> 
> [AD RMS에서 Azure RMS로](http://technet.microsoft.com/library/Dn858447.aspx), 그리고 [Azure RMS에서 AD RMS로](http://msdn.microsoft.com/library/azure/dn629429.aspx) 지원되는 마이그레이션 경로가 있습니다. Azure RMS를 배포한 후 이 클라우드 서비스를 더 이상 사용하지 않겠다고 결정한 경우 [Azure 권한 관리 서비스 해제 및 비활성화](decommission-deactivate.md)를 참조하세요.

다음 섹션에서 Azure RMS 요구 사항에 대한 자세한 내용을 확인하세요.

## <a name="BKMK_SupportedSubscriptions"></a>Azure RMS를 지원하는 클라우드 구독
Azure RMS를 사용하려면 조직에서 사용자를 위한 충분한 수의 라이선스와 파일 및 메일 메시지를 보호할 서비스를 포함하는 다음과 같은 구독 중 하나를 사용하고 있어야 합니다. 사용자(파일 또는 메일 메시지 소유자)에 대해 보호를 적용하는 서비스를 사용 중인 경우 이러한 사용자는 다음 라이선스 중 하나가 있어야 합니다. 이 보호된 데이터를 사용(예: 읽기 및 편집)만 하는 사용자의 경우 라이선스가 필요하지 않습니다.

-   Office 365

-   Azure Rights Management 프리미엄(이전의 Azure RMS 독립 실행형)

-   Enterprise Mobility Suite

-   개인용 RMS

다음 섹션에서 자세한 내용 및 등록 옵션을 확인하세요.

유료 구독에 대한 Azure RMS 기능의 라이선스를 비교하려면 [RMS(권한 관리 서비스) 제공 서비스 비교](http://technet.microsoft.com/dn858608)를 참조하세요.

Azure RMS 라이센스에 대한 추가 질문이 있나요? [Azure 권한 관리 구매](https://www.microsoft.com/en-us/server-cloud/products/azure-rights-management/Purchasing.aspx) 페이지에서 **Azure 권한 관리에 대한 라이선스 FAQ**를 다운로드합니다. 

### Office 365 구독
[30일 무료 평가판: Enterprise E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

이 구독은 Office Online 서비스를 사용하고, Azure RMS를 사용하는 정보 권한 관리 기능을 사용하려는 조직을 위해 디자인되었습니다. 그러나 일부 Office 365 구독에는 Azure RMS가 포함되어 있지 않습니다.

|라이선싱 옵션|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office  365  Enterprise  E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint 계획 1<br />SharePoint 계획 2|Exchange Online 계획 1<br />Exchange Online 계획 2|
|--------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|정보 권한 보호(IRM)|아니요|아니요|아니요|예|예|예|아니요|아니요|아니요|

### Azure 권한 관리 프리미엄 구독
[30일 무료 평가판](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

이 구독은 이전에 Azure RMS 독립 실행형으로 알려졌으며 Azure RMS를 사용하려고 하지만 Azure RMS를 포함하는 구독이 없는 조직을 위해 설계되었습니다. 예를 들어 Office 365 Business Essentials 또는 Office 365 Enterprise E1 구독이 있는 경우 해당 구독에는 Azure RMS가 포함되어 있지 않습니다(이전 섹션의 표 참조). Azure RMS를 사용하려면 Azure 권한 관리 프리미엄 구독을 구입하거나 Office 365 Enterprise E4와 같이 Azure RMS가 포함된 다른 구독을 구입합니다.

자세한 내용은 [Microsoft Azure 권한 관리](http://products.office.com/business/microsoft-azure-rights-management)를 참조하세요.

구독 시에는 사용자 25명이 Azure RMS를 사용해 볼 수 있는 평가 기간도 무료로 제공됩니다. 대체 구독을 구매하기 전에 구독이 만료되는 경우 다음 섹션인 "평가용 구독이 만료되는 경우" 섹션을 참조하세요

|라이선싱 옵션|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office  365  Enterprise  E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint 계획 1<br />SharePoint 계획 2|Exchange Online 계획 1<br />Exchange Online 계획 2|
|--------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|정보 권한 보호(IRM)|예|예[각주 1]|예|예|예|예|예|예|예|
각주 1: Business Premium의 경우 몇 가지 클라이언트 제한 사항이 있습니다. RMS에서 Outlook Web App 및 RMS 공유 앱을 사용하여 콘텐츠를 보호하고 보호된 콘텐츠를 사용할 수 있습니다. Office Online 및 Office 365 Business Premium용 클라이언트 응용 프로그램을 비롯한 다른 모든 Office 응용 프로그램을 사용하여 보호된 콘텐츠를 사용할 수 있습니다.

#### <a name="BKMK_TrialExpiryBehavior"></a>평가용 구독이 만료되는 경우
평가판 구독이 만료되면 Azure RMS의 평가판 구독을 사용하여 보호된 콘텐츠에 액세스할 수 없게 됩니다. 그러나 Azure RMS를 지원하는 구독을 구입하면 액세스 권한이 자동으로 복원됩니다.

단, 평가판 구독을 받기 전에 조직에서 개인용 RMS 구독을 통해 Azure RMS를 사용했던 경우에는 평가판 구독이 만료되어도 콘텐츠 액세스 권한이 유지됩니다. 따라서 평가용 구독이 만료되어도 이전에 보호했던 콘텐츠에 계속 액세스할 수 있습니다.

### Enterprise Mobility Suite 구독
[30일 무료 평가판](http://go.microsoft.com/fwlink/?LinkId=615385)

이 구독은 Azure Active Directory Premium, Windows Intune 및 Azure 권한 관리를 함께 사용하려는 조직을 위해 설계되었습니다. 자세한 내용은 [Microsoft Enterprise Mobility 개요](http://go.microsoft.com/fwlink/?LinkId=615386)를 참조하세요.

|라이선싱 옵션|Office 365 Business Essentials|Office 365 Business Premium|Office 365 Enterprise E1<br /><br />Office 365 Education A1|Office  365  Enterprise  E3<br /><br />Office 365 Education A3<br /><br />Office 365 Government G3|Office 365 Enterprise E4<br /><br />Office 365 Education A4<br /><br />Office 365 Government G4|Office 365 Enterprise E5<br /><br />Office 365 Education A5<br /><br />Office 365 Government G5|Office 365 Enterprise K1|SharePoint 계획 1<br />SharePoint 계획 2|Exchange Online 계획 1<br />Exchange Online 계획 2|
|--------------------|----------------------------------|-------------------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------|----------------------------------------|--------------------------------------------------|
|정보 권한 보호(IRM)|예|예[각주 1]|예|예|예|예|예|예|예|
각주 1: Business Premium의 경우 몇 가지 클라이언트 제한 사항이 있습니다. RMS에서 Outlook Web App 및 RMS 공유 앱을 사용하여 콘텐츠를 보호하고 보호된 콘텐츠를 사용할 수 있습니다. Office Online 및 Office 365 Business Premium용 클라이언트 응용 프로그램을 비롯한 다른 모든 Office 응용 프로그램을 사용하여 보호된 콘텐츠를 사용할 수 있습니다.

### 개인용 RMS 구독
이 구독은 Azure RMS 또는 AD RMS를 배포하지 않은 조직의 개인을 위해 디자인되었습니다. 이 구독을 통해 이러한 사용자는 Azure RMS를 사용 중인 조직에서 보호하는 콘텐츠를 읽을 수 있으며 자신의 콘텐츠를 보호할 수도 있습니다.

자세한 내용은 [개인용 RMS 및 Azure 권한 관리](rms-for-individuals.md)를 참조하세요.

## <a name="BKMK_AzureADTenant"></a>Azure AD 디렉터리
Azure RMS를 사용하려면 Azure AD 디렉터리가 있어야 합니다. Azure 클래식 포털에 로그인하려면 이 디렉터리의 조직 계정을 사용합니다. Azure 클래식 포털에서는 Rights Management 템플릿을 구성 및 관리하는 등의 작업을 할 수 있습니다.

조직에서 아직 Azure를 구독하지 않은 경우 무료 평가판을 신청하여 사용해 볼 수 있습니다. [Azure 시작](https://account.windowsazure.com/organization) 페이지로 이동하여 지침을 따르세요.

자세한 내용은 Azure Active Directory 문서에서 다음 리소스를 참조하세요.

-   [Azure AD 디렉터리란?](http://msdn.microsoft.com/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Azure 구독과 Azure AD의 연관 관계](http://msdn.microsoft.com/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

Azure AD 디렉터리를 온-프레미스 AD 포리스트와 통합하려면 [디렉터리 통합](http://msdn.microsoft.com/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8)을 참조하세요.

> [!NOTE]
> AD FS 또는 이와 동등한 인증 공급자를 사용하여 온-프레미스를 인증하는 모바일 장치나 Mac 컴퓨터를 사용하는 경우
> 
> -   **Windows Server 2012 R2** 이상의 서버 버전이나 OAuth 2.0 프로토콜을 지원하는 다른 인증 공급자에서 AD FS를 사용해야 합니다.

### <a name="BKMK_MFA"></a>Multi-Factor Authentication(MFA) 및 Azure RMS
Azure RMS로 Multi-Factor Authentication(MFA)를 사용하려면 다음 중 하나 이상이 필요합니다.

-   Office 2013(최소 버전)

    -   Office 2013을 사용하는 경우 [Office 2013 2015년 6월 9일 업데이트(KB3054853)](https://support.microsoft.com/kb/3054853)도 설치해야 합니다. 이 업데이트 및 최신 인증이 Office 2013에 ADAL(Active Directory 인증 라이브러리) 기반 로그인을 제공하는 방식에 대한 자세한 내용은 Office 블로그에서 [발표된 Office 2013 최신 인증 공개 미리 보기](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)를 참조하세요.

-   Windows용 권한 관리 공유 응용 프로그램:

    -   제어판, 프로그램 및 기능을 사용하여 확인할 수 있는 1.0.1908.0의 최소 버전을 설치해야 합니다. 공유 응용 프로그램에 대한 자세한 내용은 [Windows용 권한 관리 공유 응용 프로그램](sharing-app-windows.md)을 참조하세요.

-   모바일 장치 및 Mac 컴퓨터에 대한 Rights Management 공유 앱:

    -   설치된 최신 버전이 있는지 확인하세요. MFA 지원은 RMS 공유 앱의 2015년 9월 릴리스에 들어있습니다.

그런 다음 MFA 솔루션을 구성합니다.

-   Microsoft에서 관리하는 테넌트의 경우입니다.(Azure Active Directory 또는 Office 365 보유)

    -   Azure MFA를 구성하여 사용자에 MFA를 적용합니다. 지침은 Azure 설명서에서 [클라우드에서 Azure Multi-Factor Authentication 시작](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/)을 참조하세요.

        Azure MFA에 대한 자세한 내용은 [Azure Multi-Factor Authentication 정의](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)를 참조하세요.

-   페더레이션된 테넌트의 경우입니다.(사용자가 페더레이션 서버 온-프레미스 동작)

    -   Azure Active Directory 또는 Office 365에 페더레이션 서버를 구성합니다. 예를 들어 AD FS를 사용하는 경우 TechNet에서 [AD FS에 대한 추가 인증 방법 구성](https://technet.microsoft.com/library/dn758113.aspx)을 참조하세요.

        이 시나리오에 대한 자세한 내용은 Office 블로그에서 [Office 365로 작동 - 이제 간소화된 ID 프로그램](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/)을 참조하세요.

## <a name="BKMK_SupportedDevices"></a>Azure RMS를 지원하는 클라이언트 장치
다음 섹션을 참조하여 Azure 권한 관리(RMS)를 지원하는 장치와 이러한 장치에서 지원하는 RMS 기능을 확인할 수 있습니다.

-   [컴퓨터](requirements-azure-rms.md#BKMK_RMSSupportedComputers)

-   [모바일 장치](requirements-azure-rms.md#BKMK_RMSSupportedMobileDevices)

-   [클라이언트 장치 기능](requirements-azure-rms.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>컴퓨터
Azure 권한 관리를 지원하는 컴퓨터 운영 체제는 다음과 같습니다.

-   **Windows 7**(x86, x64)

-   **Windows 8**(x86, x64)

-   **Windows 8.1**(x86, x64)

-   **Windows 10**(x86, x64)

-   **Mac OS X**: Mac OS X 10.8(Mountain Lion) 버전 이상

### <a name="BKMK_RMSSupportedMobileDevices"></a>모바일 장치
Azure 권한 관리를 지원하는 모바일 장치 운영 체제는 다음과 같습니다.

-   **Windows Phone**: Windows Phone 8.1

-   **Android 휴대폰 및 태블릿**: 최소 Android 4.0.3 버전 이상

-   **iPhone 및 iPad**: 최소 iOS 7.0 버전 이상

-   **Windows RT 태블릿**: Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>클라이언트 장치 기능
지원되는 모든 클라이언트 장치에서 현재 모든 RMS 기능을 지원하는 것은 아닙니다. 다음 표에서 RMS 기능을 지원하는 응용 프로그램 및 예외를 확인할 수 있습니다.

별도의 설명이 없으면 지원되는 기능은 Azure RMS와 AD RMS 둘 다에 적용됩니다. 또한 iOS, Android, OS X 및 Windows Phone 8.1에서 AD RMS를 지원하려면 [Active Directory Rights Management Services 모바일 장치 확장](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341)이 필요합니다.

테이블 열에 대한 정보:

-   **보호된 PDF**: 파일 이름 확장명이 .ppdf이고 RMS 공유 응용 프로그램을 사용하여 Office 파일 및 PDF 파일을 메일로 공유할 때 자동으로 생성되는 파일입니다. RMS 공유 응용 프로그램에는 보호 PDF 파일용 뷰어가 포함되어 있습니다. 이전에 Azure RMS 또는 AD RMS를 사용하여 보호된 PDF 파일을 만든 경우 Foxit Reader 및 Nitro Pro를 사용하여 Windows, iOS 및 Android 장치에서 해당 파일을 계속 읽을 수 있습니다.

-   **메일:** 나열된 메일 클라이언트는 메일 메시지 자체를 보호할 수 있으므로 첨부된 파일도 자동으로 보호됩니다. 이 시나리오에서 클라이언트의 미리 보기 기능은 권한 있는 받는 사람에게 보호된 콘텐츠(메시지 및 첨부 파일)를 표시할 수 있습니다. 그러나 전자 메일 메시지 자체가 보호되지 않고 첨부 파일만 보호되면, 클라이언트의 미리 보기 기능이 권한 있는 받는 사람에게 보호된 첨부 파일을 표시할 수 없습니다.

-   **기타 파일 형식**: 텍스트 및 이미지 파일에는 파일 이름 확장명이 .txt, .xml, .jpg, .jpeg와 같은 파일이 포함됩니다. 이러한 파일은 RMS의 기본 보호를 통해 읽기 전용으로 바뀌면 파일 확장명이 변경됩니다. 기본 보호를 적용할 수 없는 파일은 RMS의 일반적인 보호를 받으며 파일 확장명으로 .pfile이 지정됩니다. 자세한 내용은 [Rights Management 공유 응용 프로그램 관리자 가이드](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)에서 [보호 수준 – 기본 및 일반](https://technet.microsoft.com/library/dn339003.aspx)과 [지원되는 파일 형식 및 파일 이름 확장명](https://technet.microsoft.com/library/dn339003.aspx) 섹션을 참조하세요.

|**장치 운영 체제**|Word, Excel, PowerPoint|보호된 PDF|전자 메일|다른 파일 형식|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office Mobile 앱(Azure RMS만 해당) [각주 1]<br /><br />Office Online [각주 2]|Gaaiho 문서<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS 공유 앱 |Outlook 2010<br /><br />Outlook 2013<br /><br />OWA(Outlook Web App) [각주 3]<br /><br />Windows Mail [각주 4]|Windows용 RMS 공유 응용 프로그램: 텍스트, 이미지, pfile<br /><br />Siemens JT2Go: JT 파일(Windows 10에만 해당)|
|**iOS**|iPad 및 iPhone용 Office [각주 5]<br /><br />Office Online [각주 2]<br /><br />TITUS Docs|Foxit Reader<br /><br />RMS 공유 앱[각주 1]<br /><br />TITUS Docs|NitroDesk [각주 4]<br /><br />iPad 및 iPhone용 Outlook [각주 4]<br /><br />iOS용 OWA [각주 3]<br /><br />TITUS Mail|RMS 공유 앱 [각주 1]: 텍스트, 이미지, pfile<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online [각주 2]|GigaTrust App for Android<br /><br />Foxit Reader<br /><br />RMS 공유 앱[각주 1]|9Folders [각주 4]<br /><br />GigaTrust App for Android [각주 4]<br /><br />NitroDesk [각주 4]<br /><br />Android용 OWA [각주 3 및 6]<br /><br />Samsung Email(S3 이상) [각주 6]<br /><br />TITUS Classification for Mobile|RMS 공유 앱 [각주 1]: 텍스트, 이미지, pfile|
|**OS X**|Office 2011(AD RMS만 해당)<br /><br />Mac용 Office 2016<br /><br />Office Online [각주 2]|Foxit Reader<br /><br />RMS 공유 앱[각주 1]|Outlook 2011(AD RMS만 해당)<br /><br />Mac용 Outlook 2016<br /><br />Outlook for Mac|RMS 공유 앱 [각주 1]: 텍스트, 이미지, pfile|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [각주 2]|지원되지 않음|Outlook 2013 RT<br /><br />Windows용 메일 앱<br /><br />Windows Mail [각주 4]|Siemens JT2Go: JT 파일|
|**Windows Phone 8.1**|Office Mobile(AD RMS만 해당)|RMS 공유 앱[각주 1]|Outlook Mobile[각주 4]|RMS 공유 앱 [각주 1]: 텍스트, 이미지, pfile|
|**Blackberry 10**|지원되지 않음|지원되지 않음|Blackberry 메일[각주 4]|지원되지 않음|
각주 1: 보호된 콘텐츠 보기를 지원합니다.

각주 2: SharePoint Online, 비즈니스용 OneDrive, Outlook Web Access에서 보호된 콘텐츠 보기를 지원합니다.

각주 3: Exchange 온-프레미스에 사서함이 있는 받는 사람이 보호된 메일을 수신하는 경우 이 콘텐츠는 Outlook과 같은 서식 있는 메일 클라이언트에서만 열 수 있습니다.  이 콘텐츠는 Outlook Web Access에서 열 수 없습니다.

각주 4: Exchange 관리자가 사용하도록 설정해야 하는 Exchange ActiveSync IRM을 사용합니다. 사용자는 보호된 전자 메일 메시지를 보기, 회신 및 전체 회신할 수 있지만 사용자는 새 전자 메일 메시지 자체를 보호할 수 없습니다.

Exchange 온-프레미스에 사서함이 있는 받는 사람이 Exchange를 사용하는 다른 조직으로부터 보호된 전자 메일을 수신하는 경우 이 콘텐츠는 Outlook과 같은 서식 있는 전자 메일 클라이언트에서만 열 수 있습니다.  이 콘텐츠는 Exchange Active Sync IRM을 사용하는 장치에서 열 수 없습니다.

각주 5: 보호된 문서 보기 및 편집을 지원합니다. 자세한 내용은 Office 블로그에서 [iPad 및 iPhone용 Office에 Azure 권한 관리 지원 제공](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) 게시물을 참조하세요.

각주 6: 자세한 내용은 Office 블로그에서 [이제 일부 선택된 장치에서 Android용 OWA를 사용할 수 있음](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) 게시물을 참조하세요.

> [!TIP]
> 다른 플랫폼용 Office에서 제공될 RMS 지원에 대한 자세한 내용은 Office 블로그에서 [어디서나 Office, 어디서나 암호화](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)게시물을 참조하세요.

## <a name="BKMK_SupportedApplications"></a>Azure RMS를 지원하는 응용 프로그램
다음 응용 프로그램은 Azure RMS를 기본적으로 지원합니다. 즉, 이러한 응용 프로그램에는 사용 제한을 지원하기 위해 RMS API를 통해 RMS가 긴밀하게 통합되어 있습니다. 이러한 응용 프로그램을 RMS 지원이라고도 합니다.

-   다음 제품군의 **Microsoft Office 응용 프로그램**(Word, Excel, PowerPoint 및 Outlook)은 Azure RMS를 사용하여 콘텐츠를 보호할 수 있습니다.

    -   Office 365 ProPlus

    -   Office  365  Enterprise  E3

    -   Office 365 Enterprise E4

    -   Office 365 Enterprise E5

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    Office 2007을 제외하고 다른 버전의 Office에서 보호된 콘텐츠를 사용할 수 있습니다.

    > [!NOTE]
    > Office Professional Plus 2010 또는 Office Professional 2010을 사용하는 Azure RMS:
    > 
    > -   Windows용 Rights Management 공유 응용 프로그램이 필요
    > -   Windows 10에서는 지원되지 않음

-   **Windows용 Rights Management 공유 응용 프로그램**

    Windows용 Rights Management 공유 응용 프로그램에 대한 자세한 내용은 다음 리소스를 참조하세요.

    -   [Rights Management 공유 응용 프로그램 관리자 가이드](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Rights Management 공유 응용 프로그램 사용자 가이드](http://technet.microsoft.com/library/dn339006.aspx)

-   **모바일 플랫폼용 Rights Management 공유 응용 프로그램**

    모바일 플랫폼용 Rights Management 공유 응용 프로그램에 대한 자세한 내용은 다음 리소스를 참조하세요.

    -   [Microsoft Rights Management 페이지](http://go.microsoft.com/fwlink/?LinkId=303970)의 링크를 사용하여 관련 앱 다운로드
 
    -   [모바일 플랫폼용 Microsoft Rights Management 공유 응용 프로그램 FAQ](http://technet.microsoft.com/dn451248)

-   **RMS API를 지원하는 기타 응용 프로그램**:

    -   RMS SDK를 사용하여 사내에서 작성한 LOB(기간 업무) 응용 프로그램

    -   소프트웨어 공급업체에서 RMS SDK를 사용하여 작성한 응용 프로그램

    SDK에 대한 자세한 내용은 [Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx)를 참조하세요.

> [!IMPORTANT]
> 다음 응용 프로그램은 Azure RMS에서 현재 지원되지 않습니다.
> 
> -   Microsoft Office for Mac 2011
> -   SharePoint Server 2013에 대한 Microsoft 비즈니스용 OneDrive
> -   XPS 뷰어
> 
> 또한 RMS 공유 응용 프로그램에는 다음과 같은 제한이 있습니다.
> 
> -   Windows 컴퓨터의 경우: 최소 Windows 7 서비스 팩 1 이상 버전이 필요합니다.

이러한 응용 프로그램이 Azure RMS를 지원하는 방식에 대한 자세한 내용은 [응용 프로그램이 Azure 권한 관리를 지원하는 방식](applications-support.md)을 참조하세요.

구성 방법에 대한 자세한 내용은 [Azure 권한 관리에 대해 응용 프로그램 구성](configure-applications.md)을 참조하세요.

## <a name="BKMK_SupportedServers"></a>Azure RMS를 지원하는 온-프레미스 서버
다음 온-프레미스 서버 제품은 Azure RMS 커넥터를 사용할 경우 Azure RMS에서 지원되며, Azure RMS 커넥터는 온-프레미스 서버와 Azure RMS 사이에서 통신 인터페이스(릴레이) 역할을 합니다. 또한 이 구성을 사용하려면 Active Directory 포리스트와 Azure Active Directory 간의 디렉터리 동기화를 구성해야 합니다.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Windows Server를 실행하고 FCI(파일 분류 인프라)를 사용하는 파일 서버**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Windows Server 2008 R2를 실행하는 파일 서버에는 RMS 보호를 적용하는 기본 제공 파일 관리 작업 동작이 없으므로 이 시나리오에는 RMS 커넥터를 사용할 수 없습니다. 그러나 Azure RMS를 사용하여 파일을 보호할 수 있는 사용자 지정 파일 관리 작업(실행 파일 또는 스크립트를 실행)을 구성하는 경우 이러한 운영 체제에서 파일 분류 인프라 및 Azure RMS를 사용할 수 있습니다. 예를 들어 [RMS 보호 cmdlet](https://msdn.microsoft.com/library/azure/mt433195.aspx)을 사용하는 Windows PowerShell 스크립트입니다.
    > 
    > 또한 이러한 cmdlet이 모든 파일 형식을 보호할 수 있다는 혜택을 가진 이후 버전의 Windows Server를 실행하는 서버로 이러한 cmdlet를 사용할 수 있습니다. RMS 커넥터는 Office 파일만을 보호합니다. 방법 지침은 [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](configure-fci.md)를 참조하세요.

RMS 커넥터는 Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2에서 지원됩니다.

이러한 온-프레미스 서버에 대해 RMS 커넥터를 구성하는 방법에 대한 자세한 내용은 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)를 참조하세요.

## 참고 항목
[Azure Rights Management 시작하기](getting-started-with-azure-rights-management.md)



<!--HONumber=Apr16_HO3-->


