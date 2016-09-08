---
title: "응용 프로그램이 Azure 권한 관리를 지원하는 방식 | Azure RMS"
description: "다음 정보를 참조하여 Office 응용 프로그램, Word, Excel, PowerPoint, Outlook 등의 자주 사용하는 최종 사용자 응용 프로그램과 Exchange, SharePoint 등의 서비스에서 Microsoft Azure 권한 관리를 통해 조직 데이터를 보호하는 방식을 파악할 수 있습니다."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: df66b53238acecd4173b7d1bc57a611c403ec256


---

# 응용 프로그램이 Azure 권한 관리를 지원하는 방식

>*적용 대상: Azure 권한 관리, Office 365*

다음 정보를 참조하여 Office 응용 프로그램, Word, Excel, PowerPoint, Outlook 등의 자주 사용하는 최종 사용자 응용 프로그램과 Exchange, SharePoint 등의 서비스에서 Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 통해 조직 데이터를 보호하는 방식을 파악할 수 있습니다. 
> [!NOTE]
> [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)](Azure RMS)에서 지원하는 응용 프로그램과 버전을 확인하려면 [Azure 권한 관리 요구 사항](../get-started/requirements-azure-rms.md)을 참조하세요.

구성된 정책에 따라 정보 보호가 자동으로 적용되는 경우도 있습니다. SharePoint 라이브러리, 분류된 파일, Exchange 전송 규칙 등을 예로 들 수 있습니다. 사용자가 템플릿이나 특정 옵션을 선택하여 응용 프로그램에서 정보 보호를 직접 적용해야 하는 경우도 있습니다. 사용자가 메일로 파일을 공유하거나 조직 외부 사용자 또는 선택한 사용자에 대해 액세스 또는 사용을 제한하여 내부에서 파일을 보호하는 경우를 예로 들 수 있습니다.

정책을 구성하는 관리자와 사용자는 템플릿을 통해 보다 간편하게 올바른 수준의 보호를 적용하고 조직 내 사용자에 대해 액세스를 제한할 수 있습니다. [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]에서는 기본 템플릿 두 개가 제공되지만 개별 옵션을 지정해야 하는 경우 시간을 단축하기 위해 사용자 지정 템플릿을 만들 수도 있습니다. 자세한 내용은 [Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

사용자가 정보 보호를 직접 적용해야 하는 경우에는 적용 방법과 시기에 대한 지침을 제공해야 합니다. 사용자가 사용 중인 응용 프로그램 및 버전과 해당 사용 방법에 따라 구체적인 지침을 제공해야 하며, 업무상 정보 보호를 적용하는 것이 적절한 시기와 적용 방법에 대한 지침도 제공해야 합니다. 자세한 내용은 [사용자가 Azure 권한 관리를 사용하여 파일을 보호할 수 있도록 지원](../deploy-use/help-users.md)을 참조하세요.

이러한 응용 프로그램을 Azure RMS에 대해 구성하는 방법에 대한 자세한 내용은 [Azure 권한 관리에 대해 응용 프로그램 구성](../deploy-use/configure-applications.md)을 참조하세요.

> [!TIP]
> Azure RMS를 사용하는 응용 프로그램의 예와 스크린샷을 보려면 [Azure RMS 실행: 관리자와 사용자에게 표시되는 내용](what-admins-users-see.md)을 참조하세요.

검색 서비스는 여러 방법으로 Rights Management를 통합할 수 있습니다. 예를 들면 다음과 같습니다. 

- Exchange Online 및 Exchange Server에서는 사용자의 RMS로 보호된 메일이 자동으로 검색 결과에 표시되도록 서비스 측 인덱싱을 사용합니다. 

- SharePoint Online 및 SharePoint Server에서는 다운로드 시에만 파일에 RMS 보호를 적용합니다. 즉, SharePoint의 인덱싱 및 검색 결과는 이 문서 보호 솔루션의 영향을 받지 않습니다. 그러나 SharePoint에 저장하지만 검색 결과에 반환되어서는 안 되는 문서가 있으면 SharePoint에 업로드하기 전에 해당 파일을 RMS로 보호합니다.

- Windows 데스크톱 검색은 장치의 여러 사용자 간에 공유된 인덱스를 사용하므로 보호된 문서의 데이터를 안전하게 유지하기 위해 RMS로 보호된 파일을 인덱싱하지 않습니다. 즉, 검색 결과에 보호하는 파일이 포함되지 않더라도 중요한 데이터를 포함하는 파일이 PC에 로그인하거나 연결하는 다른 사용자를 위한 검색 결과에 표시되지 않는다는 것을 알 수 있습니다. 



## 다음 단계

다음 항목이 각각 Azure RMS를 지원하는 방식에 대한 자세한 정보:

-   [Windows 및 모바일 플랫폼용 RMS 공유 응용 프로그램](sharing-app-support.md)

-   [Office 응용 프로그램 및 서비스](office-apps-services-support.md)

-   [Windows Server를 실행하고 FCI(파일 분류 인프라)를 사용하는 파일 서버](file-server-support.md)

-   [RMS API를 지원하는 기타 응용 프로그램](api-support.md)




<!--HONumber=Aug16_HO4-->


