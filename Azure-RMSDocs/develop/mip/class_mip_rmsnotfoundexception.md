# <a name="class-miprmsnotfoundexception"></a>클래스 mip::RMSNotFoundException 
RMS를 찾을 수 없음 예외입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline RMSNotFoundException(const std::string& message)  |  [RMSNotFoundException](#classmip_1_1_r_m_s_not_found_exception) 생성자입니다.
public inline RMSNotFoundException(const char*const& message)  |  [RMSNotFoundException](#classmip_1_1_r_m_s_not_found_exception) 생성자입니다.
public inline virtual const char* what() const  |  예외 메시지를 가져옵니다.
public inline virtual ExceptionTypes type() const  |  예외 유형을 가져옵니다.
public inline virtual int error() const  |  오류 코드를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="rmsnotfoundexception"></a>RMSNotFoundException
[RMSNotFoundException](#classmip_1_1_r_m_s_not_found_exception) 생성자입니다.
  
#### <a name="parameters"></a>매개 변수
* message 예외 메시지
  
### <a name="rmsnotfoundexception"></a>RMSNotFoundException
[RMSNotFoundException](#classmip_1_1_r_m_s_not_found_exception) 생성자입니다.
  
#### <a name="parameters"></a>매개 변수
* message 예외 메시지
  
### <a name="what"></a>what
예외 메시지를 가져옵니다.
  
#### <a name="returns"></a>Returns
예외 메시지
  
### <a name="exceptiontypes"></a>ExceptionTypes
예외 유형을 가져옵니다.
  
#### <a name="returns"></a>Returns
예외 종류
  
### <a name="error"></a>오류
오류 코드를 가져옵니다.
  
#### <a name="returns"></a>Returns
[오류](#classmip_1_1_error) 코드를 반환합니다.