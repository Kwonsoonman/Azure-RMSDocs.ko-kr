---
# required metadata

title: Azure 권한 관리에 대해 응용 프로그램 구성 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리에 대해 응용 프로그램 구성
> [!NOTE]
> 이 정보는 Azure Rights Management를 배포한 IT 관리자 및 컨설턴트를 대상으로 합니다. 특정 응용 프로그램용 권한 관리를 사용하는 방법이나 권한으로 보호된 파일을 여는 방법에 대한 정보와 사용자 도움말을 원하는 경우 응용 프로그램을 함께 제공되는 지침 및 도움말을 사용하세요.
>
> 예를 들어 Office 응용 프로그램의 경우 도움말 아이콘을 클릭하고 **Rights Management** 또는 **IRM**과 같은 검색 용어를 입력합니다. Windows용 RMS용 공유 응용 프로그램에 대한 자세한 내용은 [Rights Management 공유 응용 프로그램 사용자 가이드](../rms-client/sharing-app-user-guide.md)를 참조하세요.

조직에 대해 Azure RMS(Azure 권한 관리)가 있는 경우 다음 정보를 사용하여 Azure RMS를 지원하도록 응용 프로그램 및 서비스를 구성하세요. 여기에는 Word 2013 및 Word 2010과 같은 Office 응용 프로그램, Exchange Online(전송 규칙, 데이터 손실 방지, 전달 금지 및 메시지 암호화) 및 SharePoint Online(보호된 라이브러리)과 같은 서비스가 포함됩니다. 이러한 응용 프로그램과 서비스에서 Rights Management를 지원하는 방식에 대한 자세한 내용은 [응용 프로그램이 Azure 권한 관리를 지원하는 방식](../understand-explore/applications-support.md)을 참조하세요.

> [!IMPORTANT]
> 지원되는 버전 및 기타 요구 사항에 대한 자세한 내용은 [Azure 권한 관리에 대한 요구 사항](../get-started/requirements-azure-rms.md)을 참조하세요.

-   [Office 365: 클라이언트 및 온라인 서비스 구성](configure-office365.md)

    -   [Exchange Online: IRM 구성](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online 및 비즈니스용 OneDrive: IRM 구성](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Office 응용 프로그램: 클라이언트 구성](configure-office-apps.md)

    -   [Office 2016 및 Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office-2010)

-   [Rights Management 공유 응용 프로그램: 클라이언트 설치 및 구성](configure-sharing-app.md)

    -   [Windows용 RMS 공유 응용 프로그램: 설치 및 구성](configure-sharing-app.md#the-rms-sharing-application-for-windows-installation-and-configuration)

    -   [모바일 플랫폼용 RMS 공유 응용 프로그램: 설치 및 관리](configure-sharing-app.md#the-rms-sharing-application-for-mobile-platforms-installation-and-management)


온-프레미스 서버(예: Exchange Server 및 SharePoint Server)를 구성하려면 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)를 참조하세요.

> [!TIP]
> Azure RMS를 사용하도록 구성된 응용 프로그램의 개괄적인 예와 스크린샷을 보려면 [Azure RMS 실행: 관리자와 사용자에게 표시되는 내용](../understand-explore/what-admins-users-see.md)을 참조하세요.


이러한 응용 프로그램 및 서비스 외에도 RMS API를 지원하는 다른 응용 프로그램이 있습니다. 이 범주에는 RMS SDK를 사용하여 내부에서 작성한 LOB(기간 업무) 응용 프로그램과 소프트웨어 공급업체에서 RMS SDK를 사용하여 작성한 응용 프로그램이 포함됩니다. 이러한 응용 프로그램의 경우 응용 프로그램과 함께 제공된 지침을 따르세요.

## 다음 단계
Azure 권한 관리를 지원하도록 응용 프로그램을 구성한 후에는 [Azure 권한 관리 배포 로드맵](../plan-design/deployment-roadmap.md)을 사용하여 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 사용자와 관리자에게 배포하기 전에 수행할 수 있는 다른 구성 단계가 있는지 확인합니다. 없으면 다음과 같은 운영 정보가 유용할 수도 있습니다.

- [Azure 권한 관리 확인](verify.md)

- [사용자가 Azure 권한 관리를 사용하여 파일을 보호할 수 있도록 지원](help-users.md)

- [Azure 권한 관리 로깅 및 분석](log-analyze-usage.md)

- [Azure 권한 관리 테넌트 키에 대한 작업](operations-tenant-key.md)




<!--HONumber=Apr16_HO3-->


