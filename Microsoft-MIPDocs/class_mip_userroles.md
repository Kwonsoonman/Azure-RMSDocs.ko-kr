# <a name="class-mipuserroles"></a>클래스 mip::UserRoles 
사용자 그룹 및 이들과 연결된 역할을 나타냅니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public MIP_EXPORT UserRolesUserList & users,const RoleList & roles) public inline const UserList & Users | 역할 집합과 연결된 사용자를 가져옵니다.
public inline const RoleList & Roles | 사용자 그룹과 연결된 역할을 가져옵니다.
## <a name="members"></a>멤버
### <a name="userroles"></a>UserRoles
[UserRoles](#classmip_1_1_user_roles) 생성자입니다.
#### <a name="parameters"></a>매개 변수
* users 동일한 역할을 공유하는 사용자 그룹 
* roles 사용자 그룹에서 공유되는 [역할](#classmip_1_1_roles)
### <a name="userlist"></a>UserList
역할 집합과 연결된 사용자를 가져옵니다.
#### <a name="returns"></a>Returns
역할 집합과 연결된 사용자
### <a name="rolelist"></a>RoleList
사용자 그룹과 연결된 역할을 가져옵니다.
#### <a name="returns"></a>Returns
사용자 그룹과 연결된 [역할](#classmip_1_1_roles)