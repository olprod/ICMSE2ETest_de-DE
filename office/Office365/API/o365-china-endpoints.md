MS-です。 TocTitle: 中国のタイトルの Office 365 の API エンドポイント: 中国の説明については、Office 365 の API エンドポイント: 中国の Office 365 のアプリケーションは、Office 365 の API のリソースとサービスで別の Url があります。 21Vianet によって運営されて、中国の Office 365 の API のエンドポイントを検索します。 MS-です。 ContentId: F8110642-6BAB-4C68-9306-A0B01B820A81 ms.topic: ms.date を参照 (API): 2016 年 4 月 19 日

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="a-nameapi-endpoints-of-office-365-operated-by-21vianeta21vianet-office-365-api-"></a><a name="api-endpoints-of-office-365-operated-by-21vianet"></a>21Vianet によって運営されて Office 365 の API エンドポイント

 _**に適用されます:** 21Vianet によって運営されて中国の Office 365_


21Vianet 中国で運用している Office 365 のアプリケーションは、API リソースおよび関連するサービスその他の Office 365 サービスのさまざまな Url があります。 これらの違いは、次のように記載されています。 

## <a name="a-namemicrosoft-graph-apiagraph-api"></a><a name="microsoft-graph-api"></a>Diagramm-API 

アプリケーションが使用されている Office 365 の統合 API は、 [Microsoft Graph](https://graph.microsoft.io/en-us/)を使用するのには今すぐアップグレードできます。

###<a name="a-nameservice-root-endpointa-"></a><a name="service-root-endpoint"></a>サービスのルート エンドポイント

|**Diagramm の 21Vianet によって運営されて**|**Microsoft Graph**|
|:-----|:-----|
| `https://microsoftgraph.chinacloudapi.cn` | `https://graph.microsoft.com` | 

###<a name="a-namemicrosoft-graph-exploreragraph-"></a><a name="microsoft-graph-explorer"></a>Diagramm のエクスプ ローラー

|**Diagramm の 21Vianet によって運営されて**|**Microsoft Graph**|
|:-----|:-----|
| `https://graphexplorerchina.azurewebsites.net` | `https://graphexplorer2.azurewebsites.net` | 


[Diagramm のエンドポイントとサービスの機能](https://graph.microsoft.io/en-us/docs/overview/deployments)について詳しく説明します。

## <a name="a-nameazure-active-directory-graph-apiaazure-active-directory-api"></a><a name="azure-active-directory-graph-api"></a>Azure Active Directory グラフ-API 

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|  
| `https://graph.chinacloudapi.cn` | `https://graph.windows.net` |

## <a name="a-namediscovery-service-apia-api"></a><a name="discovery-service-api"></a>探索サービスの-API
|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| まだ利用できません。 |  `https://api.office.com/discovery` |

探索サービスは、Microsoft Diagramm を呼び出す場合は必要ありません (`https://graph.microsoft.com/`) 。

## <a name="a-namecalendar-apia-api"></a><a name="calendar-api"></a>カレンダー-API

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://partner.outlook.cn` | `https://graph.microsoft.com`<br /><br />`https://outlook.office.com` |

たとえば、Office 365 を運用している 21Vianet のバージョン 2.0 を使用してユーザーの予定表を取得するには、次のように送信します。 、`GET`を要求する`https://partner.outlook.cn/api/v2.0/me/calendars`。

## <a name="a-namecontacts-apia-api"></a><a name="contacts-api"></a>連絡先-API

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://partner.outlook.cn` | `https://graph.microsoft.com`<br /><br />`https://outlook.office.com` |

たとえば、Office 365 を運用している 21Vianet のバージョン 2.0 を使用してユーザーの連絡先を取得するには、次のように送信します。 、`GET`を要求する`https://partner.outlook.cn/api/v2.0/me/contacts`。

## <a name="a-namemail-apia-api"></a><a name="mail-api"></a>メール-API

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://partner.outlook.cn` | `https://graph.microsoft.com`<br /><br />`https://outlook.office.com` |

たとえば、Office 365 を運用している 21Vianet のバージョン 2.0 を使用してユーザーの電子メールを取得するには、次のように送信します。 、`GET`を要求する`https://partner.outlook.cn/api/v2.0/me/messages`。

## <a name="a-namefiles-apia-api"></a><a name="files-api"></a>ファイル-API

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://{tenant}-my.sharepoint.cn/_api/v1.0/me`<br /><br />`https://{tenant}.sharepoint.cn/{site-path}/_api/v1.0` | `https://graph.microsoft.com`<br /><br />`https://{tenant}-my.sharepoint.com/_api/v1.0/me`(ビジネスのための OneDrive)<br /><br />`https://{tenant}.sharepoint.com/{site-path}/_api/v1.0`(SharePoint サイト) |

## <a name="a-namecalendar-contacts-and-mail-odata-entitya-odata-"></a><a name="calendar-contacts-and-mail-odata-entity"></a>予定表、連絡先、およびメールの OData のエンティティ

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://partner.outlook.cn/api/{version}/$metadata` | `https://graph.microsoft.com/{version}/$metadata`<br /><br />`https://outlook.office.com/api/{version}/$metadata` |  

正確なバージョンを指定して`{version}`。 などの`@odata.context`21Vianet によって運営されて Office 365 の v2. 0 のエンティティは、カレンダーの`https://partner.outlook.cn/api/v2.0/$metadata#Me/Calendars/$entity`。

## <a name="a-namefiles-odata-entitya-odata-"></a><a name="files-odata-entity"></a>ファイル OData のエンティティ

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://{tenantId}-my.sharepoint.cn/_api/v1.0/$metadata` | `https://graph.microsoft.com/v1.0/$metadata`<br /><br />`https://{tenantId}-my.sharepoint.com/_api/v1.0/$metadata` |  

<br />
次の Url は、アカウントおよび認証に関連します。

## <a name="a-namemicrosoft-azureamicrosoft-azure"></a><a name="microsoft-azure"></a>Microsoft Azure

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
|`https://account.windowsazure.cn` | `https://account.windowsazure.com` |

`https://account.windowszaure.cn`21Vianet によって運営されて Office 365 の開発環境を設定します。 詳細については、 [Office 365 の開発環境のセットアップ](..\howto\setup-development-environment.md)を参照してください。

## <a name="a-nameazure-openid-connect-and-oauthaazure-openid-oauth"></a><a name="azure-openid-connect-and-oauth"></a>Azure OpenID を接続し、OAuth

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://login.chinacloudapi.cn` | `https://login.microsoftonline.com` |

使用`https://login.chinacloudapi.cn/common/oauth2/authorize`ユーザーを認証するために、 `https://login.chinacloudapi.cn/common/oauth2/token` 21Vianet によって運営されて Office 365 の呼び出しをアプリケーションがトークンを取得するにします。

## <a name="a-nameoffice-365-developer-siteaoffice-365-"></a><a name="office-365-developer-site"></a>Office 365 開発者向けサイト

次の Url の`{your-sub-domain}`は、開発者向けサイトを設定するときに指定した名前です。

|**Office 365 の 21Vianet によって運営されて**|**Office 365**|
|:-----|:-----|
| `https://{your-sub-domain}.partner.onmschina.cn` | `https://{your-sub-domain}.onmicrosoft.com` |