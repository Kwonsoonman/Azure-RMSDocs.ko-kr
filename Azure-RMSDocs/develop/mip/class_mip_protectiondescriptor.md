# <a name="class-mipprotectiondescriptor"></a>class mip::ProtectionDescriptor 
보호된 콘텐츠와 연결된 임시 정책을 나타냅니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public ProtectionType GetProtectionType() const  |  보호 SDK 템플릿에서 비롯되었는지 여부와 관계없이 보호 유형을 가져옵니다.
 public const std::string& GetName() const  |  정책 이름을 가져옵니다.
 public const std::string& GetDescription() const  |  정책 설명을 가져옵니다.
 public const std::string& GetTemplateId() const  |  보호 템플릿 ID를 가져옵니다.
public const std::vector<UserRights>& GetUserRights() const  |  사용자-권한 매핑의 컬렉션을 가져옵니다.
public const std::vector<UserRoles>& GetUserRoles() const  |  사용자-역할 매핑의 컬렉션을 가져옵니다.
public const std::chrono::time_point<std::chrono::system_clock>& GetContentValidUntil() const  |  정책 만료 시간을 가져옵니다.
 public bool DoesAllowOfflineAccess() const  |  정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 가져옵니다.
 public const std::string& GetReferrer() const  |  정책 참조 주소를 가져옵니다.
public const std::map<std::string, std::string>& GetEncryptedAppData() const  |  암호화된 앱별 데이터를 가져옵니다.
public const std::map<std::string, std::string>& GetSignedAppData() const  |  서명된 앱별 데이터를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="protectiontype"></a>ProtectionType
보호 SDK 템플릿에서 비롯되었는지 여부와 관계없이 보호 유형을 가져옵니다.

  
**반환**: 보호 유형
  
### <a name="getname"></a>GetName
정책 이름을 가져옵니다.

  
**반환**: 정책 이름
  
### <a name="getdescription"></a>GetDescription
정책 설명을 가져옵니다.

  
**반환**: 정책 설명
  
### <a name="gettemplateid"></a>GetTemplateId
보호 템플릿 ID를 가져옵니다.

  
**반환**: 템플릿 ID
  
### <a name="userrights"></a>UserRights
사용자-권한 매핑의 컬렉션을 가져옵니다.

  
**반환**: 사용자-권한 매핑 컬렉션. 현재 사용자에게 사용자 권한 정보에 대한 액세스 권한이 없는 경우(소유자가 아니며 VIEWRIGHTSDATA 권한이 없음) [UserRights](class_mip_userrights.md) 속성 값이 비어 있습니다.
  
### <a name="userroles"></a>UserRoles
사용자-역할 매핑의 컬렉션을 가져옵니다.

  
**반환**: 사용자-역할 매핑의 컬렉션
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
정책 만료 시간을 가져옵니다.

  
**반환**: 정책 만료 시간
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 가져옵니다.

  
**반환**: 정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부(기본값 = true)
  
### <a name="getreferrer"></a>GetReferrer
정책 참조 주소를 가져옵니다.

  
**반환**: 정책의 참조 주소. 참조는 사용자가 콘텐츠에 액세스할 권한을 얻는 방법에 대한 정보가 포함된 정책 취득 실패 시 사용자에게 표시될 수 있는 URI입니다.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
암호화된 앱별 데이터를 가져옵니다.

  
**반환**: 앱별 데이터. [ProtectionHandler](class_mip_protectionhandler.md)에는 보호 서비스에 의해 암호화된 앱별 데이터 사전이 포함될 수 있습니다. 이 암호화된 데이터는 [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata)를 통해 액세스할 수 있는 서명된 데이터와 관련이 없습니다.
  
### <a name="getsignedappdata"></a>GetSignedAppData
서명된 앱별 데이터를 가져옵니다.

  
**반환**: 앱별 데이터. [ProtectionHandler](class_mip_protectionhandler.md)에는 보호 서비스에 의해 서명된 앱별 데이터 사전이 포함될 수 있습니다. 이 서명된 데이터는 [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata)를 통해 액세스할 수 있는 암호화된 데이터와 관련이 없습니다.