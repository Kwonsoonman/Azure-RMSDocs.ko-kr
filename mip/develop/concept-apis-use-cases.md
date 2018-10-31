---
title: 개념 - MIP SDK의 API.
description: 이 문서는 MIP SDK에 있는 API의 세 가지 유형, 이 API가 어떻게 관련되는지, 그리고 각 API의 사용 사례를 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: bryanla
ms.openlocfilehash: 5c3f7ee97bfe003f2f215ba95ba196894ab8e197
ms.sourcegitcommit: cc65c3851d4b8169a1a62c83afaf0f75402f7631
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/20/2018
ms.locfileid: "49476190"
---
# <a name="microsoft-information-protection-sdk---api-concepts"></a>Microsoft Information Protection SDK - API 개념

다음 다이어그램에 표시된 것처럼 MIP(Microsoft Information Protection) SDK는 3가지 API로 구성되어 있습니다.

[![MIP SDK API 다이어그램](media/concept-apis-use-cases/mip-sdk-components.png)](media/concept-apis-use-cases/mip-sdk-components.png#lightbox)

응용 프로그램의 요구 사항에 따라 파일 API 계층에서 접속하거나 정책 또는 보호 API 계층과 직접 작업해야 할 수 있습니다.

## <a name="file-api"></a>파일 API

파일 API는 보호 API와 정책 API의 추상화입니다. 서비스에서 레이블을 읽고, 정의된 파일 형식에 레이블을 적용하고, 이 파일 형식에서 레이블을 읽을 수 있는 사용하기 쉬운 인터페이스를 제공합니다. 파일 API는 다음과 같은 모든 서비스 또는 응용 프로그램에서 사용됩니다.

- 지원되는 파일 유형을 사용함
- 레이블을 읽거나 써야 함
- 콘텐츠를 보호하거나 콘텐츠 암호를 해독해야 함

### <a name="file-api-use-cases"></a>파일 API 사용 사례

- 금융 서비스 기관의 소프트웨어 엔지니어가 일반적으로 Excel 형식으로 내보내는 LOB 응용 프로그램의 데이터에 대해 콘텐츠 기반의 레이블을 지정하려고 합니다. 파일 API를 사용하여 사용 가능한 레이블을 나열한 후 지원되는 파일 형식에 해당하는 레이블을 적용할 수 있습니다.

- 조직에서 CASB(클라우드 액세스 보안 브로커)를 개발합니다. 고객이 Microsoft Office 및 PDF 문서에 MIP 레이블을 적용하는 기능을 요청합니다. 파일 API를 사용하면 구성된 레이블 목록을 표시한 다음 고객이 지정된 레이블에 적용할 규칙을 작성하도록 할 수 있습니다. 파일 API는 레이블 ID를 받아들여 고객의 기준을 충족하는 파일에 대해 나머지 작업을 처리합니다.

- 조직에서 SaaS 응용 프로그램을 모니터하여 파일 활동을 확인하는 서비스 기반 데이터 손실 방지 솔루션 또는 CASB를 제공합니다. 데이터가 MIP로 보호되는 경우 데이터 손실 또는 노출의 위험을 줄이기 위해 서비스가 보호된 파일의 콘텐츠를 검색해야 합니다. 서비스가 권한 있는 사용자인 경우 지원되는 형식에 파일 API를 사용하여 다음 작업을 수행할 수 있습니다.

  1. 보호 제거
  2. 제한된 콘텐츠 또는 중요한 콘텐츠가 있는지 콘텐츠 검색
  3. 일반 텍스트 결과 버리기
  4. 위험(찾은 경우)에 대해 보고하거나 위험을 해결하기 위한 서비스 규칙 적용

## <a name="policy-api"></a>정책 API

정책 API 또는 UPE(Universal Policy Engine)는 특정 사용자에 대한 레이블 지정 정책을 검색하는 기능을 소프트웨어 개발자에게 제공합니다. 그런 다음 해당 레이블이 취해야 하는 조치를 “계산”합니다.

정책 API는 개발자가 인터페이스 및 파일 형식을 제어하는 클라이언트 응용 프로그램에서 주로 사용합니다. 또한 레이블 파일이 아니라 사용자 정책을 직접 검색하는 것이 유일한 요구 사항인 경우에 사용됩니다. 

### <a name="policy-api-use-cases"></a>정책 API 사용 사례

- 조직에서 독점 파일 형식을 사용하는 3D 디자인 소프트웨어를 개발합니다. 고객은 MIP를 사용하며 응용 프로그램을 통해 기본적으로 레이블을 적용하는 기능을 원합니다. 소프트웨어 엔지니어는 정책 API 및 사용자 지정 컨트롤을 사용하여 인증된 사용자가 사용할 수 있는 레이블을 표시합니다. 사용자가 레이블을 선택하면 API의 계산 작업 메서드를 호출합니다. API는 메타데이터, 콘텐츠 표시 및 보호에 관해 무엇을 적용해야 할지 정확하게 알려줍니다.

- 조직에서 고객이 중앙 관리 포털을 통해 DLP 정책을 구성할 수 있도록 하는 DLP(데이터 손실 방지) 서비스를 개발합니다. MIP를 사용하고 DLP 정책의 일부로 AIP 레이블을 읽거나 적용해야 하는 고객이 있습니다. 소프트웨어 엔지니어는 정책 API를 사용하여 고객 조직에 대한 레이블 목록을 가져올 수 있습니다. 그런 다음 DLP 규칙의 일부로 이러한 레이블을 읽거나 규칙 작업의 일부로 레이블 정보를 적용할 수 있습니다.

## <a name="protection-api"></a>보호 API

보호 API는 일반 텍스트 스트림을 권한으로 관리되는 스트림으로 변환하거나 그 반대로 변환할 수 있는 기능을 소프트웨어 개발자에게 제공합니다.

### <a name="protection-api-use-cases"></a>보호 API 사용 사례

- 조직에서 독점 파일 형식을 사용하는 3D 인쇄 소프트웨어를 개발합니다. MIP를 사용해 파일을 보호함으로써 특정 사용자만 인쇄할 수 있도록 하고 싶습니다. 보호 API를 사용하면 승인된 이용자만 열거나 인쇄할 수 있도록 파일에 보호를 적용할 수 있습니다. 

- 조직에서 Exchange 사서함 및 .PST 파일을 처리하는 eDiscovery 솔루션을 개발합니다. eDiscovery를 수행하려면 응용 프로그램에서 사용자가 메시지의 암호를 해독할 수 있어야 합니다. 사용자 지정 메시지/RPMSG 파서 및 충분한 권한이 있는 계정을 사용해 RMS API로 다음 작업을 수행할 수 있습니다.
  - 암호화된 파일 암호 해독
  - 콘텐츠 검색
  - 버리기(범위를 벗어나는 경우) 또는 패키징(범위 내에 있는 경우)

## <a name="next-steps"></a>다음 단계

이제 사용 가능한 MIP API 및 그 사용 방법에 대해 전반적으로 이해했으며 계속해서 [프로필 및 엔진 개체 개념](concept-profile-engine-cpp.md)을 알아보세요. 이 개념은 기본적이며 모든 MIP API 집합에 적용됩니다.