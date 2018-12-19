---
title: Azure Information Protection을 사용하는 일반적인 시나리오에 대한 방법 지침입니다.
description: Azure Information Protection에서 사용하여 조직의 데이터를 분류 및 보호하는 사용 사례를 식별합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7986648999a830985c4dbd1f31855bb222a443c2
ms.sourcegitcommit: 2a1c0882d2b0400f4da6370dbc1830df09867e3d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53218377"
---
# <a name="how-to-guides-for-common-scenarios-that-use-azure-information-protection"></a>Azure Information Protection을 사용하는 일반적인 시나리오에 대한 방법 가이드

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection을 사용하여 여러 가지 방법으로 조직의 문서 및 이메일을 분류하고 필요에 따라 보호할 수 있습니다. 

가장 성공적인 배포는 조직에 최고의 비즈니스 혜택을 제공하는 구체적인 사용 사례를 식별하는 경우입니다. 다음과 같은 일반적인 시나리오 및 지침 목록을 사용하여 배포를 순조롭게 진행하세요.

## <a name="common-scenarios"></a>일반적인 시나리오

|시나리오: 수행하려는 작업...|지침|
|----------------|---------------|
|조직이 온-프레미스에 저장하는 중요한 정보 찾기|[빠른 시작 온-프레미스에 저장된 파일에 있는 중요한 정보 찾기](quickstart-findsensitiveinfo.md)|
|사용자가 중요한 정보를 포함하는 이메일을 쉽게 보호하도록 지원|[빠른 시작 사용자가 중요한 정보가 포함된 이메일을 쉽게 보호하도록 레이블 구성](quickstart-label-dnf-protectedemail.md)|
|사용자가 생성 및 편집된 데이터를 쉽게 분류하고, 중요한 정보가 포함된 경우 보호하도록 지원| [자습서: 정책 편집 및 새 레이블 만들기](infoprotect-quick-start-tutorial.md)|
|사용자가 보호된 문서로 쉽게 공동 작업을 수행하도록 지원|[Azure Information Protection을 사용하여 보안 문서 공동 작업 구성](secure-collaboration-documents.md)|
|조직 외부에서 전송된 사용자의 이메일을 자동으로 보호| [Azure Information Protection 레이블에 대한 메일 흐름 규칙 구성](configure-exo-rules.md)
|온-프레미스 데이터 저장소의 기존 데이터를 자동으로 분류하고 보호|[Azure Information Protection 스캐너 배포](deploy-aip-scanner.md)|
|고유한 키를 사용하여 조직의 데이터 보호| [테넌트 키 계획 및 구현](plan-implement-tenant-key.md)|
|AD RMS에서 마이그레이션|[AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)|

## <a name="additional-deployment-instructions"></a>추가 배포 지침

[Azure Information Protection 기술 블로그](https://aka.ms/AIPblog)에는 고객 환경 엔지니어링 팀의 추가적인 단계별 지침이 있습니다. 예를 들면 다음과 같습니다.

- [PDF 및 Adobe Acrobat Reader를 보호하는 Azure Information Protection을 사용하여 PDF 및 Adobe Acrobat Reader 확인](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Using-Azure-Information-Protection-to-protect-PDF-s-and-Adobe/ba-p/282010)

- [레이블을 구성하기 전이라도 AIP를 사용하여 중요한 데이터의 카탈로그 작업 수행!](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Cataloging-your-Sensitive-Data-with-AIP-Even-Before-Configuring/ba-p/267241)

- [Azure Information Protection 스캐너 빠른 설치](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-Scanner-Express-Installation/ba-p/265424)

- [AIP 스캐너(AIP 프리미엄 P1)를 사용하여 중요한 데이터 검색](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discovery-of-Sensitive-Data-Using-the-AIP-Scanner-AIP-Premium-P1/ba-p/252040)

## <a name="next-steps"></a>다음 단계

사용자 시나리오가 목록에 없나요? 계획 및 배포 단계의 전체 목록을 보려면 [배포 로드맵](deployment-roadmap.md)을 확인하세요.

Azure Information Protection을 처음 사용하는 경우 배포를 시작하기 전에 [Azure Information Protection이란?](what-is-information-protection.md)에서 빠른 서비스 소개를 검토하세요.
