---
title: "Azure 포털에서 RMS 인증을 위해 구성 | Azure RMS"
description: "ADAL 인증을 위한 프로세스를 간략히 설명합니다."
keywords: "인증, RMS, ADAL"
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2680b399-febb-4bd6-b844-ac3d1e69aca4
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: eb9cea79d9e5a7902839d34d9b4f13bdefe5a5d3


---

# 방법: Azure 포털에서 RMS 인증을 위해 구성

Azure ADAL(Active Directory 인증 라이브러리)을 사용하여 Azure RMS에 앱을 인증합니다.

응용 프로그램에서 자체 OAuth 인증을 관리하려는 경우 이 방법을 사용합니다. 이 방법의 경우 인증이 필요할 때 RMS 클라이언트에서 응용 프로그램 정의 콜백을 실행합니다.

## Azure 포털을 통해 구성
Azure 포털을 통해 앱의 등록을 구성하려면 이 가이드에 따라 [ADAL 인증을 위해 Azure RMS 구성](adal-auth.md)부터 수행합니다. 나중에 사용할 수 있도록 이 프로세스에서 *클라이언트 ID* 및 *리디렉션 URI*를 복사하여 저장해야 합니다.

## 코드 샘플
다음은 모바일 클라이언트 코드에서 Azure ADAL을 사용하기 위한 큰 샘플에서 가져온 코드 조각입니다. 자세한 내용은 [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)에 있는 전체 샘플을 참조하세요.

       /**
       * Instantiates a new rms authentication callback.
       *
       * @param parentActivity the parent activity
       * @throws NoSuchAlgorithmException the no such algorithm exception
       * @throws InvalidKeySpecException the invalid key spec exception
       * @throws UnsupportedEncodingException the unsupported encoding exception
       */

       public MsipcAuthenticationCallback(Activity parentActivity) throws NoSuchAlgorithmException, InvalidKeySpecException, UnsupportedEncodingException
       {
         mParentActivity = parentActivity;
         setADALKeyStore();

         /**
         * Note: Following values of are client_id and redirect_uri are for demo purpose only.
         * Your values will come from the preceeding Azure Portal process.
         */
         mClientId = "com.microsoft.rightsmanagement.sampleapp";
         mRedirectURI = mClientId + "://authorize";
       }


## 관련 항목

- [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)
- [ADAL 인증을 위해 Azure RMS 구성](adal-auth.md)



<!--HONumber=Sep16_HO5-->


