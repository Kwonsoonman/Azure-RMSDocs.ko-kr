# <a name="class-mipprotectionprofilesettings"></a>클래스 mip::ProtectionProfile::Settings 
만드는 동안, 그리고 수명 내내 [ProtectionProfile](#classmip_1_1_protection_profile)에서 사용되는 [설정](#classmip_1_1_protection_profile_1_1_settings)입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline Settings(const std::string& path, const std::shared_ptr<ProtectionProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  [ProtectionProfile::Settings](#classmip_1_1_protection_profile_1_1_settings) 생성자입니다.
public inline const std::string& GetPath() const  |  로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 경로를 가져옵니다.
public inline const std::shared_ptr<ProtectionProfile::Observer>& GetObserver() const  |  [ProtectionProfile](#classmip_1_1_protection_profile)에 관련된 이벤트의 알림을 받는 관찰자를 가져옵니다.
public inline const ApplicationInfo& GetApplicationInfo() const  |  보호 SDK를 사용 중인 응용 프로그램에 관한 정보를 가져옵니다.
public inline bool GetSkipTelemetryInit() const  |  원격 분석 초기화를 건너뛰어야 할지 여부를 가져옵니다.
public inline void SetSkipTelemetryInit()  |  원격 분석 초기화를 사용하지 않도록 설정합니다.
public inline void SetSessionId(const std::string& sessionId)  |  세션 ID를 설정합니다.
public inline const std::string& GetSessionId() const  |  세션 ID를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
[ProtectionProfile::Settings](#classmip_1_1_protection_profile_1_1_settings) 생성자입니다.
  
#### <a name="parameters"></a>매개 변수
* path 로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 파일 경로 
* observer [ProtectionProfile](#classmip_1_1_protection_profile)에 관련된 이벤트의 알림을 받을 [Observer](#classmip_1_1_protection_profile_1_1_observer) 인스턴스
* applicationInfo 보호 SDK를 사용 중인 응용 프로그램에 관한 정보
  
### <a name="getpath"></a>GetPath
로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 경로를 가져옵니다.
  
#### <a name="returns"></a>Returns
로깅, 원격 분석 및 기타 보호 참고 자료가 저장되는 경로
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
[ProtectionProfile](#classmip_1_1_protection_profile)에 관련된 이벤트의 알림을 받는 관찰자를 가져옵니다.
  
#### <a name="returns"></a>Returns
[ProtectionProfile](#classmip_1_1_protection_profile)에 관련된 이벤트의 알림을 받는 [Observer](#classmip_1_1_protection_profile_1_1_observer)
  
### <a name="applicationinfo"></a>ApplicationInfo
보호 SDK를 사용 중인 응용 프로그램에 관한 정보를 가져옵니다.
  
#### <a name="returns"></a>Returns
보호 SDK를 사용 중인 응용 프로그램에 관한 정보
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
원격 분석 초기화를 건너뛰어야 할지 여부를 가져옵니다.
  
#### <a name="returns"></a>Returns
원격 분석 초기화를 건너뛰어야 할지 여부
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
원격 분석 초기화를 사용하지 않도록 설정합니다.
이 매개 변수는 보통 클라이언트 응용 프로그램에서 호출되지 않아야 하고, 오히려 이미 원격 분석을 초기화하는 파일 SDK에서 중복 초기화를 방지하는 데 사용됩니다.
  
### <a name="setsessionid"></a>SetSessionId
세션 ID를 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* sessionId 로그/원격 분석을 상호 연결하는 데 사용되는 세션 ID
  
### <a name="getsessionid"></a>GetSessionId
세션 ID를 가져옵니다.
  
#### <a name="returns"></a>Returns
로그/원격 분석을 상호 연결하는 데 사용되는 세션 ID