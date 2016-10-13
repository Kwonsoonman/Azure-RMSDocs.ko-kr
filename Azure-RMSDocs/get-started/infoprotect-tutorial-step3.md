---
title: "빠른 시작 자습서 3단계 | Azure Information Protection"
description: "조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 3단계로 약 30분 만에 완료해야 합니다."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: b5c87669c965d1e67b47dcfbd8ba97f1da41d104
ms.openlocfilehash: 042e168452d2b5cbc1eeec4fc06a3b0f137a5caf


---

# 3단계: 클라이언트 및 응용 프로그램 설치 

>*적용 대상: Azure Information Protection*

이 단계에서는 방금 구성한 정책이 Windows PC에 다운로드되고 Office 응용 프로그램에 레이블이 표시되도록 먼저 Azure Information Protection 클라이언트를 설치합니다.

두 번째로 문서를 메일로 안전하게 공유하고 문서 사용 방식을 추적할 수 있도록 Rights Management 공유 응용 프로그램을 설치합니다. 

두 설치 모두 Office 응용 프로그램과 통합되며, 현재 설치는 개별적으로 해야 합니다.


## Azure Information Protection 클라이언트 설치

1. Office가 설치된(그러나 Word는 현재 열려 있지 않은) PC에서 Microsoft 다운로드 센터로부터 [Azure Information Protection 클라이언트를 다운로드](https://www.microsoft.com/en-us/download/details.aspx?id=53018)합니다. 

2. **AzInfoProtection.exe**를 실행하고 메시지의 지시에 따라 클라이언트를 설치합니다.

    이 자습서에서는 방금 구성한 정책이 Azure에서 다운로드되고 설치된 경우 데모 정책을 바꿀 것이므로 데모 정책 설치 옵션의 선택 여부는 중요하지 않습니다. 그러나 Azure Information Protection에 연결하지 않고 기본 레이블을 경험해 보려는 경우 데모 정책 옵션을 사용할 수 있습니다. 

## Rights Management 공유 응용 프로그램 설치 

1. Microsoft 웹 사이트의 [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) 페이지로 이동합니다.

2. **컴퓨터** 섹션에서 **Windows용 RMS 앱** 의 아이콘을 클릭하고 **Setup.exe** 파일을 저장하여 Microsoft Rights Management 공유 응용 프로그램을 설치합니다.

3. **Microsoft RMS 설치** 페이지에서 **다음**을 클릭하고 설치가 완료될 때까지 기다립니다. 그런 다음 컴퓨터를 다시 시작하라는 메시지가 표시되면 **다시 시작**을 클릭하거나, **닫기**를 클릭하여 설치를 완료합니다.


## 설치 확인

Word와 새 빈 문서를 열어 설치가 완료되었는지 확인합니다(이번에는 저장하지 않음). 사용자 이름과 암호를 입력하라는 메시지가 표시되면 전역 관리자 계정의 세부 정보를 입력합니다. 

문서가 로드되면 다음과 같은 세 가지 새로운 사항을 보게 됩니다.

- **홈** 탭의 새 **보호** 그룹과 **보호**라는 레이블이 지정된 단추

    **보호** > **도움말 및 피드백**을 클릭하고 **Microsoft Azure Information Protection** 대화 상자에서 클라이언트 상태를 확인합니다. **Information Protection policy is installed**(Information Protection 정책이 설치됨)와 최근 연결 시간이 표시되어야 합니다. 표시된 사용자 이름이 테넌트에 대해 올바른지 확인합니다.

- **홈** 탭의 새 **RMS** 그룹과 **보호된 항목 공유**라는 레이블이 지정된 단추

- 리본 아래에 새로운 표시줄인 Information Protection 표시줄이 표시됩니다. 제목 **Sensitivity**(민감도)와 구성한 기본 레이블 **Internal**(내부)이 표시됩니다. 
    
    ![Azure Information Protection 빠른 시작 자습서 3단계 - 클라이언트 설치됨](../media/word2013-callouts2.png)

이제 Azure Information Protection의 작동 방식을 살펴볼 준비가 되었습니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|Azure Information Protection 클라이언트 설치 정보|[Azure Information Protection 클라이언트 설치](../rms-client/info-protect-client.md)|
|Rights Management 공유 응용 프로그램 설치 정보 및 사용자 지침 정보|[Rights Management 공유 응용 프로그램 사용자 가이드](../rms-client/sharing-app-user-guide.md)|
|스크립트를 이용한 Windows용 Rights Management 공유 응용 프로그램 설치 정보 및 자세한 기술 정보|[Rights Management 공유 응용 프로그램 관리자 가이드](../rms-client/sharing-app-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; 2단계](infoprotect-tutorial-step2.md)
[4단계 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Sep16_HO4-->


