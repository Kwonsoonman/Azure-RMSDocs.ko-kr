---
title: "응용 프로그램 배포 | Azure Information Protection"
description: "이 항목에서는 응용 프로그램 배포를 간략하게 설명하고 안내합니다."
keywords: "배포, RMS, AIP"
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 00bf0748f67afe3f81de86fa643e78652cc0d7a4


---
# <a name="deploy-into-production"></a>프로덕션 환경에 배포

이 항목에서는 AIP(Azure Information Protection)/RMS(Rights Management Services) 사용 응용 프로그램의 배포 프로세스를 안내합니다.

## <a name="request-an-information-protection-integration-agreement-ipia"></a>IPIA(정보 보호 통합 계약) 요청
AIP/RMS를 사용하여 개발한 응용 프로그램을 릴리스하려면 먼저 Microsoft에 정식 계약을 신청하고 완료해야 합니다.

### <a name="begin-the-process"></a>프로세스 시작
다음 정보가 포함된 전자 메일을 **IPIA@microsoft.com**으로 보내 IPIA를 완료합니다.

**제목:** *회사 이름*의 IPIA 요청

전자 메일의 본문에서 다음을 포함합니다.
- 응용 프로그램 또는 제품 이름
- 요청자의 성과 이름
- 요청자의 메일 주소

### <a name="next-steps"></a>다음 단계
Microsoft는 IPIA 요청을 받으면 양식(Word 문서)을 보내드립니다.
IPIA 약관을 검토하고 다음 정보를 기입하여 해당 양식을 **IPIA@microsoft.com**으로 다시 보내세요.
- 회사의 상호
- 회사가 있는 시/도 또는 국가
- 회사 URL
- 담당자의 전자 메일 주소
- 회사의 추가 주소(선택 사항)
- 회사 응용 프로그램의 이름
- 응용 프로그램에 대한 간략한 설명
- *Azure 테넌트 ID*
- 응용 프로그램의 *앱 ID*
- 급한 상황에 연락할 수 있는 회사 연락처, 전자 메일 및 전화 번호

### <a name="completing-the-agreement"></a>계약 완료
양식이 다시 수신되면 디지털 서명을 위해 최종 IPIA 링크를 보내드립니다. 귀하께서 서명하시면 해당 Microsoft 담당자가 서명을 하게 되고 이로써 계약이 완료됩니다.

### <a name="already-have-a-signed-ipia"></a>서명된 IPIA가 이미 있나요?
서명된 IPIA가 이미 있으며 릴리스할 응용 프로그램에 대해 새 *앱 ID*를 추가하려는 경우에는 **IPIA@microsoft.com**에 전자 메일을 보내 다음과 같은 정보를 제공하세요.
- 회사 응용 프로그램의 이름
- 응용 프로그램에 대한 간략한 설명
- Azure 테넌트 ID(이전에 동일한 ID가 있어도 필요함)
- 응용 프로그램의 앱 ID
- 급한 상황에 연락할 수 있는 회사 연락처, 전자 메일 및 전화 번호

전자 메일을 보내신 후에 승인이 수신될 때까지 최대 72시간이 소요될 수 있습니다.

## <a name="deploying-to-the-client-environment"></a>클라이언트 환경에 배포

AIP(Azure Information Protection)/RMS(Rights Management Services) 도구가 기본적으로 제공된 응용 프로그램을 배포하려면 최종 사용자 컴퓨터에 RMS Client 2.1을 배포해야 합니다.

### <a name="rms-client-21"></a>RMS Client 2.1
RMS Client 2.1은 온-프레미스 또는 Microsoft 데이터 센터에 설치되어 있는 AIP/RMS 사용 응용 프로그램을 통과하는 정보에 대한 액세스 및 사용을 보호하기 위해 고안되었습니다.

RMS Client 2.1은 Windows 운영 체제 구성 요소가 아닙니다. 클라이언트는 승인 및 사용권 계약 동의가 지정된 상태로 응용 프로그램과 함께 무료로 배포될 수 있는 선택적 다운로드로 제공됩니다.

> [!IMPORTANT]
> RMS Client 2.1은 아키텍처와 관련이 있으며, 대상 운영 체제의 아키텍처와 일치해야 합니다.


## <a name="rms-client-21-installation-options"></a>RMS Client 2.1 설치 옵션

### <a name="creating-your-deployment-package"></a>배포 패키지 만들기

원하는 설치 기술을 사용하여 RMS 클라이언트 설치 관리자 패키지와 응용 프로그램 또는 솔루션을 번들로 묶는 것이 좋습니다. RMS 클라이언트는 다른 응용 프로그램 및 솔루션과 함께 자유롭게 재배포할 수 있습니다.

RMS Client 2.1 설치 관리자를 시작하여 대화형으로 RMS Client 2.1을 설치하거나 자동으로 설치하도록 선택할 수 있습니다. 통합 단계는 다음과 같습니다.

-   RMS 클라이언트 2.1 설치 관리자 다운로드
-   응용 프로그램 설치 관리자와 RMS Client 2.1 설치 관리자 실행 통합

RMS Client 2.1을 응용 프로그램에 통합하는 예로 [권한 보호 폴더 탐색기](https://technet.microsoft.com/en-us/library/rights-protected-folder-explorer(v=ws.10).aspx) 패키지를 들 수 있습니다. 방법을 이해하려면 직접 설치해 보세요.

### <a name="make-rms-client-21-a-pre-requisite-for-your-application-install"></a>RMS Client 2.1을 응용 프로그램 설치의 필수 조건으로 설정

이 경우 최종 사용자 컴퓨터에 RMS Client 2.1이 없으면 응용 프로그램 설치에 실패하도록 필수 조건을 만듭니다.

클라이언트가 없을 경우 RMS Client 2.1의 복사본을 다운로드할 수 있는 위치를 사용자에게 알리는 오류 메시지를 제공합니다.

클라이언트가 있을 경우 응용 프로그램 설치를 계속합니다.

## <a name="enabling-azure-information-protection--rights-management-services-with-your-application"></a>응용 프로그램에서 Azure Information Protection/Rights Management Services 사용

> [!NOTE]
> 새 ADAL 인증 모델로 마이그레이션한 경우에는 **SIA**를 설치할 필요가 없습니다. 자세한 내용은 [ADAL authentication for your RMS enabled application](adal-auth.md)(RMS 사용 응용 프로그램에 대한 ADAL 인증) 항목을 참조하세요.
> 또한 **Windows 10용 응용 프로그램을 인증**할 수 있습니다. Microsoft Online 로그인 도우미가 아닌 ADAL 인증을 사용하도록 응용 프로그램을 업데이트하여 개발자와 고객은 컴퓨터에 대한 관리자 권한을 요구하지 않고 다단계 인증을 사용하여 RMS Client 2.1을 설치할 수 있습니다.


최종 사용자가 Information Protection/Rights Management Services를 활용하려면 *Online Services SIA(로그인 도우미)*를 배포해야 합니다. 응용 프로그램 개발자는 최종 사용자가 RMS(온-프레미스) 또는 Azure Information Protection 중 어떤 방식으로 Information Protection을 사용할지 알 수 없습니다.


> [!IMPORTANT]
> Azure 기반 RMS를 사용하여 클라이언트 응용 프로그램을 실행하려는 경우 고유한 테넌트를 만들어야 합니다. 자세한 내용은 [Azure RMS requirements: Cloud subscriptions that support Azure RMS](../get-started/requirements-subscriptions.md)(Azure RMS 요구 사항: Azure RMS를 지원하는 클라우드 구독) 항목을 참조하세요.
> Azure RMS를 사용하여 실행하는 방법에 대한 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

-   Microsoft 다운로드 센터에서 [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/en-us/download/details.aspx?id=28177)를 다운로드합니다.
-   권한 사용 응용 프로그램 배포에 이 서비스 선택에 대한 필수 조건 확인이 포함되어 있는지 확인합니다.
-   자체 테스트 및 최종 사용자의 온라인 서비스 사용에 대한 자세한 내용은 TechNet 항목인 [권한 관리 구성](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)을 참조하세요.

응용 프로그램이 Azure 권한 관리 서비스에 RMS를 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 [응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

## <a name="related-topics"></a>관련 항목

* [Microsoft Online Services 로그인 도우미](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Rights Management 구성](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


