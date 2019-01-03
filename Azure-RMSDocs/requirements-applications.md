---
title: RMS 데이터 보호를 위한 애플리케이션 지원 - AIP
description: RMS API를 사용하여 Azure Information Protection의 Azure Rights Management 서비스를 기본적으로 지원하는 애플리케이션을 식별합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/13/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: cc823bcb175c9f4181d365a8caf99da33171c338
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173913"
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Azure Rights Management 데이터 보호를 지원하는 애플리케이션

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Azure Information Protection에 대한 데이터 보호를 제공하는 Azure RMS(Azure Rights Management 서비스)를 기본적으로 지원하는 애플리케이션 및 솔루션을 식별하려면 다음 표를 참조하세요.

이러한 애플리케이션 및 솔루션의 경우 Rights Management API를 통해 사용 제한을 지원하여 Rights Management 서비스를 강력히 통합합니다. 이러한 애플리케이션 및 솔루션을 "RMS 지원"이라고도 합니다.

별도의 설명이 없으면 지원되는 기능은 Azure RMS와 AD RMS 둘 다에 적용됩니다. 또한 iOS, Android, macOS 및 Windows Phone 8.1에서 AD RMS를 지원하려면 [Active Directory Rights Management Services 모바일 디바이스 확장](https://technet.microsoft.com/library/dn673574.aspx)이 필요합니다.

## <a name="rms-enlightened-applications"></a>RMS 지원 애플리케이션

다음 표에는 Microsoft 및 소프트웨어 공급업체에서 제공하는 RMS 지원 클라이언트 애플리케이션이 표시되어 있습니다. 

보호된 PDF 문서를 보는 방법에 대한 정보는 [Microsoft Information Protection에 대한 보호된 PDF reader](./rms-client/protected-pdf-readers.md)를 참조하세요.

테이블 열에 대한 정보:

-   **이메일:** 나열된 이메일 클라이언트는 이메일 메시지 자체를 보호할 수 있으므로 아직 보호되지 않은 첨부된 모든 Office 파일도 자동으로 보호됩니다. 이 시나리오에서 클라이언트의 미리 보기 기능은 권한 있는 받는 사람에게 보호된 콘텐츠(메시지 및 첨부 파일)를 표시할 수 있습니다. 그러나 전자 메일 메시지 자체가 보호되지 않고 첨부 파일만 보호되면, 클라이언트의 미리 보기 기능이 권한 있는 받는 사람에게 보호된 첨부 파일을 표시할 수 없습니다. 
    
    팁: 팁: 이메일 보호를 지원하지 않는 이메일 클라이언트의 경우 [Exchange Online 메일 흐름 규칙을 사용하여 이 보호를 적용](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8)하는 것이 좋습니다.

-   **다른 파일 형식**: 텍스트 및 이미지 파일에는 파일 확장명이 .txt, .xml, .jpg 및 .jpeg와 같은 파일이 포함됩니다. 이러한 파일은 Rights Management의 기본 보호를 통해 읽기 전용으로 바뀌면 파일 이름 확장명이 변경됩니다. 기본 보호를 적용할 수 없는 파일은 Rights Management의 일반적인 보호를 받으며 파일 이름 확장명으로 .pfile이 지정됩니다. 자세한 내용은 Azure Information Protection 클라이언트 관리자 가이드에서 [지원되는 파일 형식](./rms-client/client-admin-guide-file-types.md)을 참조하세요.


|**장치 운영 체제**|Word, Excel, PowerPoint|메일|다른 파일 형식|
|---------------------------|-----------------------|-----------------|---------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office Online(보호된 문서 보기)[[1]](#footnote-1)<br /><br />웹 브라우저 [[2]](#footnote-2)|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />웹 브라우저 [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4) |Windows용 Azure Information Protection 클라이언트: 텍스트, 이미지, pfile<br /><br />Windows용 RMS 공유 응용 프로그램: 텍스트, 이미지, pfile<br /><br />AutoCAD용 SealPath RMS 플러그 인: .dwg|
|**iOS**|GigaTrust<br /><br /> Office Mobile(보호된 문서 보기 및 편집)<br /><br />Office Online [[1]](#footnote-1)<br /><br />TITUS Docs<br /><br />웹 브라우저 [[2]](#footnote-2)|Azure Information Protection 앱(보호된 전자 메일 보기)<br /><br />BlackBerry 작업<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />iPad 및 iPhone용 Outlook [[4]](#footnote-4)<br /><br />TITUS Mail <br /><br />웹 브라우저 [[3]](#footnote-3)|Azure Information Protection 앱(텍스트 및 이미지 보호 보기)<br /><br />TITUS Docs: Pfile|
|**OWA(Outlook Web Access)**|GigaTrust App for Android<br /><br />Office Online [[1]](#footnote-1)<br /><br />Office Mobile <br /><br />웹 브라우저 [[2]](#footnote-2)|9Folders [[4]](#footnote-4)<br /><br />Azure Information Protection 앱(보호된 전자 메일 보기)<br /><br />BlackBerry 작업 <br /><br />Android용 GigaTrust App [[4]](#footnote-4)<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Android용 Outlook [[4]](#footnote-4)<br /><br />Samsung Email(S3 이상) [[4]](#footnote-4)<br /><br />TITUS Classification for Mobile <br /><br />웹 브라우저 [[3]](#footnote-3)|Azure Information Protection 앱(보호된 텍스트 및 이미지 보기)|
|**macOS**|Mac용 Office 2016<br /><br />Office Online [[1]](#footnote-1)<br /><br />웹 브라우저 [[2]](#footnote-2)|Mac용 Outlook 2016<br /><br />웹 브라우저 [[3]](#footnote-3)|RMS 공유 앱(보호된 텍스트, 이미지, 일반적으로 보호된 파일 보기)|
|**Windows 10 Mobile**|Office Mobile 앱(Azure RMS를 사용하여 보호된 문서 보기) <br /><br />웹 브라우저 [[2]](#footnote-2)|Citrix WorxMail <br /><br />Outlook 메일(보호된 메일 보기) <br /><br />웹 브라우저 [[3]](#footnote-3)|지원되지 않음|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[1]](#footnote-1)<br /><br />웹 브라우저 [[2]](#footnote-2)|Outlook 2013 RT<br /><br />Windows용 메일 앱<br /><br />웹 브라우저 [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4)|Siemens JT2Go: JT 파일|
|**Windows Phone 8.1**|Office Mobile(AD RMS만 해당)<br /><br />웹 브라우저 [[2]](#footnote-2)|Outlook Mobile [[4]](#footnote-4) <br /><br />웹 브라우저 [[3]](#footnote-3)|RMS 공유 앱(보호된 텍스트, 이미지, 일반적으로 보호된 파일 보기)|
|**Blackberry 10**|웹 브라우저 [[2]](#footnote-2)|Blackberry 메일 [[4]](#footnote-4) <br /><br />웹 브라우저 [[3]](#footnote-3)|지원되지 않음|

###### <a name="footnote-1"></a>각주 1
SharePoint Online 및 비즈니스용 OneDrive에서만 지원되며, 문서는 먼저 보호된 라이브러리에 업로드해야 보호할 수 있습니다.

###### <a name="footnote-2"></a>각주 2
[새로운 기능을 갖춘 Office 365 메시지 암호화](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)를 사용하여 보호되는 [Office 첨부 파일](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM)에 해당합니다.

###### <a name="footnote-3"></a>각주 3
보낸 사람과 받는 사람이 동일한 조직에 속하는 경우. 또는 다음 조건 중 하나:

- 보낸 사람 또는 받는 사람이 Exchange Online을 사용하고 있습니다.

- 보낸 사람이 하이브리드 구성으로 Exchange 온-프레미스를 사용하고 있습니다. 

###### <a name="footnote-4"></a>각주 4
Exchange 관리자가 사용하도록 설정해야 하는 Exchange ActiveSync IRM을 사용합니다. 사용자는 보호된 전자 메일 메시지를 보고, 회신하고, 전체 회신할 수 있지만 사용자는 새 전자 메일 메시지를 보호할 수 없습니다.
 
Exchange ActiveSync IRM을 사용하도록 설정되지 않아서 전자 메일 애플리케이션에서 메시지를 렌더링할 수 없는 경우, 받는 사람은 보낸 사람이 Exchange Online을 사용할 때 웹 브라우저에서 전자 메일을 보거나 하이브리드 구성으로 Exchange 온-프레미스의 전자 메일을 볼 수 있습니다. 



### <a name="more-information-about-azure-rms-support-for-office"></a>Office에 대한 Azure RMS 지원과 관련된 자세한 내용

Azure RMS는 Word, Excel, PowerPoint 및 Outlook 앱에 긴밀하게 통합되어 있으며, 이러한 앱에서 이 기능은 종종 IRM(정보 권한 관리)이라고 불립니다. 

참고 항목: [Office 애플리케이션 서비스 설명](https://technet.microsoft.com/library/office-applications-service-description.aspx)

#### <a name="windows-computers-for-information-rights-management-irm"></a>IRM(정보 권한 관리)용 Windows 컴퓨터

다음 Office 클라이언트 제품군은 Azure Rights Management 서비스를 사용하여 Windows 컴퓨터에서 파일 및 메일 보호를 지원합니다.

- 사용자에게 Azure Rights Management(Office 365용 Azure Information Protection이라고도 함) 라이선스가 지정될 경우 Office 365(Office 2016 앱)(최소 버전 1805, 빌드 9330.2078)

- Office 365 ProPlus: Office 2016 및 Office 2013
    
    이러한 Office 버전은 Azure Information Protection에서 데이터 보호를 포함하는 Office 365 구독의 전부는 아니지만 대부분이 포함됩니다. Office 365 ProPlus가 포함되어 있는지 확인하려면 구독 정보를 확인합니다. 또한 이 정보는 [Azure Information Protection 데이터 시트](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)에서 찾을 수 있습니다.

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010 서비스 팩 2

Office 2007을 제외하고 모든 버전의 Office에서 보호된 콘텐츠를 사용할 수 있습니다.

Office Professional Plus 2010 서비스 팩 2 또는 Office Professional 2010 서비스 팩 2에서 Azure Rights Management 서비스를 사용하는 경우 다음이 적용됩니다.

- Windows용 Azure Information Protection 클라이언트 또는 Windows용 Rights Management 공유 애플리케이션이 필요합니다.

- Windows 10에서는 지원되지 않음.

- 페더레이션된 사용자 계정에 대한 양식 기반 인증은 지원되지 않습니다. 이러한 계정은 Windows 통합 인증을 사용해야 합니다.

- 사용자가 Azure Information Protection 클라이언트에서 선택한 사용자 지정 권한으로 템플릿 보호를 재정의하는 것은 지원되지 않습니다. 이 시나리오에서는 사용자 지정 사용 권한을 적용하기 전에 원래 보호를 먼저 제거해야 합니다.

#### <a name="mac-computers-for-information-rights-management-irm"></a>IRM(정보 권한 관리)용 Mac 컴퓨터

다음 Office 클라이언트 제품군은 Azure RMS를 사용하여 macOS에서 파일 및 메일 보호를 지원합니다.

- Office 365 ProPlus: Office 2016

- Mac용 Office Standard 2016

팁: Mac용 Office를 사용하여 문서를 보호하려면 다음과 같은 유용한 FAQ를 찾아볼 수 있습니다: [문서를 보호하고 추적하도록 Mac 컴퓨터를 구성하려면 어떻게 해야 하나요?](faqs-rms.md#how-do-i-configure-a-mac-computer-to-protect-and-track-documents)

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>iOS 및 Android용 Azure Information Protection 앱에 대한 자세한 내용

iOS 및 Android용 Azure Information Protection 뷰어 앱은 이러한 디바이스에 대한 RMS 공유 앱을 대체합니다. 동일한 기능을 제공하고 SharePoint Online에서 권한으로 보호되는 메일 메시지와 권한으로 보호되는 PDF 파일을 지원합니다.

Microsoft Intune에서 iOS 및 Android 디바이스를 등록하는 경우 정책 관리 앱을 사용하여 이 앱을 배포 및 관리할 수 있습니다. 자세한 내용은 Intune 설명서에서 [Microsoft Intune 콘솔에서 모바일 애플리케이션 관리 정책 구성 및 배포](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)를 참조하세요. 이 Intune 설명서에서 2단계에서는 정책 관리 앱 게시 지침을 사용합니다.

자세한 내용은 [iOS 및 Android용 Microsoft Azure Information Protection 앱에 대한 FAQ](./rms-client/mobile-app-faq.md)를 참조하세요.


### <a name="more-information-about-the-azure-information-protection-client-for-windows"></a>Windows용 Azure Information Protection 클라이언트에 대한 자세한 내용

이 클라이언트는 Windows용 Rights Management 공유 애플리케이션을 대신합니다.

자세한 내용은 다음 참조 자료를 참조하세요.

- [Azure Information Protection 클라이언트 관리자 가이드](./rms-client/client-admin-guide.md)

- [Azure Information Protection 클라이언트 사용자 가이드](./rms-client/client-user-guide.md)

- [iOS 및 Android용 Azure Information Protection 앱 FAQ](./rms-client/mobile-app-faq.md)

[Microsoft Azure Information Protection 페이지](https://go.microsoft.com/fwlink/?LinkId=303970)의 링크를 사용하여 관련 앱을 다운로드하세요.

### <a name="more-information-about-the-rights-management-sharing-application"></a>Rights Management 공유 애플리케이션에 대한 자세한 내용

이 애플리케이션은 Azure Information Protection 클라이언트로 대체되고 있습니다. 하지만 Windows Phone 모바일 디바이스에서 보호된 파일을 보려면 여전히 필요합니다. 

Mac 컴퓨터의 경우 보호된 PDF 파일(.ppdf), 보호된 텍스트 이미지 및 일반적으로 보호되는 파일에 대한 뷰어를 제공합니다. Mac용 RMS 공유 앱은 이미지 파일을 보호할 수 있지만 다른 파일은 보호할 수 없습니다. Office 파일을 보호하려면 Mac용 Office를 사용합니다. 

자세한 내용은 다음 참조 자료를 참조하세요.

-   [Rights Management 공유 응용 프로그램 관리자 가이드](./rms-client/sharing-app-admin-guide.md)

-   [Rights Management 공유 응용 프로그램 사용자 가이드](./rms-client/sharing-app-user-guide.md)

-   [모바일 플랫폼용 Microsoft Rights Management 공유 응용 프로그램 FAQ](https://technet.microsoft.com/dn451248)

[Microsoft Azure Information Protection 페이지](https://go.microsoft.com/fwlink/?LinkId=303970)의 링크를 사용하여 Mac 컴퓨터 및 Windows Phone용 뷰어를 다운로드하세요.


### <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Azure Information Protection을 지원하는 다른 애플리케이션에 대한 자세한 내용

표에 나와 있는 애플리케이션 외에도 Azure Rights Management 서비스용 API를 지원하는 다음과 같은 모든 애플리케이션을 Azure Information Protection과 통합할 수 있습니다.

- RMS SDK를 사용하여 사내에서 작성한 LOB(기간 업무) 애플리케이션

- 소프트웨어 공급업체에서 RMS SDK를 사용하여 작성한 애플리케이션

자세한 내용은 [Azure Information Protection 개발자 가이드](./develop/developers-guide.md)를 참조하세요.

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Azure RMS에서 지원되지 않는 애플리케이션

Azure RMS에서 현재 지원되지 않는 애플리케이션은 다음과 같습니다.

-   SharePoint Server 2013에 대한 Microsoft 비즈니스용 OneDrive

-   XPS 뷰어

또한 RMS 공유 애플리케이션 및 Azure Information Protection 클라이언트에 다음과 같은 제한 사항이 적용됩니다.

-   Windows 컴퓨터의 경우: 최소 Windows 7 서비스 팩 1 버전이 필요함

## <a name="rms-enlightened-solutions"></a>RMS 지원 솔루션

다음 표에는 소프트웨어 공급업체에서 제공하는 RMS 지원 솔루션이 표시되어 있습니다.

이 표에 나열되어 있지 않은 솔루션을 보유하나 소프트웨어 공급업체의 경우는 애플리케이션을 Azure AD에 등록합니다. 자세한 내용은 [Azure AD에서 RMS를 등록하고 앱을 사용하도록 설정하는 방법](./develop/authentication-integration.md)을 참조하세요.


|제품|공급업체|설명|
|-------------------------------|---------------------------|-----------------|
|Absolute|Absolute|DLP(데이터 손실 방지)를 통한 콘텐츠 보호.|
|Content Locker|VMware|보호된 콘텐츠를 저장, 소비, 생성합니다.|
|Controle|TakeControle|레이블 지정 및 보호를 사용한 eDiscovery.|
|Forcepoint|Forcepoint DLP|조직의 데이터 보안 정책을 적용하는 엔드포인트 DLP(데이터 손실 방지) 솔루션입니다.|
|Halocore|Secude|SAP 환경에서 내보낸 파일을 보호합니다.|
|MaaS 360|IBM|문서 소비 및 보호를 위한 통합.|
|Mobiliya|Mobiliya|EMC의 Documentum 리포지토리에서 문서를 보호합니다.
|Ramessys|Ramessys|Chemcart 및 Documentum 통합.
|Sealpath|Sealpath Technologies|AutoCAD 및 Siemens Jt2GO와 같은 CAD 설계 도구와의 통합.
|SecRMM|Sqaudra Technologies |이동식 미디어의 문서 보호.
|Security Sheriff|CryptZone |분류 및 액세스 권한을 기반으로 SharePoint에서 액세스 관리 및 문서 보호.
|Symantec DLP|Symantec |보호된 파일에 대한 검색 및 모니터링.

## <a name="next-steps"></a>다음 단계
기타 요구 사항을 확인하려면 [Azure Information Protection에 대한 요구 사항](requirements.md)을 참조하세요.

자주 사용하는 애플리케이션이 Azure RMS를 지원하는 방식에 대한 자세한 내용은 [애플리케이션이 Azure 권한 관리 서비스를 지원하는 방식](./applications-support.md)을 참조하세요.

자주 사용하는 애플리케이션을 Azure RMS에 대해 구성하는 방법에 대한 자세한 내용은 [Azure 권한 관리에 대해 애플리케이션 구성](configure-applications.md)을 참조하세요.

