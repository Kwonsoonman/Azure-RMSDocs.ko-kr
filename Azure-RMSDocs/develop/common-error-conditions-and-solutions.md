---
# required metadata

title: 일반 오류 조건 및 해결 방법 | Azure RMS
description: 이 항목에는 RMS SDK 2.1 개발자 도구를 사용할 때 발생할 수 있는 가장 일반적인 오류 메시지가 포함되어 있습니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: A5B95EB8-3528-4CFF-86FC-166613A5F4A3
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 일반 오류 조건 및 해결 방법
이 항목에는 권한 관리 서비스 SDK 2.1 개발자 도구를 사용할 때 발생할 수 있는 가장 일반적인 오류 메시지가 포함되어 있습니다. 해당하는 경우 오류를 수정하는 권장 조치도 제공합니다.

**중요** - 오류 조건 처리를 위해 SDK API 호출에 실패하면 즉시 [IpcGetErrorMessageText](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) 호출을 항상 사용하여 오류 특성에 대한 전체 정보를 가져옵니다.

 

## 오류 및 작업 ##
아래 목록에는 오류 상수 목록, 해당 설명 및 오류 조건을 처리하는 제안된 작업이 포함되어 있습니다.

**오류** - *IPCERROR_DEBUGGER_DETECTED* - RMS SDK 2.1에서 디버거를 발견했습니다.

**작업** - 개발자 버전의 RMS SDK 2.1에서는 디버거의 현재 상태를 확인하지 않습니다. 가능하면 이 버전의 RMS SDK 2.1을 사용하여 응용 프로그램을 디버그합니다.
프로덕션 버전의 RMS SDK 2.1을 통해 디버그해야 하는 경우 다음 지침을 따르세요.

다음과 같은 RMS SDK 2.1 함수는 디버거에서 실패하도록 설계되었습니다.
- [IpcGetKey</strong>](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
- [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
- [IpcGetTemplateIssuerList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)

이러한 함수 호출 뒤에 있는 코드를 디버그하려면 프로세스를 중단하고 함수 호출이 완료된 후 디버거를 연결해야 합니다. 이 작업을 수행하는 한 가지 방법은 디버거를 중단하는 ASSERT 문을 사용하는 것입니다. ASSERTE 매크로는 *Crtdbg.h* 헤더에 포함되어 있습니다.
\_ASSERTE에 대한 자세한 내용은 [\_ASSERT, \_ASSERTE 매크로](https://msdn.microsoft.com/en-us/library/ezb1wyez.aspx)를 참조하세요.

**오류** - *IPCERROR_BROKEN_CERT_CHAIN* - 인증서 체인이 일치하지 않습니다.

**작업** - AD RMS 응용 프로그램 매니페스트에 서명하는 데 사용한 키에 따라 올바른 값이 계층 구조 키에 포함되어 있는지 확인합니다.
서명 키 및 관련된 값(**DWORD** 계층 구조)은 다음과 같습니다.
- ISV-1
- 프로덕션 - 0 또는 없음

**오류** - *IPCERROR_MACHINE_CERT_NOT_TRUSTED* - ISV 서명 키로 서명된 응용 프로그램을 사용 중인데 응용 프로그램이 프로덕션 AD RMS 서버와 통신하려고 하거나 그 반대의 경우입니다.

- 개발자 버전의 AD RMS 서버를 사용하는 경우 ISV 서명 키를 사용해서 응용 프로그램에 서명해야 합니다.
- 프로덕션 버전의 AD RMS 서버를 사용하는 경우 프로덕션 서명 키를 사용해서 응용 프로그램에 서명해야 합니다.

**오류** - *IPCERROR_APPLICATION_AUTH_ERROR_MANIFEST* - 응용 프로그램 매니페스트가 잘못되었습니다. 이진 파일(응용 프로그램)을 다시 빌드했으며 매니페스트가 다시 생성되지 않은 경우에 발생할 수 있습니다.

**작업** - 응용 프로그램을 다시 빌드할 때마다 응용 프로그램 매니페스트를 다시 생성해야 합니다.

## 관련 항목 ##
* [개발자 노트](developer-notes.md)
* [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [IpcGetTemplateIssuerList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [\_ASSERT, \_ASSERTE 매크로](https://msdn.microsoft.com/en-us/library/ezb1wyez.aspx)
 

 


<!--HONumber=Apr16_HO4-->


