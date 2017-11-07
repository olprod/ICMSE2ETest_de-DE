<a name="-ms-toctitle-outlook-rest-api-outlook-api-office-365-outlookcom-rest-api-ms-contentid-c324d0f3-b093-44d3-8ef7-6ff810f9c99a-mstopic-msdate-api-2016-5-16-"></a><<<<<<< ヘッド ms です。 TocTitle: Outlook の通知の REST API リファレンス タイトル: Outlook の通知の残りの部分の API リファレンスの説明: サブスクライブし、イベントの場合、サービスによって送信されたプッシュ通知を待機する Office 365 と Outlook.com の通知の REST API を使用する方法を参照します。 MS-です。 ContentId: c324d0f3-b093-44d3-8ef7-6ff810f9c99a ms.topic: ms.date を参照 (API): 2016 5 月 16 日 ===
---
MS-です。 TOCTitle: Outlook のプッシュ通知の REST API リファレンス タイトル: Outlook の通知の REST API リファレンスの説明: Office 365 と Outlook.com のプッシュ通知の REST API を使用して、サブスクライブし、イベントの場合、サービスによって送信されたプッシュ通知を待機する方法を参照します。 MS-です。 ContentId: c324d0f3-b093-44d3-8ef7-6ff810f9c99a ms.date: 2016 年 9 月 20 日
>>>>>>> ステージング

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="a-nameoutlook-push-notifications-rest-api-referenceaoutlook-rest-api-"></a><a name="outlook-push-notifications-rest-api-reference"></a>Outlook のプッシュ通知の REST API リファレンス

[!INCLUDE [Add the Outlook REST API filters--v2 default v1 disabled](../includes/controls/addOutlookversion_v2default_v1disabled.html)]


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<p class="previewnote">ドキュメントのこのバージョンでは、プレビューでのプッシュ通知 API について説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 可能な場合、バージョン 2.0 は現在推奨されるバージョンです。</p>


_**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_


Outlook プッシュ通知の REST-API は、アプリケーションがユーザーのメールボックス データへの変更について説明をできるようにするクライアント側の Web サービスに通知を送信します。 ユーザーのメール、予定表、連絡先、または、Office 365 では具体的にはこれらのドメインでアカウントをマイクロソフトに類似したデータでは、Azure Active Directory によってセキュリティで保護されたタスクのデータの変更を行う: Hotmail.com、Live.com である MSN.com、Outlook.com、および Passport.com。 

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

**API のベータ版では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


_**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_


Outlook プッシュ通知の REST-API は、アプリケーションに関するユーザーのメールボックス データへの変更を通知するためにクライアント側の Web サービスに、webhook を使用して通知を送信します。 データは、ユーザーのメール、予定表、連絡先、または、Office 365 で、またはこれらのドメインで具体的には Microsoft アカウントでは、Azure Active Directory によってセキュリティで保護されたタスクのデータであることができます: Hotmail.com、Live.com である MSN.com、Outlook.com、および Passport.com。  

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

**API のバージョン 2.0 では関係ないですか?** 右上のコントロールを使用し、使用バージョンを選択します。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->






## <a name="a-nameoverviewa"></a><a name="overview"></a>概要


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Office 365 のプッシュ通知サービスと API は、コールバック アドレスで Web サービスを提供し、クライアント アプリケーションに通知を配信するのには Webhooks を使用しているクライアントで動作します。 Webhooks は、通常、サード パーティの信頼される側のバックエンド Web サービスで構成されている HTTP-のコールバックです。 Web サービスでは、トリガ イベントが発生する別の動作を呼び出す 1 つのサイト上に Webhooks を構成できます。 

アプリケーションは、メッセージなど、ユーザーの受信トレイ内の特定のリソースの通知にサブスクライブする場合は、サブスクリプション要求に Webhook コールバック URL を指定します。 (受信トレイに新しいメッセージ) のようにトリガーを起動するイベントが発生する、Office 365 の通知サービスは、コールバック URL に、webhook を使用して通知をプッシュします。 アプリケーションは、さらに、新しいメッセージを取得する、未読のカウントを更新するなど、ビジネス ロジックに従って、アクションを受け取ります。

アプリケーションは、期限が切れる前にサブスクリプションを更新する必要があります。 通知の受信を停止することができますまた。

<!-- Remove this image as confirmed by Michael that it's not correct. 
The following figure describes this notification method.

![Client application is redirected to login from backend server, provides consent, backend server subscribes for notifications, notifications are sent to the client application](images\O365APIs_REST_Notifications.png)
1.  Client application is opened. A request goes to the trusted backend server which has already been given app-only access to Microsoft Azure to get an access token to act on behalf of the client application user.
2.  The backend server subscribes for notifications from Office 365 using the access token.
3.  As changes are made to mail, contacts, and events, Office 365 pushes notifications to the backend server.
4.  The backend server relays the changes to the client application through a notification service.
-->


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


Office 365 のプッシュ通知サービスと API は、コールバック アドレスで Web サービスを提供し、クライアント アプリケーションに通知を配信するのには Webhooks を使用しているクライアントで動作します。 Webhooks は、通常、サード パーティの信頼される側のバックエンド Web サービスで構成されている HTTP-のコールバックです。 Web サービスでは、トリガ イベントが発生する別の動作を呼び出す 1 つのサイト上に Webhooks を構成できます。 

アプリケーションは、メッセージなど、ユーザーの受信トレイ内の特定のリソースの通知にサブスクライブする場合は、サブスクリプション要求に Webhook コールバック URL を指定します。 (受信トレイに新しいメッセージ) のようにトリガーを起動するイベントが発生する、Office 365 の通知サービスは、コールバック URL に、webhook を使用して通知をプッシュします。 アプリケーションは、さらに、新しいメッセージを取得する、未読のカウントを更新するなど、ビジネス ロジックに従って、アクションを受け取ります。

アプリケーションは、期限が切れる前にサブスクリプションを更新する必要があります。 通知の受信を停止することができますまた。

<!-- Remove this image as confirmed by Michael that it's not correct. 
The following figure describes this notification method.

![Client application is redirected to login from backend server, provides consent, backend server subscribes for notifications, notifications are sent to the client application](images\O365APIs_REST_Notifications.png)
1.  Client application is opened. A request goes to the trusted backend server which has already been given app-only access to Microsoft Azure to get an access token to act on behalf of the client application user.
2.  The backend server subscribes for notifications from Office 365 using the access token.
3.  As changes are made to mail, contacts, and events, Office 365 pushes notifications to the backend server.
4.  The backend server relays the changes to the client application through a notification service.
-->


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



## <a name="a-namecompare-streaming-and-push-notificationsa"></a><a name="compare-streaming-and-push-notifications"></a>ストリーミングを比較し、プッシュ通知


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

メール、予定表、CRM アプリケーション、ローカル キャッシュ、対応するクライアントのビュー、または変更時にバックエンド システムを更新するのには通常の通知を使用します。 Outlook では、[ストリーミング](..\api\notify-streaming-rest-operations.md)とプッシュ通知をサポートしています。 現時点では、プッシュ通知で頻繁に使用モバイル アプリケーションは、変更をポーリングするクライアントを必要としませんし、更新できるようクライアントをほぼ瞬時にします。 

ストリーミングの通知と比較すると、プッシュ通知は、クライアントが通知をストリーミング、クライアントと Office 365 のストリーミングの通知サービスとの間の直接接続のみが必要となりますが、通知を取得するために独自の Web サービスを提供する必要があります。 

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

メール、予定表、CRM アプリケーション、ローカル キャッシュ、対応するクライアントのビュー、または変更時にバックエンド システムを更新するのには通常の通知を使用します。 Outlook では、[ストリーミング](..\api\notify-streaming-rest-operations.md)とプッシュ通知をサポートしています。 現時点では、プッシュ通知で頻繁に使用モバイル アプリケーションは、変更をポーリングするクライアントを必要としませんし、更新できるようクライアントをほぼ瞬時にします。 

ストリーミングの通知と比較すると、プッシュ通知は、クライアントが通知をストリーミング、クライアントと Office 365 のストリーミングの通知サービスとの間の直接接続のみが必要となりますが、通知を取得するために独自の Web サービスを提供する必要があります。 

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


## <a name="a-nameuse-the-push-notifications-rest-apia-rest-api-"></a><a name="use-the-push-notifications-rest-api"></a>プッシュ通知の REST-API を使用します。

### <a name="a-nameauthenticationa"></a><a name="authentication"></a>認証

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

購読、クエリを更新、サブスクリプションを削除に通知しリソースの種類に適したスコープを指定します。

_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _https://Outlook.Office.com/Tasks.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_


他の[REST-API の Outlook](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)、Outlook をプッシュ通知 API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 プッシュ通知 API では、特定の操作を続行するには、この点に留意してください。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

購読、クエリを更新、サブスクリプションを削除に通知しリソースの種類に適したスコープを指定します。

_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _https://Outlook.Office.com/Tasks.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_

他の[REST-API の Outlook](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)、Outlook をプッシュ通知 API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 プッシュ通知 API では、特定の操作を続行するには、この点に留意してください。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


###<a name="a-nameversion-of-apiaapi-"></a><a name="version-of-api"></a>API のバージョン


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

この API は、一般的な可用性 (GA) の状態に、プレビューから昇格されています。 Outlook の REST-API 2.0 のバージョン とベータ版のバージョンでサポートされています。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

この API は、一般的な可用性 (GA) の状態に、プレビューから昇格されています。 Outlook の REST-API 2.0 のバージョン とベータ版のバージョンでサポートされています。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


###<a name="a-nametarget-usera-"></a><a name="target-user"></a>ターゲット ユーザー


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

プッシュ通知 API 要求は、現在のユーザーに代わって実行されます。 

Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

プッシュ通知 API 要求は、現在のユーザーに代わって実行されます。 

Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。

****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="NotificationOperations"> </a>
##プッシュ通知の操作<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

[通知を購読する](#SubscribeOperation) | [更新サブスクリプション](#RenewSub) | [のサブスクリプションを削除します。 ](#DeleteSub)

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

[通知を購読する](#SubscribeOperation) | [更新サブスクリプション](#RenewSub) | [のサブスクリプションを削除します。 ](#DeleteSub)

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->









<a name="SubscribeOperation"> </a>
###メール、予定表、連絡先、またはタスクの変更を購読します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**サブスクリプション プロセス** 

サブスクリプション プロセスは、次のようになります。 

1. クライアント アプリケーションは、特定のリソースのサブスクリプション要求 (POST) を行います。 その他のプロパティの間での通知の URL が含まれています。

2. Outlook の通知サービスは、リスナー サービスに通知 URL を検証しようとします。 検証要求の検証トークンが含まれています。

3. リスナー サービスは、URL を正常に検証をしている場合、正常な応答を次のように 5 秒以内返します。

   - \Plain の応答ヘッダーのコンテンツ タイプを設定します。 
   - 応答の本文の検証と同じトークンが含まれます。 
   - HTTP-200 の応答コードを返します。 リスナーは、その後の検証のトークンを破棄できます。 

4. URL の検証の結果によっては、Outlook の通知サービスは、クライアント アプリケーションへの応答を送信します。

   - URL の検証が成功した場合、サービスは固有のサブスクリプション ID を使用して、サブスクリプションを作成し、クライアントへの応答を送信します。 
   - URL の検証が正常に終了しない場合、サービスはエラー コードとその他の詳細のエラー応答を送信します。

5. 正常な応答を受信するには、時に、クライアント アプリケーションは、このサブスクリプションでの今後の通知に関連付けるためのサブスクリプション-ID を格納します。 



**サブスクリプション要求**

Office 365 または Outlook.com では、メール、予定表イベント、連絡先、またはタスクを変更するときに通知を受信するリスナー サービスをサブスクライブします。 の通知を取得を開始するクライアントの最初のステップです。 これは、リソース (エンティティまたはエンティティのコレクション) 


```no-highlight
POST https://outlook.office.com/api/beta/me/subscriptions
```

要求の本文では、プッシュ サブスクリプション要求の次のプロパティを指定します。 **ClientState**を除くすべてのプロパティが必要です。 詳細については、 [通知のエンティティ](#NotificationEntities)を参照してください。 

- OData.Type - は、 `"@odata.type":"#Microsoft.OutlookServices.PushSubscription"`。 **PushSubscription**エンティティでは、 **NotificationURL**を定義します。
- **ChangeType** がそのリソースを監視するイベントの種類を指定します。 サポートされている種類の[ChangeType](#ChangeType)を参照してください。 
- **ClientState** - 同じ名前の **ClientState**値でヘッダーを持つ各通知を送信することを示す省略可能なプロパティです。 これには、リスナーの各通知の正当性を確認することができます。
- **NotificationURL** -への通知の送信先を指定します。 この URL は、通常、クライアントによって実装されている Web サービスを表します。
- **リソース** を監視し、通知を受信するリソースを指定します。 次のいずれかを指定できます。

  - 通常のフォルダーまたはメッセージ、イベント、連絡先、またはタスクのフォルダーを検索します。 例。 
  
    `https://outlook.office.com/api/beta/me/mailfolders('inbox')/messages`
  
    `https://outlook.office.com/api/beta/me/taskfolders('{folder_id}')/tasks`
   
  - または、メッセージ、イベントのトップ レベルのエンティティのコレクションは、取引先担当者、またはタスクを次のようにします。
  
    `https://outlook.office.com/api/beta/me/messages`
  
    `https://outlook.office.com/api/beta/me/events`
  
    `https://outlook.office.com/api/beta/me/contacts`
  
    `https://outlook.office.com/api/beta/me/tasks`



**要求のサンプル**

次の例では、新しいイベントをサブスクライブする方法を示します。 

```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1
Content-Type: application/json

{
   "@odata.type":"#Microsoft.OutlookServices.PushSubscription",
   "Resource": "https://outlook.office.com/api/beta/me/events",
   "NotificationURL": "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",  
   "ChangeType": "Created",
   "ClientState": "c75831bd-fad3-4191-9a66-280a48528679"
}
```


**通知の条件を絞り込む**

詳細を使用して通知するための条件を指定できます、`$filter`のパラメーターのクエリを実行します。 

次の使用例は、 [下書き] フォルダーに作成される 1 つまたは複数添付ファイル、および重要性の中に含まれるメッセージの通知を要求 `High`。 

```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1 
Content-Type: application/json 
 
{ 
  @odata.type:"#Microsoft.OutlookServices.PushSubscription", 
  Resource: "https://outlook.office.com/api/beta/me/mailfolders('Drafts')/messages?$filter=HasAttachments%20eq%20true%20AND%20Importance%20eq%20%27High%27", 
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient", 
  ChangeType: "Created", 
  ClientState: "Has attachments and high importance" 
} 
```


次の例では、作成されている終日のイベントの通知を要求します。 

```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1 
Content-Type: application/json 
 
{ 
  @odata.type:"#Microsoft.OutlookServices.PushSubscription", 
  Resource: "https://outlook.office.com/api/beta/me/events?$filter=IsAllDay%20eq%20true", 
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient", 
  ChangeType: "Created", 
  ClientState: "Notifications for events that IsAllDay." 
} 
```


次の使用例は、Contoso 社の中の会社で作成されている連絡先の通知を要求します。 

```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1 
Content-Type: application/json 
 
{ 
  @odata.type:"#Microsoft.OutlookServices.PushSubscription", 
  Resource: "https://outlook.office.com/api/beta/me/contacts?$filter=CompanyName%20eq%20%27Contoso%27", 
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient", 
  ChangeType: "Created", 
  ClientState: "Contacts in Contoso." 
} 
```

1 つの一般的なアプリケーション`$filter`は、指定されたリソースの特定のプロパティの変更の通知を取得します。 使用することができますたとえば、 `$filter` ( **IsRead**プロパティが False) 、フォルダー内の未読メ ッ セージを購読し、すべての種類変更にはが含まれます。

- メッセージに追加するか、フォルダー内の未読のマークをトリガー、`Created`通知します。 
- メッセージを読んでいたり、フォルダーに読み取りをトリガーとしてマークして、`Deleted`通知します。
- **IsRead**フォルダー内のメッセージの以外の任意のプロパティへの変更をトリガー、`Updated`通知します。

次のように、このようなサブスクリプションを作成することができます。

```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1
Content-Type: application/json

{
  @odata.type:"#Microsoft.OutlookServices.PushSubscription",
  Resource: "https://outlook.office.com/api/beta/me/mailfolders('folder_id')/messages$filter=IsRead%20eq%20false",
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",
  ChangeType: "Created,Deleted,Updated",
  ClientState: "Message unread"
}
```


使用しない場合、`$filter`としてサブスクリプションを作成するとき。 (下)

- フォルダーにメッセージを追加することになる、`Created`通知します。
- フォルダー内のメッセージを読み取り、メッセージを開封済みにマークを付けるまたはいずれかを変更する他のフォルダー内のメッセージのメッセージ ・ プロパティになるでしょう、`Updated`通知します。 
- メッセージを削除することになる、`Delete`通知します。

```
POST https://outlook.office.com/api/beta/me/subscriptions HTTP/1.1
Content-Type: application/json

{
  @odata.type:"#Microsoft.OutlookServices.PushSubscription",
  Resource: "https://outlook.office.com/api/beta/me/mailfolders('folder_id')/messages,
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",
  ChangeType: "Created,Deleted,Updated",
  ClientState: "Message unread"
}
```

**評価の要求**

検証要求がサブスクリプション要求に、クライアント アプリケーションを指定する NotificationURL を検証しようとするとします。
```no-highlight
POST https://{notificationUrl}?validationToken={token}
```
Outlook のサービスでは、 {NotificationUrl} をサブスクリプション要求に、NotificationURL を指定し、検証のトークンとして文字列 {のトークン} を定義します。 クライアント アプリケーションには、サブスクリプション要求のいずれかが含まれている場合、Outlook のサービスにはからも**ClientState**ヘッダーが含まれます。


**サブスクリプション応答**

サブスクリプションの応答には、要求、および次の追加プロパティのプロパティが含まれています。
- **ID**の今後の通知と一致するようにクライアント アプリケーションを保存する必要があります、一意なサブスクリプション-ID です。
- **ChangeType**の要求、応答内で指定した値とは別**喪失**、追加の通知の種類含まれています。 
- **SubscriptionExpirationDateTime** - 日付と時刻をサブスクリプションの有効期限が切れます。 要求は、期限を指定していないか、応答が時間から 3 日である最大値を設定する要求は、3 日間よりも長い有効期限を指定する場合は、要求が送信されます。
- 他の OData 関連のプロパティです。


**応答データのサンプル**

この応答は、リスナー サービスで新しいイベントの通知を期待して、変更が失われているを示します。 変更が失われる場合は、クライアントがそれらをキャプチャするようにサービスと同期する必要があります。

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Subscriptions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.PushSubscription",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Subscriptions('Mjk3QNERDQQ==')",
    "Id": "Mjk3QNERDQQ==",
    "Resource": "https://outlook.office.com/api/beta/me/events",
    "ChangeType": "Created, Missed",
    "ClientState": "c75831bd-fad3-4191-9a66-280a48528679",
    "NotificationURL": "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",
    "SubscriptionExpirationDateTime": "2015-04-23T22:46:13.8805047Z"
}
```


**サブスクリプションのクエリ**サインインしているユーザーの既存のサブスクリプションのいずれかに関する詳細情報を検索するには、そのサブスクリプションの ID を指定します。 たとえば、最後の例で作成したサブスクリプションのクエリを実行するのには。
```
GET https://outlook.office.com/api/beta/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Subscriptions('Mjk3QNERDQQ==')
```
成功した場合、応答になる最後のサンプルの応答のデータと同じ点を除いて、ClientState を除外するには  
クライアント アプリケーションは、潜在的なセキュリティ上のリスクを避けるために指定しています。 


**通知**

各通知には、その種類に関係なく、次のプロパティが含まれています。
- **ClientState**ヘッダーに、クライアントがサブスクリプション要求の**ClientState**プロパティを指定した場合にのみに存在します。 通知の真偽を確認するのには、リスナーによって使用されます。
- クライアント アプリケーションにこの通知が所属しているサブスクリプションの**サブスクリプション-Id**を識別します。
- **SubscriptionExpirationDateTime** - サブスクリプションの有効期限日時。 
- **シーケンス番号**の通知がない場合に特定のクライアント アプリケーションのために、通知のシーケンス内の数値です。
- **ChangeType**のクライアント アプリケーションが (メールを受信したときに**作成された**イベントの種類など、メッセージを読み取るときの**更新**イベントの型) に通知する必要があるイベントの種類。 
- **リソース**に (たとえば、変更されたメッセージまたはイベントへの URL) は、監視する特定のリソース項目の URL です。 
- **ResourceData** - (受信、読み取り、メッセージを削除するなど) のリソースの変更に関連する通知には、この変更された項目のリソース-ID を格納する追加のプロパティがあります。 ビジネス ロジックに従って、この項目を処理するためにクライアントがこのリソース ID を使用できます (この項目を取得、そのフォルダーの同期など) 。

注: エンティティの[通知](#NotificationResource)では、Id プロパティは使用されません。

<a name="ChangeNotificationPayload"> </a>

**変更通知ペイロード**

次の例では、ユーザーが、新しいイベントを受け取ると通知サービス通知を送信「作成」に設定 ChangeType とします。 通知のヘッダーには、初期サブスクリプション要求で指定されている ClientState が含まれます。 受信イベントの通知には、次のようなペイロードがあります。

```no-highlight
{
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.Notification",
            "Id": null,
            "SubscriptionId": "Mjk3QNERDQQ==",
            "SubscriptionExpirationDateTime": "2015-04-23T22:46:13.8805047Z",
            "SequenceNumber": 1,
            "ChangeType": "Created",
            "Resource" : "https://outlook.office.com/api/beta/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Events('AAMkADNkNmAA=')",
            "ResourceData": {
                "@odata.type": "#Microsoft.OutlookServices.Event",
                "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Events('AAMkADNkNmAA=')",
                "Id": "AAMkADNkNmAA="
            }
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


**サブスクリプション プロセス** 

サブスクリプション プロセスは、次のようになります。 

1. クライアント アプリケーションは、特定のリソースのサブスクリプション要求 (POST) を行います。 その他のプロパティの間での通知の URL が含まれています。

2. Outlook の通知サービスは、リスナー サービスに通知 URL を検証しようとします。 検証要求の検証トークンが含まれています。

3. リスナー サービスは、URL を正常に検証をしている場合、正常な応答を次のように 5 秒以内返します。

   - \Plain の応答ヘッダーのコンテンツ タイプを設定します。 
   - 応答の本文の検証と同じトークンが含まれます。 
   - HTTP-200 の応答コードを返します。 リスナーは、その後の検証のトークンを破棄できます。 

4. URL の検証の結果によっては、Outlook の通知サービスは、クライアント アプリケーションへの応答を送信します。

   - URL の検証が成功した場合、サービスは固有のサブスクリプション ID を使用して、サブスクリプションを作成し、クライアントへの応答を送信します。 
   - URL の検証が正常に終了しない場合、サービスはエラー コードとその他の詳細のエラー応答を送信します。

5. 正常な応答を受信するには、時に、クライアント アプリケーションは、このサブスクリプションでの今後の通知に関連付けるためのサブスクリプション-ID を格納します。 



**サブスクリプション要求**

Office 365 または Outlook.com では、メール、予定表イベント、連絡先、またはタスクを変更するときに通知を受信するリスナー サービスをサブスクライブします。 の通知を取得を開始するクライアントの最初のステップです。 これは、リソース (エンティティまたはエンティティのコレクション) 


```no-highlight
POST https://outlook.office.com/api/v2.0/me/subscriptions
```

要求の本文では、プッシュ サブスクリプション要求の次のプロパティを指定します。 **ClientState**を除くすべてのプロパティが必要です。 詳細については、 [通知のエンティティ](#NotificationEntities)を参照してください。 

- OData.Type - は、 `"@odata.type":"#Microsoft.OutlookServices.PushSubscription"`。 **PushSubscription**エンティティでは、 **NotificationURL**を定義します。
- **ChangeType** がそのリソースを監視するイベントの種類を指定します。 サポートされている種類の[ChangeType](#ChangeType)を参照してください。 
- **ClientState** - 同じ名前の **ClientState**値でヘッダーを持つ各通知を送信することを示す省略可能なプロパティです。 これには、リスナーの各通知の正当性を確認することができます。
- **NotificationURL** -への通知の送信先を指定します。 この URL は、通常、クライアントによって実装されている Web サービスを表します。
- **リソース** を監視し、通知を受信するリソースを指定します。 次のいずれかを指定できます。

  - 通常のフォルダーまたはメッセージ、イベント、連絡先、またはタスクのフォルダーを検索します。 例。 
  
    `https://outlook.office.com/api/v2.0/me/mailfolders('inbox')/messages`
  
    `https://outlook.office.com/api/v2.0/me/taskfolders('{folder_id}')/tasks`
   
  - または、メッセージ、イベントのトップ レベルのエンティティのコレクションは、取引先担当者、またはタスクを次のようにします。
  
    `https://outlook.office.com/api/v2.0/me/messages`
  
    `https://outlook.office.com/api/v2.0/me/events`
  
    `https://outlook.office.com/api/v2.0/me/contacts`
  
    `https://outlook.office.com/api/v2.0/me/tasks`


**要求のサンプル**

次の例では、新しいイベントをサブスクライブする方法を示します。 

```
POST https://outlook.office.com/api/v2.0/me/subscriptions HTTP/1.1
Content-Type: application/json

{
   "@odata.type":"#Microsoft.OutlookServices.PushSubscription",
   "Resource": "https://outlook.office.com/api/v2.0/me/events",
   "NotificationURL": "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",  
   "ChangeType": "Created",
   "ClientState": "c75831bd-fad3-4191-9a66-280a48528679"
}

```


**通知の条件を絞り込む** 

詳細を使用して通知するための条件を指定できます、`$filter`のパラメーターのクエリを実行します。 

次の使用例は、 [下書き] フォルダーに作成される 1 つまたは複数添付ファイル、および重要性の中に含まれるメッセージの通知を要求 `High`。 

```
POST https://outlook.office.com/api/v2.0/me/subscriptions HTTP/1.1 
Content-Type: application/json 
 
{ 
  @odata.type:"#Microsoft.OutlookServices.PushSubscription", 
  Resource: "https://outlook.office.com/api/v2.0/me/mailfolders('Drafts')/messages?$filter=HasAttachments%20eq%20true%20AND%20Importance%20eq%20%27High%27", 
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient", 
  ChangeType: "Created", 
  ClientState: "Has attachments and high importance" 
} 
```


次の例では、作成されている終日のイベントの通知を要求します。 

```
POST https://outlook.office.com/api/v2.0/me/subscriptions HTTP/1.1 
Content-Type: application/json 
 
{ 
  @odata.type:"#Microsoft.OutlookServices.PushSubscription", 
  Resource: "https://outlook.office.com/api/v2.0/me/events?$filter=IsAllDay%20eq%20true", 
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient", 
  ChangeType: "Created", 
  ClientState: "Notifications for events that IsAllDay." 
} 
```


次の使用例は、Contoso 社の中の会社で作成されている連絡先の通知を要求します。 

```
POST https://outlook.office.com/api/v2.0/me/subscriptions HTTP/1.1 
Content-Type: application/json 
 
{ 
  @odata.type:"#Microsoft.OutlookServices.PushSubscription", 
  Resource: "https://outlook.office.com/api/v2.0/me/contacts?$filter=CompanyName%20eq%20%27Contoso%27", 
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient", 
  ChangeType: "Created", 
  ClientState: "Contacts in Contoso." 
} 
```

1 つの一般的なアプリケーション`$filter`は、指定されたリソースの特定のプロパティの変更の通知を取得します。 使用することができますたとえば、 `$filter` ( **IsRead**プロパティが False) 、フォルダー内の未読メ ッ セージを購読し、すべての種類変更にはが含まれます。

- メッセージに追加するか、フォルダー内の未読のマークをトリガー、`Created`通知します。 
- メッセージを読んでいたり、フォルダーに読み取りをトリガーとしてマークして、`Deleted`通知します。
- **IsRead**フォルダー内のメッセージの以外の任意のプロパティへの変更をトリガー、`Updated`通知します。

次のように、このようなサブスクリプションを作成することができます。

```
POST https://outlook.office.com/api/v2.0/me/subscriptions HTTP/1.1
Content-Type: application/json

{
  @odata.type:"#Microsoft.OutlookServices.PushSubscription",
  Resource: "https://outlook.office.com/api/v2.0/me/mailfolders('folder_id')/messages$filter=IsRead%20eq%20false",
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",
  ChangeType: "Created,Deleted,Updated",
  ClientState: "Message unread"
}
```


使用しない場合、`$filter`としてサブスクリプションを作成するとき。 (下)

- フォルダーにメッセージを追加することになる、`Created`通知します。
- フォルダー内のメッセージを読み取り、メッセージを開封済みにマークを付けるまたはいずれかを変更するフォルダー内のメッセージの他の財産になるでしょう、`Updated`通知します。 
- メッセージを削除することになる、`Delete`通知します。

```
POST https://outlook.office.com/api/v2.0/me/subscriptions HTTP/1.1
Content-Type: application/json

{
  @odata.type:"#Microsoft.OutlookServices.PushSubscription",
  Resource: "https://outlook.office.com/api/v2.0/me/mailfolders('folder_id')/messages,
  NotificationURL: "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",
  ChangeType: "Created,Deleted,Updated",
  ClientState: "Message unread"
}
```


**評価の要求**

検証要求がサブスクリプション要求に、クライアント アプリケーションを指定する NotificationURL を検証しようとするとします。
```no-highlight
POST https://{notificationUrl}?validationToken={token}
```
Outlook のサービスでは、 {NotificationUrl} をサブスクリプション要求に、NotificationURL を指定し、検証のトークンとして文字列 {のトークン} を定義します。 クライアント アプリケーションには、サブスクリプション要求のいずれかが含まれている場合、Outlook のサービスにはからも**ClientState**ヘッダーが含まれます。


**サブスクリプション応答**

サブスクリプションの応答には、要求、および次の追加プロパティのプロパティが含まれています。
- **ID**の今後の通知と一致するようにクライアント アプリケーションを保存する必要があります、一意なサブスクリプション-ID です。
- **ChangeType**の要求、応答内で指定した値とは別**喪失**、追加の通知の種類含まれています。 
- **SubscriptionExpirationDateTime** - 日付と時刻をサブスクリプションの有効期限が切れます。 要求は、期限を指定していないか、応答が時間から 3 日である最大値を設定する要求は、3 日間よりも長い有効期限を指定する場合は、要求が送信されます。
- 他の OData 関連のプロパティです。


**応答データのサンプル**

この応答は、リスナー サービスで新しいイベントの通知を期待して、変更が失われているを示します。 変更が失われる場合は、クライアントがそれらをキャプチャするようにサービスと同期する必要があります。

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Subscriptions/$entity",
    "@odata.type": "#Microsoft.OutlookServices.PushSubscription",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Subscriptions('Mjk3QNERDQQ==')",
    "Id": "Mjk3QNERDQQ==",
    "Resource": "https://outlook.office.com/api/v2.0/me/events",
    "ChangeType": "Created, Missed",
    "ClientState": "c75831bd-fad3-4191-9a66-280a48528679",
    "NotificationURL": "https://mywebhook.azurewebsites.net/api/send/myNotifyClient",
    "SubscriptionExpirationDateTime": "2015-04-23T22:46:13.8805047Z"
}
```


**サブスクリプションのクエリ**サインインしているユーザーの既存のサブスクリプションのいずれかに関する詳細情報を検索するには、そのサブスクリプションの ID を指定します。 たとえば、最後の例で作成したサブスクリプションのクエリを実行するのには。
```
GET https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Subscriptions('Mjk3QNERDQQ==')
```
成功した場合、応答になる最後のサンプルの応答のデータと同じ点を除いて、ClientState を除外するには  
クライアント アプリケーションは、潜在的なセキュリティ上のリスクを避けるために指定しています。 


**通知**

各通知には、その種類に関係なく、次のプロパティが含まれています。
- **ClientState**ヘッダーに、クライアントがサブスクリプション要求の**ClientState**プロパティを指定した場合にのみに存在します。 通知の真偽を確認するのには、リスナーによって使用されます。
- クライアント アプリケーションにこの通知が所属しているサブスクリプションの**サブスクリプション Id**を識別します。
- **SubscriptionExpirationDateTime** - サブスクリプションの有効期限日時。 
- **シーケンス番号**の通知がない場合に特定のクライアント アプリケーションのために、通知のシーケンス内の数値です。
- **ChangeType**のクライアント アプリケーションが (メールを受信したときに**作成された**イベントの種類など、メッセージを読み取るときの**更新**イベントの型) に通知する必要があるイベントの種類。 
- **リソース**に (たとえば、変更されたメッセージまたはイベントへの URL) は、監視する特定のリソース項目の URL です。 
- **ResourceData** - (受信、読み取り、メッセージを削除するなど) のリソースの変更に関連する通知には、この変更された項目のリソース-ID を格納する追加のプロパティがあります。 ビジネス ロジックに従って、この項目を処理するためにクライアントがこのリソース ID を使用できます (この項目を取得、そのフォルダーの同期など) 。

注: エンティティの[通知](#NotificationResource)では、Id プロパティは使用されません。

<a name="ChangeNotificationPayload"> </a>

**変更通知ペイロード**

次の例では、ユーザーが、新しいイベントを受け取ると通知サービス通知を送信「作成」に設定 ChangeType とします。 通知のヘッダーには、初期サブスクリプション要求で指定されている ClientState が含まれます。 受信イベントの通知には、次のようなペイロードがあります。

```no-highlight
{
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.Notification",
            "Id": null,
            "SubscriptionId": "Mjk3QNERDQQ==",
            "SubscriptionExpirationDateTime": "2015-04-23T22:46:13.8805047Z",
            "SequenceNumber": 1,
            "ChangeType": "Created",
            "Resource" : "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Events('AAMkADNkNmAA=')",
            "ResourceData": {
                "@odata.type": "#Microsoft.OutlookServices.Event",
                "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/Events('AAMkADNkNmAA=')",
                "Id": "AAMkADNkNmAA="
            }
        }
    ]
}
```



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->









<a name="RenewSub"> </a>

### <a name="a-namerenew-subscriptiona"></a><a name="renew-subscription"></a>サブスクリプションを更新します。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

更新の要求の時間から最大 3 日間のサブスクリプションを更新します。  

```no-highlight
PATCH https://outlook.office.com/api/beta/me/subscriptions/{subscriptionId}
```

既定のサブスクリプションの長さは、3 日間です。 ペイロードに更新要求を送信することができ、3 日間でサブスクリプションを拡張します。


**要求のサンプル**

```
PATCH https://outlook.office.com/api/beta/me/subscriptions/Mjk3QNERDQQ==

{
   @odata.type:"#Microsoft.OutlookServices.PushSubscription",
   "SubscriptionExpirationDateTime": "2015-05-28T17:17:45.9028722Z"
}

```

正常な応答は HTTP 200 の応答コードが表示されます。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


更新の要求の時間から最大 3 日間のサブスクリプションを更新します。  

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/subscriptions/{subscriptionId}
```

既定のサブスクリプションの長さは、3 日間です。 ペイロードに更新要求を送信することができ、3 日間でサブスクリプションを拡張します。


**要求のサンプル**

```
PATCH https://outlook.office.com/api/v2.0/me/subscriptions/Mjk3QNERDQQ==

{
   @odata.type:"#Microsoft.OutlookServices.PushSubscription",
   "SubscriptionExpirationDateTime": "2015-05-28T17:17:45.9028722Z"
}

```

正常な応答は HTTP 200 の応答コードが表示されます。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->







 

<a name="DeleteSub"></a>

### <a name="a-namedelete-subscriptiona"></a><a name="delete-subscription"></a>サブスクリプションを削除します。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

サブスクリプション ID を指定することでサブスクリプションを削除します。

```no-highlight
DELETE https://outlook.office.com/api/beta/me/subscriptions('{subscriptionId}')
```

**要求のサンプル**

```
Delete https://outlook.office.com/api/beta/me/subscriptions('Mjk3QNERDQQ==')
```

によって正常な応答が示されている、`HTTP 204 No Content`応答コード。  


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


サブスクリプション ID を指定することでサブスクリプションを削除します。

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/subscriptions('{subscriptionId}')
```

**要求のサンプル**

```
Delete https://outlook.office.com/api/v2.0/me/subscriptions('Mjk3QNERDQQ==')
```

によって正常な応答が示されている、`HTTP 204 No Content`応答コード。  


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->









<a name="NotificationEntities"> </a>
##エンティティを通知し、列挙型<a name="SubscriptionResource"> </a>
###サブスクリプション<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


ベースのサブスクリプションを表します。 これは、抽象基本クラスです。

基本型:**エンティティ**

|**プロパティ**|**タイプ**|**説明**|**書き込み可能でしょうか。**|**フィルター処理可能でしょうか。**|
|:-----|:-----|:-----|:-----|:-----|
| リソース | string | 変更の監視対象リソースを指定します。 | ある | n/v |
| ChangeType | ChangeType | 通知を発生させるイベントの種類を示します。 サポートされている種類の[ChangeType](#ChangeType)を参照してください。 | ある  | n/v |


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


ベースのサブスクリプションを表します。 これは、抽象基本クラスです。

基本型:**エンティティ**

|**プロパティ**|**タイプ**|**説明**|**書き込み可能でしょうか。**|**フィルター処理可能でしょうか。**|
|:-----|:-----|:-----|:-----|:-----|
| リソース | string | 変更の監視対象リソースを指定します。 | ある | n/v |
| ChangeType | ChangeType | 通知を発生させるイベントの種類を示します。 サポートされている種類の[ChangeType](#ChangeType)を参照してください。 | ある  | n/v |
 


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->







<a name="NotificationResource"> </a>
###通知<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

クライアントに送信される通知を表します。 場合は、プッシュ通知は、クライアントによって指定されたリスナー サービスに通知が送信されます。

基本型:**エンティティ**

|**プロパティ**|**タイプ**|**説明**|**書き込み可能でしょうか。**|**フィルター処理可能でしょうか。**|
|:-----|:-----|:-----|:-----|:-----|
| サブスクリプション-Id | string | サブスクリプションの一意の識別子です。 | 不可 | 不可 |
| SubscriptionExpirationDateTime | Edm.DateTimeOffset | 通知サブスクリプションの有効期限が切れる日時を指定します。 時刻は utc です。 | ある | n/v |
| SequenceNumber | Int32 | 変更通知のシーケンスの値を示します。 | 非表示  | 該当なし |
| ChangeType | ChangeType | 通知を発生させたイベントの種類を示します。 列挙値: 作成 = 1、更新 = 2、削除済み = 4、喪失 = 16。 喪失の通知は、通知サービスは、要求された通知を送信できない場合に発生します。 | 非表示 | 該当なし |
| リソース | string | 変更の監視対象リソース項目を指定します。 | ある | n/v |
| ResourceData | エンティティ | 変更されたエンティティを識別します。 これは、ナビゲーション プロパティです。 | 非表示 | 該当なし |



[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


クライアントに送信される通知を表します。 場合は、プッシュ通知は、クライアントによって指定されたリスナー サービスに通知が送信されます。

基本型:**エンティティ**

|**プロパティ**|**タイプ**|**説明**|**書き込み可能でしょうか。**|**フィルター処理可能でしょうか。**|
|:-----|:-----|:-----|:-----|:-----|
| サブスクリプション-Id | string | サブスクリプションの一意の識別子です。 | 不可 | 不可 |
| SubscriptionExpirationDateTime | Edm.DateTimeOffset | 通知サブスクリプションの有効期限が切れる日時を指定します。 時刻は utc です。 | ある | n/v |
| SequenceNumber | Int32 | 変更通知のシーケンスの値を示します。 | 非表示  | 該当なし |
| ChangeType | ChangeType | 通知を発生させたイベントの種類を示します。 列挙値: 作成 = 1、更新 = 2、削除済み = 4、喪失 = 16。 喪失の通知は、通知サービスは、要求された通知を送信できない場合に発生します。 | 非表示 | 該当なし |
| リソース | string | 変更の監視対象リソース項目を指定します。 | ある | n/v |
| ResourceData | エンティティ | 変更されたエンティティを識別します。 これは、ナビゲーション プロパティです。 | 非表示 | 該当なし |



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->









<a name="PushSubscription"> </a>
###PushSubscription<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

プッシュ通知メカニズムを使用するサブスクリプションを表します。

基本型:[サブスクリプション](#SubscriptionResource)

|**プロパティ**|**タイプ**|**説明**|**書き込み可能でしょうか。**|**フィルター処理可能でしょうか。**|
|:-----|:-----|:-----|:-----|:-----|
| NotificationURL | string | プッシュ通知を受信するアプリケーションの URL です。  | ある | n/v |
| SubscriptionExpirationDateTime | Edm.DateTimeOffset | 通知サブスクリプションの有効期限が切れる日時を指定します。 時刻は utc です。 | ある | n/v |
| ClientState | string | 通知ごとにサービスによって送信された ClientState ヘッダーの値を指定します。 最大の長さは、255 文字です。 クライアントは、その通知が各通知を受信した ClientState ヘッダーの値を持つ ClientState プロパティで設定された値を比較することによってサービスから送られたを確認できます。 | ○ | 不可 |


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


プッシュ通知メカニズムを使用するサブスクリプションを表します。

基本型:[サブスクリプション](#SubscriptionResource)

|**プロパティ**|**タイプ**|**説明**|**書き込み可能でしょうか。**|**フィルター処理可能でしょうか。**|
|:-----|:-----|:-----|:-----|:-----|
| NotificationURL | string | プッシュ通知を受信するアプリケーションの URL です。  | ある | n/v |
| SubscriptionExpirationDateTime | Edm.DateTimeOffset | 通知サブスクリプションの有効期限が切れる日時を指定します。 時刻は utc です。 | ある | n/v |
| ClientState | string | 通知ごとにサービスによって送信された ClientState ヘッダーの値を指定します。 最大の長さは、255 文字です。 クライアントは、その通知が各通知を受信した ClientState ヘッダーの値を持つ ClientState プロパティで設定された値を比較することによってサービスから送られたを確認できます。 | ○ | 不可 |


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<a "name"="ChangeType"></a>
###ChangeType<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

発生するイベントの種類を指定する列挙体には、通知を発生できるリソースがサポートされています。

サポートされている値。

- 受信確認
- 作成日時
- 削除された
- 失われています。 Eine`Missed`通知は、通知サービスは、要求された通知を送信できない場合に発生します。
- 更新

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

発生するイベントの種類を指定する列挙体には、通知を発生できるリソースがサポートされています。

サポートされている値。

- 受信確認
- 作成日時
- 削除された
- 失われています。 Eine`Missed`通知は、通知サービスは、要求された通知を送信できない場合に発生します。
- 更新

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<a name="NextSteps"> </a>
##次のステップ<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

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

- [REST-API のタスク](..\api\task-rest-operations.md) (プレビュー)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


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

- [メール、予定表、連絡先、タスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]



