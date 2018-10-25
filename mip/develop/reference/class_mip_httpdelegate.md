---
title: 클래스 mip HttpDelegate
description: 클래스 mip HttpDelegate에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3e55f9aff5a9ebd97731ec21e408a33f22905648
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445373"
---
# <a name="class-miphttpdelegate"></a>클래스 mip::HttpDelegate 
HTTP 처리를 재정의하기 위한 인터페이스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public std::shared_ptr<HttpResponse> Send(const std::shared_ptr<HttpRequest>& request, const std::shared_ptr<void>& context)  |  HTTP 요청을 보냅니다.
  
## <a name="members"></a>멤버
  
### <a name="httpresponse"></a>HttpResponse
HTTP 요청을 보냅니다.

매개 변수:  
* **request**: HTTP 요청 


* **context**: 이 HTTP 요청을 발생시킨, API에 전달된 동일한 불투명 클라이언트 컨텍스트



  
**반환**: HTTP 응답