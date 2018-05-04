# <a name="class-miprmsofficefileexception"></a>클래스 mip::RMSOfficeFileException 
RMS Office 파일 예외입니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline  RMSOfficeFileExceptionReason reason) public inline  RMSOfficeFileExceptionReason reason) public inline virtual Reason reason | Office 파일 오류 분류를 가져옵니다.
public inline virtual const char * what | 예외 메시지를 가져옵니다.
public inline virtual ExceptionTypes type | 예외 유형을 가져옵니다.
public inline virtual int error | 오류 코드를 가져옵니다.
## <a name="members"></a>멤버
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) 생성자입니다.
#### <a name="parameters"></a>매개 변수
* message 예외 메시지 
* reason Office 파일 오류 분류
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) 생성자입니다.
#### <a name="parameters"></a>매개 변수
* message 예외 메시지 
* reason Office 파일 오류 분류
### <a name="reason"></a>이유
Office 파일 오류 분류를 가져옵니다.
#### <a name="returns"></a>Returns
Office 파일 오류 분류
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