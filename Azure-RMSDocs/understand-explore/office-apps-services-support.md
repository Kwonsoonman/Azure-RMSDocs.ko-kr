---
title: "Office 응용 프로그램 및 서비스 | Azure Information Protection"
description: "최종 사용자 Office 응용 프로그램(예: Word, Excel, PowerPoint, Outlook) 및 Office 서비스(예: Exchange, SharePoint)에서 Azure Rights Management 서비스를 사용하여 조직의 데이터를 보호하는 방법을 소개합니다."
author: cabailey
manager: mbaldwin
ms.date: 10/31/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3571ab868d2476d6683317295d366f973a88ff43
ms.openlocfilehash: 4cb92bc420eecc0102f144a66a579d58aa4112b5


---


# <a name="office-applications-and-services"></a>Office 응용 프로그램 및 서비스

>*적용 대상: Azure Information Protection, Office 365*

최종 사용자 Office 응용 프로그램(예: Word, Excel, PowerPoint, Outlook) 및 Office 서비스(예: Exchange, SharePoint)에서 Azure Information Protection의 Azure Rights Management 서비스를 사용하여 조직의 데이터를 보호할 수 있습니다.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Office 응용 프로그램: Word, Excel, PowerPoint, Outlook
이러한 응용 프로그램은 정보 권한 관리(IRM)를 사용하여 Rights Management를 기본적으로 지원하며 사용자가 저장된 문서 또는 전송할 메일 메시지에 보호를 적용할 수 있도록 합니다. 사용자는 템플릿을 적용하거나 Word, Excel 및 PowerPoint의 경우 액세스, 권한 및 사용 제한을 위해 자세하게 사용자 지정된 설정을 선택할 수 있습니다. 

예를 들어 사용자는 조직 내의 사용자만 액세스할 수 있도록 Word 문서를 구성할 수도 있고 Excel 스프레드시트의 편집 가능 여부를 제어하거나 파일을 읽기 전용으로 제한하거나 파일 인쇄를 차단할 수도 있습니다. 시간이 중요한 파일의 경우에는 파일에 더 이상 액세스할 수 없는 만료 시간을 구성할 수 있습니다(사용자가 직접 구성하거나 템플릿 적용). Outlook에서는 사용자가 템플릿을 선택하는 일 외에 **전달 금지** 옵션을 선택하여 데이터 유출을 방지할 수도 있습니다.

## <a name="exchange-online-and-exchange-server"></a>Exchange Online 및 Exchange Server
Exchange Online 또는 Exchange Server를 사용할 때는 IRM(정보 권한 관리) 통합을 사용하면 정보 보호 솔루션이 추가로 제공됩니다.

-   **Exchange ActiveSync IRM** - 모바일 장치에서 메일 메시지를 보호하고 보호된 메일 메시지를 사용할 수 있습니다.

-   **Outlook Web App**용 RMS 지원 - Outlook 클라이언트와 비슷한 방식으로 구현되며, 사용자가 템플릿을 적용하거나 개별 옵션을 지정하여 메일 메시지를 보호할 수 있으며 자신에게 전송되는 보호된 메일 메시지를 읽고 사용할 수 있습니다.

-   Outlook 클라이언트용 **보호 규칙** - 관리자가 지정된 받는 사람의 메일 메시지에 Rights Management 템플릿을 자동으로 적용하도록 구성하는 규칙입니다. 예를 들어 법률 자문 부서로 전송하는 내부 메일은 법률 자문 부서 구성원만 읽을 수 있으며 전달할 수 없도록 구성할 수 있습니다. 사용자는 메일 메시지를 보내기 전에 메시지에 적용되는 보호를 확인할 수 있으며 기본적으로 보호가 필요하지 않다고 판단되면 제거할 수 있습니다. 메일은 전송되기 전에 암호화됩니다. 자세한 내용은 Exchange 라이브러리에서 [Outlook 보호 규칙](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) 및 [Outlook 보호 규칙 만들기](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx)를 참조하세요.

-   **전송 규칙** - 관리자가 보낸 사람, 받는 사람, 메시지 제목, 내용 등의 속성을 기준으로 메일 메시지에 Rights Management 템플릿을 자동으로 적용하도록 구성하는 규칙입니다. 이러한 규칙은 개념상 보호 규칙과 비슷하지만 사용자가 보호를 제거할 수 없고, 모바일 장치에서 보내는 메일과 Outlook Web Access에도 적용 가능하며, 클라이언트에서 메일 메시지를 보내기 전에 암호화하지 않는다는 점이 다릅니다. 자세한 내용은 Exchange 라이브러리에서 [전송 보호 규칙 만들기](https://technet.microsoft.com/library/dd302432.aspx)를 참조하세요.

-   **DLP(데이터 손실 방지) 정책** - 메일 메시지를 필터링하고 기밀 또는 중요한 데이터(예: 개인 정보 또는 신용 카드 정보)에 대해 데이터 손실을 방지하기 위한 작업을 수행하는 조건 집합을 포함하는 정책입니다. 중요한 데이터가 검색되면 정책 팁을 사용하여 메일 메시지의 정보를 기준으로 정보 보호를 적용해야 할 수 있다는 알림을 사용자에게 표시할 수 있습니다. 자세한 내용은 Exchange 라이브러리에서 [데이터 손실 방지](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx)를 참조하세요.

-   **Office 365 메시지 암호화** - 전송 규칙을 사용하여 회사 외부 사용자에게 암호화된 메일을 보냅니다. 이러한 메일은 Outlook Web App과 비슷한 인터페이스가 포함된 브라우저에서 읽을 수 있습니다. 회사의 암호화된 메일에서 고지 사항 텍스트와 헤더 텍스트를 사용자 지정할 수 있으며 회사 로고도 추가할 수 있습니다. 자세한 내용은 Office 웹사이트에서 [Office 365 메시지 암호화](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx)를 참조하세요.

Exchange Server를 사용하는 경우에는 온-프레미스 서버와 Azure Rights Management 서비스 간의 릴레이 역할을 하는 RMS 커넥터를 배포하여 Azure Rights Management 서비스를 통해 정보 보호 기능을 사용할 수 있습니다. 자세한 내용은 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.

## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online 및 SharePoint Server
SharePoint Online 또는 SharePoint Server를 사용할 때는 IRM(정보 권한 관리) 통합을 사용할 수 있습니다. 그러면 관리자가 목록 또는 라이브러리를 보호할 수 있습니다. 그러므로 사용자가 문서를 체크 아웃할 때 파일이 보호된 상태이기 때문에 지정한 정보 보호 정책에 따라 권한이 있는 사용자만 파일을 확인 및 사용할 수 있습니다. 예를 들어 파일을 읽기 전용으로 지정하고, 텍스트를 복사할 수 없도록 설정하고, 로컬 복사본 저장 및 파일 인쇄를 금지할 수 있습니다.

목록 및 라이브러리의 경우 항상 최종 사용자가 아닌 관리자가 정보 보호 기능을 적용합니다. 그리고 개별 파일이 아니라 해당 컨테이너의 모든 문서에 대해 목록 또는 라이브러리 수준에서 적용됩니다.  SharePoint Online을 사용하면 사용자는 IRM을 비즈니스 라이브러리용 OneDrive에 적용할 수 있습니다.

이렇게 하려면 먼저 SharePoint에 대해 IRM 서비스를 사용하도록 설정해야 합니다. 그런 다음 라이브러리에 대한 정보 권한 관리를 지정합니다. SharePoint Online 및 비즈니스용 OneDrive의 경우, 사용자는 비즈니스 라이브러리용 OneDrive에 대해 정보 권한 관리도 지정할 수 있습니다. SharePoint는 템플릿에서 지정할 수 있는 설정과 거의 근접하게 선택할 수 있는 SharePoint 구성 설정이 있더라도 권한 정책 템플릿을 사용하지 않습니다.

SharePoint Server를 사용하는 경우에는 온-프레미스 서버와 Azure Rights Management 클라우드 서비스 간의 릴레이 역할을 하는 RMS 커넥터를 배포하여 Rights Management 서비스를 통해 정보 보호 기능을 사용할 수 있습니다. 자세한 내용은 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.

> [!NOTE]
> 현재 SharePoint와 함께 IRM을 사용하는 경우 다음과 같이 몇 가지 제한 사항이 있습니다.
> 
> - 기본값 또는 Azure 클래식 포털에서 관리하는 사용자 지정 템플릿을 사용할 수 없습니다.
> - 보호된 PDF 파일에 대한 .PPDF 파일 이름 확장명을 가진 파일은 지원되지 않습니다. 기본적으로 Rights Management를 지원하는 PDF Reader를 사용하는 경우 파일 이름 확장명이 .PDF이며 Rights Management로 기본적으로 보호되는 파일이 지원됩니다.


Azure RMS는 문서를 SharePoint에서 처음 만들거나 라이브러리로 업로드할 때가 아니라 SharePoint에서 다운로드할 때 문서에 사용 제한 및 데이터 암호화를 적용합니다. 문서가 다운로드되기 전에 보호하는 방법에 대한 자세한 내용은 SharePoint 설명서에서 [비즈니스용 OneDrive 및 SharePoint Online의 데이터 암호화](https://technet.microsoft.com/library/dn905447.aspx) 를 참조하세요.

SharePoint와 함께 Azure Rights Management 서비스를 사용하는 방법에 대한 자세한 내용은 Office 블로그의 [What’s New with Information Rights Management in SharePoint and SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)(SharePoint와 SharePoint Online의 정보 권한 관리의 새로운 기능) 게시물을 참조하세요.

## <a name="next-steps"></a>다음 단계

다른 응용 프로그램과 서비스에서 Azure Information Protection의 Azure Rights Management 서비스를 지원하는 방식을 보려면 [응용 프로그램이 Azure Rights Management 서비스를 지원하는 방식](applications-support.md)을 참조하세요.


<!--HONumber=Oct16_HO5-->


