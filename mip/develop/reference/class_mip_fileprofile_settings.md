---
title: 클래스 mip FileProfile Settings
description: 클래스 mip FileProfile Settings에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 4b79d8eb75a54a56f1b3e48645bdd5eec0afaa19
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446382"
---
# <a name="class-mipfileprofilesettings"></a>클래스 mip::FileProfile::Settings 
만드는 동안 그리고 수명 기간 내내 [FileProfile](class_mip_fileprofile.md)에서 사용되는 [설정](class_mip_fileprofile_settings.md)입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, std::shared_ptr<AuthDelegate> authDelegate, std::shared_ptr<ConsentDelegate> consentDelegate, std::shared_ptr<Observer> observer, const ApplicationInfo& applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) 생성자입니다.
 public const std::string& GetPath() const  |  로깅, 원격 분석 및 기타 영구 상태가 저장되는 경로를 가져옵니다.
 public bool GetUseInMemoryStorage() const  |  모든 상태가 메모리(디스크가 아닌)에 저장되어야 하는지 여부를 가져옵니다.
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  인증 토큰을 얻는 데 사용되는 인증 대리자를 가져옵니다.
public std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  서비스에 연결하는 사용자 동의를 요청하는 데 사용되는 동의 대리자를 가져옵니다.
public std::shared_ptr<Observer> GetObserver() const  |  [FileProfile](class_mip_fileprofile.md)과 관련된 이벤트에 대한 알림을 받는 관찰자를 가져옵니다.
 public const ApplicationInfo GetApplicationInfo() const  |  SDK를 사용하는 애플리케이션에 대한 정보를 가져옵니다.
 public bool GetSkipTelemetryInit() const  |  원격 분석 초기화를 건너뛰어야 할지 여부를 가져옵니다.
 public void SetSkipTelemetryInit()  |  원격 분석 초기화를 사용하지 않도록 설정합니다.
 public void SetNewFeaturesDisabled()  |  새로운 기능을 사용하지 않도록 설정합니다.
 public bool AreNewFeaturesDisabled() const  |  새로운 기능이 해제되었는지 여부를 가져옵니다.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  애플리케이션에서 제공하는 로거 대리자를 가져옵니다(있는 경우).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  기본 로거를 재정의합니다.
public std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  애플리케이션에서 제공하는 HTTP 대리자(있는 경우)를 가져옵니다.
public void SetHttpDelegate(const std::shared_ptr<HttpDelegate>& httpDelegate)  |  기본 HTTP 스택을 클라이언트 고유 스택으로 재정의합니다.
 public void OptOutTelemetry()  |  모든 원격 분석 수집을 옵트아웃합니다.
 public bool IsTelemetryOptedOut() const  |  원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.
 public void SetSessionId(const std::string& sessionId)  |  세션 ID를 설정합니다.
 public const std::string& GetSessionId() const  |  세션 ID를 가져옵니다.
 public void SetMinimumLogLevel(LogLevel logLevel)  |  로깅 이벤트를 트리거할 가장 낮은 로그 수준을 설정합니다.
 public LogLevel GetMinimumLogLevel() const  |  로깅 이벤트를 트리거할 가장 낮은 로그 수준을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
[FileProfile::Settings](class_mip_fileprofile_settings.md) 생성자입니다.

매개 변수:  
* **path**: 로깅, 원격 분석 및 기타 영구 상태가 저장되는 파일 경로 


* **useInMemoryStorage**: 모든 상태가 메모리에 저장되어야 하는 경우 true, 상태가 디스크에 캐시될 수 있는 경우 false 


* **authDelegate**: 인증 토큰을 얻는 데 사용되는 인증 대리자 


* **observer**: [FileProfile](class_mip_fileprofile.md)과 관련된 이벤트의 알림을 받을 [Observer](class_mip_fileprofile_observer.md) 인스턴스


* **applicationInfo**: SDK를 사용 중인 응용 프로그램에 대한 정보


  
### <a name="getpath"></a>GetPath
로깅, 원격 분석 및 기타 영구 상태가 저장되는 경로를 가져옵니다.

  
**반환**: 로깅, 원격 분석 및 기타 영구 상태가 저장되는 경로
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
모든 상태가 메모리(디스크가 아닌)에 저장되어야 하는지 여부를 가져옵니다.

  
**반환**: 모든 상태가 메모리(디스크가 아닌)에 저장되어야 하는지 여부
  
### <a name="getauthdelegate"></a>GetAuthDelegate
인증 토큰을 얻는 데 사용되는 인증 대리자를 가져옵니다.

  
**반환**: 인증 토큰을 얻는 데 사용되는 인증 대리자
  
### <a name="consentdelegate"></a>ConsentDelegate
서비스에 연결하는 사용자 동의를 요청하는 데 사용되는 동의 대리자를 가져옵니다.

  
**반환**: 사용자 동의를 요청하는 데 사용되는 동의 대리자
  
### <a name="observer"></a>관찰자
[FileProfile](class_mip_fileprofile.md)과 관련된 이벤트에 대한 알림을 받는 관찰자를 가져옵니다.

  
**반환**: [FileProfile](class_mip_fileprofile.md)과 관련된 이벤트 알림을 받는 [Observer](class_mip_fileprofile_observer.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
SDK를 사용하는 애플리케이션에 대한 정보를 가져옵니다.

  
**반환**: SDK를 사용 중인 응용 프로그램에 대한 정보
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
원격 분석 초기화를 건너뛰어야 할지 여부를 가져옵니다.

  
**반환**: 원격 분석 초기화를 건너뛰어야 할지 여부
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
원격 분석 초기화를 사용하지 않도록 설정합니다.
이 메서드는 일반적으로 클라이언트 애플리케이션이 호출하지 않고 파일 SDK에서 중복 초기화를 방지하는 데 사용됩니다.
  
### <a name="setnewfeaturesdisabled"></a>SetNewFeaturesDisabled
새로운 기능을 사용하지 않도록 설정합니다.
새로운 기능을 시도하지 않으려는 애플리케이션에 사용됩니다.
  
### <a name="arenewfeaturesdisabled"></a>AreNewFeaturesDisabled
새로운 기능이 해제되었는지 여부를 가져옵니다.

  
**반환**: 새로운 기능이 해제되었는지 여부
  
### <a name="loggerdelegate"></a>LoggerDelegate
애플리케이션에서 제공하는 로거 대리자를 가져옵니다(있는 경우).

  
**반환**: 로거
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
기본 로거를 재정의합니다.

매개 변수:  
* **loggerDelegate**: 클라이언트 응용 프로그램이 구현하는 로깅 콜백 인터페이스


이 메서드는 자체 로거 구현을 사용하는 클라이언트 애플리케이션에서 이를 호출해야 합니다.
  
### <a name="httpdelegate"></a>HttpDelegate
애플리케이션에서 제공하는 HTTP 대리자(있는 경우)를 가져옵니다.

  
**반환**: HTTP 작업에 사용할 HTTP 대리자
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
기본 HTTP 스택을 클라이언트 고유 스택으로 재정의합니다.

매개 변수:  
* **httpDelegate**: 클라이언트 응용 프로그램이 구현하는 HTTP 콜백 인터페이스


  
### <a name="optouttelemetry"></a>OptOutTelemetry
모든 원격 분석 수집을 옵트아웃합니다.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.

  
**반환**: 원격 분석 수집을 해제해야 하는지 여부
  
### <a name="setsessionid"></a>SetSessionId
세션 ID를 설정합니다.

매개 변수:  
* **sessionId**: 로그/원격 분석의 상관 관계를 지정하는 데 사용할 세션 ID


  
### <a name="getsessionid"></a>GetSessionId
세션 ID를 가져옵니다.

  
**반환**: 로그/원격 분석의 상관 관계를 지정하는 데 사용할 세션 ID
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
로깅 이벤트를 트리거할 가장 낮은 로그 수준을 설정합니다.

매개 변수:  
* **logLevel**: 로깅 이벤트를 트리거할 가장 낮은 로그 수준 



  
**반환**: True
  
### <a name="loglevel"></a>로그 수준
로깅 이벤트를 트리거할 가장 낮은 로그 수준을 가져옵니다.

  
**반환**: 로깅 이벤트를 트리거할 가장 낮은 로그 수준