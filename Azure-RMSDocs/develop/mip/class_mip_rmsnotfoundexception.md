# <a name="class-miprmsnotfoundexception"></a>클래스 mip::RMSNotFoundException 
RMS를 찾을 수 없음 예외입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public RMSNotFoundException(const std::string& message)  |  [RMSNotFoundException](class_mip_rmsnotfoundexception.md) 생성자입니다.
 public RMSNotFoundException(const char*const& message)  |  [RMSNotFoundException](class_mip_rmsnotfoundexception.md) 생성자입니다.
 public virtual const char* what() const  |  예외 메시지를 가져옵니다.
 public virtual ExceptionTypes type() const  |  예외 유형을 가져옵니다.
 public virtual int error() const  |  오류 코드를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="rmsnotfoundexception"></a>RMSNotFoundException
[RMSNotFoundException](class_mip_rmsnotfoundexception.md) 생성자입니다.

매개 변수:  
* **message**: 예외 메시지


  
### <a name="rmsnotfoundexception"></a>RMSNotFoundException
[RMSNotFoundException](class_mip_rmsnotfoundexception.md) 생성자입니다.

매개 변수:  
* **message**: 예외 메시지


  
### <a name="what"></a>what
예외 메시지를 가져옵니다.

  
**반환**: 예외 메시지
  
### <a name="exceptiontypes"></a>ExceptionTypes
예외 유형을 가져옵니다.

  
**반환**: 예외 유형
  
### <a name="error"></a>오류
오류 코드를 가져옵니다.

  
**반환**: [오류](class_mip_error.md) 코드