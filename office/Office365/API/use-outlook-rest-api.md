MS-です。 TocTitle: Outlook の REST-API のタイトルを使用する: Outlook の REST-API の説明を使用して: 登録および承認、サポートに関する一般的な情報エンドポイント、対象ユーザー、およびメール、予定表、連絡先、ユーザー、データの拡張機能を含む、すべての Outlook REST-API のアクセス ユーザーのメールボックスにクライアント ライブラリを使用してのバージョンの拡張プロパティ、通知、およびユーザーの写真です。 MS-です。 ContentId: ffb867ed-eede-405f-91ff-28276c39e874 <<<<<<< ヘッド ms.topic: 参照 (API) ms.date: 2016 年 4 月 22 日

=======
MS.Date: 2016 年 9 月 20 日
---
>>>>>>> ステージング[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="a-nameuse-the-outlook-rest-apiaoutlook-rest-api-"></a><a name="use-the-outlook-rest-api"></a>Outlook の REST-API を使用します。

[!INCLUDE [Add the Outlook REST API filters--v2 default](../includes/controls/addOutlookVersion_v2default.html)]

 _**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

<a name="DefineOutlookRESTAPI"></a>

Outlook の REST-API には、Office 365、Hotmail.com、Live.com、MSN.com、Outlook.com、および Passport.com でユーザーのメールボックス データへのアクセスを許可するのには、次のサブセットが含まれています。 次の表は、各サブセットのコア機能は、利用可能となった最初のバージョンを示します。 、サブセット内で API の新機能とその後を追加できること、それ以降のバージョンに注意してください。 たとえば、v1.0、カレンダー API が導入されました、会議の時間を示す機能はのみのベータ版がない v1. 0 またはバージョン 2.0 では、現在利用可能です。 

|**API-のサブセット**|**使用可能なバージョン**|
|:-------------|:---------------------|
|[カレンダー-API](..\api\calendar-rest-operations.md)|以降では v1. 0|
|[連絡先-API](..\api\contacts-rest-operations.md)|以降では v1. 0|
|[データ拡張機能-API](..\api\extensions-rest-operations.md)|バージョン 2.0 以降では|
|[拡張 API のプロパティ](..\api\extended-properties-rest-operations.md)|バージョン 2.0 以降では|
|[メール-API](..\api\mail-rest-operations.md)|V1. 0 以降では|
|[プッシュ通知-API](..\api\notify-rest-operations.md)|バージョン 2.0 以降では|
|[通知 API のストリーミング](..\api\notify-streaming-rest-operations.md) (プレビュー)|Beta|
|[API の人](..\api\people-rest-operations.md) (プレビュー)|Beta|
|[タスク-API](..\api\task-rest-operations.md)|バージョン 2.0 以降では|
|[API-のユーザーの写真](..\api\photo-rest-operations.md)|バージョン 2.0 以降では| 
|[複数の API 呼び出しをバッチ処理](#..\api\batch-outlook-rest-requests.md) (プレビュー)|Beta| 

**メモ**  

この資料の残りの部分では、Outlook の REST-API のすべてのサブセットに適用される一般的な情報について説明します。 参照のわかりやすくするため、この資料の残りの部分を使用して**Hotmail.com、Live.com である MSN.com、Outlook.com、および Passport.com ドメインのアカウントを含めるには、「Outlook.com」** 。

<a name="ShortRegAuthWorkflow"></a>

## <a name="a-nameregister-and-authenticate-your-appa"></a><a name="register-and-authenticate-your-app"></a>登録し、アプリを認証

Outlook の REST-API を使用して、ユーザーのメールボックス データにアクセスするのには、アプリは登録とユーザー認証を処理する必要があります。
1. 最初に、Outlook の REST-API へのアクセスを取得するアプリケーションを登録します。 アプリで API の呼び出しを実装することができます。 

2. 、実行時にユーザーからの承認の取得し、ユーザーのメールボックスにアクセスするための REST-API 要求を作成します。 

アプリケーションの登録とユーザー認証を処理するために現在 2 つの方法があります。
- [Azure AD v2 認証エンドポイントを使用します。](#RegAuthConverged)
- [Azure Active Directory は、OAuth を使用して、](#RegAuthAzure) 

<a name="RegAuthConverged"> </a>

### <a name="a-nameazure-ad-v2-authentication-endpointaazure-ad-v2-"></a><a name="azure-ad-v2-authentication-endpoint"></a>Azure AD v2 認証のエンドポイント 

Azure AD v2 認証エンドポイントは、Microsoft 組織と個人のアカウントの両方で動作するアプリケーションの構築を簡略化します。 仕事、学校、および 1 つのボタンを使用してサインインするのには個人アカウントのユーザーを有効にします。

この集中型のプログラミング モデルは、次の構成されている最新の方法です。
- [Microsoft アプリケーション登録ポータル](https://apps.dev.microsoft.com) 
- [認証のスコープ v2](..\howto\authenticate-Office-365-APIs-using-v2.md#bk_Outlookscopes)
- 認証エンドポイント v2
  - https://Login.microsoftonline.com/Common/oauth2/v2.0/Authorize
  - https://Login.microsoftonline.com/Common/oauth2/v2.0/Token
- ADAL ライブラリです。 v2 

この方法では、シームレスなアプリケーションの登録とユーザー認証経験 Outlook.com Office 365 にユーザーのメールボックス データにアクセスするための適切なトークンを取得します。 Outlook.com のアプリケーションを開発する場合は、この方法を使用する必要があります。 

アプリケーションの登録時にアクセス許可を要求するのではなく、v2 認証エンドポイントは実行時に対応するユーザーの操作に基づいて、必要なアクセス許可を要求し、動的にダイアログを表示することができます。 

この集中型のプログラミング モデルは、いくつかのコンポーネントで構成されていますので、1 つのコンポーネントを使用する場合、他にもを使用する必要があります。 詳細については、[はじめの例](https://dev.outlook.com/RestGettingStarted)を参照してください。 と[Office 365 の認証および Outlook.com Api を使用して、v2 認証エンドポイント](..\howto\authenticate-Office-365-APIs-using-v2.md)。

**注意** 

- V2 認証エンドポイントを使用するには、アプリケーションは直接 Outlook の REST-API を呼び出す必要があります。 既存の Office 365 クライアント ライブラリを使用することはしません。 V2 認証エンドポイントと新規の Outlook の REST エンドポイントを使用するのには後で、ライブラリが更新されます。

- [作成またはアプリケーションを更新するには](#UpgradePath)、アプリが有効になっているメールボックスを Outlook.com を処理できるため、Outlook REST API、およびそれらのメールボックスを有効にするを待機しているを使用してアクセスすることができますを確認します。 [テストとこのような Outlook.com のシナリオの処理](#OutlookRESTCaution)方法の詳細を確認します。
  

<a name="RegAuthAzure"> </a>

### <a name="a-nameregister-and-authenticate-using-azure-ad-and-oauthaazure-ad-oauth"></a><a name="register-and-authenticate-using-azure-ad-and-oauth"></a>登録して、Azure AD を使用して認証と OAuth

これは、Office 365 のみにメールボックス データにアクセスする前のアプローチです。 Outlook.com では、上のデータにアクセスしたり、Office 365 用の新しいアプリケーションを作成することを計画している場合は、 [v2 認証エンドポイント](#RegAuthConverged)を使用してください。 

しばらくの間、メールボックスのデータにアクセス Office 365 で実施できるようとする前に、Azure の AD にアプリを登録するのにはアプリを必要とする[適切なスコープでアクセス許可](..\howto\Application-Manifest.md#AppManifest_ExchangeScopes)を指定します。 実行時に、アプリは、Azure AD を使用し、アプリケーションの要求を認証するために OAuth を続行できます。 [Office 365 アプリケーションの認証の概念](..\howto\common-app-authentication-tasks.md)の詳細が表示されます。 の[アップグレード ・ パス](#UpgradePath)を計画する必要があります。 

この手法を使用して Office 365 のアプリケーションで直接呼び出すことによって、または Office 365 クライアント ライブラリを使用して Outlook の REST-API にアクセスするを選択できます。 

<a name="UpgradePath"></a>

### <a name="a-nameupgrade-patha-"></a><a name="upgrade-path"></a>アップグレード ・ パス

V2 認証エンドポイントは、 [Outlook と Outlook.com の開発者のための一般的に利用可能な (GA) ステータスをプレビューから昇格](https://blogs.technet.microsoft.com/ad/2016/02/23/for-developers-the-first-use-cases-of-the-converged-microsoft-account-and-azure-active-directory-programming-model-are-now-ga/)されています。 V2 認証エンドポイントとは、最新の Outlook のエンドポイントを使用する予定が、Office 365 のメールボックス データにアクセスする本番環境でアプリケーションがある場合、または Office 365 または Outlook.com の_新しい_アプリケーションを作成する場合は、 (`https://outlook.office.com/`の下の詳細を参照) を利用できる Office 365 の組織と個人の Outlook.com ユーザーの両方のコードの 1 つのセットを作成します。

Outlook.com のメールボックス データにアクセスする Windows Live-API を使用する生産のアプリを使っている場合を使用するアプリケーションを書き換える必要があります、v2 認証エンドポイントと Outlook の REST-API です。 Outlook.com の Windows Live-API が廃止される予定と、Outlook.com を表示する自分のメールボックスを Outlook の REST-API を有効になっている、そのような Windows Live-API-アプリケーションを実行しようとしています。 これらのユーザーは HTTP 404 エラーを取得します。 REST-API-は、の新しい機会を開きます その一方で、Outlook の: ノード、Python、Swift、Java、およびなどの共通の言語の一覧から選択することができますアプリケーションを 1 回の書き込みし、web、iOS、Android、または Windows に Outlook.com_と_Office 365 ユーザーの両方をキャプチャ デバイスです。 

**メモ** 

_のみ_Outlook.com のメールボックス データにアクセスするための継続運用でアプリを実行する場合に、Outlook の REST-API のほとんどにアクセスするのには、同じ Windows Live のスコープを使用する続行できます。 参照してください。  
[Windows Live を使用してスコープと Outlook.com のメールボックス データにアクセスする Outlook の REST-API](#WindowsLiveScopeMapping)の詳細について。

アプリケーションの登録とユーザー認証のいずれかのアプローチを使用するか、最新の Outlook の REST エンドポイントが実稼働環境では、アプリケーションのターゲット Office 365 または Outlook.com のメールボックス データ、および REST-API の呼び出しで使用を開始することができるかどうか常に準備が整ったら。

`https://outlook.office.com/api/{version}/{user_context}`

次の Outlook の REST エンドポイントがの唯一の Office 365 のメールボックス データの間動作し続けます。

`https://outlook.office365.com/api/{version}/{user_context}`

[サポートされている残りの部分の動作エンドポイント](#SupportedEndpoints)と[のバージョン](#SupportedVersions)の下の詳細を参照してください。 

<a name="OutlookRESTCaution"></a>

**注意**

- Outlook の REST-API-エンドポイントでは、基本認証はサポートされていません`https://outlook.office.com`。 V2 認証エンドポイントまたは Azure AD を使用して、新しい Outlook の REST-API エンドポイントを使用するアプリケーションの認証および承認を行います。  
- 新しい Outlook の REST エンドポイントを使用する場合の最適なパフォーマンスは、次のように追加します。 、`x-AnchorMailbox`のすべての要求のヘッダーにユーザーの電子メール アドレスを設定します。 例えば:`x-AnchorMailbox:john@contoso.com`
- 発生するため、Outlook の REST-API の Outlook.com 上のメールボックスを有効にする期間内に、既存の Outlook.com アカウント可能性があります時間がかかる取得を有効にします。 Outlook.comのメールボックスが既に有効になっているデータにアクセスするアプリケーションをテストするには、outlookdev@microsoft.comを電子メールで送信することによって、有効な新しい Outlook.com 開発者プレビュー アカウントを要求できます。 
- アプリ、Outlook.com のメールボックス データにアクセスする場合を処理するようシナリオ、ユーザーのメールボックスがまだ有効になっていない Outlook REST-API です。 このような状況では、残りの要求を行うときはエラーが発生する次のように。
  - HTTP-エラー: 404
  - エラー コード: MailboxNotEnabledForRESTAPI または MailboxNotSupportedForRESTAPI 
  - エラー メッセージ: "REST-API はまだできませんこのメールボックスの。
- V2 認証エンドポイントを使用するコード サンプルでは、 [dev.outlook.com](https://dev.outlook.com/RestGettingStarted)を参照してください。  

<a name="WindowsLiveScopeMapping"></a>

**Outlook.com のメールボックス データにアクセスする Windows Live のスコープと Outlook の REST-API を使用します。**

Outlook.com に本番環境でアプリケーションを使用して、Windows Live のスコープでは、Office 365 のメールボックスのデータを対象にしない場合は、Outlook の REST-API のほとんどにこれらの Windows Live のスコープを使用する続行できます。 次の表は、Outlook の REST-API のスコープに Windows Live の範囲をマップする方法を示しています。 Windows Live スコープ直接のマッピング Mail.Read はしていないことに注意してください。 アプリは、WL.IMAP を使用して、Mail.Read を必要とするこれらの Outlook の REST-API の操作にアクセスすることができます。

|**Windows Live のスコープ**|**Outlook REST-API の範囲**|
|:-----|:-----|
|WL.Basic | User.Read、Contacts.Read |
|WL.calendars | Calendars.Read |
|WL.calendars_update | Calendars.ReadWrite |
|WL.contacts_create | Contacts.ReadWrite |
|WL.contacts_calendars | Calendars.Read |
|WL.EMails | User.Read |
|WL.events_create | Calendars.ReadWrite |
|WL.IMAP | Mail.ReadWrite、Mail.Send |


****

<a name="SupportedEndpoints"></a>

## <a name="a-namesupported-rest-actions-and-endpointsa"></a><a name="supported-rest-actions-and-endpoints"></a>サポートされている残りの部分の動作とエンドポイント

サポートされているメソッドを使用して HTTP 要求を送信する Outlook の他の API との対話をするには: 取得、投稿、修正、または削除します。 投稿し、修正プログラムは、JSON のペイロードのボディとサーバーの応答が送信を要求します。

URL リソースのパス名とクエリ パラメーターは、大文字と小文字です。 ただし、値を割り当てる、エンティティ Id、およびその他の base64 でエンコードされた値は、大文字小文字を区別します。

Outlook の REST-API のすべての要求は、次の新しいルートの URL 形式を使用します。

 `https://outlook.office.com/api/{version}/{user_context}`

適切なユーザー認証では、REST API で、このルートの URL は Office 365 と Outlook.com にメールボックス データへのアクセスを提供します。 この資料の残りの部分では、このエンドポイントで REST-API について説明します。 

既存のルート URL を使用するコードがある場合は

 `https://outlook.office365.com/api/{version}/{user_context}`
 
コードは、Office 365 の間、作業を続行しますが、新しいルート URL への切り替えを計画する必要があります。

**注意**最適なパフォーマンス、新しいルートの URL を使用して残りの要求を行う場合、次のように追加します。 、`x-AnchorMailbox`ヘッダーにユーザーの電子メール アドレスを設定します。 また、大文字と小文字、Outlook.com のユーザーのメールボックスがまだ有効になっていない Outlook の REST-API のエラー コード MailboxNotEnabledForRESTAPI と MailboxNotSupportedForRESTAPI のチェックを処理します。 詳細についてを参照してください[ここで](..\api\use-outlook-rest-api.md#OutlookRESTCaution)。  

### <a name="a-namenotes-for-developers-in-chinaa"></a><a name="notes-for-developers-in-china"></a>中国の開発者用のメモ 

- 中国で Office 365 のアプリケーションを開発する場合に[中国向けの Office 365 の API のエンドポイント](..\api\o365-china-endpoints.md)を使用して続行してください。

- Outlook.com では、中国のアプリを作成する場合は、 [v2 認証エンドポイント](..\api\use-outlook-rest-api.md#RegAuthConverged)をして、次の新しい Outlook の REST エンドポイントを使用してください。。`https://outlook.office.com/api/{version}/{user_context}`

<a name="SupportedVersions"> </a>

##<a name="a-namesupported-versions-of-apiaapi-"></a><a name="supported-versions-of-api"></a>API-のバージョンがサポートされています。

`{version}`ルートの指定した URL で Outlook の REST-API のバージョンを表します。 次の値のいずれかを指定できます。 

- `v1.0`の状態で最も古いバージョンは、実稼働コードで使用することができます。 .全般的な可用性 (GA) URL-の例で、 `http://outlook.office.com/api/v1.0/me/events`。 

- `v2.0`. このバージョンでは、GA の状態でも、実稼働コードで使用することができます。 URL-の例で、 `http://outlook.office.com/api/v2.0/me/events`。 このバージョンにはでは v1. 0 と成長があり、GA のステータスをプレビューから昇格されているその他の API のセットを解除する可能性があります変更が含まれます。 

- `beta`. このバージョンでは、プレビューの状態では、実稼働コードでは使用しない必要があります。 URL-の例で、 `http://outlook.office.com/api/beta/me/events`。 このバージョンには、追加の API のセットをプレビューでは、ファイナライズする前に変更することがあり、同様に、ga の時点での最新の API が含まれています。

Outlook REST-API の残りの部分の操作の大半は、サポートされて、上記に一覧表示されているバージョンの間で記述と同様の動作をします。 

##<a name="a-nametarget-usera-"></a><a name="target-user"></a>ターゲット ユーザー

REST-API-を除く ユーザーの写真の`{user_context}`、現在サインインしているユーザーは、Outlook の REST-API は、現在のユーザーの代理として常に実行を要求します。

REST-API ユーザーの写真の の`{user_context}`は、サインインしているユーザー、またはユーザー-ID で指定されたユーザー 

Outlook の REST-API のセットを指定できます`{user_context}`で、次のいずれかの残りの部分_の要求_。 

- `me`のショートカット: `/api/{version}/me`。 Die URL になります ルートの`https://outlook.office.com/api/{version}/me`。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

- `users/{upn}`次のように、UPN または、ログインしているユーザーのプロキシ アドレスを渡す形式: `/api/beta/users/sadie@contoso.com`。 この例では、ルート URL になります`https://outlook.office.com/api/beta/users/sadie@contoso.com`。

- `users/{AAD_userId@AAD_tenandId}`形式でユーザー ID と Azure Active Directory 内のテナント ID を利用します。 たとえば、 `users/ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77`。 Die URL になります ルートの`https://outlook.office.com/api/beta/users/ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77`。

使用率は、好みの問題です。 

この形式で識別されるユーザー コンテキストでサーバーの_応答_: `users/{AAD_userId@AAD_tenandId}`。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

- `users/{upn}`次のように、UPN または、ログインしているユーザーのプロキシ アドレスを渡す形式: `/api/beta/users/sadie@contoso.com`。 この例では、ルート URL になります`https://outlook.office.com/api/beta/users/sadie@contoso.com`。

- `users/{AAD_userId@AAD_tenandId}`形式でユーザー ID と Azure Active Directory 内のテナント ID を利用します。 たとえば、 `users/ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77`。 Die URL になります ルートの`https://outlook.office.com/api/beta/users/ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77`。

使用率は、好みの問題です。 

この形式で識別されるユーザー コンテキストでサーバーの_応答_: `users/{AAD_userId@AAD_tenandId}`。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

- `users/{upn}`次のように、UPN または、ログインしているユーザーのプロキシ アドレスを渡す形式: `/api/v1.0/users/sadie@contoso.com`。 この例では、ルート URL になります`https://outlook.office.com/api/v1.0/users/sadie@contoso.com`。

使用率は、好みの問題です。 サーバーの応答では、ユーザー コンテキストはこの形式で識別されます。`/api/v1.0/users('sadie@contoso.com')`

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

## <a name="a-nameaccessing-item-in-a-collectiona"></a><a name="accessing-item-in-a-collection"></a>コレクション内の項目へのアクセス

Outlook の REST-API には、エンティティ コレクション内の項目を指定する 2 とおりの方法がサポートされています。 好みの問題は、同様に評価されます。

- 例では、コレクションの後の URL セグメント。`/api/{version}/me/events/AAMkAGI3...`
    
- たとえば、引用符で囲まれた文字列としてかっこ。`/api/{version}/me/events('AAMkAGI3...')`


****

## <a name="a-nameuse-a-client-library-to-access-the-outlook-rest-apiaoutlook-rest-api-"></a><a name="use-a-client-library-to-access-the-outlook-rest-api"></a>Outlook の REST-API にアクセスするクライアント ライブラリを使用してください。

アプリを使用する場合[Azure AD とアプリケーションの登録とユーザー認証用の OAuth](..\api\use-outlook-rest-api.md#RegAuthAzure)、Office 365 の API のクライアント ライブラリは容易にできるように、REST API と対話する: [.NET](..\howto\getting-started-Office-365-APIs.md)、 [JavaScript](..\howto\getting-started-Office-365-APIs.md)、 [Android](..\howto\getting-started-Office-365-APIs.md)、および[iOS](..\howto\getting-started-Office-365-APIs.md)です。 認証トークンを管理し、クエリを実行し、Office 365 のデータを使用するに必要なコードを簡略化するのに役立ちます。


**注意**クライアント ライブラリは、登録、承認、Outlook.com の[v2 認証エンドポイント](..\api\use-outlook-rest-api.md#RegAuthConverged)の操作を後で更新されます。 Outlook.com のメールボックス データにアクセスする場合は、REST API を直接呼び出します。


[Visual Studio の Office 365 の API ツール](http://aka.ms/clientlibrary)の最新バージョンの .NET または JavaScript ライブラリを取得できます。 または、右にし、 [Windows ストア アプリのスタート プロジェクトを試してみてください](http://aka.ms/o365-apis-start-windows)の詳細を確認できます。

.NET または JavaScript クライアント ライブラリを使用して Outlook の REST-API にアクセスするには、アクセス トークンを取得し、Outlook のサービス クライアントを取得する必要があります。 次に、予定表のデータと対話するのには、非同期クエリを送信できます。

[アクセス トークンを取得する](#GetAuthToken) | [サービスの Outlook クライアントを取得します。 ](#GetClient)

<a name="GetAuthToken"> </a>
### <a name="a-nameget-an-access-tokena-"></a><a name="get-an-access-token"></a>アクセス トークンを取得します。

認証に使用されるアクセス トークンを取得します。 Azure Active Directory にアプリを登録するとき、URI の認証、クライアント ID が割り当てられます。 

**メモ**このパターンは、Windows デバイス上で実行されるコードのみに適用されます。 Windows ストア アプリケーションでは、アプリケーションを登録するときに、プロジェクトの App.xaml ファイルにクライアント Id と AuthorizationUri の値が追加されます。 AuthorizationUri は、CommonAuthority 変数のホスト名として使用されます。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Properties of the native client app. Get the ClientId from the resources section of the App.xaml file.
public const string ClientID = Application.Current.Resources["ida:ClientID"] as String; 
// Get the _returnUri from app settings.
public static Uri _returnUri = Windows.Security.Authentication.Web.WebAuthenticationBroker.GetCurrentApplicationCallbackUri();

// Properties used to communicate with a Windows Azure AD tenant.  
public const string CommonAuthority = "https://login.windows.net/Common"; 
public const string DiscoveryResourceId = "https://api.office.com/discovery/"; 

//Store authority in application data so that it isn't tied to the lifetime of the access token.
private static ApplicationDataContainer _settings = ApplicationData.Current.LocalSettings;
private static string LastAuthority
{
    get
    {
        if (_settings.Values.ContainsKey("LastAuthority") && _settings.Values["LastAuthority"] != null)
        {
            return _settings.Values["LastAuthority"].ToString();
        }
        else
        {
            return string.Empty;
        }

    }

    set
    {
        _settings.Values["LastAuthority"] = value;
    }
}

public static AuthenticationContext _authenticationContext { get; set; } 
private static async Task<string> GetTokenHelperAsync(AuthenticationContext context, string resourceId)
{
    string accessToken = null;
    AuthenticationResult result = null;

    result = await context.AcquireTokenAsync(resourceId, ClientID, _returnUri);

    accessToken = result.AccessToken;
    //Store authority in application data.
    _settings.Values["LastAuthority"] = context.Authority;

    return accessToken;
}
```
```javascript 
var authContext;
var authToken; // for use with creating an outlookClient later.
authContext = new O365Auth.Context();
authContext.getIdToken("https://outlook.office365.com/")
   .then((function (token) {
       authToken = token;
       // The auth token also carries additional information. For example:  
       userName = token.givenName + " " + token.familyName;
   }).bind(this), function (reason) {
       console.log('Failed to login. Error = ' + reason.message);
   });

```
<!-- ENDSECTION -->

<a name="GetClient"> </a>
###Outlook サービス クライアントを取得します。


**OutlookServicesClient**オブジェクトを取得します。 サービスの Outlook クライアントを使用する他の方法から、このコードを呼び出すことができます。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
public static async Task<OutlookServicesClient> CreateOutlookClientAsync(string capability)
{
    try
    {
        //First, look for the authority used during the last authentication.
        //If that value is not populated, use CommonAuthority.
        string authority = null;
        if (String.IsNullOrEmpty(LastAuthority))
        {
            authority = CommonAuthority;
        }
        else
        {
            authority = LastAuthority;
        }
        // Create an AuthenticationContext using this authority.
        _authenticationContext = new AuthenticationContext(authority);
        
        //See the Discovery Service Sample (https://github.com/OfficeDev/Office365-Discovery-Service-Sample)
        //for an approach that improves performance by storing the discovery service information in a cache.
        DiscoveryClient discoveryClient = new DiscoveryClient(
            async () => await GetTokenHelperAsync(_authenticationContext, DiscoveryResourceId));

        // Get the specified capability ("Calendar").
        CapabilityDiscoveryResult result = 
            await discoveryClient.DiscoverCapabilityAsync(capability);
        var client = new OutlookServicesClient(
            result.ServiceEndpointUri,
            async () => 
                await GetTokenHelperAsync(_authenticationContext, result.ServiceResourceId));
        return client;
    }
    catch (Exception)
    {
        if (_authenticationContext != null && _authenticationContext.TokenCache != null)
        _authenticationContext.TokenCache.Clear();
        return null;
    }
}
```
```javascript 
// Once the authToken has been acquired, create an outlookClient. One place to do this is inside of the
//    ".then" function callback of authContext.getIdToken(...) above.
var outlookClient = new Microsoft.OutlookServices.Client('https://outlook.office365.com/api/v1.0', authToken.getAccessTokenFn('https://outlook.office365.com'));
```
<!-- ENDSECTION -->

****


<a name="ShutdownEarlierPreviewEndpoint"></a>
## <a name="a-nameshutting-down-of-earlier-preview-endpointa-"></a><a name="shutting-down-of-earlier-preview-endpoint"></a>以前のプレビューのエンドポイントのシャット ダウン

既に使用している場合`https://outlook.office.com/api`または`https://outlook.office365.com/api`ルート URL と  
Outlook の REST-API にアクセスするには、この廃止する影響しません。 まだ以前のプレビューのエンドポイントを使用している場合に読み取り`https://outlook.office365.com/ews/odata`。

Outlook の REST-API では、2014 年の 10 月の 1.0 の全般的な可用性を最初のプレビュー表示から移動します。 この移行を完了するために私たちは最後にシャット ダウン古いプレビュー エンドポイント`https://outlook.office365.com/ews/odata` **2015 年 10 月 15 日**にします。

私たちは、すべてのアプリケーションとサービスの以前のエンドポイントを使用する必要があります。

`https://outlook.office365.com/ews/odata` 

移動するのには

`https://outlook.office.com/api/v1.0` 

で 2015 年 10 月 15 日。 V1. 0 (GA) は、その日付に移動するのには最低限の全般的な可用性 エンドポイントです。 

GA エンドポイントの優先バージョン 2.0 を使用する代わりに、 (`https://outlook.office.com/api/v2.0`) 、またはプレビューのエンドポイント (`https://outlook.office.com/api/beta`) プレビュー状態の最新の Api を実行します。 ファイナライズする前に一般的に、API のプレビューのステータスが変化することに留意してください。 それらを使用する場合は、アプリの機能を確認し、適切な変更を準備してください。 API のプレビューではファイナライズを取得するときは、GA のエンドポイントも同様にこれらの拡張機能にアクセスすることができます。



## <a name="a-namenext-stepsa"></a><a name="next-steps"></a>次のステップ

Outlook の REST-API を使用する手順に従います。

- [メール API リファレンス](..\api\mail-rest-operations.md)

- [カレンダー API リファレンス](..\api\calendar-rest-operations.md)
  
- [連絡先 API リファレンス](..\api\contacts-rest-operations.md)

- [REST-API のタスク](..\api\task-rest-operations.md)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)

- [ユーザーの API リファレンス](..\api\people-rest-operations.md) (プレビュー)

- [データ拡張機能 API リファレンス](..\api\extensions-rest-operations.md)

- [拡張のプロパティの API リファレンス](..\api\extended-properties-rest-operations.md) 

- [プッシュ通知の残りの部分の API リファレンス](..\api\notify-rest-operations.md)

- [通知他のストリーミング API リファレンス](..\api\notify-streaming-rest-operations.md) (プレビュー)

- [ユーザーの写真の残りの部分の API リファレンス](..\api\photo-rest-operations.md) 

- [バッチ Outlook の他の要求](#..\api\batch-outlook-rest-requests.md) (プレビュー)

[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]



