# <a name="class-mippolicydescriptor"></a>클래스 mip::PolicyDescriptor 
보호된 콘텐츠와 연결된 임시 정책을 나타냅니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::string& GetName()  |  정책 이름을 가져옵니다.
public void SetName(const std::string& value)  |  정책 이름을 설정합니다.
public const std::string& GetDescription()  |  정책 설명을 가져옵니다.
public void SetDescription(const std::string& value)  |  정책 설명을 설정합니다.
public const std::vector<UserRights>& GetUserRightsList() const  |  사용자-권한 매핑의 컬렉션을 가져옵니다.
public const std::vector<mip::UserRoles>& GetUserRolesList()  |  사용자-역할 매핑의 컬렉션을 가져옵니다.
public const std::chrono::time_point<std::chrono::system_clock>& GetContentValidUntil()  |  정책 만료 시간을 가져옵니다.
public void SetContentValidUntil(const std::chrono::time_point<std::chrono::system_clock>& value)  |  정책 만료 시간을 설정합니다.
public bool DoesAllowOfflineAccess()  |  정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 가져옵니다.
public void SetAllowOfflineAccess(bool value)  |  정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 설정합니다.
public const std::string& GetReferrer() const  |  정책 참조 주소를 가져옵니다.
public void SetReferrer(const std::string& uri)  |  정책 참조 주소를 설정합니다.
public const AppDataHashMap& GetEncryptedAppData()  |  암호화된 앱별 데이터를 가져옵니다.
public void SetEncryptedAppData(const AppDataHashMap& value)  |  암호화해야 하는 앱별 데이터를 설정합니다.
public const AppDataHashMap& GetSignedAppData()  |  서명된 앱별 데이터를 가져옵니다.
public void SetSignedAppData(const AppDataHashMap& value)  |  서명해야 하는 앱별 데이터를 설정합니다.
  
## <a name="members"></a>멤버
  
### <a name="getname"></a>GetName
정책 이름을 가져옵니다.
  
#### <a name="returns"></a>Returns
정책 이름
  
### <a name="setname"></a>SetName
정책 이름을 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* value 정책 이름
  
### <a name="getdescription"></a>GetDescription
정책 설명을 가져옵니다.
  
#### <a name="returns"></a>Returns
정책 설명
  
### <a name="setdescription"></a>SetDescription
정책 설명을 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* value 정책 설명
  
### <a name="userrights"></a>UserRights
사용자-권한 매핑의 컬렉션을 가져옵니다.
  
#### <a name="returns"></a>Returns
사용자-권한 매핑 컬렉션, 현재 사용자에게 사용자 권한 정보에 대한 액세스 권한이 없는 경우(소유자가 아니고 VIEWRIGHTSDATA 권한이 없음) UserRightsList 속성 값이 비어 있습니다.
  
### <a name="mipuserroles"></a>mip::UserRoles
사용자-역할 매핑의 컬렉션을 가져옵니다.
  
#### <a name="returns"></a>Returns
사용자-역할 매핑 컬렉션.
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
정책 만료 시간을 가져옵니다.
  
#### <a name="returns"></a>Returns
정책 만료 시간
  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
정책 만료 시간을 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* value 정책 만료 시간
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 가져옵니다.
  
#### <a name="returns"></a>Returns
정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부(기본값 = true)
  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* value 정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부
  
### <a name="getreferrer"></a>GetReferrer
정책 참조 주소를 가져옵니다.
  
#### <a name="returns"></a>Returns
정책의 참조 주소, 참조는 사용자가 콘텐츠에 액세스할 권한을 얻는 방법에 대한 정보가 포함된 정책 취득 실패 시 사용자에게 표시될 수 있는 URI입니다.
  
### <a name="setreferrer"></a>SetReferrer
정책 참조 주소를 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* uri 정책의 참조 주소, 참조는 사용자가 콘텐츠에 액세스할 권한을 얻는 방법에 대한 정보가 포함된 정책 취득 실패 시 사용자에게 표시될 수 있는 URI입니다.
  
### <a name="appdatahashmap"></a>AppDataHashMap
암호화된 앱별 데이터를 가져옵니다.
  
#### <a name="returns"></a>Returns
앱별 데이터, [UserPolicy](#classmip_1_1_user_policy)에는 RMS 서비스에 의해 암호화된 앱별 데이터의 사전이 포함될 수 있습니다. 이 암호화된 데이터는 [PolicyDescriptor::GetSignedAppData](#classmip_1_1_policy_descriptor_1ad523870efc92f9f81c82121a054d74d4)를 통해 액세스할 수 있는 서명된 데이터와 관련이 없습니다.
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
암호화해야 하는 앱별 데이터를 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* value 앱별 데이터, 응용 프로그램이 RMS 서비스에 의해 암호화되는 앱별 데이터의 사전을 지정할 수 있습니다. 이 암호화된 데이터는 [PolicyDescriptor::SetSignedAppData](#classmip_1_1_policy_descriptor_1a00f35c0b91e48ccdcc6387466a61f362)를 통해 설정된 서명된 데이터와 관련이 없습니다.
  
### <a name="appdatahashmap"></a>AppDataHashMap
서명된 앱별 데이터를 가져옵니다.
  
#### <a name="returns"></a>Returns
앱별 데이터, [UserPolicy](#classmip_1_1_user_policy)에는 RMS 서비스에 의해 서명된 앱별 데이터의 사전이 포함될 수 있습니다. 이 서명된 데이터는 [PolicyDescriptor::GetEncryptedAppData](#classmip_1_1_policy_descriptor_1a9a5bcf9d1bf7357de549429179197ab6)를 통해 액세스할 수 있는 암호화된 데이터와 관련이 없습니다.
  
### <a name="setsignedappdata"></a>SetSignedAppData
서명해야 하는 앱별 데이터를 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* value 앱별 데이터, 응용 프로그램이 RMS 서비스에 의해 서명되는 앱별 데이터의 사전을 지정할 수 있습니다. 이 서명된 데이터는 [PolicyDescriptor::SetEncryptedAppData](#classmip_1_1_policy_descriptor_1a5275224932dc17319092304497e59eb2)를 통해 설정된 암호화된 데이터와 관련이 없습니다.