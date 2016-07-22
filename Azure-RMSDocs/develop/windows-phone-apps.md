---
title: "Windows Phone 설정 | Azure RMS"
description: "Windows Phone 응용 프로그램에서 Microsoft Rights Management SDK 4.2를 통해 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e25a446e-b977-4736-9c65-7711171fb0e1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 90552435666b8f25c893fcffe8c8cf3355a5942d
ms.openlocfilehash: 136d6e9d0c45a9779f87e32eed8288fe8ee3a622


---

# Windows Phone 설정


Windows Phone 응용 프로그램에서 Microsoft Rights Management SDK 4.2를 통해 AAD RM(Azure Active Directory Rights Management)을 사용하여 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다.

이 항목에서는 새 앱을 만들기 위한 환경을 설정하는 과정을 안내합니다.

-   [필수 구성 요소](#prerequisites)
-   [개발 환경 구성](#configuring_your_development_environment)
-   [참고 항목](#see_also)

## 필수 구성 요소


개발 시스템에 다음 소프트웨어가 있어야 합니다.

-   [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet) 운영 체제
-   [Windows Phone 8.1 개발 도구(SDK)](http://dev.windowsphone.com/en-us/downloadsdk)
-   Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview) 이상 또는 Windows Phone SDK 8.0/8.1에 포함되어 있는 Visual Studio Express 2012
-   Windows Phone용 MS RMS SDK 4.2 패키지. 자세한 내용은 [시작](get-started.md)을 참조하세요.
-   인증 라이브러리: [Azure AD 인증 라이브러리](https://msdn.microsoft.com/en-us/library/jj573266.aspx)를 사용하는 것이 좋으며 다른 인증 라이브러리를 사용할 수도 있습니다.

API 업데이트, 장치 및 환경 정보, 릴리스 정보 및 FAQ(질문과 대답)에 대한 자세한 내용은 [새로운 기능](release-notes.md) 항목을 참조하세요.

Windows Phone 개발자 센터에서 [Windows Phone 개발](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx) 가이드에 있는 정보를 검토합니다.

## 개발 환경 구성


-   *Visual Studio*를 엽니다.
-   **파일**을 클릭합니다. **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.
-   **새 프로젝트** 대화 상자에서 **Visual C\#**, **비어 있는 앱(Windows Phone)**을 차례로 선택하고 **확인**을 클릭합니다.

    ![새 프로젝트 만들기](../media/wpsetup-newproj.png)

-   솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택하여 **참조 추가** 대화 상자를 엽니다.

    ![참조 추가](../media/wpsetup-addref.png)

-   **참조 추가** 대화 상자의 왼쪽 아래에서 **찾아보기**를 클릭하고 패키지를 추출한 폴더에 있는 *Microsoft.RightsManagment.dll* 파일을 선택합니다.
-   **관리되는 앱** - 관리되는 앱을 빌드하려면 이 참조를 추가하고 **Windows 8.1**-&gt;**확장**을 선택한 다음 **Windows용 Windows Visual C++ 런타임 패키지** 확인란을 선택해야 합니다.

    ![확장 추가](../media/wpsetup-refmngr.png)

-   **기능 추가** - 응용 프로그램에서 SDK를 사용하려면 "인터넷(클라이언트 및 서버)" 기능이 필요합니다. 이 기능을 앱에 추가하려면 프로젝트에서 *Package.appxmanifest* 파일을 열고 **기능** 탭으로 이동하여 추가합니다.

이제 새 Windows Phone 앱을 만들 준비가 되었습니다.

### 참고 항목

[시작](get-started.md)

[새로운 기능](release-notes.md)

[핵심 개념](core-concepts.md)

[Windows Phone 개발](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx)

[Windows API 참조](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Windows Phone SDK](http://dev.windowsphone.com/en-us/downloadsdk)

 

 






<!--HONumber=Jul16_HO3-->


