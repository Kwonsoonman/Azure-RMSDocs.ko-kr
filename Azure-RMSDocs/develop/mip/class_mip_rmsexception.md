# <a name="class-miprmsexception"></a>클래스 mip::RMSException 
기본 RMS 예외입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline RMSException(const ExceptionTypes type, const int error, const std::string& message)  |  [RMSException](#classmip_1_1_r_m_s_exception) 생성자입니다.
public inline RMSException(const ExceptionTypes type, const int error, const char*const& message)  |  [RMSException](#classmip_1_1_r_m_s_exception) 생성자입니다.
public inline virtual const char* what() const  |  예외 메시지를 가져옵니다.
public inline virtual ExceptionTypes type() const  |  예외 유형을 가져옵니다.
public inline virtual int error() const  |  오류 코드를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception) 생성자입니다.
  
#### <a name="parameters"></a>매개 변수
* type 예외 유형 
* error [오류](#classmip_1_1_error) 코드 
* message 예외 메시지
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception) 생성자입니다.
  
#### <a name="parameters"></a>매개 변수
* type 예외 유형 
* error [오류](#classmip_1_1_error) 코드 
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