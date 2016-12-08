MS-です。 TocTitle: 探索サービスの REST-API リファレンス タイトル: 探索サービスの REST-API リファレンスの説明: Office 365 の探索サービス API を使用して、Office 365 アプリケーションが接続できるサービスにアクセスするためのエンドポイントを自動的に検索する方法を参照します。 MS-です。 ContentId: 799c9512-7020-4033-b7b8-1e9a2174555d ms.topic: ms.date を参照 (API): 2015 年 6 月 9 日

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="a-namediscovery-service-rest-api-referencea-rest-api-"></a><a name="discovery-service-rest-api-reference"></a>探索サービスの REST-API リファレンス

<!--You use Discovery Service to find endpoints for services that you access in an Office 365 APIs application. In this article, you'll find reference information for the Discovery Service APIs.-->


 _**に適用されます:** Office 365_

<a name="DiscSvc_RESTinterface"> </a>
## <a name="a-nameuse-the-office-365-discovery-serviceaoffice-365-"></a><a name="use-the-office-365-discovery-service"></a>Office 365 の探索サービスを使用します。

<a name="a-name-heada-"></a><a name="-head"></a><<<<<<< ヘッド
=======
[!INCLUDE [Use Microsoft Graph](../includes/use-msgraph-note.md)]

>>>>>>> HTTP-および OData 要求を送信する検出サービスの API と対話するステージングします。 探索サービスは、探索の**予定表**、**連絡先**、**メール**、 **MyFiles**を OneDrive とのビジネスのサービス エンドポイントの OneDrive) 、 () 、OneNote の**ノート**および (SharePoint) の**Workflowwebsite**をサポートします。

探索サービスのリソース-ID: `ResourceId = https://api.office.com/discovery/`。

探索サービス API を使用して、Office 365 の Api を使用してアクセスするサービスのエンドポイントを検索する方法のコード サンプルを参照してください[の-Api für Office 365: 検出サービスを使用する方法](https://code.msdn.microsoft.com/Office-365-APIs-How-to-use-609102ea#content)と[Office 365 の探索サービスのサンプル](https://github.com/OfficeDev/Office365-Discovery-Service-Sample)です。

**メモ**探索サービスは、オンライン環境を Office 365 の機能を提供のみと設置型展開では動作しません。

### <a name="a-nameversioninga"></a><a name="versioning"></a>バージョン管理

探索サービスのバージョンを次に示します。

|**サービス API エンドポイントの検出**|**説明**|
|:-----|:-----|
|https://API.Office.com/Discovery/v1.0/Me| Office 365 の Api のリリース バージョン用のサービスごとに 1 つの API エンドポイントをサポートしています。 <br>OData v4 を返します (http://www.odata.org/documentation/odata-version-4-0/) 既定では。</br>|
|https://API.Office.com/Discovery/v2.0/Me| Office 365 の Api のリリース バージョン用のサービスごとに複数の API エンドポイントをサポートしています。  <br>OData v4 を返します (http://www.odata.org/documentation/odata-version-4-0/) 既定では。</br>|




## <a name="a-namediscovery-service-operationsa"></a><a name="discovery-service-operations"></a>探索サービスの操作

<a name="DiscSvc_FirstSignIn"> </a>
### <a name="a-nameinitial-sign-ina"></a><a name="initial-sign-in"></a>最初にサインイン

これにより、クライアントの Web ページにユーザーがアカウント情報を入力します。 探索サービスを続行するために必要なエンドポイントを返します。 ユーザーには、アプリケーションがしようとすると、最初に使用されます。 アプリケーションを示します。
   1. どのようなクラウドのユーザーに属しています。
   2. アプリケーションがユーザー ログインを送信できます。
   3. トークンを取得する場所

****

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
| `scope`|string|スペースで区切られたトークンのリスト<i>capability.operation</i> 。 このスコープは、Office 365 の用語では。<br>例: MyFiles.Write または Mail.Read</br>|
|`redirect_uri`|string|承認が完了した後にリダイレクトする URI。 <br>例: https://contoso.com/continue </br>|
|`lcid`|string| 省略可能です。 電子メール HRD の BENUTZEROBERFLÄCHE をローカライズするのには 10 進数の LCID です。<br>例: 1031 </br><br>**メモ**この API 意図的にしないために、受信ユーザーの電子メールの現在のドメインからユーザーの電子メールを送信することによってユーザーのプライバシーを侵害する可能性があります。</br>|

|**応答**|**説明**|
|:-----|:-----|
|`302`見つかりません |応答の本体には、アプリケーションとユーザーの値が含まれています。|

|**応答本文の項目**|**説明**|
|:-----|:-----|
|場所: Redirect_URI| 承認が完了した後にリダイレクトする URI。|
|? User_email =. | ユーザーが入力した電子メール アドレス。|
|&amp;Account_type =. | 1 Microsoft アカウント (Live) <br>2-組織のアカウント (Office 365)</br>|
|&amp;Authorization_service =. | エンドポイントの URL は、クライアントが認証コードを取得できます。|
|&amp;Token_service =. |エンドポイントの URL は、クライアントがアクセス トークン、更新トークンの認証コードを交換できます。|
|&amp;スコープ =. | 元のスコープは、ターゲットとなる領域に変換されます。 のみ、クライアントは、Office 365 の範囲の用語を知っておく必要があります。 対象となる領域が Live の場合は、元の Office 365 のスコープは、ライブの用語に変換されます。|
|&amp;Unsupported_scope =. |変換できない範囲の項目がある場合は、unsupported_scope を変更せずにコンパイルします。 各承認サービスは、独自の条件でのみスコープを理解するために必要です。 Office 365 の認証サービスには、スコープ パラメーターがそのまま使用しない、ためのスコープと Unsupported_scope の両方は空です。|
|&amp;Discovery_service =. |エンドポイントの URL は、クライアントがターゲット サービスを検出できます。|
|&amp;Discovery_resource =. |探索サービスのリソース Id です。 探索サービスのトークン要求の一部としてトークン サービスに渡されます必要があります。|

**メモ**このすべての情報は、このユーザー アカウントで静的です。 したがってクライアントが、キャッシュして不要な BENUTZEROBERFLÄCHE を使用してユーザーを迷惑なを避けるために再利用します。

**例:**
```
var firstSignInUri = new Uri(string.Format("https://api.office.com/discovery/v1.0/me/FirstSignIn?redirect_uri={0}&scope={1}", TerminalUriText, Scope));
var terminalUri = new Uri(TerminalUriText);

//Starting authorization
var webAuthResult = await WebAuthenticationBroker.AuthenticateAsync(WebAuthenticationOptions.None, firstSignInUri, terminalUri)
   .AsTask().ConfigureAwait(continueOnCapturedContext: true);

//Authorization finished
If (webAuthResult.ResponseStatus == WebAuthenticationStatus.Success)
{
var userEmail = MyExtractParamter("user_email",webAuthResult.ResponseData);
var accountType = MyExtractParamter("account_type",webAuthResult.ResponseData);
var authorizationService = MyExtractParamter("authorization_service",webAuthResult.ResponseData);
var tokenService = MyExtractParamter("token_service", webAuthResult.ResponseData);
var discoveryService = MyExtractParamter("discovery_service", webAuthResult.ResponseData);
var scope = MyExtractParamter("scope",webAuthResult.ResponseData);
var unsupportedScope = MyExtractParamter("unsupported_scope", webAuthResult.ResponseData);

MyCacheUserInfo(...);
}
```

<a name="DiscSvc_Services"> </a>
### <a name="a-namediscover-specific-servicesa"></a><a name="discover-specific-services"></a>特定のサービスを検出します。

**API/サービス インスタンスの API**を使用すると、特定のサービスのエンドポイントを取得します。

****

|**ヘッダー**|**説明**|
|:-----|:-----|
|`Authorization`| 認証フェーズ中に取得したアクセス トークンです。 <br>例: 認証: ベアラー 2YotnFZFEjr1zCsicMWpAA. </br>|
|`Accept`| 省略可能です。 このヘッダーは、応答の内容の書式を制御します。 <br>アトム: のアプリケーション/アトム + Xml</br><br>JSON: アプリケーションまたは Json; OData = 詳細 </br><br>このヘッダーを省略すると、既定ではアトムです。 </br><br>例: 受け付ける: アプリケーションまたは Json; OData = 詳細 </br>|

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|`$select`|string| 省略可能です。 オブジェクトのプロパティのコンマ区切りのリストです。 により、選択したプロパティのみをプロジェクトにサービス。 しないアプリケーションで使用されていないプロパティをダウンロードすることで帯域幅を節約するために使用されます。 Http://www.OData.org/docs/ を参照してください。 <br>例: 機能、ServiceUri</br>|
|`$filter`|string| 省略可能です。 元の結果セットをフィルター処理する OData 述語です。 しないアプリケーションで使用されていないオブジェクトのインスタンスをダウンロードすることで帯域幅を節約するために使用されます。 使用可能な述語関数のドキュメンテーション」タブの下の http://www.odata.org を参照してください。 |

|**応答**|**意味**|**説明**|
|:-----|:-----|:-----|
|`200`| OK |応答の本体には、投影、フィルター、および、OData 要求に従ってエンコードされた[ServiceInfo スキーマ](#DiscSvc_SvcInfoSchema)のエントリの一覧が含まれています。 [ServiceInfo スキーマ](#DiscSvc_SvcInfoSchema)スキーマの定義を参照してください。|

**例:**
```
var url = string.Format("https://api.office.com/discovery/v1.0/me/services", discoveryService);

var request = HttpWebRequest.CreateHttp(url);
request.Method = "GET";
request.Headers["Authorization"] = "Bearer " + accessToken;

var response = await request.GetResponseAsync().ConfigureAwait(continueOnCapturedContext: true) as HttpWebResponse;
```

<a name="DiscSvc_AllServices"> </a>
### <a name="a-namelearn-what-services-are-discoverablea"></a><a name="learn-what-services-are-discoverable"></a>についてはどのようなサービスが検出可能


すべての検出可能な機能と、それを実装するサービスについては、 **/allservices** API を使用します。 **/AllServices**は匿名の要求を受け入れるし、そのため、アクセス トークンを必要としません。

****


|**ヘッダー**|**説明**|
|:-----|:-----|
|`Accept`| 省略可能です。 このヘッダーは、応答の内容の書式を制御します。 <br>アトム: のアプリケーション/アトム + Xml</br><br>JSON: アプリケーションまたは Json; OData = 詳細 </br><br>このヘッダーを省略すると、既定ではアトムです。 </br><br>例: 受け付ける: アプリケーションまたは Json; OData = 詳細</br>|

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|`$select`|string | 省略可能です。 オブジェクトのプロパティのコンマ区切りのリストです。 により、選択したプロパティのみをプロジェクトにサービス。 しないアプリケーションで使用されていないプロパティをダウンロードすることで帯域幅を節約するために使用されます。 Http://www.OData.org/docs/ を参照してください。 例: 機能、ServiceUri|
|`$filter`|string | 省略可能です。 元の結果セットをフィルター処理する OData 述語です。 しないアプリケーションで使用されていないオブジェクトのインスタンスをダウンロードすることで帯域幅を節約するために使用されます。 使用可能な述語関数のドキュメンテーション」タブの下の http://www.odata.org を参照してください。 |

|**応答**|**意味**|**説明**|
|:-----|:-----|:-----|
|`200`| OK |応答の本体には、投影、フィルター、および、OData 要求に従ってエンコードされた[ServiceInfo スキーマ](#DiscSvc_SvcInfoSchema)のエントリの一覧が含まれています。 [ServiceInfo スキーマ](#DiscSvc_SvcInfoSchema)スキーマの定義を参照してください。|

**例:**
```
var request = HttpWebRequest.CreateHttp("https://api.office.com/discovery/v1.0/me/services");
request.Method = "GET";
request.Headers["Accept"] = "application/json;odata=verbose";

var response = await request.GetResponseAsync().ConfigureAwait(continueOnCapturedContext: true) as HttpWebResponse;
```

## <a name="a-nameserviceinfo-schemaaserviceinfo-"></a><a name="serviceinfo-schema"></a>ServiceInfo スキーマ
<a name="DiscSvc_SvcInfoSchema"> </a>

[/サービス インスタンスの API](#DiscSvc_Services)と[/allservices API](#DiscSvc_AllServices)の Api は、その応答の本体に ServiceInfo エントリを使用します。

****

|**プロパティ**|**タイプ**|**使用例**|
|:-----|:-----|:-----|
|機能|String|MyFiles|
|serviceId|String||
|Dienstname|String|O365_SHAREPOINT|
|serviceEndpointUri|String|https://Contoso-My.SharePoint.com/Personal/alexd_contoso_com |
|serviceResourceId|String|https://Contoso-My.SharePoint.com|

## <a name="a-nameadditional-resourcesa"></a><a name="additional-resources"></a>その他のリソース
<a name="bk_addresources"> </a>


-  [Office 365 のプラットフォーム上での開発の概要](..\howto\platform-development-overview.md)

-  [探索サービス API を使用して、Office 365 アプリケーションのエンドポイントを検索するには](..\howto\discover-service-endpoints.md)

-  [Office 365-の 探索サービスを使用する方法を Api。](http://code.msdn.microsoft.com/Office-365-APIs-How-to-use-609102ea)
