---
title: "RMS 데이터 보호를 위한 응용 프로그램 지원 - AIP"
description: "RMS API를 사용하여 Azure Information Protection의 Azure Rights Management 서비스를 기본적으로 지원하는 응용 프로그램을 식별합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 27c970216c2bc0166529270db11304f83f553a07
ms.sourcegitcommit: 1f65f71f742063e2bebcac88f72180d3aa4318a4
translationtype: HT
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Azure Rights Management 데이터 보호를 지원하는 응용 프로그램

>*적용 대상: Azure Information Protection, Office 365*


Azure Information Protection에 대한 데이터 보호를 제공하는 Azure RMS(Azure Rights Management 서비스)를 기본적으로 지원하는 응용 프로그램 및 솔루션을 식별하려면 다음 표를 참조하세요. 

이러한 응용 프로그램 및 솔루션의 경우 Rights Management API를 통해 사용 제한을 지원하여 Rights Management 서비스를 강력히 통합합니다. 이러한 응용 프로그램 및 솔루션을 RMS 지원이라고도 합니다.

별도의 설명이 없으면 지원되는 기능은 Azure RMS와 AD RMS 둘 다에 적용됩니다. 또한 iOS, Android, OS X 및 Windows Phone 8.1에서 AD RMS를 지원하려면 [Active Directory Rights Management Services 모바일 장치 확장](https://technet.microsoft.com/library/dn673574.aspx)이 필요합니다.

## <a name="rms-enlightened-applications"></a>RMS 지원 응용 프로그램

다음 표에는 Microsoft 및 소프트웨어 공급업체에서 제공하는 RMS 지원 클라이언트 응용 프로그램이 표시되어 있습니다.

테이블 열에 대한 정보:

-   **보호된 PDF**: 파일 이름 확장명이 .ppdf이고 RMS 공유 응용 프로그램을 사용하여 Office 파일 및 PDF 파일을 메일로 공유할 때 자동으로 생성되는 파일입니다. RMS 공유 응용 프로그램, iOS/Android용 Azure Information Protection 앱 및 Windows용 Azure Information Protection 클라이언트에는 보호되는 PDF 파일용 판독기가 포함되어 있습니다. 이전에 Azure RMS 또는 AD RMS를 사용하여 보호된 PDF 파일을 만든 경우 Foxit Reader 및 Nitro Pro를 사용하여 Windows, iOS 및 Android 장치에서 해당 파일을 계속 읽을 수 있습니다.

-   **메일:** 나열된 메일 클라이언트는 메일 메시지 자체를 보호할 수 있으므로 첨부된 파일도 자동으로 보호됩니다. 이 시나리오에서 클라이언트의 미리 보기 기능은 권한 있는 받는 사람에게 보호된 콘텐츠(메시지 및 첨부 파일)를 표시할 수 있습니다. 그러나 전자 메일 메시지 자체가 보호되지 않고 첨부 파일만 보호되면, 클라이언트의 미리 보기 기능이 권한 있는 받는 사람에게 보호된 첨부 파일을 표시할 수 없습니다.

-   **기타 파일 형식**: 텍스트 및 이미지 파일에는 파일 이름 확장명이 .txt, .xml, .jpg, .jpeg와 같은 파일이 포함됩니다. 이러한 파일은 Rights Management의 기본 보호를 통해 읽기 전용으로 바뀌면 파일 이름 확장명이 변경됩니다. 기본 보호를 적용할 수 없는 파일은 Rights Management의 일반적인 보호를 받으며 파일 이름 확장명으로 .pfile이 지정됩니다. 자세한 내용은 Azure Information Protection 클라이언트 관리자 가이드에서 [지원되는 파일 형식](../rms-client/client-admin-guide-file-types.md)을 참조하세요.


|**장치 운영 체제**|Word, Excel, PowerPoint|보호된 PDF|메일|다른 파일 형식|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Mobile 앱(Azure RMS에만 해당) [[1]](#footnote-1)<br /><br />Office Online [[2]](#footnote-2)|Windows용 Azure Information Protection 클라이언트 <br /><br />Gaaiho 문서<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS 공유 앱|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />OWA(Outlook Web App) [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4)|Windows용 Azure Information Protection 클라이언트: 텍스트, 이미지, pfile<br /><br />Windows용 RMS 공유 응용 프로그램: 텍스트, 이미지, pfile<br /><br />AutoCAD용 SealPath RMS 플러그 인 [[8]](#footnote-8): .dwg<br />|
|**iOS**|iPad 및 iPhone용 Office [[5]](#footnote-5)<br /><br />Office Online [[2]](#footnote-2)<br /><br />TITUS Docs|Azure Information Protection 앱 [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />TITUS Docs|Azure Information Protection 앱 [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />iPad 및 iPhone용 Outlook [[4]](#footnote-4)<br /><br />iOS용 OWA [[3]](#footnote-3)<br /><br />TITUS Mail|Azure Information Protection 앱 [[1]](#footnote-1): 텍스트, 이미지<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online [[2]](#footnote-2)<br /><br />Office Mobile(Azure RMS에만 해당) [[1]](#footnote-1)|Azure Information Protection 앱 [[1]](#footnote-1)<br /><br />GigaTrust App for Android<br /><br />Foxit Reader<br /><br />RMS 공유 앱 [[1]](#footnote-1)|9Folders [[4]](#footnote-4)<br /><br />Azure Information Protection 앱 [[1]](#footnote-1)<br /><br />GigaTrust App for Android [[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Android용 Outlook [[4]](#footnote-4)<br /><br />Android용 OWA [[3]](#footnote-3) 및 [[7]](#footnote-7)<br /><br />Samsung Email(S3 이상) [[7]](#footnote-7)<br /><br />TITUS Classification for Mobile|Azure Information Protection 앱 [[1]](#footnote-1): 텍스트, 이미지|
|**macOS**|Office 2011(AD RMS만 해당)<br /><br />Mac용 Office 2016<br /><br />Office Online [[2]](#footnote-2)|Foxit Reader<br /><br />RMS 공유 앱 [[1]](#footnote-1)|Outlook 2011(AD RMS만 해당)<br /><br />Mac용 Outlook 2016<br /><br />Outlook for Mac|RMS 공유 앱 [[1]](#footnote-1): 텍스트, 이미지, pfile|
|**Windows 10 Mobile**|Office Mobile 앱(Azure RMS에만 해당) [[1]](#footnote-1)|지원되지 않음|Citrix WorxMail [[6]](#footnote-6)<br /><br />Outlook 메일|지원되지 않음|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[2]](#footnote-2)|지원되지 않음|Outlook 2013 RT<br /><br />Windows용 메일 앱<br /><br />Windows Mail [[4]](#footnote-4)|Siemens JT2Go: JT 파일|
|**Windows Phone 8.1**|Office Mobile(AD RMS만 해당)|RMS 공유 앱 [[1]](#footnote-1)|Outlook Mobile [[4]](#footnote-4)|RMS 공유 앱 [[1]](#footnote-1): 텍스트, 이미지, pfile|
|**Blackberry 10**|지원되지 않음|지원되지 않음|Blackberry 메일 [[4]](#footnote-4)|지원되지 않음|


###### <a name="footnote-1"></a>각주 1
사용권 계약에 따라 보호하는 콘텐츠 보기를 지원합니다.

###### <a name="footnote-2"></a>각주 2 
SharePoint Online 및 비즈니스용 OneDrive에서 보호되지 않은 문서를 보호된 라이브러리로 업로드하는 경우 보호된 문서 보기를 지원합니다. 

###### <a name="footnote-3"></a>각주 3
받는 사람이 보호된 메일을 수신하고 Exchange를 메일 서버로 사용하지 않거나 보내는 사람이 다른 조직에 속하는 경우, 이 콘텐츠는 Outlook과 같은 서식 있는 메일 클라이언트에서만 열 수 있습니다. 이 콘텐츠는 Outlook Web Access에서 열 수 없습니다.

###### <a name="footnote-4"></a>각주 4
Exchange 관리자가 사용하도록 설정해야 하는 Exchange ActiveSync IRM을 사용합니다. 사용자는 보호된 메일 메시지를 보기, 회신 및 전체 회신할 수 있지만 사용자는 새 메일 메시지 자체를 보호할 수 없습니다.

받는 사람이 보호된 메일을 수신하고 Exchange를 메일 서버로 사용하지 않거나 보내는 사람이 다른 조직에 속하는 경우, 이 콘텐츠는 Outlook과 같은 서식 있는 메일 클라이언트에서만 열 수 있습니다. 이 콘텐츠는 Exchange Active Sync IRM을 사용하여 모바일 메일 클라이언트 또는 Outlook Web Access에서 열 수 없습니다.

###### <a name="footnote-5"></a>각주 5
iOS용 보호된 문서 보기 및 편집을 지원하고, Android용 보호된 문서 보기를 지원합니다. 자세한 내용은 Office 블로그에서 [iPad 및 iPhone용 Office에 Azure 권한 관리 지원 제공](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) 게시물을 참조하세요.

###### <a name="footnote-6"></a>각주 6
자세한 내용은 Citrix [WorxMail에 대한 제품 설명서](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html)를 참조하세요.

###### <a name="footnote-7"></a>각주 7
자세한 내용은 Office 블로그에서 [이제 일부 선택된 장치에서 Android용 OWA를 사용할 수 있음](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) 게시물을 참조하세요.

###### <a name="footnote-8"></a>각주 8
자세한 내용은 Enterprise Mobility + Security 블로그에서 [SealPath brings RMS protection to AutoCAD](https://blogs.technet.microsoft.com/enterprisemobility/2015/09/08/sealpath-brings-rms-protection-to-autocad/)(SealPath에서 AutoCAD에 대한 RMS 보호 제공) 게시물을 참조하세요.


### <a name="more-information-about-azure-rms-support-for-office"></a>Office에 대한 Azure RMS 지원과 관련된 자세한 내용

Azure RMS는 Word, Excel, PowerPoint 및 Outlook 앱에 긴밀하게 통합되어 있으며, 이러한 앱에서 이 기능은 종종 IRM(정보 권한 관리)이라고 불립니다. 다음 Office 클라이언트 버전은 Azure RMS를 사용하여 파일 및 메일 보호를 지원합니다.

- Office 365 ProPlus: Office 2016 및 Office 2013

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Office 2007을 제외하고 모든 버전의 Office에서 보호된 콘텐츠를 사용할 수 있습니다.

Office Professional Plus 2010 또는 Office Professional 2010을 사용하는 Azure RMS:

- Windows용 Azure Information Protection 클라이언트 또는 Windows용 Rights Management 공유 응용 프로그램이 필요합니다.

- Windows 10에서는 지원되지 않음

- 페더레이션된 사용자 계정에 대한 양식 기반 인증은 지원되지 않습니다. 이러한 계정은 Windows 통합 인증을 사용해야 합니다.

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>iOS 및 Android용 Azure Information Protection 앱에 대한 자세한 내용

iOS 및 Android용 Azure Information Protection 앱은 이러한 장치에 대한 RMS 공유 앱을 대체합니다. 동일한 기능을 제공하고 SharePoint Online에서 권한으로 보호되는 메일 메시지와 권한으로 보호되는 PDF 파일을 지원합니다.

Microsoft Intune에서 iOS 및 Android 장치를 등록하는 경우 정책 관리 앱을 사용하여 이 앱을 배포 및 관리할 수 있습니다. 자세한 내용은 Intune 설명서에서 [Microsoft Intune 콘솔에서 모바일 응용 프로그램 관리 정책 구성 및 배포](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)를 참조하세요. 이 Intune 설명서에서 2단계에서는 정책 관리 앱 게시 지침을 사용합니다.

자세한 내용은 [iOS 및 Android용 Microsoft Azure Information Protection 앱에 대한 FAQ](../rms-client/mobile-app-faq.md)를 참조하세요.


### <a name="more-information-about-the-azure-information-protection-client-for-windows"></a>Windows용 Azure Information Protection 클라이언트에 대한 자세한 내용

이 클라이언트는 Windows용 Rights Management 공유 응용 프로그램을 대신합니다. 

자세한 내용은 다음 참조 자료를 참조하세요.

- [Azure Information Protection 클라이언트 관리자 가이드](../rms-client/client-admin-guide.md)

- [Azure Information Protection 클라이언트 사용자 가이드](../rms-client/client-user-guide.md)

- [iOS 및 Android용 Azure Information Protection 앱 FAQ](../rms-client/mobile-app-faq.md)

[Microsoft Azure Information Protection 페이지](http://go.microsoft.com/fwlink/?LinkId=303970)의 링크를 사용하여 관련 앱을 다운로드하세요.

### <a name="more-information-about-the-rights-management-sharing-application"></a>Rights Management 공유 응용 프로그램에 대한 자세한 내용

이 응용 프로그램은 Azure Information Protection 클라이언트로 대체되고 있습니다. Mac 컴퓨터 및 Windows Phone 모바일 장치에는 여전히 필요합니다. 

자세한 내용은 다음 참조 자료를 참조하세요.

-   [Rights Management 공유 응용 프로그램 관리자 가이드](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management 공유 응용 프로그램 사용자 가이드](../rms-client/sharing-app-user-guide.md)

-   [모바일 플랫폼용 Microsoft Rights Management 공유 응용 프로그램 FAQ](https://technet.microsoft.com/dn451248)

[Microsoft Azure Information Protection 페이지](http://go.microsoft.com/fwlink/?LinkId=303970)의 링크를 사용하여 Mac 컴퓨터 및 Windows Phone용 앱을 다운로드하세요.


### <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Azure Information Protection을 지원하는 다른 응용 프로그램에 대한 자세한 내용

표에 나와 있는 응용 프로그램 외에도 Azure Rights Management 서비스용 API를 지원하는 다음과 같은 모든 응용 프로그램을 Azure Information Protection과 통합할 수 있습니다.

- RMS SDK를 사용하여 사내에서 작성한 LOB(기간 업무) 응용 프로그램

- 소프트웨어 공급업체에서 RMS SDK를 사용하여 작성한 응용 프로그램

자세한 내용은 [Azure Information Protection 개발자 가이드](../develop/developers-guide.md)를 참조하세요.

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Azure RMS에서 지원되지 않는 응용 프로그램

Azure RMS에서 현재 지원되지 않는 응용 프로그램은 다음과 같습니다.

-   Microsoft Office for Mac 2011

-   SharePoint Server 2013에 대한 Microsoft 비즈니스용 OneDrive

-   XPS 뷰어
 
또한 RMS 공유 응용 프로그램 및 Azure Information Protection 클라이언트에 다음과 같은 제한 사항이 적용됩니다.

-   Windows 컴퓨터의 경우: 최소 Windows 7 서비스 팩 1 이상 버전이 필요합니다.

## <a name="rms-enlightened-solutions"></a>RMS 지원 솔루션

다음 표에는 소프트웨어 공급업체에서 제공하는 RMS 지원 솔루션이 표시되어 있습니다.

이 표에 나열되어 있지 않은 솔루션을 보유하나 소프트웨어 공급업체의 경우는 응용 프로그램을 Azure AD에 등록합니다. 자세한 내용은 [Azure AD에서 RMS를 등록하고 앱을 사용하도록 설정하는 방법](../develop/authentication-integration.md)을 참조하세요.


|제품|공급업체|설명|
|-------------------------------|---------------------------|-----------------|
|절대|절대|DLP(데이터 손실 방지)를 통한 콘텐츠 보호.|
|Content Locker|VMware|보호된 콘텐츠를 저장, 소비, 생성합니다.|
|Controle|TakeControle|레이블 지정 및 보호를 사용한 eDiscovery.|
|Halocore|Secude|SAP 환경에서 내보낸 파일을 보호합니다.|
|MaaS 360|IBM|문서 소비 및 보호를 위한 통합.|
|Mobiliya|Mobiliya|EMC의 Documentum 리포지토리에서 문서를 보호합니다.
|Ramessys|Ramessys|Chemcart 및 Documentum 통합.
|Sealpath|Sealpath Technologies|AutoCAD 및 Siemens Jt2GO와 같은 CAD 설계 도구와의 통합.
|SecRMM|Sqaudra Technologies |이동식 미디어의 문서 보호.
|Security Sheriff|CryptZone |분류 및 액세스 권한을 기반으로 SharePoint에서 액세스 관리 및 문서 보호.


## <a name="next-steps"></a>다음 단계
기타 요구 사항을 확인하려면 [Azure Information Protection에 대한 요구 사항](requirements-azure-rms.md)을 참조하세요.

자주 사용하는 응용 프로그램이 Azure RMS를 지원하는 방식에 대한 자세한 내용은 [응용 프로그램이 Azure 권한 관리 서비스를 지원하는 방식](../understand-explore/applications-support.md)을 참조하세요.

자주 사용하는 응용 프로그램을 Azure RMS에 대해 구성하는 방법에 대한 자세한 내용은 [Azure 권한 관리에 대해 응용 프로그램 구성](../deploy-use/configure-applications.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]