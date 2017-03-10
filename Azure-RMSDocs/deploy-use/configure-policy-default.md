---
title: "Azure Information Protection의 기본 정책"
description: "Azure Information Protection에 대한 기본 정책을 구성하는 방법을 설명합니다. 기본 정책을 수정하는 경우 이러한 값을 참조하여 정책을 기본값으로 반환할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
ms.openlocfilehash: 08b110d46b41da6582ed59363f6f6d66450c6ec2
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="the-default-azure-information-protection-policy"></a>기본 Azure Information Protection 정책

>*적용 대상: Azure Information Protection*

다음 정보를 사용하여 Azure Information Protection에 대한 기본 정책을 구성하는 방법을 이해할 수 있습니다. 기본 정책을 수정하는 경우 이러한 값을 참조하여 정책을 기본값으로 반환할 수 있습니다.

## <a name="information-protection-bar"></a>Information Protection 표시줄

|설정|값|
|-------------------------------|---------------------------|
|제목|민감도|
|도구 설명|정보 민감도는 사용자가 회사 내부 또는 외부의 권한 없는 사용자에게 정보를 노출하는 위험을 식별할 수 있도록 네 가지 고유 수준(공개, 내부, 기밀, 비밀)으로 구성됩니다.|

## <a name="labels"></a>레이블입니다.

|Label|도구 설명|설정|
|-------------------------------|---------------------------|-----------------|
|개인|개인 전용. 이 데이터는 조직에서 모니터링하지 않습니다. 개인 정보는 비즈니스 관련 데이터를 포함할 수 없습니다.|**사용**: 켜기 <br /><br />**색**: 연한 녹색<br /><br />**시각적 표시**: 끄기 <br /><br />**조건**: 없음<br /><br />**보호**: 없음|
|Public|이 정보는 내부용이며, 회사 내부 또는 외부의 모든 사용자가 사용할 수 있습니다.|**사용**: 켜기 <br /><br />**색**: 녹색<br /><br />**시각적 표시**: 끄기<br /><br />**조건**: 없음<br /><br />**보호**: 없음|
|Internal|이 정보는 모든 직원이 사용할 수 있으며, 권한 있는 고객 및 비즈니스 파트너와 공유할 수 있는 광범위한 내부 비즈니스 데이터를 포함합니다. 내부 정보의 예로는 회사 정책과 대부분의 내부 통신이 있습니다.|**사용**: 켜기 <br /><br />**색**: 파란색 <br /><br />**시각적 표시**: 바닥글(문서 및 메일)<br /><br />**조건**: 없음<br /><br />**보호**: 없음|
|기밀|이 데이터는 민감한 비즈니스 정보를 포함합니다. 권한 없는 사용자에게 이 데이터를 노출하면 조직이 해를 입을 수 있습니다. 기밀 정보의 예로는 직원 정보, 개별 고객 프로젝트 또는 계약 및 판매 계정 데이터가 있습니다.|**사용**: 켜기 <br /><br />**색**: 주황색<br /><br />**시각적 표시**: 바닥글(문서 및 메일)<br /><br />**조건**: 없음<br /><br />**보호**: 없음|
|비밀|이 데이터는 보호해야 하는 매우 민감한 비즈니스 정보를 포함합니다. 권한 없는 사용자에게 비밀 데이터를 노출하면 조직이 심각한 해를 입을 수 있습니다. 비밀 정보의 예로는 개인 식별 정보, 고객 레코드, 소스 코드, 사전 발표된 재무 보고서 등이 있습니다.|**사용**: 켜기 <br /><br />**색**: 빨간색<br /><br />**시각적 표시**: 바닥글(문서 및 메일)<br /><br />**조건**: 없음<br /><br />**보호**: 없음|

## <a name="sub-labels"></a>하위 레이블

|Label|도구 설명|설정|
|-------------------------------|---------------------------|-----------------|
|비밀 \ 모든 회사|이 데이터는 모든 회사 직원에게 허용되는 민감한 비즈니스 정보를 포함합니다.|**사용**: 켜기 <br /><br />**시각적 표시**: 끄기<br /><br />**조건**: 없음<br /><br />**보호**: 없음|
|비밀 \ 내 그룹|이 데이터는 직원 그룹에만 허용되는 민감한 비즈니스 정보를 포함합니다.|**사용**: 켜기 <br /><br />**시각적 표시**: 끄기<br /><br />**조건**: 없음<br /><br />**보호**: 없음|

## <a name="global-settings"></a>전역 설정

|설정|값|
|-------------------------------|---------------------------|
|All documents and emails must have a label (applied automatically or by users)(모든 문서와 메일에 레이블이 있어야 함(자동으로 적용되거나 사용자에 의해 적용됨))|꺼짐|
|Select the default label(기본 레이블 선택)|없음|
|Users must provide justification to set a lower classification label, remove a label, or remove protection(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함)|꺼짐|


## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요. 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]