---
MS-です。 TOCTitle: Office 365 のデータ拡張機能の REST-API リファレンス タイトル: Office 365 のデータ拡張機能の REST-API リファレンスの説明: oData オープン型の拡張機能の一部としてプロパティを動的に作成するには、Office 365 と Outlook.com を取得、設定および削除するカスタム データのデータ拡張機能の REST-API を使用する方法を参照します。 MS-です。 ContentId: 6034eaed-831f-4a6e-888a-0c670476023f ms.topic: ms.date を参照 (API): 2016 年 4 月 20 日

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="a-nameoffice-365-data-extensions-rest-api-referenceaoffice-365-api-"></a><a name="office-365-data-extensions-rest-api-reference"></a>Office 365 のデータ拡張機能の残りの部分の API リファレンス

[!INCLUDE [Add the Outlook REST API filters--v2 default v1 disabled](../includes/controls/addOutlookversion_v2default_v1disabled.html)]

 _**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<p class="previewnote">このドキュメントでは、プレビューの状態で Office 365 のデータ拡張機能 API のベータ版について説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 可能な場合、バージョン 2.0 は現在推奨されるバージョンです。</p>

Office 365 のデータ拡張機能の REST-API-は、メッセージ、イベント、またはユーザーのアカウントの連絡先にカスタム データを動的に格納するアプリケーションです。 アカウントは、Office 365 または Microsoft アカウント (Hotmail.com、Live.com、MSN.com、Outlook.com、Passport.com) に配置できます。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

**API のベータ版では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Office 365 のデータ拡張機能の REST API は、メッセージ、イベント、またはユーザーのアカウントの連絡先にカスタム データを動的に格納するアプリケーションです。 アカウントは、Office 365 または Microsoft アカウント (Hotmail.com、Live.com、MSN.com、Outlook.com、Passport.com) に配置できます。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

**API のバージョン 2.0 では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


## <a name="a-nameoverviewa"></a><a name="overview"></a>概要

Outlook の REST-API でのデータ拡張機能は、v4 は、実行時に指定できるプロパティが含まれている型を開き、OData です。 _拡張_動的に JSON ペイロードにユーザー設定のプロパティと値を指定することによって既に定義されてで、エンティティ データ モデル (EDM) のメッセージ、イベント、または取引先担当者のエンティティ型のインスタンスにデータ拡張機能 API を使用することができます。 これは、ため、このようなエンティティの種類の定義より柔軟性が高く、この目的で新しいエンティティ型を定義するのには時間を節約します。

**.-Kennung Erweiterungsname**プロパティは、すべての拡張機能に対して定義されている唯一のプロパティです。 拡張モジュールの名前が一意であることを確認するために 1 つの方法に依存している_自分のドメイン_では、たとえば、逆引きドメイン名システム (DNS) メソッドを使用するには`Com.Contoso.Contact`です。 拡張子名でマイクロソフトのドメインを使用することはしません。

拡張子がオープン型であるために、エンティティのインスタンスに固有の追加データを指定できます。 などの会社名と最初の参照元などのカスタム データを追跡する個々 のビジネス用連絡先の拡張機能を作成および次に示すように JSON ペイロードのデータを指定できます。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```
POST https://outlook.office.com/api/beta/me/contacts('{contact_id}')/extensions
{
   @odata.type: "Microsoft.OutlookServices.OpenTypeExtension",  
   "ExtensionName": "Com.Contoso.Customer",
   "CompanyName": "Alpine Skis",
   "InitialReferrer":  "Robin McCall"
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```
POST https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/extensions
{
   @odata.type: "Microsoft.OutlookServices.OpenTypeExtension",  
   "ExtensionName": "Com.Contoso.Customer",
   "CompanyName": "Alpine Skis",
   "InitialReferrer":  "Robin McCall"
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


データ拡張機能 API を使用すると、新規または既存のリソースに対して CRUD 操作を実行します。 についての[操作をサポート](#ExtensionOperations)します。 

OData のオープン型の詳細については、 [OData.org](http://www.odata.org/documentation/)の OData v4 のマニュアルを参照してください。

## <a name="a-nameusing-the-data-extensions-rest-apia-rest-api-"></a><a name="using-the-data-extensions-rest-api"></a>データ拡張 REST-API を使用します。

###<a name="a-namedata-extensions-or-extended-propertiesa"></a><a name="data-extensions-or-extended-properties"></a>データ拡張機能または拡張プロパティでしょうか。

データ拡張機能は、格納して、カスタムのデータへのアクセスに関連するほとんどのシナリオの推奨されるソリューションです。 ただし、REST API の Outlook メタデータを通じて公開されていない Outlook MAPI-プロパティのカスタムのデータにアクセスする必要がある場合は、[拡張プロパティおよびその他の API](..\api\extended-properties-rest-operations.md)を使用できます。 Https://Outlook.Office.com/API/ {バージョン} でメタデータを公開するプロパティを確認することができます / $Metadata、置き換えて {バージョン} v2. 0 やベータ版などで、任意のバージョンに対応します。


###<a name="a-nameauthenticationa"></a><a name="authentication"></a>認証
他の[Outlook の他の API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)、データ拡張機能 API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 データ拡張機能 API では、特定の操作を続行するには、この点に留意してください。

###<a name="a-namesupported-rest-resourcesa"></a><a name="supported-rest-resources"></a>サポートされている他のリソース 

拡張機能を作成する Outlook の REST エンドポイントでは、次のリソースのインスタンス。
- [メッセージ](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)
- [イベント](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)
- [連絡先](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)


###<a name="a-nameversion-of-apiaapi-"></a><a name="version-of-api"></a>API のバージョン

この API は、一般的な可用性 (GA) の状態に、プレビューから昇格されています。 バージョン 2.0 とベータ版のバージョンではサポートします。

`https://outlook.office.com/api/v2.0/`

`https://outlook.office.com/api/beta/`

### <a name="a-nameurl-parametersaurl-"></a><a name="url-parameters"></a>URL-パラメーター

残りのパラメーターでこの資料の次の ID を使用してプレース ホルダーの例では、Url を要求します。 拡張機能を作成するリソースのインスタンスの ID を指定する必要があります。

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。 |
|event_id|string|イベント-Id です。 |
|メッセージ-id|string|メッセージ id。 |


Outlook-REST-API と Office 365 のデータ拡張機能の REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。


****

<a name="ExtensionOperations"> </a>
## <a name="a-nameextension-operationsa"></a><a name="extension-operations"></a>拡張オペレーション

[既存の項目の拡張機能を作成する](#CreateExtensionInExistingItem) | [拡張子が付いた新しいアイテムを作成する](#CreateExtensionInNewItem) | 
[の拡張機能を取得する](#GetExtension) | [拡張子を持つ展開されたアイテムを取得](#GetExpandedExtension) |  
[検索し、拡張子を持つアイテムを展開する](#FindAndExpandItemsWithExtension) | 
[追加の拡張機能でデータを変更または](#UpdateExtension) | [の拡張機能を削除](#DeleteExtension)


<a name="CreateExtensionInExistingItem"> </a>

### <a name="a-namecreate-extension-in-an-existing-itema"></a><a name="create-extension-in-an-existing-item"></a>既存の項目の拡張機能を作成します。

拡張機能を作成し、リソースのインスタンスを指定のカスタム プロパティを追加します。 リソースは、メッセージ、カレンダー イベント、または、Office 365 または Outlook.com にお問い合わせください。 JSON ペイロード内のデータには、プリミティブ型、またはプリミティブ型の配列ができます。

サポートされているリソースごとに、拡張機能を作成します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages('{message_id}')/extensions
POST https://outlook.office.com/api/beta/me/events('{event_id}')/extensions
POST https://outlook.office.com/api/beta/me/contacts('{contact_id}')/extensions
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages('{message_id}')/extensions
POST https://outlook.office.com/api/v2.0/me/events('{event_id}')/extensions
POST https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/extensions
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_本文パラメーター_|
|.-Kennung Erweiterungsname|string|拡張機能の一意の文字列識別子です。 必須。|

 
**要求のサンプル**

この例では、指定されたメッセージの拡張機能を作成します。 要求の本体には、拡張機能は、次が含まれています。
- 型`Microsoft.OutlookServices.OpenTypeExtension`が定義されている Outlook REST-API メタデータで OData オープン型です。 
- 拡張子"com.contoso.Referral"です。
- JSON ペイロードにユーザー定義のプロパティとして格納される追加のデータ: `CompanyName`、 `DealValue`、および`ExpirationDate`のプリミティブ型を含んでいると`TopModels`と`TopSalespersons`プリミティブ型の配列を含んでいます。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```
POST https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions

Content-Type: application/json

{ 
  "@odata.type" : "Microsoft.OutlookServices.OpenTypeExtension", 
  "ExtensionName" : "Com.Contoso.Referral", 
  "CompanyName" : "Wingtip Toys",
  "DealValue@odata.type": "#Int64", 
  "DealValue" : 500050, 
  "ExpirationDate" : "2015-12-03T10:00:00.000Z",
  "TopModels": [
     3001,
     4002,
     5003
  ],
  "TopSalespersons": [
     "Dana Swope",
     "Fanny Downs",
     "Randi Welch"
  ]
} 
```

**応答の例**

によって正常な応答が示されている、`HTTP 201 Created`応答コード。

応答の本体には、次新しい拡張機能にはが含まれています。
- 既定のプロパティの**.-Kennung Erweiterungsname**。
- **ID**プロパティの完全修飾名を持つ`Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`。
- カスタムのデータを格納します。  

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "ExtensionName": "Com.Contoso.Referral",
    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys",
    "DealValue@odata.type": "#Int64",
    "DealValue": 500050,
    "ExpirationDate": "2015-12-03T10:00:00.000Z",
    "TopModels@odata.type": "#Collection(Int32)",
    "TopModels": [
      3001,
      4002,
      5003
    ],
    "TopSalespersons@odata.type": "#Collection(String)",
    "TopSalespersons": [
      "Dana Swope",
      "Fanny Downs",
      "Randi Welch"
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```
POST https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions

Content-Type: application/json

{ 
  "@odata.type" : "Microsoft.OutlookServices.OpenTypeExtension", 
  "ExtensionName" : "Com.Contoso.Referral", 
  "CompanyName" : "Wingtip Toys",
  "DealValue@odata.type": "#Int64", 
  "DealValue" : 500050, 
  "ExpirationDate" : "2015-12-03T10:00:00.000Z",
  "TopModels": [
     3001,
     4002,
     5003
  ],
  "TopSalespersons": [
     "Dana Swope",
     "Fanny Downs",
     "Randi Welch"
  ]
} 
```

**応答の例**

によって正常な応答が示されている、`HTTP 201 Created`応答コード。

応答の本体には、次新しい拡張機能にはが含まれています。
- 既定のプロパティの**.-Kennung Erweiterungsname**。
- **ID**プロパティの完全修飾名を持つ`Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`。
- カスタムのデータを格納します。  

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "ExtensionName": "Com.Contoso.Referral",
    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys",
    "DealValue@odata.type": "#Int64",
    "DealValue": 500050,
    "ExpirationDate": "2015-12-03T10:00:00.000Z",
    "TopModels@odata.type": "#Collection(Int32)",
    "TopModels": [
      3001,
      4002,
      5003
    ],
    "TopSalespersons@odata.type": "#Collection(String)",
    "TopSalespersons": [
      "Dana Swope",
      "Fanny Downs",
      "Randi Welch"
    ]
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


****

<a name="#CreateExtensionInNewItem)"></a>

### <a name="a-namecreate-extension-in-a-new-itema"></a><a name="create-extension-in-a-new-item"></a>新しい項目の拡張機能を作成します。

同じ POST 呼び出し内のすべてのリソースの新しいインスタンスを作成するときに 1 つまたは複数の拡張機能を作成し、拡張機能にカスタム プロパティを追加します。 リソースは、メッセージ、カレンダー イベント、または、Office 365 または Outlook.com にお問い合わせください。 JSON ペイロード内のデータには、プリミティブ型、またはプリミティブ型の配列ができます。

サポートされているリソースごとに、拡張機能を作成するには、POST 要求の本文に拡張機能が含まれ、そのリソースを作成するような投稿を確認します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages
POST https://outlook.office.com/api/beta/me/events
POST https://outlook.office.com/api/beta/me/contacts
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages
POST https://outlook.office.com/api/v2.0/me/events
POST https://outlook.office.com/api/v2.0/me/contacts
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_本文パラメーター_|
|.-Kennung Erweiterungsname|string|拡張機能の一意の文字列識別子です。 必須。|

 
**要求のサンプル**

この例では、同じ呼び出し内のメッセージは、拡張機能を作成します。 要求の本体には、次のものが含まれています。
- **件名**、**本文**、および**ToRecipients**プロパティは、新しいメッセージの一般的です。 
- および拡張機能を。
  - 型`Microsoft.OutlookServices.OpenTypeExtension`が定義されている Outlook REST-API メタデータで OData オープン型です。 
  - 拡張子"com.contoso.Referral"です。
  - JSON ペイロードにユーザー定義のプロパティとして格納される追加のデータ: `CompanyName`、 `ExpirationDate`、および`DealValue`のプリミティブ型を含んでいると`TopModels`と`TopSalespersons`プリミティブ型の配列を含んでいます。  

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```
POST https://outlook.office.com/api/beta/me/messages

Content-Type: application/json

{
  "Subject": "Annual review",
  "Body": {
    "ContentType": "HTML",
    "Content": "You should be proud!"
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "rufus@contoso.com"
      }
    }
  ],
  "Extensions": [
    {
      "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
      "ExtensionName": "Com.Contoso.Referral",
      "CompanyName": "Wingtip Toys",
      "ExpirationDate": "2015-12-30T11:00:00.000Z",
      "DealValue": 10000,
      "TopModels": [
        3001,
        4002,
        5003
      ],
      "TopSalespersons": [
        "Dana Swope",
        "Fanny Downs",
        "Randi Welch"
      ]
    }
  ]
}
```

**応答の例**

によって正常な応答が示されている、`HTTP 201 Created`応答コード。

応答の本体には、新しいメッセージと、新しい拡張機能は、次のプロパティが含まれています。
- **ID**プロパティの完全修飾名を持つ`Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`。 
- 既定のプロパティ**.-Kennung Erweiterungsname**は、要求で指定します。
- カスタム プロパティとして格納されている要求で指定されたカスタム データ。 

```
{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Messages
('AAMkAGEbs88AAB84uLuAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj\"",
  "Id": "AAMkAGEbs88AAB84uLuAAA=",
  "CreatedDateTime": "2015-10-30T03:03:43Z",
  "LastModifiedDateTime": "2015-10-30T03:03:43Z",
  "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj",
  "Categories": [ ],
  "ReceivedDateTime": "2015-10-30T03:03:43Z",
  "SentDateTime": "2015-10-30T03:03:43Z",
  "HasAttachments": false,
  "Subject": "Annual review",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r
\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nYou should be proud!\r\n</body>\r
\n</html>\r\n"
  },
  "BodyPreview": "You should be proud!",
  "Importance": "Normal",
  "ParentFolderId": "AQMkAGEwAAAIBDwAAAA==",
  "Sender": null,
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "rufus@contoso.com",
        "Name": "John Doe"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkAGEFGugh3SVdMzzc=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?
ItemID=AAMkAGEbs88AAB84uLuAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "Extensions@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages
('AAMkAGEbs88AAB84uLuAAA%3D')/Extensions",
  "Extensions": [
    {
      "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
      "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Messages
('AAMkAGEbs88AAB84uLuAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
      "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
      "ExtensionName": "Com.Contoso.Referral",
      "CompanyName": "Wingtip Toys",
      "ExpirationDate": "2015-12-30T11:00:00.000Z",
      "DealValue": 10000,
      "TopModels@odata.type": "#Collection(Int32)",
      "TopModels": [
        3001,
        4002,
        5003
      ],
      "TopSalespersons@odata.type": "#Collection(String)",
      "TopSalespersons": [
        "Dana Swope",
        "Fanny Downs",
        "Randi Welch"
      ]
    }
  ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```
POST https://outlook.office.com/api/v2.0/me/messages

Content-Type: application/json

{
  "Subject": "Annual review",
  "Body": {
    "ContentType": "HTML",
    "Content": "You should be proud!"
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "rufus@contoso.com"
      }
    }
  ],
  "Extensions": [
    {
      "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
      "ExtensionName": "Com.Contoso.Referral",
      "CompanyName": "Wingtip Toys",
      "ExpirationDate": "2015-12-30T11:00:00.000Z",
      "DealValue": 10000,
      "TopModels": [
        3001,
        4002,
        5003
      ],
      "TopSalespersons": [
        "Dana Swope",
        "Fanny Downs",
        "Randi Welch"
      ]
    }
  ]
}
```

**応答の例**

によって正常な応答が示されている、`HTTP 201 Created`応答コード。

応答の本体には、新しいメッセージと、新しい拡張機能は、次のプロパティが含まれています。
- **ID**プロパティの完全修飾名を持つ`Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`。 
- 既定のプロパティ**.-Kennung Erweiterungsname**は、要求で指定します。
- カスタム プロパティとして格納されている要求で指定されたカスタム データ。 

```
{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Messages
('AAMkAGEbs88AAB84uLuAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj\"",
  "Id": "AAMkAGEbs88AAB84uLuAAA=",
  "CreatedDateTime": "2015-10-30T03:03:43Z",
  "LastModifiedDateTime": "2015-10-30T03:03:43Z",
  "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj",
  "Categories": [ ],
  "ReceivedDateTime": "2015-10-30T03:03:43Z",
  "SentDateTime": "2015-10-30T03:03:43Z",
  "HasAttachments": false,
  "Subject": "Annual review",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r
\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nYou should be proud!\r\n</body>\r
\n</html>\r\n"
  },
  "BodyPreview": "You should be proud!",
  "Importance": "Normal",
  "ParentFolderId": "AQMkAGEwAAAIBDwAAAA==",
  "Sender": null,
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "rufus@contoso.com",
        "Name": "John Doe"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkAGEFGugh3SVdMzzc=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?
ItemID=AAMkAGEbs88AAB84uLuAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "Extensions@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages
('AAMkAGEbs88AAB84uLuAAA%3D')/Extensions",
  "Extensions": [
    {
      "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Messages
('AAMkAGEbs88AAB84uLuAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
      "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
      "ExtensionName": "Com.Contoso.Referral",
      "CompanyName": "Wingtip Toys",
      "ExpirationDate": "2015-12-30T11:00:00.000Z",
      "DealValue": 10000,
      "TopModels@odata.type": "#Collection(Int32)",
      "TopModels": [
        3001,
        4002,
        5003
      ],
      "TopSalespersons@odata.type": "#Collection(String)",
      "TopSalespersons": [
        "Dana Swope",
        "Fanny Downs",
        "Randi Welch"
      ]
    }
  ]
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


****

<a name="GetExtension"> </a>

### <a name="a-nameget-extensiona"></a><a name="get-extension"></a>拡張子を取得します。

名前または ID が指定されたリソースのインスタンス内で、拡張機能を取得します。 リソースは、メッセージ、カレンダー イベント、または、Office 365 または Outlook.com にお問い合わせください。 

名前または ID によって、拡張機能を取得するには、同じ応答の本体が返されます。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
GET https://outlook.office.com/api/beta/me/messages('{message_id}')/extensions('{extensionId}')
GET https://outlook.office.com/api/beta/me/events('{event_id}')/extensions('{extensionId}')
GET https://outlook.office.com/api/beta/me/contacts('{contact_id}')/extensions('{extensionId}')
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages('{message_id}')/extensions('{extensionId}')
GET https://outlook.office.com/api/v2.0/me/events('{event_id}')/extensions('{extensionId}')
GET https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/extensions('{extensionId}')
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|extensionID geändert|string|リソースのインスタンスでは、すべての拡張機能の中で一意のテキスト識別子には、拡張機能ファイル名または拡張子の種類と一意の文字列識別子を連結するための完全修飾名を指定できます。 拡張機能を作成するときは、ID プロパティの完全修飾名が返されます。 必須。 |


<a name="GetExtensionExample"></a> 

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**サンプル リクエスト**

最初の例では、名前を使用して拡張機能を参照して、指定されたメッセージの拡張機能を取得

```
GET https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

2 番目の例では、id (完全修飾名) 拡張機能を参照し、指定されたメッセージの拡張機能を取得します。

```
GET https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```

**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。 

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "ExtensionName": "Com.Contoso.Referral",
    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys",
    "DealValue": 500050,
    "ExpirationDate": "2015-12-03T10:00:00Z"
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**サンプル リクエスト**

最初の例では、名前を使用して拡張機能を参照して、指定されたメッセージの拡張機能を取得

```
GET https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

2 番目の例では、id (完全修飾名) 拡張機能を参照し、指定されたメッセージの拡張機能を取得します。

```
GET https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```

**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。 

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "ExtensionName": "Com.Contoso.Referral",
    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys",
    "DealValue": 500050,
    "ExpirationDate": "2015-12-03T10:00:00Z"
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


****

<a name="GetExpandedExtension"> </a>

### <a name="a-nameget-item-expanded-with-extensiona"></a><a name="get-item-expanded-with-extension"></a>拡張子を持つ展開された項目を取得します。

フィルターで指定されている拡張子を持つリソースのインスタンスが展開されている Get、 `Id`。 リソースは、メッセージ、カレンダー イベント、または、Office 365 または Outlook.com にお問い合わせください。

抽出することができます、`Id`拡張モジュールの名前または完全修飾名は、 [Get とインスタンスが展開されて、拡張子を持つ次のようにします。 フィルター文字列内のスペース文字を[URL エンコード](http://www.w3schools.com/tags/ref_urlencode.asp)を適用することを確認します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
GET https://outlook.office.com/api/beta/me/messages('{message_id}')?$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/beta/me/events('{event_id}')?$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/beta/me/contacts('{contact_id}')?$expand=Extensions($filter=Id eq '{extensionId}')
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages('{message_id}')?$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/v2.0/me/events('{event_id}')?$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')?$expand=Extensions($filter=Id eq '{extensionId}')
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|extensionID geändert|string|リソースのインスタンスでは、すべての拡張機能の中で一意のテキスト識別子には、拡張機能ファイル名または拡張子の種類と一意の文字列識別子を連結するための完全修飾名を指定できます。 拡張機能を作成するときは、ID プロパティの完全修飾名が返されます。 必須。 |


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**要求のサンプル**

次の例では、取得し、フィルターから返される拡張機能を含めることによって指定されたメッセージを展開します。 フィルターを持つ拡張機能から返される、 `Id` 、完全修飾名と一致します。

便宜のため、予約済みの文字、スペースの URL のエンコーディングを使用して要求を次に示します。

```
GET https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')?$expand=Extensions($filter=Id%20eq%20'Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、指定されたメッセージと、フィルターから返される拡張機能のすべてのプロパティが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM\"",
    "Id": "AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===",
    "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM",
    "Categories": [
    ],
    "CreateDateTime": "2015-06-19T02:03:31Z",
    "LastModifiedDateTime": "2015-08-13T02:28:00Z",
    "Subject": "Attached is the requested info",
    "BodyPreview": "See the images attached.",
    "Body": {
        "ContentType": "HTML",
        "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none;\"><!-- P {margin-top:0;margin-bottom:0;} --></style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>See the images attached. <br>\r\n</p>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "Importance": "Normal",
    "HasAttachments": true,
    "ParentFolderId": "AQMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===QAAAA==",
    "From": {
        "EmailAddress": {
            "Address": "desmond@contoso.com",
            "Name": "Desmond Raley"
        }
    },
    "Sender": {
        "EmailAddress": {
            "Address": "desmond@contoso.com",
            "Name": "Desmond Raley"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Address": "wendy@contoso.com",
                "Name": "Wendy Molina"
            }
        }
    ],
    "CcRecipients": [
    ],
    "BccRecipients": [
    ],
    "ReplyTo": [
    ],
    "ConversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===mivdTmQ=",
    "ReceivedDateTime": "2015-06-19T02:05:04Z",
    "SentDateTime": "2015-06-19T02:04:59Z",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsDraft": false,
    "IsRead": true,
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===%2FNJTqt5NqHlVnKVBwCY4MQpaFz9SbqUDe4%2Bbs88AAAAAAEJAACY4MQpaFz9SbqUDe4%2Bbs88AAApA4JMAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "MentionedMe": null,
    "Mentioned": [
    ],
    "InferenceClassification": "Focused",
    "Extensions@odata.context": "https://outlook.office.com/api/beta/$metadata#Users('desmond40contoso.com')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions", 
    "Extensions": [ 
      { 
        "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
        "ExtensionName": "Com.Contoso.Referral",
        "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
        "CompanyName": "Wingtip Toys",
        "DealValue": 500050,
        "ExpirationDate": "2015-12-03T10:00:00Z"
      }
     ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**要求のサンプル**

次の例では、取得し、フィルターから返される拡張機能を含めることによって指定されたメッセージを展開します。 フィルターを持つ拡張機能から返される、 `Id` 、完全修飾名と一致します。

便宜のため、予約済みの文字、スペースの URL のエンコーディングを使用して要求を次に示します。

```
GET https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')?$expand=Extensions($filter=Id%20eq%20'Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、指定されたメッセージと、フィルターから返される拡張機能のすべてのプロパティが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM\"",
    "Id": "AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===",
    "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM",
    "Categories": [
    ],
    "CreateDateTime": "2015-06-19T02:03:31Z",
    "LastModifiedDateTime": "2015-08-13T02:28:00Z",
    "Subject": "Attached is the requested info",
    "BodyPreview": "See the images attached.",
    "Body": {
        "ContentType": "HTML",
        "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none;\"><!-- P {margin-top:0;margin-bottom:0;} --></style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>See the images attached. <br>\r\n</p>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "Importance": "Normal",
    "HasAttachments": true,
    "ParentFolderId": "AQMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===QAAAA==",
    "From": {
        "EmailAddress": {
            "Address": "desmond@contoso.com",
            "Name": "Desmond Raley"
        }
    },
    "Sender": {
        "EmailAddress": {
            "Address": "desmond@contoso.com",
            "Name": "Desmond Raley"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Address": "wendy@contoso.com",
                "Name": "Wendy Molina"
            }
        }
    ],
    "CcRecipients": [
    ],
    "BccRecipients": [
    ],
    "ReplyTo": [
    ],
    "ConversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===mivdTmQ=",
    "ReceivedDateTime": "2015-06-19T02:05:04Z",
    "SentDateTime": "2015-06-19T02:04:59Z",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsDraft": false,
    "IsRead": true,
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===%2FNJTqt5NqHlVnKVBwCY4MQpaFz9SbqUDe4%2Bbs88AAAAAAEJAACY4MQpaFz9SbqUDe4%2Bbs88AAApA4JMAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "MentionedMe": null,
    "Mentioned": [
    ],
    "InferenceClassification": "Focused",
    "Extensions@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Users('desmond40contoso.com')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions", 
    "Extensions": [ 
      { 
        "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
        "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
        "ExtensionName": "Com.Contoso.Referral",
        "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
        "CompanyName": "Wingtip Toys",
        "DealValue": 500050,
        "ExpirationDate": "2015-12-03T10:00:00Z"
      }
     ]
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


****

<a name="FindAndExpandItemsWithExtension"></a>
### <a name="a-namefind-and-expand-items-with-an-extensiona"></a><a name="find-and-expand-items-with-an-extension"></a>検索し、拡張子を持つアイテムを展開します。

フィルターに一致する拡張子が含まれているリソースのインスタンスが表示されます。 さらに、同じクエリでは、これらの拡張子を持つ拡張のインスタンスを取得できます。 このセクションのクエリは、このようなインスタンスを検索、展開し、応答の拡張機能が含まれます。 

リソースは、メッセージ、カレンダー イベント、または、Office 365 または Outlook.com にお問い合わせください。

抽出することができます、`Id`拡張モジュールの名前または完全修飾名は、 [Get とインスタンスが展開されて、拡張子を持つ次のようにします。 フィルター文字列内のスペース文字を[URL エンコード](http://www.w3schools.com/tags/ref_urlencode.asp)を適用することを確認します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
GET https://outlook.office.com/api/beta/me/messages?$filter=Extensions/any(f:f/Id eq '{extensionId}')&$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/beta/me/events?$filter=Extensions/any(f:f/Id eq '{extensionId}')&$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/beta/me/contacts?$filter=Extensions/any(f:f/Id eq '{extensionId}')&$expand=Extensions($filter=Id eq '{extensionId}')
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages?$filter=Extensions/any(f:f/Id eq '{extensionId}')&$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/v2.0/me/events?$filter=Extensions/any(f:f/Id eq '{extensionId}')&$expand=Extensions($filter=Id eq '{extensionId}')

GET https://outlook.office.com/api/v2.0/me/contacts?$filter=Extensions/any(f:f/Id eq '{extensionId}')&$expand=Extensions($filter=Id eq '{extensionId}')
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|extensionID geändert|string|リソースのインスタンスでは、すべての拡張機能の中で一意のテキスト識別子には、拡張機能ファイル名または拡張子の種類と一意の文字列識別子を連結するための完全修飾名を指定できます。 拡張機能を作成するときは、ID プロパティの完全修飾名が返されます。 必須。 |

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**要求のサンプル**

次の例では、検索フィルターに一致する拡張子が含まれているし、拡張機能を含めることで、それらを展開するのにはサインインしているユーザーのメールボックス内のすべてのメッセージを検索します。 フィルターを持つ拡張機能から返される、`Id`拡張モジュールの名前に一致する`Com.Contoso.Referral`。

便宜のため、予約済みの文字、スペースの URL のエンコーディングを使用して要求を次に示します。

```
GET https://outlook.office.com/api/beta/me/messages?$filter=Extensions/any(f:f/Id%20eq%20'Com.Contoso.Referral')&$expand=Extensions($filter=Id%20eq%20'Com.Contoso.Referral')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、一致する拡張子を持つすべてのメッセージとすべてのメッセージ プロパティが含まれています。 この例では、応答には、2 つのメッセージが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.EventMessage",
            "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyDREAAA=')",
            "@odata.etag": "W/\"DAAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ9tn\"",
            "Id": "AAMkADIyDREAAA=",
            "CreatedDateTime": "2016-01-06T02:20:17Z",
            "LastModifiedDateTime": "2016-01-13T02:13:54Z",
            "ChangeKey": "DAAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ9tn",
            "Categories": [
            ],
            "ReceivedDateTime": "2016-01-06T02:20:18Z",
            "SentDateTime": "2016-01-06T02:20:18Z",
            "HasAttachments": false,
            "InternetMessageId": "<BY1PR19MB0023E92E0B43F5E268406F0DF5F40@BY1PR19MB0023.namprd19.prod.outlook.com>",
            "Subject": "Accepted: Latin American Product Manual Group",
            "Body": {
                "ContentType": "Text",
                "Content": ""
            },
            "BodyPreview": "",
            "Importance": "Normal",
            "ParentFolderId": "AAMkADIyAAAAEJAAA=",
            "Sender": {
                "EmailAddress": {
                    "Name": "MOD Administrator",
                    "Address": "admin@adatumltd.onmicrosoft.com"
                }
            },
            "From": {
                "EmailAddress": {
                    "Name": "MOD Administrator",
                    "Address": "admin@adatumltd.onmicrosoft.com"
                }
            },
            "ToRecipients": [
                {
                    "EmailAddress": {
                        "Name": "Engineering",
                        "Address": "engineering@adatumltd.onmicrosoft.com"
                    }
                }
            ],
            "CcRecipients": [
            ],
            "BccRecipients": [
            ],
            "ReplyTo": [
            ],
            "ConversationId": "AAQkADIyWejUoYAg=",
            "IsDeliveryReceiptRequested": null,
            "IsReadReceiptRequested": false,
            "IsRead": true,
            "IsDraft": false,
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADIyDREAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
            "InferenceClassification": "Focused",
            "UnsubscribeData": [
            ],
            "UnsubscribeEnabled": false,
            "MeetingMessageType": "MeetingAccepted",
            "StartDateTime": {
                "DateTime": "2015-01-05T19:00:00.0000000",
                "TimeZone": "UTC"
            },
            "EndDateTime": {
                "DateTime": "2015-01-05T20:30:00.0000000",
                "TimeZone": "UTC"
            },
            "Location": {
                "DisplayName": "Mt. Adams"
            },
            "Type": "SeriesMaster",
            "Recurrence": {
                "Pattern": {
                    "Type": "RelativeMonthly",
                    "Interval": 2,
                    "Month": 0,
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Monday"
                    ],
                    "FirstDayOfWeek": "Sunday",
                    "Index": "First"
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2015-01-05",
                    "EndDate": "0001-01-01",
                    "RecurrenceTimeZone": "tzone://Microsoft/Utc",
                    "NumberOfOccurrences": 0
                }
            },
            "IsOutOfDate": false,
            "Extensions@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkADIyDREAAA%3D')/Extensions",
            "Extensions": [
                {
                    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
                    "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyDREAAA=')/Extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
                    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
                    "ExtensionName": "Com.Contoso.Referral",
                    "CompanyName": "Wingtip Toys",
                    "DealValue@odata.type": "#Int64",
                    "DealValue": 500300,
                    "ExpirationDate": "2015-12-03T10:00:00.000Z"
                }
            ],
            "Event@odata.associationLink": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Events('AAMkADIyAAAAABrdAAA=')/$ref",
            "Event@odata.navigationLink": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Events('AAMkADIyAAAAABrdAAA=')"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyAHVAAA=')",
            "@odata.etag": "W/\"CQAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ6aq\"",
            "Id": "AAMkADIyAHVAAA=",
            "CreatedDateTime": "2016-01-06T02:20:02Z",
            "LastModifiedDateTime": "2016-01-13T02:24:50Z",
            "ChangeKey": "CQAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ6aq",
            "Categories": [
            ],
            "ReceivedDateTime": "2016-01-06T02:20:02Z",
            "SentDateTime": "2016-01-06T02:20:01Z",
            "HasAttachments": false,
            "InternetMessageId": "<CY1PR19MB0032531C620A46068FDDD45DE3F40@CY1PR19MB0032.namprd19.prod.outlook.com>",
            "Subject": "International Launch Planning for XT2000",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nWe will be ready to ship XT 2000 on 10/1, how's the International launch plan going?<br>\r\n<div style=\"display:inline-block\">\r\n<table border=\"0\" cellspacing=\"0\" style=\"background-color:#F4F4F4\">\r\n<tbody>\r\n<tr>\r\n<td style=\"padding:20px; font-size:12px; color:#666666\">You're receiving this message because you're a subscribed member of the Engineering group.<br>\r\n<a href=\"https://outlook.office.com/owa/engineering@adatumltd.onmicrosoft.com/groupsubscription.ashx?realm=adatumltd.onmicrosoft.com&amp;action=conversations&amp;source=EscalatedMessage\">View group conversations</a> |\r\n<a href=\"https://adatumltd.sharepoint.com/_layouts/groupstatus.aspx?id=dbcbe107-6244-40ba-b0f1-1c46ad35435d&amp;target=documents\">\r\nView group files</a> | <a id=\"BD5134C6-8D33-4ABA-A0C4-08581FDF89DB\" href=\"https://outlook.office.com/owa/engineering@adatumltd.onmicrosoft.com/groupsubscription.ashx?realm=adatumltd.onmicrosoft.com&amp;action=unsubscribe&amp;source=EscalatedMessage\">\r\nUnsubscribe</a></td>\r\n</tr>\r\n</tbody>\r\n</table>\r\n</div>\r\n</body>\r\n</html>\r\n"
            },
            "BodyPreview": "We will be ready to ship XT 2000 on 10/1, how's the International launch plan going?\r\nYou're receiving this message because you're a subscribed member of the Engineering group.\r\nView group conversations | View group files | Unsubscribe",
            "Importance": "Normal",
            "ParentFolderId": "AAMkADIyAAAEMAAA=",
            "Sender": {
                "EmailAddress": {
                    "Name": "Engineering",
                    "Address": "engineering@adatumltd.onmicrosoft.com"
                }
            },
            "From": {
                "EmailAddress": {
                    "Name": "Garret Vargas",
                    "Address": "GarretV@adatumltd.onmicrosoft.com"
                }
            },
            "ToRecipients": [
                {
                    "EmailAddress": {
                        "Name": "Engineering",
                        "Address": "engineering@adatumltd.onmicrosoft.com"
                    }
                }
            ],
            "CcRecipients": [
            ],
            "BccRecipients": [
            ],
            "ReplyTo": [
            ],
            "ConversationId": "AAQkADIyLESZnSPc=",
            "IsDeliveryReceiptRequested": null,
            "IsReadReceiptRequested": false,
            "IsRead": false,
            "IsDraft": false,
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADIyAHVAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
            "InferenceClassification": "Focused",
            "UnsubscribeData": [
            ],
            "UnsubscribeEnabled": false,
            "Extensions@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkADIyAHVAAA%3D')/Extensions",
            "Extensions": [
                {
                    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
                    "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyAHVAAA=')/Extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
                    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
                    "ExtensionName": "Com.Contoso.Referral",
                    "CompanyName": "Wingtip Toys",
                    "DealValue@odata.type": "#Int64",
                    "DealValue": 500050,
                    "ExpirationDate": "2015-12-03T10:00:00.000Z"
                }
            ]
        }
    ]
} 
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**要求のサンプル**

次の例では、検索フィルターに一致する拡張子が含まれているし、拡張機能を含めることで、それらを展開するのにはサインインしているユーザーのメールボックス内のすべてのメッセージを検索します。 フィルターを持つ拡張機能から返される、`Id`拡張モジュールの名前に一致する`Com.Contoso.Referral`。

便宜のため、予約済みの文字、スペースの URL のエンコーディングを使用して要求を次に示します。

```
GET https://outlook.office.com/api/v2.0/me/messages?$filter=Extensions/any(f:f/Id%20eq%20'Com.Contoso.Referral')&$expand=Extensions($filter=Id%20eq%20'Com.Contoso.Referral')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、一致する拡張子を持つすべてのメッセージとすべてのメッセージ プロパティが含まれています。 この例では、応答には、2 つのメッセージが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.EventMessage",
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyDREAAA=')",
            "@odata.etag": "W/\"DAAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ9tn\"",
            "Id": "AAMkADIyDREAAA=",
            "CreatedDateTime": "2016-01-06T02:20:17Z",
            "LastModifiedDateTime": "2016-01-13T02:13:54Z",
            "ChangeKey": "DAAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ9tn",
            "Categories": [
            ],
            "ReceivedDateTime": "2016-01-06T02:20:18Z",
            "SentDateTime": "2016-01-06T02:20:18Z",
            "HasAttachments": false,
            "InternetMessageId": "<BY1PR19MB0023E92E0B43F5E268406F0DF5F40@BY1PR19MB0023.namprd19.prod.outlook.com>",
            "Subject": "Accepted: Latin American Product Manual Group",
            "Body": {
                "ContentType": "Text",
                "Content": ""
            },
            "BodyPreview": "",
            "Importance": "Normal",
            "ParentFolderId": "AAMkADIyAAAAEJAAA=",
            "Sender": {
                "EmailAddress": {
                    "Name": "MOD Administrator",
                    "Address": "admin@adatumltd.onmicrosoft.com"
                }
            },
            "From": {
                "EmailAddress": {
                    "Name": "MOD Administrator",
                    "Address": "admin@adatumltd.onmicrosoft.com"
                }
            },
            "ToRecipients": [
                {
                    "EmailAddress": {
                        "Name": "Engineering",
                        "Address": "engineering@adatumltd.onmicrosoft.com"
                    }
                }
            ],
            "CcRecipients": [
            ],
            "BccRecipients": [
            ],
            "ReplyTo": [
            ],
            "ConversationId": "AAQkADIyWejUoYAg=",
            "IsDeliveryReceiptRequested": null,
            "IsReadReceiptRequested": false,
            "IsRead": true,
            "IsDraft": false,
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADIyDREAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
            "InferenceClassification": "Focused",
            "UnsubscribeData": [
            ],
            "UnsubscribeEnabled": false,
            "MeetingMessageType": "MeetingAccepted",
            "StartDateTime": {
                "DateTime": "2015-01-05T19:00:00.0000000",
                "TimeZone": "UTC"
            },
            "EndDateTime": {
                "DateTime": "2015-01-05T20:30:00.0000000",
                "TimeZone": "UTC"
            },
            "Location": {
                "DisplayName": "Mt. Adams"
            },
            "Type": "SeriesMaster",
            "Recurrence": {
                "Pattern": {
                    "Type": "RelativeMonthly",
                    "Interval": 2,
                    "Month": 0,
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Monday"
                    ],
                    "FirstDayOfWeek": "Sunday",
                    "Index": "First"
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2015-01-05",
                    "EndDate": "0001-01-01",
                    "RecurrenceTimeZone": "tzone://Microsoft/Utc",
                    "NumberOfOccurrences": 0
                }
            },
            "IsOutOfDate": false,
            "Extensions@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkADIyDREAAA%3D')/Extensions",
            "Extensions": [
                {
                    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
                    "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyDREAAA=')/Extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
                    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
                    "ExtensionName": "Com.Contoso.Referral",
                    "CompanyName": "Wingtip Toys",
                    "DealValue@odata.type": "#Int64",
                    "DealValue": 500300,
                    "ExpirationDate": "2015-12-03T10:00:00.000Z"
                }
            ],
            "Event@odata.associationLink": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Events('AAMkADIyAAAAABrdAAA=')/$ref",
            "Event@odata.navigationLink": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Events('AAMkADIyAAAAABrdAAA=')"
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyAHVAAA=')",
            "@odata.etag": "W/\"CQAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ6aq\"",
            "Id": "AAMkADIyAHVAAA=",
            "CreatedDateTime": "2016-01-06T02:20:02Z",
            "LastModifiedDateTime": "2016-01-13T02:24:50Z",
            "ChangeKey": "CQAAABYAAACGYzsRv+OAR5zyXf6CQkRrAAADJ6aq",
            "Categories": [
            ],
            "ReceivedDateTime": "2016-01-06T02:20:02Z",
            "SentDateTime": "2016-01-06T02:20:01Z",
            "HasAttachments": false,
            "InternetMessageId": "<CY1PR19MB0032531C620A46068FDDD45DE3F40@CY1PR19MB0032.namprd19.prod.outlook.com>",
            "Subject": "International Launch Planning for XT2000",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nWe will be ready to ship XT 2000 on 10/1, how's the International launch plan going?<br>\r\n<div style=\"display:inline-block\">\r\n<table border=\"0\" cellspacing=\"0\" style=\"background-color:#F4F4F4\">\r\n<tbody>\r\n<tr>\r\n<td style=\"padding:20px; font-size:12px; color:#666666\">You're receiving this message because you're a subscribed member of the Engineering group.<br>\r\n<a href=\"https://outlook.office.com/owa/engineering@adatumltd.onmicrosoft.com/groupsubscription.ashx?realm=adatumltd.onmicrosoft.com&amp;action=conversations&amp;source=EscalatedMessage\">View group conversations</a> |\r\n<a href=\"https://adatumltd.sharepoint.com/_layouts/groupstatus.aspx?id=dbcbe107-6244-40ba-b0f1-1c46ad35435d&amp;target=documents\">\r\nView group files</a> | <a id=\"BD5134C6-8D33-4ABA-A0C4-08581FDF89DB\" href=\"https://outlook.office.com/owa/engineering@adatumltd.onmicrosoft.com/groupsubscription.ashx?realm=adatumltd.onmicrosoft.com&amp;action=unsubscribe&amp;source=EscalatedMessage\">\r\nUnsubscribe</a></td>\r\n</tr>\r\n</tbody>\r\n</table>\r\n</div>\r\n</body>\r\n</html>\r\n"
            },
            "BodyPreview": "We will be ready to ship XT 2000 on 10/1, how's the International launch plan going?\r\nYou're receiving this message because you're a subscribed member of the Engineering group.\r\nView group conversations | View group files | Unsubscribe",
            "Importance": "Normal",
            "ParentFolderId": "AAMkADIyAAAEMAAA=",
            "Sender": {
                "EmailAddress": {
                    "Name": "Engineering",
                    "Address": "engineering@adatumltd.onmicrosoft.com"
                }
            },
            "From": {
                "EmailAddress": {
                    "Name": "Garret Vargas",
                    "Address": "GarretV@adatumltd.onmicrosoft.com"
                }
            },
            "ToRecipients": [
                {
                    "EmailAddress": {
                        "Name": "Engineering",
                        "Address": "engineering@adatumltd.onmicrosoft.com"
                    }
                }
            ],
            "CcRecipients": [
            ],
            "BccRecipients": [
            ],
            "ReplyTo": [
            ],
            "ConversationId": "AAQkADIyLESZnSPc=",
            "IsDeliveryReceiptRequested": null,
            "IsReadReceiptRequested": false,
            "IsRead": false,
            "IsDraft": false,
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADIyAHVAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
            "InferenceClassification": "Focused",
            "UnsubscribeData": [
            ],
            "UnsubscribeEnabled": false,
            "Extensions@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkADIyAHVAAA%3D')/Extensions",
            "Extensions": [
                {
                    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
                    "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Messages('AAMkADIyAHVAAA=')/Extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
                    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
                    "ExtensionName": "Com.Contoso.Referral",
                    "CompanyName": "Wingtip Toys",
                    "DealValue@odata.type": "#Int64",
                    "DealValue": 500050,
                    "ExpirationDate": "2015-12-03T10:00:00.000Z"
                }
            ]
        }
    ]
} 
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



****

<a name="UpdateExtension"></a>

### <a name="a-nameadd-or-modify-data-in-an-extensiona"></a><a name="add-or-modify-data-in-an-extension"></a>追加または拡張機能内のデータを変更します。

要求の本文のプロパティと拡張機能を更新します。
- 要求の本文内のプロパティには、既存の拡張機能のプロパティの名前が一致すると、拡張機能のデータが更新されます。
- それ以外の場合そのプロパティとそのデータは、拡張機能に追加されます。 

拡張機能が、メッセージ、カレンダー イベント、または Office 365 または Outlook.com に問い合わせてリソースです。 名前または ID で参照できるし、どちらの場合も同じ応答を返します。 JSON ペイロード内のデータには、プリミティブ型、またはプリミティブ型の配列ができます。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
PATCH https://outlook.office.com/api/beta/me/messages('{message_id}')/extensions('{extensionId}')
PATCH https://outlook.office.com/api/beta/me/events('{event_id}')/extensions('{extensionId}')
PATCH https://outlook.office.com/api/beta/me/contacts('{contact_id}')/extensions('{extensionId}')
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/messages('{message_id}')/extensions('{extensionId}')
PATCH https://outlook.office.com/api/v2.0/me/events('{event_id}')/extensions('{extensionId}')
PATCH https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/extensions('{extensionId}')
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|extensionID geändert|string|リソースのインスタンスでは、すべての拡張機能の中で一意のテキスト識別子には、拡張機能ファイル名または拡張子の種類と一意の文字列識別子を連結するための完全修飾名を指定できます。 拡張機能を作成するときは、ID プロパティの完全修飾名が返されます。 必須。 |
|_本文パラメーター_|
|.-Kennung Erweiterungsname|string|拡張機能の一意の文字列識別子です。 必須。|


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**要求のサンプル**

2 このセクションの つの例のそれぞれは、[拡張機能の例を取得する](#GetExtensionExample)上で、拡張機能を使用します。 最初の拡張機能名を参照-ID で 2 つ目その要求ボディと応答は、同じです。

各例では、によって、[上記の拡張機能](#GetExtensionExample)を更新します。
- 変更`CompanyName`から`Wingtip Toys`に`Wingtip Toys (USA)`
- 変更`DealValue`から`500050`に`500100`
- カスタム プロパティとして新しいデータを追加します。`Updated`

次の使用例は、名前を使用して拡張機能を参照します。
```
PATCH https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions('Com.Contoso.Referral')

Content-Type: application/json

{
    "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
    "ExtensionName": "Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys (USA)",
    "DealValue": "500100",
    "ExpirationDate": "2015-12-03T10:00:00.000Z",
    "Updated": "2015-10-29T11:00:00.000Z"
} 
```


次の使用例は、その-ID (完全修飾名) で拡張機能を参照します。
```
PATCH https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')

Content-Type: application/json

{
    "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
    "ExtensionName": "Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys (USA)",
    "DealValue": "500100",
    "ExpirationDate": "2015-12-03T10:00:00.000Z",
    "Updated": "2015-10-29T11:00:00.000Z"
} 
```

**応答の例**

によって正常な応答が示されている、 `HTTP 200 OK` 、応答コードおよび応答の本体で更新された拡張機能です。

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "ExtensionName": "Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys (USA)",
    "DealValue": 500100,
    "ExpirationDate": "2015-12-03T10:00:00Z",
    "Updated": "2015-10-29T11:00:00.000Z"
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**要求のサンプル**

このセクションの 2 つの例のそれぞれは、[拡張機能の例を取得する](#GetExtensionExample)上で、拡張機能を使用します。 最初の拡張機能名を参照 ID で 2 つ目その要求ボディと応答は、同じです。

各例では、によって、[上記の拡張機能](#GetExtensionExample)を更新します。
- 変更`CompanyName`から`Wingtip Toys`に`Wingtip Toys (USA)`
- 変更`DealValue`から`500050`に`500100`
- カスタム プロパティとして新しいデータを追加します。`Updated`

次の使用例は、名前を使用して拡張機能を参照します。
```
PATCH https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions('Com.Contoso.Referral')

Content-Type: application/json

{
    "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
    "ExtensionName": "Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys (USA)",
    "DealValue": "500100",
    "ExpirationDate": "2015-12-03T10:00:00.000Z",
    "Updated": "2015-10-29T11:00:00.000Z"
} 
```


次の使用例は、その-ID (完全修飾名) で拡張機能を参照します。
```
PATCH https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')

Content-Type: application/json

{
    "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
    "ExtensionName": "Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys (USA)",
    "DealValue": "500100",
    "ExpirationDate": "2015-12-03T10:00:00.000Z",
    "Updated": "2015-10-29T11:00:00.000Z"
} 
```

**応答の例**

によって正常な応答が示されている、 `HTTP 200 OK` 、応答コードおよび応答の本体で更新された拡張機能です。

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/Extensions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.OpenTypeExtension",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/Messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "Id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "ExtensionName": "Com.Contoso.Referral",
    "CompanyName": "Wingtip Toys (USA)",
    "DealValue": 500100,
    "ExpirationDate": "2015-12-03T10:00:00Z",
    "Updated": "2015-10-29T11:00:00.000Z"
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


****

<a name="DeleteExtension"> </a>

### <a name="a-namedelete-an-extensiona"></a><a name="delete-an-extension"></a>拡張機能を削除します。

リソースの指定したインスタンスから、拡張子を削除します。 リソースは、メッセージ、カレンダー イベント、または、Office 365 または Outlook.com にお問い合わせください。

サポートされているリソースのそれぞれのインスタンスで拡張機能を削除するには。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
DELETE https://outlook.office.com/api/beta/me/messages('{message_id}')/extensions('{extension_name}')
DELETE https://outlook.office.com/api/beta/me/events('{event_id}')/extensions('{extension_name}')
DELETE https://outlook.office.com/api/beta/me/contacts('{contact_id}')/extensions('{extension_name}')
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/messages('{message_id}')/extensions('{extension_name}')
DELETE https://outlook.office.com/api/v2.0/me/events('{event_id}')/extensions('{extension_name}')
DELETE https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/extensions('{extension_name}')
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|extension_name|string|拡張機能の一意の文字列識別子です。 必須。|

 
**サンプル リクエスト**

次の例では、名前を使用して拡張機能を参照し、指定したメッセージ内の拡張子を削除します。 

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```
DELETE https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```
DELETE https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


**応答の例**

によって正常な応答が示されている、`HTTP 204 No Content`応答コード。 

****


## <a name="a-nameextension-entitiesa"></a><a name="extension-entities"></a>拡張エンティティ

<a name="ExtensionEntity"> </a>
### <a name="a-nameextensiona"></a><a name="extension"></a>拡張子

種類: **Microsoft.OutlookServices.Entity**

抽象基本型と**エンティティ**のエンティティとエンティティです。


<a name="OpenTypeExtensionEntity"> </a>
### <a name="a-nameopentypeextensionaopentypeextension"></a><a name="opentypeextension"></a>OpenTypeExtension

種類: **Microsoft.OutlookServices.Extension**

抽象、OData v4 では、エンティティ型のインスタンスを更新するのには、JSON ペイロードに動的に指定するプロパティとデータをサポートする型を開きます。   

|プロパティ|型|説明|書き込み可能でしょうか。|フィルター処理可能でしょうか。
|:-----|:-----|:-----|:-----|:-----|
|.-Kennung Erweiterungsname| string |固有の拡張機能の名前です。 独自のドメインでは、たとえば、com.contoso.Contact に基づいて逆引きドメイン名システムを使用します。 |○|不可|



****


<a name="NextSteps"> </a>
## <a name="a-namenext-stepsa"></a><a name="next-steps"></a>次のステップ

アプリケーションの構築を開始、あるいは詳細については、準備が整ったら、かどうかお任せします。

- [メール、カレンダー、および連絡先の他の Api を使用](http://dev.outlook.com/RestGettingStarted)します。

- 対話型の[API のサンド ボックス](https://apisandbox.msdn.microsoft.com/)を使用して Office 365 の Api について説明します。

- サンプルをしますか。 [きました](..\howto\starter-projects-and-code-samples.md)。


または、Office 365 のプラットフォームを使用する方法の詳細について説明します。

- [REST-API を Outlook で Outlook のデベロッパー センター](http://dev.outlook.com/RestGettingStarted/Overview)

- [Office 365 のプラットフォーム上での開発の概要](..\howto\platform-development-overview.md)

- [Office 365 アプリケーションの認証およびリソースの承認](..\howto\common-app-authentication-tasks.md)

- [Azure AD で Office 365 の Api にアクセスできるように、アプリケーションを手動で登録します。](..\howto\add-common-consent-manually.md)

- [メールの残りの部分の Api を参照します。](..\api\mail-rest-operations.md)

- [REST-Api の予定表を参照します。](..\api\calendar-rest-operations.md)

- [REST-Api リファレンスを取引先担当者します。](..\api\contacts-rest-operations.md)

- [タスクの残りの部分の-API (プレビュー)](..\api\task-rest-operations.md)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)



[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]






