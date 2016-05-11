---
# required metadata

title: API 보안 모드 설정 | Azure RMS
description: 파일 API 응용 프로그램에서 실행하는 보안 모드를 선택합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b3acfcd5-1af5-4f3a-912b-962198c59103

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# API 보안 모드 설정

[**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) 함수를 사용하여 파일 API 응용 프로그램이 실행되는 보안 모드를 선택할 수 있습니다.

서버 모드에서 실행되도록 응용 프로그램을 초기화하려면 [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) 함수를 호출하고 보안 모드를 [**IPC\_API\_MODE\_SERVER**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER)로 설정합니다. 기본적으로 응용 프로그램은 클라이언트 모드인 **IPC\_API\_MODE\_CLIENT**에서 실행됩니다.

서버 모드에 대한 자세한 내용은 [응용 프로그램 종류](application-types.md)를 참조하세요.

**중요** 다른 권한 관리 서비스 SDK 2.1 함수를 호출하기 전에 보안 모드를 설정해야 합니다. 보안 모드를 설정한 후에는 현재 프로세스에 대해 변경할 수 없습니다.

 

### 관련 항목

* [응용 프로그램 종류](application-types.md)
* [개발자 개념](ad-rms-concepts-nav.md)
* [**API 모드 값**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
 

 





<!--HONumber=Apr16_HO3-->


