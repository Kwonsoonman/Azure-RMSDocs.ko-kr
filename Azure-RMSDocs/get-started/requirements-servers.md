---
title: "Azure RMS 요구 사항&#58; Azure 권한 관리를 지원하는 온-프레미스 서버 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: 7e718d8178dd7c4b18ea7a19eb3165ee06dc4b36


---


# Azure RMS 요구 사항: Azure RMS를 지원하는 온-프레미스 서버

*적용 대상: Azure 권한 관리, Office 365*

다음 온-프레미스 서버 제품은 Azure RMS 커넥터를 사용할 경우 Azure RMS에서 지원되며, Azure RMS 커넥터는 온-프레미스 서버와 Azure RMS 사이에서 통신 인터페이스(릴레이) 역할을 합니다. 또한 이 구성을 사용하려면 Active Directory 포리스트와 Azure Active Directory 간의 디렉터리 동기화를 구성해야 합니다.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Windows Server를 실행하고 FCI(파일 분류 인프라)를 사용하는 파일 서버**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Windows Server 2008 R2를 실행하는 파일 서버에는 RMS 보호를 적용하는 기본 제공 파일 관리 작업 동작이 없으므로 이 시나리오에는 RMS 커넥터를 사용할 수 없습니다. 그러나 Azure RMS를 사용하여 파일을 보호할 수 있는 사용자 지정 파일 관리 작업(실행 파일 또는 스크립트를 실행)을 구성하는 경우 이러한 운영 체제에서 파일 분류 인프라 및 Azure RMS를 사용할 수 있습니다. 예를 들어 [RMS 보호 cmdlet](https://msdn.microsoft.com/library/azure/mt433195.aspx)을 사용하는 Windows PowerShell 스크립트입니다.
    > 
    > 또한 이러한 cmdlet이 모든 파일 형식을 보호할 수 있다는 혜택을 가진 이후 버전의 Windows Server를 실행하는 서버로 이러한 cmdlet를 사용할 수 있습니다. RMS 커넥터는 Office 파일만을 보호합니다. 방법 지침은 [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](../rms-client/configure-fci.md)를 참조하세요.

RMS 커넥터는 Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2에서 지원됩니다.

이러한 온-프레미스 서버에 대해 RMS 커넥터를 구성하는 방법에 대한 자세한 내용은 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.

## 다음 단계
기타 요구 사항을 확인하려면 [Azure 권한 관리 요구 사항](requirements-azure-rms.md)을 참조하세요.



<!--HONumber=Jun16_HO4-->


