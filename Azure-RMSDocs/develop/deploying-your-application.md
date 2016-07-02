---
title: "응용 프로그램 배포 | Azure RMS"
description: "이 항목에서는 권한 사용 응용 프로그램에 대한 배포 옵션을 간략하게 설명하고 안내합니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 872bb0c20db2ef8d661d321598a2b1fe61d69316
ms.openlocfilehash: 902721ae3e69afd144c552b8ee0a916958e80afc


---

# 사전 프로덕션 환경에 배포


이 항목에서는 권한 사용 응용 프로그램에 대한 배포 옵션을 간략하게 설명하고 안내합니다.

## 프로덕션 사용권 계약 요청

 권한 관리 서비스 SDK 2.1을 사용하여 개발한 응용 프로그램을 릴리스하려면 먼저 프로덕션 사용권 계약을 신청하여 프로덕션 인증서를 얻어야 합니다.

> [!IMPORTANT]
> Azure 기반 RMS를 사용하여 클라이언트 응용 프로그램을 실행하려는 경우 고유한 테넌트를 만들어야 합니다. 자세한 내용은 [Azure RMS requirements: Cloud subscriptions that support Azure RMS](../get-started/requirements-subscriptions.md)(Azure RMS 요구 사항: Azure RMS를 지원하는 클라우드 구독) 항목을 참조하세요.
> Azure RMS를 사용하여 실행하는 방법에 대한 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

프로덕션 사용권 계약을 신청하면 인증서를 얻을 수 있습니다.

다음 정보를 포함하여 [RMLA@microsoft.com](mailto:rmla@microsoft.com)으로 메일 메시지를 보내세요.

- 전체 회사 이름
- 실제 회사 주소(구/군/시, 시/도, 국가 또는 지역, 우편 번호 포함)
- 회사 우편 주소(구/군/시, 시/도, 국가 또는 지역, 우편 번호 포함)
- 회사 전화 및 팩스 번호
- 회사 URL
- 회사 국가 또는 지역
- 응용 프로그램 또는 제품 이름
- 요청자의 성과 이름
- 요청자의 직함 또는 직위
- 요청자의 메일 주소

메일 계정이 꼭 필요하지는 않지만 응용 프로그램 프로세스는 일반적으로 메일을 통신에 사용합니다. Microsoft Outlook.com에서 무료 메일 계정을 얻을 수 있습니다. 계정이 없고 원하지 않는 경우 직접 입력한 신청서를 다음 주소로 보낼 수 있습니다.

      Active Directory Rights Management License Agreements (ADRMLA)

      Microsoft Corporation

      One Microsoft Way

      Redmond, WA 98052-6399

계약을 요청하는 경우 다음을 수행하세요.
- 계약서에 표시되어야 하는 대로 정보를 영어로 제출합니다.
- 요청된 모든 정보를 보냅니다. 정보가 없거나 불완전하면 요청 처리가 지연될 수 있습니다.

ADRMLA(Active Directory Rights Management 사용권 계약) 팀은 메일로 전송된 요청에 대해 업무일로 3일 내에 응답하지만 우편 서비스를 사용하여 요청을 보낸 경우에는 더 오래 걸립니다. 응답에는 사용권 계약 양식과 추가 지침이 포함됩니다. 계약서의 모든 페이지를 읽고 서명한 후 ADRMLA 팀에 다시 보냅니다. 사용권 계약의 글꼴을 변경하거나 단락 서식을 다시 지정하지 마세요.

ADRMLA 팀으로부터 받은 지침을 따라야 합니다. 지침에는 인증서 요청을 이행하는 데 필요한 디지털 정보 항목이 나와 있습니다. 단계별 지침을 따르면 지연이 줄어듭니다.

ADRMLA 팀은 프로덕션 인증서가 생성된 후 전달합니다. ADRMLA 팀이 인증서를 포함하여 메일로 회신하려면 업무일로 최대 15일 정도 걸리며, 우편 서비스로 통신하는 경우에는 더 오래 걸릴 수 있습니다.


## Rights Management Service Client 2.1의 설치 옵션 및 요구 사항

RMS SDK 2.1을 활용했다고 가정할 경우 최종 사용자 컴퓨터에 Active Directory Rights Management Service 클라이언트 2.1을 배포해야 합니다.

### RMS Client 2.1

RMS Client 2.1은 온-프레미스 또는 Microsoft 데이터 센터에 설치되어 있는지와 관계없이 RMS를 사용하는 응용 프로그램을 통과하는 정보에 대한 액세스 및 사용을 보호하도록 설계된 클라이언트 컴퓨터용 소프트웨어입니다.

RMS Client 2.1은 Windows 운영 체제 구성 요소가 아닙니다. RMS Client 2.1은 선택적 다운로드로 제공되며, 사용권 계약의 승인 및 동의를 통해 타사 소프트웨어와 함께 무료로 배포되어, 사용자 환경에서 RMS 서버를 사용하고 배포하여 권한이 보호된 콘텐츠를 클라이언트가 액세스할 수 있게 합니다.


> [!IMPORTANT]
> AD RMS 클라이언트 2.1은 아키텍처와 관련이 있으며, 대상 운영 체제의 아키텍처와 일치해야 합니다.


## RMS Client 2.1 설치 옵션

-   **RMS Client 2.1 재배포**

    원하는 설치 기술을 사용하여 RMS 클라이언트 설치 관리자 패키지와 응용 프로그램 또는 솔루션을 번들로 묶는 것이 좋습니다. RMS 클라이언트는 다른 응용 프로그램 및 IT 솔루션과 함께 무료로 재배포 및 번들될 수 있습니다.

    RMS Client 2.1 설치 관리자를 시작하여 대화형으로 RMS Client 2.1을 설치하거나 자동으로 설치하도록 선택할 수 있습니다. 통합 단계는 다음과 같습니다.

    -   RMS 클라이언트 2.1 설치 관리자 다운로드
    -   응용 프로그램 설치 관리자와 RMS Client 2.1 설치 관리자 실행 통합

    응용 프로그램과 RMS Client 2.1 통합의 좋은 예로 RMS SDK 2.1 설치 관리자 패키지와 권한 보호된 폴더 탐색기 패키지가 있습니다. 방법을 이해하려면 직접 설치해 보세요.

-   **RMS Client 2.1을 응용 프로그램 설치의 필수 조건으로 설정**

    이 경우 최종 사용자 컴퓨터에 RMS Client 2.1이 없으면 응용 프로그램 설치에 실패하도록 필수 조건을 만듭니다.

    클라이언트가 없을 경우 RMS Client 2.1의 복사본을 다운로드할 수 있는 위치를 사용자에게 알리는 오류 메시지를 제공합니다.

    클라이언트가 있을 경우 응용 프로그램 설치를 계속합니다.

## 응용 프로그램에서 Azure 권한 관리 서비스 사용

> [!NOTE]
> 새 ADAL 인증 모델로 마이그레이션한 경우에는 SIA를 설치할 필요가 없습니다. 자세한 내용은 [ADAL authentication for your RMS enabled application](adal-auth.md)(RMS 사용 응용 프로그램에 대한 ADAL 인증) 항목을 참조하세요.
> 또한 **Windows 10용 응용 프로그램을 인증**할 수 있습니다. Microsoft Online 로그인 도우미가 아닌 ADAL 인증을 사용하도록 응용 프로그램을 업데이트하여 개발자와 고객은 컴퓨터에 대한 관리자 권한을 요구하지 않고 다단계 인증을 사용하여 RMS Client 2.1을 설치할 수 있습니다.


최종 사용자가 Azure 권한 관리 서비스를 활용하려면 *Online Services SIA(로그인 도우미)*를 배포해야 합니다. 응용 프로그램 개발자는 최종 사용자가 RMS(온-프레미스)를 사용할지, 아니면 Azure 권한 관리 서비스(클라우드 서비스)를 사용할지 알 수 없습니다.


> [!IMPORTANT]
> Azure RMS를 사용하여 RMS SDK 2.1 클라이언트 응용 프로그램을 실행하려면 고유한 테넌트를 만들어야 합니다. 자세한 내용은 [Azure RMS requirements: Cloud subscriptions that support Azure RMS](../get-started/requirements-subscriptions.md)(Azure RMS 요구 사항: Azure RMS를 지원하는 클라우드 구독) 항목을 참조하세요.

-   Microsoft 다운로드 센터에서 [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/en-us/download/details.aspx?id=28177)를 다운로드합니다.
-   권한 사용 응용 프로그램 배포에 이 서비스 선택에 대한 필수 조건 확인이 포함되어 있는지 확인합니다.
-   자체 테스트 및 최종 사용자의 온라인 서비스 사용에 대한 자세한 내용은 TechNet 항목인 [권한 관리 구성](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)을 참조하세요.

응용 프로그램이 Azure 권한 관리 서비스에 RMS를 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 [응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

## 관련 항목

* [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Rights Management 구성](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)
 

 



<!--HONumber=Jun16_HO4-->


