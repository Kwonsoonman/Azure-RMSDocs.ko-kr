---
# required metadata

title: 이 SDK의 장점 | Azure RMS
description: 이 항목에서는 RMS SDK 2.1이 기존의 Active Directory Rights Management Services SDK보다 어떻게 향상되었는지를 설명합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 622D5C6E-07D5-4C71-A99D-9823C1FE6936
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 이 SDK의 장점
이 항목에서는 권한 사용 응용 프로그램을 만드는 데 필요한 개발자 작업 측면에서 권한 관리 서비스 SDK 2.1이 기존의 [Active Directory Rights Management Services SDK](https://msdn.microsoft.com/library/Cc530379)보다 어떻게 향상되었는지를 설명합니다.

**API 화면** - API 화면이 추상화를 통해 훨씬 축소되어 백 엔드 구현의 많은 세부 사항을 덜어줍니다. RMS SDK의 API 화면에는 84개 함수가 있었지만 RMS SDK 2.1에는 20개의 API 함수만 포함되어 있습니다. 대부분의 응용 프로그램은 이 API 화면의 작은 하위 집합만 사용하면 됩니다.

**시작 시간** - RMS SDK 2.1을 사용하면 단계별 가이드에 따라 중요한 응용 프로그램 리소스와 보호 방법을 식별할 수 있습니다. 반면, RMS SDK에서는 인증서, 형식 및 토폴로지를 자세히 알아야 했으며 다중 스레드를 위한 복잡한 코드를 작성해야 했습니다.

**다중 토폴로지 지원** - RMS SDK 2.1을 사용하면 코드 재작성을 최소화할 수 있습니다. 토폴로지 복잡성을 추상화하여 개발자의 작업을 줄여주므로 응용 프로그램이 모든 토폴로지에서 작동합니다. RMS SDK에서는 지원되는 모든 토폴로지를 이해하고 각 토폴로지에 대한 특정 코드를 작성 및 테스트해야 했습니다.

**미래 보증** - RMS SDK 2.1을 사용하면 권한 사용 코드 재작성을 최소화할 수 있습니다. 응용 프로그램이 모든 RMS 환경에서 작동하며, 업데이트된 핵심 RMS 기능이 릴리스되면 새로운 기능을 자동으로 이용합니다. 반면, AD RMS SDK에서는 새로운 기능을 명시적으로 이용하기 위해 응용 프로그램을 업데이트해야 했습니다.

**중요 알림**  
MSDN 라이브러리에서 기존의 [Active Directory Rights Management Services SDK](https://msdn.microsoft.com/library/Cc530379)에 있던 모든 항목이 이제 다음과 같은 지원 설명으로 시작합니다.

클라이언트가 Msdrm.dll에 노출하는 기능을 활용하는 AD RMS SDK는 Windows Server 2008, Windows Vista, Windows Server 2008 R2, Windows 7, Windows Server 2012 및 Windows 8에서 사용할 수 있습니다. 이후 버전에서는 변경되거나 제공되지 않을 수 있습니다. 클라이언트가 *Msipc.dll*에 노출하는 기능을 활용하는 [Active Directory Rights Management Services SDK 2.1](microsoft-information-protection-and-control-client-portal.md)을 대신 사용합니다.

 

## 관련 항목 ##
* [개요](ad-rms-overview.md)
* [Active Directory Rights Management Services SDK](https://msdn.microsoft.com/library/Cc530379)
* [권한 관리 서비스 SDK 2.1](microsoft-information-protection-and-control-client-portal.md)
 

 


<!--HONumber=Apr16_HO4-->


