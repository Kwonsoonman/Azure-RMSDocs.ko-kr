---
title: 클래스 mip FileEngine
description: 클래스 mip FileEngine에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7342edf27b19f43881b2e8d378fa243d26f7056
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446076"
---
# <a name="class-mipfileengine"></a>클래스 mip::FileEngine 
이 클래스는 모든 엔진 함수에 대한 인터페이스를 제공합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  엔진 설정을 반환합니다.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  민감도 레이블 목록을 반환합니다.
 public const std::string& GetMoreInfoUrl() const  |  정책/레이블에 대한 자세한 정보를 조회하기 위한 URL을 제공합니다.
 public bool IsLabelingRequired() const  |  정책이 문서에 레이블을 지정하도록 요구하는지 여부를 확인합니다.
public void CreateFileHandlerAsync(const std::string& inputFilePath, const ContentState contentState, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver, const std::shared_ptr<void>& context)  |  지정된 파일 경로에 대한 파일 처리기 생성을 시작합니다.
public void CreateFileHandlerAsync(const std::shared_ptr<Stream>& inputStream, const std::string& inputFilePath, const mip::ContentState contentState, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver, const std::shared_ptr<void>& context)  |  지정된 파일 스트림에 대한 파일 처리기 생성을 시작합니다.
 public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  응용 프로그램 특정 이벤트를 감사 파이프라인에 기록합니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
엔진 설정을 반환합니다.
  
### <a name="label"></a>Label
민감도 레이블 목록을 반환합니다.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
정책/레이블에 대한 자세한 정보를 조회하기 위한 URL을 제공합니다.

  
**반환**: 문자열 형식의 URL입니다.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
정책이 문서에 레이블을 지정하도록 요구하는지 여부를 확인합니다.

  
**반환**: 레이블 지정이 필수이면 True, 그렇지 않으면 false.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
지정된 파일 경로에 대한 파일 처리기 생성을 시작합니다.

매개 변수:  
* **The**: 열려는 파일. 경로에는 파일 이름과 파일 이름 확장명(있는 경우)이 포함되어야 합니다. 


* **contentState**: 응용 프로그램이 콘텐츠와 상호 작용하는 동안의 콘텐츠 상태 


* **A**: [FileHandler::Observer](class_mip_filehandler_observer.md) 인터페이스를 구현하는 클래스. 


* **context**: 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
지정된 파일 스트림에 대한 파일 처리기 생성을 시작합니다.

매개 변수:  
* **inputStream**: 파일 데이터를 포함하는 스트림 


* **inputFilePath**: 파일의 경로. 경로에는 파일 이름과 파일 이름 확장명(있는 경우)이 포함되어야 합니다. 


* **contentState**: 응용 프로그램이 콘텐츠와 상호 작용하는 동안의 콘텐츠 상태 


* **fileHandlerObserver**: [FileHandler::Observer](class_mip_filehandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
응용 프로그램 특정 이벤트를 감사 파이프라인에 기록합니다.

매개 변수:  
* **level**: 정보/오류/경고 로그 수준에 대한 설명 


* **eventType**: 이벤트 유형에 대한 설명 


* **eventData**: 이벤트와 연결된 데이터

