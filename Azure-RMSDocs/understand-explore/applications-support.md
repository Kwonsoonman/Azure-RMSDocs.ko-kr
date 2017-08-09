---
title: "앱에서 AIP의 Azure Rights Management를 지원하는 방식"
description: "Office 응용 프로그램, Word, Excel, PowerPoint, Outlook 등의 자주 사용하는 최종 사용자 응용 프로그램과 Exchange, SharePoint 등의 서비스에서 Azure Information Protection의 Azure Rights Management 서비스를 통해 조직의 문서와 전자 메일을 보호하는 방식을 파악합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6e66ada9f950f7b4cbeac3a98f548afd760e0c7a
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2017
---
# <a name="how-applications-support-the-azure-rights-management-service"></a>응용 프로그램에서 Azure Rights Management 서비스를 지원하는 방법

>*적용 대상: Azure Information Protection, Office 365*

다음 정보를 사용하여 가장 일반적으로 사용하는 최종 사용자 응용 프로그램과 서비스에서 Azure Information Protection의 Azure Rights Management 서비스를 통해 조직의 문서와 메일을 보호하는 방식을 파악할 수 있습니다. 이 응용 프로그램은 Word, Excel, PowerPoint 및 Outlook을 포함합니다. 서비스에는 Exchange 및 SharePoint가 포함됩니다.

> [!NOTE]
> Azure Rights Management 서비스에서 지원하는 응용 프로그램 및 버전을 확인하려면 [Azure Rights Management 데이터 보호를 지원하는 응용 프로그램](../get-started/requirements-applications.md)을 참조하세요.

일부 경우 관리자가 구성하는 정에 따라 Azure Rights Management 서비스가 보호를 자동으로 적용합니다. SharePoint 라이브러리 및 Exchange 전송 규칙 등을 예로 들 수 있습니다. 기타 경우 최종 사용자가 응용 프로그램에서 보호를 직접 적용해야 합니다. 예를 들어 사용자가 보호를 적용하도록 구성된 분류 레이블을 선택하거나 템플릿을 선택하거나 특정 옵션을 선택합니다. 사용자가 적용하는 보호는 사용자가 공유할 파일을 보호하고, 선택된 사용자 또는 조직 외부 사용자에게 액세스 또는 사용을 제한할 때 일반적입니다.

정책을 구성하는 관리자와 사용자는 템플릿을 통해 보다 간편하게 올바른 수준의 보호를 적용하고 조직 내 사용자에 대해 액세스를 제한할 수 있습니다. Azure Rights Management 서비스에서는 기본 템플릿 두 개가 제공되지만 사용자와 관리자가 개별 옵션을 지정해야 하는 경우 시간을 단축하기 위해 사용자 지정 템플릿을 만들 수도 있습니다. 템플릿에 대한 자세한 내용은 [Azure Information Protection 템플릿 구성 및 관리](../deploy-use/configure-policy-templates.md)를 참조하세요.

사용자가 보호를 직접 적용해야 하는 경우에는 적용 방법과 시기에 대한 지침을 제공해야 합니다. 사용하는 응용 프로그램과 버전 및 사용 방식에 특정한 지침을 만듭니다. 사용자가 비즈니스에 적합한 보호를 적용해야 하는 시기와 방법에 대한 지침도 제공합니다. 자세한 내용은 [사용자가 Azure Rights Management 서비스를 사용하여 파일을 보호할 수 있도록 지원](../deploy-use/help-users.md)을 참조하세요.

이러한 응용 프로그램을 Azure Information Protection의 Azure Rights Management 서비스에 대해 구성하는 방법에 대한 자세한 내용은 [Azure Rights Management에 대해 응용 프로그램 구성](../deploy-use/configure-applications.md)을 참조하세요.

검색 서비스는 여러 방법으로 Rights Management를 통합할 수 있습니다. 예를 들면 다음과 같습니다. 

- Exchange Online 및 Exchange Server에서는 사용자의 보호된 메일이 자동으로 검색 결과에 표시되도록 서비스 측 인덱싱을 사용합니다. 

- SharePoint Online 및 SharePoint Server는 다운로드 시 파일에만 Rights Management 보호를 적용합니다. 이와 같이 구현하면 이 문서 보호 솔루션이 SharePoint의 인덱싱 및 검색 결과에 영향을 미치지 않습니다. 그러나 SharePoint와 이 문서에 저장하지만 검색 결과에 반환되어서는 안 되는 문서가 있으면 SharePoint에 업로드하기 전에 해당 문서를 보호합니다.

- Windows 데스크톱 검색은 장치의 여러 사용자 간에 공유된 인덱스를 사용하므로 보호된 문서의 데이터를 안전하게 유지하기 위해 보호된 파일을 인덱싱하지 않습니다. 즉, 검색 결과에 보호하는 파일이 포함되지 않더라도 중요한 데이터를 포함하는 파일이 PC에 로그인하거나 PC에 연결하는 다른 사용자를 위한 검색 결과에 표시되지 않는다는 것을 알 수 있습니다. 

## <a name="next-steps"></a>다음 단계

다음 응용 프로그램과 서비스에서 각각 Azure Rights Management 서비스를 지원하는 방식에 대한 자세한 내용을 알아보세요.

-   [Windows 및 모바일 플랫폼용 RMS 공유 응용 프로그램](sharing-app-support.md)

-   [Office 응용 프로그램 및 서비스](office-apps-services-support.md)

-   [Windows Server를 실행하고 FCI(파일 분류 인프라)를 사용하는 파일 서버](file-server-support.md)

-   [RMS API를 지원하는 기타 응용 프로그램](api-support.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
