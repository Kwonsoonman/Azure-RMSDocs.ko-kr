---
title: 클래스 mip MetadataAction
description: 클래스 mip MetadataAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 8f7480775a0226c7161c9ad770184e54427a5084
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47444622"
---
# <a name="class-mipmetadataaction"></a>클래스 mip::MetadataAction 
콘텐츠에 메타데이터 정보를 추가하는 [동작](class_mip_action.md)입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::vector<std::string>& GetMetadataToRemove() const  |  콘텐츠에서 제거해야 하는 메타데이터의 이름 목록을 가져옵니다.
public const std::vector<std::pair<std::string, std::string>>& GetMetadataToAdd() const  |  콘텐츠에 추가해야 하는 메타데이터 이름/값 쌍을 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
콘텐츠에서 제거해야 하는 메타데이터의 이름 목록을 가져옵니다.

  
**반환**: 제거할 문자열 벡터. 메타데이터를 추가하기 전에 메타데이터 제거를 완료해야 합니다.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
콘텐츠에 추가해야 하는 메타데이터 이름/값 쌍을 가져옵니다.

  
**반환**: Const std::vector<std::pair<std::string, std::string>>& 메타데이터를 추가하기 전에 메타데이터 제거를 완료해야 합니다.
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.