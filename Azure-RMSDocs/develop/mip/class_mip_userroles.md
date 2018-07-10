# <a name="class-mipuserroles"></a>클래스 mip::UserRoles 
사용자 그룹 및 이들과 연결된 역할을 나타냅니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public UserRoles(const std::vector<std::string>& users, const std::vector<std::string>& roles)  |  [UserRoles](class_mip_userroles.md) 생성자입니다.
public const std::vector<std::string>& Users() const  |  역할 집합과 연결된 사용자를 가져옵니다.
public const std::vector<std::string>& Roles() const  |  사용자 그룹과 연결된 역할을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="userroles"></a>UserRoles
[UserRoles](class_mip_userroles.md) 생성자입니다.

매개 변수:  
* **users**: 동일한 역할을 공유하는 사용자 그룹 


* **roles**: 사용자 그룹에서 공유되는 역할


  
### <a name="users"></a>사용자
역할 집합과 연결된 사용자를 가져옵니다.

  
**반환**: 역할 집합과 연결된 사용자
  
### <a name="roles"></a>역할
사용자 그룹과 연결된 역할을 가져옵니다.

  
**반환**: 사용자 그룹과 연결된 역할