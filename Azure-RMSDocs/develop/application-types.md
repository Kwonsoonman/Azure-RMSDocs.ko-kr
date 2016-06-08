---
# required metadata

title: 응용 프로그램 종류 | Azure RMS
description: 이 항목에서는 권한 사용 응용 프로그램으로 만들도록 선택할 수 있는 응용 프로그램 종류에 대해 설명합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
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
# 응용 프로그램 종류


이 항목에서는 권한 사용 응용 프로그램으로 만들도록 선택할 수 있는 응용 프로그램 종류에 대해 설명합니다.

권한 관리 서비스 SDK 2.1에서 현재 지원되는 응용 프로그램 종류는 다음과 같습니다.

## 간단한 응용 프로그램

간단한 응용 프로그램은 제공된 파일을 암호화하도록 작성된 명령줄 도구일 수 있습니다. 간단한 권한 사용 응용 프로그램의 예는 [IPCHelloWorld - 예제 응용 프로그램](how-to-build-your-first-application.md)을 참조하세요.

### 서버 모드 응용 프로그램


*서버 모드*는 RMS 보호된 콘텐츠를 사용, 보호 또는 처리하는 비대화형 응용 프로그램에 사용됩니다. 예를 들어 파일 서버에서 서비스로 실행되며 중요한 문서를 자동으로 보호하는 *데이터 손실 방지* 응용 프로그램이 있습니다. 이 응용 프로그램 종류의 예는 [IpcDlp 샘플](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)을 참조하세요.

응용 프로그램이 *서버 모드*를 사용하는 경우 RMS 서버에 자동으로 인증해야 합니다. *클라이언트 모드*와 달리 자동으로 인증하지 못하면 RMS SDK 2.1에서 자격 증명 프롬프트가 열리지 않습니다. 또한 *서버 모드*에서 실행하는 경우에는 응용 프로그램 매니페스트가 필요하지 않습니다.

API 보안 모드 설정에 대한 자세한 내용은 [API 보안 모드 설정](setting-the-api-security-mode-api-mode.md)을 참조하세요.

### 리치 클라이언트 응용 프로그램

리치 클라이언트 응용 프로그램을 사용하면 GUI(그래픽 사용자 인터페이스)를 통해 데이터를 보고 조작할 수 있습니다. 대체로 이 GUI에 표시되는 데이터는 중요하며 도난 또는 실수에 의한 노출에 민감합니다. 정보 보호 지원은 일반적으로 기존 시나리오를 개선하지만 응용 프로그램 개발의 주요 동기 부여는 아닙니다.

리치 클라이언트 응용 프로그램과 함께 RMS SDK 2.1을 사용하면 다음가 같은 작업에 도움이 됩니다.

-   이 데이터가 항상 암호화되도록 합니다.

-   사용자가 보호되지 않는 형식으로 데이터를 추출할 수 없도록 합니다(예: 클립보드를 사용한 복사 및 붙여넣기 차단).

Microsoft 메모장은 간단한 리치 클라이언트 응용 프로그램입니다. Microsoft Office는 좀더 복잡한 리치 클라이언트 응용 프로그램입니다.

응용 프로그램 보호에 대한 자세한 내용은 [사용 제한 이해](understanding-usage-restrictions.md)를 참조하세요.

## 관련 항목

* [개발자 개념](ad-rms-concepts-nav.md)
* [IpcDlp 샘플](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
* [IPCHelloWorld - 예제 응용 프로그램](how-to-build-your-first-application.md)
* [API 보안 모드 설정](setting-the-api-security-mode-api-mode.md)
* [사용 제한 이해](understanding-usage-restrictions.md)
 

 





<!--HONumber=Jun16_HO1-->


