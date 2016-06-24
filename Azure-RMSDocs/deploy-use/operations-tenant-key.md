---
# required metadata

title: Azure 권한 관리 테넌트 키에 대한 작업 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리 테넌트 키에 대한 작업

*적용 대상: Azure 권한 관리, Office 365*

Microsoft Azure 권한 관리(Azure RMS) 테넌트 키를 구현한 후의 제어 및 책임 수준은 테넌트 키 토폴로지(Microsoft 관리 또는 고객 관리)에 따라 다릅니다.

테넌트 키를 직접 관리하는 방식은 대개 BYOK(Bring Your Own Key)라고 합니다. 이 시나리오와, 두 테넌트 키 토폴로지 중에서 선택하는 방법에 대한 자세한 내용은 [Azure 권한 관리 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md) 항목을 참조하세요..

다음 표에는 Azure RMS 테넌트 키에 대해 선택한 토폴로지에 따라 수행할 수 있는 작업이 나와 있습니다.

|수명 주기 작업|Microsoft 관리(기본값)|고객 관리(BYOK)|
|-----------------------|-------------------------------|---------------------------|
|테넌트 키 해지|아니요(자동)|아니요(자동)|
|테넌트 키 다시 입력|예|예|
|테넌트 키 백업/복구|아니요|예|
|테넌트 키 내보내기|예|아니요|
|위반 사항에 대응|예|예|

구현한 토폴로지를 파악한 후 다음 중 하나를 선택하여 Azure RMS 테넌트 키에 수행할 수 있는 이러한 작업에 대한 자세한 내용을 확인하세요.


- [Microsoft 관리 테넌트 키](operations-microsoft-managed-tenant-key.md)
- [고객 관리 테넌트 키](operations-customer-managed-tenant-key.md)






<!--HONumber=Apr16_HO4-->


