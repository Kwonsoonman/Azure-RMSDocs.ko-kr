---
title: "iOS 및 Android용 Azure Information Protection 앱에 대한 FAQ | Azure Information Protection"
description: 
keywords: "iOS 및 Android용 Azure Information Protection 앱을 사용하는 데 도움이 되는 몇 가지 질문과 대답"
author: cabailey
manager: mbaldwin
ms.date: 11/03/2016
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2f1930f4657278d25ef6dd369866f16e4ba71644
ms.openlocfilehash: 1cafa88ded2bf951f8af93e4b27cc526735d19e8


---

# <a name="faqs-for-microsoft-azure-information-protection-app-for-ios-and-android"></a>iOS 및 Android용 Microsoft Azure Information Protection 앱에 대한 FAQ

*적용 대상: Active Directory Rights Management Services, Azure Information Protection*

이 페이지에서는 iOS 및 Android용 Azure Information Protection 앱에 대한 질문과 대답을 제공합니다.

## <a name="what-can-i-do-with-the-azure-information-protection-app"></a>Azure Information Protection 앱으로 수행할 수 있는 작업

메일 앱에서 권한 관리 데이터 보호를 기본적으로 지원하지 않는 경우 이 앱을 사용하여 권한으로 보호된 메일 메시지(.rpmsg 파일)를 볼 수 있습니다. 또한 권한으로 보호되는 PDF 파일과 권한으로 보호되는 사진 및 텍스트 파일도 볼 수 있습니다. 현재 이 앱을 사용하여 보호되는 메일 메시지를 새로 만들거나, 회신하거나, 보호되는 파일을 만들거나 편집할 수 없습니다.

## <a name="can-i-open-pdf-files-that-are-in-sharepoint-protected-libraries-and-onedrive-for-business"></a>SharePoint 보호된 라이브러리 및 비즈니스용 OneDrive에 있는 PDF 파일을 열 수 있나요?

예, 다른 사람이 SharePoint 및 비즈니스용 OneDrive를 통해 공유한 보호된 PDF 파일을 열 수 있습니다. 링크를 탭하고 이 앱을 선택하여 필요한 파일을 열 수 있습니다. 

## <a name="how-do-i-get-started-with-the-viewer-app"></a>뷰어 앱을 시작하려면 어떻게 하나요?

모바일 장치에서 뷰어의 작동을 확인하려면 앱에서 지원하는 파일 중 하나에 액세스해야 합니다. 예를 들면 다음과 같습니다.

- **.rpmsg 파일**: 이 권한으로 보호된 메일 메시지는 모바일 장치의 메일 앱에서 권한 관리 데이터 보호를 기본적으로 지원하지 않는 경우 메일 메시지의 첨부 파일로 표시됩니다. 
    
    모바일 장치에서 액세스할 수 있는 권한으로 보호된 메일 메시지를 다른 장치를 사용하여 자신에게 보냅니다. 예를 들어 Windows 컴퓨터에서 Outlook을 사용합니다. 권한 관리를 기본적으로 지원하는 메일 클라이언트 목록은 [Azure Rights Management 데이터 보호를 지원하는 응용 프로그램](../get-started/requirements-applications.md) 페이지에서 메일 열을 참조하세요.

- **권한으로 보호된 PDF 파일**: Windows 컴퓨터에서 Rights Management 공유 응용 프로그램이나 권한 관리를 기본적으로 지원하는 PDF 응용 프로그램을 사용하여 권한으로 보호된 PDF 파일을 메일 첨부 파일로 자신에게 보냅니다. 또는 PDF 파일을 SharePoint 보호된 라이브러리로 업로드한 다음 메일 주소를 사용하여 이 파일을 공유합니다.

- **.ptxt, .pjpg 또는 .ppng**: Windows 컴퓨터에서 Rights Management 공유 응용 프로그램과 [보호된 항목 공유](sharing-app-protect-by-email.md) 옵션을 사용하여 보호된 파일을 메일 첨부 파일로 자신에게 보냅니다. 테스트에 사용할 수 있는 파일 형식의 전체 목록은 Rights Management 공유 응용 프로그램 관리자 가이드의 [지원되는 파일 형식 및 파일 이름 확장명](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) 섹션에서 첫 번째 표를 참조하세요. 

Azure Information Protection 뷰어 응용 프로그램에서 이러한 파일을 보려면 메일 첨부 파일이나 링크를 탭합니다. 여는 데 사용할 앱을 선택하라는 메시지가 표시되면 **AIP 뷰어** 앱을 선택합니다. 회사 또는 학교 계정에 로그인하라는 메시지가 표시됩니다. 성공적으로 인증되면 Azure Information Protection 앱에 읽을 메일이나 파일이 표시됩니다.

## <a name="what-credentials-should-i-use-to-sign-in-to-this-app"></a>이 앱에 로그인하는 데 어떤 자격 증명을 사용해야 하나요?

조직에 AD RMS 온-프레미스(모바일 장치 확장 포함)가 이미 있거나 Azure Rights Management 서비스를 사용하는 경우 자격 증명을 사용하여 로그인할 수 있습니다. 그렇지 않은 경우 [Azure Information Protection 페이지](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload)를 사용하여 새 계정을 무료로 등록할 수 있습니다.

## <a name="can-i-sign-up-for-the-free-account-with-my-personal-email-address-such-as-a-hotmail-or-gmail-account"></a>개인 메일 주소(예: Hotmail 또는 Gmail 계정)로 무료 계정에 등록할 수 있나요?

아직은 아닙니다. 현재는 비즈니스 메일 주소(직장 또는 학교 계정)로만 등록할 수 있습니다. 현재 개인 메일 주소를 지원하기 위해 노력하고 있으며 사용 가능한 경우 이 항목을 업데이트할 것입니다.

## <a name="which-file-extensions-can-i-open-with-this-app"></a>이 앱에서 열 수 있는 파일 확장명은 무엇인가요?

.rpmsg, .pdf, .ppdf, .pjpg, .ptxt 및 기타 다양한 텍스트 및 이미지 파일 형식을 열 수 있습니다.

##  <a name="how-do-i-provide-feedback-about-this-app"></a>이 앱에 대한 피드백을 제공하려면 어떻게 해야 하나요?

앱에서 **설정** > **의견 보내기**로 이동합니다.


## <a name="my-question-has-not-been-answeredwhat-should-i-do"></a>내 질문에 대한 답변이 없습니다. 어떻게 해야 하나요?

질문을 [Yammer 사이트](http://www.yammer.com/AskIPTeam)에 게시하거나 [Information Protection 팀에 메일을 보내 주세요](mailto:askIPteam@microsoft.com?subject=Question%20about%20Azure%20Information%20Protection%20app).



<!--HONumber=Nov16_HO1-->


