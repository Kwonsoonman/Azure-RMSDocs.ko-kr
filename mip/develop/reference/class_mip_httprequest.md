---
title: 클래스 mip HttpRequest
description: 클래스 mip HttpRequest에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e838eb247bc00d43da72db1de03304e89a1b1da5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445243"
---
# <a name="class-miphttprequest"></a>클래스 mip::HttpRequest 
단일 HTTP 요청을 설명하는 인터페이스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public HttpRequestType GetRequestType() const  |  요청 유형을 가져옵니다.
 public const std::string& GetUrl() const  |  요청 URL을 가져옵니다.
 public const std::string& GetBody() const  |  요청 본문을 가져옵니다.
public const std::map<std::string, std::string, CaseInsensitiveComparator>& GetHeaders() const  |  요청 헤더를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="httprequesttype"></a>HttpRequestType
요청 유형을 가져옵니다.

  
**반환**: 요청 유형
  
### <a name="geturl"></a>GetUrl
요청 URL을 가져옵니다.

  
**반환**: 요청 URL
  
### <a name="getbody"></a>GetBody
요청 본문을 가져옵니다.

  
**반환**: 요청 본문
  
### <a name="getheaders"></a>GetHeaders
요청 헤더를 가져옵니다.

  
**반환**: 요청 헤더