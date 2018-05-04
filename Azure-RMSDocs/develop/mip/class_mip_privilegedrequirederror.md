# <a name="class-mipprivilegedrequirederror"></a>클래스 mip::PrivilegedRequiredError 
현재 레이블은 권한 할당 메서드에 의해 설정되어 재정의될 수 없습니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline char const  * what | cstring 오류 메시지를 가져옵니다.
public std::shared_ptr< Error > Clone | 오류를 복제합니다.
public inline virtual ErrorType GetErrorType | 오류 유형을 가져옵니다.
public inline virtual const std::string & GetErrorName | 오류 이름을 가져옵니다.
public inline virtual const std::string & GetMessage | 오류 메시지를 가져옵니다.
public inline virtual void SetMessage | 오류 메시지를 설정합니다.
## <a name="members"></a>멤버
### <a name="what"></a>what
cstring 오류 메시지를 가져옵니다.
#### <a name="returns"></a>Returns
cstring 오류 메시지
### <a name="error"></a>오류
오류를 복제합니다.
#### <a name="returns"></a>Returns
오류 복제본을 반환합니다.
### <a name="errortype"></a>ErrorType
오류 유형을 가져옵니다.
#### <a name="returns"></a>Returns
오류 유형.
### <a name="geterrorname"></a>GetErrorName
오류 이름을 가져옵니다.
#### <a name="returns"></a>Returns
오류 이름.
### <a name="getmessage"></a>GetMessage
오류 메시지를 가져옵니다.
#### <a name="returns"></a>Returns
오류 메시지.
### <a name="setmessage"></a>SetMessage
오류 메시지를 설정합니다.
#### <a name="parameters"></a>매개 변수
* msg 오류 메시지입니다.