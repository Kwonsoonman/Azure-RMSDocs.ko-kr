# <a name="class-mipprotectionprofileobserver"></a>클래스 mip::ProtectionProfile::Observer 
[ProtectionProfile](class_mip_protectionprofile.md)에 관련된 알림을 받는 인터페이스입니다.
이 인터페이스는 보호 SDK를 사용하여 응용 프로그램에 의해 구현되어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<ProtectionProfile>& profile, const std::shared_ptr<void>& context)  |  프로필이 성공적으로 로드되었을 때 호출됩니다.
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  엔진 목록이 성공적으로 생성되었을 때 호출됩니다.
public virtual void OnListEnginesError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 나열로 오류가 발생했을 때 호출됩니다.
public virtual void OnAddEngineSuccess(const std::shared_ptr<ProtectionEngine>& engine, const std::shared_ptr<void>& context)  |  새 엔진이 성공적으로 추가되었을 때 호출됩니다.
public virtual void OnAddEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  새 엔진 추가로 오류가 발생했을 때 호출됩니다.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  엔진이 성공적으로 삭제되었을 때 호출됩니다.
public virtual void OnDeleteEngineError(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 삭제로 오류가 발생했을 때 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="onloadsuccess"></a>OnLoadSuccess
프로필이 성공적으로 로드되었을 때 호출됩니다.

매개 변수:  
* **profile**: 새로 만들어진 [ProtectionProfile](class_mip_protectionprofile.md)에 대한 참조


* **context**: ProtectionProfile::LoadAsync에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 ProtectionProfile::LoadAsync에 전달할 수 있고 이 동일 컨텍스트는 있는 그대로 [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) 또는 [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)에 전달됩니다.
  
### <a name="onloadfailure"></a>OnLoadFailure
프로필 로드로 인해 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 로드 중에 발생한 [오류](class_mip_error.md) 


* **context**: ProtectionProfile::LoadAsync에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 ProtectionProfile::LoadAsync에 전달할 수 있고 이 동일 컨텍스트는 있는 그대로 [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) 또는 [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)에 전달됩니다.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
엔진 목록이 성공적으로 생성되었을 때 호출됩니다.

매개 변수:  
* **engineIds**: 사용 가능한 엔진 ID 목록 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onlistengineserror"></a>OnListEnginesError
엔진 나열로 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 나열 작업 실패의 원인이 되는 오류. 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
새 엔진이 성공적으로 추가되었을 때 호출됩니다.
  
### <a name="onaddengineerror"></a>OnAddEngineError
새 엔진 추가로 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 추가 작업 실패의 원인이 되는 오류 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
엔진이 성공적으로 삭제되었을 때 호출됩니다.

매개 변수:  
* **context**: 작업에 전달되는 컨텍스트


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
엔진 삭제로 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 삭제 작업 실패의 원인이 되는 오류 


* **context**: 작업에 전달되는 컨텍스트

