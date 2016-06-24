---
# required metadata

title: iOS/OS X 코드 예제 | Azure RMS
description: 이 항목에서는 iOS/OS X 버전의 RMS SDK에 대한 중요한 코드 요소를 소개합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7E12EBF2-5A19-4A8D-AA99-531B09DA256A
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# iOS/OS X 코드 예제

이 항목에서는 iOS/OS X 버전의 RMS SDK에 대한 중요한 코드 요소를 소개합니다.

**참고** 뒤에 나오는 예제 코드 및 설명에서는 MSIPC(Microsoft 정보 보호 및 제어)라는 용어를 사용하여 클라이언트 프로세스를 가리킵니다.

 

##Microsoft Rights Management SDK 4.2 사용 - 주요 시나리오


다음은 이 SDK를 이해하는 데 중요한 개발 시나리오를 나타내는 큰 샘플 응용 프로그램에서 가져온 **Objective C** 코드 예제입니다. 이 예제에서는 보호된 파일이라고 지칭되는 Microsoft 보호된 파일 형식 사용, 사용자 지정 보호된 파일 형식 사용 및 사용자 지정 UI 컨트롤 사용을 보여 줍니다.

###시나리오: RMS 보호된 파일 사용


- **1단계**: [**MSProtectedData**](/rights-management/sdk/4.2/api/iOS/msprotectedd) 개체를 만듭니다.

 **설명**: [**MSAuthenticationCallback**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msauthenticationcallback_protocol_objc)을 사용하고 **MSAuthenticationCallback** 인스턴스를 *authenticationCallback* 매개 변수로 MSIPC API에 전달하여 토큰을 가져와서 서비스 인증을 구현하는 해당 create 메서드를 통해 [**MSProtectedData**](/rights-management/sdk/4.2/api/iOS/msprotectedd) 개체를 인스턴스화합니다. 다음 예제 코드 섹션에서 [**protectedDataWithProtectedFile**](/rights-management/sdk/4.2/api/iOS/msprotecteddata#msipcthin2_msprotecteddata_protecteddatawithprotectedfile_completionblock_method_objc) 호출을 참조하세요.

        + (void)consumePtxtFile:(NSString *)path authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // userId can be provided as a hint for authentication
            [MSProtectedData protectedDataWithProtectedFile:path
                                                 userId:nil
                                 authenticationCallback:authenticationCallback
                                                options:Default
                                        completionBlock:^(MSProtectedData *data, NSError *error)
            {
                //Read the content from the ProtectedData, this will decrypt the data
                NSData *content = [data retrieveData];
            }];
        }

- **2단계**: ADAL(Active Directory 인증 라이브러리)을 사용하여 인증을 설정합니다.

  **설명**: 이 단계에서는 [**MSAuthenticationCallback**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msauthenticationcallback_protocol_objc)을 구현하는 데 사용되는 ADAL과 예제 인증 매개 변수를 확인할 수 있습니다. ADAL을 사용하는 방법에 대한 자세한 내용은 Azure ADAL(AD 인증 라이브러리)을 참조하세요.

      // AuthenticationCallback holds the necessary information to retrieve an access token.
      @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

      @end

      @implementation MsipcAuthenticationCallback

      - (void)accessTokenWithAuthenticationParameters:
             (MSAuthenticationParameters *)authenticationParameters
                                    completionBlock:
             (void(^)(NSString *accessToken, NSError *error))completionBlock
      {
          ADAuthenticationError *error;
          ADAuthenticationContext* context = [
              ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority
                                                                error:&amp;error
          ];
          NSString *appClientId = @”com.microsoft.sampleapp”;
          NSURL *redirectURI = [NSURL URLWithString:@"local://authorize"];
          // Retrieve token using ADAL
          [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result) {
                              if (result.status != AD_SUCCEEDED)
                              {
                                  NSLog(@"Auth Failed");
                                  completionBlock(nil, result.error);
                              }
                              else
                              {
                                  completionBlock(result.accessToken, result.error);
                              }
                          }];
       }

-   **3단계**: [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc) 개체의 [**accessCheck**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_accesscheck_method_objc) 메서드를 통해 이 사용자에게 이 콘텐츠에 대한 편집 권한이 있는지 확인합니다.

        - (void)accessCheckWithProtectedData:(MSProtectedData *)protectedData
        {
            //check if user has edit rights and apply enforcements
            if (!protectedData.userPolicy.accessCheck(EditableDocumentRights.Edit))
            {
                // enforce on the UI
                textEditor.focusableInTouchMode = NO;
                textEditor.focusable = NO;
                textEditor.enabled = NO;
            }
        }

### 시나리오: 템플릿을 사용하여 새 보호된 파일 만들기

이 시나리오에서는 먼저 템플릿 목록 [**MSTemplateDescriptor**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_mstemplatedescriptor_interface_objc)를 가져오고 첫 번째 템플릿을 선택하여 정책을 만든 다음 새 보호된 파일을 만들어서 씁니다.

-   **1단계**: 템플릿 목록을 가져옵니다.

        + (void)templateListUsageWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSTemplateDescriptor templateListWithUserId:@"user@domain.com"
                            authenticationCallback:authenticationCallback
                                   completionBlock:^(NSArray/*MSTemplateDescriptor*/ *templates, NSError *error)
                                   {
                                     // use templates array of MSTemplateDescriptor (Note: will be nil on error)
                                   }];
        }

-   **2단계**: 목록의 첫 번째 템플릿 파일을 사용하여 [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc)를 만듭니다.

        + (void)userPolicyCreationFromTemplateWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSUserPolicy userPolicyWithTemplateDescriptor:[templates objectAtIndex:0]
                                            userId:@"user@domain.com"
                                     signedAppData:nil
                            authenticationCallback:authenticationCallback
                                           options:None
                                   completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
            // use userPolicy (Note: will be nil on error)
            }];
        }

-   **3단계**: [**MSMutableProtectedData**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msmutableprotecteddata_interface_objc)를 만들고 파일에 콘텐츠를 씁니다.

        + (void)createPtxtWithUserPolicy:(MSUserPolicy *)userPolicy contentToProtect:(NSData *)contentToProtect
        {
            // create an MSMutableProtectedData to write content
            [contentToProtect protectedDataInFile:filePath
                        originalFileExtension:kDefaultTextFileExtension
                               withUserPolicy:userPolicy
                              completionBlock:^(MSMutableProtectedData *data, NSError *error)
            {
             // use data (Note: will be nil on error)
            }];
        }

### 시나리오: 사용자 지정 보호된 파일 열기


-   **1단계**: *serializedContentPolicy*에서 [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc)를 만듭니다.

        + (void)userPolicyWith:(NSData *)protectedData
        authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // Read header information from protectedData and extract the  PL
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger serializedPolicySize;
            NSMutableData *serializedPolicy;
            [protectedData getBytes:&amp;serializedPolicySize length:sizeof(serializedPolicySize)];
            [protectedData getBytes:[serializedPolicy mutableBytes] length:serializedPolicySize];

            // Get the user policy , this is an async method as it hits the REST service
            // for content key and usage restrictions
            // userId provided as a hint for authentication
            [MSUserPolicy userPolicyWithSerializedPolicy:serializedPolicy
                                              userId:@"user@domain.com"
                              authenticationCallback:authenticationCallback
                                             options:Default
                                     completionBlock:^(MSUserPolicy *userPolicy,
                                                       NSError *error)
            {

            }];
         }

-   **2단계**: **1단계**에서 만든 [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc)를 사용하여 [**MSCustomProtectedData**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_mscustomprotecteddata_interface_objc)를 만들고 읽습니다.

        + (void)customProtectedDataWith:(NSData *)protectedData
        {
            // Read header information from protectedData and extract the  protectedContentSize
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger protectedContentSize;
            [protectedData getBytes:&amp;protectedContentSize
                         length:sizeof(protectedContentSize)];

            // Create the MSCustomProtector used for decrypting the content
            // The content start position is the header length
            [MSCustomProtectedData customProtectedDataWithPolicy:userPolicy
                                               protectedData:protectedData
                                        contentStartPosition:sizeof(NSUInteger) + serializedPolicySize
                                                 contentSize:protectedContentSize
                                             completionBlock:^(MSCustomProtectedData *customProtector,
                                                               NSError *error)
            {
             //Read the content from the custom protector, this will decrypt the data
             NSData *content = [customProtector retrieveData];
             NSLog(@"%@", content);
            }];
         }

### 시나리오: 사용자 지정(임시) 정책을 사용하여 사용자 지정 보호된 파일 만들기


-   **1단계**: 사용자가 제공한 메일 주소를 사용하여 정책 설명자를 만듭니다.

    **설명**: 실제로 다음 개체는 장치 인터페이스 [**MSUserRights**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserrights_interface_objc) 및 [**MSPolicyDescriptor**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc)의 사용자 입력을 사용하여 생성됩니다.

        + (void)policyDescriptor
        {
            MSUserRights *userRights = [[MSUserRights alloc] initWithUsers:[NSArray arrayWithObjects: @"user1@domain.com", @"user2@domain.com", nil] rights:[MSEmailRights all]];

            MSPolicyDescriptor *policyDescriptor = [[MSPolicyDescriptor alloc] initWithUserRights:[NSArray arrayWithObjects:userRights, nil]];
            policyDescriptor.contentValidUntil = [[NSDate alloc] initWithTimeIntervalSinceNow:NSTimeIntervalSince1970 + 3600.0];
            policyDescriptor.offlineCacheLifetimeInDays = 10;
        }

-   **2단계**: 정책 설명자 *selectedDescriptor*에서 사용자 지정 [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc)를 만듭니다.

        + (void)userPolicyWithPolicyDescriptor:(MSPolicyDescriptor *)policyDescriptor
        {
            [MSUserPolicy userPolicyWithPolicyDescriptor:policyDescriptor
                                          userId:@"user@domain.com"
                          authenticationCallback:authenticationCallback
                                         options:None
                                 completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
              // use userPolicy (Note: will be nil on error)
            }];
        }

-   **3단계**: [**MSMutableCustomProtectedData**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msmutablecustomprotecteddata_interface_objc)를 만들고 콘텐츠를 쓴 다음 닫습니다.

        + (void)mutableCustomProtectedData:(NSMutableData *)backingData policy:(MSUserPolicy *)policy contentToProtect:(NSString *)contentToProtect
        {
            //Get the serializedPolicy from a given policy
            NSData *serializedPolicy = [policy serializedPolicy];

            // Write header information to backing data including the PL
            // ------------------------------------
            // | PL length | PL | ContetSizeLength |
            // -------------------------------------
            NSUInteger serializedPolicyLength = [serializedPolicy length];
            [backingData appendData:[NSData dataWithBytes:&amp;serializedPolicyLength length:sizeof(serializedPolicyLength)]];
            [backingData appendData:serializedPolicy];
            NSUInteger protectedContentLength = [MSCustomProtectedData getEncryptedContentLengthWithPolicy:policy contentLength:unprotectedData.length];
            [backingData appendData:[NSData dataWithBytes:&amp;protectedContentLength length:sizeof(protectedContentLength)]];

            NSUInteger headerLength = sizeof(serializedPolicyLength) + serializedPolicyLength + sizeof(protectedContentLength);

            // Create the MSMutableCustomProtector used for encrypting content
            // The content start position is the current length of the backing data
            // The encryptedContentSize content size is 0 since there is no content yet
            [MSMutableCustomProtectedData customProtectorWithUserPolicy:policy
                                                        backingData:backingData
                                             protectedContentOffset:headerLength
                                                    completionBlock:^(MSMutableCustomProtectedData *customProtector,
                                                                      NSError *error)
            {
                //Append data to the custom protector, this will encrypt the data and write it to the backing data
                [customProtector appendData:[contentToProtect dataUsingEncoding:NSUTF8StringEncoding] error:&amp;error];

                //close the custom protector so it will flush and finalise encryption
                [customProtector close:&amp;error];

            }];
          }


 

 

<!--HONumber=Apr16_HO4-->


