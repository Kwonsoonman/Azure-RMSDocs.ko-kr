---
title: Android 코드 예제 | Azure RMS
description: 이 항목에서는 Android 버전의 RMS SDK에 대한 중요한 코드 요소를 소개합니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: 58CC2E50-1E4D-4621-A947-25312C3FF519
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 7a0f49d540abff1e4e2fbdd5dbf937590ea1fc60
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42803750"
---
# <a name="android-code-examples"></a>Android 코드 예제

이 문서에서는 Android 버전의 RMS SDK 요소를 코딩하는 방법을 보여줍니다.

**참고**: 이 문서에서 ‘MSIPC’(Microsoft 정보 보호 및 제어)라는 용어는 클라이언트 프로세스를 의미합니다.


## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Microsoft Rights Management SDK 4.2 사용 - 주요 시나리오

이러한 코드 샘플은 이 SDK를 이해하는 데 중요한 개발 시나리오를 나타내는 더 큰 응용 프로그램 예제에서 가져옵니다. 다음을 사용하는 방법을 보여줍니다.

- ‘보호된 파일’이라고도 하는 Microsoft Protected File 형식입니다.
- 사용자 정의 보호된 파일 형식
- 사용자 정의 UI(사용자 인터페이스) 컨트롤

‘MSIPCSampleApp’ 응용 프로그램 예제는 Android 운영 체제용 SDK와 함께 사용할 수 있습니다. 자세한 내용은 [rms-sdk-ui-for-android](https://github.com/AzureAD/rms-sdk-ui-for-android)를 참조하세요.

### <a name="scenario-consume-an-rms-protected-file"></a>시나리오: RMS 보호된 파일 사용

- **1단계**: [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx)을 만듭니다.

    **원본**: *MsipcAuthenticationCallback.java*

    **설명**: [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx) 개체를 인스턴스화하고 서비스 인증을 구현합니다.  [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758250.aspx)을 통해 **AuthenticationRequestCallback**의 인스턴스를 ‘mRmsAuthCallback’ 매개 변수로 MSIPC API에 전달하여 토큰을 가져옵니다. 다음 예제 코드 섹션의 끝에 있는 [ProtectedFileInputStream.create](https://msdn.microsoft.com/library/dn790851.aspx) 호출을 참조하세요.

    ``` java
        public void startContentConsumptionFromPtxtFileFormat(InputStream inputStream)
        {
            CreationCallback<ProtectedFileInputStream> protectedFileInputStreamCreationCallback =
              new CreationCallback<ProtectedFileInputStream>()
            {
                @Override
                public Context getContext()
                {
                   …
               }

                @Override
                public void onCancel()
                {
                   …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                   …
                }

                @Override
                public void onSuccess(ProtectedFileInputStream protectedFileInputStream)
                {
                   …
                   …
                    byte[] dataChunk = new byte[16384];
                    try
                    {
                        while ((nRead = protectedFileInputStream.read(dataChunk, 0,
                                dataChunk.length)) != -1)
                        {
                            …
                        }
                         …
                        protectedFileInputStream.close();
                    }
                    catch (IOException e)
                    {
                      …
                    }  
              }
            };
            try
            {
               …
                ProtectedFileInputStream.create(inputStream, null, mRmsAuthCallback,
                                                PolicyAcquisitionFlags.NONE,
                                                protectedFileInputStreamCreationCallback);
            }
            catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
            {
                …
            }
        }
    ```

- **2단계**: ADAL(Active Directory 인증 라이브러리)을 사용하여 인증을 설정합니다.

    **원본**: *MsipcAuthenticationCallback.java*.

    **설명**: 이 단계에서는 예제 인증 매개 변수와 함께 ADAL을 사용하여 [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx)을 구현합니다. 자세한 내용은 [ADAL(Azure AD 인증 라이브러리)](https://msdn.microsoft.com/library/jj573266.aspx)을 참조하세요.


    ``` java
        class MsipcAuthenticationCallback implements AuthenticationRequestCallback
        {

        …

        @Override
        public void getToken(Map<String, String> authenticationParametersMap,
                             final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
        {
            String authority = authenticationParametersMap.get("oauth2.authority");
            String resource = authenticationParametersMap.get("oauth2.resource");
            String userId = authenticationParametersMap.get("userId");
            final String userHint = (userId == null)? "" : userId;
            AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
            if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
            {
                try
                {
                    authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                    App.getInstance().setAuthenticationContext(authenticationContext);
                }
                catch (NoSuchAlgorithmException e)
                {
                    …
                    authenticationCompletionCallbackToMsipc.onFailure();
                }
                catch (NoSuchPaddingException e)
                {
                    …
                    authenticationCompletionCallbackToMsipc.onFailure();
                }
           }
            App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                           "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                            {
                                @Override
                                public void onError(Exception exc)
                                {
                                    …
                                    if (exc instanceof AuthenticationCancelError)
                                    {
                                         …
                                        authenticationCompletionCallbackToMsipc.onCancel();
                                    }
                                    else
                                    {
                                         …
                                        authenticationCompletionCallbackToMsipc.onFailure();
                                    }
                                }

                                @Override
                                public void onSuccess(AuthenticationResult result)
                                {
                                    …
                                    if (result == null || result.getAccessToken() == null
                                            || result.getAccessToken().isEmpty())
                                    {
                                         …
                                    }
                                    else
                                    {
                                        // request is successful
                                        …
                                        authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                    }
                                }
                            }

                            );
                      }
    ```

- **3단계**: [UserPolicy.accessCheck](https://msdn.microsoft.comlibrary/dn790885.aspx) 메서드를 통해 이 사용자에게 이 콘텐츠에 대한 **편집** 권한이 있는지 확인합니다.

    **원본**: *TextEditorFragment.java*

    ``` java
         //check if user has edit rights and apply enforcements
                if (!mUserPolicy.accessCheck(EditableDocumentRights.Edit))
                {
                    mTextEditor.setFocusableInTouchMode(false);
                    mTextEditor.setFocusable(false);
                    mTextEditor.setEnabled(false);
                    …
                }
    ```


### <a name="scenario-create-a-new-protected-file-using-a-template"></a>시나리오: 템플릿을 사용하여 새 보호된 파일 만들기

이 시나리오에서는 먼저 템플릿 목록을 가져오고 첫 번째 템플릿을 선택하여 정책을 만든 다음 새 보호된 파일을 만들어서 씁니다.

- **1단계**: [TemplateDescriptor](https://msdn.microsoft.com/library/dn790871.aspx) 개체를 통해 템플릿 목록을 가져옵니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
    CreationCallback<List<TemplateDescriptor>> getTemplatesCreationCallback = new CreationCallback<List<TemplateDescriptor>>()
      {
          @Override
          public Context getContext()
          {
              …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(List<TemplateDescriptor> templateDescriptors)
          {
             …
          }
      };
      try
      {
              …
          mIAsyncControl = TemplateDescriptor.getTemplates(emailId, mRmsAuthCallback, getTemplatesCreationCallback);
      }
      catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
      {
              …
      }
    ```

- **2단계**: 목록의 첫 번째 템플릿 파일을 사용하여 [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)를 만듭니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
      CreationCallback<UserPolicy> userPolicyCreationCallback = new CreationCallback<UserPolicy>()
      {
          @Override
          public Context getContext()
          {
              …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(final UserPolicy item)
          {
              …
          }
      };
      try
      {
           …
          mIAsyncControl = UserPolicy.create((TemplateDescriptor)selectedDescriptor, mEmailId, mRmsAuthCallback,
                            UserPolicyCreationFlags.NONE, userPolicyCreationCallback);
           …
      }
      catch (InvalidParameterException e)
      {
              …
      }
    ```

-  **3단계**: [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx)을 만들고 파일에 콘텐츠를 씁니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
    private void createPTxt(final byte[] contentToProtect)
        {
             …
            CreationCallback<ProtectedFileOutputStream> protectedFileOutputStreamCreationCallback = new CreationCallback<ProtectedFileOutputStream>()
            {
                @Override
                public Context getContext()
                {
                 …
                }

                @Override
                public void onCancel()
                {
                 …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                 …
                }

                @Override
                public void onSuccess(ProtectedFileOutputStream protectedFileOutputStream)
                {
                    try
                    {
                        // write to this stream
                        protectedFileOutputStream.write(contentToProtect);
                        protectedFileOutputStream.flush();
                        protectedFileOutputStream.close();
                        …
                    }
                    catch (IOException e)
                    {
                        …
                    }
                }
            };
            try
            {
                File file = new File(filePath);
                outputStream = new FileOutputStream(file);
                mIAsyncControl = ProtectedFileOutputStream.create(outputStream, mUserPolicy, originalFileExtension,
                        protectedFileOutputStreamCreationCallback);
            }
            catch (FileNotFoundException e)
            {
                 …
            }
            catch (InvalidParameterException e)
            {
                 …
            }
        }
    ```


### <a name="scenario-open-a-custom-protected-file"></a>시나리오: 사용자 지정 보호된 파일 열기

- **1단계**: *serializedContentPolicy*에서 [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)를 만듭니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
    CreationCallback<UserPolicy> userPolicyCreationCallbackFromSerializedContentPolicy = new CreationCallback<UserPolicy>()
            {
                @Override
                public void onSuccess(UserPolicy userPolicy)
                {
                  …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                  …
                }

                @Override
                public void onCancel()
                {
                  …
                }

                @Override
                public Context getContext()
                {
                  …
                }
            };


    try
    {
      ...

      // Read the serializedContentPolicyLength from the inputStream.
      long serializedContentPolicyLength = readUnsignedInt(inputStream);

      // Read the PL bytes from the input stream using the PL size.
      byte[] serializedContentPolicy = new byte[(int)serializedContentPolicyLength];
      inputStream.read(serializedContentPolicy);

      ...

      UserPolicy.acquire(serializedContentPolicy, null, mRmsAuthCallback, PolicyAcquisitionFlags.NONE,
              userPolicyCreationCallbackFromSerializedContentPolicy);
    }
    catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
    {
      ...
    }
    catch (IOException e)
    {
      ...
    }
    ```


- **2단계**: **1단계**의 [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)를 사용하여 [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx)을 만듭니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
      CreationCallback<CustomProtectedInputStream> customProtectedInputStreamCreationCallback = new CreationCallback<CustomProtectedInputStream>()
      {
         @Override
         public Context getContext()
         {
             …
         }

         @Override
         public void onCancel()
         {
             …
         }

         @Override
         public void onFailure(ProtectionException e)
         {
             …
         }

         @Override
         public void onSuccess(CustomProtectedInputStream customProtectedInputStream)
         {
            …

             byte[] dataChunk = new byte[16384];
             try
             {
                 while ((nRead = customProtectedInputStream.read(dataChunk, 0, dataChunk.length)) != -1)
                 {
                      …
                 }
                  …
                 customProtectedInputStream.close();
             }
             catch (IOException e)
             {
                …
             }
             …
         }
     };

    try
    {
      ...

      // Retrieve the encrypted content size.
      long encryptedContentLength = readUnsignedInt(inputStream);

      updateTaskStatus(new TaskStatus(TaskState.Starting, "Consuming content", true));

      CustomProtectedInputStream.create(userPolicy, inputStream,
                                     encryptedContentLength,
                                     customProtectedInputStreamCreationCallback);
    }
    catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
    {
      ...
    }
    catch (IOException e)
    {
      ...
    }
    ```

- **3단계**: [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx)의 콘텐츠를 *mDecryptedContent*로 읽어온 다음 닫습니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
    @Override
    public void onSuccess(CustomProtectedInputStream customProtectedInputStream)
    {
      mUserPolicy = customProtectedInputStream.getUserPolicy();
      ByteArrayOutputStream buffer = new ByteArrayOutputStream();

      int nRead;                      
      byte[] dataChunk = new byte[16384];

      try
      {
        while ((nRead = customProtectedInputStream.read(dataChunk, 0,
                                                            dataChunk.length)) != -1)
        {
           buffer.write(dataChunk, 0, nRead);
        }

        buffer.flush();
        mDecryptedContent = new String(buffer.toByteArray(), Charset.forName("UTF-8"));

        buffer.close();
        customProtectedInputStream.close();
      }
      catch (IOException e)
      {
        ...
      }
    }
    ```

### <a name="scenario-create-a-custom-protected-file-using-a-custom-policy"></a>시나리오: 사용자 지정 정책을 사용하여 사용자 지정 보호된 파일 만들기

- **1단계**: 사용자가 제공한 메일 주소를 사용하여 정책 설명자를 만듭니다.

    **원본**: *MsipcTaskFragment.java*

    **설명**: 실제로 다음 개체는 장치 인터페이스 [UserRights](https://msdn.microsoft.com/library/dn790911.aspx) 및 [PolicyDescriptor](https://msdn.microsoft.com/library/dn790843.aspx)의 사용자 입력을 사용하여 생성됩니다.

    ``` java
      // create userRights list
      UserRights userRights = new UserRights(Arrays.asList("consumer@domain.com"),
        Arrays.asList( CommonRights.View, EditableDocumentRights.Print));
      ArrayList<UserRights> usersRigthsList = new ArrayList<UserRights>();
      usersRigthsList.add(userRights);

      // Create PolicyDescriptor using userRights list
      PolicyDescriptor policyDescriptor = PolicyDescriptor.createPolicyDescriptorFromUserRights(
                                                             usersRigthsList);
      policyDescriptor.setOfflineCacheLifetimeInDays(10);
      policyDescriptor.setContentValidUntil(new Date());
    ```


- **2단계**: 정책 설명자 *selectedDescriptor*에서 사용자 지정 [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)를 만듭니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
       mIAsyncControl = UserPolicy.create((PolicyDescriptor)selectedDescriptor,
         mEmailId, mRmsAuthCallback, UserPolicyCreationFlags.NONE, userPolicyCreationCallback);
    ```


- **3단계**: [CustomProtectedOutputStream](https://msdn.microsoft.com/library/dn758274.aspx)을 만들고 콘텐츠를 쓴 다음 닫습니다.

    **원본**: *MsipcTaskFragment.java*

    ``` java
    File file = new File(filePath);
        final OutputStream outputStream = new FileOutputStream(file);
        CreationCallback<CustomProtectedOutputStream> customProtectedOutputStreamCreationCallback = new CreationCallback<CustomProtectedOutputStream>()
        {
            @Override
            public Context getContext()
            {
              …
            }

            @Override
            public void onCancel()
            {
              …
            }

            @Override
            public void onFailure(ProtectionException e)
            {
              …
            }

            @Override
            public void onSuccess(CustomProtectedOutputStream protectedOutputStream)
            {
                try
                {
                    // write serializedContentPolicy
                    byte[] serializedContentPolicy = mUserPolicy.getSerializedContentPolicy();
                    writeLongAsUnsignedIntToStream(outputStream, serializedContentPolicy.length);
                    outputStream.write(serializedContentPolicy);
                    // write encrypted content
                    if (contentToProtect != null)
                    {
                        writeLongAsUnsignedIntToStream(outputStream,
                                CustomProtectedOutputStream.getEncryptedContentLength(contentToProtect.length,
                                        protectedOutputStream.getUserPolicy()));
                        protectedOutputStream.write(contentToProtect);
                        protectedOutputStream.flush();
                        protectedOutputStream.close();
                    }
                    else
                    {
                        outputStream.flush();
                        outputStream.close();
                    }
                    …
                }
                catch (IOException e)
                {
                  …
                }
            }
        };
        try
        {
            mIAsyncControl = CustomProtectedOutputStream.create(outputStream, mUserPolicy,
                    customProtectedOutputStreamCreationCallback);
        }
        catch (InvalidParameterException e)
        {
          …
        }
    ```
