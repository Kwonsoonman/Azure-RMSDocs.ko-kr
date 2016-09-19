---
title: "Azure Information Protection 빠른 시작 자습서 3단계 | Azure Information Protection"
description: "15분 이내에 완료할 수 있는 4단계를 통해 조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 3단계입니다."
author: cabailey
manager: mbaldwin
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: 6bbac611f9c8bba96fbbba69e8044e494134d792
ms.openlocfilehash: f5e15870a3a67f67261db9c3d1d735c126f48ee2


---

# 3단계: Azure Information Protection 클라이언트 설치 

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

이 단계에서는 방금 구성한 정책이 Windows PC에 다운로드되고 Office 응용 프로그램에 레이블이 표시되도록 Azure Information Protection 클라이언트를 설치합니다. 

1. Office가 설치된(그러나 Word는 현재 열려 있지 않은) PC에서 Microsoft 다운로드 센터로부터 [Azure Information Protection 클라이언트를 다운로드](https://www.microsoft.com/en-us/download/details.aspx?id=53018)합니다. 

2. **AzInfoProtection.exe**를 실행하고 메시지의 지시에 따라 클라이언트를 설치합니다.

    이 자습서에서는 방금 구성한 정책이 Azure에서 다운로드되고 설치된 경우 데모 정책을 바꿀 것이므로 데모 정책 설치 옵션의 선택 여부는 중요하지 않습니다. 그러나 Azure Information Protection에 연결하지 않고 기본 레이블을 경험해 보려는 경우 데모 정책 옵션을 사용할 수 있습니다. 

3. Word와 새 문서를 열어 클라이언트가 설치되었는지 확인합니다(이번에는 저장하지 않음). 사용자 이름과 암호를 입력하라는 메시지가 표시되면 전역 관리자 계정의 세부 정보를 입력합니다. 문서가 로드되면 다음과 같은 두 가지 새로운 사항을 보게 됩니다.

    - **홈** 탭의 새 **보호** 그룹과 **보호**라는 레이블이 지정된 단추

        **보호** > **도움말 및 피드백**을 클릭하고 **Microsoft Azure Information Protection** 대화 상자에서 클라이언트 상태를 확인합니다. **Information Protection policy is installed**(Information Protection 정책이 설치됨)와 최근 연결 시간이 표시되어야 합니다. 표시된 사용자 이름이 테넌트에 대해 올바른지 확인합니다.

    - 리본 아래에 새로운 표시줄인 Information Protection 표시줄이 표시됩니다. 제목 **Sensitivity**(민감도)와 구성한 기본 레이블 **Internal**(내부)이 표시됩니다. 
    
        ![Azure Information Protection 빠른 시작 자습서 3단계 - 클라이언트 설치됨](../media/word2013-callouts2.png)

이제 마지막 단계인 실제 분류, 레이블 지정 및 보호 작동 방식을 확인할 준비가 되었습니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|클라이언트 설치 정보|[Azure Information Protection 클라이언트 설치](info-protect-client.md)|


>[!div class="step-by-step"]
[&#171; 2단계](infoprotect-tutorial-step2.md)
[4단계 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Sep16_HO1-->


