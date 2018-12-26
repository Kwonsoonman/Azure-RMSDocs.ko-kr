---
title: 개요 - Microsoft Information Projection SDK
description: MIP(Microsoft Information Protection)은 Microsoft의 분류, 레이블링 및 보호 서비스를 단일 관리 환경 및 SDK(소프트웨어 개발 키트)로 통합한 것입니다.
author: BryanLa
ms.service: information-protection
ms.topic: overview
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 775ae3d524947c8300de0e011b92c2cad106905a
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251729"
---
# <a name="overview"></a>개요

## <a name="microsoft-information-protection"></a>Microsoft Information Protection

MIP(Microsoft Information Protection)은 Microsoft의 분류, 레이블링 및 보호 서비스를 단일 관리 환경 및 SDK(소프트웨어 개발 키트)로 통합한 것입니다. 통합된 관리는 Office 365, Azure Information Protection, Windows Information Protection 및 기타 Microsoft 서비스에서 제공됩니다. 타사에서는 이 SDK를 사용해 일관된 표준 데이터 레이블 지정 스키마와 보호 서비스를 사용하는 애플리케이션과 통합할 수 있습니다.

* [Office 365 보안 및 준수 센터란?](https://docs.microsoft.com/office365/securitycompliance/)
* [Azure Information Protection이란?](/azure/information-protection/understand-explore/what-is-information-protection)
* [Azure Information Protection에서 보호가 작동하는 방식](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

## <a name="microsoft-information-protection-sdk"></a>Microsoft Information Protection SDK

MIP SDK는 Office 365 보안 및 준수 센터의 레이블 지정 및 보호 서비스를 타사 애플리케이션 및 서비스에 표시합니다. 개발자는 이 SDK를 사용하여 레이블 및 보호를 파일에 적용하기 위한 기본 지원을 빌드할 수 있습니다. 개발자는 특정 레이블이 감지된 경우 어떤 조치를 취해야 하지 판단하고, MIP로 암호화된 정보를 근거로 판단할 수 있습니다. 

Microsoft 서비스 제품군 간 정보에 적용된 레이블과 보호는 **일관됩니다**. 이러한 일관성 덕분에 MIP를 지원하는 애플리케이션 및 서비스가 예측 가능한 공통된 방식으로 레이블을 읽고 쓸 수 있습니다.

MIP SDK의 수준 높은 사용 사례는 다음과 같습니다.

* 내보낼 때 파일에 분류 레이블을 적용하는 사업 부문 애플리케이션
* CAD/CAM 설계 애플리케이션은 Microsoft Information Protection 레이블을 기본적으로 지원합니다.
* 클라우드 액세스 보안 브로커 또는 데이터 손실 방지 솔루션이 Azure Information Protection을 사용하여 암호화된 데이터를 근거로 판단합니다.

자세한 목록을 보려면 [API 개념](concept-apis-use-cases.md)을 검토하세요.

## <a name="next-steps"></a>다음 단계

이제 SDK를 시작할 준비가 되었습니다. 수행해야 하는 첫 번째는 [MIP SDK 설정 및 구성 단계를 완료](setup-configure-mip.md)하여 Office 365 구독 및 클라이언트 머신이 올바르게 설정되어 있는지 확인하는 것입니다.

