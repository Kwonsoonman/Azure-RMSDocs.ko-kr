# <a name="class-mipuserpolicy"></a>클래스 mip::UserPolicy 
보호된 콘텐츠와 연결된 정책을 나타냅니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public bool AccessCheck(const std::string& right) const  |  정책이 지정된 액세스 권한을 사용자에게 부여하는지 확인합니다.
 public UserPolicyType GetType()  |  정책 유형을 가져옵니다.
 public std::string GetName()  |  정책 이름을 가져옵니다.
 public std::string GetDescription()  |  정책 설명을 가져옵니다.
public std::shared_ptr<TemplateDescriptor> GetTemplateDescriptor()  |  템플릿 기반 [UserPolicy](class_mip_userpolicy.md)에 대한 [TemplateDescriptor](class_mip_templatedescriptor.md)를 가져옵니다.
public std::shared_ptr<PolicyDescriptor> GetPolicyDescriptor()  |  임시 [UserPolicy](class_mip_userpolicy.md)에 대한 [PolicyDescriptor](class_mip_policydescriptor.md)를 가져옵니다.
 public std::string GetOwner()  |  콘텐츠 소유자의 메일 주소를 가져옵니다.
 public std::string GetIssuedTo()  |  보호 정책과 연결된 사용자를 가져옵니다.
 public bool IsIssuedToOwner()  |  현재 사용자가 콘텐츠 소유자인지 여부를 가져옵니다.
 public std::string GetContentId()  |  문서/콘텐츠에 대한 고유 식별자를 가져옵니다.
 public const mip::AppDataHashMap GetEncryptedAppData()  |  암호화된 앱별 데이터를 가져옵니다.
 public const mip::AppDataHashMap GetSignedAppData()  |  서명된 앱별 데이터를 가져옵니다.
public std::chrono::time_point<std::chrono::system_clock> GetContentValidUntil()  |  정책 만료 시간을 가져옵니다.
 public bool DoesUseDeprecatedAlgorithms()  |  정책에서 이전 버전과의 호환성을 위해 사용 중단된 암호화 알고리즘(ECB)을 사용하는지 여부를 가져옵니다.
 public bool IsAuditedExtractAllowed()  |  정책이 사용자에게 ‘감사된 추출’ 권한을 부여하는지 여부를 가져옵니다.
public const std::vector<unsigned char> GetSerializedPolicy()  |  [UserPolicy](class_mip_userpolicy.md)를 PL(게시 라이선스)로 직렬화합니다.
public std::shared_ptr<rmscore::core::ProtectionPolicy> GetImpl()  |  [UserPolicy](class_mip_userpolicy.md)의 내부 파생 클래스 구현을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="accesscheck"></a>AccessCheck
정책이 지정된 액세스 권한을 사용자에게 부여하는지 확인합니다.

매개 변수:  
* **right**: 확인할 권한



  
**반환**: 정책이 지정된 액세스 권한을 사용자에게 부여하는지 여부
  
### <a name="userpolicytype"></a>UserPolicyType
정책 유형을 가져옵니다.

  
**반환**: 정책 유형
  
### <a name="getname"></a>GetName
정책 이름을 가져옵니다.

  
**반환**: 정책 이름
  
### <a name="getdescription"></a>GetDescription
정책 설명을 가져옵니다.

  
**반환**: 정책 설명
  
### <a name="templatedescriptor"></a>TemplateDescriptor
템플릿 기반 [UserPolicy](class_mip_userpolicy.md)에 대한 [TemplateDescriptor](class_mip_templatedescriptor.md)를 가져옵니다.

  
**반환**: [UserPolicy](class_mip_userpolicy.md)가 템플릿 기반인 경우 [TemplateDescriptor](class_mip_templatedescriptor.md), 그렇지 않으면 nullptr
  
### <a name="policydescriptor"></a>PolicyDescriptor
임시 [UserPolicy](class_mip_userpolicy.md)에 대한 [PolicyDescriptor](class_mip_policydescriptor.md)를 가져옵니다.

  
**반환**: [UserPolicy](class_mip_userpolicy.md)가 임시인 경우 [PolicyDescriptor](class_mip_policydescriptor.md), 그렇지 않으면 nullptr
  
### <a name="getowner"></a>GetOwner
콘텐츠 소유자의 메일 주소를 가져옵니다.

  
**반환**: 콘텐츠 소유자의 메일 주소
  
### <a name="getissuedto"></a>GetIssuedTo
보호 정책과 연결된 사용자를 가져옵니다.

  
**반환**: 보호 정책과 연결된 사용자
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
현재 사용자가 콘텐츠 소유자인지 여부를 가져옵니다.

  
**반환**: 현재 사용자가 콘텐츠 소유자인지 여부
  
### <a name="getcontentid"></a>GetContentId
문서/콘텐츠에 대한 고유 식별자를 가져옵니다.

  
**반환**: 고유한 콘텐츠 식별자
  
### <a name="mipappdatahashmap"></a>mip::AppDataHashMap
암호화된 앱별 데이터를 가져옵니다.
[UserPolicy](class_mip_userpolicy.md)에는 RMS 서비스에 의해 암호화된 앱별 데이터의 사전이 포함될 수 있습니다. 이 암호화된 데이터는 [UserPolicy::GetSignedAppData](class_mip_userpolicy.md#getsignedappdata)를 통해 액세스할 수 있는 서명된 데이터와 관련이 없습니다.
  
### <a name="mipappdatahashmap"></a>mip::AppDataHashMap
서명된 앱별 데이터를 가져옵니다.
[UserPolicy](class_mip_userpolicy.md)에는 RMS 서비스에 의해 서명된 앱별 데이터의 사전이 포함될 수 있습니다. 이 서명된 데이터는 [UserPolicy::GetEncryptedAppData](class_mip_userpolicy.md#getencryptedappdata)를 통해 액세스할 수 있는 암호화된 데이터와 관련이 없습니다.
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
정책 만료 시간을 가져옵니다.

  
**반환**: 정책 만료 시간
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
정책에서 이전 버전과의 호환성을 위해 사용 중단된 암호화 알고리즘(ECB)을 사용하는지 여부를 가져옵니다.

  
**반환**: 정책에서 사용 중단된 암호화 알고리즘을 사용하는지 여부
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
정책이 사용자에게 ‘감사된 추출’ 권한을 부여하는지 여부를 가져옵니다.

  
**반환**: 정책이 사용자에게 ‘감사된 추출’ 권한을 부여하는지 여부
  
### <a name="getserializedpolicy"></a>GetSerializedPolicy
[UserPolicy](class_mip_userpolicy.md)를 PL(게시 라이선스)로 직렬화합니다.

  
**반환**: 직렬화된 [UserPolicy](class_mip_userpolicy.md)
  
### <a name="getimpl"></a>GetImpl
[UserPolicy](class_mip_userpolicy.md)의 내부 파생 클래스 구현을 가져옵니다.

  
**반환**: 내부 전용 [UserPolicy](class_mip_userpolicy.md)의 파생 클래스 구현