---
title: 클래스 mip CustomAction
description: 클래스 mip CustomAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a94a41c0e7f7848201e2af44187cce2540579b27
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47444727"
---
# <a name="class-mipcustomaction"></a>클래스 mip::CustomAction 
[CustomAction](class_mip_customaction.md)은 동작의 모든 하위 속성을 속성 모음으로 캡처하는 일반 동작 클래스입니다. 호출자는 동작의 의미를 이해해야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetName() const  |  작업 이름을 가져옵니다.
public const std::vector<std::pair<std::string, std::string>>& GetProperties() const  |  속성 키 값 쌍 목록을 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getname"></a>GetName
작업 이름을 가져옵니다.

  
**반환**: 작업 이름이 있으면 작업 이름, 없으면 빈 문자열
  
### <a name="getproperties"></a>GetProperties
속성 키 값 쌍 목록을 가져옵니다.

  
**반환**: 키 값 쌍 목록.
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.