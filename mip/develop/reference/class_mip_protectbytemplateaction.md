---
title: 클래스 mip ProtectByTemplateAction
description: 클래스 mip ProtectByTemplateAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: cb5f42b25e6f499bc09f3f460ec4a253627b45a5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445464"
---
# <a name="class-mipprotectbytemplateaction"></a>클래스 mip::ProtectByTemplateAction 
문서에 템플릿에 의한 보호를 추가하도록 지정하는 동작 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetTemplateId() const  |  동작과 연결된 보호 템플릿 ID를 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="gettemplateid"></a>GetTemplateId
동작과 연결된 보호 템플릿 ID를 가져옵니다.

  
**반환**: 보호 템플릿 ID
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.