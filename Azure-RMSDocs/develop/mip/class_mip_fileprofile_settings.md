# <a name="class-mipfileprofilesettings"></a>클래스 mip::FileProfile::Settings 
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline Settings(const std::string& path, bool useInMemoryStorage, std::shared_ptr<AuthDelegate> authDelegate, std::shared_ptr<Observer> observer, const ApplicationInfo& applicationInfo)  |  프로필을 구성하기 위한 인터페이스입니다.
public inline ~Settings()  |  
public inline const std::string& GetPath() const  |  
public inline bool GetUseInMemoryStorage() const  |  
public inline std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  
public inline std::shared_ptr<Observer> GetObserver() const  |  
public inline const ApplicationInfo GetApplicationInfo() const  |  
public inline bool GetSkipTelemetryInit() const  |  
public inline void SetSkipTelemetryInit()  |  
public inline void SetSessionId(const std::string& sessionId)  |  프로필 세션 ID를 설정합니다.
public inline const std::string& GetSessionId() const  |  프로필 세션 ID를 반환합니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
프로필을 구성하기 위한 인터페이스입니다.
  
#### <a name="parameters"></a>매개 변수
* observer [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) 인터페이스를 구현하는 클래스입니다. nullptr일 수 없습니다.
  
### <a name="settings"></a>~Settings
  
### <a name="getpath"></a>GetPath
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
  
### <a name="getauthdelegate"></a>GetAuthDelegate
  
### <a name="observer"></a>관찰자
  
### <a name="applicationinfo"></a>ApplicationInfo
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
  
### <a name="setsessionid"></a>SetSessionId
프로필 세션 ID를 설정합니다.
  
### <a name="getsessionid"></a>GetSessionId
프로필 세션 ID를 반환합니다.