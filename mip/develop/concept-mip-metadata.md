---
title: 개념-MIP SDK에서 메타 데이터 레이블
description: 이 문서는 Microsoft Information Protection SDK에서 생성 되는 메타 데이터를 이해 하는 데 도움이 됩니다.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/08/2018
ms.author: tommos
ms.openlocfilehash: 9f9e4768a01d3d82f7b9563cb907533e53c7a228
ms.sourcegitcommit: 03c9d1131177041e320d1bdbbdd92852a0d1d5cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52156857"
---
# <a name="microsoft-information-protection-sdk---metadata"></a>Microsoft Information Protection SDK-메타 데이터

Microsoft Information Protection SDK 파일에 적용 해야 하는 메타 데이터 집합을 생성 합니다. 이 메타 데이터는 레이블의 표현입니다. 이 문서에서는 SDK가 메일, 문서 및 다른 레코드를 적용 하기 위해 생성 하는 메타 데이터를 설명 합니다.

## <a name="labels"></a>레이블입니다.

Microsoft Information Protection SDK의 레이블 정보의 중요도 설명 하는 정보에 적용 됩니다. 레이블 데이터 파일 또는 레이블 설명 하는 키-값 쌍의 집합의 레코드에 저장 됩니다. 메타 데이터 이름은 다음 구조를 기반으로 합니다.

`DefinedPrefix_ElementType_GlobalIdentifier_AttributeName`

Microsoft Information Protection을 사용 하 여 레이블이 지정 된 데이터에 적용 하는 경우 결과:

`MSIP_Label_GUID_Enabled = true`

GUID에는 조직에서 각 레이블에 대 한 고유 식별자입니다.

## <a name="microsoft-information-protection-sdk-metadata"></a>Microsoft Information Protection SDK 메타 데이터

MIP SDK에는 다음과 같은 메타 데이터 집합이 적용 됩니다.

| 특성 | 형식 또는 값                 | 설명                                                                                                                                                                                                                                        | 필수 |
|-----------|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| **사용 하도록 설정**   | True 또는 False                 | 이 특성은 키-값 쌍이이 집합을 나타내는 분류 된 데이터 항목에 대 한 사용 되는지 여부를 나타냅니다. 일반적으로 DLP 제품 분류 레이블을 식별 하는이 키의 존재 여부를 확인 합니다. | 예       |
| **SiteId**    | GUID                          | Azure Active Directory 테 넌 트 ID                                                                                                                                                                                                                   | 예       |
| **ActionId**  | GUID                          | ActionID는 레이블을 설정 됩니다 될 때마다 변경 됩니다. 감사 로그 활동 데이터 항목으로 레이블 지정의 연결을 허용 하도록 이전 및 새 actionID를 포함 됩니다.                                                                                 | 예       |
| **방법**    | Standard, Privileged, 또는 자동        | Mip::AssignmentMethod 통해 설정                                                                                                                                                                                                                 | 아니요        |
| **SetDate**   | 확장 된 ISO 8601 날짜 형식 | 레이블이 설정 된 경우의 타임 스탬프입니다.                                                                                                                                                                                                              | 아니요        |
| **이름**      | string                        | 레이블 테 넌 트 내에서 고유한 이름입니다. 이름에 표시할와 반드시 일치 하지 않습니다.                                                                                                                                                              | 아니요      |
| **ContentBits** | integer | 파일에 표시 하는 콘텐츠의 형식을 설명 하는 비트 마스크를 적용 되어야 합니다. CONTENT_HEADER CONTENT_FOOTER 0X1 = 0X2, 워터 마크 = 0X4 =
 | 아니요 |

파일에 적용 되 면 결과 아래 표를 비슷합니다.

| Key                                                         | 값                                |
|-------------------------------------------------------------|--------------------------------------|
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled     | true                                 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate     | 2018-11-08T21:13:16-0800             |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method      | 권한                           |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name        | 기밀                         |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId      | cb46c030-1825-4e81-a295-151c039dbf02 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits | 2                                    |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId    | 88124cf5-1340-457d-90e1-0000a9427c99 |

## <a name="extending-metadata-with-custom-attributes"></a>사용자 지정 특성을 사용 하 여 메타 데이터 확장

파일 및 정책 API를 통해 사용자 지정 메타 데이터를 추가할 수 있습니다. 사용자 지정 특성에는 기본 유지 관리 해야 `MSIP_Label_GUID` 접두사입니다. 

예를 들어 Contoso Corporation에서 작성 된 응용 프로그램은 레이블이 지정 된 파일을 생성 하는 시스템을 나타내는 메타 데이터를 적용 해야 합니다. 응용 프로그램에는 접두사로 사용 하 여 새 레이블을 만들 수 있습니다 `MSIP_Label_GUID`합니다. 소프트웨어 공급 업체 이름 및 사용자 지정 특성은 사용자 지정 메타 데이터를 생성할 접두사에 추가 됩니다.

```
MSIP_Label_f048e7b8-f3aa-4857-bf32-a317f4bc3f29_ContosoCorp_GeneratedBy = HRReportingSystem
```

> [!Note]
> 일반 응용 프로그램을 각각에 대 한 최대 길이 대해 호환성을 유지 하는 키와 값은 255 자입니다.

## <a name="versioning"></a>버전 관리

시간이 지남에 따라 특성을 수 도입, 수정 하거나 사용 중지 합니다. 응용 프로그램은 계속 이전 이러한 처리 또는 기업 전체에서 값을 대체 되는 사용 되지 않음된 특성 몇 년이 걸릴 수는 예상 됩니다.

최신 버전을 사용 하 여 특성을 바꿀 때 특성에 버전 접미사를 추가 해야 합니다.

`MSIP_Label_GUID_EnabledV2 = True | False | Condition`

## <a name="email"></a>메일

전자 메일에 적용 하는 메타 데이터 유지 관리는 키/값 쌍 형식 문서와 유사 합니다. 주요 차이점은 호출 하는 단일 전자 메일 헤더에 모든 특성에서 직렬화 되 **MSIP_Labels**합니다. 키/값 쌍을 공백 및 세미콜론으로 구분 되며 새 머리글에 배치 됩니다.

위의 샘플 메타 데이터를 사용합니다.

```
MSIP_Labels: MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled=true; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate=2018-11-08T21:13:16-0800; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method=Privileged; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name=Confidential; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId=cb46c030-1825-4e81-a295-151c039dbf02; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits=2; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId=88124cf5-1340-457d-90e1-0000a9427c99
```
