---
title: 빠른 시작 자습서 3단계 - AIP
description: Azure Information Protection를 빠르게 사용해 보기 위한 소개 자습서 3단계 - 클라이언트 설치
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
ms.openlocfilehash: 203964dfb153b45c515fa93c8cb6b69ebe3fbd37
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151642"
---
# <a name="step-3-install-the-client"></a>3단계: 클라이언트 설치

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

이 단계에서는 방금 구성한 정책이 Windows PC에 다운로드되고 Office 응용 프로그램에 레이블이 표시되도록 Azure Information Protection 클라이언트를 설치합니다.


## <a name="install-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트 설치

1. Office가 설치된(그러나 Word는 현재 열려 있지 않은) PC에서 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)로 이동하여 **AzInfoProtection.exe**를 다운로드합니다.
    
2. 방금 다운로드한 실행 파일을 실행하고 프롬프트에 따라 클라이언트를 설치합니다.
    
    이 자습서에서는 방금 구성한 정책이 Azure에서 다운로드되고 설치된 경우 데모 정책을 바꿀 것이므로 데모 정책 설치 옵션의 선택 여부는 중요하지 않습니다. 그러나 Azure Information Protection에 연결하지 않고 기본 레이블을 경험해 보려는 경우 데모 정책 옵션을 사용할 수 있습니다. 

## <a name="verify-the-installation"></a>설치 확인

Word와 새 빈 문서를 열어 설치가 완료되었는지 확인합니다(이번에는 저장하지 않음). 사용자 이름과 암호를 입력하라는 메시지가 표시되면 전역 관리자 계정의 세부 정보를 입력합니다. 

이번이 처음으로 클라이언트를 설치하는 경우에만 기본 지침이 포함된 **축하합니다.** 페이지가 표시됩니다. 내용을 읽은 후에 **닫기**를 클릭합니다.

문서가 로드되면 다음과 같은 두 가지 새로운 사항을 보게 됩니다.

![Azure Information Protection 빠른 시작 자습서 3단계 - 클라이언트 설치됨](./media/word2016-calloutsv2.png)

- **홈** 탭의 새 **보호** 그룹(**보호** 단추가 포함됨)
    
    **보호** > **도움말 및 피드백**을 클릭하고 **Microsoft Azure Information Protection** 대화 상자에서 클라이언트 상태를 확인합니다. **연결 방식**과 사용자 이름이 표시됩니다. 또한 마지막 연결의 최근 시간 및 날짜와 Information Protection 정책이 설치된 시기도 표시됩니다. 표시된 사용자 이름이 테넌트에 대해 올바른지 확인합니다.

- 리본 아래에 새로운 표시줄인 Information Protection 표시줄이 표시됩니다. 여기에는 Azure Portal에서 봤던 **민감도** 제목과 레이블이 표시됩니다. 

이제 Azure Information Protection의 작동 방식을 살펴볼 준비가 되었습니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|Azure Information Protection 클라이언트 설치 정보|[Azure Information Protection 클라이언트 다운로드 및 설치](./rms-client/install-client-app.md)|
|Azure Information Protection 클라이언트에 대한 관리자 지침|[Azure Information Protection 클라이언트 관리자 가이드](./rms-client/client-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; 2단계](infoprotect-tutorial-step2.md)
[4단계 &#187;](infoprotect-tutorial-step4.md)
