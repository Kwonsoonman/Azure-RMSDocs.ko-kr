# <a name="class-mipprotectionprofilesettings"></a>클래스 mip::ProtectionProfile::Settings 
만드는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 [설정](class_mip_protectionprofile_settings.md)입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, bool isLicenseCachingEnabled, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const std::shared_ptr<ProtectionProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) 생성자입니다.
 public const std::string& GetPath() const  |  로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 경로를 가져옵니다.
 public bool GetUseInMemoryStorage() const  |  캐시가 메모리에만(디스크가 아닌) 저장되는지 여부를 가져옵니다.
 public bool IsLicenseCachingEnabled() const  |  라이선스의 캐싱이 활성화되는지 여부를 가져옵니다.
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  인증 토큰을 얻는 데 사용되는 인증 대리자를 가져옵니다.
public std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  서비스에 연결하는 데 사용되는 동의 대리자를 가져옵니다.
public const std::shared_ptr<ProtectionProfile::Observer>& GetObserver() const  |  [ProtectionProfile](class_mip_protectionprofile.md)과 관련된 이벤트 알림을 받는 관찰자를 가져옵니다.
 public const ApplicationInfo& GetApplicationInfo() const  |  보호 SDK를 사용 중인 응용 프로그램에 관한 정보를 가져옵니다.
 public void OptOutTelemetry()  |  모든 원격 분석 수집을 옵트아웃합니다.
 public bool IsTelemetryOptedOut() const  |  원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  응용 프로그램에서 제공하는 로거 대리자를 가져옵니다(있는 경우).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  외부 로거 구현을 사용합니다.
 public bool GetSkipTelemetryInit() const  |  원격 분석 초기화를 건너뛰어야 할지 여부를 가져옵니다.
 public void SetSkipTelemetryInit()  |  원격 분석 초기화를 사용하지 않도록 설정합니다.
 public void SetSessionId(const std::string& sessionId)  |  세션 ID를 설정합니다.
 public const std::string& GetSessionId() const  |  세션 ID를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) 생성자입니다.

매개 변수:  
* **path**: 로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 파일 경로 


* **useInMemoryStorage**: 캐시된 상태를 디스크가 아닌 메모리에 저장합니다. 


* **isLicenseCachingEnabled**: 보호 sdk 라이선스 캐싱을 활성화 또는 비활성화합니다. 


* **authDelegate**: 클라이언트 응용 프로그램에 의해 구현된, 인증에 사용될 콜백 개체 


* **observer**: [ProtectionProfile](class_mip_protectionprofile.md)에 관련된 이벤트의 알림을 받을 [Observer](class_mip_protectionprofile_observer.md) 인스턴스


* **applicationInfo**: 보호 SDK를 사용 중인 응용 프로그램에 관한 정보


  
### <a name="getpath"></a>GetPath
로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 경로를 가져옵니다.

  
**반환**: 로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 경로
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
캐시가 메모리에만(디스크가 아닌) 저장되는지 여부를 가져옵니다.

  
**반환**: 캐시가 메모리에만 저장되는 경우 True
  
### <a name="islicensecachingenabled"></a>IsLicenseCachingEnabled
라이선스의 캐싱이 활성화되는지 여부를 가져옵니다.

  
**반환**: 보호 SDK 라이선스 캐싱이 활성화된 경우 True
  
### <a name="getauthdelegate"></a>GetAuthDelegate
인증 토큰을 얻는 데 사용되는 인증 대리자를 가져옵니다.

  
**반환**: 인증 토큰을 얻는 데 사용되는 인증 대리자
  
### <a name="consentdelegate"></a>ConsentDelegate
서비스에 연결하는 데 사용되는 동의 대리자를 가져옵니다.

  
**반환**: 서비스에 연결하는 데 사용되는 동의 대리자
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
[ProtectionProfile](class_mip_protectionprofile.md)과 관련된 이벤트 알림을 받는 관찰자를 가져옵니다.

  
**반환**: [ProtectionProfile](class_mip_protectionprofile.md)과 관련된 이벤트 알림을 받는 [관찰자](class_mip_protectionprofile_observer.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
보호 SDK를 사용 중인 응용 프로그램에 관한 정보를 가져옵니다.

  
**반환**: 보호 SDK를 사용 중인 응용 프로그램에 관한 정보
  
### <a name="optouttelemetry"></a>OptOutTelemetry
모든 원격 분석 수집을 옵트아웃합니다.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
원격 분석 수집을 사용하지 않아야 하는지 여부를 가져옵니다.

  
**반환**: 원격 분석 수집을 사용하지 않아야 하는지 여부
  
### <a name="loggerdelegate"></a>LoggerDelegate
응용 프로그램에서 제공하는 로거 대리자를 가져옵니다(있는 경우).

  
**반환**: 로깅에 사용되는 로거 대리자
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
외부 로거 구현을 사용합니다.
자신의 로거 구현을 사용하려는 경우 클라이언트 응용 프로그램에서 이를 호출해야 합니다.
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
원격 분석 초기화를 건너뛰어야 할지 여부를 가져옵니다.

  
**반환**: 원격 분석 초기화를 건너뛰어야 할지 여부
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
원격 분석 초기화를 사용하지 않도록 설정합니다.
이 매개 변수는 보통 클라이언트 응용 프로그램에서 호출되지 않아야 하고, 오히려 이미 원격 분석을 초기화하는 파일 SDK에서 중복 초기화를 방지하는 데 사용됩니다.
  
### <a name="setsessionid"></a>SetSessionId
세션 ID를 설정합니다.

매개 변수:  
* **sessionId**: 로그/원격 분석을 상호 연결하는 데 사용되는 세션 ID


  
### <a name="getsessionid"></a>GetSessionId
세션 ID를 가져옵니다.

  
**반환**: 로그/원격 분석을 상호 연결하는 데 사용되는 세션 ID