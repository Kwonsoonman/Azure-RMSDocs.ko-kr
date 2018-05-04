# <a name="class-mipprotectionprofileobserver"></a>클래스 mip::ProtectionProfile::Observer 
[ProtectionProfile](#classmip_1_1_protection_profile)에 관련된 알림을 받는 인터페이스입니다.
이 인터페이스는 보호 SDK를 사용하여 응용 프로그램에 의해 구현되어야 합니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline virtual void OnLoadSuccessProtectionProfile > & profile,const std::shared_ptr< void > & context) | 프로필이 성공적으로 로드되었을 때 호출됩니다.
public inline virtual void OnLoadFailure | 프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
## <a name="members"></a>멤버
### <a name="onloadsuccess"></a>OnLoadSuccess
프로필이 성공적으로 로드되었을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* profile 새로 만들어진 [ProtectionProfile](#classmip_1_1_protection_profile)에 대한 참조
* context [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031)에 전달된 동일한 컨텍스트, 응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031)에 전달할 수 있고 이 동일 컨텍스트는 있는 그대로 [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) 또는 [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291)에 전달됨
### <a name="onloadfailure"></a>OnLoadFailure
프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* error 로드 중에 발생한 [오류](#classmip_1_1_error) 
* context [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031)에 전달된 동일한 컨텍스트, 응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031)에 전달할 수 있고 이 동일 컨텍스트는 있는 그대로 [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) 또는 [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291)에 전달됨