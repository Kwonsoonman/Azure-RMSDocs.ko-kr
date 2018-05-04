# <a name="class-mipmetadataaction"></a>클래스 mip::MetadataAction 
콘텐츠에 추가해야 하는 메타데이터 정보를 지정하는 [동작](#classmip_1_1_action)입니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::vector< std::string > & GetMetadataToRemove | 콘텐츠에서 제거해야 하는 메타데이터의 이름 목록을 가져옵니다.
public const std::vector< std::pair< std::string, std::string > > & GetMetadataToAdd | 메타데이터의 목록을 키 값 쌍으로 가져옵니다. 메타데이터를 콘텐츠 메타데이터에 추가해야 합니다.
public ActionType GetType
## <a name="members"></a>멤버
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
콘텐츠에서 제거해야 하는 메타데이터의 이름 목록을 가져옵니다.
#### <a name="returns"></a>Returns
제거할 문자열 벡터. 메타데이터를 추가하기 전에 메타데이터 제거를 완료해야 합니다.
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
메타데이터의 목록을 키 값 쌍으로 가져옵니다. 메타데이터를 콘텐츠 메타데이터에 추가해야 합니다.
#### <a name="returns"></a>Returns
const std::vector<std::pair<std::string, std::string>>&, 메타데이터를 추가하기 전에 메타데이터 제거를 완료해야 합니다.
### <a name="actiontype"></a>ActionType
[동작](#classmip_1_1_action) 유형을 가져옵니다.
#### <a name="returns"></a>Returns
ActionType 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.