# <a name="class-mipprotectionengine"></a>class mip::ProtectionEngine 
특정 ID와 관련된 보호 관련 동작을 수행합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  엔진 설정을 가져옵니다.
public void GetTemplatesAsync(const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  사용자가 사용할 수 있는 템플릿 컬렉션을 가져옵니다.
public void CreateProtectionHandlerFromDescriptorAsync(const std::shared_ptr<ProtectionDescriptor>& descriptor, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  권한/역할이 특정 사용자에게 할당되는 보호 처리기를 생성합니다.
public void CreateProtectionHandlerFromPublishingLicenseAsync(const std::vector<uint8_t>& serializedPublishingLicense, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  직렬화된 양식에서 보호 처리기를 생성합니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
엔진 설정을 가져옵니다.

  
**반환**: 엔진 설정
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
사용자가 사용할 수 있는 템플릿 컬렉션을 가져옵니다.

매개 변수:  
* **observer**: [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 이 동일한 컨텍스트는 [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) 또는 [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)로 전달됩니다.


  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
권한/역할이 특정 사용자에게 할당되는 보호 처리기를 생성합니다.

매개 변수:  
* **descriptor**: 보호 구성을 설명하는 [ProtectionDescriptor](class_mip_protectiondescriptor.md) 


* **options**: 생성 옵션 


* **observer**: [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 이 동일한 컨텍스트가 [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) 또는 ProtectionHandler::Observer::OnCreateProtectionHandlerFailure로 전달됩니다.


  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
직렬화된 양식에서 보호 처리기를 생성합니다.

매개 변수:  
* **serializedPublishingLicense**: 직렬화된 게시 라이선스 


* **options**: 생성 옵션 


* **observer**: [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 이 동일한 컨텍스트가 [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) 또는 ProtectionHandler::Observer::OnCreateProtectionHandlerFailure로 전달됩니다.

