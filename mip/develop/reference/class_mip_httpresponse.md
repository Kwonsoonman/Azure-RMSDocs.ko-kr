---
title: 클래스 mip HttpResponse
description: 클래스 mip HttpResponse에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a19ea78b048cafe94501d452bb9c7409237f6ffd
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445360"
---
# <a name="class-miphttpresponse"></a>클래스 mip::HttpResponse 
[HttpDelegate](class_mip_httpdelegate.md)를 재정의할 때 클라이언트 앱에서 구현하는, 단일 HTTP 응답을 설명하는 인터페이스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public int32_t GetStatusCode() const  |  응답 상태 코드를 가져옵니다.
 public const std::string& GetBody() const  |  요청 본문을 가져옵니다.
public const std::map<std::string, std::string, CaseInsensitiveComparator>& GetHeaders() const  |  요청 헤더를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getstatuscode"></a>GetStatusCode
응답 상태 코드를 가져옵니다.

  
**반환**: 상태 코드
  
### <a name="getbody"></a>GetBody
요청 본문을 가져옵니다.

  
**반환**: 요청 본문
  
### <a name="getheaders"></a>GetHeaders
요청 헤더를 가져옵니다.

  
**반환**: 요청 헤더