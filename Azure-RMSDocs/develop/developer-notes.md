---
# required metadata

title: 개발자 노트 | Azure RMS
description: 이 항목에서는 중요한 여러 개발 시나리오에 대한 특정 지침을 제공합니다. 
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** 이 SDK 콘텐츠는 현재 버전이 아닙니다. 잠시 MSDN에서 [현재 버전](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx)의 설명서를 확인해 주세요. **
# 개발자 노트

이 섹션에서는 중요한 여러 개발 시나리오에 대한 특정 지침을 제공합니다. 이 섹션의 시나리오는 이 릴리스의 권한 관리 서비스 SDK 2.1에만 해당하며, 후속 릴리스에서 변경될 수 있습니다.

- [명시적 소유자 권한 추가](add-explicit-owner-rights.md) - 라이선스를 처음부터 만드는 경우([IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)) 응용 프로그램에서 &quot;소유자&quot; 권한을 명시적으로 추가해야 합니다.
- [일반 오류 조건 및 해결 방법](common-error-conditions-and-solutions.md) - RMS SDK 2.1 개발자 도구를 사용할 때 발생할 수 있는 가장 일반적인 오류 메시지입니다.
- [메일 알림 사용](how-to-enable-email-notification.md) - 메일 알림을 사용하면 누군가가 보호된 콘텐츠에 액세스할 경우 보호된 콘텐츠 소유자가 알림을 받을 수 있습니다.
- [파일 API 구성](file-api-configuration.md) - 레지스트리 설정을 통해 파일 API의 동작을 구성할 수 있습니다.
- [IPCHelloWorld - 예제 응용 프로그램](how-to-build-your-first-application.md) - 이 항목에는 예제 권한 사용 응용 프로그램을 만드는 지침이 포함되어 있습니다.
- [API 보안 모드 설정](setting-the-api-security-mode-api-mode.md) - [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) 함수를 사용하여 파일 API 응용 프로그램이 실행되는 보안 모드를 선택할 수 있습니다.
- [지원되는 파일 형식](supported-file-formats.md) - 파일 API는 네이티브 형식과 Pfile 형식을 지원합니다.
- [콘텐츠 추적](tracking-content.md) - 이 항목에서는 RMS SDK 2.1을 통해 보호된 콘텐츠의 문서 추적을 구현하기 위한 기본 지침을 제공합니다.
- [암호화 작업](working-with-encryption.md) - 이 항목에서는 암호화 패키지에 대해 설명하고 사용과 관련된 몇 가지 코드 조각을 보여 줍니다.

 

## 관련 항목 ##
* [개요](ad-rms-overview.md)
* [사용 방법](how-to-use-msipc.md)
 

 


<!--HONumber=Jun16_HO1-->


