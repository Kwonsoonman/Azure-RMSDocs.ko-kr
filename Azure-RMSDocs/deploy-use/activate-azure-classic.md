---
title: "Azure 클래식 포털에서 Azure Rights Management를 활성화하는 방법 | Azure Information Protection"
description: "Azure Portal 액세스 권한이 있는 경우의 Azure Rights Management 서비스 활성화 지침을 제공합니다. 예를 들어 Enterprise Mobility Suite 구독이 있거나 Azure Information Protection Premium 구독이 있는 경우입니다."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 565f2479fe1d41aa051dd64752413eb72d644535
ms.openlocfilehash: 74aac58a7b523f98ef627831830577d4fde7d5af


---

# Azure 클래식 포털에서 Azure 권한 관리를 활성화하는 방법

>*적용 대상: Azure Information Protection*


Azure 포털에 액세스할 수 있는 경우 다음 지침을 따르세요. 예를 들어 Enterprise Mobility Suite 구독이 있거나 Azure Information Protection Premium 구독이 있는 경우입니다.

> [!TIP]
> 2분 동영상 시청: [Azure RMS를 활성화하는 방법](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms)

1.  Azure 계정에 등록한 후 [Azure 클래식 포털에 로그인](http://go.microsoft.com/fwlink/p/?LinkID=275081)합니다. Azure Rights Management를 포함하는 구독을 가져오는 데 사용한 계정과 같은 전역 관리자 계정을 사용하세요.

2.  왼쪽 창에서 **ACTIVE DIRECTORY**를 클릭합니다.

3.  **Active Directory** 페이지에서 **Rights Management**를 클릭합니다.

4.  [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]에 대해 관리할 디렉터리를 선택하고 **활성화**를 클릭한 다음 작업을 확인합니다.

    > [!NOTE]
    >참고: 활성화 오류가 표시되는 경우 서비스 계획 또는 제품 버전에 Azure Information Protection의 Azure Rights Management 서비스가 포함되지 않았기 때문일 수 있습니다.
    >
    >Azure Rights Management Service를 활성화하려면 [Azure Information Protection Premium plan](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing)(Azure Information Protection Premium 계획) 또는 [Rights Management가 포함된 Office 365 계획](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)이 있어야 합니다. 이 문제에 대한 도움이 필요한 경우 [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS)으로 전자 메일 메시지를 보내 주세요.


이제 **Rights Management 상태** 가 **활성** 으로 표시되고 **활성화** 옵션이 **비활성화**로 바뀝니다.

## Azure 클래식 포털의 Rights Management 상태 값 및 설명
Rights Management 서비스가 사용되도록 설정되고 사용할 준비가 되었음을 나타내는 **활성** 상태뿐만 아니라 **비활성**, **사용할 수 없음**또는 **권한 없음**도 확인할 수 있습니다.

|상태 값|설명|
|----------------|---------------|
|**활성**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 가 사용할 준비가 되었습니다.|
|**비활성**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 를 사용할 수 없으며 조직에서 파일을 보호하려면 활성화해야 합니다.|
|**Unavailable**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 서비스가 중지되었습니다. 나중에 다시 시도하세요.|
|**권한 없음**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 서비스 상태를 볼 권한이 없습니다. 예를 들어 계정이 잠겼거나 선택한 테넌트에 대한 전역 관리자가 아닙니다.|

## 다음 단계
[Azure 권한 관리 활성화](activate-service.md)로 돌아갑니다.


<!--HONumber=Oct16_HO1-->


