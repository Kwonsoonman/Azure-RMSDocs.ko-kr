# <a name="class-mipprotectionprofile"></a>클래스 mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md)은 보호 작업을 수행하기 위한 루트 클래스입니다.
보호 작업을 수행하기 전에 응용 프로그램이 [ProtectionProfile](class_mip_protectionprofile.md)을 만들어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 설정을 가져옵니다.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  엔진 나열 작업을 시작합니다.
public void AddEngineAsync(const ProtectionEngine::Settings& settings, const std::shared_ptr<void>& context)  |  프로필에 새 보호 엔진 추가를 시작합니다.
public void DeleteEngineAsync(const std::string& engineId, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 보호 엔진 삭제를 시작합니다. 지정된 엔진에 대한 모든 데이터가 완전히 삭제됩니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 설정을 가져옵니다.

  
**반환**: 초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 [설정](class_mip_protectionprofile_settings.md)
  
### <a name="listenginesasync"></a>ListEnginesAsync
엔진 나열 작업을 시작합니다.

매개 변수:  
* **context**: observer 함수에 전달될 매개 변수 


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="addengineasync"></a>AddEngineAsync
프로필에 새 보호 엔진 추가를 시작합니다.

매개 변수:  
* **settings**: 엔진의 매개 변수를 지정하는 [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) 개체 


* **context**: observer 함수에 전달될 매개 변수 


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
지정된 ID를 사용하여 보호 엔진 삭제를 시작합니다. 지정된 엔진에 대한 모든 데이터가 완전히 삭제됩니다.

매개 변수:  
* **id**: 고유 엔진 ID 


* **context**: observer 함수에 전달될 매개 변수 


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)는 성공 또는 실패 시 호출됩니다.