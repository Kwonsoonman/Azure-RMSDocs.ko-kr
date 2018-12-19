---
title: Azure RMS 데이터 보호를 위한 서버 지원 - AIP
description: Rights Management 커넥터를 통해 Azure Information Protection의 Azure Rights Management 서비스를 사용할 수 있는 온-프레미스 서버 제품을 식별합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1afe0dcde0ce73fb727da1b1efd9d262d954ae66
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305270"
---
# <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Azure Rights Management 데이터 보호를 지원하는 온-프레미스 서버

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Rights Management 커넥터를 사용할 때 Azure Information Protection에서 지원되는 온-프레미스 서버 제품은 다음과 같습니다. 이 커넥터는 Azure Information Protection에서 Office 문서 및 메일을 보호하는 데 사용되는 온-프레미스 서버와 Azure Rights Management 서비스 간의 통신 인터페이스(릴레이) 역할을 합니다. 

이 커넥터를 사용하려면 Active Directory 포리스트와 Azure Active Directory 간의 디렉터리 동기화를 구성해야 합니다.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Windows Server를 실행하고 FCI(파일 분류 인프라)를 사용하는 파일 서버**:

    -   Windows Server 2016

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Windows Server 2008 R2를 실행하는 파일 서버에는 Rights Management 보호를 적용하는 기본 제공 파일 관리 작업 동작이 없으므로 이 시나리오에는 Rights Management 커넥터를 사용할 수 없습니다. 그러나 Azure RMS를 사용하여 파일을 보호할 수 있는 사용자 지정 파일 관리 작업(실행 파일 또는 스크립트를 실행)을 구성하는 경우 이러한 운영 체제에서 파일 분류 인프라 및 Azure RMS를 사용할 수 있습니다. [AzureInformationProtection cmdlet](/powershell/azureinformationprotection/vlatest/aip)을 사용하는 Windows PowerShell 스크립트를 예로 들 수 있습니다.
    > 
    > 또한 이러한 cmdlet이 모든 파일 형식을 보호할 수 있다는 혜택을 가진 이후 버전의 Windows Server를 실행하는 서버로 이러한 cmdlet를 사용할 수 있습니다. RMS 커넥터는 Office 파일만을 보호합니다. 방법 지침은 [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](./rms-client/configure-fci.md)를 참조하세요.

Rights Management 커넥터는 Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2에서 지원됩니다.

이러한 온-프레미스 서버에 대해 Rights Management 커넥터를 구성하는 방법에 대한 자세한 내용은 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계
기타 요구 사항을 확인하려면 [Azure 권한 관리 요구 사항](requirements.md)을 참조하세요.
