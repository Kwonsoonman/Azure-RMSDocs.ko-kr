---
title: 클래스 mip AddWatermarkAction
description: 클래스 mip AddWatermarkAction에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f49bd7aa16ae12aef240d05fff6acf507ddc341d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446093"
---
# <a name="class-mipaddwatermarkaction"></a>클래스 mip::AddWatermarkAction 
워터마크를 추가하도록 지정하는 동작 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetUIElementName()  |  워터마크 요소를 표시하는 데 사용되는 API입니다.
 public WatermarkLayout GetLayout() const  |  워터마크 레이아웃을 가져오는 데 사용되는 API입니다.
 public const std::string& GetText() const  |  워터마크로 이동하려는 텍스트를 가져옵니다.
 public const std::string& GetFontName() const  |  워터마크를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.
 public int GetFontSize() const  |  워터마크를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.
 public const std::string& GetFontColor() const  |  워터마크를 표시하는 데 사용되는 글꼴 색을 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getuielementname"></a>GetUIElementName
워터마크 요소를 표시하는 데 사용되는 API입니다.

  
**반환**: 워터마크를 포함하는 UI 요소에 사용해야 하는 이름. 워터마크를 제거해야 하는 경우 동일한 이름이 RemoveWatermarkingAction에 반환됩니다.
  
### <a name="getlayout"></a>GetLayout
워터마크 레이아웃을 가져오는 데 사용되는 API입니다.

  
**반환**: WatermarkLayout. 열거형 HORIZONTAL|DIAGONAL 형식의 워터마크 레이아웃입니다. ,
  
### <a name="gettext"></a>GetText
워터마크로 이동하려는 텍스트를 가져옵니다.

  
**반환**: 콘텐츠 헤더 텍스트
  
### <a name="getfontname"></a>GetFontName
워터마크를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.

  
**반환**: 글꼴 이름. 정책에서 아무것도 설정하지 않은 경우 기본값은 Calibri입니다.
  
### <a name="getfontsize"></a>GetFontSize
워터마크를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.

  
**반환**: 정수 글꼴 크기
  
### <a name="getfontcolor"></a>GetFontColor
워터마크를 표시하는 데 사용되는 글꼴 색을 가져옵니다.

  
**반환**: 문자열 글꼴 색(예: "#000000")
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.