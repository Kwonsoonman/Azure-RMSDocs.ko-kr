---
title: Azure Rights Management용 응용 프로그램 구성 - AIP
description: Azure Information Protection에 대한 Azure Rights Management 보호 서비스를 지원하도록 응용 프로그램 및 서비스를 구성하는 관리자에 대한 지침입니다. Word 2013, Word 2010등의 Office 응용 프로그램과 Exchange Online(전송 규칙, 데이터 손실 방지, 전달 금지, 메시지 암호화) 및 SharePoint Online(보호된 라이브러리) 등의 서비스를 예로 들 수 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3e4a84fc212c1e998556eec88a896d33d7615f05
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39489996"
---
# <a name="configuring-applications-for-azure-rights-management"></a>Azure 권한 관리에 대해 응용 프로그램 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> 이 정보는 Azure Information Protection을 배포한 IT 관리자 및 컨설턴트를 대상으로 합니다. 특정 응용 프로그램용 Rights Management 기능을 사용하는 방법이나 권한으로 보호된 파일을 여는 방법에 대한 정보와 사용자 도움말을 원하는 경우 응용 프로그램을 함께 제공되는 지침 및 도움말을 사용하세요.
>
> 예를 들어 Office 응용 프로그램의 경우 도움말 아이콘을 클릭하고 **Rights Management** 또는 **IRM**과 같은 검색 용어를 입력합니다. Windows용 Azure Information Protection 클라이언트의 경우 [Azure Information Protection 클라이언트 사용자 가이드](./rms-client/client-user-guide.md)를 참조하세요.

조직에 대해 Azure Information Protection을 배포한 경우 다음 정보를 사용하여 응용 프로그램, Azure Information Protection 클라이언트 및 서비스를 구성하세요. Word 2016, Word 2013 및 Word 2010과 같은 Office 응용 프로그램을 예로 들 수 있습니다. 또한 Exchange Online(전송 규칙, 데이터 손실 방지, 전달 금지, 메시지 암호화) 및 SharePoint Online(보호된 라이브러리) 등의 서비스도 여기에 해당합니다. 이러한 응용 프로그램과 서비스가 Azure Information Protection의 데이터 보호 서비스를 지원하는 방식에 대한 자세한 내용은 [응용 프로그램이 Azure Rights Management 서비스를 지원하는 방식](applications-support.md)을 참조하세요.

> [!IMPORTANT]
> 지원되는 버전 및 기타 요구 사항에 대한 자세한 내용은 [Azure 권한 관리에 대한 요구 사항](requirements.md)을 참조하세요.

-   [Office 365: 클라이언트 및 온라인 서비스 구성](configure-office365.md)

    -   [Exchange Online: IRM 구성](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online 및 비즈니스용 OneDrive: IRM 구성](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Office 응용 프로그램: 클라이언트 구성](configure-office-apps.md)

    -   [Office 2016 및 Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office-2010)

-   [Azure Information Protection 클라이언트: 클라이언트 설치 및 구성](configure-sharing-app.md)

-   [Rights Management 공유 응용 프로그램: 클라이언트 설치 및 구성](configure-sharing-app.md)


온-프레미스 서버(예: Exchange Server 및 SharePoint Server)를 구성하려면 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)를 참조하세요.

이러한 응용 프로그램 및 서비스 외에도 Rights Management API를 지원하는 다른 응용 프로그램이 있습니다. 이 범주에는 Rights Management SDK를 사용하여 내부에서 작성한 LOB(기간 업무) 응용 프로그램과 소프트웨어 공급업체에서 Rights Management SDK를 사용하여 작성한 응용 프로그램이 포함됩니다. 이러한 응용 프로그램의 경우 응용 프로그램과 함께 제공된 지침을 따르세요.

## <a name="next-steps"></a>다음 단계
Azure Rights Management 서비스를 지원하도록 응용 프로그램을 구성한 후에는 [Azure Information Protection 배포 로드맵](deployment-roadmap.md)을 사용하여 사용자와 관리자에게 Azure Information Protection을 배포하기 전에 수행할 수 있는 다른 구성 단계가 있는지 확인합니다. 없으면 다음과 같은 운영 정보가 유용할 수도 있습니다.

- [Azure Rights Management 서비스 확인](verify.md)

- [사용자가 Azure Rights Management 서비스를 사용하여 파일을 보호할 수 있도록 지원](help-users.md)

- [Azure Rights Management 서비스 로깅 및 분석](log-analyze-usage.md)

- [Azure Information Protection 테넌트 키에 대한 작업](operations-tenant-key.md)


