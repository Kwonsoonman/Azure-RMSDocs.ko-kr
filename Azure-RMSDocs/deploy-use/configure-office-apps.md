---
title: "Office 앱, 클라이언트 구성 - AIP"
description: "관리자가 Azure Information Protection의 Azure Rights Management 서비스에서 작동하도록 Office 앱을 구성하는 방법 및 지침을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 430f390bef496b5e297ae25a03531da42954121d
ms.lasthandoff: 02/24/2017


---

# <a name="office-apps-configuration-for-clients"></a>Office 앱: 클라이언트 구성

>*적용 대상: Azure Information Protection, Office 365*


이 정보를 사용하여 최종 사용자가 사용하는 Office 앱이 Azure Information Protection의 Azure Rights Management 서비스와 함께 작동하기 위해 수행해야 하는 작업을 확인할 수 있습니다.

## <a name="office-2016-and-office-2013"></a>Office 2016 및 Office 2013
이러한 이후 버전의 Office는 기본적으로 Azure Rights Management 서비스를 지원하므로 Word, Excel, PowerPoint, Outlook 및 Outlook Web App과 같은 응용 프로그램에 대해 IRM(정보 권한 관리) 기능을 지원하기 위해 클라이언트 컴퓨터를 구성할 필요가 없습니다. 사용자는 [!INCLUDE[o365_1](../includes/o365_1_md.md)] 자격 증명을 사용하여 Office 응용 프로그램에 로그인하기만 하면 되며, 로그인하면 파일과 메일을 보호하고 다른 사용자가 보호한 파일과 메일을 사용할 수 있습니다.

그러나 사용자가 Office 추가 기능 및 추가 파일 형식 지원에 따른 이점을 얻을 수 있도록 Azure Information Protection 클라이언트로 이러한 응용 프로그램을 보완하는 것이 좋습니다. 자세한 내용은 [Azure Information Protection 클라이언트: 클라이언트 설치 및 구성](configure-client.md)을 참조하세요.

## <a name="office-2010"></a>Office 2010
클라이언트 컴퓨터가 Azure Rights Management 서비스를 Office 2010과 함께 사용하도록 하려면 클라이언트 컴퓨터에 Azure Information Protection 클라이언트 또는 Windows용 Rights Management 공유 응용 프로그램을 설치해야 합니다. 사용자가 [!INCLUDE[o365_1](../includes/o365_1_md.md)] 자격 증명을 사용하여 로그인하는 것 외에 추가 구성은 필요하지 않으며, 로그인하면 파일을 보호하고 다른 사용자가 보호한 파일을 사용할 수 있습니다.

Azure Information Protection 클라이언트에 대한 자세한 내용은 [Azure Information Protection 클라이언트: 클라이언트 설치 및 구성](configure-client.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

