# <a name="class-miprmsnetworkexception"></a>클래스 mip::RMSNetworkException 
RMS 네트워크 예외입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public RMSNetworkException(const std::string& message, Reason reason)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) 생성자입니다.
 public RMSNetworkException(const char*const& message, Reason reason)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) 생성자입니다.
 public virtual Reason reason() const  |  네트워크 오류 분류를 가져옵니다.
 public virtual const char* what() const  |  예외 메시지를 가져옵니다.
 public virtual ExceptionTypes type() const  |  예외 유형을 가져옵니다.
 public virtual int error() const  |  오류 코드를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) 생성자입니다.

매개 변수:  
* **message**: 예외 메시지 


* **reason**: 네트워크 오류 분류


  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) 생성자입니다.

매개 변수:  
* **message**: 예외 메시지 


* **reason**: 네트워크 오류 분류


  
### <a name="reason"></a>Reason
네트워크 오류 분류를 가져옵니다.

  
**반환**: 네트워크 오류 분류
  
### <a name="what"></a>what
예외 메시지를 가져옵니다.

  
**반환**: 예외 메시지
  
### <a name="exceptiontypes"></a>ExceptionTypes
예외 유형을 가져옵니다.

  
**반환**: 예외 유형
  
### <a name="error"></a>error
오류 코드를 가져옵니다.

  
**반환**: [오류](class_mip_error.md) 코드