---
title: 클래스 mip JustificationRequiredError
description: 클래스 mip JustificationRequiredError에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 059d139fc5222fd5f1865c66834519347e23a5a9
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445991"
---
# <a name="class-mipjustificationrequirederror"></a>클래스 mip::JustificationRequiredError 
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual std::shared_ptr<Error> Clone() const  |  오류를 복제합니다.
 public char const* what() const  |  오류 메시지를 가져옵니다.
 public virtual ErrorType GetErrorType() const  |  오류 유형을 가져옵니다.
 public virtual const std::string& GetErrorName() const  |  오류 이름을 가져옵니다.
 public virtual const std::string& GetMessage() const  |  오류 메시지를 가져옵니다.
 public virtual void SetMessage(const std::string& msg)  |  오류 메시지를 설정합니다.
  
## <a name="members"></a>멤버
  
### <a name="error"></a>오류
오류를 복제합니다.

  
**반환**: 오류 복제본
  
### <a name="what"></a>what
오류 메시지를 가져옵니다.

  
**반환**: 오류 메시지
  
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

