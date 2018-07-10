# <a name="class-mipprotectionengineobserver"></a>class mip::ProtectionEngine::Observer 
[ProtectionEngine](class_mip_protectionengine.md)과 관련된 알림을 받는 인터페이스입니다.
이 인터페이스는 보호 SDK를 사용하여 응용 프로그램에 의해 구현되어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual void OnGetTemplatesSuccess(const std::shared_ptr<std::vector<std::string>>& templateIds, const std::shared_ptr<void>& context)  |  템플릿이 성공적으로 검색될 때 호출됩니다.
public virtual void OnGetTemplatesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  템플릿 검색 시 오류가 발생될 때 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="ongettemplatessuccess"></a>OnGetTemplatesSuccess
템플릿이 성공적으로 검색될 때 호출됩니다.

매개 변수:  
* **templateIds**: 검색된 템플릿 목록에 대한 참조입니다. 


* **context**: [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) 또는 [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)에 전달됩니다.
  
### <a name="ongettemplatesfailure"></a>OnGetTemplatesFailure
템플릿 검색 시 오류가 발생될 때 호출됩니다.

매개 변수:  
* **error**: 템플릿 검색 중에 발생한 [오류](class_mip_error.md) 


* **context**: [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) 또는 [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)에 전달됩니다.