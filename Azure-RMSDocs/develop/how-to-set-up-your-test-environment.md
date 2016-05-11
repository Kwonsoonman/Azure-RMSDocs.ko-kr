---
# required metadata

title: 테스트 환경 설정 | Azure RMS
description: 다양한 서버 옵션으로 권한 사용 응용 프로그램을 테스트할 수 있습니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4d32682c-754d-4e30-977d-95b08e0662cc

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
# 테스트 환경 설정

다양한 서버 옵션으로 권한 사용 응용 프로그램을 테스트할 수 있습니다.

**중요** 먼저 AD RMS 사전 프로덕션 환경에서 AD RMS 서버에 대해 권한 관리 서비스 SDK 2.1 응용 프로그램을 테스트하는 것이 좋습니다. 그런 다음 고객이 Azure RMS 서비스와 함께 응용 프로그램을 사용할 수 있게 하려는 경우 해당 환경에서 테스트합니다. 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

 

### 필수 구성 요소

-   [SDK 설치](create-your-first-rights-aware-application.md)

지침

### 1단계: 테스트 환경 설정

권한 사용 응용 프로그램을 테스트하려면 사전 프로덕션용으로 구성된 RMS 서버에 대해 실행해야 합니다. 사전 프로덕션 RMS 서버는 사전 프로덕션/ISV 인증서 계층 구조를 사용하여 파일을 암호화하고 암호를 해독합니다.

AD RMS 인증서 계층 구조에 대한 자세한 내용은 [인증서 체인 이해](understanding-certificate-chains.md)를 참조하세요.

RMS 서버에 대해 응용 프로그램을 테스트하는 데 사용할 수 있는 옵션에는 다음 두 가지가 있습니다.

-   **단일 시스템(1-box) AD RMS ISV 환경에서 응용 프로그램을 실행할 수 있습니다**. Windows Server 2012, Windows Server 2008 R2 또는 Windows Server 2008을 실행하며 Hyper-V가 설치되어 있는 경우 AD RMS 단일 시스템(1-box) VHD로 가상 컴퓨터를 빌드하여 단일 시스템(1-box) AD RMS ISV 환경을 배포할 수 있습니다. 단일 시스템(1-box) AD RMS ISV 환경에서는 사전 프로덕션용으로 구성된 RMS 서버를 제공하며 Active Directory Rights Management Services 클라이언트 2.1도 설치되어 있습니다. RMS 서버와 클라이언트에 대한 레지스트리 설정은 이미 구성되어 있습니다. 응용 프로그램을 테스트하려면 단일 시스템(1-box) 환경이 배포된 가상 컴퓨터에서 실행합니다.
-   **사전 프로덕션용으로 구성되고 네트워크에 배포된 RMS 서버에 대해 응용 프로그램을 실행할 수 있습니다**. 이 경우 응용 프로그램을 실행할 컴퓨터에 AD RMS 클라이언트 2.1도 설치 및 구성해야 합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [클라이언트 구성](how-to-configure-the-ad-rms-client-2-0.md)을 참조하세요. RMS 서버를 배포하고 사전 프로덕션용으로 구성하는 방법에 대한 자세한 내용은 [서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md)을 참조하세요.

### 관련 항목

* [사용 방법](how-to-use-msipc.md)
* [AD RMS SDK 웹 세미나 참고 자료 다운로드 페이지](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
* [클라이언트 구성](how-to-configure-the-ad-rms-client-2-0.md)
* [SDK 설치](create-your-first-rights-aware-application.md)
* [서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md)
* [인증서 체인 이해](understanding-certificate-chains.md)
 

 





<!--HONumber=Apr16_HO3-->


