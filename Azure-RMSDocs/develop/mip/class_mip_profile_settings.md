# <a name="class-mipprofilesettings"></a>클래스 mip::Profile::Settings 
만드는 동안 그리고 수명 기간 내내 [Profile](class_mip_profile.md)에서 사용되는 [설정](class_mip_profile_settings.md)입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<Profile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  프로필을 구성하기 위한 인터페이스입니다.
 public const std::string& GetPath() const  |  저장된 상태의 경로를 가져옵니다.
 public bool GetUseInMemoryStorage() const  |  메모리 저장소에 사용 플래그를 가져옵니다.
public const std::shared_ptr<AuthDelegate>& GetAuthDelegate() const  |  인증 대리자를 가져옵니다.
public const std::shared_ptr<Profile::Observer>& GetObserver() const  |  이벤트 관찰자를 가져옵니다.
 public const ApplicationInfo GetApplicationInfo() const  |  응용 프로그램 정보를 가져옵니다.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  응용 프로그램에서 제공하는 로거 대리자를 가져옵니다(있는 경우).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  외부 로거 구현을 사용합니다.
 public void OptOutTelemetry()  |  모든 원격 분석 수집을 옵트아웃합니다.
 public bool IsTelemetryOptedOut() const  |  원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
프로필을 구성하기 위한 인터페이스입니다.

매개 변수:  
* **path**: SDK가 프로필 상태를 저장할 디렉터리 경로. 


* **useInMemoryStorage**: 디스크에 상태를 저장해야 하는지 여부를 나타내는 플래그. 


* **authDelegate**: SDK에서 인증 토큰을 얻는 데 사용되는 인증 대리자 


* **observer**: [Profile::Observer](class_mip_profile_observer.md) 인터페이스를 구현하는 클래스. nullptr일 수 없습니다. 


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
  
### <a name="profileobserver"></a>Profile::Observer
이벤트 관찰자를 가져옵니다.

  
**반환**: 이벤트 관찰자.
  
### <a name="applicationinfo"></a>ApplicationInfo
응용 프로그램 정보를 가져옵니다.

  
**반환**: 응용 프로그램 정보.
  
### <a name="loggerdelegate"></a>LoggerDelegate
응용 프로그램에서 제공하는 로거 대리자를 가져옵니다(있는 경우).

  
**반환**: 로깅에 사용되는 로거 대리자
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
외부 로거 구현을 사용합니다.
자신의 로거 구현을 사용하려는 경우 클라이언트 응용 프로그램에서 이를 호출해야 합니다.
  
### <a name="optouttelemetry"></a>OptOutTelemetry
모든 원격 분석 수집을 옵트아웃합니다.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.

  
**반환**: 원격 분석 수집을 사용하지 않아야 하는지 여부