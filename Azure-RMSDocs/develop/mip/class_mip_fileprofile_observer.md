# <a name="class-mipfileprofileobserver"></a>클래스 mip::FileProfile::Observer 
클라이언트가 프로필 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](#classmip_1_1_file_profile_1_1_observer) 인터페이스입니다.
*오류 이벤트가 발생하면 오류 개체는 [mip::Error](#classmip_1_1_error) 클래스 내부에 포함됩니다. 클라이언트는 관찰자를 호출하는 스레드에서 엔진을 다시 호출하면 안 됩니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline virtual ~Observer()  |  
public inline virtual void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context)  |  프로필이 성공적으로 로드되었을 때 호출됩니다.
public inline virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  엔진 목록이 성공적으로 생성되었을 때 호출됩니다.
public inline virtual void OnListEnginesError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 나열로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnUnloadEngineSuccess(const std::shared_ptr<void>& context)  |  엔진이 성공적으로 언로드되었을 때 호출됩니다.
public inline virtual void OnUnloadEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 언로드로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnAddEngineSuccess(const std::shared_ptr<mip::FileEngine>& engine, const std::shared_ptr<void>& context)  |  새 엔진이 성공적으로 추가되었을 때 호출됩니다.
public inline virtual void OnAddEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  새 엔진 추가로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  엔진이 성공적으로 삭제되었을 때 호출됩니다.
public inline virtual void OnDeleteEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 삭제로 인해 오류가 발생했을 때 호출됩니다.
public inline virtual void OnPolicyChanged(const std::string& engineId)  |  지정된 ID를 가진 엔진에 대한 정책이 변경되었을 때 호출됩니다.
protected inline Observer()  |  
  
## <a name="members"></a>멤버
  
### <a name="observer"></a>~Observer
  
### <a name="onloadsuccess"></a>OnLoadSuccess
프로필이 성공적으로 로드되었을 때 호출됩니다.
  
### <a name="onloadfailure"></a>OnLoadFailure
프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
엔진 목록이 성공적으로 생성되었을 때 호출됩니다.
  
### <a name="onlistengineserror"></a>OnListEnginesError
엔진 나열로 인해 오류가 발생했을 때 호출됩니다.
  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
엔진이 성공적으로 언로드되었을 때 호출됩니다.
  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
엔진 언로드로 인해 오류가 발생했을 때 호출됩니다.
  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
새 엔진이 성공적으로 추가되었을 때 호출됩니다.
  
### <a name="onaddengineerror"></a>OnAddEngineError
새 엔진 추가로 인해 오류가 발생했을 때 호출됩니다.
  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
엔진이 성공적으로 삭제되었을 때 호출됩니다.
  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
엔진 삭제로 인해 오류가 발생했을 때 호출됩니다.
  
### <a name="onpolicychanged"></a>OnPolicyChanged
지정된 ID를 가진 엔진에 대한 정책이 변경되었을 때 호출됩니다.
  
### <a name="observer"></a>관찰자