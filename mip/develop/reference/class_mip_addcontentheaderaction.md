---
title: 클래스 mip AddContentHeaderAction
description: 클래스 mip AddContentHeaderAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: bc60fe32005a0c6bc8088ab7687a3f711ae7a99a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445651"
---
# <a name="class-mipaddcontentheaderaction"></a>클래스 mip::AddContentHeaderAction 
콘텐츠 헤더를 추가하도록 지정하는 동작 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetUIElementName()  |  콘텐츠 헤더 요소를 표시하는 데 사용되는 API입니다.
 public const std::string& GetText() const  |  콘텐츠 헤더로 이동하려는 텍스트를 가져옵니다.
 public const std::string& GetFontName() const  |  콘텐츠 헤더를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.
 public int GetFontSize() const  |  콘텐츠 헤더를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.
 public const std::string& GetFontColor() const  |  콘텐츠 헤더를 표시하는 데 사용되는 글꼴 색을 가져옵니다.
 public ContentMarkAlignment GetAlignment() const  |  헤더의 맞춤을 가져옵니다.
 public int GetMargin() const  |  아래쪽의 헤더 여백을 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getuielementname"></a>GetUIElementName
콘텐츠 헤더 요소를 표시하는 데 사용되는 API입니다.

  
**반환**: 콘텐츠 헤더를 포함하는 UI 요소에 사용해야 하는 이름. 콘텐츠 헤더를 제거해야 하는 경우 동일한 이름이 [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)에 반환됩니다.
  
### <a name="gettext"></a>GetText
콘텐츠 헤더로 이동하려는 텍스트를 가져옵니다.

  
**반환**: 콘텐츠 헤더 텍스트
  
### <a name="getfontname"></a>GetFontName
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.

  
**반환**: 글꼴 이름. 정책에서 아무것도 설정하지 않은 경우 기본값은 Calibri입니다.
  
### <a name="getfontsize"></a>GetFontSize
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.

  
**반환**: 정수 글꼴 크기
  
### <a name="getfontcolor"></a>GetFontColor
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 색을 가져옵니다.

  
**반환**: 문자열 글꼴 색(예: #000000")
  
### <a name="getalignment"></a>GetAlignment
헤더의 맞춤을 가져옵니다.

  
**반환**: ContentMarkAlignment 열거자, LEFT|RIGHT|CENTER 
  
**참고 항목**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
아래쪽의 헤더 여백을 가져옵니다.

  
**반환**: 문서 아래쪽의 여백을 나타내는 정수(예: 10mm)
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.