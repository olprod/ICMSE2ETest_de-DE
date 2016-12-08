---
title: "IT 管理者向けのエンドユーザー Intune 登録手順"
description: "IT 管理者向けのエンドユーザー Intune 登録手順"
keywords: 
author: craigcaseyMSFT
manager: jeffgilb
ms.date: 09/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 5c13446e-aa31-47df-ad9d-373be7660197
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 2a40e68c5257309563aac6a7bed7a1bff17d99d9
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="it-intune-"></a>IT 管理者向けのエンドユーザー Intune 登録手順

このドキュメントでは、管理者がカスタマイズできる登録手順について説明します。 また、ユーザーが自分の iOS デバイスと Android デバイスを Microsoft Intune™ (Windows デバイス用、Intune で Windows デバイスを使用する方法を参照してください) に登録できるようにする手順についても説明します。 このドキュメントから、ユーザーに最適と思われる部分をコピーすることをお勧めします。 たとえば、デバイス プラットフォームごとに 1 つのドキュメントを作成したり、スクリーンショットを増やしたりすることができます。

このような書面の手順に加え、[http://aka.ms/IntuneUserVideos](http://aka.ms/IntuneUserVideos)に掲載されている Intune エンド ユーザー向けビデオのハイパーリンクを含めることもできます。

> [!NOTE]
> Microsoft、Intune、および Office 365 は、Microsoft Corporation の登録商標です。 iPhone、Mac、および Apple は、Apple, Inc の商標です。 Android は Google Inc の商標です。 Samsung KNOX は Samsung Electronics Co. Ltd の商標です。

## <a name="intune-"></a>Intune に登録する理由
登録すると、モバイル デバイスを使用して職場や学校のファイルとデータにアクセスできるようになります。 また、IT 部門が職場や学校のリソースを管理してそれらの安全性を保持する一方で、ユーザーは好みのデバイスを使用して作業を進めることができます。

職場で自分のデバイスを使用するには、ポータル サイトを使用して Intune に登録します。 インストールする会社のアプリの検索、追加した他のデバイスの確認、IT 管理者の連絡先の検索が簡単になります。 また、使用しているデバイスの管理を IT 管理者に許可することで、デバイスに保存されている会社情報を保護しやすくすることもできます。 登録を開始する前に、Wi-Fi または携帯ネットワークのインターネット接続が良好であることを確認します。

## <a name="intune-intune-android-"></a>Intune ポータル サイト アプリを使用して Intune に Android デバイスを登録する

これらの登録手順は Samsung Knox Android デバイスと、 "ネイティブな" (Samsung Knox 以外の) Android デバイス用の手順です。 Samsung Knox デバイスがあるかどうかを判断するには、**[設定] 、 [端末情報]**の順に選択します。 "Knox" という単語がない場合、デバイスはネイティブ Android デバイスです。 デバイスの画面は、このセクションの画面とは少し異なる可能性があります。

Intune にデバイスを登録している最中にエラーが表示された場合は、「[IT 管理者に登録に関するエラーを送信する](https://technet.microsoft.com/en-US/library/mt502762(TechNet.10).aspx#BKMK_andr_send_enroll_errors)」を参照してください。

登録の前後に、デバイスの使用方法に適したカテゴリを選ぶように求められる場合があります。 IT-管理者は、このカテゴリを使用してアクセスできるアプリを判断します。
1.  
            [Google wiedergeben](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)から無料の Microsoft Intune ポータル サイト アプリをデバイスにインストールします。
2.  Microsoft Intune ポータル サイト アプリを開きます。
3.  ポータル サイトの**[ようこそ]**画面で、**[サインイン]**をタップし、職場または学校アカウントを使用してサインインします。

  ![Intune ポータル サイトのサインイン画面のスクリーンショット (Android デバイス)](./media/ft-userEnrollAndroid-1-signUp.png)

4.  IT-管理者によって会社の使用条件が設定されている場合は、**[同意する]**をタップして該当する条項に同意します。

  ![Android デバイスの使用条件に同意を求めるスクリーンショット](./media/ft-userEnrollAndroid-2-accept.png)
5.  Android 6.0 以降のデバイスを使用している場合は、この手順を実行してください。 それ以外の場合は、次の手順に進みます。

  IT-管理者が特定のポリシーを設定している場合は、次のメッセージのいずれかまたは両方が表示されることがあります。

  - 
            **"ポータル サイトに連絡先へのアクセスを許可しますか?"** というメッセージが表示されたら、**[許可]**をタップします。 Microsoft が連絡先にアクセスすることはないため、 [許可] をタップしても問題はありません。 Google がメッセージ テキストを制御しているため、Microsoft では変更できません。 アクセスを許可すると、ポータル サイト アプリがデバイスの問題をトラブルシューティングするために役立つデータ ログへのアクセスのみが許可されます。

        ![Screenshot in der Benutzer gefragt, um das Portal Access Kontakten für Android-Gerät zuzulassen](./media/ft-userEnrollAndroid-3-accessContacts.png)
  - 
            **"電話での通話とその管理をポータル サイトに許可しますか?"** というメッセージが表示される場合、**[許可]**をタップします。 Microsoft が通話や電話の管理を行うことはないため、 [許可] をタップしても問題はありません。 Google がメッセージ テキストを制御しているため、Microsoft では変更できません。 アクセスを許可しても、会社のポータル アプリが電話番号や IMEI と呼ばれる ID を確認することを許可しているだけです。

        ![Screenshot, der Benutzer zum Portal Telefonanrufe auf Android-Gerät verwalten zulassen](./media/ft-userEnrollAndroid-4-manageCalls.png)

  
            **[拒否]** をタップすると、次に会社のポータルにサインインしたときにもう一度メッセージが表示されますが、**[今後このメッセージを表示しない]** チェック ボックスをタップすると、メッセージ表示をオフにできます。 後でアクセスを許可する場合、**[設定]、[アプリ]、[ポータル サイト]、[アクセス許可]、[電話]** の順に移動して、アクセス許可を有効にします。
6.  職場または学校の電子メール アドレスとパスワードを使用してポータル サイト アプリにサインインし、**[サインイン]**をタップします。

  ![ポータル サイトにサインインするように求めるスクリーンショット (Android デバイス)](./media/ft-userEnrollAndroid-5-signIn.png)
7.  [会社アクセスのセットアップ] ページで、**[開始]**をタップします。

  ![[会社アクセスのセットアップ] ページのスクリーンショット (Android デバイス)](./media/ft-userEnrollAndroid-6-beginSetup.png)
8.  デバイスを登録すると可能になる操作についての説明を確認してから、**[続行]**をタップします。

  ![Android デバイスの登録が推奨される理由に関する情報のスクリーンショット](./media/ft-userEnrollAndroid-7-whyEnroll.png)
9.  IT 管理者が登録済みのデバイスに関して確認できる情報と確認できない情報についての一覧を確認し、**[続行]**をタップします。

  ![Android デバイスのプライバシー ポリシーを示すスクリーンショット](./media/ft-userEnrollAndroid-8-privacy.png)
10. をタップすると表示される可能性のあるいくつかの項目を確認します。 [登録] 読み終えたら、**[登録]**をタップします。

  ![これからの登録手順を示すスクリーン ショット (Android デバイス)](./media/ft-userEnrollAndroid-9-whatNext.png)
11. [デバイス管理者のアクティブ化] 画面で、**[アクティブ化]**をタップします。

  ![デバイス管理者をアクティブ化するように求めるスクリーンショット (Android デバイス)](./media/ft-userEnrollAndroid-10-activateAdmin.png)
12. 画面の指示に従って、PIN またはパスワードを入力します。 このデバイス上で PIN またはパスワードを既に設定している場合は、この画面は表示されず、新しい PIN またはパスワードを入力するように求められます。

  ![PIN-NUMMER を Android デバイスに入力するように求めるスクリーンショット](./media/ft-userEnrollAndroid-11-enterPIN.png)
13. と一致する次の手順に従います。 使用しているデバイスの種類 (ネイティブ Android または Samsung Knox) Samsung Knox デバイスを持っていない場合は、ネイティブ Android の手順に従います。 Samsung Knox デバイスがあるかどうかを判断するには、**[設定] 、 [端末情報]**の順に選択します。 "Knox" という単語がない場合、デバイスはネイティブ Android デバイスです。
 - ネイティブ (Samsung Knox 以外): **[証明書の名前指定]**画面で、**[OK]**をタップして既定の証明書を受け入れます。

        ![Screenshot prompting the user to accept the default certificate on a native Android device](./media/ft-userEnrollAndroid-12-android.png)
 - Samsung Knox デバイス: をタップします。 **[確認]**

        ![Screenshot prompting the user to confirm the privacy policy for a Samsung Knox device](./media/ft-userEnrollAndroid-13-knox.png)

 Intune がデバイスを登録している間、次のメッセージが画面に表示されます。

  ![Android デバイスが登録されていることを示すスクリーンショット](./media/ft-userEnrollAndroid-14-enrollingDevice.png)
14.  
            **[会社アクセスのセットアップ]**画面で、**[続行]**をタップします。 IT 管理者が別のセキュリティ要件 (パスワードの設定など) をセットアップしている場合は、画面の指示に従って、 [会社アクセスのセットアップ] 画面に戻ったときに**[続行]**をタップします。

  ![Android デバイスが準拠しており、ユーザーに続行を求めるスクリーンショット](./media/ft-userEnrollAndroid-15-coAccessSetup.png)
15. 
            をタップします。 **[完了]**

  ![会社アクセスのセットアップ完了時のスクリーン ショット (Android デバイス)](./media/ft-userEnrollAndroid-16-SetupComplete.png)
16. これでデバイスが Intune に登録され、ポータル サイト アプリに戻ります。
17. 会社のアプリをインストールするには、最初に**[設定] 、 [セキュリティ]**の順に選び、**[不明なソース]**をオンにします。 アプリをインストールする前に、このオプションをオンにしない場合、次のメッセージが表示されます。 [インストールがブロックされました。 セキュリティ上の理由から、電話は不明のソースから取得したアプリのインストールをブロックするように設定されています。 ] エラー ダイアログの**[設定]**をタップすると、**[不明なソース]**オプションを表示できます。

## <a name="intune-ios-"></a>Intune に iOS デバイスを登録する
これらの手順を使用して、Intune に iOS デバイスを登録します。 登録の詳細については、「[ポータル サイト アプリをインストールし、Intune にデバイスを登録するとどうなりますか](https://technet.microsoft.com/library/mt598622(TechNet.10).aspx#BKMK_ios_what_happ_enroll)」を参照してください。 Intune にデバイスを登録している最中にエラーが表示された場合は、「[IT 管理者に登録に関するエラーを送信する](https://technet.microsoft.com/library/mt598622(TechNet.10).aspx#BKMK_ios_error_enrolling_tbl)」を参照してください。

登録の前後に、デバイスの使用方法に適したカテゴリを選ぶように求められる場合があります。 IT-管理者は、このカテゴリを使用してアクセスできるアプリを判断します。
1.  App ストアから無料の Microsoft Intune ポータル サイト アプリをデバイスにインストールします。
2.  Microsoft Intune ポータル サイト アプリを開きます。
3.  ポータル サイトの**[ようこそ]**画面で、**[サインイン]**をタップし、職場または学校アカウントを使用してサインインします。

  ![Intune ポータル サイトのサインイン画面のスクリーンショット (iOS デバイス)](./media/ft-userEnrollIOS-1-signUp.png)
4.  IT 管理者によって会社の使用条件が設定されている場合は、**[同意する]**をタップして該当する条項に同意します。
5.  [会社アクセスのセットアップ] ページで、**[開始]**をタップします。

  ![iOS デバイスで登録プロセスを始めるように求めるスクリーンショット](./media/ft-userEnrollIOS-2-coAccessSetup.png)
6.  デバイスを登録すると可能になる操作についての説明を確認してから、**[続行]**をタップします。

  ![iOS デバイスの登録が推奨される理由に関する情報のスクリーンショット](./media/ft-userEnrollIOS-3-whyEnroll.png)
7.  IT 管理者が登録済みのデバイスに関して確認できる情報と確認できない情報についての一覧を確認し、**[続行]**をタップします。

  ![iOS デバイスのプライバシー ポリシーを示すスクリーンショット](./media/ft-userEnrollIOS-4-privacy.png)
8.  をタップすると表示される可能性のあるいくつかの項目を確認します。 [登録] 読み終えたら、**[登録]**をタップします。

  ![これからの登録手順を示すスクリーン ショット (デバイス iOS)](./media/ft-userEnrollIOS-5-whatNext.png)
9.  [プロファイルのインストール] 画面で、**[インストール]**をタップし、入力を求められたらパスコードを入力します。

  ![管理プロファイルをインストールするように求めるスクリーンショット (iOS デバイス)](./media/ft-userEnrollIOS-6-installProfile.png)
10. 
            をタップします。 **[インストール]**

  ![[インストール] ボタンをタップして、iOS デバイスにプロファイルをインストールするように求めるスクリーンショット](./media/ft-userEnrollIOS-7-tapInstall.png)
11. 
            **[インストール]**をタップすると、警告を読んだことになります。

  ![プロファイル管理警告を読んだことを確認するスクリーンショット (iOS デバイス)](./media/ft-userEnrollIOS-8-readWarning.png)
12. 
            **[信頼]**をタップします。

  ![プロファイルのソースを確認するように求めるスクリーンショット (iOS デバイス)](./media/ft-userEnrollIOS-9-tapTrust.png)
13. プロファイルのインストールが完了したことを示す画面に変わったら、**[完了]**をタップします。 "デバイス登録中" メッセージが画面に表示されます。

  ![プロファイルが iOS デバイスにインストールされていることを示すスクリーンショット](./media/ft-userEnrollIOS-10-profileInstalled.png)
14. ポータル サイトでページを開くことを確認するメッセージが表示されたら、**[開く]**をタップします。

  ![ポータル サイトでページを開くように求めるスクリーンショット (iOS デバイス)](./media/ft-userEnrollIOS-11-openPage.png)
- [会社アクセスのセットアップ] 画面で、**[続行]**をタップします。 IT-管理者が別のセキュリティ要件 (パスワードの設定など) をセットアップしている場合は、画面の指示に従って、すべてのコンプライアンス要件に対応します。 [会社アクセスのセットアップ] 画面に戻った後、**[続行]**をタップします。

  ![iOS デバイスが準拠しており、ユーザーに続行を求めるスクリーンショット](./media/ft-userEnrollIOS-12-coAccessSetup.png)
15. 
            をタップします。 **[完了]**

  ![会社アクセスのセットアップ完了時のスクリーン ショット (iOS デバイス)](./media/ft-userEnrollIOS-13-setupComplete.png)

これでデバイスが Intune に登録され、ポータル サイト アプリに戻ります。

## <a name="intune-mac-os-x-"></a>Intune に Mac OS X デバイスを登録する
1.  Safari ブラウザーを使用して、[ポータル Web サイト](https://portal.manage.microsoft.com/)を開き、通知バーをタップします。
2.  
            をタップします。 **[このデバイスは登録されていないか、ポータル サイトで特定できません]**

  ![ポータル サイトで Macintosh OS X デバイスを特定できないことを示すスクリーンショット](./media/ft-userEnrollMacOSx-1-enrollBegin.png)
3.  
            をタップして、デバイスの登録を開始します。 **[インストール]**

  ![Macintosh OS X デバイスを登録するように求めるスクリーンショット](./media/ft-userEnrollMacOSx-2-enrollDevice.png)
4.  [管理プロファイルのインストール] ダイアログ ボックスで、**[インストール]**をタップします。 資格情報の入力を求めるダイアログ ボックスが表示された場合は、ユーザー名とパスワードを入力し、**[続行] 、 [インストール]**の順にタップします。

  ![管理プロファイルをインストールするように求めるスクリーンショット (Macintosh OS X デバイス)](./media/ft-userEnrollMacOSx-3-installProfile.png)

登録が完了すると、プロファイルが検証されたことを示す管理プロファイル ページが表示されます。

  ![管理プロファイルが検証されたことを示すスクリーンショット (Macintosh OS X デバイス)](./media/ft-userEnrollMacOSx-4-profileVerified.png)

### <a name=""></a>詳細な情報をご希望ですか?
「[Enterprise Mobilität Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx)」を参照してください。.
