---
title: Azure Information Protection 테넌트 키에 대한 작업
description: Azure Information Protection 테넌트 키에 적용되는 다양한 제어 및 책임 수준에 대해 알아봅니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 72607226c594e3b9d8b7fa203c38f9ee86ca4283
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304811"
---
# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Azure Information Protection 테넌트 키에 대한 작업

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection에 대한 테넌트 키를 토폴로지에 따라 Azure Information Protection 테넌트 키에 대한 제어 및 책임 수준이 달라집니다. 두 가지 주요 토폴로지는 **Microsoft-managed** 및 **customer-managed**입니다.

Azure 주요 자격 증명 모음의 테넌트 키를 직접 관리하는 방식은 대개 BYOK(Bring Your Own Key)라고 합니다. 이 시나리오 및 두 테넌트 키 토폴로지 중 선택하는 방법에 대한 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)을 참조하세요.

다음 테이블에는 Azure Information Protection 테넌트 키에 대해 선택한 토폴로지에 따라 수행할 수 있는 작업이 나와 있습니다.

|수명 주기 작업|Microsoft 관리(기본값)|고객 관리(BYOK)|
|-----------------------|-------------------------------|---------------------------|
|테넌트 키 해지|아니요(자동)|예|
|테넌트 키 다시 입력|예|예|
|테넌트 키 백업/복구|아니요|예|
|테넌트 키 내보내기|예|아니요|
|위반 사항에 대응|예|예|

구현한 토폴로지를 파악한 후 다음 링크 중 하나를 선택하여 Azure Information Protection 테넌트 키에 수행할 수 있는 작업에 대한 자세한 내용을 확인하세요.

- [Microsoft 관리 테넌트 키](operations-microsoft-managed-tenant-key.md)
- [고객 관리 테넌트 키](operations-customer-managed-tenant-key.md)

그러나 Active Directory Rights Management Services에서 TPD(신뢰할 수 있는 게시 도메인)를 가져와서 Azure Information Protection 테넌트 키를 만들려는 경우 이 가져오기 작업은 [AD RMS에서 Azure Information Protection으로의 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)에 포함되어 진행됩니다.  

