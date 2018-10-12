---
title: 클래스 mip JustifyAction
description: 클래스 mip JustifyAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: db61b9c718ae7ddbe1441d379e5a4b6b95d69951
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445294"
---
# <a name="class-mipjustifyaction"></a>클래스 mip::JustifyAction 
근거 제공 [동작](class_mip_action.md)에는 레이블 다운그레이드에 대한 근거 제공이 필요하고 실행 상태에서 응답을 설정해야 합니다.
  
**참고 항목**: [mip::ExecutionState::IsDowngradeJustified](class_mip_executionstate.md#isdowngradejustified)
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.