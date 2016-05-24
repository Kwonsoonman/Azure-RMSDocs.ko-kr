---
# required metadata

title: 프로덕션 라이선스 얻기 | Azure RMS
description: RMS SDK 2.1을 사용하여 개발한 응용 프로그램을 릴리스하려면 프로덕션 사용권 계약이 필요합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6749817E-FF34-4384-BF63-39AEA5C372CA
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 프로덕션 라이선스 얻기

권한 관리 서비스 SDK 2.1을 사용하여 개발한 응용 프로그램을 릴리스하려면 먼저 프로덕션 사용권 계약을 신청하여 프로덕션 인증서를 얻어야 합니다.

> [!IMPORTANT]
> Azure 기반 RMS를 사용하여 클라이언트 응용 프로그램을 실행하려는 경우 Azure RMS 테넌트를 요청해야 합니다. 테넌트 요청을 포함하여 <rmcstbeta@microsoft.com>으로 메일을 보내세요.

Azure RMS를 사용하여 실행하는 방법에 대한 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.


프로덕션 인증서와 사전 프로덕션 인증서는 유사한 기능을 수행하지만 서로 다른 환경에서 사용됩니다. 둘 다 Microsoft CA(인증 기관) 인증서가 신뢰할 수 있는 루트에 있는 인증서 체인을 포함하지만 사전 프로덕션 인증서는 RMS 응용 프로그램을 개발하는 경우에만 사용됩니다. 프로덕션 인증서는 릴리스 후 환경에서 사용됩니다. 프로덕션 인증서 및 연결된 개인 키는 응용 프로그램의 프로세스 공간에 로드될 수 있거나 로드되어야 하는 파일과 로드되지 않아야 하는 파일을 식별하는 매니페스트를 만들고 서명하는 데 사용됩니다.

키에 대한 자세한 내용은 [권한 사용 응용 프로그램 테스트](running-your-first-application.md)를 참조하세요.

프로덕션 사용권 계약을 신청하면 인증서를 얻을 수 있습니다.

## 프로덕션 사용권 계약 요청

-   다음 정보를 포함하여 [RMLA@microsoft.com](mailto:rmla@microsoft.com)으로 메일 메시지를 보내세요.

    -   전체 회사 이름

    -   실제 회사 주소(구/군/시, 시/도, 국가 또는 지역, 우편 번호 포함)
    -   회사 우편 주소(구/군/시, 시/도, 국가 또는 지역, 우편 번호 포함)
    -   회사 전화 및 팩스 번호
    -   회사 URL
    -   회사 국가 또는 지역
    -   응용 프로그램 또는 제품 이름
    -   요청자의 성과 이름
    -   요청자의 직함 또는 직위
    -   요청자의 메일 주소

    메일 계정이 꼭 필요하지는 않지만 응용 프로그램 프로세스는 일반적으로 메일을 통신에 사용합니다. Microsoft Outlook.com에서 무료 메일 계정을 얻을 수 있습니다. 계정이 없고 원하지 않는 경우 직접 입력한 신청서를 다음 주소로 보낼 수 있습니다.

    `Active Directory Rights Management License Agreements (ADRMLA)`

    `Microsoft Corporation`

    `One Microsoft Way`

    `Redmond, WA 98052-6399`

    계약을 요청하는 경우 다음을 수행하세요.

    -   계약서에 표시되어야 하는 대로 정보를 영어로 제출합니다.
    -   요청된 모든 정보를 보냅니다. 정보가 없거나 불완전하면 요청 처리가 지연될 수 있습니다.

    ADRMLA(Active Directory Rights Management 사용권 계약) 팀은 메일로 전송된 요청에 대해 업무일로 3일 내에 응답하지만 우편 서비스를 사용하여 요청을 보낸 경우에는 더 오래 걸립니다. 응답에는 사용권 계약 양식과 추가 지침이 포함됩니다. 계약서의 모든 페이지를 읽고 서명한 후 ADRMLA 팀에 다시 보냅니다. 사용권 계약의 글꼴을 변경하거나 단락 서식을 다시 지정하지 마세요.

    ADRMLA 팀으로부터 받은 지침을 따라야 합니다. 지침에는 인증서 요청을 이행하는 데 필요한 디지털 정보 항목이 나와 있습니다. 단계별 지침을 따르면 지연이 줄어듭니다.

    ADRMLA 팀은 프로덕션 인증서가 생성된 후 전달합니다. 인증서는 제공한 사용권 계약 및 디지털 정보(공개 키 포함)를 기반으로 생성됩니다. ADRMLA 팀이 인증서를 포함하여 메일로 회신하려면 업무일로 최대 15일 정도 걸리며, 우편 서비스로 통신하는 경우에는 더 오래 걸릴 수 있습니다.

## 관련 항목

* [사용 방법](how-to-use-msipc.md)
* [권한 사용 응용 프로그램 테스트](running-your-first-application.md)
 

 





<!--HONumber=Apr16_HO4-->


