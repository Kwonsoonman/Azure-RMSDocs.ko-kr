# <a name="class-miprmsstreamexception"></a>클래스 mip::RMSStreamException 
RMS 스트림 예외입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public RMSStreamException(const std::string& message)  |  [RMSStreamException](class_mip_rmsstreamexception.md) 생성자입니다.
 public RMSStreamException(const char*const& message)  |  [RMSStreamException](class_mip_rmsstreamexception.md) 생성자입니다.
 public virtual const char* what() const  |  예외 메시지를 가져옵니다.
 public virtual ExceptionTypes type() const  |  예외 유형을 가져옵니다.
 public virtual int error() const  |  오류 코드를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstreamexception.md) 생성자입니다.

매개 변수:  
* **message**: 예외 메시지


  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstreamexception.md) 생성자입니다.

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