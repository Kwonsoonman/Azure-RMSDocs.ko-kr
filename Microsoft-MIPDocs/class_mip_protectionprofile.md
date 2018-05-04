# <a name="class-mipprotectionprofile"></a>클래스 mip::ProtectionProfile 
[ProtectionProfile](#classmip_1_1_protection_profile)은 보호 작업을 수행하기 위한 루트 클래스입니다.
보호 작업을 수행하기 전에 응용 프로그램이 [ProtectionProfile](#classmip_1_1_protection_profile)을 만들어야 합니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const Settings & GetSettings public void ClearCaches | 캐시를 삭제합니다(예: 동의 데이터베이스 등).
## <a name="members"></a>멤버
### <a name="settings"></a>설정
초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](#classmip_1_1_protection_profile)에서 사용되는 설정을 가져옵니다.
#### <a name="returns"></a>Returns
초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](#classmip_1_1_protection_profile_1_1_settings)에서 사용되는 [Settings](#classmip_1_1_protection_profile)입니다.
### <a name="clearcaches"></a>ClearCaches
캐시를 삭제합니다(예: 동의 데이터베이스 등). 디버깅/테스트에 유용합니다.