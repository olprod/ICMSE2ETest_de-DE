---
ms.Toctitle: Outlook Streaming Notifications REST API reference (preview)
title: "Outlook の通知以降のストリーミング API リファレンス (プレビュー)"
description: "購読して、サービスから送信されるイベント通知を待機する、Office 365 と Outlook.com のストリーミングの通知の REST API を使用する方法を参照してください。"
ms.date: September 20, 2016
ms.openlocfilehash: b9bf400a2b2ec507806263c1092816aee7db93a4
ms.sourcegitcommit: 3f7951e0d1cd486dcad11b39b27f2fb7d8b41d14
translationtype: MT
---
[!INCLUDE[Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="a-nameoutlook-streaming-notifications-rest-api-reference-previewaoutlook-api-"></a><a name="outlook-streaming-notifications-rest-api-reference-preview"></a>Outlook の通知以降のストリーミング API リファレンス (プレビュー)

[!INCLUDE [Add the Outlook REST API filters--beta default v1 v2 disabled](../includes/controls/addOutlookversion_betadefault_v1v2disabled.html)]    

<p class="previewnote">ドキュメントのこのバージョンでは、プレビューでは、ストリーミング通知 API について説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 可能な場合、バージョン 2.0 は、現在の優先バージョンです。</p>

_**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

Outlook の通知以降のストリーミング API は、アプリケーションがユーザーのメールボックス データへの変更についてクライアントに直接接続の通知を送信します。 データは、ユーザーのメール、予定表、連絡先、または、Office 365 で、またはこれらのドメインで具体的には Microsoft アカウントでは、Azure Active Directory によってセキュリティで保護されたタスクのデータであることができます: Hotmail.com、Live.com である MSN.com、Outlook.com、および Passport.com。 

**メモ**参照のわかりやすくするため、この資料の残りの部分は、これらの Microsoft アカウントのドメインを含むように**Outlook.com**を使用します。

## <a name="a-nameoverviewa"></a><a name="overview"></a>概要

Office 365 のストリーミングの通知サービスは、クライアントとの直接接続を確立し、クライアント アプリケーションから要求されたデータの変更の通知を提供します。 

アプリケーションは、メッセージなど、ユーザーの受信トレイ内の特定のリソースの変更イベントの種類の通知をサブスクライブして、Office 365 のサーバーとクライアントの間で長期的な接続が確立されます。 トリガーとなるイベントの発生時などで新しいメッセージ、受信トレイ) 、Office 365 のサービス ストリーム クライアントに通知します。 クライアントでは、通知を解析し、新しいメッセージを取得する、未読のカウントを更新するなど、ビジネス ロジックに従って処理を実行します。

## <a name="a-namecompare-streaming-and-push-notificationsa"></a><a name="compare-streaming-and-push-notifications"></a>ストリーミングを比較し、プッシュ通知

メール、予定表、CRM アプリケーション、ローカル キャッシュ、対応するクライアントのビュー、または変更時にバックエンド システムを更新するのには通常の通知を使用します。 Outlook では、ストリーミングと[プッシュ](..\api\notify-rest-operations.md)通知をサポートしています。 プッシュ通知には、リスナーに通知をストリーミング、クライアント間の直接接続のみが必要となりますが、Office 365 のサーバーから通知を受信する Web サービスを提供するクライアントが必要ですと、Office 365 のサーバーです。 サーバーとの接続が確立されると、接続は開いたまま一定の時間にします。 この間、クライアントの投稿、長期的な`GetNotifications`回だけです。 要求を 1 トリガーとなるイベントが発生するたびにサーバーが応答ストリームの一部としてこの通知を送信できますだけです。 これまでの接続がタイムアウトになる、クライアントによって接続が切断またはネットワークに問題が発生しました。  


## <a name="a-nameuse-the-streaming-notifications-rest-apia-rest-api-"></a><a name="use-the-streaming-notifications-rest-api"></a>ストリーミング通知 REST-API を使用します。

### <a name="a-nameauthenticationa"></a><a name="authentication"></a>認証

購読、取得、および通知を閉じるに通知しリソースの種類に適したスコープを指定します。

_**必要な範囲の最小値:**対象となるリソースに対応する読み取り範囲は次のいずれかです。_
 
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _https://Outlook.Office.com/Tasks.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_

その他の[Outlook の他の Api](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)Outlook のストリーミング通知 API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 通知 API では、特定の操作を続行するには、この点に留意してください。

### <a name="a-nameversion-of-the-apiaapi-"></a><a name="version-of-the-api"></a>API のバージョン

現時点では、この API はプレビュー状態で、ベータ版の REST-API エンドポイントのみで利用可能です。

`https://outlook.office.com/api/beta/`

### <a name="a-nametarget-usera-"></a><a name="target-user"></a>ターゲット ユーザー

ストリーミング API の通知の要求は、現在のユーザーに代わって実行されます。

## <a name="a-namestreaming-notification-operationsa"></a><a name="streaming-notification-operations"></a>通知の操作をストリーミング

<a name="subscribe"> </a>
### <a name="a-namesubscribe-to-changes-in-my-mail-calendar-contacts-or-tasksa"></a><a name="subscribe-to-changes-in-my-mail-calendar-contacts-or-tasks"></a>メール、予定表、連絡先またはタスクの変更を購読します。

Office 365 または Outlook.com のメールボックスにメール、予定表イベント、連絡先、またはタスクを変更するときに通知をストリーミングをサブスクライブします。 の通知を取得を開始するクライアントの最初のステップです。 これは、リソース (エンティティまたはエンティティのコレクション) 

```no-highlight
POST https://outlook.office.com/api/beta/me/subscriptions
```

要求の本体では、ストリーミングのサブスクリプション要求の次の必要なプロパティを指定します。 詳細については、 [通知のエンティティ](#NotificationEntities)を参照してください。 

- OData.Type - は、 `"@odata.type":"#Microsoft.OutlookServices.StreamingSubscription"`。 
- **ChangeType** がそのリソースを監視するイベントの種類を指定します。 サポートされている種類の[ChangeType](#ChangeType)を参照してください。 
- **リソース** を監視し、通知を受信するリソースを指定します。 次のいずれかを指定できます。

  - 通常のフォルダーまたはメッセージ、イベント、連絡先、またはタスクのフォルダーを検索します。 例。 
  
    `https://outlook.office.com/api/beta/me/mailfolders('inbox')/messages`
  
    `https://outlook.office.com/api/beta/me/taskfolders('{folder_id}')/tasks`
   
  - または、メッセージ、イベントのトップ レベルのエンティティのコレクションは、取引先担当者、またはタスクを次のようにします。
  
    `https://outlook.office.com/api/beta/me/messages`
  
    `https://outlook.office.com/api/beta/me/events`
  
    `https://outlook.office.com/api/beta/me/contacts`
  
    `https://outlook.office.com/api/beta/me/tasks`


サブスクリプション要求が成功した場合は、サブスクリプション-ID が返されます。 既定では、このサブスクリプション-ID は有効期限が切れる 30 分以内にしない限り、クライアントの[接続に関する通知の待機を開始](#listeningForNotifications)します。 接続が開いている限り、サブスクリプションは自動的に更新します。

 
**要求のサンプル**
 
次のような要求は、ユーザーの受信トレイのストリーミングのサブスクリプションを作成、更新、および削除の変更を作成します。
 
```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1
Content-Type: application/json
 
{
   @odata.type: "#Microsoft.OutlookServices.StreamingSubscription",
   Resource: "https://outlook.office.com/api/beta/me/mailfolders('inbox')/Messages",
   ChangeType: "Created,Updated,Deleted"
}
```

**応答の例**

正常な応答は HTTP 201 が返され、サブスクリプション ID が含まれています例の応答は、次のようにします。

```
HTTP/1.1 201 Created

{
    "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Subscriptions/$entity",
    "@odata.type":"#Microsoft.OutlookServices.StreamingSubscription",
    "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Subscriptions('RUM4OEJFNUIQUQ4MQ==')",
    "Id":"RUM4OEJFNUIQUQ4MQ==",
    "Resource":"https://outlook.office.com/api/beta/me/mailfolders('inbox')/Messages",
    "ChangeType":"Created, Updated, Deleted, Missed"
}
```

**通知の条件を絞り込む**

<!-- Commenting out for now as we're not exposing rich notifications yet

You can request that specific fields be returned in the notification by using a ``$select`` 
clause. By requesting specific fields your client application can speed up the display of 
information to the user, such as showing the subject of an email message without waiting for 
a request and response for details about the message.
 
 ```no-highlight
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1
Content-Type: application/json
 
{
   @odata.type: "#Microsoft.OutlookServices.StreamingSubscription",
   Resource: "https://outlook.office.com/api/beta/me/mailfolders('inbox')/Messages?$select=subject,from",
   ChangeType: "Created,Updated,Deleted"
}
 ```

-->

使用して、一部のアイテムの通知を制限することも、``$filter``句。 DIE フィールドに「プラン A」とメッセージが変更された場合にのみ通知を返すするサブスクリプションを作成します。 などの次のような要求は、 [件名]
 
```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1
Content-Type: application/json
 
{
   @odata.type: "#Microsoft.OutlookServices.StreamingSubscription",
   Resource: "https://outlook.office.com/api/beta/me/mailfolders('inbox')/Messages?$filter=Subject%20eq%20%27Supplements%27",
   ChangeType: "Created,Updated,Deleted"
}
```
 
正常な応答は、次のようになります。

```
HTTP/1.1 201 Created

{
    "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Subscriptions/$entity",
    "@odata.type":"#Microsoft.OutlookServices.StreamingSubscription",
    "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Subscriptions('MjcwOUQ2MjEtQUQ4MQ==')",
    "Id":"MjcwOUQ2MjEtQUQ4MQ==",
    "Resource":"https://outlook.office.com/api/beta/me/mailfolders('inbox')/Messages?$filter=Subject%20eq%20%27Supplements%27",
    "ChangeType":"Created, Updated, Deleted, Missed"
}
```

<a name="listeningForNotifications"></a>
### <a name="a-namelisten-for-notificationsa"></a><a name="listen-for-notifications"></a>通知を待機します。
 
クライアントでは、保留中の通知のストリーミングを開始するようサーバーに要求を指定したサブスクリプションの送信接続の長期的なを作成します。

```no-highlight
POST https://outlook.office.com/api/beta/Me/GetNotifications
```

POST-要求は、指定まで完了しない この`ConnectionTimeoutinMinutes`に達するとの問題と、クライアントまたはサーバーが接続を終了してもう一方を使用する必要がある場合やサーバーが応答を JSON の Blob を終了します。 

接続が、接続を使用するすべてのサブスクリプションは、自動更新します。 接続が終了する場合は、これらの購読期限は 30 分にも、クライアントは、これらのサブスクリプションに対して新しい接続を設定しない限り、です。

この POST 要求を行うコードが返されるステータス コードを処理するかどうかを確認`HTTP 404 Not found`を指定したサブスクリプションが期限切れ実際に返されます。 かどうかよう、もう一度その通知をリッスンする前に[新しいサブスクリプションを要求](#subscribe)します。


|本文が必要なパラメーター|型|説明|
|:-----|:-----|:-----|
|ConnectionTimeoutInMinutes|Int32|接続を有効にする必要があります生き残るを分単位の数。|
|KeepAliveNotificationIntervalInSeconds|Int32|接続は開いたまま、クライアントに通知するために、Keep alive の通知を送信するサーバーによって使用される間隔。|
|SubscriptionIds|Collection(String)|この接続で通知されるサブスクリプションの Id です。|

**サンプル リクエスト**
 
```no-highlight
POST https://outlook.office.com/api/beta/Me/GetNotifications HTTP/1.1
Content-Type: application/json
 
{
   ConnectionTimeoutInMinutes: 30,
   KeepAliveNotificationIntervalInSeconds: 15,
   SubscriptionIds: [
       "N0UzMEU4RjMtMjg1Ri00OEFGLUE5NzEtRDM5MkI3NjBDMDY5XzdFMzU4QTE1LTFCQjAtNDc4NS04MTg2LUYwRjFFNUVFNTNDRg=="
   ]
}
```

要求の 1 つ以上のサブスクリプション ID を含めることによって、複数のサブスクリプションの通知をリッスンするように、同一の長期的な接続を使用できます。 BUCHEN

```no-highlight
POST https://outlook.office.com/api/beta/Me/GetNotifications HTTP/1.1
Content-Type: application/json
 
{
   ConnectionTimeoutInMinutes: 30,
   KeepAliveNotificationIntervalInSeconds: 15,
   SubscriptionIds: [
       "N0UzMEU4RjMtMjg1Ri00OEFGLUE5NzEtRDM5MkI3NjBDMDY5XzdFMzU4QTE1LTFCQjAtNDc4NS04MTg2LUYwRjFFNUVFNTNDRg==",
       "Dc4NS04MTg2LUYwRjFFNUVFNTNDRgN0UzMEU4RjMtMjg1Ri00OEFGLUE5NzEtRDM5MkI3NjBDMDY5XzdFMzU4QTE1LTFCQjAtN=="
   ]
}
```


**応答ストリームのサンプル**

サービスを設定すると、クライアントは通知の JSON の Blob の先頭を受信します。

```no-highlight
{
    {"@odata.context":"https://outlook.office.com/api/beta/metadata#Notifications", 
    "value": [
```

サーバーでは、開き、アクティブな接続を維持するのには一定の間隔で Keep-alive-の通知を送信します。 クライアントでこの間隔を設定します`KeepAliveNotificationIntervalInSeconds`プロパティ。 Lassen Sie alive の通知の形式は次のとおりです。

```no-highlight
{
    "@odata.type": "#Microsoft.OutlookServices.KeepAliveNotification",
    "Status": "OK"
}
```

トラックされた変更は、サーバーで発生する場合、サーバーは、接続を使用してクライアントに通知を送信します。 サーバーの設定は、各通知に、`SubscriptionExpirationDateTime`プロパティ、および前の通知が成功した場合に限り更新することができます。 

```no-highlight
{ 
    "@odata.type": "#Microsoft.OutlookServices.Notification",
    "Id": null, 
    "SubscriptionId": "N0UzMEU4...", 
    "SubscriptionExpirationDateTime": "2016-09-09T18:36:42.3454926Z",
    "SequenceNumber": 9, 
    "ChangeType": "Created", 
    "Resource": "https://outlook.office.com/api/beta/Users('bee8ce18...')", 
    "ResourceData": { 
        "@odata.type": "#Microsoft.OutlookServices.Message", 
        "@odata.id": "https://outlook.office.com/api/beta/Users('bee8ce18...')", 
        "@odata.etag": "W/\"CQAAABYAAAB+0z/4Ly/1ToDr5FGl5k99AAABl5Do\"", 
        "Id": "AAMkADdl..." 
    } 
} 
```

アプリケーションが同じの長期的な接続で複数の通知をリッスンしているときに使用できます、 ``SubscriptionId`` 、サブスクリプション、通知を送信するかを決定するフィールドです。

**メモ**サーバーから送信された 2 つ目およびそれ以降の通知で業界をリードする通知を作成するのには角かっこの前にカンマがある有効な JSON。

```no-highlight
,{
    "Id": null, 
    "SubscriptionId": "N0UzMEU4...", 
    ...
}
```

<a name="closingTheConnection"></a>
### <a name="a-nameclose-the-connectiona"></a><a name="close-the-connection"></a>接続を閉じる

タイムアウトを指定する場合、``ConnectionTimeoutInMinutes``プロパティに達すると、サーバーが接続を閉じるし、JSON Blob の最後に次のように送信します。

```no-highlight
    ]
}
```

ネットワークの問題や再起動などサーバーへの変更などその他の状況では、接続が切断する可能性があります。 クライアントは、接続がアクティブのままか削除されたかを確認するのには、Keep alive の通知を使用できます。 後者の場合、クライアントが再接続しようと、既存のサブスクリプション ID を使用してサブスクリプション ID の有効期限が切れている場合は、接続を再確立するために新しいサブスクリプション要求を行ってください。

POST-要求をキャンセルし、接続を切断できます。 場合は、クライアントはこれ以上のサブスクリプションをリッスンするように、クライアントは 次回のサーバーは、通知を送信しようとしていますがエラーが発生、接続のドロップを検出、Keep alive の通知を停止して接続を閉じます。


<a name="notificationEntities"></a>
## <a name="a-namenotification-entities-and-enumerationsa"></a><a name="notification-entities-and-enumerations"></a>通知のエンティティおよび列挙体

### <a name="a-namesubscriptiona"></a><a name="subscription"></a>サブスクリプション

ベースのサブスクリプションを表します。 これは、抽象基本クラスです。

基本型:**エンティティ**

|プロパティ|型|説明|書き込み可能でしょうか。|Filterbar|
|:-----|:-----|:-----|:-----|:-----|
| リソース |string|変更の監視対象リソースを指定します。|ある|n/v|
| ChangeType | ChangeType | 通知を発生させるイベントの種類を示します。 サポートされている種類の[ChangeType](#ChangeType)を参照してください。 | ある  | n/v |


### <a name="a-namenotificationa"></a><a name="notification"></a>通知

クライアントに送信される通知を表します。

基本型:**エンティティ**

|プロパティ|型|説明|書き込み可能でしょうか。|Filterbar|
|:-----|:-----|:-----|:-----|:-----|
|サブスクリプション-Id|string|サブスクリプションの一意の識別子です。|非表示|該当なし|
|SequenceNumber|Int32|変更通知のシーケンスの値を示します。|非表示|該当なし|
|ChangeType|string|通知を発生させたイベントの種類を示します。 サポートされている種類の[ChangeType](#ChangeType)を参照してください。  |非表示|該当なし|
|リソース|string|変更の監視対象リソース項目を指定します。|非表示|該当なし|
|ResourceData|エンティティ|変更されたエンティティを識別します。 これは、ナビゲーション プロパティ|非表示|該当なし|


< [名] = "ChangeType" ></a>
###<a name="a-namechangetypeachangetype"></a><a name="changetype"></a>ChangeType

発生するイベントの種類を指定する列挙体には、通知を発生できるリソースがサポートされています。

サポートされている値。

- 受信確認
- 作成日時
- 削除された
- 失われています。 Eine`Missed`通知は、通知サービスは、要求された通知を送信できない場合に発生します。
- 更新


<a name="NextSteps"></a>
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

- [Outlook の REST-API を使用します。](..\api\use-outlook-rest-api.md)

- [メールの残りの部分の Api を参照します。](..\api\mail-rest-operations.md)

- [REST-Api の予定表を参照します。](..\api\calendar-rest-operations.md)

- [REST-Api リファレンスを取引先担当者します。](..\api\contacts-rest-operations.md)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)

[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]


