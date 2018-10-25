---
title: 클래스 mip LoggerDelegate
description: 클래스 mip LoggerDelegate에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b25cdb177735feccfa5c4d344613e4747d18b77f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445855"
---
# <a name="class-miploggerdelegate"></a>class mip::LoggerDelegate 
MIP SDK 로거에 대한 인터페이스를 정의하는 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public void Init(const std::string& storagePath, LogLevel logLevel)  |  로거를 초기화합니다.
 public LogLevel GetLogLevel() const  |  로깅 이벤트를 트리거하는 가장 낮은 로그 수준을 가져옵니다.
 public void Flush()  |  로거를 플러시합니다.
 public void WriteToLog(const LogLevel level, const std::string& message, const std::string& function, const std::string& file, const int32_t line)  |  로그 파일에 로그 문을 작성합니다.
  
## <a name="members"></a>멤버
  
### <a name="init"></a>Init
로거를 초기화합니다.

매개 변수:  
* **storagePath**: 로그를 포함하여 영구 상태가 저장될 수 있는 위치에 대한 경로입니다. 


* **logLevel**: 로깅 이벤트를 트리거해야 하는 가장 낮은 로그 수준


  
### <a name="loglevel"></a>로그 수준
로깅 이벤트를 트리거하는 가장 낮은 로그 수준을 가져옵니다.

  
**반환**: 로깅 이벤트를 트리거하는 가장 낮은 로그 수준
  
### <a name="flush"></a>플러시
로거를 플러시합니다.
  
### <a name="writetolog"></a>WriteToLog
로그 파일에 로그 문을 작성합니다.

매개 변수:  
* **level**: 로그 문의 로그 수준 


* **message**: 로그 문의 메시지입니다. 


* **function**: 로그 문의 함수 이름입니다. 


* **file**: 로그 문이 생성된 파일 이름입니다. 


* **line**: 로그 문이 생성된 줄 번호입니다.

