---
title: 클래스 mip PolicyHandler
description: 클래스 mip PolicyHandler에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 23de5616558a298189cb885727d69a20373a3609
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445940"
---
# <a name="class-mippolicyhandler"></a>클래스 mip::PolicyHandler 
이 클래스는 파일에 대한 모든 정책 처리기 함수의 인터페이스를 제공합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public std::shared_ptr<ContentLabel> GetSensitivityLabel(const ExecutionState& state)  |  기존 콘텐츠에서 민감도 레이블을 가져옵니다.
public std::vector<std::shared_ptr<Action>> ComputeActions(const ExecutionState& state)  |  제공된 상태에 따라 처리기에서 규칙을 실행하고 실행할 작업 목록을 반환합니다.
 public void NotifyCommittedActions(const ExecutionState& state)  |  계산된 작업이 적용되고 데이터가 디스크에 커밋되고 나면 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="contentlabel"></a>ContentLabel
기존 콘텐츠에서 민감도 레이블을 가져옵니다.

매개 변수:  
* **state**: 콘텐츠의 현재 상태 



  
**반환**: 현재 콘텐츠에 적용된 레이블. 레이블이 지정되지 않은 경우 빈 값을 반환합니다.
  
### <a name="action"></a>작업
제공된 상태에 따라 처리기에서 규칙을 실행하고 실행할 작업 목록을 반환합니다.

매개 변수:  
* **state**: 규칙이 실행 중인 콘텐츠의 현재 실행 상태. 



  
**반환**: 콘텐츠에 적용되어야 하는 동작 목록.
  
### <a name="notifycommittedactions"></a>NotifyCommittedActions
계산된 작업이 적용되고 데이터가 디스크에 커밋되고 나면 호출됩니다.

매개 변수:  
* **state**: 작업이 커밋된 후 콘텐츠의 현재 실행 상태 


: 이 호출은 감사 이벤트를 보냅니다.