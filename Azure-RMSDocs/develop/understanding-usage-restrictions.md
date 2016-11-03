---
title: "사용 제한 이해 | Azure RMS"
description: "모든 RMS 사용 응용 프로그램은 사용 제한을 적용해야 합니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cb33a6c784a9b7efca0780771e764b984b51fedd
ms.openlocfilehash: 3141c4131d83e043e987546900d433e43ee4c946


---

# 사용 제한 이해

모든 RMS 사용 응용 프로그램은 사용 제한을 적용해야 합니다. 사용 제한은 사용자가 작업(예: 문서 인쇄)을 수행하려고 하지만 해당 문서에 대한 RMS 정책에서 이 작업을 수행할 수 있는 권한(예: PRINT 권한)을 부여하지 않을 경우 발생하는 조건입니다.

[IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)함수를 사용하여 문서에 대한 사용자 권한을 쿼리할 수 있습니다.

## 사용 제한 이해

-   표준 RMS 권한 익히기

    응용 프로그램에서 적용할 수 있는 RMS 권한의 전체 집합은 [사용 제한 참조](usage-restriction-reference.md)를 참조하세요.

    사용자 상황과 관련된 응용 프로그램 정의 권한이 표준 RMS 권한보다 높게 만들어질 수도 있습니다.

-   사용 제한 적용 지점 식별

    *사용 제한 적용 지점*은 사용 제한을 적용해야 하는 응용 프로그램 제어 흐름 내의 위치입니다. [사용 제한 참조](usage-restriction-reference.md) 항목에서는 일반적인 적용 지점의 몇 가지 예를 제공합니다.

    사용자 응용 프로그램을 평가하여 적용되는 사용 제한 적용 지점을 확인합니다.

    [사용 제한 참조](usage-restriction-reference.md)에 설명된 모든 적용 지점이 응용 프로그램에 필요한 것은 아닙니다. 예를 들어 응용 프로그램에서 사용자가 콘텐츠를 인쇄하도록 허용하지 않는 경우 **IPC\_GENERIC\_PRINT** 권한을 확인할 필요가 없습니다.

-   각 적용 지점에서 액세스를 검사하도록 코드 업데이트

    특정 권한을 적용하는 방법에 대한 지침은 [사용 제한 참조](usage-restriction-reference.md)를 참조하세요.

## 관련 항목

* [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)
* [사용 제한 참조](usage-restriction-reference.md)
 

 



<!--HONumber=Oct16_HO3-->


