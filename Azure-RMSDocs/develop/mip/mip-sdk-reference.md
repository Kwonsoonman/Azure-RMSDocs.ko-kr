# <a name="mip-sdk-for-c-preview-reference"></a>C++용 MIP SDK(미리 보기) 참조

C++용 MIP(Microsoft Information Protection) SDK(미리 보기)를 사용하여 개발자는 데이터 보호 정책을 관리하고 데이터 및 기타 디지털 자산에 적용할 수 있습니다.  

자세한 내용은 [MIP 개발자 블로그](https://aka.ms/MIPDevelopers) 및 [MIP 샘플](https://aka.ms/mipsdksamples)을 참조하세요.

C++에 대한 MIP SDK에는 다음이 포함됩니다.

- [열거형 및 구조체](mip-enums-and-structs.md)
- [Functions (함수)](mip-functions.md)
- 다음 클래스:

| 클래스 이름 | 설명 |
| :----------|:------------|
[ConsentDelegate](class_consentdelegate.md)  |  동의 관련 작업에 대한 대리자입니다.
[mip::AccessDeniedError](class_mip_accessdeniederror.md)  |  사용자가 콘텐츠에 액세스할 수 없습니다. 예: 권한 없음, 콘텐츠가 취소됨 등
[mip::Action](class_mip_action.md)  |  동작에 대한 인터페이스입니다. 각 작업은 응용 프로그램이 레이블(정책에 정의된 대로)을 적용하는 데 필요한 단계로 변환됩니다.
[mip::AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  문서에 콘텐츠 바닥글을 추가하도록 지정하는 동작 클래스입니다.
[mip::AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  콘텐츠 헤더를 추가하도록 지정하는 동작 클래스입니다.
[mip::AddWatermarkAction](class_mip_addwatermarkaction.md)  |  워터마크를 추가하도록 지정하는 동작 클래스입니다.
[mip::ApplyLabelAction](class_mip_applylabelaction.md)  |  레이블 적용 동작에 따라 호출 응용 프로그램은 특정 레이블을 적용해야 합니다.
[mip::BadInputError](class_mip_badinputerror.md)  |  잘못된 입력 오류입니다. SDK API에 대한 입력이 잘못된 경우에 이 오류가 throw됩니다.
[mip::ClassificationResult](class_mip_classificationresult.md)  |  실행 상태에서 분류 호출의 결과를 포함하는 클래스입니다.
[mip::ContentLabel](class_mip_contentlabel.md)  |  콘텐츠 조각, 일반적으로 문서에 적용되는 Microsoft Information Protection 레이블의 추상화입니다.
[mip::CustomAction](class_mip_customaction.md)  |  [CustomAction](class_mip_customaction.md)은 동작의 모든 하위 속성을 속성 모음으로 캡처하는 일반 동작 클래스입니다. 호출자는 동작의 의미를 이해해야 합니다.
[mip::Error](class_mip_error.md)  |  MIP SDK에서 보고(throw 또는 반환)되는 모든 오류의 기본 클래스입니다.
[mip::ExecutionState](class_mip_executionstate.md)  |  엔진을 실행하는 데 필요한 모든 상태에 대한 인터페이스입니다.
[mip::FileEngine](class_mip_fileengine.md)  |  모든 엔진 함수에 대한 인터페이스입니다.
[mip::FileEngine::Settings](class_mip_fileengine::settings.md)  | _아직 문서화되지 않았습니다._
[mip::FileHandler](class_mip_filehandler.md)  |  모든 파일 처리 함수에 대한 인터페이스입니다.
[mip::FileHandler::Observer](class_mip_filehandler::observer.md)  |  클라이언트가 파일 처리기 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](class_mip_filehandler_observer.md) 인터페이스입니다.
[mip::FileIOError](class_mip_fileioerror.md)  |  파일 IO 오류입니다.
[mip::FileProfile](class_mip_fileprofile.md)  |  [FileProfile](class_mip_fileprofile.md) 클래스는 Microsoft Information Protection 작업을 사용하기 위한 루트 클래스입니다.
[mip::FileProfile::Observer](class_mip_fileprofile_observer.md)  |  클라이언트가 프로필 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](class_mip_fileprofile_observer.md) 인터페이스입니다.
[mip::FileProfile::Settings](class_mip_fileprofile_settings.md)  |  만드는 동안 그리고 수명 기간 내내 [FileProfile](class_mip_fileprofile.md)에서 사용되는 [설정](class_mip_fileprofile_settings.md)입니다.
[mip::InternalError](class_mip_internalerror.md)  |  내부 오류입니다. 이 오류는 실행 중 예기치 않은 상황이 발생할 때 throw됩니다.
[mip::JustificationRequiredError](class_mip_justificationrequirederror.md)  | _아직 문서화되지 않았습니다._
[mip::JustifyAction](class_mip_justifyaction.md)  |  근거 제공 [동작](class_mip_action.md)에는 레이블 다운그레이드에 대한 근거 제공이 필요하고 실행 상태에서 응답을 설정해야 합니다.
[mip::Label](class_mip_label.md)  |  단일 Microsoft Information Protection 레이블에 대한 추상화입니다.
[mip::LabelingOptions](class_mip_labelingoptions.md)  |  SetLabel 메서드에 대한 레이블 옵션을 구성하기 위한 인터페이스입니다.
[mip::LoggerDelegate](class_mip_loggerdelegate.md)  |  MIP SDK 로거에 대한 인터페이스를 정의하는 클래스입니다.
[mip::MetadataAction](class_mip_metadataaction.md)  |  콘텐츠에 메타데이터 정보를 추가하는 [동작](class_mip_action.md)입니다.
[mip::NetworkError](class_mip_networkerror.md)  |  네트워킹 오류입니다. 서비스 끝점에 대한 네트워크 호출을 수행할 때 예기치 않은 동작에 의해 발생했습니다.
[mip::NotSupportedError](class_mip_notsupportederror.md)  |  응용 프로그램에서 요청한 작업이 SDK에서 지원되지 않습니다.
[mip::PolicyEngine](class_mip_policyengine.md)  |  이 클래스는 모든 엔진 함수에 대한 인터페이스를 제공합니다.
[mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  엔진을 시작하려면 적절한 매개 변수를 사용하여 이 클래스 인스턴스를 제공해야 합니다.
[mip::PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  현재 레이블이 권한 있는 작업(관리자 작업에 해당)으로 할당되었으므로 재정의될 수 없습니다.
[mip::Profile](class_mip_profile.md)  |  [Profile](class_mip_profile.md) 클래스는 Microsoft Information Protection 작업을 사용하기 위한 루트 클래스입니다. 일반적인 응용 프로그램은 하나의 [프로필](class_mip_profile.md)만 필요하지만 필요한 경우 여러 프로필을 만들 수 있습니다.
[mip::Profile::Observer](class_mip_profile_observer.md)  |  클라이언트가 프로필 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](class_mip_profile_observer.md) 인터페이스입니다.
[mip::Profile::Settings](class_mip_profile_settings.md)  |  만드는 동안 그리고 수명 기간 내내 [Profile](class_mip_profile.md)에서 사용되는 [설정](class_mip_profile_settings.md)입니다.
[mip::ProtectAdhocAction](class_mip_protectadhocaction.md)  |  문서에 임시 보호를 추가하도록 지정하는 동작 클래스입니다.
[mip::ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  문서에 템플릿에 의한 보호를 추가하도록 지정하는 동작 클래스입니다.
[mip::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  문서에 전달 안 함 보호를 추가하도록 지정하는 동작 클래스입니다.
[mip::ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  보호된 콘텐츠와 연결된 임시 정책을 나타냅니다.
[mip::ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  보호된 콘텐츠와 연결된 임시 정책을 나타냅니다.
[mip::ProtectionEngine](class_mip_protectionengine.md)  |  특정 ID와 관련된 보호 관련 동작을 수행합니다.
[mip::ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  [ProtectionEngine](class_mip_protectionengine.md)과 관련된 알림을 받는 인터페이스입니다.
[mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  만드는 동안 그리고 수명 기간 내내 [ProtectionEngine](class_mip_protectionengine.md)에서 사용되는 [설정](class_mip_protectionengine_settings.md)입니다.
[mip::ProtectionHandler](class_mip_protectionhandler.md)  |  특정 보호 구성(사용자, 권한, 역할 등)에 대한 보호 관련 동작을 수행합니다.
[mip::ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)  |  [ProtectionHandler](class_mip_protectionhandler.md)와 관련된 알림을 받는 인터페이스입니다.
[mip::ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md)은 보호 작업을 수행하기 위한 루트 클래스입니다.
[mip::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  [ProtectionProfile](class_mip_protectionprofile.md)에 관련된 알림을 받는 인터페이스입니다.
[mip::ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  만드는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 [설정](class_mip_protectionprofile_settings.md)입니다.
[mip::RecommendLabelAction](class_mip_recommendlabelaction.md)  |  레이블 권장 동작은 사용자에게 레이블을 제안하기 위한 것입니다. 사용자가 권장 레이블을 무시한 후 이 호출을 표시하지 않는 것은 실행 상태에서 지원되는 작업을 통해 수행되어야 합니다.
[mip::RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  문서에서 콘텐츠 바닥글을 제거하도록 지정하는 동작 클래스입니다.
[mip::RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  문서에서 콘텐츠 헤더를 제거하도록 지정하는 동작 클래스입니다.
[mip::RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  문서에서 보호를 제거하도록 지정하는 동작 클래스입니다.
[mip::RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  문서에서 워터마크를 제거하도록 지정하는 동작 클래스입니다.
[mip::Stream](class_mip_stream.md)  |  MIP SDK와 스트림 기반 콘텐츠 간에 인터페이스를 정의하는 클래스입니다.
[mip::UserRights](class_mip_userrights.md)  |  사용자 그룹 및 이들과 연결된 권한을 나타냅니다.
[mip::UserRoles](class_mip_userroles.md)  |  사용자 그룹 및 이들과 연결된 역할을 나타냅니다.

 
