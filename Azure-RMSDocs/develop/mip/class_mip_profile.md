# <a name="class-mipprofile"></a>클래스 mip::Profile 
[Profile](class_mip_profile.md) 클래스는 Microsoft Information Protection 작업을 사용하기 위한 루트 클래스입니다. 일반적인 응용 프로그램은 하나의 [프로필](class_mip_profile.md)만 필요하지만 필요한 경우 여러 프로필을 만들 수 있습니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  프로필에 설정된 설정을 가져옵니다.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  엔진 나열 작업을 시작합니다.
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 정책 엔진 언로드를 시작합니다.
public void AddEngineAsync(const PolicyEngine::Settings& settings, const std::shared_ptr<void>& context)  |  프로필에 대한 새 정책 엔진 추가를 시작합니다.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 정책 엔진 삭제를 시작합니다. 지정된 프로필에 대한 모든 데이터가 완전히 삭제됩니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
프로필에 설정된 설정을 가져옵니다.

  
**반환**: 프로필에 설정된 설정
  
### <a name="listenginesasync"></a>ListEnginesAsync
엔진 나열 작업을 시작합니다.

매개 변수:  
* **context**: observer 함수에 전달될 매개 변수 


[Profile::Observer](class_mip_profile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
지정된 ID를 사용하여 정책 엔진 언로드를 시작합니다.

매개 변수:  
* **id**: 고유 엔진 ID 


* **context**: observer 함수에 전달될 매개 변수 


[Profile::Observer](class_mip_profile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="addengineasync"></a>AddEngineAsync
프로필에 대한 새 정책 엔진 추가를 시작합니다.

매개 변수:  
* **settings**: 엔진 매개 변수를 지정하는 [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) 개체 


* **context**: observer 함수에 전달될 매개 변수 


[Profile::Observer](class_mip_profile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
지정된 ID를 사용하여 정책 엔진 삭제를 시작합니다. 지정된 프로필에 대한 모든 데이터가 완전히 삭제됩니다.

매개 변수:  
* **id**: 고유 엔진 ID 


* **context**: observer 함수에 전달될 매개 변수 


[Profile::Observer](class_mip_profile_observer.md)는 성공 또는 실패 시 호출됩니다.