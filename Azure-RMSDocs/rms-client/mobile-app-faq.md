---
title: iOS 및 Android용 Azure Information Protection 앱 FAQ
description: ''
keywords: iOS 및 Android용 Azure Information Protection 앱을 사용하는 데 도움이 되는 몇 가지 질문과 대답
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/31/2018
ms.topic: conceptual
ms.service: information-protection
ms.custom: askipteam
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e880fc87bd3685dc6375d3fd598cab707e36f1ba
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151098"
---
# <a name="faqs-for-microsoft-azure-information-protection-app-for-ios-and-android"></a>iOS 및 Android용 Microsoft Azure Information Protection 앱에 대한 FAQ

*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

이 페이지에서는 iOS 및 Android용 Azure Information Protection 앱에 대한 질문과 대답을 제공합니다.

## <a name="what-can-i-do-with-the-azure-information-protection-app"></a>Azure Information Protection 앱으로 수행할 수 있는 작업

메일 앱에서 권한 관리 데이터 보호를 기본적으로 지원하지 않는 경우 이 앱을 사용하여 권한으로 보호된 메일 메시지(.rpmsg 파일)를 볼 수 있습니다. 또한 권한으로 보호되는 PDF 파일과 권한으로 보호되는 사진 및 텍스트 파일도 볼 수 있습니다. 현재 이 앱을 사용하여 보호되는 메일 메시지를 새로 만들거나, 회신하거나, 보호되는 파일을 만들거나 편집할 수 없습니다.

## <a name="can-i-open-pdf-files-that-are-in-sharepoint-protected-libraries-and-onedrive-for-business"></a>SharePoint 보호된 라이브러리 및 비즈니스용 OneDrive에 있는 PDF 파일을 열 수 있나요?

예, 다른 사람이 SharePoint 및 비즈니스용 OneDrive를 통해 공유한 보호된 PDF 파일을 열 수 있습니다. 링크를 탭하고 이 앱을 선택하여 필요한 파일을 열 수 있습니다. 

이 앱을 실행하면 SharePoint 및 비즈니스용 OneDrive 외부에서 보호된 PDF 파일(보호된 PDF 및 .ppdf 파일)도 열 수 있습니다.

## <a name="can-my-mobile-device-run-the-azure-information-protection-app"></a>모바일 장치에서 Azure Information Protection 앱을 실행할 수 있나요?

Azure Information Protection 앱을 사용하려면 **iOS 8** 또는 **Android 4.4** 이상 버전이 필요합니다.

이러한 버전이 있거나 그 이상 버전이 있으면 모바일 장치에 앱을 설치할 수 있습니다.

- 모바일 장치가 Microsoft Intune을 통해 관리되는 경우 회사 포털에서 Azure Information Protection 앱을 설치할 수 있습니다.

- 모바일 장치가 Microsoft Intune을 통해 관리되지 않거나 회사 포털에서 Azure Information Protection을 사용할 수 없으면 iTunes 스토어 및 Google Play 스토어에서 직접 앱을 설치하거나 [Azure Information Protection 다운로드 페이지](https://portal.azurerms.com/#/download)의 **모바일 장치** 섹션에서 iOS 또는 Android 아이콘을 클릭하여 앱을 설치할 수 있습니다. 

## <a name="how-do-i-get-started-with-the-viewer-app"></a>뷰어 앱을 시작하려면 어떻게 하나요?

앱을 설치한 후에는 더 이상 수행할 작업이 없습니다. 보려는 보호된 메일 또는 파일을 받을 때까지 기다린 다음 **AIP 뷰어**를 선택하여 엽니다. 그러면 회사 또는 학교 계정으로 로그인하라는 메시지가 표시되거나 인증서를 선택하라는 메시지가 표시됩니다. 이러한 자격 증명이 인증된 후 내용을 읽을 수 있습니다.

그러나 기다리고 싶지 않은 경우 [iOS 및 Android용 Microsoft Azure Information Protection 앱 시작](mobile-app-get-started.md)의 지침에 따라 자신에게 보려는 보호된 메일 또는 파일을 보낼 수 있습니다. 

## <a name="what-credentials-should-i-use-to-sign-in-to-this-app"></a>이 앱에 로그인하는 데 어떤 자격 증명을 사용해야 하나요?

조직에 AD RMS 온-프레미스(모바일 장치 확장 포함)가 이미 있거나 Azure Rights Management 서비스를 사용하는 경우 회사 자격 증명을 사용하여 로그인합니다. 

파일을 보호하는 데 개인 메일 주소를 사용한 경우에는 [Microsoft 계정](https://signup.live.com)의 자격 증명을 사용하여 로그인합니다.

## <a name="can-i-sign-up-for-the-free-account-with-my-personal-email-address-such-as-a-hotmail-or-gmail-account"></a>개인 메일 주소(예: Hotmail 또는 Gmail 계정)로 무료 계정에 등록할 수 있나요?

예. Microsoft 계정을 신청하면 Hotmail 또는 Gmail 메일 주소나 소유한 다른 메일 주소를 지정할 수 있습니다. 

그러나 이 뷰어는 이 계정으로 보호된 파일을 열 수 있지만 인증에 Microsoft 계정을 사용할 경우, 일부 응용 프로그램이 보호된 콘텐츠를 열 수 없습니다. [추가 정보](../secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="which-file-extensions-can-i-open-with-this-app"></a>이 앱에서 열 수 있는 파일 확장명은 무엇인가요?

.rpmsg, .pdf, .ppdf, .pjpg, .pjpeg, .ptiff, .ppng, .ptxt, .pxml 및 기타 다양한 텍스트 및 이미지 파일 형식을 열 수 있습니다.

텍스트 및 이미지 파일 이름 확장명의 전체 목록은 관리자 가이드의 [분류 및 보호가 지원되는 파일 형식](client-admin-guide-file-types.md#supported-file-types-for-classification-and-protection) 섹션에서 첫 번째 표를 참조하세요.

##  <a name="how-do-i-provide-feedback-about-this-app"></a>이 앱에 대한 피드백을 제공하려면 어떻게 해야 하나요?

앱에서 **설정** > **의견 보내기**로 이동합니다.


## <a name="my-question-has-not-been-answeredwhat-should-i-do"></a>내 질문에 대한 답변이 없습니다. 어떻게 해야 하나요?

[Yammer 사이트](https://www.yammer.com/AskIPTeam)에 질문을 게시하세요.
