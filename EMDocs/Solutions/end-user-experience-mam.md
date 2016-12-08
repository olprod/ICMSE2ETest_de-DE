---
title: "MAM のエンドユーザー エクスペリエンス"
description: "モバイル アプリ管理ポリシーのエンドユーザー エクスペリエンス。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc9f6ea-fc92-468d-bb5b-60c67949ca28
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 0fcbeb0e5c1333954c51c4a35fb680c0b9deb401
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>モバイル アプリ管理ポリシーのエンドユーザー エクスペリエンス
MAM ポリシーは、アプリが作業コンテキストで使用されている場合にのみ適用されます。 次のシナリオ例は、管理対象アプリの動作方法をユーザーが理解できるように教育する上で役立ちます。

ここでは、次のエンド ユーザー エクスペリエンスの例を示します。

- シナリオ: iOS デバイスで OneDrive にアクセスする
- シナリオ: Android デバイスで OneDrive にアクセスする

その他の特定のエンド ユーザー エクスペリエンスについては、次の記事をご覧ください。

- [複数の ID を使用するアプリのサポート](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#using-apps-with-multi-identity-support)
- [ユーザー アカウントの管理](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#managing-user-accounts)
- [Rights Management 共有アプリを使用したメディア ファイルの表示](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)

## <a name="-ios-onedrive-"></a>シナリオ: iOS デバイスで OneDrive にアクセスする

1. ユーザーが**OneDrive**アプリを起動し、サインイン ページを開きます。
> [!NOTE]
> 個人用デバイスの場合は、通常、エンドユーザーがアプリをダウンロードします。 デバイスが MDM ソリューションで管理されている場合は、管理者がアプリをデバイスに展開できます。

2. ユーザーが作業アカウントのユーザー名を入力すると、作業用の資格情報を入力する**O365 認証**ページにリダイレクトされます。

  Azure AD によって資格情報が正しく認証されると、MAM ポリシーが適用されます。
3. ユーザーは (ポリシーで構成している場合) アプリの**PIN**を設定するよう求められます。

4.  PIN-NUMMER を設定し確認すると、ユーザーは**OneDrive for Business**のファイルにアクセスできるようになります。
> [!NOTE]
> 展開済みのポリシーを変更すると、次回アプリを開いたときにその変更が適用されます。

## <a name="-android-onedrive-"></a>シナリオ: Android デバイスで OneDrive にアクセスする
1. ユーザーが**OneDrive**アプリを起動し、サインイン ページを開きます。
> [!NOTE]
> 個人用デバイスの場合は、通常、エンドユーザーがアプリをダウンロードします。 デバイスが MDM ソリューションで管理されている場合は、管理者がアプリをデバイスに展開できます。

2.  ユーザーが作業アカウントのユーザー名を入力すると、作業用の資格情報を入力する**O365 認証**ページにリダイレクトされます。

  Azure AD によって資格情報が正しく認証されると、MAM ポリシーが適用されます。

3.  
            **OneDrive**アプリへのアクセスにポリシー設定で**PIN**が必要であると設定されている場合、**OneDrive**アプリが自動的に起動され、ユーザーは**PIN**を設定するよう求められます。

4.  PIN-NUMMER が設定されて確認されると、アプリのポリシーで管理されるようになった**OneDrive**を継続して使用できます。

## <a name=""></a>この後の対応
エンド ユーザー エクスペリエンスの詳細については、「[複数の-ID を使用するアプリのサポート](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#using-apps-with-multi-identity-support)」、「[ユーザー アカウントの管理](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#managing-user-accounts)」、および「[Rights Management 共有アプリを使用したメディア ファイルの表示](https://docs.microsoft.com/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)」などをご覧ください。
