---
title: "Azure Information Protection을 사용하는 Office 앱 및 서비스"
description: "최종 사용자 Office 응용 프로그램(예: Word, Excel, PowerPoint, Outlook) 및 Office 서비스(예: Exchange, SharePoint)에서 Azure Rights Management 서비스를 사용하여 조직의 데이터를 보호하는 방법을 소개합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d812476d882525b1fd5686418151188e57afa80d
ms.sourcegitcommit: 724b0b5d7a3ab694643988148ca68c0eac769f1e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/21/2017
---
# <a name="office-applications-and-services"></a>Office 응용 프로그램 및 서비스

>*적용 대상: Azure Information Protection, Office 365*

최종 사용자 Office 응용 프로그램(예: Word, Excel, PowerPoint, Outlook) 및 Office 서비스(예: Exchange, SharePoint)에서 Azure Information Protection의 Azure Rights Management 서비스를 사용하여 조직의 데이터를 보호할 수 있습니다.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Office 응용 프로그램: Word, Excel, PowerPoint, Outlook
이러한 응용 프로그램은 정보 권한 관리(IRM)를 사용하여 Rights Management를 기본적으로 지원하며 사용자가 저장된 문서 또는 전송할 메일 메시지에 보호를 적용할 수 있도록 합니다. 사용자는 템플릿을 적용하거나 Word, Excel 및 PowerPoint의 경우 액세스, 권한 및 사용 제한을 위해 사용자 지정된 설정을 선택할 수 있습니다. 

예를 들어 사용자는 조직 내의 사용자만 액세스할 수 있도록 Word 문서를 구성할 수도 있고 Excel 스프레드시트의 편집 가능 여부를 제어하거나 파일을 읽기 전용으로 제한하거나 파일 인쇄를 차단할 수도 있습니다. 시간이 중요한 파일의 경우에는 파일에 더 이상 액세스할 수 없는 만료 시간을 구성할 수 있습니다(사용자가 직접 구성하거나 템플릿 적용). Outlook에서는 사용자가 템플릿을 선택하는 일 외에 **전달 금지** 옵션을 선택하여 데이터 유출을 방지할 수도 있습니다.

이러한 응용 프로그램은 네이티브 IRM 지원 외에도 [Azure Information Protection 클라이언트](../rms-client/aip-client.md)와 함께 설치되는 Azure Information Protection 표시줄도 지원합니다. 이 표시줄에는 사용자가 자동으로 중요한 데이터가 포함된 문서 및 전자 메일에 Rights Management 보호를 보다 쉽게 적용할 수 있는 레이블이 표시됩니다.

Office 앱 및 Azure Information Protection 클라이언트를 구성할 준비가 된 경우:

- Office 앱을 구성하려면 [Office 앱: 클라이언트 구성](../deploy-use/configure-office-apps.md)을 참조하세요.

- Azure Information Protection 클라이언트를 설치 및 구성하려면 [Azure Information Protection 클라이언트: 클라이언트 설치 및 구성](../deploy-use/configure-client.md)을 참조하세요.

## <a name="exchange-online-and-exchange-server"></a>Exchange Online 및 Exchange Server
Exchange Online 또는 Exchange Server를 사용할 때는 IRM(정보 권한 관리) 통합을 사용하면 정보 보호 솔루션이 추가로 제공됩니다.

-   **Exchange ActiveSync IRM** - 모바일 장치에서 메일 메시지를 보호하고 보호된 메일 메시지를 사용할 수 있습니다.

-   **Outlook Web App**용 RMS 지원 - Outlook 클라이언트와 비슷한 방식으로 구현되며, 사용자가 템플릿을 적용하거나 개별 옵션을 지정하여 메일 메시지를 보호할 수 있으며 자신에게 전송되는 보호된 메일 메시지를 읽고 사용할 수 있습니다.

-   Outlook 클라이언트용 **보호 규칙** - 관리자가 지정된 받는 사람의 메일 메시지에 Rights Management 템플릿을 자동으로 적용하도록 구성하는 규칙입니다. 예를 들어 법률 자문 부서로 전송하는 내부 메일은 법률 자문 부서 구성원만 읽을 수 있으며 전달할 수 없도록 구성할 수 있습니다. 사용자는 메일 메시지를 보내기 전에 메시지에 적용되는 보호를 확인할 수 있으며 기본적으로 보호가 필요하지 않다고 판단되면 제거할 수 있습니다. 메일은 전송되기 전에 암호화됩니다. 자세한 내용은 Exchange 라이브러리에서 [Outlook 보호 규칙](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) 및 [Outlook 보호 규칙 만들기](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx)를 참조하세요.

-   **전송 규칙** - 관리자가 보낸 사람, 받는 사람, 메시지 제목, 내용 등의 속성을 기준으로 메일 메시지에 Rights Management 템플릿을 자동으로 적용하도록 구성하는 규칙입니다. 이러한 규칙은 개념상 보호 규칙과 비슷하지만 사용자가 보호를 제거할 수 없고, 모바일 장치에서 보내는 메일과 Outlook Web Access에도 적용 가능하며, 클라이언트에서 메일 메시지를 보내기 전에 암호화하지 않는다는 점이 다릅니다. 자세한 내용은 Exchange 라이브러리에서 [전송 보호 규칙 만들기](https://technet.microsoft.com/library/dd302432.aspx)를 참조하세요.

-   **DLP(데이터 손실 방지) 정책** - 메일 메시지를 필터링하고 기밀 또는 중요한 데이터(예: 개인 정보 또는 신용 카드 정보)에 대해 데이터 손실을 방지하기 위한 작업을 수행하는 조건 집합을 포함하는 정책입니다. 중요한 데이터가 검색되면 정책 팁을 사용하여 메일 메시지의 정보를 기준으로 정보 보호를 적용해야 할 수 있다는 알림을 사용자에게 표시할 수 있습니다. 자세한 내용은 Exchange 라이브러리에서 [데이터 손실 방지](https://technet.microsoft.com/library/jj150527(v=exchg.160).aspx)를 참조하세요.

-   **Office 365 메시지 암호화** - 전송 규칙을 사용하여 회사 외부 사용자에게 암호화된 메일을 보냅니다. 이러한 메일은 Outlook Web App과 비슷한 인터페이스가 포함된 브라우저에서 읽을 수 있습니다. 회사의 암호화된 메일에서 고지 사항 텍스트와 헤더 텍스트를 사용자 지정할 수 있으며 회사 로고도 추가할 수 있습니다. 자세한 내용은 Office 웹사이트에서 [Office 365 메시지 암호화](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx)를 참조하세요.

Exchange Server를 사용하는 경우에는 온-프레미스 서버와 Azure Rights Management 서비스 간의 릴레이 역할을 하는 RMS 커넥터를 배포하여 Azure Rights Management 서비스를 통해 정보 보호 기능을 사용할 수 있습니다.

IRM에 대해 Exchange를 구성할 준비가 된 경우:

- Exchange Online에 관한 내용은 [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration)을 참조하세요.

- Exchange 온-프레미스에 관한 내용은 [Azure Rights Management 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.


## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online 및 SharePoint Server

SharePoint Online 또는 SharePoint Server를 사용할 때 IRM(정보 권한 관리)을 사용하여 문서를 보호할 수 있습니다. 이 구성을 사용하면 관리자가 목록 또는 라이브러리를 보호할 수 있습니다. 그러므로 사용자가 문서를 체크 아웃할 때 다운로드된 파일이 보호된 상태이기 때문에 지정한 정보 보호 정책에 따라 권한이 있는 사용자만 파일을 확인 및 사용할 수 있습니다. 예를 들어 파일을 읽기 전용으로 지정하고, 텍스트를 복사할 수 없도록 설정하고, 로컬 복사본 저장 및 파일 인쇄를 금지할 수 있습니다.

기본적으로 보호는 문서를 다운로드하는 사람에게 제한됩니다. 하지만 SharePoint의 문서에 대해 액세스 권한이 있는 모든 사용자 또는 사용자가 지정한 그룹으로 보호를 확장하는 구성 옵션을 사용하여 이러한 제한을 변경할 수 있습니다.

SharePoint 목록 및 라이브러리의 경우 항상 최종 사용자가 아닌 관리자가 정보 보호 기능을 구성합니다. 사용 권한은 사이트 수준에서 설정하며, 이러한 사용 권한은 기본적으로 해당 사이트에 있는 모든 목록 또는 라이브러리에 상속됩니다. SharePoint Online을 사용하면 사용자는 IRM 보호를 위해 비즈니스 라이브러리용 OneDrive를 구성할 수도 있습니다.

보다 세부적으로 제어하려면 부모로부터 사용 권한의 상속을 중단하도록 해당 사이트 내에 목록 또는 라이브러리를 구성할 수 있습니다. 그런 후에 해당 수준(목록 또는 라이브러리)에서 IRM 사용 권한을 구성하면 그 사용 권한을 "고유 사용 권한"이라고 합니다. 그러나 사용 권한은 항상 컨테이너 수준에서 설정되며, 개별 파일에서 사용 권한을 설정할 수는 없습니다. 

이렇게 하려면 먼저 SharePoint에 대해 IRM 서비스를 사용하도록 설정해야 합니다. 그런 다음 라이브러리의 IRM 사용 권한을 지정합니다. SharePoint Online 및 비즈니스용 OneDrive의 경우, 사용자는 비즈니스 라이브러리용 OneDrive에 대해 IRM 사용 권한도 지정할 수 있습니다. SharePoint는 템플릿에서 지정할 수 있는 몇 가지 설정과 일치하며 선택 가능한 SharePoint 구성 설정이 있더라도 권한 정책 템플릿을 사용하지 않습니다.

SharePoint Server를 사용하는 경우에 Azure Rights Management 커넥터를 배포하여 이 IRM 보호 기능을 사용할 수 있습니다. 이 커넥터는 온-프레미스 서버와 Rights Management 클라우드 서비스 사이에서 릴레이 역할을 합니다. 자세한 내용은 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.

> [!NOTE]
> 현재 SharePoint IRM을 사용하는 경우 다음과 같이 몇 가지 제한 사항이 있습니다.
> 
> - 기본값 또는 Azure 클래식 포털에서 관리하는 사용자 지정 템플릿을 사용할 수 없습니다. 
> 
> - 보호된 PDF 파일에 대한 .PPDF 파일 이름 확장명을 가진 파일은 지원되지 않습니다. 기본적으로 Rights Management를 지원하는 PDF Reader를 사용하는 경우 파일 이름 확장명이 .PDF이며 Rights Management로 기본적으로 보호되는 파일이 지원됩니다.


IRM 보호를 사용할 때, Azure Rights Management 서비스는 문서를 SharePoint에서 처음 만들거나 라이브러리로 업로드할 때가 아니라 SharePoint에서 다운로드할 때 문서에 사용 제한 및 데이터 암호화를 적용합니다. 문서가 다운로드되기 전에 보호하는 방법에 대한 자세한 내용은 SharePoint 설명서에서 [비즈니스용 OneDrive 및 SharePoint Online의 데이터 암호화](https://technet.microsoft.com/library/dn905447.aspx) 를 참조하세요.

Office 블로그 게시물 [SharePoint와 SharePoint Online의 정보 권한 관리의 새로운 기능](https://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)에 있는 내용은 더 이상 새로운 정보가 아니지만, 유용한 추가 정보 몇 가지가 있습니다.

IRM에 대해 SharePoint를 구성할 준비가 된 경우:

- SharePoint Online에 관한 내용은 [SharePoint Online 및 비즈니스용 OneDrive: IRM 구성](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)을 참조하세요.

- Sharepoint Server에 관한 내용은 [Azure Rights Management 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.


## <a name="next-steps"></a>다음 단계

Office 365를 사용하는 경우 Office 365의 파일 보호에 대해 권장되는 기능을 제공하는 [Office 365의 파일 보호 솔루션](https://technet.microsoft.com/library/dn919927.aspx#BKMK_O365fileprotect)을 검토하는 데 관심이 있을 수 있습니다.

다른 응용 프로그램과 서비스에서 Azure Information Protection의 Azure Rights Management 서비스를 지원하는 방식을 보려면 [응용 프로그램이 Azure Rights Management 서비스를 지원하는 방식](applications-support.md)을 참조하세요.

이러한 응용 프로그램 및 서비스의 구성을 포함한 배포를 시작할 준비가 되면 [Azure Information Protection 배포 로드맵](../plan-design/deployment-roadmap.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]