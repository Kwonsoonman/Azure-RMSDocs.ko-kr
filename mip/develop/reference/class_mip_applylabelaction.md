---
title: 클래스 mip ApplyLabelAction
description: 클래스 mip ApplyLabelAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06a17ef1e60503cfb7d690bea9bb72316544f16d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445770"
---
# <a name="class-mipapplylabelaction"></a>class mip::ApplyLabelAction 
레이블 적용 동작에 따라 호출 애플리케이션은 특정 레이블을 적용해야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetLabelId() const  |  필요한 레이블 ID를 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getlabelid"></a>GetLabelId
필요한 레이블 ID를 가져옵니다.

  
**반환**: 레이블 ID
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.