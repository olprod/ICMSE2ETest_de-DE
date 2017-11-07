---
title: "Windows Phone における条件付きアクセスのエンド ユーザー エクスペリエンス"
description: "Windows Phone を登録するエンド ユーザー エクスペリエンスです。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 906566e0-f05e-4af5-b4d5-0efb083dca76
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 523ac8f389a1830e79afc717e8af2bc99169c09e
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="windows-phone"></a>Windows Phone

登録プロセスおよび表示される画面は、エンド ユーザーのデバイスで実行されている OS のバージョンによって多少異なります。  このトピックでは、Windows Telefon を登録するためのエンド ユーザー エクスペリエンスについて説明します。

## <a name=""></a>登録

1.  ユーザーが既に Intune に登録されており準拠している場合は、Windows デバイスでの違いはありません。 引き続き電子メールにアクセスできます。 Intune にまだ登録していないユーザーには、次の例のような検疫電子メールが表示されます。

    ![ユーザーが受信する検疫電子メールのスクリーンショット (Windows Phone)](./media/ProtectEmail/EUX-Windows-quarantineEmail.png)

    
            **[今すぐ開始]** をクリックすると、デバイスの登録が開始されます。

2.  [会社アクセスのセットアップ] 画面で**[開始]**をクリックして、デバイスの設定およびデバイスが準拠しているかどうかの確認を開始します。

    ![[会社アクセスのセットアップ] 画面のスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows1-company-Access-Setup.png)

3.  [デバイスの登録] 画面で**[登録の確認]**をクリックして、デバイスの登録を開始します。

    ![[デバイスの登録] 画面のスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows3-enroll-Device.png)

    登録中に、モバイル デバイス管理プロファイルがインストールされ、IT 管理者はデバイスをリモートで管理できるようになります。 ユーザーは、社内参加を承認する証明書に同意するように求められる可能性があります。

    ![社内参加のスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows4-workplaceJoin1.png)

4.  Office で使用している電子メール アドレスを使用してサインインします。 サインイン後、再度**[登録の確認]**をクリックして、デバイスの登録を続行する必要がある場合があります。

    ![社内参加の実行中のスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows5-workplaceJoin2.png)

    デバイスが登録されているかどうかの確認が行われます。

    ![デバイス登録の開始のスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows6-checking-Enrollment.png)

5.  自分のデバイスを選択し、 **[選択]**をクリックして登録プロセスを完了します。 デバイスが表示されない場合は、 **[デバイスが表示されません]**を選択してもう一度やり直してください。

    ![ユーザーによる Windows Phone 用デバイスの確認が必要であることを示すスクリーン ショット](./media/ProtectEmail/EUX-Windows7-confirm-Device.png)

    デバイスが会社のポリシーに準拠しているかどうかの確認が行われます。

    ![Windows Phone のポリシー準拠チェック中のスクリーン ショット](./media/ProtectEmail/EUX-Windows9-checking-Compliance.png)

6.  準拠に関して問題がある場合は、問題を解決してから (有効なパスワードの作成など) 、 **[ポリシー準拠状況の確認]**をクリックして続行するように求められます。

    ![ユーザーによるポリシー準拠問題の解決が必要であることを示すスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows13-resolve-Compliance.png)

    準拠状況の確認後、登録がアクティブ化されたことが示されます。

    ![登録のアクティブ化の開始のスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows10-activating-Enrollment.png)

7.  登録がアクティブ化されたら、 **[続行]**をクリックしてプロセスを完了します。 をクリックしてセットアップを終了します。         **[完了]**

    ![会社アクセスのセットアップ完了時のスクリーン ショット (Windows Phone)](./media/ProtectEmail/EUX-Windows11-COMPLETE.png)

    ユーザーの登録および準拠の確認後、数分以内に電子メールにアクセスできるようになります。

これらの手順を実行して登録を行い準拠を確認した後、まだモバイル デバイスから電子メールにアクセスできない場合は、次の追加手順に従って問題を解決してください。

-   最初に、そのデバイスが登録されていることを確認します。 登録されていない場合は、上記の手順に従います。

-   
            **[ポリシー準拠状況の確認]**をクリックして、デバイスが準拠していることを確認します。 準拠エラーが識別される場合は、パスワードをリセットするなど、解決策についてモバイル デバイスに固有の指示に従います。

-   ヘルプ デスクに連絡します。

## <a name=""></a>問題と解決策
既定では、8 時間ごとにデバイスがポリシーに準拠しているかどうかがチェックされます。 以前は準拠していたデバイスが、 (たとえば、コンプライアンス ポリシーが追加または変更されたため) 後で準拠しなくなった場合は、次の手順に従ってデバイスの準拠状況を戻すことができます。

1.  デバイスが準拠していないことを示す通知を、電子メールまたはデバイスで受け取ります。 この時点で、デバイスは Exchange で検疫されます。

2.  ユーザーが電子メールにアクセスしようとすると、Intune ポータル サイトから [会社アクセスのセットアップ] 画面にリダイレクトされ、準拠しなくなったことが示されます。

    ![Windows Phone がポリシーに準拠していないことを示すスクリーン ショット](./media/ProtectEmail/EUX-Windows14-OutOfCompliance.png)

3.  
            をクリックすると、電子メールへのアクセスを妨げている準拠の問題が示されます。 **[続行]**

4.  問題を解決した後、 **[ポリシー準拠状況の確認]**をクリックして、問題が解決されたことを確認します。

5.  問題が解決されたら、 **[続行]**をクリックしてプロセスを完了します。 電子メールへのアクセスは、数分以内に再度使用可能になります。

### <a name=""></a>この後の対応
他のモバイル デバイスのエンド ユーザー エクスペリエンスは若干異なります。             [Android](end-user-experience-conditional-access-android.md)および[iOS](end-user-experience-conditional-access-ios.md)のエンド ユーザー エクスペリエンスについて詳しく説明します。
