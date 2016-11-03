---
title: "방법: API 보안 모드 설정 | Azure RMS"
description: "파일 API 응용 프로그램에서 실행하는 보안 모드를 선택합니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 77e2dfe7f2afb1e70de658850f83f86e9224aea6
ms.openlocfilehash: 9235fa1c194162689b854493ea31e76c08c40ce7


---

# 방법: API 보안 모드 설정

[IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) 함수를 사용하여 파일 API 응용 프로그램이 실행되는 보안 모드를 선택할 수 있습니다.

*서버 모드*에서 실행되도록 응용 프로그램을 초기화하려면 [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) 함수를 호출하고 보안 모드를 [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx)로 설정합니다. 기본적으로 응용 프로그램은 *클라이언트 모드*인 **IPC\_API\_MODE\_CLIENT**에서 실행됩니다.

*서버 모드*에 대한 자세한 내용은 [응용 프로그램 종류](application-types.md)를 참조하세요.

**중요** 다른 권한 관리 서비스 SDK 2.1 함수를 호출하기 전에 보안 모드를 설정해야 합니다. 보안 모드를 설정한 후에는 현재 프로세스에 대해 변경할 수 없습니다.

## 관련 항목

* [응용 프로그램 종류](application-types.md)
* [API 모드 값](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
 

 



<!--HONumber=Oct16_HO3-->


