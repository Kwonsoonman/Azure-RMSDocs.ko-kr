# <a name="mip-sdk-for-c-preview-reference"></a>C++용 MIP SDK(미리 보기) 참조

C++용 MIP(Microsoft Information Protection) SDK(미리 보기)를 사용하여 개발자는 데이터 보호 정책을 관리하고 데이터 및 기타 디지털 자산에 적용할 수 있습니다.  

자세한 내용은 [MIP 개발자 블로그](https://aka.ms/MIPDevelopers) 및 [MIP 샘플](https://aka.ms/mipsdksamples)을 참조하세요.

C++용 MIP SDK에는 다음 클래스가 포함되어 있습니다.

| 클래스 이름 | 설명 |
| :----------|:------------|
[mip::Action](class_mip_action.md) | 모든 동작의 기본 클래스입니다. |
[mip::AddContentFooterAction](class_mip_addcontentfooteraction.md) | 문서에 콘텐츠 바닥글을 추가하도록 지정하는 동작 클래스입니다.
[mip::addContentHeaderAction](class_mip_addcontentheaderaction.md) | 콘텐츠 헤더를 추가하도록 지정하는 동작 클래스입니다.
[mip::AddWatermarkAction](class_mip_addwatermarkaction.md) | 워터마크를 추가하도록 지정하는 동작 클래스입니다.
[mip::BadInputError](class_mip_badinputerror.md) | 잘못된 입력 오류입니다. API에 대한 입력이 잘못되었습니다.
[mip::CommonRights](class_mip_commonrights.md) | 전체적으로 지원되는 권한입니다.
[mip::Consent](class_mip_consent.md) | 동작 허용에 대한 사용자의 수락/거부를 나타냅니다.
[mip::ConsentCallback](class_mip_consentcallback.md) | 동의 요청 알림에 대한 인터페이스입니다.
[mip::ConsentResult](class_mip_consentresult.md) | 사용자 조작 후에 동의 요청의 결과를 설명합니다.
[mip::ContentLabel](class_mip_contentlabel.md) | 콘텐츠 조각, 일반적으로 문서에 적용되는 Microsoft Information Protection 레이블의 추상화입니다.
[mip::CustomAction](class_mip_customaction.md) | 동작의 모든 하위 속성을 속성 모음으로 캡처하는 일반 동작 클래스입니다.
[mip::CustomProtectedStream](class_mip_customprotectedstream.md) | 스트림을 래핑하여 읽기 및 쓰기에 대한 투명한 암호화 및 암호 해독을 제공합니다.
[mip::EditableDocumentRights](class_mip_editabledocumentrights.md) | 편집 가능한 문서에 적용되는 권한입니다.
[mip::EmailRights](class_mip_emailrights.md) | 메일에 적용되는 권한입니다.
[mip::Error](class_mip_error.md) | MIP SDK에서 보고(throw 또는 반환)되는 모든 오류의 기본 클래스입니다.
[mip::ExecutionState](class_mip_executionstate.md) | 엔진을 실행하는 데 필요한 모든 상태에 대한 인터페이스입니다.
[mip::EileEngine](class_mip_fileengine.md) | 모든 엔진 함수에 대한 인터페이스입니다.
[mip::FileEngine::Settings](class_mip_fileengine_settings.md) | 
[mip::FileHandler](class_mip_filehandler.md) | 모든 파일 처리 함수에 대한 인터페이스입니다.
[mip::FileHandler::Observer](class_mip_filehandler_observer.md) | 클라이언트가 파일 처리기 관련 이벤트에 대한 알림을 가져올 수 있는 Observer 인터페이스입니다.
[mip::FileIOError](class_mip_fileioerror.md) | 파일 IO 오류입니다.
[mip::FileProfile](class_mip_fileprofile.md) | Microsoft Information Protection 작업의 루트 클래스입니다.
[mip::FileProfile::Observer](class_mip_fileprofile_observer.md) | 프로필 관련 이벤트 알림을 받는 데 사용되는 Observer 인터페이스입니다.
[mip::FileProfile::Settings](class_mip_fileprofile_settings.md) | 파일 프로필 설정을 관리하기 위한 인터페이스입니다.
[mip::GetUserPolicyResult](class_mip_getuserpolicyresult.md) | 사용자 정책 취득 요청의 결과를 설명합니다.
[mip::InternalError](class_mip_internalerror.md) | 내부 SDK 오류입니다. 예기치 않은 문제가 발생했습니다.
[mip::IStream](class_mip_istream.md) | 보호된 스트림의 기본 인터페이스입니다.
[mip::JustificationRequiredError](class_mip_justificationrequirederror.md) | 요청된 변경에는 변경에 대한 설명이 필요합니다.
[mip::JustifyAction](class_mip_justifyaction.md) | 요청에는 레이블 다운그레이드에 대한 근거가 필요하고 실행 상태에서 응답을 설정해야 합니다.
[mip::Label](class_mip_label.md) | 단일 Microsoft Information Protection 레이블에 대한 추상화입니다.
[mip::LabelingOptions](class_mip_labelingoptions.md) | SetLabel 메서드에 대한 레이블 옵션을 구성하기 위한 인터페이스입니다.
[mip::MetadataAction](class_mip_metadataaction.md) | 콘텐츠에 추가할 메타데이터 정보를 지정하는 동작입니다.
[mip::NetworkError](class_mip_networkerror.md) | 네트워킹 오류입니다.
[mip::NotSupportedError](class_mip_notsupportederror.md) | 작업이 지원되지 않음 오류입니다.
[mip::PolicyDescriptor](class_mip_policydescriptor.md) | 보호된 콘텐츠와 연결된 임시 정책을 나타냅니다.
[mip::PolicyEngine](class_mip_policyengine.md) | 이 클래스는 모든 엔진 함수에 대한 인터페이스를 제공합니다.
[mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) | 엔진을 시작하려면 적절한 매개 변수를 사용하여 이 클래스 인스턴스를 제공해야 합니다.
[mip::PrivilegedRequiredError](class_mip_privilegedrequirederror.md) | 현재 레이블은 권한 할당 메서드에 의해 설정되어 재정의될 수 없습니다.
[mip::Profile](class_mip_profile.md) | Microsoft Information Protection 작업의 루트 클래스입니다.
[mip::Profile::Observer](class_mip_profile_observer.md) | 프로필 관련 이벤트 알림을 받는 데 사용되는 인터페이스입니다.
[mip::Profile::Settings](class_mip_profile_settings.md) | 프로필 설정을 구성합니다.
[mip::ProtectAdhocAction](class_mip_protectadhocaction.md) | 문서에 임시 보호를 추가하도록 지정하는 동작 클래스입니다.  
[mip::ProtectbyTemplateAction](class_mip_protectbytemplateaction.md) | 문서에 템플릿에 의한 보호를 추가하도록 지정하는 동작 클래스입니다.
[mip::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md) | 문서에 전달 안 함 보호를 추가하도록 지정하는 동작 클래스입니다.
[mip::ProtectionProfile](class_mip_protectionprofile.md) | 보호 작업을 수행하는 데 사용되는 기본 클래스입니다.
[mip::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) | 보호 프로필 알림을 받는 데 사용합니다.
[mip::ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) | 인스턴스 수명 내내 사용되는 보호 프로필 설정입니다.
[mip::RemoveContentFooterAction](class_mip_removecontentfooteraction.md) | 문서에서 콘텐츠 바닥글을 제거하도록 지정하는 동작 클래스입니다.
[mip::RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) | 문서에서 콘텐츠 헤더를 제거하도록 지정하는 동작 클래스입니다.
[mip::RemoveProtectionAction](class_mip_removeprotectionaction.md) | 문서에서 보호를 제거하도록 지정하는 동작 클래스입니다.
[mip::RemoveWatermarkAction](class_mip_removewatermarkaction.md) | 문서에서 워터마크를 제거하도록 지정하는 동작 클래스입니다.
[mip::RMSCryptographyException](class_mip_rmscryptographyexception.md) | RMS 암호화 예외입니다.
[mip::RMSException](class_mip_rmsexception.md) | 기본 RMS 예외입니다.
[mip::RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md) | RMS 잘못된 인수 예외입니다.
[mip::RMSLogicException](class_mip_rmslogicexception.md) | RMS 논리 예외입니다.
[mip::RMSNetworkException](class_mip_rmsnetworkexception.md) | RMS 네트워크 예외입니다.
[mip::RMSNotFoundException](class_mip_rmsnotfoundexception.md) | RMS를 찾을 수 없음 예외입니다.
[mip::RMSNullPointerException](class_mip_rmsnullpointerexception.md) | RMS null 포인터 예외입니다.
[mip::RMSOfficeFileException](class_mip_rmsofficefileexception.md) | RMS Office 파일 예외입니다.
[mip::RMSPFileException](class_mip_rmspfileexception.md) | RMS PFile 예외입니다.
[mip::RMSRightsException](class_mip_rmsrightsexception.md) | RMS 권한 예외입니다.
[mip::RMSStreamException](class_mip_rmsstreamexception.md) | RMS 스트림 예외입니다.
[mip::Roles](class_mip_roles.md) | 데이터 보호를 위한 역할을 정의합니다.
[mip::Stream](class_mip_stream.md) | MIP SDK와 스트림 기반 콘텐츠 간에 인터페이스를 정의하는 클래스입니다.
[mip::TemplateDescriptor](class_mip_templatedescriptor.md) | RMS 템플릿에 대해 설명합니다.
[mip::UserPolicy](class_mip_userpolicy.md) | 보호된 콘텐츠와 연결된 정책을 나타냅니다.
[mip::UserRights](class_mip_userrights.md) | 사용자 그룹 및 이들과 연결된 권한을 나타냅니다.
[mip::UserRoles](class_mip_userroles.md) | 사용자 그룹 및 이들과 연결된 역할을 나타냅니다.
 
