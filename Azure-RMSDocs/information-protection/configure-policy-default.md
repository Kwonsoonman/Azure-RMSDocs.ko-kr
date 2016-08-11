---
title: "기본 Azure Information Protection 정책 | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/21/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 977cbf2f45cab75aaca9c2a16dd1564c2af2fe4a


---

# 기본 Azure Information Protection 정책

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

다음 정보를 사용하여 Azure Information Protection에 대한 기본 정책을 구성하는 방법을 이해할 수 있습니다. 기본 정책을 수정하는 경우 이러한 값을 참조하여 정책을 기본값으로 반환할 수 있습니다.

## Information Protection 표시줄

제목: **Sensitivity**(민감도)

도구 설명: **정보 민감도는 사용자가 회사 내부 또는 외부의 권한 없는 사용자에게 정보를 노출하는 위험을 식별할 수 있도록 네 가지 고유 수준(공개, 내부, 기밀, 비밀)으로 구성됩니다.**


## 레이블입니다.

다음과 같은 설정의 5가지 기본 레이블이 있습니다.

### **개인**

도구 설명: **개인 전용. 이 데이터는 조직에서 모니터링하지 않습니다. 개인 정보는 비즈니스 관련 데이터를 포함할 수 없습니다.**

색: 연한 녹색

시각적 표시: 없음

조건: 없음

보호: 아니요

----


### **Public**

도구 설명: **이 정보는 내부용이며, 회사 내부 또는 외부의 모든 사용자가 사용할 수 있습니다.**

색: 녹색

시각적 표시: 없음

조건: 없음

보호: 아니요

----

### **Internal**

도구 설명: **이 정보는 모든 직원이 사용할 수 있으며, 권한 있는 고객 및 비즈니스 파트너와 공유할 수 있는 광범위한 내부 비즈니스 데이터를 포함합니다. 내부 정보의 예로는 회사 정책과 대부분의 내부 통신이 있습니다.**

색: 파란색

시각적 표시: 바닥글(문서 및 전자 메일)

조건: 없음

보호: 아니요

----

### **기밀**

도구 설명: **이 데이터는 민감한 비즈니스 정보를 포함합니다. 권한 없는 사용자에게 이 데이터를 노출하면 조직이 해를 입을 수 있습니다. 기밀 정보의 예로는 직원 정보, 개별 고객 프로젝트 또는 계약 및 판매 계정 데이터가 있습니다.**

색: 주황색

시각적 표시: 바닥글(문서 및 전자 메일)

조건: 없음

보호: 아니요

----

### **비밀**

도구 설명: **이 데이터는 보호해야 하는 매우 민감한 비즈니스 정보를 포함합니다. 권한 없는 사용자에게 비밀 데이터를 노출하면 조직이 심각한 해를 입을 수 있습니다. 비밀 정보의 예로는 개인 식별 정보, 고객 레코드, 소스 코드, 사전 발표된 재무 보고서 등이 있습니다.**

색: 빨간색

시각적 표시: 바닥글(문서 및 전자 메일)

조건: 없음

보호: 아니요

----


## 하위 레이블

다음과 같은 설정의 두 가지 기본 하위 레이블이 있습니다.

### 비밀 > **모든 회사**

도구 설명: **이 데이터는 모든 회사 직원에게 허용되는 민감한 비즈니스 정보를 포함합니다.**

시각적 표시: 없음

조건: 없음

보호: 아니요

----

### 비밀 > **내 그룹**

도구 설명: **이 데이터는 직원 그룹에만 허용되는 민감한 비즈니스 정보를 포함합니다.**

시각적 표시: 없음

조건: 없음

보호: 아니요

## 전역 설정

**All documents and emails must have a label (applied automatically or by users)**(모든 문서와 메일에 레이블이 있어야 함(자동으로 적용되거나 사용자에 의해 적용됨)): 끄기

**Select the default label**(기본 레이블 선택): 없음

**Users must provide justification when lowering the sensitivity level (for example, from Confidential to Public)**(민감도를 낮출 때(예: 기밀에서 공개로) 사용자가 근거를 제공해야 함): 끄기

## 다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organization-s-policy) 섹션의 링크를 사용하세요. 



<!--HONumber=Jul16_HO5-->


