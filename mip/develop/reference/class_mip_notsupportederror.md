---
title: 클래스 mip NotSupportedError
description: 클래스 mip NotSupportedError에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6053c29463b34b938f919508cb24f4e03f504c47
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446467"
---
# <a name="class-mipnotsupportederror"></a>클래스 mip::NotSupportedError 
애플리케이션에서 요청한 작업이 SDK에서 지원되지 않습니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public char const* what() const  |  오류 메시지를 가져옵니다.
public std::shared_ptr<Error> Clone() const  |  오류를 복제합니다.
 public virtual ErrorType GetErrorType() const  |  오류 유형을 가져옵니다.
 public virtual const std::string& GetErrorName() const  |  오류 이름을 가져옵니다.
 public virtual const std::string& GetMessage() const  |  오류 메시지를 가져옵니다.
 public virtual void SetMessage(const std::string& msg)  |  오류 메시지를 설정합니다.
  
## <a name="members"></a>멤버
  
### <a name="what"></a>what
오류 메시지를 가져옵니다.

  
**반환**: 오류 메시지
  
### <a name="error"></a>오류
오류를 복제합니다.

  
**반환**: 오류 복제본
  
### <a name="errortype"></a>ErrorType
오류 유형을 가져옵니다.

  
**반환**: 오류 유형
  
### <a name="geterrorname"></a>GetErrorName
오류 이름을 가져옵니다.

  
**반환**: 오류 이름
  
### <a name="getmessage"></a>GetMessage
오류 메시지를 가져옵니다.

  
**반환**: 오류 메시지
  
### <a name="setmessage"></a>SetMessage
오류 메시지를 설정합니다.

매개 변수:  
* **msg**: 오류 메시지

