---
title: Azure Information Protection용 클라이언트
description: Microsoft Azure Information Protection은 조직 데이터를 보호하는 데 사용할 수 있는 클라이언트-서버 솔루션을 제공합니다. 클라이언트(Azure Information Protection 클라이언트 또는 Rights Management 클라이언트)는 컴퓨터와 모바일 장치에서 실행하는 응용 프로그램과 통합됩니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/19/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9026560849d04939799a013d28d6d6d4d38ae442
ms.sourcegitcommit: 8d854ee417d9af1a85e7d4ecb3807a69a43b0313
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52177197"
---
# <a name="the-client-side-of-azure-information-protection"></a>Azure Information Protection의 클라이언트 측면

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection은 조직의 문서와 전자 메일을 보호하는 데 사용할 수 있는 클라이언트-서버 솔루션을 제공합니다.

- 클라이언트는 Azure Information Protection 클라이언트 또는 Rights Management 클라이언트일 수 있으며, 컴퓨터와 모바일 장치에서 실행하는 응용 프로그램과 통합됩니다. 

- 서비스는 클라우드(정보 보호를 위해 Azure Rights Management 서비스를 사용하는 Azure Information Protection) 또는 온-프레미스(Active Directory Rights Management Services)에서 제공됩니다. 

Azure Information Protection 클라이언트는 보호 외에도 분류 및 레이블 지정 기능을 지원합니다. 이 클라이언트는 Office 응용 프로그램과 통합되며 별도로 설치해야 합니다.

RMS(Rights Management) 클라이언트는 Office 응용 프로그램, Azure Information Protection 클라이언트, 소프트웨어 공급업체의 RMS 지원 응용 프로그램 등의 일부 응용 프로그램과 함께 자동으로 설치됩니다. 그러나 독립적으로 설치하여, 기간 업무 응용 프로그램에 Rights Management 보호를 통합하려는 개발자 등의 시나리오를 지원할 수도 있습니다.

조직의 데이터 보호를 위해 Azure Information Protection 및 Active Directory Rights Management Services와 함께 사용할 수 있는 이러한 클라이언트를 배포하고 사용하는 방법에 대한 자세한 내용은 다음 문서를 참조하세요.

- [Azure Information Protection 클라이언트](AIP-client.md)

- [RMS 클라이언트 배포 참고 사항](client-deployment-notes.md)

- [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](configure-fci.md)

- [Windows용 Rights Management 공유 응용 프로그램](sharing-app-windows.md)

Windows용 Rights Management 공유 응용 프로그램 및 RMS 보호 도구는 이제 Azure Information Protection 클라이언트로 대체됩니다. 


## <a name="see-also"></a>참고 항목
[Azure Information Protection 및 AD RMS 비교](../compare-on-premise.md)
