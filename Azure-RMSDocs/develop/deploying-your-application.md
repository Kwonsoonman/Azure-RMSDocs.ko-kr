---
title: 응용 프로그램 배포 - AIP
description: 이 항목에서는 응용 프로그램의 배포 과정을 간략하게 설명합니다.
keywords: 배포, RMS, AIP
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 300fb1d14bc4eda93b0e40ffbd9e6c2329c88517
ms.sourcegitcommit: e21fb3385de6f0e251167e5dc973e90f0e7f2bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2018
ms.locfileid: "28908088"
---
# <a name="deploy-into-production"></a>프로덕션에 배포

이 항목에서는 AIP(Azure Information Protection)/RMS(Rights Management Services) 사용 응용 프로그램의 배포 프로세스 과정을 설명합니다.

## <a name="request-an-information-protection-integration-agreement-ipia"></a>IPIA(Information Protection Integration Agreement) 요청
AIP/RMS를 사용하여 개발한 응용 프로그램을 릴리스하기 전에 Microsoft와의 공식 계약을 적용하고 완료해야 합니다.

### <a name="begin-the-process"></a>프로세스 시작
다음과 같은 정보가 포함된 **IPIA@microsoft.com**에 이메일을 전송하여 IPIA를 가져옵니다.

**제목:** *회사 이름*에 대한 IPIA 요청

이메일의 본문에는 다음이 포함됩니다.
- 응용 프로그램 및 제품 이름
- 요청자의 성과 이름
- 요청자의 이메일 주소

### <a name="next-steps"></a>다음 단계
IPIA 요청을 받는 즉시 양식을 전송합니다(Word 문서로).
IPIA의 약관을 검토하고 다음과 같은 정보를 포함하여 양식을 **IPIA@microsoft.com**에 반환합니다.
- 회사의 공식 이름
- 법인의 시/도(미국 / 캐나다) 또는 국가
- 회사 URL
- 담당자의 이메일 주소
- 회사의 추가 주소(선택 사항)
- 회사 응용 프로그램의 이름
- 응용 프로그램에 대한 간단한 설명
- *Azure 테넌트 ID*
- 응용 프로그램의 *앱 ID*
- 중요한 상황 대응을 위한 회사 연락처, 이메일 및 전화

### <a name="completing-the-agreement"></a>규약 완료
양식을 수신하면 디지털로 서명할 최종 IPIA 링크를 전송합니다. 로그인한 후에 적절한 Microsoft 담당자가 서명하면 규약이 완료됩니다.

### <a name="already-have-a-signed-ipia"></a>이미 IPIA에 서명하셨나요?
이미 서명된 IPIA가 있고 릴리스하는 응용 프로그램에 새 *앱 ID*를 추가하려는 경우 **IPIA@microsoft.com**에 이메일을 보내고 다음과 같은 정보를 제공합니다.
- 회사 응용 프로그램의 이름
- 응용 프로그램에 대한 간단한 설명
- Azure 테넌트 ID(이전과 동일한 경우에도)
- 응용 프로그램의 앱 ID
- 중요한 상황 대응을 위한 회사 연락처, 이메일 및 전화

이메일을 보내면 수신을 승인하는 데 최대 72시간이 걸립니다.

## <a name="deploying-to-the-client-environment"></a>클라이언트 환경에 배포

응용 프로그램을 배포하기 위해 AIP(Azure Information Protection)/RMS(Rights Management Services) 도구를 기반으로 최종 사용자의 컴퓨터에 RMS 클라이언트 2.1을 배포해야 합니다.

### <a name="rms-client-21"></a>RMS 클라이언트 2.1
RMS 클라이언트 2.1은 온-프레미스 또는 Microsoft 데이터 센터에 설치되어 있는지와 상관 없이 AIP/RMS 사용 응용 프로그램을 통해 흐르는 정보대에 한 액세스 및 사용량을 보호하도록 디자인되었습니다.

RMS 클라이언트 2.1은 Windows 운영 체제 구성 요소가 아닙니다. 클라이언트는 사용권 계약의 승인 및 동의와 함께 선택적 다운로드로 제공될 수 있으며 응용 프로그램에서 무료로 배포됩니다.

> [!IMPORTANT]
> RMS 클라이언트 2.1은 아키텍처가 지정되며 대상 운영 체제의 아키텍처와 일치해야 합니다.


## <a name="rms-client-21-installation-options"></a>RMS 클라이언트 2.1 설치 옵션

### <a name="creating-your-deployment-package"></a>배포 패키지 만들기

원하는 설치 방법을 사용하여 응용 프로그램 또는 솔루션에서 RMS 클라이언트 설치 관리자 패키지를 번들하는 것이 좋습니다. RMS 클라이언트는 다른 응용 프로그램 및 솔루션과 함께 자유롭게 다시 배포될 수 있습니다.

RMS 클라이언트 2.1 설치 관리자를 시작하거나 자동으로 설치하여 RMS 클라이언트 2.1을 대화형으로 설치할 수 있습니다. 통합 단계는 다음과 같습니다.

-   RMS 클라이언트 2.1 설치 관리자 다운로드
-   응용 프로그램 설치 관리자와 실행할 RMS 클라이언트 2.1 설치 관리자 통합

응용 프로그램과 RMS 클라이언트 2.1을 통합하는 예로 [권한 보호 폴더 탐색기](https://technet.microsoft.com/library/rights-protected-folder-explorer(v=ws.10).aspx) 패키지가 있습니다. 이제 설치하여 방법을 이해해보세요.

### <a name="make-rms-client-21-a-pre-requisite-for-your-application-install"></a>응용 프로그램 설치를 위한 필수 구성 요소인 RMS 클라이언트 2.1

이 경우에 최종 사용자 컴퓨터에 RMS 클라이언트 2.1이 설치되지 않으면 응용 프로그램 설치에 실패하도록 필수 구성 요소를 만듭니다.

클라이언트가 없는 경우 RMS 클라이언트 2.1의 복사본을 다운로드할 수 있는 위치를 사용자에게 알리는 오류 메시지가 제공됩니다.

클라이언트가 있는 경우 응용 프로그램 설치를 진행합니다.

## <a name="enabling-azure-information-protection-services-with-your-application"></a>응용 프로그램에서 Azure Information Protection 서비스 사용

> [!NOTE]
> 인증을 위해 새로운 ADAL 모델로 마이그레이션한 경우 **SIA**를 설치할 필요가 없습니다. 자세한 내용은 [RMS 사용 응용 프로그램에서 ADAL 인증](adal-auth.md)을 참조하세요.
> 또한 **Windows 10용 응용 프로그램을 인증**할 수 있습니다. 사용자와 고객은 Microsoft Online 로그인 도우미 대신 ADAL 인증을 사용하도록 응용 프로그램을 업데이트하여 컴퓨터에 대한 관리자 권한이 필요 없이 다단계 인증 설치 RMS 클라이언트 2.1을 활용할 수 있습니다.

최종 사용자가 Information Protection 서비스를 활용하기 위해 *Online Services SIA(로그인 도우미)* 를 배포해야 합니다. 사용자가 응용 프로그램 개발자인 경우 최종 사용자가 RMS(온-프레미스) 또는 Azure Information Protection을 통해 Information Protection을 사용할지 여부를 알 수 없습니다.


> [!IMPORTANT]
> Azure 기반 RMS에서 클라이언트 응용 프로그램을 실행하려는 경우 고유한 테넌트를 만들어야 합니다. 자세한 내용은 [Azure RMS 요구 사항: Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하세요.
> Azure RMS에서 실행에 대한 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용하도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

-   Microsoft 다운로드 센터에서 [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/download/details.aspx?id=28177)를 다운로드합니다.
-   권한 사용 응용 프로그램의 배포에 이 서비스를 선택하기 위한 필수 구성 요소 검사가 포함되어 있는지 확인합니다.
-   고유한 테스트 및 최종 사용자의 온라인 서비스 사용은 TechNet 항목 [Rights Management 구성](https://TechNet.Microsoft.Com/library/jj585002.aspx)을 참조하세요.

[Azure Active Directory 로그인을 사용하도록 App Service 응용 프로그램을 구성하는 방법](https://docs.microsoft.com/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication) 가이드를 사용하여 앱을 구성해야 합니다.

응용 프로그램이 Azure Rights Management 서비스에 RMS를 사용하도록 설정하는 방법에 대한 자세한 내용은 [응용 프로그램에서 클라우드 기반 RMS를 사용하도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

## <a name="related-topics"></a>관련 항목

* [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/download/details.aspx?id=28177)
* [Rights Management 구성](https://TechNet.Microsoft.Com/library/jj585002.aspx)
* [응용 프로그램에서 클라우드 기반 RMS를 사용하도록 설정](how-to-use-file-api-with-aadrm-cloud.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
