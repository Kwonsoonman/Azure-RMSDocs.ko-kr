# <a name="class-mipgetuserpolicyresult"></a>클래스 mip::GetUserPolicyResult 
사용자 정책 취득 요청의 결과를 설명합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public GetUserPolicyResultStatus GetResultStatus()  |  정책 취득 요청의 상태를 가져옵니다.
public std::shared_ptr<std::string> GetReferrer()  |  정책의 참조 주소를 가져옵니다.
public std::shared_ptr<UserPolicy> GetPolicy()  |  [UserPolicy](#classmip_1_1_user_policy) 인스턴스를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getuserpolicyresultstatus"></a>GetUserPolicyResultStatus
정책 취득 요청의 상태를 가져옵니다.
  
#### <a name="returns"></a>Returns
정책 취득 요청의 상태
  
### <a name="getreferrer"></a>GetReferrer
정책의 참조 주소를 가져옵니다.
  
#### <a name="returns"></a>Returns
정책의 참조 주소, 참조는 사용자가 콘텐츠에 액세스할 권한을 얻는 방법에 대한 정보가 포함된 정책 취득 실패 시 사용자에게 표시될 수 있는 URI입니다.
  
### <a name="userpolicy"></a>UserPolicy
[UserPolicy](#classmip_1_1_user_policy) 인스턴스를 가져옵니다.
  
#### <a name="returns"></a>Returns
취득에 성공한 경우 [UserPolicy](#classmip_1_1_user_policy) 인스턴스, 실패한 경우 `nullptr`입니다.