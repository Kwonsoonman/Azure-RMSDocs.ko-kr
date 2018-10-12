---
title: 클래스 mip PolicyProfile Settings
description: 클래스 mip PolicyProfile Settings에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 07cbcbc022c02a43f751e1cf55b5b0efdfb816d1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446913"
---
# <a name="class-mippolicyprofilesettings"></a>클래스 mip::PolicyProfile::Settings 
만드는 동안 그리고 수명 기간 내내 [PolicyProfile](class_mip_policyprofile.md)에서 사용되는 [설정](class_mip_policyprofile_settings.md)입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<PolicyProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  프로필을 구성하기 위한 인터페이스입니다.
 public const std::string& GetPath() const  |  저장된 상태의 경로를 가져옵니다.
 public bool GetUseInMemoryStorage() const  |  메모리 저장소에 사용 플래그를 가져옵니다.
public const std::shared_ptr<AuthDelegate>& GetAuthDelegate() const  |  인증 대리자를 가져옵니다.
public const std::shared_ptr<PolicyProfile::Observer>& GetObserver() const  |  이벤트 관찰자를 가져옵니다.
 public const ApplicationInfo GetApplicationInfo() const  |  응용 프로그램 정보를 가져옵니다.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  응용 프로그램에서 제공하는 로거 대리자를 가져옵니다(있는 경우).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  기본 로거를 재정의합니다.
public std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  응용 프로그램에서 제공하는 HTTP 대리자(있는 경우)를 가져옵니다.
public void SetHttpDelegate(const std::shared_ptr<HttpDelegate>& httpDelegate)  |  기본 HTTP 스택을 클라이언트 고유 스택으로 재정의합니다.
 public void OptOutTelemetry()  |  모든 원격 분석 수집을 옵트아웃합니다.
 public bool IsTelemetryOptedOut() const  |  원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.
 public void SetMinimumLogLevel(LogLevel logLevel)  |  로깅 이벤트를 트리거할 최소 로그 수준을 설정합니다.
 public LogLevel GetMinimumLogLevel() const  |  최소 로그 수준 개체를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
프로필을 구성하기 위한 인터페이스입니다.

매개 변수:  
* **path**: SDK가 프로필 상태를 저장할 디렉터리 경로 


* **useInMemoryStorage**: 캐시된 상태를 디스크가 아닌 메모리에 저장합니다. 


* **authDelegate**: SDK에서 인증 토큰을 얻는 데 사용되는 인증 대리자 


* **observer**: [PolicyProfile::Observer](class_mip_policyprofile_observer.md) 인터페이스를 구현하는 클래스 nullptr일 수 없습니다. 


* **applicationInfo**: 서비스 액세스에 사용되는 응용 프로그램 식별자.


  
### <a name="getpath"></a>GetPath
저장된 상태의 경로를 가져옵니다.

  
**반환**: 저장된 상태의 경로.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
메모리 저장소에 사용 플래그를 가져옵니다.

  
**반환**: 메모리에 사용이 설정된 경우 true, 그렇지 않으면 false.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
인증 대리자를 가져옵니다.

  
**반환**: 인증 대리자.
  
### <a name="policyprofileobserver"></a>PolicyProfile::Observer
이벤트 관찰자를 가져옵니다.

  
**반환**: 이벤트 관찰자.
  
### <a name="applicationinfo"></a>ApplicationInfo
응용 프로그램 정보를 가져옵니다.

  
**반환**: 응용 프로그램 정보.
  
### <a name="loggerdelegate"></a>LoggerDelegate
응용 프로그램에서 제공하는 로거 대리자를 가져옵니다(있는 경우).

  
**반환**: 로거
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
기본 로거를 재정의합니다.

매개 변수:  
* **loggerDelegate**: 클라이언트 응용 프로그램이 구현하는 로깅 콜백 인터페이스


이 메서드는 자체 로거 구현을 사용하는 클라이언트 응용 프로그램에서 이를 호출해야 합니다.
  
### <a name="httpdelegate"></a>HttpDelegate
응용 프로그램에서 제공하는 HTTP 대리자(있는 경우)를 가져옵니다.

  
**반환**: HTTP 작업에 사용할 Http 대리자
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
기본 HTTP 스택을 클라이언트 고유 스택으로 재정의합니다.

매개 변수:  
* **httpDelegate**: 클라이언트 응용 프로그램이 구현하는 Http 콜백 인터페이스


  
### <a name="optouttelemetry"></a>OptOutTelemetry
모든 원격 분석 수집을 옵트아웃합니다.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.

  
**반환**: 원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
로깅 이벤트를 트리거할 최소 로그 수준을 설정합니다.

매개 변수:  
* **logLevel**: 로깅 이벤트를 트리거할 최소 로그 수준 



  
**반환**: True
  
### <a name="loglevel"></a>로그 수준
최소 로그 수준 개체를 가져옵니다.

  
**반환**: 로깅 이벤트를 트리거할 최소 로그 수준