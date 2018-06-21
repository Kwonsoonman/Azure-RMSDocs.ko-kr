# <a name="class-mipfileprofilesettings"></a>클래스 mip::FileProfile::Settings 
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, std::shared_ptr<AuthDelegate> authDelegate, std::shared_ptr<Observer> observer, const ApplicationInfo& applicationInfo)  |  프로필을 구성하기 위한 인터페이스입니다.
 public ~Settings()  | _아직 문서화되지 않았습니다._
 public const std::string& GetPath() const  | _아직 문서화되지 않았습니다._
 public bool GetUseInMemoryStorage() const  | _아직 문서화되지 않았습니다._
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  | _아직 문서화되지 않았습니다._
public std::shared_ptr<Observer> GetObserver() const  | _아직 문서화되지 않았습니다._
 public const ApplicationInfo GetApplicationInfo() const  | _아직 문서화되지 않았습니다._
 public bool GetSkipTelemetryInit() const  | _아직 문서화되지 않았습니다._
 public void SetSkipTelemetryInit()  | _아직 문서화되지 않았습니다._
 public void SetSessionId(const std::string& sessionId)  |  프로필 세션 ID를 설정합니다.
 public const std::string& GetSessionId() const  |  프로필 세션 ID를 반환합니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
프로필을 구성하기 위한 인터페이스입니다.

매개 변수:  
* **observer**: [FileHandler::Observer](class_mip_filehandler_observer.md) 인터페이스를 구현하는 클래스. nullptr일 수 없습니다.


  
### <a name="settings"></a>~Settings
_아직 문서화되지 않았습니다._

  
### <a name="getpath"></a>GetPath
_아직 문서화되지 않았습니다._

  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
_아직 문서화되지 않았습니다._

  
### <a name="getauthdelegate"></a>GetAuthDelegate
_아직 문서화되지 않았습니다._

  
### <a name="observer"></a>관찰자
_아직 문서화되지 않았습니다._

  
### <a name="applicationinfo"></a>ApplicationInfo
_아직 문서화되지 않았습니다._

  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
_아직 문서화되지 않았습니다._

  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
_아직 문서화되지 않았습니다._

  
### <a name="setsessionid"></a>SetSessionId
프로필 세션 ID를 설정합니다.
  
### <a name="getsessionid"></a>GetSessionId
프로필 세션 ID를 반환합니다.