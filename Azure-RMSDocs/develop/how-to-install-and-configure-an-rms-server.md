---
# required metadata

title: 서버 설치 및 구성 | Azure RMS
description: 권한 사용 응용 프로그램 테스트에 사용할 RMS 서버를 설치 및 구성합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e51adc12-4ee1-4819-bd8e-08ccf654fa00

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
# 서버 설치 및 구성

이 항목에서는 권한 사용 응용 프로그램 테스트에 사용할 RMS 서버를 설치 및 구성하는 단계를 설명합니다.

**중요** 단일 시스템(1-box) RMS ISV 환경에서 응용 프로그램을 실행하여 테스트하는 경우에는 단일 시스템(1-box) 환경에 RMS 서버가 이미 설치 및 구성되어 있으므로 설치할 필요가 없습니다.
단일 시스템(1-box) AD RMS ISV 환경에 대한 자세한 내용은 [테스트 환경 설정](how-to-set-up-your-test-environment.md)을 참조하세요.

 

## 지침

### 1단계: RMS 서버 설정

다음 단계에서는 RMS 서버 설정 과정을 안내하며 다음 작업을 포함합니다.

-   레지스트리 구성
-   서버 설치
-   서버 등록

1.  **레지스트리 구성**

    사전 프로덕션 인증서 계층 구조를 사용 중이라고 지정하려면 다음 레지스트리 값을 설정합니다.

    **참고** Windows Server 2008 R2 또는 Windows Server 2008을 사용하는 경우 AD RMS 서비스를 설치하기 전에 레지스트리 값을 설정합니다.

    Windows Server 2008 R2에서 AD RMS를 사용하는 경우 다음과 같은 **REG\_DWORD** 값을 설정해야 합니다. 프로덕션 계층 구조로 전환하려면 이 값을 0으로 변경합니다.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**Hierarchy** = 0x00000001

    Windows Server 2008 R2에서 AD RMS를 사용 중이며 다른 AD RMS 서비스가 Active Directory에 사전 프로덕션 서비스로 이미 배포되어 있으면 다음 빈 문자열 값을 레지스트리에 추가합니다.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**GICURL** = ""

    Windows Server 2008에서 AD RMS를 사용하는 경우 다음과 같은 **REG\_DWORD** 값을 설정해야 합니다. 프로덕션 계층 구조로 전환하려면 이 값을 0으로 변경합니다.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**Hierarchy** = 0x00000001

    Windows Server 2008에서 AD RMS를 사용 중이며 다른 AD RMS 서비스가 Active Directory에 사전 프로덕션 서비스로 이미 배포되어 있으면 다음 빈 문자열 값을 레지스트리에 추가합니다.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**GICURL** = ""

2.  **서버 설치**

    AD RMS(Active Directory Rights Management Services)는 개별 클라이언트 및 서버 구성 요소로 이루어져 있습니다. 서버 구성 요소는 RMS 인프라를 관리하고, 콘텐츠 소비자 및 게시자에게 라이선스를 발급하고, 컴퓨터 및 사용자에게 인증서를 발급하는 데 사용할 수 있는 웹 서비스 집합으로 구현됩니다.

    Windows Server 2008 이상에서는 클라이언트 및 서버 구성 요소가 운영 체제에 포함되어 있습니다. 이전 운영 체제에 대한 서버 구성 요소는 다음 위치에서 다운로드할 수 있습니다.

    -   [RMS 서버 v1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    Windows Server 2008에서 서버 구성 요소를 구성하려면 AD RMS 역할을 설치해야 합니다. 그러나 그전에 레지스트리를 구성하여 프로덕션 계층 구조가 아니라 사전 프로덕션 인증서 계층 구조를 사용하도록 지정해야 합니다. 그러나 이전 서버 운영 체제를 기반으로 하여 응용 프로그램을 개발하는 경우 RMS 서버 v1.0 SP2를 설치한 후, RMS 서비스를 프로비전하기 전에 레지스트리를 구성합니다.

    자세한 내용은 이전 단계인 1단계, "레지스트리 구성"을 참조하세요.

3.  **서버 등록**

    RMS(Rights Management Services) 서버를 등록하여 사전 프로덕션 또는 프로덕션 계층 구조에서 식별해야 합니다. 등록 프로세스를 수행하면 서버 컴퓨터에 서버 사용 허가자 인증서가 남습니다. 이 인증서는 Microsoft의 신뢰할 수 있는 루트에 다시 연결됩니다. 서버를 등록하는 방법은 사용 중인 RMS 버전에 따라 달라집니다.

    -   **자체 등록**

        Windows Server 2008 이상에서는 Microsoft에 정보를 보내지 않고 적절한 계층 구조에 RMS 서버를 등록할 수 있습니다. RMS 역할을 설치할 때 자체 등록 인증서와 개인 키도 설치됩니다. 이러한 인증서와 키는 서버 사용 허가자 인증서를 자동으로 만드는 데 사용됩니다. Microsoft와 정보를 교환하지 않습니다.

    -   **온라인 등록**AD RMS v1.0 SP2를 사용하는 경우 온라인에서 서버를 등록할 수 있습니다. 등록은 프로비전 프로세스 중 백그라운드에서 발생하지만 인터넷 연결이 있어야 하고 적절한 레지스트리 값을 지정하여 서버를 등록할 계층 구조를 식별해야 합니다. 사전 프로덕션 계층 구조를 등록하려면 다음과 같은 **REG\_SZ** 값을 추가하고 서버를 프로비전합니다. 프로덕션 계층 구조를 등록하려면 이 값을 지우고 서버를 프로비전합니다.

        자세한 내용은 이전 단계인 1단계, "레지스트리 구성"을 참조하세요.

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

### 관련 항목

* [사용 방법](how-to-use-msipc.md)
 

 





<!--HONumber=Apr16_HO3-->


