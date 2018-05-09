# <a name="class-miprmscryptographyexception"></a>클래스 mip::RMSCryptographyException 
RMS 암호화 예외입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline RMSCryptographyException(const std::string& message)  |  [RMSCryptographyException](#classmip_1_1_r_m_s_cryptography_exception) 생성자입니다.
public inline RMSCryptographyException(const char*const& message)  |  [RMSCryptographyException](#classmip_1_1_r_m_s_cryptography_exception) 생성자입니다.
public inline virtual const char* what() const  |  예외 메시지를 가져옵니다.
public inline virtual ExceptionTypes type() const  |  예외 유형을 가져옵니다.
public inline virtual int error() const  |  오류 코드를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="rmscryptographyexception"></a>RMSCryptographyException
[RMSCryptographyException](#classmip_1_1_r_m_s_cryptography_exception) 생성자입니다.
  
#### <a name="parameters"></a>매개 변수
* message 예외 메시지
  
### <a name="rmscryptographyexception"></a>RMSCryptographyException
[RMSCryptographyException](#classmip_1_1_r_m_s_cryptography_exception) 생성자입니다.
  
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