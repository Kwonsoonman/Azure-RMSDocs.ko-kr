---
title: "방법: 권한 사용 응용 프로그램 디버그 | Azure RMS"
description: "다음 항목에서는 응용 프로그램을 디버그하고 Windows 이벤트 로그를 사용하는 방법을 보여 줍니다."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 128f472eb69a52bd8a7cf2e8103ee520d83ee92c
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-debug-a-rights-enabled-application"></a>방법: 권한 사용 응용 프로그램 디버그

다음 항목에서는 응용 프로그램을 디버그하고 Windows 이벤트 로그를 사용하는 방법을 보여 줍니다.

## <a name="debugging-your-application"></a>응용 프로그램 디버그

권한 관리 서비스 SDK 2.1에서는 개발자 버전의 런타임에 있는 디버깅 검사 방지 기능을 사용할 수 없습니다.

다음 레지스트리 키를 사용하여 디버그 추적을 켤 수 있습니다. 디버그 추적을 끄려면 값을 0으로 변경합니다. 이 릴리스에서 디버깅에 필요한 추가 작업은 없습니다.


```
HKEY_LOCAL_MACHINE
   SOFTWARE
      Microsoft
         MSIPC
            "Trace" = 00000001
            Data type
            dword
```

### <a name="application-logging-by-using-the-windows-event-log"></a>Windows 이벤트 로그를 사용하는 응용 프로그램 로깅

이벤트 로그의 이름은 "Microsoft-RMS-MSIPC/Debug"입니다. 즉, Windows 이벤트 뷰어에서 로그는 "Application and Services Logs\\Microsoft\\RMS\\MSIPC\\Debug"로 표시됩니다.

**참고** 로그는 기본적으로 사용되며, 세부 정보 표시 수준 3으로 설정되어 있습니다.

 

로깅 기능의 설정을 변경하려면 Windows 이벤트 뷰어의 UI 또는 Windows에 기본 제공되는 명령줄 도구인 Wevtutil을 사용할 수 있습니다.

Wevtutil 인터페이스를 통해 로그의 세부 정보 표시 수준을 제어할 수 있습니다.

지금은 다음 세 가지 로깅 수준이 지원됩니다.

-   수준 2 - 오류
-   수준 3 - 경고
-   수준 4 - 정보

예를 들어 다음 명령은 MSIPC 이벤트 로그를 사용하도록 설정하고 세부 정보 표시 수준을 정보로 설정합니다.

**wevtutil sl Microsoft-RMS-MSIPC/Debug /e:true /l:4**

**참고** Windows 이벤트 뷰어의 **보기** 메뉴에서 **분석 및 디버그 로그 표시**를 선택하여 MSIPC 디버그 로그가 표시되도록 합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]