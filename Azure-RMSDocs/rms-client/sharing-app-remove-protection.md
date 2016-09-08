---
title: "Rights Management 공유 응용 프로그램을 사용하여 파일에서 보호 제거 | Azure RMS"
description: "이전에 RMS 공유 응용 프로그램을 사용하여 보호했던 파일에서 보호를 제거하여 파일 보호를 해제하려면 파일 탐색기에서 보호 제거 옵션을 사용합니다."
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: da95b938-eaad-4c83-a21e-ff1d4872aae4
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: b94cd999fef2186ddf67a0e6cebc3349a3586538


---

# Rights Management 공유 응용 프로그램을 사용하여 파일에서 보호 제거

>*적용 대상: Active Directory Rights Management Services, Azure 권한 관리, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

이전에 RMS 공유 응용 프로그램을 사용하여 보호했던 파일에서 보호를 제거하여 파일 보호를 해제하려면 파일 탐색기에서 **보호 제거** 옵션을 사용합니다.

> [!IMPORTANT]
> 보호를 제거하려면 파일의 소유자여야 합니다.

## 파일에서 보호를 제거하려면

1.  파일 탐색기에서 Sample.ptxt 등의 파일을 마우스 오른쪽 단추로 클릭하고 **RMS로 보호**를 선택한 다음 **바로 보호**, **보호 제거**를 차례로 클릭합니다.

    ![RMS 공유 응용 프로그램에 대한 보호 제거 메뉴 옵션](../media/ADRMS_MSRMSApp_RemoveProtection.png)

    자격 증명을 입력하라는 메시지가 표시될 수 있습니다.

참고: 이러한 옵션이 표시되지 않으면 RMS 공유 응용 프로그램이 컴퓨터에 설치되어 있지 않거나, 최신 버전을 설치하지 않았거나, 컴퓨터를 다시 시작하여 설치를 완료해야 하는 것일 수 있습니다. 공유 응용 프로그램을 설치하는 방법에 대한 자세한 내용은 [Rights Management 공유 응용 프로그램 다운로드 및 설치](install-sharing-app.md)를 참조하세요.

보호된 원본 파일(예: Sample.ptxt)이 삭제되고 이름은 같지만 보호되지 않는 파일 이름 확장명(예: Sample.txt)의 파일로 바꿉니다.

## 예제 및 기타 지침
예를 들어 Rights Management 공유 응용 프로그램 및 방법 지침을 사용하는 방법에 대한 예는 Rights Management 공유 응용 프로그램 사용자 가이드에서 다음 섹션을 참조하세요.

-   [RMS 공유 응용 프로그램 사용 예제](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [원하는 옵션을 선택하세요.](sharing-app-user-guide.md#what-do-you-want-to-do)

## 참고 항목
[Rights Management 공유 응용 프로그램 사용자 가이드](sharing-app-user-guide.md)



<!--HONumber=Aug16_HO4-->


