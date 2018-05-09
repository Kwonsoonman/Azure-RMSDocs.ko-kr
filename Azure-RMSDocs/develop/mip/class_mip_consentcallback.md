# <a name="class-mipconsentcallback"></a>클래스 mip::ConsentCallback 
동의 요청 알림에 대한 인터페이스입니다.
이 콜백은 사용자에게 동의 알림을 표시해야 하는 시기를 알기 위해 클라이언트 응용 프로그램에 의해 구현됩니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public ConsentList Consents(ConsentList& consents)  |  SDK에 작업에 대한 사용자 동의가 필요한 경우 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="consentlist"></a>ConsentList
SDK에 작업에 대한 사용자 동의가 필요한 경우 호출됩니다.
  
#### <a name="parameters"></a>매개 변수
* consents SDK에서 요청된 동의 목록
  
#### <a name="returns"></a>Returns
[동의](#classmip_1_1_consent) 결과, SDK에서 동의가 요청된 경우 클라이언트 응용 프로그램은 사용자의 동의를 얻어야 하고, 각 동의의 결과는 [Consent::Result(const ConsentResult&)](#classmip_1_1_consent_1ad6c17d9af548a40b2fe854fe0d9bca64)를 통해 저장되어야 하고, 확인된 동의 목록이 반환되어야 합니다.