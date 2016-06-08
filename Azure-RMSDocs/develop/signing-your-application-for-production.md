---
# required metadata

title: 프로덕션 응용 프로그램에 서명 | Azure RMS
description: 이 항목에서는 프로덕션 모드의 응용 프로그램에 서명하는 과정을 안내합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 09BA148C-7D1E-43C8-92EA-24BBB6EFDB19
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
# 프로덕션 응용 프로그램에 서명

이 항목에서는 프로덕션 모드의 응용 프로그램에 서명하는 과정을 안내합니다.

## 권한 사용 응용 프로그램에 서명

이러한 단계에서는 사전 프로덕션 계층 구조에 대해 응용 프로그램에 이미 서명했다고 가정합니다. 아직 서명하지 않은 경우 [권한 사용 응용 프로그램 테스트](running-your-first-application.md)에 설명된 프로세스를 진행합니다.

Microsoft에서 프로덕션 인증서를 받으면 다음 파일을 보유하게 됩니다.

-   YourPrivateKey.dat
-   YourPublicKey.dat
-   ProductionCertificate.xml

*GenManifest.exe* 및 응용 프로그램 이진(.exe)과 동일한 디렉터리에 저장합니다.

-   아래 프로세스에서는 프로덕션 인증서를 사용하여 새 MCF 파일을 만드는 과정을 안내합니다.

    -   새 디렉터리를 만들고 해당 새 디렉터리에 파일을 저장합니다. Notepad.exe를 사용하여 응용 프로그램에 대한 MCF 파일을 만듭니다. 파일에는 다음 내용이 있어야 합니다.

        ``` syntax
        AUTO-GUID
        .\\YourPrivateKey.dat
        modulelist
        req     .\\<yourappname>.exe
        POLICYLIST
        INCLUSION
        PUBLICKEY .\\YourPublicKey.dat
        EXCLUSION
        ```

    -   다음 명령을 실행하여 응용 프로그램에 서명합니다.

        **genmanifest.exe -chain ProductionCertificate.xml** *YourAppName***.mcf** *YourAppName***.exe.man**

        Genmanifest에 성공하면 다음 텍스트만 표시됩니다.

        Genmanifest에 실패하면 오류 메시지가 표시됩니다.

    -   *앱 이름*.exe.man은 항상 *앱 이름*.exe와 동일한 디렉터리에 저장해야 합니다.

## 관련 항목

* [사용 방법](how-to-use-msipc.md)
* [권한 사용 응용 프로그램 테스트](running-your-first-application.md)
 

 





<!--HONumber=Jun16_HO1-->


