---
title: 클래스 mip RemoveContentHeaderAction
description: 클래스 mip RemoveContentHeaderAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: dc79ebf5d5c7cd35a8fc5ed854315179ed9190f0
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446450"
---
# <a name="class-mipremovecontentheaderaction"></a>클래스 mip::RemoveContentHeaderAction 
문서에서 콘텐츠 헤더를 제거하도록 지정하는 동작 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::vector<std::string>& GetUIElementNames()  |  제거할 UI 요소를 찾는 데 사용되어야 하는 이름 목록을 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getuielementnames"></a>GetUIElementNames
제거할 UI 요소를 찾는 데 사용되어야 하는 이름 목록을 가져옵니다.

  
**반환**: UI 요소 이름의 목록
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.