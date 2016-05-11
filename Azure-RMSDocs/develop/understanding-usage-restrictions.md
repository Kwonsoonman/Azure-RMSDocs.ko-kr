---
# required metadata

title: 사용 제한 이해 | Azure RMS
description:
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 361bbc29-821f-4577-ace6-0aec799039a9

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿# 사용 제한 이해

모든 RMS 사용 응용 프로그램은 사용 제한을 적용해야 합니다. 사용 제한은 사용자가 작업(예: 문서 인쇄)을 수행하려고 하지만 해당 문서에 대한 RMS 정책에서 이 작업을 수행할 수 있는 권한(예: PRINT 권한)을 부여하지 않을 경우 발생하는 조건입니다.

[**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck) 함수를 사용하여 문서에 대한 사용자 권한을 쿼리할 수 있습니다.

## 사용 제한 이해

-   표준 RMS 권한 익히기

    응용 프로그램에서 적용할 수 있는 RMS 권한의 전체 집합은 [사용 제한 참조](usage-restriction-reference.md)를 참조하세요.

    사용자 상황과 관련된 응용 프로그램 정의 권한이 표준 RMS 권한보다 높게 만들어질 수도 있습니다.

-   사용 제한 적용 지점 식별

    사용 제한 적용 지점은 사용 제한을 적용해야 하는 응용 프로그램 제어 흐름 내의 위치입니다. [사용 제한 참조](usage-restriction-reference.md) 항목에서는 일반적인 적용 지점의 몇 가지 예를 제공합니다.

    사용자 응용 프로그램을 평가하여 적용되는 사용 제한 적용 지점을 확인합니다.

    [사용 제한 참조](usage-restriction-reference.md)에 설명된 모든 적용 지점이 응용 프로그램에 필요한 것은 아닙니다. 예를 들어 응용 프로그램에서 사용자가 콘텐츠를 인쇄하도록 허용하지 않는 경우 **IPC\_GENERIC\_PRINT** 권한을 확인할 필요가 없습니다.

-   각 적용 지점에서 액세스를 검사하도록 코드 업데이트

    특정 권한을 적용하는 방법에 대한 지침은 [사용 제한 참조](usage-restriction-reference.md)를 참조하세요.

### 관련 항목

* [개발자 개념](ad-rms-concepts-nav.md)
* [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck)
* [사용 제한 참조](usage-restriction-reference.md)
 

 





<!--HONumber=Apr16_HO3-->

