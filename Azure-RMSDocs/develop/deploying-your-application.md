---
# required metadata

title: 응용 프로그램 배포 | Azure RMS
description: 이 항목에서는 권한 사용 응용 프로그램에 대한 배포 옵션을 간략하게 설명하고 안내합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 응용 프로그램 배포


이 항목에서는 권한 사용 응용 프로그램에 대한 배포 옵션을 간략하게 설명하고 안내합니다.

> [!IMPORTANT]
> 먼저 RMS 사전 프로덕션 환경에서 RMS 서버에 대해 권한 관리 서비스 SDK 2.1 응용 프로그램을 테스트하는 것이 좋습니다. 그런 다음 고객이 Azure RMS 서비스와 함께 응용 프로그램을 사용할 수 있게 하려는 경우 해당 환경에서 테스트합니다. 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

 

## Active Directory Rights Management Services 클라이언트 2.1에 대한 설치 옵션

프로덕션 인증서를 사용하여 매니페스트 파일을 만들었으면 응용 프로그램을 배포할 준비가 된 것입니다. RMS SDK 2.1을 활용했다고 가정할 경우 최종 사용자 컴퓨터에 Active Directory Rights Management Service 클라이언트 2.1을 배포해야 합니다.

### AD RMS 클라이언트 2.1

AD RMS 클라이언트 2.1은 온-프레미스 또는 Microsoft 데이터 센터에 설치되어 있는지에 관계없이 응용 프로그램을 통과하는 정보에 대한 액세스 및 사용을 보호하도록 설계된 클라이언트 컴퓨터용 소프트웨어입니다.

AD RMS 클라이언트 2.1은 Windows 운영 체제 구성 요소가 아닙니다. AD RMS 클라이언트 2.1은 선택적 다운로드로 제공되며, 사용권 계약의 승인 및 동의를 통해 타사 소프트웨어와 함께 무료로 배포되어 사용자 환경에서 RMS 서버를 사용 및 배포하여 권한이 보호된 콘텐츠를 클라이언트가 액세스할 수 있게 합니다.

> [!IMPORTANT]
> AD RMS 클라이언트 2.1은 아키텍처와 관련이 있으며, 대상 운영 체제의 아키텍처와 일치해야 합니다.


## AD RMS 클라이언트 2.1 설치 옵션

-   **AD RMS 클라이언트 2.1 재배포**

    원하는 설치 기술을 사용하여 RMS 클라이언트 설치 관리자 패키지와 응용 프로그램 또는 솔루션을 번들로 묶는 것이 좋습니다. RMS 클라이언트는 다른 응용 프로그램 및 IT 솔루션과 함께 무료로 재배포 및 번들될 수 있습니다.

    AD RMS 클라이언트 2.1 설치 관리자를 시작하여 대화형으로 AD RMS 클라이언트 2.1을 설치하거나 자동으로 설치하도록 선택할 수 있습니다. 통합 단계는 다음과 같습니다.

    -   RMS 클라이언트 2.1 설치 관리자 다운로드
    -   응용 프로그램 설치 관리자와 AD RMS 클라이언트 2.1 설치 관리자 실행 통합

    응용 프로그램과 AD RMS 클라이언트 2.1 통합의 좋은 예로 RMS SDK 2.1 설치 관리자 패키지와 권한 보호된 폴더 탐색기 패키지가 있습니다. 방법을 이해하려면 직접 설치해 보세요.

-   **AD RMS 클라이언트 2.1을 응용 프로그램 설치의 필수 조건으로 설정**

    이 경우 최종 사용자 컴퓨터에 AD RMS 클라이언트 2.1이 없으면 응용 프로그램 설치에 실패하도록 필수 조건을 만듭니다.

    클라이언트가 없을 경우 AD RMS 클라이언트 2.1의 복사본을 다운로드할 수 있는 위치를 사용자에게 알리는 오류 메시지를 제공합니다.

    클라이언트가 있을 경우 응용 프로그램 설치를 계속합니다.

## 응용 프로그램에서 Azure 권한 관리 서비스 사용

> [!NOTE]
> 새 ADAL 인증 모델로 마이그레이션한 경우에는 SIA를 설치할 필요가 없습니다. 자세한 내용은 RMS 사용 응용 프로그램에 대한 ADAL 인증을 참조하세요.

- **Windows 10용 응용 프로그램 인증**: Microsoft Online 로그인 도우미 대신 ADAL 인증을 사용하도록 응용 프로그램을 업데이트하면 개발자와 고객이 다음을 수행할 수 있습니다.
  - 다단계 인증 활용
  - 컴퓨터에 대한 관리자 권한 없이 RMS 2.1 클라이언트 설치
 
  최종 사용자가 Azure 권한 관리 서비스를 활용하려면 *Online Services 로그인 도우미*를 배포해야 합니다. 응용 프로그램 개발자는 최종 사용자가 RMS(온-프레미스)를 사용할지, 아니면 Azure 권한 관리 서비스(클라우드 서비스)를 사용할지 알 수 없습니다.

> [!IMPORTANT]
> Azure RMS를 사용하여 RMS SDK 2.1 클라이언트 응용 프로그램을 실행하려면 Azure RMS 테넌트를 요청해야 합니다. 테넌트 요청을 포함하여 <rmcstbeta@microsoft.com>으로 메일을 보내세요.

-   Microsoft 다운로드 센터에서 [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/en-us/download/details.aspx?id=28177)를 다운로드합니다.
-   권한 사용 응용 프로그램 배포에 이 서비스 선택에 대한 필수 조건 확인이 포함되어 있는지 확인합니다.
-   자체 테스트 및 최종 사용자의 온라인 서비스 사용에 대한 자세한 내용은 TechNet 항목인 [권한 관리 구성](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)을 참조하세요.

응용 프로그램이 Azure 권한 관리 서비스에 RMS를 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 [응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

## 관련 항목

* [사용 방법](how-to-use-msipc.md)
* [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Rights Management 구성](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)
 

 





<!--HONumber=Apr16_HO4-->


