---
title: "Azure Information Protection에 대한 FAQ"
description: "Azure Information Protection과, 데이터 보호 서비스인 Azure Rights Management(Azure RMS)에 대한 몇 가지 질문과 대답입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b27a4b536e135526bb7e1b4236e88b85b6ea84b1
ms.sourcegitcommit: 7b773ca5bf1abf30e527c34717ecb2dc96f88033
translationtype: HT
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Azure Information Protection 질문과 대답

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection 또는 Azure RMS(Azure Rights Management 서비스)에 대해 질문이 있나요? 여기에 해당 질문에 대한 대답이 있는지 확인하세요.

이 FAQ 페이지는 정기적으로 업데이트되며, 새로 추가된 내용은 [Enterprise Mobility and Security Blog(Enterprise Mobility 및 보안 블로그)](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services)의 월간 설명서 업데이트 공지에 등록됩니다.

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Azure Information Protection과 Azure Rights Management의 차이는 무엇인가요?

Azure Information Protection은 조직의 문서와 메일을 분류하고, 레이블 지정하고, 보호하는 기능을 제공합니다. Azure Rights Management는 보호 기술에서 사용됩니다. 즉 Azure Information Protection의 구성 요소입니다.

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>Azure Information Protection을 사용하려면 어떤 구독이 필요하며, 포함된 기능은 무엇인가요?
Azure Information Protection 사이트의 [구독 정보](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 및 [기능 목록](https://www.microsoft.com/cloud-platform/azure-information-protection-features)을 참조하세요. 

Rights Management를 포함하는 Office 365 구독이 있는 경우 **기능** 페이지에서 [Azure Information Protection 라이선싱 데이터시트](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)를 다운로드하세요.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Azure Information Protection 클라이언트는 분류 및 레이블이 포함된 구독에만 사용할 수 있나요?

아니요. Azure Information Protection 클라이언트에서 본 대부분의 프레젠테이션과 데모에는 분류 및 레이블을 지원하는 방법이 표시되어 있지만, Azure Rights Management 서비스만으로 데이터를 보호하는 구독에도 이 클라이언트를 사용할 수 있습니다.

Windows용 Azure Information Protection 클라이언트가 설치되어 있고 Azure Information Protection 정책이 없는 경우는 클라이언트가 자동으로 [보호 전용 모드](../rms-client/client-protection-only-mode.md)에서 작동합니다. 이 모드에서 사용자는 Rights Management 템플릿과 사용자 지정 권한을 쉽게 적용할 수 있습니다. 나중에 분류 및 레이블 지정이 포함된 구독을 구입하면 Azure Information Protection 정책을 다운로드할 때 클라이언트가 자동으로 표준 모드로 전환됩니다.

현재 Windows용 Rights Management 공유 응용 프로그램을 사용하고 있다면 Azure Information Protection 클라이언트로 교체할 것을 권장합니다. 공유 응용 프로그램에 대한 지원은 2018년 1월 31일에 종료됩니다. 전환에 관한 도움말은 [RMS 공유 응용 프로그램으로 수행해왔던 작업](../rms-client/upgrade-client-app.md)을 참조하세요.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Azure Information Protection에서는 온-프레미스 및 하이브리드 시나리오를 지원하나요?

예. Azure Information Protection은 클라우드 기반 솔루션이지만 클라우드 뿐 아니라 온-프레미스에 저장된 문서 및 전자 메일을 분류, 레이블 지정 및 보호할 수 있습니다.

Exchange Server, SharePoint Server 및 Windows 파일 서버가 있는 경우 [Rights Management 커넥터](../deploy-use/deploy-rms-connector.md)를 배포하여 이러한 온-프레미스 서버가 Azure Rights Management 서비스를 통해 전자 메일 및 문서를 보호하도록 할 수 있습니다. [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)등을 통해, 더 원활한 인증 환경을 위해 Active Directory 도메인 컨트롤러를 동기화 및 페더레이션할 수도 있습니다.

Azure Rights Management 서비스는 필요에 따라 XrML 인증서를 자동으로 생성하여 관리하므로 온-프레미스 PKI를 사용하지 않습니다. Azure Rights Management에서 인증서를 사용하는 방식에 대한 자세한 내용은 [Azure RMS 작동 방식](../understand-explore/how-does-it-work.md) 문서에서 [Azure RMS 작동 방식 연습: 첫 번째 사용, 콘텐츠 보호, 콘텐츠 소비](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) 섹션을 참조하세요.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>곧 새 릴리스가 Azure Information Protection용으로 나올 예정이라고 들었습니다. 언제 나오나요?

기술 설명서에는 예정된 릴리스에 대한 정보가 없습니다. 이러한 종류의 정보와 릴리스 발표에 대해서는 [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services)(Enterprise Mobility 및 보안 블로그)를 확인하고 Twitter의 [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy)에서 최신 업데이트를 받으세요. 관심이 있는 Office 릴리스의 경우에는 [Office 블로그](https://blogs.office.com/)도 꼭 확인하세요.

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>법적 정보, 규정 준수, SLA 등의 Azure Information Protection 관련 지원 정보는 어디서 찾을 수 있나요?

[Azure Information Protection에 대한 규정 준수 및 지원 정보](../understand-explore/compliance.md)를 참조하세요.

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Azure Information Protection에 대한 문제를 보고하거나 의견을 보낼 수 있나요?

기술 지원에 대해서는 표준 지원 채널을 사용하거나 [Microsoft 지원에 문의](information-support.md#to-contact-microsoft-support)하세요.

향상된 기능 또는 새 기능에 대한 제안과 같은 피드백을 보내려면 Office 응용 프로그램의 **홈** 탭에 있는 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다. **Microsoft Azure Information Protection** 대화 상자에서 **피드백 보내기**를 클릭합니다. 그러면 Information Protection 팀으로 보낼 메일 메시지가 열립니다. 또한 엔지니어링 팀과 의견을 나눌 수 있게 [Azure Information Protection Yammer 사이트](https://www.yammer.com/askipteam/)에 여러분을 초대합니다. 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>내 문의 내용이 여기 없다면 어떻게 하나요?

먼저 분류 및 레이블 지정 또는 데이터 보호와 관련된 질문과 대답을 검토합니다. Azure RMS(Rights Management Service)는 Azure Information Protection에 대한 데이터 보호 기술을 제공하며, Azure RMS는 분류 및 레이블 지정과 함께 사용하거나 분류 및 레이블 지정 없이 사용할 수 있습니다. 

- [분류 및 레이블 지정에 대한 FAQ](faqs-infoprotect.md)

- [데이터 보호에 대한 FAQ](faqs-rms.md)

질문에 대한 대답이 되지 않으면 [Azure Information Protection에 대한 정보 및 지원](information-support.md)에 나열된 링크와 리소스를 사용합니다.

최종 사용자를 위한 FAQ도 있습니다.

- [iOS 및 Android용 Azure Information Protection 앱 FAQ](../rms-client/mobile-app-faq.md)

- [Mac 컴퓨터 및 Windows Phone용 RMS 공유 앱에 대 한 FAQ](https://technet.microsoft.com/dn451248)

- [FAQ for Rights Management Sharing Application for Windows](https://technet.microsoft.com/dn467883)(Windows용 Rights Management 공유 응용 프로그램 FAQ)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

