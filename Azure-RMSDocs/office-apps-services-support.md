---
title: Office 앱 및 서비스가 AIP에서 Azure RMS를 지원하는 방법
description: '최종 사용자 Office 응용 프로그램(예: Word 및 Outlook) 및 Office 서비스(예: Exchange 및 SharePoint)에서 AIP의 Azure Rights Management 서비스를 사용하여 조직의 데이터를 보호하는 방법을 소개합니다.'
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/13/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e1a44fb7cf6e4ad340a89f236920e5ff6d96b7d0
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173998"
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>Office 응용 프로그램 및 서비스에서 Azure Rights Management를 지원하는 방법 

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

최종 사용자 Office 응용 프로그램 및 Office 서비스에서 Azure Information Protection의 Azure Rights Management 서비스를 사용하여 조직의 데이터를 보호할 수 있습니다. 이 Office 응용 프로그램은 Word, Excel, PowerPoint 및 Outlook입니다. Office 서비스는 Exchange 및 SharePoint입니다. Azure Rights Management 서비스를 지원하는 Office 구성에서 종종 **IRM(정보 권한 관리)** 이라는 용어를 사용합니다.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Office 응용 프로그램: Word, Excel, PowerPoint, Outlook
이러한 응용 프로그램은 Azure Rights Management를 기본적으로 지원하며 사용자가 저장된 문서 또는 전송할 메일 메시지에 보호를 적용할 수 있도록 합니다. 사용자는 보호를 적용하는 [템플릿](configure-policy-templates.md)을 적용할 수 있습니다. 또는 Word, Excel 및 PowerPoint의 경우 액세스, 권한 및 사용 제한을 위해 사용자 지정된 설정을 선택할 수 있습니다.

예를 들어 조직의 사용자만 액세스할 수 있도록 Word 문서를 구성할 수 있습니다. 또는 Excel 스프레드시트를 편집할 수 있는지, 읽기 전용으로 제한되는지, 아니면 인쇄되지 못하게 방지되는지 제어합니다. 시간이 중요한 파일의 경우에는 파일에 더 이상 액세스할 수 없는 만료 시간을 구성할 수 있습니다. 이 구성은 사용자가 직접 만들거나 보호 템플릿을 적용하여 만들 수 있습니다. Outlook에서는 사용자가 **전달 금지** 옵션을 선택하여 데이터 유출을 방지할 수도 있습니다.

이러한 응용 프로그램은 네이티브 Officedml Azure Rights Management 지원 외에도 [Azure Information Protection 클라이언트](./rms-client/aip-client.md)와 함께 설치되는 Azure Information Protection 표시줄도 지원합니다. 이 표시줄에는 사용자가 자동으로 중요한 데이터가 포함된 문서 및 메일에 보호를 보다 쉽게 적용할 수 있는 레이블이 표시됩니다.

Office 앱 및 Azure Information Protection 클라이언트를 구성할 준비가 된 경우:

- Office 앱을 구성하려면 [Office 앱: 클라이언트 구성](configure-office-apps.md)을 참조하세요.

- Azure Information Protection 클라이언트를 설치 및 구성하려면 [Azure Information Protection 클라이언트: 클라이언트 설치 및 구성](configure-client.md)을 참조하세요.

## <a name="exchange-online-and-exchange-server"></a>Exchange Online 및 Exchange Server
Exchange Online 또는 Exchange Server를 사용하는 경우 Azure Information Protection에 대한 옵션을 구성할 수 있습니다. 이 구성을 사용하면 Exchange에서 다음 보호 솔루션을 제공할 수 있습니다.

-   **Exchange ActiveSync IRM** - 모바일 장치에서 메일 메시지를 보호하고 보호된 메일 메시지를 사용할 수 있습니다.

-   Outlook 클라이언트와 비슷하게 구현된 **웹의 Outlook**의 메일 보호 지원 이 구성을 사용하면 보호 템플릿 또는 옵션을 사용하여 메일 메시지를 보호할 수 있습니다. 사용자가 받은 보호된 메일 메시지를 읽고 사용할 수 있습니다.

-   Outlook 클라이언트용**보호 규칙** - 관리자가 지정된 받는 사람의 메일 메시지에 보호 템플릿 및 옵션을 자동으로 적용하도록 구성하는 규칙입니다. 예를 들어 법률 자문 부서로 전송하는 내부 메일은 법률 자문 부서 구성원만 읽을 수 있으며 전달할 수 없도록 구성할 수 있습니다. 사용자는 메일 메시지를 보내기 전에 메시지에 적용되는 보호를 확인할 수 있으며 기본적으로 보호가 필요하지 않다고 판단되면 제거할 수 있습니다. 메일은 전송되기 전에 암호화됩니다. 자세한 내용은 Exchange 라이브러리에서 [Outlook 보호 규칙](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) 및 [Outlook 보호 규칙 만들기](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx)를 참조하세요.

-   **Mail flow rules**(메일 흐름 규칙) - 관리자가 메일 메시지에 보호 템플릿 또는 옵션을 자동으로 적용하도록 구성하는 규칙입니다. 이러한 규칙은 보낸 사람, 받는 사람, 메시지 제목 및 콘텐츠 등의 속성을 기반으로 합니다. 이러한 규칙은 보호 규칙 개념과 유사하지만, 클라이언트가 아닌 Exchange 서비스에서 보호를 설정하므로 사용자가 보호를 제거할 수 없습니다. 서비스가 보호를 설정하므로 사용자가 사용하는 장치나 운영 체제는 관계가 없습니다. 자세한 내용은 [Exchange Online의 메일 흐름 규칙(전송 규칙)](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)을 참조하고 Exchange 온-프레미스의 경우는 [전송 보호 규칙 만들기](https://technet.microsoft.com/library/dd302432.aspx)를 참조하세요.

-   **DLP(데이터 손실 방지) 정책** - 기밀 또는 중요 콘텐츠의 데이터 손실을 방지하기 위해 메일 메시지를 필터링하고 여러 작업을 수행하는 조건 집합이 포함된 정책입니다. 지정할 수 있는 작업 중 하나는 보호 템플릿 또는 옵션 중 하나를 지정하여 암호화를 보호로 적용하는 것입니다. 중요한 데이터가 검색되면 정책 팁을 사용하여 보호를 적용해야 할 수 있다는 알림을 사용자에게 표시할 수 있습니다. 자세한 내용은 Exchange Online 설명서에서 [데이터 손실 방지](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)를 참조하세요.

-   **Office 365 메시지 암호화** - 보호된 메일 메시지와 보호된 Office 문서를 어떠한 장치에서든지 원하는 메일 주소에 첨부 파일로 보내도록 지원합니다. Azure AD를 사용하지 않는 사용자 계정의 경우 웹 환경에서 소셜 ID 공급자 또는 일회성 암호를 지원합니다. 자세한 내용은 Office 365 설명서에서 [Azure Information Protection을 기반으로 구축된 새로운 Office 365 메시지 암호화 기능 설정](/office365/securitycompliance/set-up-new-message-encryption-capabilities)을 참조하세요. 이 구성과 관련된 추가 정보를 찾으려면 [Office 365 메시지 암호화](https://docs.microsoft.com/office365/securitycompliance/ome)를 참조하세요.

Exchange 온-프레미스를 사용하면 Azure Rights Management 커넥터를 배포하여 Azure Rights Management 서비스와 IRM 기능을 사용할 수 있습니다. 이 커넥터는 온-프레미스 서버와 Azure Rights Management 서비스 사이에서 릴레이 역할을 합니다.

보호 템플릿에 대한 자세한 내용은 [Azure Information Protection의 템플릿 구성 및 관리](configure-policy-templates.md)를 참조하세요.

메일을 보호하는 데 사용할 수 있는 메일 옵션에 대한 자세한 내용은 [메일에 대한 전달 금지 옵션](configure-usage-rights.md#do-not-forward-option-for-emails) 및 [메일에 대한 암호화 전용 옵션](configure-usage-rights.md#encrypt-only-option-for-emails)을 참조하세요.

메일을 보호하기 위해 Exchange를 구성할 준비가 된 경우:

- Exchange Online은 [Exchange Online: IRM 구성](configure-office365.md#exchange-online-irm-configuration)을 참조하세요.

- Exchange 온-프레미스에 관한 내용은 [Azure Rights Management 커넥터 배포](deploy-rms-connector.md)를 참조하세요.


## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online 및 SharePoint Server

SharePoint Online 또는 SharePoint Server를 사용할 때 SharePoint IRM(정보 권한 관리) 기능을 사용하여 문서를 보호할 수 있습니다. 이 기능을 사용하면 관리자가 목록 또는 라이브러리를 보호할 수 있습니다. 그러므로 사용자가 문서를 체크 아웃할 때 다운로드된 파일이 보호된 상태이기 때문에 지정한 정보 보호 정책에 따라 권한이 있는 사용자만 파일을 확인 및 사용할 수 있습니다. 예를 들어 파일을 읽기 전용으로 지정하고, 텍스트를 복사할 수 없도록 설정하고, 로컬 복사본 저장 및 파일 인쇄를 금지할 수 있습니다.

Word, PowerPoint, Excel 및 PDF 문서는 이 SharePoint IRM 보호를 지원합니다. 기본적으로 보호는 문서를 다운로드하는 사람에게 제한됩니다. **그룹 보호 허용**이라는 구성 옵션을 사용하여 이 기본값을 변경할 수 있습니다. 이 옵션을 선택하면 지정하는 그룹으로 보호가 확장됩니다. 예를 들어 라이브러리의 문서를 편집할 권한이 있는 그룹을 지정하여 문서를 다운로드한 사용자와 관계없이 동일한 사용자 그룹이 SharePoint 외부의 문서를 편집할 수 있습니다. 또는 SharePoint에서 권한이 부여되지 않은 그룹을 지정할 수 있지만, 이러한 그룹의 사용자는 SharePoint 외부에서 문서에 액세스해야 합니다. 

SharePoint 목록 및 라이브러리의 경우 항상 최종 사용자가 아닌 관리자가 이 보호 기능을 구성합니다. 사용 권한은 사이트 수준에서 설정하며, 이러한 사용 권한은 기본적으로 해당 사이트에 있는 모든 목록 또는 라이브러리에 상속됩니다. SharePoint Online을 사용하면 사용자는 IRM 보호를 위해 비즈니스 라이브러리용 OneDrive를 구성할 수도 있습니다.

보다 세부적으로 제어하려면 부모로부터 사용 권한의 상속을 중단하도록 해당 사이트 내에 목록 또는 라이브러리를 구성할 수 있습니다. 그런 후에 해당 수준(목록 또는 라이브러리)에서 IRM 사용 권한을 구성하면 그 사용 권한을 "고유 사용 권한"이라고 합니다. 그러나 사용 권한은 항상 컨테이너 수준에서 설정되며, 개별 파일에서 사용 권한을 설정할 수는 없습니다. 

이렇게 하려면 먼저 SharePoint에 대해 IRM 서비스를 사용하도록 설정해야 합니다. 그런 다음 라이브러리의 IRM 사용 권한을 지정합니다. SharePoint Online 및 비즈니스용 OneDrive의 경우, 사용자는 비즈니스 라이브러리용 OneDrive에 대해 IRM 사용 권한도 지정할 수 있습니다. SharePoint는 템플릿에서 지정할 수 있는 몇 가지 설정과 일치하며 선택 가능한 SharePoint 구성 설정이 있더라도 권한 정책 템플릿을 사용하지 않습니다.

SharePoint Server를 사용하는 경우에 Azure Rights Management 커넥터를 배포하여 이 IRM 보호 기능을 사용할 수 있습니다. 이 커넥터는 온-프레미스 서버와 Rights Management 클라우드 서비스 사이에서 릴레이 역할을 합니다. 자세한 내용은 [Azure Rights Management 커넥터 배포](deploy-rms-connector.md)를 참조하세요.

> [!NOTE]
> 현재 SharePoint IRM을 사용하는 경우 다음과 같이 몇 가지 제한 사항이 있습니다.
> 
> - 기본값 또는 Azure Portal에서 관리하는 사용자 지정 보호 템플릿을 사용할 수 없습니다. 
> 
> - 보호된 PDF 파일에 대한 .ppdf 파일 이름 확장명을 가진 파일은 지원되지 않습니다. 보호된 PDF 문서를 보는 방법에 대한 자세한 내용은 [Microsoft Information Protection에 대한 보호된 PDF reader](./rms-client/protected-pdf-readers.md)를 참조하세요.
> 
> - 두 명 이상의 사용자가 동시에 문서를 편집하는 경우 공동 작성이 지원되지 않습니다. IRM으로 보호되는 라이브러리의 문서를 편집하려면 먼저 문서를 체크 아웃하여 다운로드한 후 Office 응용 프로그램에서 편집해야 합니다. 따라서 한 번에 한 사용자만 문서를 편집할 수 있습니다.

IRM으로 보호되지 않는 라이브러리의 경우 SharePoint 또는 OneDrive에 업로드하는 파일을 보호하면 이 파일로 작동하지 않는 것은 다음과 같습니다: 공동 작성, Office Online, 검색, 문서 미리 보기, 썸네일, eDiscovery 및 DLP(데이터 손실 방지).

SharePoint IRM 보호를 사용할 때, Azure Rights Management 서비스는 문서를 SharePoint에서 처음 만들거나 라이브러리로 업로드할 때가 아니라 SharePoint에서 다운로드할 때 문서에 사용 제한 및 데이터 암호화를 적용합니다. 문서가 다운로드되기 전에 보호하는 방법에 대한 자세한 내용은 SharePoint 설명서에서 [비즈니스용 OneDrive 및 SharePoint Online의 데이터 암호화](https://technet.microsoft.com/library/dn905447.aspx) 를 참조하세요.

더 이상 새 정보는 아니지만 Office 365 블로그의 다음 게시물에는 유용할 수 있는 몇 가지 추가 정보가 있습니다: [SharePoint와 SharePoint Online의 정보 권한 관리의 새로운 기능](https://www.microsoft.com/en-us/microsoft-365/blog/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

IRM에 대해 SharePoint를 구성할 준비가 된 경우:

- SharePoint Online은 [SharePoint Online 및 비즈니스용 OneDrive: IRM 구성](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)을 참조하세요.

- Sharepoint Server에 관한 내용은 [Azure Rights Management 커넥터 배포](deploy-rms-connector.md)를 참조하세요.


## <a name="next-steps"></a>다음 단계

Office 365를 사용하는 경우 Office 365의 파일 보호에 대해 권장되는 기능을 제공하는 [Office 365의 파일 보호 솔루션](/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365fileprotect)을 검토하는 데 관심이 있을 수 있습니다.

다른 응용 프로그램과 서비스에서 Azure Information Protection의 Azure Rights Management 서비스를 지원하는 방식을 보려면 [응용 프로그램이 Azure Rights Management 서비스를 지원하는 방식](applications-support.md)을 참조하세요.

이러한 응용 프로그램 및 서비스의 구성을 포함한 배포를 시작할 준비가 되면 [Azure Information Protection 배포 로드맵](deployment-roadmap.md)을 참조하세요.
