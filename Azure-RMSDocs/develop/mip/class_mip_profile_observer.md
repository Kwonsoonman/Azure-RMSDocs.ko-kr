# <a name="class-mipprofileobserver"></a>클래스 mip::Profile::Observer 
클라이언트가 프로필 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](#classmip_1_1_profile_1_1_observer) 인터페이스입니다.
*오류 이벤트가 발생하면 오류 개체는 [mip::Error](#classmip_1_1_error) 클래스 내부에 포함됩니다. 클라이언트는 관찰자를 호출하는 스레드에서 엔진을 다시 호출하면 안 됩니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline virtual void OnLoadSuccessProfile > & profile,const std::shared_ptr< void > & context) | 프로필이 성공적으로 로드되었을 때 호출됩니다.
public inline virtual void OnLoadFailure | 프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnListEnginesSuccess | 엔진 목록이 성공적으로 생성되었을 때 호출됩니다.
public inline virtual void OnListEnginesError | 엔진 나열로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnUnloadEngineSuccess | 엔진이 성공적으로 언로드되었을 때 호출됩니다.
public inline virtual void OnUnloadEngineError | 엔진 언로드로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnAddEngineSuccessPolicyEngine > & engine,const std::shared_ptr< void > & context) | 새 엔진이 성공적으로 추가되었을 때 호출됩니다.
public inline virtual void OnAddEngineError | 새 엔진 추가로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnDeleteEngineSuccess | 엔진이 성공적으로 삭제되었을 때 호출됩니다.
public inline virtual void OnDeleteEngineError | 엔진 삭제로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnPolicyChanged | 지정된 ID를 가진 엔진에 대한 정책이 변경되었을 때 호출됩니다.
## <a name="members"></a>멤버
### <a name="onloadsuccess"></a>OnLoadSuccess
프로필이 성공적으로 로드되었을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* profile 작업을 시작하는 데 사용되는 현재 프로필입니다. 
* context 작업에 전달되는 컨텍스트입니다.
### <a name="onloadfailure"></a>OnLoadFailure
프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* error 로드 작업 실패의 원인이 되는 오류입니다. 
* context 작업에 전달되는 컨텍스트입니다.
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
엔진 목록이 성공적으로 생성되었을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* engineIds 사용 가능한 엔진 ID 목록입니다. 
* context 작업에 전달되는 컨텍스트입니다.
### <a name="onlistengineserror"></a>OnListEnginesError
엔진 나열로 인해 오류가 발생했을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* error 엔진 나열 작업 실패의 원인이 되는 오류입니다. 
* context 작업에 전달되는 컨텍스트입니다.
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
엔진이 성공적으로 언로드되었을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* context 작업에 전달되는 컨텍스트입니다.
### <a name="onunloadengineerror"></a>OnUnloadEngineError
엔진 언로드로 인해 오류가 발생했을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* error 엔진 언로드 작업 실패의 원인이 되는 오류입니다. 
* context 작업에 전달되는 컨텍스트입니다.
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
새 엔진이 성공적으로 추가되었을 때 호출됩니다.
### <a name="onaddengineerror"></a>OnAddEngineError
새 엔진 추가로 인해 오류가 발생했을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* error 엔진 추가 작업 실패의 원인이 되는 오류입니다. 
* context 작업에 전달되는 컨텍스트입니다.
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
엔진이 성공적으로 삭제되었을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* context 작업에 전달되는 컨텍스트입니다.
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
엔진 삭제로 인해 오류가 발생했을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* error 엔진 삭제 작업 실패의 원인이 되는 오류입니다. 
* context 작업에 전달되는 컨텍스트입니다.
### <a name="onpolicychanged"></a>OnPolicyChanged
지정된 ID를 가진 엔진에 대한 정책이 변경되었을 때 호출됩니다.
#### <a name="parameters"></a>매개 변수
* engineId 새 정책을 로드하기 위한 엔진으로, 지정된 엔진 ID를 사용하여 AddEngineAsync를 다시 호출하는 데 필요합니다.