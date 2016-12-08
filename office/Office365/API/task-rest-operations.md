<a name="-ms-toctitle-outlook-api-outlook-api-rest-api-outlook-outlookcom-ms-contentid-6c3b5d47-656c-4a72-8427-c252dc1406db-mstopic-msdate-api-2016-6-28-"></a><<<<<<< ヘッド ms です。 TocTitle: Outlook タスクの残りの部分の API リファレンス (プレビュー) タイトル: Outlook タスクの残りの部分の API リファレンス (プレビュー) 説明: REST-API の参照を作成、取得、更新、および Outlook と Outlook.com でタスクを削除します。 MS-です。 ContentId: 6c3b5d47-656c-4a72-8427-c252dc1406db ms.topic: ms.date を参照 (API): 2016 年 6 月 28 日 ===
---
<a name="ms-toctitle-outlook-api-outlook-api-rest-api-outlook-outlookcom-ms-contentid-6c3b5d47-656c-4a72-8427-c252dc1406db-msdate-2016-9-19-"></a>MS-です。 TOCTitle: Outlook タスクの残りの部分の API リファレンス タイトル: Outlook タスクの残りの部分の API リファレンスの説明: REST-API の参照を作成、取得、更新、および Outlook と Outlook.com でタスクを削除します。 MS-です。 ContentId: 6c3b5d47-656c-4a72-8427-c252dc1406db ms.date: 2016 年 9 月 19 日
---
>>>>>>> ステージング

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="a-nameoutlook-task-rest-api-referenceaoutlook-api-"></a><a name="outlook-task-rest-api-reference"></a>Outlook のタスクの残りの部分の API リファレンス

[!INCLUDE [Add the Outlook REST API filters--v2 default v1 disabled](../includes/controls/addOutlookversion_v2default_v1disabled.html)]

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

 _**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

<p class="previewnote">このドキュメントでは、プレビュー バージョンの Outlook タスクの REST API について説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 可能な場合、バージョン 2.0 は現在推奨されるバージョンです。</p>

Outlook タスクの REST-API では、作成、読み取り、同期、更新、および Office 365 で、Azure Active Directory によってセキュリティで保護されているユーザーのタスクを削除することができます。 ユーザーのアカウントは、Office 365 または Microsoft アカウント (Hotmail.com、Live.com、MSN.com、Outlook.com、Passport.com) に配置できます。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

**API のベータ版では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_


Outlook タスクの REST-API では、作成、読み取り、同期、更新、および Office 365 で、Azure Active Directory によってセキュリティで保護されているユーザーのタスクを削除することができます。 ユーザーのアカウントは、Office 365 または Microsoft アカウント (Hotmail.com、Live.com、MSN.com、Outlook.com、Passport.com) に配置できます。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

**API のバージョン 2.0 では関係ないですか?** 右上のコントロールを使用し、使用バージョンを選択します。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


## <a name="a-nameoverviewa"></a><a name="overview"></a>概要

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


Outlook の[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)を使用するには、作業項目を追跡します。 開始日を期限に注意して、または実際の終了日、進行状況や状態、またはかどうか定期的な通知が必要です。 

タスクは、[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)の順に編成された[タスク フォルダー](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)で構成されます。 各メールボックスには既定の作業フォルダー (**名前**プロパティを使用して`Tasks`) と既定のタスク グループ (**Namen**プロパティは、 `My Tasks`) 。 

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Outlook の[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)を使用するには、作業項目を追跡します。 開始日を期限に注意して、または実際の終了日、進行状況や状態、またはかどうか定期的な通知が必要です。 

タスクは、[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)の順に編成された[タスク フォルダー](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)で構成されます。 各メールボックスには既定の作業フォルダー (**名前**プロパティを使用して`Tasks`) と既定のタスク グループ (**Name**プロパティは、 `My Tasks`) 。 

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


## <a name="a-nameusing-the-task-rest-apia-rest-api-"></a><a name="using-the-task-rest-api"></a>タスクの REST-API を使用してください。

###<a name="a-nameauthenticationa"></a><a name="authentication"></a>認証

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

他の[Outlook の他の API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)タスクの残りの部分 api のすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 タスクの REST-API では、特定の操作を続行するには、この点に留意してください。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

他の[Outlook の他の API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)タスクの残りの部分 api のすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 タスクの REST-API では、特定の操作を続行するには、この点に留意してください。

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



### <a name="a-nametarget-usera-"></a><a name="target-user"></a>ターゲット ユーザー

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

タスク API 要求は、常にサインインしているユーザーの代理として実行されます。 

Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

彼のタスクの API 要求は、常にサインインしているユーザーの代理として実行されます。 

Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。

****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


### <a name="a-nameurl-parametersaurl-"></a><a name="url-parameters"></a>URL-パラメーター

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

残りのパラメーターでこの資料の次の ID を使用してプレース ホルダーの例では、Url を要求します。 拡張機能を作成するリソースのインスタンスの ID を指定する必要があります。

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|folder_id|string|デフォルトの`Tasks`、既知のフォルダーの名前、または仕事フォルダーで、ユーザーのメールボックス内で一意の数値 ID。 |
|group_id|string|タスク グループ、ユーザーのメールボックス内で一意の数値 ID。 |
|TASK_ID|string|数値のタスク ID、ユーザーのメールボックス内で一意です。 |

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

残りのパラメーターでこの資料の次の ID を使用してプレース ホルダーの例では、Url を要求します。 拡張機能を作成するリソースのインスタンスの ID を指定する必要があります。

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|folder_id|string|デフォルトの`Tasks`、既知のフォルダーの名前、または仕事フォルダーで、ユーザーのメールボックス内で一意の数値 ID。 |
|group_id|string|タスク グループ、ユーザーのメールボックス内で一意の数値 ID。 |
|TASK_ID|string|数値のタスク ID、ユーザーのメールボックス内で一意です。 |

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="NoteAboutStartDueDateTimes"></a>
###させると DueDateTime プロパティを指定します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


タスクを作成するには。
- **させる**と**DueDateTime**オプションですが、**させる**を設定する場合は、同じまたはそれ以降の日付に**DueDateTime**を設定する必要があります。 
- **させる**のだけを設定すると、 **DueDateTime**は自動的に**させる**のと同じ値に設定します。 
- **DueDateTime**に設定する場合は、 `null`、**示す**も自動的に設定されますし、 `null`。

**させる**または**DueDateTime**を作成するか、タスクを更新するときに設定する場合。
- 日付とタイム ゾーンの情報を指定します。
- 投稿 (または修正プログラム) の方法は常に無視し、指定されたタイム ゾーンで午前 0 時を想定するいますと、これらのプロパティでは、特定の時刻を指定しないでください。 
- 既定では、投稿 (または修正プログラム) の方法値を UTC に変換し、返しますを UTC で応答。 、 

**させる**で 4 月 26 の東部標準時 (EST) を指定する場合など。
```
  "StartDateTime": {
      "DateTime": "2016-04-26T09:00:00",
      "TimeZone": "Eastern Standard Time"
  }
```

投稿 (または修正プログラム) は、時刻部分は無視され、4 月 26 の午前 0 時を UTC に EST での変換 (utc) の応答でその値を返します。
```
  "StartDateTime": {
    "DateTime": "2016-04-26T04:00:00.0000000",
    "TimeZone": "UTC"
  }
```

使用することができます、`Prefer: outlook.timezone`ヘッダーに UTC 以外のタイム ゾーンで表される応答ですべての日付に関連するプロパティがあります。 

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

タスクを作成するには。
- **させる**と**DueDateTime**オプションですが、**させる**を設定する場合は、同じまたはそれ以降の日付に**DueDateTime**を設定する必要があります。 
- **させる**のだけを設定すると、 **DueDateTime**は自動的に**させる**のと同じ値に設定します。 
- **DueDateTime**に設定する場合は、 `null`、**示す**も自動的に設定されますし、 `null`。

**させる**または**DueDateTime**を作成するか、タスクを更新するときに設定する場合。
- 日付とタイム ゾーンの情報を指定します。
- 投稿 (または修正プログラム) の方法は常に無視し、指定されたタイム ゾーンで午前 0 時を想定するいますと、これらのプロパティでは、特定の時刻を指定しないでください。 
- 既定では、投稿 (または修正プログラム) の方法値を UTC に変換し、返しますを UTC で応答。 、 

**させる**で 4 月 26 の東部標準時 (EST) を指定する場合など。
```
  "StartDateTime": {
      "DateTime": "2016-04-26T09:00:00",
      "TimeZone": "Eastern Standard Time"
  }
```

投稿 (または修正プログラム) は、時刻部分は無視され、4 月 26 の午前 0 時を UTC に EST での変換 (utc) の応答でその値を返します。
```
  "StartDateTime": {
    "DateTime": "2016-04-26T04:00:00.0000000",
    "TimeZone": "UTC"
  }
```

使用することができます、`Prefer: outlook.timezone`ヘッダーに UTC 以外のタイム ゾーンで表される応答ですべての日付に関連するプロパティがあります。 

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="NoteAboutPreferHeader"></a>
###カスタム タイム ゾーンの日付に関連するプロパティを返す<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)リソース内の日付に関連するプロパティを以下に示します。
- **CompletedDateTime**
- **CreatedDateTime**
- **DueDateTime**
- **LastModifiedDateTime**
- **ReminderDateTime**
- **させる**

既定では、POST、GET、パッチ、および包括的なオペレーションは UTC で、残りの応答に日付に関連するプロパティを返します。 使用することができます、`Prefer: outlook.timezone`ヘッダーに UTC 以外のタイム ゾーンで表される応答ですべての日付に関連するプロパティがあります。 次の例では、対応する応答の EST の日付に関連するプロパティを返します。

```
Prefer: outlook.timezone="Eastern Standard Time"
```

Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API-の使用](..\api\use-outlook-rest-api.md)を参照してください。


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)リソース内の日付に関連するプロパティを以下に示します。
- **CompletedDateTime**
- **CreatedDateTime**
- **DueDateTime**
- **LastModifiedDateTime**
- **ReminderDateTime**
- **させる**

既定では、POST、GET、パッチ、および包括的なオペレーションは UTC で、残りの応答に日付に関連するプロパティを返します。 使用することができます、`Prefer: outlook.timezone`ヘッダーに UTC 以外のタイム ゾーンで表される応答ですべての日付に関連するプロパティがあります。 次の例では、対応する応答の EST の日付に関連するプロパティを返します。

```
Prefer: outlook.timezone="Eastern Standard Time"
```

Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="CreateTasks"> </a>
##タスクを作成します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスクを作成します。 2 つの主なシナリオがあります。

デフォルトのタスク グループにタスクを作成することができます (`My Tasks`) と既定の作業フォルダー (`Tasks`) ユーザーのメールボックスの。 この例では、タスク グループまたはタスク フォルダーを指定する必要はありません。

```no-highlight
POST https://outlook.office.com/api/beta/me/tasks
```

特定のタスク フォルダーにタスクを作成することも。

```no-highlight
POST https://outlook.office.com/api/beta/me/taskfolders('{folder_id}')/tasks
```

要求の本体を作成する[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)の JSON 表現を指定します。

**させる**と**DueDateTime**の設定に関する[詳細についてを参照してください](#NoteAboutStartDueDateTimes)のです。

応答メッセージに特定のタイム ゾーンの日付に関連するすべてのプロパティを指定する[方法について説明](#NoteAboutPreferHeader)をします。

**応答**

成功状態コード: 201 作成されました

応答本文: 作成された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)。


**要求のサンプル**

最初の例は、指定したタスク フォルダーにタスクを作成し、要求の本体で**示す**と**DueDateTime**の太平洋標準時 (PST) を表現します。

```
POST https://outlook.office.com/api/beta/me/taskfolders('AAMkADIyAAAhrbPXAAA=')/tasks
Content-Type: application/json

{
  "Subject": "Shop for dinner",
  "StartDateTime": {
      "DateTime": "2016-04-23T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "DueDateTime":  {
      "DateTime": "2016-04-25T13:00:00",
      "TimeZone": "Pacific Standard Time"
  }
}
```

**応答の例**

POST メソッドは、要求の本文に時刻部分は無視され、指定されたタイム ゾーン (PST) の午前 0 時を常に時間を想定しています。 既定では、POST メソッドに変換し、応答に UTC の日付に関連するすべてのプロパティを示しています。

```
Status code: 201 Created

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/TaskFolders('AAMkADIyAAAhrbPXAAA%3D')/Tasks/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADIyAAAhrb_PAAA=')",
  "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIbAOlw==\"",
  "Id": "AAMkADIyAAAhrb_PAAA=",
  "CreatedDateTime": "2016-04-22T05:44:01.2012012Z",
  "LastModifiedDateTime": "2016-04-22T05:44:02.9980882Z",
  "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMxw==",
  "Categories": [ ],
  "AssignedTo": null,
  "Body": {
    "ContentType": "Text",
    "Content": ""
  },
  "CompletedDateTime": null,
  "DueDateTime": {
    "DateTime": "2016-04-25T07:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Importance": "Normal",
  "IsReminderOn": false,
  "Owner": "Administrator",
  "ParentFolderId": "AQMkADA1MTkAAAAIBEgAAAA==",
  "Recurrence": null,
  "ReminderDateTime": null,
  "Sensitivity": "Normal",
  "StartDateTime": {
    "DateTime": "2016-04-23T07:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Status": "NotStarted",
  "Subject": "Shop for dinner"
}
```

**要求のサンプル**

表示する方法、`Prefer: outlook.timezone`ヘッダーは、次の使用例は、タスクを作成および、**させる**と**DueDateTime**東部標準時 (EST) で表されますが含まれています、`Prefer`です。 ヘッダーの太平洋標準時 (PST)

```
POST https://outlook.office.com/api/beta/me/tasks HTTP/1.1

Content-Type: application/json
Prefer: outlook.timezone="Pacific Standard Time"

{
  "Subject": "Shop for children's weekend",
  "StartDateTime": {
      "DateTime": "2016-05-03T09:00:00",
      "TimeZone": "Eastern Standard Time"
  },
  "DueDateTime":  {
      "DateTime": "2016-05-05T16:00:00",
      "TimeZone": "Eastern Standard Time"
  }
}
```

**応答の例**

まったく同様に最後の例では、Post メソッド要求の本文で**示す**と**DueDateTime**の時刻の部分を無視して指定されたタイム ゾーン (EST) の午前 0 時を常に時間を想定しています。

なので、 `Prefer` PST を指定するヘッダー、POST メソッドは、PST の応答の中のすべての日付に関連するプロパティを表します。 具体的には、**させる**と**DueDateTime**のプロパティの POST メソッドは EST の午前 0 時を PST に変換し、PST の応答で返します。

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Tasks/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Tasks('AAMkADA1MHgwAAA=')",
    "@odata.etag": "W/\"1/KC9Vmu40G3DwB6Lgs7MAAAIW9XXA==\"",
    "Id": "AAMkADA1MHgwAAA=",
    "CreatedDateTime": "2016-04-22T15:19:18.9526004-07:00",
    "LastModifiedDateTime": "2016-04-22T15:19:19.015101-07:00",
    "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIW9XXA==",
    "Categories": [
    ],
    "AssignedTo": null,
    "Body": {
        "ContentType": "Text",
        "Content": ""
    },
    "CompletedDateTime": null,
    "DueDateTime": {
        "DateTime": "2016-05-04T21:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "Importance": "Normal",
    "IsReminderOn": false,
    "Owner": "Administrator",
    "ParentFolderId": "AQMkADA1MTEgAAAA==",
    "Recurrence": null,
    "ReminderDateTime": null,
    "Sensitivity": "Normal",
    "StartDateTime": {
        "DateTime": "2016-05-02T21:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "Status": "NotStarted",
    "Subject": "Shop for children's weekend"
}
```

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスクを作成します。 2 つの主なシナリオがあります。

デフォルトのタスク グループにタスクを作成することができます (`My Tasks`) と既定の作業フォルダー (`Tasks`) ユーザーのメールボックスの。 この例では、タスク グループまたはタスク フォルダーを指定する必要はありません。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/tasks
```

特定のタスク フォルダーにタスクを作成することも。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/taskfolders('{folder_id}')/tasks
```

要求の本体を作成する[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)の JSON 表現を指定します。

**させる**と**DueDateTime**の設定に関する[詳細についてを参照してください](#NoteAboutStartDueDateTimes)のです。

応答メッセージに特定のタイム ゾーンの日付に関連するすべてのプロパティを指定する[方法について説明](#NoteAboutPreferHeader)をします。

**応答**

成功状態コード: 201 作成されました

応答本文: 作成された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)。


**要求のサンプル**

最初の例は、指定したタスク フォルダーにタスクを作成し、要求の本体で**示す**と**DueDateTime**の太平洋標準時 (PST) を表現します。

```
POST https://outlook.office.com/api/v2.0/me/taskfolders('AAMkADIyAAAhrbPXAAA=')/tasks
Content-Type: application/json

{
  "Subject": "Shop for dinner",
  "StartDateTime": {
      "DateTime": "2016-04-23T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "DueDateTime":  {
      "DateTime": "2016-04-25T13:00:00",
      "TimeZone": "Pacific Standard Time"
  }
}
```

**応答の例**

POST メソッドは、要求の本文に時刻部分は無視され、指定されたタイム ゾーン (PST) の午前 0 時を常に時間を想定しています。 既定では、POST メソッドに変換し、応答に UTC の日付に関連するすべてのプロパティを示しています。

```
Status code: 201 Created

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/TaskFolders('AAMkADIyAAAhrbPXAAA%3D')/Tasks/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADIyAAAhrb_PAAA=')",
  "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIbAOlw==\"",
  "Id": "AAMkADIyAAAhrb_PAAA=",
  "CreatedDateTime": "2016-04-22T05:44:01.2012012Z",
  "LastModifiedDateTime": "2016-04-22T05:44:02.9980882Z",
  "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMxw==",
  "Categories": [ ],
  "AssignedTo": null,
  "Body": {
    "ContentType": "Text",
    "Content": ""
  },
  "CompletedDateTime": null,
  "DueDateTime": {
    "DateTime": "2016-04-25T07:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Importance": "Normal",
  "IsReminderOn": false,
  "Owner": "Administrator",
  "ParentFolderId": "AQMkADA1MTkAAAAIBEgAAAA==",
  "Recurrence": null,
  "ReminderDateTime": null,
  "Sensitivity": "Normal",
  "StartDateTime": {
    "DateTime": "2016-04-23T07:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Status": "NotStarted",
  "Subject": "Shop for dinner"
}
```

**要求のサンプル**

表示する方法、`Prefer: outlook.timezone`ヘッダーは、次の使用例は、タスクを作成および、**させる**と**DueDateTime**東部標準時 (EST) で表されますが含まれています、`Prefer`です。 ヘッダーの太平洋標準時 (PST)

```
POST https://outlook.office.com/api/v2.0/me/tasks HTTP/1.1

Content-Type: application/json
Prefer: outlook.timezone="Pacific Standard Time"

{
  "Subject": "Shop for children's weekend",
  "StartDateTime": {
      "DateTime": "2016-05-03T09:00:00",
      "TimeZone": "Eastern Standard Time"
  },
  "DueDateTime":  {
      "DateTime": "2016-05-05T16:00:00",
      "TimeZone": "Eastern Standard Time"
  }
}
```

**応答の例**

まったく同様に最後の例では、Post メソッド要求の本文で**示す**と**DueDateTime**の時刻の部分を無視して指定されたタイム ゾーン (EST) の午前 0 時を常に時間を想定しています。

なので、 `Prefer` PST を指定するヘッダー、POST メソッドは、PST の応答の中のすべての日付に関連するプロパティを表します。 具体的には、**させる**と**DueDateTime**のプロパティの POST メソッドは EST の午前 0 時を PST に変換し、PST の応答で返します。

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Tasks/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Tasks('AAMkADA1MHgwAAA=')",
    "@odata.etag": "W/\"1/KC9Vmu40G3DwB6Lgs7MAAAIW9XXA==\"",
    "Id": "AAMkADA1MHgwAAA=",
    "CreatedDateTime": "2016-04-22T15:19:18.9526004-07:00",
    "LastModifiedDateTime": "2016-04-22T15:19:19.015101-07:00",
    "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIW9XXA==",
    "Categories": [
    ],
    "AssignedTo": null,
    "Body": {
        "ContentType": "Text",
        "Content": ""
    },
    "CompletedDateTime": null,
    "DueDateTime": {
        "DateTime": "2016-05-04T21:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "Importance": "Normal",
    "IsReminderOn": false,
    "Owner": "Administrator",
    "ParentFolderId": "AQMkADA1MTEgAAAA==",
    "Recurrence": null,
    "ReminderDateTime": null,
    "Sensitivity": "Normal",
    "StartDateTime": {
        "DateTime": "2016-05-02T21:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "Status": "NotStarted",
    "Subject": "Shop for children's weekend"
}
```

****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="GetTasks"> </a>
##タスクを取得します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


[すべてのタスクを取得する](#GetAllTasksBeta) | [タスクを取得します。 ](#GetATaskBeta) 


<a name="GetAllTasksBeta"> </a>
### <a name="a-nameget-all-tasksa"></a><a name="get-all-tasks"></a>すべてのタスクを取得します。 

_**スコープが必要です**: https://outlook.office.com/tasks.read_

複数のタスクを取得します。

サインインしているユーザーのメールボックス内のすべてのタスクを取得できます。
```no-highlight
GET https://outlook.office.com/api/beta/me/tasks
```

<a name="GetTasksInFolderBeta"></a>または、特定のフォルダー内のすべてのタスクを取得できます。
```no-highlight
GET https://outlook.office.com/api/beta/me/taskfolders('{folder_id}')/tasks
```

1 つ以上のタスク グループがあり、特定のタスク グループ内のすべてのタスクを取得すること、まず[タスク グループ内のすべてのタスク フォルダー](#GetTaskFolders)とのこれらのタスク フォルダーにタスクを取得します。 


**応答**

成功状態コード: 200 OK

応答本文:[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)のコレクション

既定では、応答で、日付に関連するプロパティは UTC で表されます。 応答メッセージに特定のタイム ゾーンの日付に関連するすべてのプロパティを指定する[方法について説明](#NoteAboutPreferHeader)をします。


**要求のサンプル**

次の使用例は、ユーザーのメールボックス内のすべてのタスクを取得します。

```
GET https://outlook.office.com/api/beta/me/tasks
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Tasks",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Tasks('AAMkADA1MTrfAAA=')",
      "@odata.etag": "W/\"1/KC9Vmu40G3DwB6Lgs7MAAAIOJMxw==\"",
      "Id": "AAMkADA1MTrfAAA=",
      "CreatedDateTime": "2016-04-22T05:44:01.2012012Z",
      "LastModifiedDateTime": "2016-04-22T05:44:02.9980882Z",
      "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMxw==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTime": {
        "DateTime": "2016-04-25T07:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkADA1MTBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": {
        "DateTime": "2016-04-23T07:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Status": "NotStarted",
      "Subject": "Shop for dinner"
    },
    {
      "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Tasks('AAMkADA1MTrgAAA=')",
      "@odata.etag": "W/\"1/KC9Vmu40G3DwB6Lgs7MAAAIOJMyQ==\"",
      "Id": "AAMkADA1MTrgAAA=",
      "CreatedDateTime": "2016-04-22T06:03:35.9279794Z",
      "LastModifiedDateTime": "2016-04-22T06:03:35.9436052Z",
      "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMyQ==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTime": {
        "DateTime": "2016-04-27T04:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkADA1MTBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": {
        "DateTime": "2016-04-26T04:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Status": "NotStarted",
      "Subject": "Shop for dinner"
    }
  ]
}
```

<a name="GetATaskBeta"> </a>
### <a name="a-nameget-a-taska"></a><a name="get-a-task"></a>タスクを取得します。 

_**スコープが必要です**: https://outlook.office.com/tasks.read_

特定のタスクを取得します。

```no-highlight
GET https://outlook.office.com/api/beta/me/tasks('{task_id}')
```

**応答**

成功状態コード: 200 OK

応答本文: 要求された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。

既定では、応答で、日付に関連するプロパティは UTC で表されます。 応答メッセージに特定のタイム ゾーンの日付に関連するすべてのプロパティを指定する[方法について説明](#NoteAboutPreferHeader)をします。

**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/tasks('AAMkADA1MTrgAAA=') 
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Tasks/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADA1MTrgAAA=')",
  "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIa/+kw==\"",
  "Id": "AAMkADA1MTrgAAA=",
  "CreatedDateTime": "2016-04-22T06:03:35.9279794Z",
  "LastModifiedDateTime": "2016-04-22T06:03:35.9436052Z",
  "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMyQ==",
  "Categories": [ ],
  "AssignedTo": null,
  "Body": {
    "ContentType": "Text",
    "Content": ""
  },
  "CompletedDateTime": null,
  "DueDateTime": {
    "DateTime": "2016-04-27T04:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Importance": "Normal",
  "IsReminderOn": false,
  "Owner": "Administrator",
  "ParentFolderId": "AQMkADA1MTBEgAAAA==",
  "Recurrence": null,
  "ReminderDateTime": null,
  "Sensitivity": "Normal",
  "StartDateTime": {
    "DateTime": "2016-04-26T04:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Status": "NotStarted",
  "Subject": "Shop for dinner"
}
```

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

[すべてのタスクを取得する](#GetAllTasksV2) | [タスクを取得します。 ](#GetATaskV2) 


<a name="GetAllTasksV2"> </a>
### <a name="a-nameget-all-tasksa"></a><a name="get-all-tasks"></a>すべてのタスクを取得します。 

_**スコープが必要です**: https://outlook.office.com/tasks.read_

複数のタスクを取得します。

サインインしているユーザーのメールボックス内のすべてのタスクを取得できます。
```no-highlight
GET https://outlook.office.com/api/v2.0/me/tasks
```

<a name="GetTasksInFolderV2"></a>または、特定のフォルダー内のすべてのタスクを取得できます。
```no-highlight
GET https://outlook.office.com/api/v2.0/me/taskfolders('{folder_id}')/tasks
```

1 つ以上のタスク グループがあり、特定のタスク グループ内のすべてのタスクを取得すること、まず[タスク グループ内のすべてのタスク フォルダー](#GetTaskFolders)とのこれらのタスク フォルダーにタスクを取得します。 


**応答**

成功状態コード: 200 OK

応答本文:[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)のコレクション

既定では、応答で、日付に関連するプロパティは UTC で表されます。 応答メッセージに特定のタイム ゾーンの日付に関連するすべてのプロパティを指定する[方法について説明](#NoteAboutPreferHeader)をします。


**要求のサンプル**

次の使用例は、ユーザーのメールボックス内のすべてのタスクを取得します。

```
GET https://outlook.office.com/api/v2.0/me/tasks
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Tasks",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Tasks('AAMkADA1MTrfAAA=')",
      "@odata.etag": "W/\"1/KC9Vmu40G3DwB6Lgs7MAAAIOJMxw==\"",
      "Id": "AAMkADA1MTrfAAA=",
      "CreatedDateTime": "2016-04-22T05:44:01.2012012Z",
      "LastModifiedDateTime": "2016-04-22T05:44:02.9980882Z",
      "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMxw==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTime": {
        "DateTime": "2016-04-25T07:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkADA1MTBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": {
        "DateTime": "2016-04-23T07:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Status": "NotStarted",
      "Subject": "Shop for dinner"
    },
    {
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Tasks('AAMkADA1MTrgAAA=')",
      "@odata.etag": "W/\"1/KC9Vmu40G3DwB6Lgs7MAAAIOJMyQ==\"",
      "Id": "AAMkADA1MTrgAAA=",
      "CreatedDateTime": "2016-04-22T06:03:35.9279794Z",
      "LastModifiedDateTime": "2016-04-22T06:03:35.9436052Z",
      "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMyQ==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTime": {
        "DateTime": "2016-04-27T04:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkADA1MTBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": {
        "DateTime": "2016-04-26T04:00:00.0000000",
        "TimeZone": "UTC"
      },
      "Status": "NotStarted",
      "Subject": "Shop for dinner"
    }
  ]
}
```

<a name="GetATaskV2"> </a>
### <a name="a-nameget-a-taska"></a><a name="get-a-task"></a>タスクを取得します。 

_**スコープが必要です**: https://outlook.office.com/tasks.read_

特定のタスクを取得します。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/tasks('{task_id}')
```

**応答**

成功状態コード: 200 OK

応答本文: 要求された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。

既定では、応答で、日付に関連するプロパティは UTC で表されます。 応答メッセージに特定のタイム ゾーンの日付に関連するすべてのプロパティを指定する[方法について説明](#NoteAboutPreferHeader)をします。

**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/tasks('AAMkADA1MTrgAAA=') 
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Tasks/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADA1MTrgAAA=')",
  "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIa/+kw==\"",
  "Id": "AAMkADA1MTrgAAA=",
  "CreatedDateTime": "2016-04-22T06:03:35.9279794Z",
  "LastModifiedDateTime": "2016-04-22T06:03:35.9436052Z",
  "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIOJMyQ==",
  "Categories": [ ],
  "AssignedTo": null,
  "Body": {
    "ContentType": "Text",
    "Content": ""
  },
  "CompletedDateTime": null,
  "DueDateTime": {
    "DateTime": "2016-04-27T04:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Importance": "Normal",
  "IsReminderOn": false,
  "Owner": "Administrator",
  "ParentFolderId": "AQMkADA1MTBEgAAAA==",
  "Recurrence": null,
  "ReminderDateTime": null,
  "Sensitivity": "Normal",
  "StartDateTime": {
    "DateTime": "2016-04-26T04:00:00.0000000",
    "TimeZone": "UTC"
  },
  "Status": "NotStarted",
  "Subject": "Shop for dinner"
}
```

****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="UpdateTasks"> </a>
##タスクを更新します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスクの書き込み可能なプロパティを変更します。

```no-highlight
PATCH https://outlook.office.com/api/beta/me/tasks/{task_id}
```

要求の本体で[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)を更新するのには書き込み可能なプロパティの JSON の形式を指定します。

**させる**と**DueDateTime**の設定に関する[詳細についてを参照してください](#NoteAboutStartDueDateTimes)のです。

[完了](#CompleteTasks)アクション、または明示的に修正プログラムの操作では、 **CompletedDateTime**プロパティを設定できます。 **CompletedDateTime**を設定するのには修正プログラムを使用する場合は、**状態**を設定することを確認してください`Completed`も同様です。

既定では、応答で、日付に関連するプロパティは UTC で表されます。 応答ですべての日付に関連するプロパティのカスタム タイム ゾーンを指定する[方法について説明](#NoteAboutPreferHeader)をします。

**応答**

成功状態コード: 200 OK

応答本文: 更新された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。


**要求のサンプル**

次の使用例は、 **DueDateTime**を変更しを使用して、`Prefer: outlook.timezone`を表現する日付に関連するプロパティを指定します。 ヘッダーを応答に東部標準時 (EST)
 
```
PATCH https://outlook.office.com/api/beta/me/tasks('AAMkADA1MTHgwAAA=')

Prefer: outlook.timezone="Eastern Standard Time"
Content-Type: application/json

{
  "DueDateTime":  {
      "DateTime": "2016-05-06T16:00:00",
      "TimeZone": "Eastern Standard Time"
  }
}
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Tasks/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADA1MTHgwAAA=')",
  "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIa/+lg==\"",
  "Id": "AAMkADA1MTHgwAAA=",
    "CreatedDateTime": "2016-04-22T18:19:18.9526004-04:00",
    "LastModifiedDateTime": "2016-04-22T18:38:20.5541528-04:00",
    "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIW9XXg==",
    "Categories": [
    ],
    "AssignedTo": null,
    "Body": {
        "ContentType": "Text",
        "Content": ""
    },
    "CompletedDateTime": null,
    "DueDateTime": {
        "DateTime": "2016-05-06T00:00:00.0000000",
        "TimeZone": "Eastern Standard Time"
    },
    "Importance": "Normal",
    "IsReminderOn": false,
    "Owner": "Administrator",
    "ParentFolderId": "AQMkADA1MTIBEgAAAA==",
    "Recurrence": null,
    "ReminderDateTime": null,
    "Sensitivity": "Normal",
    "StartDateTime": {
        "DateTime": "2016-05-03T00:00:00.0000000",
        "TimeZone": "Eastern Standard Time"
    },
    "Status": "NotStarted",
    "Subject": "Shop for children's weekend"
}
```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスクの書き込み可能なプロパティを変更します。

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/tasks/{task_id}
```

要求の本体で[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)を更新するのには書き込み可能なプロパティの JSON の形式を指定します。

**させる**と**DueDateTime**の設定に関する[詳細についてを参照してください](#NoteAboutStartDueDateTimes)のです。

[完了](#CompleteTasks)アクション、または明示的に修正プログラムの操作では、 **CompletedDateTime**プロパティを設定できます。 **CompletedDateTime**を設定するのには修正プログラムを使用する場合は、**状態**を設定することを確認してください`Completed`も同様です。

既定では、応答で、日付に関連するプロパティは UTC で表されます。 応答ですべての日付に関連するプロパティのカスタム タイム ゾーンを指定する[方法について説明](#NoteAboutPreferHeader)をします。

**応答**

成功状態コード: 200 OK

応答本文: 更新された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。


**要求のサンプル**

次の使用例は、 **DueDateTime**を変更しを使用して、`Prefer: outlook.timezone`を表現する日付に関連するプロパティを指定します。 ヘッダーを応答に東部標準時 (EST)
 
```
PATCH https://outlook.office.com/api/v2.0/me/tasks('AAMkADA1MTHgwAAA=')

Prefer: outlook.timezone="Eastern Standard Time"
Content-Type: application/json

{
  "DueDateTime":  {
      "DateTime": "2016-05-06T16:00:00",
      "TimeZone": "Eastern Standard Time"
  }
}
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Tasks/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADA1MTHgwAAA=')",
  "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIa/+lg==\"",
  "Id": "AAMkADA1MTHgwAAA=",
    "CreatedDateTime": "2016-04-22T18:19:18.9526004-04:00",
    "LastModifiedDateTime": "2016-04-22T18:38:20.5541528-04:00",
    "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIW9XXg==",
    "Categories": [
    ],
    "AssignedTo": null,
    "Body": {
        "ContentType": "Text",
        "Content": ""
    },
    "CompletedDateTime": null,
    "DueDateTime": {
        "DateTime": "2016-05-06T00:00:00.0000000",
        "TimeZone": "Eastern Standard Time"
    },
    "Importance": "Normal",
    "IsReminderOn": false,
    "Owner": "Administrator",
    "ParentFolderId": "AQMkADA1MTIBEgAAAA==",
    "Recurrence": null,
    "ReminderDateTime": null,
    "Sensitivity": "Normal",
    "StartDateTime": {
        "DateTime": "2016-05-03T00:00:00.0000000",
        "TimeZone": "Eastern Standard Time"
    },
    "Status": "NotStarted",
    "Subject": "Shop for children's weekend"
}
```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="DeleteTasks"> </a>
##タスクを削除します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

ユーザーのメールボックス内の指定されたタスクを削除します。

```no-highlight
DELETE https://outlook.office.com/api/beta/me/tasks('{task_id}')
```

**応答**

成功状態コード: 204 コンテンツなし

応答本文: なし


**要求のサンプル**

```
DELETE https://outlook.office365.com/api/beta/me/tasks('AAMkADIyAAAhrb_QAAA=')
```

**応答の例**

```
Status code: 204 No Content
```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

ユーザーのメールボックス内の指定されたタスクを削除します。

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/tasks('{task_id}')
```

**応答**

成功状態コード: 204 コンテンツなし

応答本文: なし


**要求のサンプル**

```
DELETE https://outlook.office365.com/api/v2.0/me/tasks('AAMkADIyAAAhrb_QAAA=')
```

**応答の例**

```
Status code: 204 No Content
```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="CompleteTasks"> </a>
##タスクを完了<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスクを完了し、 **CompletedDateTime**プロパティに現在の日付、および**状態**のプロパティを設定`Completed`。

```no-highlight
POST https://outlook.office.com/api/beta/me/tasks('{task_id}')/complete
```

**メモ** 

**CompletedDateTime**は、タスクが完了すると、日付を表します。 **CompletedDateTime**の時刻部分は、UTC の午前 0 時に既定で設定されています。 

アプリケーションでカスタム タイム ゾーンを指定できます、`Prefer`要求ヘッダー。 タイム ゾーンが太平洋標準時 (PST) に**CompletedDateTime**を設定する例は次のとおりです。

```
Prefer: outlook.timezone="Pacific Standard Time"
```

この要求ヘッダーでは、指定されたタイム ゾーンへの応答ですべての日付に関連するプロパティを設定します。

**応答**

成功状態コード: 200 OK

応答本文: 完了した[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)タスクのコレクションで。 定期的な一連のタスクを実行している場合、シリーズでは、完了したタスクとデータ系列の次のタスクは、タスクのコレクションが含まれます。


**要求のサンプル**

次の例では、指定したタスクの完了をマークします。 太平洋標準時 (PST) で指定されているため、`Prefer: outlook.timezone`ヘッダー、 **CompletedDateTime**およびその他の日付に関連するプロパティの応答では、PST で表されます。

```
POST https://outlook.office.com/api/beta/me/tasks('AAMkADA1MT15rfAAA=')/complete

Prefer: outlook.timezone="Pacific Standard Time"
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Tasks",
  "value": [
    {
      "@odata.id": "https://outlook.office365.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADA1MT15rfAAA=')",
      "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIa/+lw==\"",
      "Id": "AAMkADA1MT15rfAAA=",
      "CreatedDateTime": "2016-04-21T22:44:01.2012012-07:00",
      "LastModifiedDateTime": "2016-04-22T19:28:38.5300447-07:00",
      "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIW9XYQ==",
      "Categories": [
      ],
      "AssignedTo": null,
      "Body": {
          "ContentType": "Text",
          "Content": ""
      },
      "CompletedDateTime": {
          "DateTime": "2016-04-22T00:00:00.0000000",
          "TimeZone": "Pacific Standard Time"
      },
      "DueDateTime": {
          "DateTime": "2016-04-25T00:00:00.0000000",
          "TimeZone": "Pacific Standard Time"
      },
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkADA1MTIBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": {
          "DateTime": "2016-04-21T00:00:00.0000000",
          "TimeZone": "Pacific Standard Time"
      },
      "Status": "Completed",
      "Subject": "Shop for dinner"
    }
  ]
}
```

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスクを完了し、 **CompletedDateTime**プロパティに現在の日付、および**状態**のプロパティを設定`Completed`。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/tasks('{task_id}')/complete
```

**メモ** 

**CompletedDateTime**は、タスクが完了すると、日付を表します。 **CompletedDateTime**の時刻部分は、UTC の午前 0 時に既定で設定されています。 

アプリケーションでカスタム タイム ゾーンを指定できます、`Prefer`要求ヘッダー。 タイム ゾーンが太平洋標準時 (PST) に**CompletedDateTime**を設定する例は次のとおりです。

```
Prefer: outlook.timezone="Pacific Standard Time"
```

この要求ヘッダーでは、指定されたタイム ゾーンへの応答ですべての日付に関連するプロパティを設定します。

**応答**

成功状態コード: 200 OK

応答本文: 完了した[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)タスクのコレクションで。 定期的な一連のタスクを実行している場合、シリーズでは、完了したタスクとデータ系列の次のタスクは、タスクのコレクションが含まれます。


**要求のサンプル**

次の例では、指定したタスクの完了をマークします。 太平洋標準時 (PST) で指定されているため、`Prefer: outlook.timezone`ヘッダー、 **CompletedDateTime**およびその他の日付に関連するプロパティの応答では、PST で表されます。

```
POST https://outlook.office.com/api/v2.0/me/tasks('AAMkADA1MT15rfAAA=')/complete

Prefer: outlook.timezone="Pacific Standard Time"
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Tasks",
  "value": [
    {
      "@odata.id": "https://outlook.office365.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/Tasks('AAMkADA1MT15rfAAA=')",
      "@odata.etag": "W/\"hmM7Eb/jgEec8l3+gkJEawAAIa/+lw==\"",
      "Id": "AAMkADA1MT15rfAAA=",
      "CreatedDateTime": "2016-04-21T22:44:01.2012012-07:00",
      "LastModifiedDateTime": "2016-04-22T19:28:38.5300447-07:00",
      "ChangeKey": "1/KC9Vmu40G3DwB6Lgs7MAAAIW9XYQ==",
      "Categories": [
      ],
      "AssignedTo": null,
      "Body": {
          "ContentType": "Text",
          "Content": ""
      },
      "CompletedDateTime": {
          "DateTime": "2016-04-22T00:00:00.0000000",
          "TimeZone": "Pacific Standard Time"
      },
      "DueDateTime": {
          "DateTime": "2016-04-25T00:00:00.0000000",
          "TimeZone": "Pacific Standard Time"
      },
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkADA1MTIBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": {
          "DateTime": "2016-04-21T00:00:00.0000000",
          "TimeZone": "Pacific Standard Time"
      },
      "Status": "Completed",
      "Subject": "Shop for dinner"
    }
  ]
}
```

****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="SyncTasks"></a>
##タスクまたはタスク フォルダーを同期します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**スコープが必要です**: http://outlook.office.com/tasks.readwrite_

作業フォルダー、またはユーザーのメールボックス内のタスク フォルダーにタスクを同期することができます。 タスクを同期するフォルダーごとの操作は、すべてのタスクを既定のタスク フォルダーに同期するたとえば、 `Tasks`。 フォルダー階層内のタスクを同期するには、各タスクのフォルダーを個別に同期する必要があります。 タスクまたはタスク フォルダーを同期するプロセスと同様に、通常 の呼び出しは、それぞれ 2 つ以上の同期要求のラウンドを必要とします。 ABRUFEN 

方法と同様に、Get メソッドを使用して[、フォルダー内のタスクを取得](#GetTasksInFolderBeta)する、または[メールボックス内のフォルダーのタスクを取得する](#GetTaskFolders)には、特定の要求のヘッダー、および_DeltaToken_を含めることを除いて、または_SkipToken_を適切な場合。

**要求ヘッダー** 

- 指定する必要があります、`Prefer: odata.track-changes`を含むものを除く、すべての同期要求のヘッダー、 `skipToken` 、前回の同期要求に返されます。 最初の応答での調査、_優先順位で適用した: odata.track 変更_リソースが開始する前に同期をサポートしていることを確認するヘッダー。 (の詳細については、`skipToken`で同期する場合は、タスクまたは[タスク フォルダーの 2 つ目応答のデータをサンプル](#SyncTaskFoldersSampleSecondResponseBeta)では、作業フォルダーを同期する場合の[タスクの 2 番目の応答のデータをサンプル](#SyncTasksSampleSecondResponseBeta)します) 。
- 指定すること、`Prefer: odata.maxpagesize={x}`のタスク (またはタスク フォルダーを同期するかによって) の最大数を示すヘッダー各同期要求を返す。

同期の一般的なラウンドです。

1. GET-要求を行う 必須の最初の_選択: odata.track 変更_ヘッダー。 同期要求に対する初回の応答は、常に、 _DeltaToken_を返します。 (2 番目およびそれ以降の GET 要求とは異なる最初の GET 要求によって、 _DeltaToken_または前の応答で受信した_SkipToken_のいずれかを含むします。 )

2. 最初の応答が返された場合、_の設定で適用した: odata.track 変更_ヘッダー、リソースの同期を続行することができます。

  - GET-要求を行います。 2 つ目の 指定の_選択: odata.track 変更_を同期するのにはリソースの追加のインスタンスがあるかどうかを決定する最初の取得からヘッダーと_DeltaToken_が返されます。 2 番目の要求を返します追加のインスタンスとするか、 _SkipToken_がある場合複数のインスタンスが使用可能なまたは_DeltaToken_を停止する場合、最後のインスタンスが同期された場合。

  - ABRUFEN von の呼び出しを送信し、前の呼び出しから返される_SkipToken_を含む同期を続行します。 同期が完了することを示すの_DeltaToken_ 、_@odata.deltaLink_ヘッダーを含む最終的な応答を取得する場合を停止します。


見て初期とそれ以降の呼び出しの構文で同期のラウンドです。


**タスク フォルダーにタスクを同期するには。**

最初の要求。

```no-highlight
GET https://outlook.office.com/api/beta/me/TaskFolders('{folder_id}')/Tasks
```


2 番目の要求、またはそれ以降のラウンドの最初の要求。

```no-highlight
GET https://outlook.office.com/api/beta/me/TaskFolders('{folder_id}')/Tasks/?$deltatoken={delta_token}
```


3 つ目以降の要求で同じラウンドです。 含む応答を取得するときに停止、`@odata.deltaLink`を持つヘッダー、`deltaToken`もう一度。

```no-highlight
GET https://outlook.office.com/api/beta/me/TaskFolders('{folder_id}')/Tasks/?$skiptoken={skip_token}
```


**メールボックス内のタスク フォルダーを同期するには**

最初の要求。

```no-highlight
GET https://outlook.office.com/api/beta/me/TaskFolders
```


2 番目の要求、またはそれ以降のラウンドの最初の要求。

```no-highlight
GET https://outlook.office.com/api/beta/me/TaskFolders/?$deltatoken={delta_token}
```


3 つ目以降の要求で同じラウンドです。 含む応答を取得するときに停止、`@odata.deltaLink`を持つヘッダー、`deltaToken`もう一度。

```no-highlight
GET https://outlook.office.com/api/beta/me/TaskFolders/?$skiptoken={skip_token}
```




**パラメーター**

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_ヘッダーのパラメーター_|
|好む|OData.Track 変更|要求が同期要求であることを示します。 ラウンドの最初の 2 つの GET 要求に対して必要です。|
|好む|OData.MaxPageSize|各応答で返されるメッセージの数を設定します。 省略可能です。|
|_URL-パラメーター_|
|deltaToken|string|`deltaToken`前の同期応答の@odata.deltaLinkの値の一部として文字列が返されます。|
|skipToken|string|`skipToken`前の同期応答の@odata.nextLinkの値の一部として文字列が返されます。 |


**メモ** 

- 指定すると、 `Prefer: odata.track-changes` 、最初の要求に応答が同期をサポートしている場合、応答が含まれます`Preference-applied: odata.track-changes`ヘッダーにします。
- 、サポートされていないリソースを同期しようとしたかどうか、または初期同期要求でない場合は表示されません、 `Preference-applied` 、応答のヘッダーです。
- 優れたレスポンス ・ タイムのプロパティを取得するだけのシナリオに便利です $select クエリ パラメーターを使用します。  
- $Filter、$ Orderby、$ Search、および $top クエリのパラメーターを使用することはできません。  


**応答本文**

- タスクを同期する場合: コレクション内の要求された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)オブジェクト。

- タスク フォルダーを同期する場合: コレクション内の要求された[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)オブジェクトです。

オブジェクトの数に設定された値に依存します`Prefer: odata.maxpagesize`要求ヘッダー。


**使用例**

2 つの例を次に示します。
- [タスク フォルダーにタスクを同期します。](#SyncTasksSampleInitialRequestBeta)
- [タスク フォルダーを同期](#SyncTaskFoldersSampleInitialRequestBeta)します。 

それぞれの例は、最初と 2 番目の同期要求を示しています。 
- 各要求は、指定`Prefer: odata.maxpagesize=1`1 つだけオブジェクトを取得する (タスクまたはタスクのフォルダーをそれぞれ) 、時にします。
- 1 つの同期オブジェクトは、初期の応答が返されます、`deltaLink`と`deltaToken`。 
- 2 番目の要求を使用している`deltatoken`。 1 つの同期オブジェクトは、2 番目の応答が返されます、`nextLink`と`skipToken`。 

GET-の呼び出しで使用して、 同期プロセスを反復処理し、次の`skipToken`を含む同期応答を取得するまでに、前回の同期要求から返される、`deltaLink`と`deltaToken`次のよう。
```
"@odata.deltaLink": “https://outlook.office.com/api/beta/me/TaskFolders('AQMkAGMw80AAAIBEgAAAA==')/Tasks/?%24deltaToken=294a8f04cc0345c5ae093d484629e186”
```

このような場合、同期の現在のラウンドが完了しました。 保存、`deltaToken`の同期は、次のラウンドにします。 


<a name="SyncTasksSampleInitialRequestBeta"></a>

**サンプルの最初の要求 (タスクの同期)**

```
    GET https://outlook.office.com/api/beta/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks HTTP/1.1
    Prefer: odata.maxpagesize=1
  Prefer: odata.track-changes
```

**サンプルの初期応答データ (タスクの同期)**

```
HTTP/1.1 200 OK
Preference-Applied: odata.track-changes

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#me/TaskFolders('AQMkAGMwAAAIBEgAAAA%3D%3D')/Tasks",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/beta/Users('47ec4680-f443-4f9c-a3e5-f7660f0aceae@b4ffe6c0-e717-4104-acd1-e9dfe38ff5f9')/Tasks('AAMkAGMwQsKVevNAAAG1VNmAAA=')",
      "@odata.etag": "W/\"3JfzyLwJe0mPNcULClXrzQAABtYBDw==\"",
      "Id": "AAMkAGMwQsKVevNAAAG1VNmAAA=",
      "CreatedDateTime": "2016-02-29T20:51:25.2226052Z",
      "LastModifiedDateTime": "2016-02-29T20:51:25.2538576Z",
      "ChangeKey": "3JfzyLwJe0mPNcULClXrzQAABtYBDw==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTime": null,
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkAGMwAAAIBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": null,
      "Status": "NotStarted",
      "Subject": "another task"
    }
  ],
  "@odata.deltaLink": "https://outlook.office.com/api/beta/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks/?%24deltatoken=175e2e04482e431ea96e89145c212f8c"
}
```

**サンプルの 2 番目の要求 (タスクの同期)**

```
    GET https://outlook.office.com/api/beta/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks/?%24deltatoken=175e2e04482e431ea96e89145c212f8c HTTP/1.1
    Prefer: odata.maxpagesize=1
  Prefer: odata.track-changes
```

<a name="SyncTasksSampleSecondResponseBeta"></a>

**サンプル 2 番目の応答データ (タスクを同期する)**

```
HTTP/1.1 200 OK

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#me/TaskFolders('AQMkAGMwAAAIBEgAAAA%3D%3D')/Tasks/$delta",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/beta/Users('47ec4680-f443-4f9c-a3e5-f7660f0aceae@b4ffe6c0-e717-4104-acd1-e9dfe38ff5f9')/Tasks('AAMkAGMwQsKVevNAAAG1VNlAAA=')",
      "@odata.etag": "W/\"3JfzyLwJe0mPNcULClXrzQAABtYBDQ==\"",
      "Id": "AAMkAGMwQsKVevNAAAG1VNlAAA=",
      "CreatedDateTime": "2016-02-29T20:51:02.5955351Z",
      "LastModifiedDateTime": "2016-02-29T20:51:03.9703679Z",
      "ChangeKey": "3JfzyLwJe0mPNcULClXrzQAABtYBDQ==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTimeTime": null,
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkAGMwAAAIBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": null,
      "Status": "NotStarted",
      "Subject": "another task"
    }
  ],
  "@odata.nextLink": "https://outlook.office.com/api/beta/me/TaskFolders('AQMkAGMw80AAAIBEgAAAA==')/Tasks/?%24skipToken=0fbce2031e844a2f9d13d8bee5ebe2c6"
}
```

GET-の呼び出しで使用して、 タスクの同期を続行し、次の`skiptoken`で返される`@odata.nextLink`の最終的な応答が含まれるまで、前の応答、`@odata.deltaLink`と`deltaToken`。 保存、`deltaToken`の同期は、次のラウンドにします。


<a name="SyncTaskFoldersSampleInitialRequestBeta"></a>

**サンプルの最初の要求 (作業フォルダーを同期する)**

```
    GET https://outlook.office.com/api/beta/me/TaskFolders HTTP/1.1
    Prefer: odata.maxpagesize=1
    Prefer: odata.track-changes
```

**サンプルの初期応答データ (タスク フォルダーを同期する)**

```
HTTP/1.1 200 OK
Preference-Applied: odata.track-changes

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#me/TaskFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGJiAAAAAAESAAA=')",
            "Id": "AAMkAGJiAAAAAAESAAA=",
            "ChangeKey": "PG2a661l00Cy9qH3YxmDfwAAAAAAPA==",
            "Name": "Tasks",
            "IsDefaultFolder":true,
            "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
        }
    ],
    "@odata.deltaLink": "https://outlook.office.com/api/beta/me/TaskFolders/?%24deltatoken=OyZKBDxtmuutZdNAsvah92MZg38AAAAAZwkBAAAA"
}
```

**サンプルの 2 番目の要求 (作業フォルダーを同期する)**

```
    GET https://outlook.office.com/api/beta/me/TaskFolders/?%24deltatoken=OyZKBDxtmuutZdNAsvah92MZg38AAAAAZwkBAAAA HTTP/1.1
    Prefer: odata.maxpagesize=1
    Prefer: odata.track-changes
```

<a name="SyncTaskFoldersSampleSecondResponseBeta"></a>

**サンプル 2 番目の応答データ (作業フォルダーを同期する)**

```
HTTP/1.1 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#me/TaskFolders/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGI5AAAunDbWAAA=')",
            "Id": "AAMkAGI5AAAunDbWAAA=",
            "ChangeKey": "PmebZ1wYAUaTmrKkvU9LIQAALqEkaw==",
            "Name": "Bingo",
            "IsDefaultFolder":false,
            "ParentGroupKey": "db0823f2-93bd-4db6-8038-98bbc5f39a45"
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/beta/me/TaskFolders/?%24skipToken=x_zCAz5nm2dcGAFGk5qypL1PSyEAAC6cRncCAAAA"
}

```

GET-の呼び出しで使用して、 同期を続行し、次の`skiptoken`で返される`@odata.nextLink`最終的な応答が含まれるまで、前の応答の`@odata.deltaLink`と`deltaToken`。 この例では、3 番目の要求が返されます、`deltaToken`の同期は、このラウンドの完了とします。


**3 サンプルの 番目の要求 (作業フォルダーを同期する)**

```
    GET https://outlook.office.com/api/beta/me/TaskFolders/?%24skipToken=x_zCAz5nm2dcGAFGk5qypL1PSyEAAC6cRncCAAAA HTTP/1.1
    Prefer: odata.maxpagesize=1
```


**サンプル 3 番目の応答データ (作業フォルダーを同期する)**

```
HTTP/1.1 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#me/TaskFolders/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGI5AAAunDbVAAA=')",
            "Id": "AAMkAGI5AAAunDbVAAA=",
            "ChangeKey": "PmebZ1wYAUaTmrKkvU9LIQAALqEkZA==",
            "Name":"Volunteer",
            "IsDefaultFolder":false,
            "ParentGroupKey": "db0823f2-93bd-4db6-8038-98bbc5f39a45"
        }
    ],
    "@odata.deltaLink":"https://outlook.office.com/api/beta/me/taskfolders/?%24deltaToken=x_zCBD5nm2dcGAFGk5qypL1PSyEAAC6cRncEAAAA"
}

```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: http://outlook.office.com/tasks.readwrite_

作業フォルダー、またはユーザーのメールボックス内のタスク フォルダーにタスクを同期することができます。 タスクを同期するフォルダーごとの操作は、すべてのタスクを既定のタスク フォルダーに同期するたとえば、 `Tasks`。 フォルダー階層内のタスクを同期するには、各タスクのフォルダーを個別に同期する必要があります。 タスクまたはタスク フォルダーを同期するプロセスと同様に、通常 の呼び出しは、それぞれ 2 つ以上の同期要求のラウンドを必要とします。 ABRUFEN 

<<<<<<< ヘッドが方法と同様に、GET メソッドを使用して[、フォルダー内のタスクを取得](#GetTasksInFolder)する、または[メールボックス内のフォルダーのタスクを取得する](#GetTaskFolders)には、 === 方法と同様に、GET メソッドを使用して[、フォルダー内のタスクを取得](#GetTasksInFolderV2)する、または[メールボックス内のフォルダーのタスクを取得する](#GetTaskFolders)には、 
>>>>>>> 特定の要求ヘッダーと_DeltaToken_や、 _SkipToken_該当する場合を含めることを除いてをステージングします。

**要求ヘッダー** 

- 指定する必要があります、`Prefer: odata.track-changes`を含むものを除く、すべての同期要求のヘッダー、 `skipToken` 、前回の同期要求に返されます。 最初の応答での調査、_優先順位で適用した: odata.track 変更_ヘッダーを確認するのには <<<<<<< ヘッドの同期を続行する前にリソースをサポートしています。 (の詳細については、`skipToken`で同期する場合はタスク、または[2 番目の応答データの仕事フォルダーのサンプル](#SyncTaskFoldersSampleSecondResponse)を使用する場合の[タスクの 2 番目の応答のデータをサンプル](#SyncTasksSampleSecondResponse)=======
リソースが開始する前に同期をサポートしています。 (の詳細については、`skipToken`で同期する場合はタスク、または[2 番目の応答データの仕事フォルダーのサンプル](#SyncTaskFoldersSampleSecondResponseV2)を使用する場合の[番目の応答のデータをサンプル タスクの 2](#SyncTasksSampleSecondResponseV2) 
>>>>>>> ステージング タスク フォルダーを同期します。
- 指定すること、`Prefer: odata.maxpagesize={x}`のタスク (またはタスク フォルダーを同期するかによって) の最大数を示すヘッダー各同期要求を返す。

同期の一般的なラウンドです。

1. GET-要求を行う 必須の最初の_選択: odata.track 変更_ヘッダー。 同期要求に対する初回の応答は、常に、 _DeltaToken_を返します。 (2 番目およびそれ以降の GET 要求とは異なる最初の GET 要求によって、 _DeltaToken_または前の応答で受信した_SkipToken_のいずれかを含むします。 )

2. 最初の応答が返された場合、_の設定で適用した: odata.track 変更_ヘッダー、リソースの同期を続行することができます。

  - 2 つ目の GET 要求を行います。 指定の_選択: odata.track 変更_を同期するのにはリソースの追加のインスタンスがあるかどうかを決定する最初の取得からヘッダーと_DeltaToken_が返されます。 2 番目の要求を返します追加のインスタンスとするか、 _SkipToken_がある場合複数のインスタンスが使用可能なまたは_DeltaToken_を停止する場合、最後のインスタンスが同期された場合。

  - の呼び出しを送信し、前の呼び出しから返される_SkipToken_を含む同期を続行します。 ABRUFEN 同期が完了することを示すの_DeltaToken_ 、_@odata.deltaLink_ヘッダーを含む最終的な応答を取得する場合を停止します。


見て初期とそれ以降の呼び出しの構文で同期のラウンドです。


**タスク フォルダーにタスクを同期するには。**

最初の要求。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/TaskFolders('{folder_id}')/Tasks
```


2 番目の要求、またはそれ以降のラウンドの最初の要求。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/TaskFolders('{folder_id}')/Tasks/?$deltatoken={delta_token}
```


3 つ目以降の要求で同じラウンドです。 含む応答を取得するときに停止、`@odata.deltaLink`を持つヘッダー、`deltaToken`もう一度。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/TaskFolders('{folder_id}')/Tasks/?$skiptoken={skip_token}
```


**メールボックス内のタスク フォルダーを同期するには**

最初の要求。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/TaskFolders
```


2 番目の要求、またはそれ以降のラウンドの最初の要求。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/TaskFolders/?$deltatoken={delta_token}
```


3 つ目以降の要求で同じラウンドです。 含む応答を取得するときに停止、`@odata.deltaLink`を持つヘッダー、`deltaToken`もう一度。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/TaskFolders/?$skiptoken={skip_token}
```




**パラメーター**

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_ヘッダーのパラメーター_|
|好む|OData.Track 変更|要求が同期要求であることを示します。 ラウンドの最初の 2 つの GET 要求に対して必要です。|
|好む|OData.MaxPageSize|各応答で返されるメッセージの数を設定します。 省略可能です。|
|_URL-パラメーター_|
|deltaToken|string|`deltaToken`前の同期応答の@odata.deltaLinkの値の一部として文字列が返されます。|
|skipToken|string|`skipToken`前の同期応答の@odata.nextLinkの値の一部として文字列が返されます。 |


**メモ** 

- 指定すると、 `Prefer: odata.track-changes` 、最初の要求に応答が同期をサポートしている場合、応答が含まれます`Preference-applied: odata.track-changes`ヘッダーにします。
- 、サポートされていないリソースを同期しようとしたかどうか、または初期同期要求でない場合は表示されません、 `Preference-applied` 、応答のヘッダーです。
- 優れたレスポンス ・ タイムのプロパティを取得するだけのシナリオに便利です $select クエリ パラメーターを使用します。  
- $Filter、$ Orderby、$ Search、および $top クエリのパラメーターを使用することはできません。  


**応答本文**

- タスクを同期する場合: コレクション内の要求された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)オブジェクト。

- タスク フォルダーを同期する場合: コレクション内の要求された[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)オブジェクトです。

オブジェクトの数に設定された値に依存します`Prefer: odata.maxpagesize`要求ヘッダー。


**使用例**

2 つの例を次に示します。
- [タスク フォルダーにタスクを同期します。](#SyncTasksSampleInitialRequestV2)
- [タスク フォルダーを同期](#SyncTaskFoldersSampleInitialRequestV2)します。 

それぞれの例は、最初と 2 番目の同期要求を示しています。 
- 各要求は、指定`Prefer: odata.maxpagesize=1`1 つだけオブジェクトを取得する (タスクまたはタスクのフォルダーをそれぞれ) 、時にします。
- 1 つの同期オブジェクトは、初期の応答が返されます、`deltaLink`と`deltaToken`。 
- 2 番目の要求を使用している`deltatoken`。 1 つの同期オブジェクトは、2 番目の応答が返されます、`nextLink`と`skipToken`。 

GET-の呼び出しで使用して、 同期プロセスを反復処理し、次の`skipToken`を含む同期応答を取得するまでに、前回の同期要求から返される、`deltaLink`と`deltaToken`次のよう。
```
"@odata.deltaLink": “https://outlook.office.com/api/v2.0/me/TaskFolders('AQMkAGMw80AAAIBEgAAAA==')/Tasks/?%24deltaToken=294a8f04cc0345c5ae093d484629e186”
```

このような場合、同期の現在のラウンドが完了しました。 保存、`deltaToken`の同期は、次のラウンドにします。 


<a name="SyncTasksSampleInitialRequestV2"></a>

**サンプルの最初の要求 (タスクの同期)**

```
<<<<<<< HEAD
    GET https://outlook.office.com/api/beta/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks HTTP/1.1
=======
    GET https://outlook.office.com/api/v2.0/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks HTTP/1.1
>>>>>>> staging
    Prefer: odata.maxpagesize=1
  Prefer: odata.track-changes
```

**サンプルの初期応答データ (タスクの同期)**

```
HTTP/1.1 200 OK
Preference-Applied: odata.track-changes

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#me/TaskFolders('AQMkAGMwAAAIBEgAAAA%3D%3D')/Tasks",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('47ec4680-f443-4f9c-a3e5-f7660f0aceae@b4ffe6c0-e717-4104-acd1-e9dfe38ff5f9')/Tasks('AAMkAGMwQsKVevNAAAG1VNmAAA=')",
      "@odata.etag": "W/\"3JfzyLwJe0mPNcULClXrzQAABtYBDw==\"",
      "Id": "AAMkAGMwQsKVevNAAAG1VNmAAA=",
      "CreatedDateTime": "2016-02-29T20:51:25.2226052Z",
      "LastModifiedDateTime": "2016-02-29T20:51:25.2538576Z",
      "ChangeKey": "3JfzyLwJe0mPNcULClXrzQAABtYBDw==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTime": null,
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkAGMwAAAIBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": null,
      "Status": "NotStarted",
      "Subject": "another task"
    }
  ],
  "@odata.deltaLink": "https://outlook.office.com/api/v2.0/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks/?%24deltatoken=175e2e04482e431ea96e89145c212f8c"
}
```

**サンプルの 2 番目の要求 (タスクの同期)**

```
<<<<<<< HEAD
    GET https://outlook.office.com/api/beta/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks/?%24deltatoken=175e2e04482e431ea96e89145c212f8c HTTP/1.1
=======
    GET https://outlook.office.com/api/v2.0/me/TaskFolders('AQMkAGMwAAAIBEgAAAA==')/Tasks/?%24deltatoken=175e2e04482e431ea96e89145c212f8c HTTP/1.1
>>>>>>> staging
    Prefer: odata.maxpagesize=1
  Prefer: odata.track-changes
```

<a name="SyncTasksSampleSecondResponseV2"></a>

**サンプル 2 番目の応答データ (タスクを同期する)**

```
HTTP/1.1 200 OK

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#me/TaskFolders('AQMkAGMwAAAIBEgAAAA%3D%3D')/Tasks/$delta",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('47ec4680-f443-4f9c-a3e5-f7660f0aceae@b4ffe6c0-e717-4104-acd1-e9dfe38ff5f9')/Tasks('AAMkAGMwQsKVevNAAAG1VNlAAA=')",
      "@odata.etag": "W/\"3JfzyLwJe0mPNcULClXrzQAABtYBDQ==\"",
      "Id": "AAMkAGMwQsKVevNAAAG1VNlAAA=",
      "CreatedDateTime": "2016-02-29T20:51:02.5955351Z",
      "LastModifiedDateTime": "2016-02-29T20:51:03.9703679Z",
      "ChangeKey": "3JfzyLwJe0mPNcULClXrzQAABtYBDQ==",
      "Categories": [ ],
      "AssignedTo": null,
      "Body": {
        "ContentType": "Text",
        "Content": ""
      },
      "CompletedDateTime": null,
      "DueDateTimeTime": null,
      "Importance": "Normal",
      "IsReminderOn": false,
      "Owner": "Administrator",
      "ParentFolderId": "AQMkAGMwAAAIBEgAAAA==",
      "Recurrence": null,
      "ReminderDateTime": null,
      "Sensitivity": "Normal",
      "StartDateTime": null,
      "Status": "NotStarted",
      "Subject": "another task"
    }
  ],
  "@odata.nextLink": "https://outlook.office.com/api/v2.0/me/TaskFolders('AQMkAGMw80AAAIBEgAAAA==')/Tasks/?%24skipToken=0fbce2031e844a2f9d13d8bee5ebe2c6"
}
```

GET-の呼び出しで使用して、 タスクの同期を続行し、次の`skiptoken`で返される`@odata.nextLink`の最終的な応答が含まれるまで、前の応答、`@odata.deltaLink`と`deltaToken`。 保存、`deltaToken`の同期は、次のラウンドにします。


<a name="SyncTaskFoldersSampleInitialRequestV2"></a>

**サンプルの最初の要求 (作業フォルダーを同期する)**

```
<<<<<<< HEAD
    GET https://outlook.office.com/api/beta/me/TaskFolders HTTP/1.1
=======
    GET https://outlook.office.com/api/v2.0/me/TaskFolders HTTP/1.1
    Prefer: odata.maxpagesize=1
    Prefer: odata.track-changes
```

**サンプルの初期応答データ (タスク フォルダーを同期する)**

```
HTTP/1.1 200 OK
Preference-Applied: odata.track-changes

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#me/TaskFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGJiAAAAAAESAAA=')",
            "Id": "AAMkAGJiAAAAAAESAAA=",
            "ChangeKey": "PG2a661l00Cy9qH3YxmDfwAAAAAAPA==",
            "Name": "Tasks",
            "IsDefaultFolder":true,
            "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
        }
    ],
    "@odata.deltaLink": "https://outlook.office.com/api/v2.0/me/TaskFolders/?%24deltatoken=OyZKBDxtmuutZdNAsvah92MZg38AAAAAZwkBAAAA"
}
```

**サンプルの 2 番目の要求 (作業フォルダーを同期する)**

```
    GET https://outlook.office.com/api/v2.0/me/TaskFolders/?%24deltatoken=OyZKBDxtmuutZdNAsvah92MZg38AAAAAZwkBAAAA HTTP/1.1
    Prefer: odata.maxpagesize=1
    Prefer: odata.track-changes
```

<a name="SyncTaskFoldersSampleSecondResponseV2"></a>

**サンプル 2 番目の応答データ (作業フォルダーを同期する)**

```
HTTP/1.1 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#me/TaskFolders/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGI5AAAunDbWAAA=')",
            "Id": "AAMkAGI5AAAunDbWAAA=",
            "ChangeKey": "PmebZ1wYAUaTmrKkvU9LIQAALqEkaw==",
            "Name": "Bingo",
            "IsDefaultFolder":false,
            "ParentGroupKey": "db0823f2-93bd-4db6-8038-98bbc5f39a45"
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/v2.0/me/TaskFolders/?%24skipToken=x_zCAz5nm2dcGAFGk5qypL1PSyEAAC6cRncCAAAA"
}

```

GET-の呼び出しで使用して、 同期を続行し、次の`skiptoken`で返される`@odata.nextLink`最終的な応答が含まれるまで、前の応答の`@odata.deltaLink`と`deltaToken`。 この例では、3 番目の要求が返されます、`deltaToken`の同期は、このラウンドの完了とします。


**3 サンプルの 番目の要求 (作業フォルダーを同期する)**

```
    GET https://outlook.office.com/api/v2.0/me/TaskFolders/?%24skipToken=x_zCAz5nm2dcGAFGk5qypL1PSyEAAC6cRncCAAAA HTTP/1.1
>>>>>>> staging
    Prefer: odata.maxpagesize=1
    Prefer: odata.track-changes
```


**サンプル 3 番目の応答データ (作業フォルダーを同期する)**

```
HTTP/1.1 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#me/TaskFolders/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGI5AAAunDbVAAA=')",
            "Id": "AAMkAGI5AAAunDbVAAA=",
            "ChangeKey": "PmebZ1wYAUaTmrKkvU9LIQAALqEkZA==",
            "Name":"Volunteer",
            "IsDefaultFolder":false,
            "ParentGroupKey": "db0823f2-93bd-4db6-8038-98bbc5f39a45"
        }
    ],
    "@odata.deltaLink":"https://outlook.office.com/api/v2.0/me/taskfolders/?%24deltaToken=x_zCBD5nm2dcGAFGk5qypL1PSyEAAC6cRncEAAAA"
}

```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="CreateTaskFolders"> </a>
##タスク フォルダーを作成します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスク フォルダーを作成します。 

既定のタスク グループでタスク フォルダーを作成することができます (`My Tasks`) のユーザーのメールボックス。

```no-highlight
POST https://outlook.office.com/api/beta/me/taskfolders
```

または、指定したタスク グループの下のタスク フォルダーを作成することができます。
```no-highlight
POST https://outlook.office.com/api/beta/me/taskgroups('{group_id}')/taskfolders
```

要求の本体を作成する[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)の JSON 表現を指定します。

**応答**

成功状態コード: 201 作成されました

応答本文: 作成された[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)。


**要求のサンプル**

という名前のタスク フォルダーを作成する例を次`Volunteer`[仕事] で既定値 (`My Tasks`) ユーザーのメールボックスの。
```
POST https://outlook.office.com/api/beta/me/taskfolders 
Content-Type: application/json

{
  "Name": "Volunteer"
}
```

**応答の例**

```
Status code: 201

{
<<<<<<< HEAD
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#me/TaskFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGJiAAAAAAESAAA=')",
            "Id": "AAMkAGJiAAAAAAESAAA=",
            "ChangeKey": "PG2a661l00Cy9qH3YxmDfwAAAAAAPA==",
            "Name": "Tasks",
            "IsDefaultFolder":true,
            "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
        }
    ],
    "@odata.deltaLink": "https://outlook.office.com/api/beta/me/TaskFolders/?%24deltatoken=OyZKBDxtmuutZdNAsvah92MZg38AAAAAZwkBAAAA"
=======
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/TaskFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPWAAA=')",
  "Id": "AAMkADIyAAAhrbPWAAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAGig==",
  "IsDefaultFolder": false,
  "Name": "Volunteer",
  "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
>>>>>>> staging
}
```

**要求のサンプル**

次の例では、作業フォルダーと呼ばれる`Cooking`で指定したタスク グループ。
```
<<<<<<< HEAD
    GET https://outlook.office.com/api/beta/me/TaskFolders/?%24deltatoken=OyZKBDxtmuutZdNAsvah92MZg38AAAAAZwkBAAAA HTTP/1.1
    Prefer: odata.maxpagesize=1
    Prefer: odata.track-changes
```
=======
投稿の Https://outlook.office.com/api/beta/me/taskgroups('AAMkADIyAAAhrbe-AAA') と Taskfolders のコンテンツの種類: アプリケーションまたは Json
>>>>>>> ステージング

{"Name": 「料理」}
```

**Sample response**

```
状態コード: 201

{<<<<<<<ヘッド"@odata.context":「https://outlook.office.com/api/beta/$のメタデータの #me/TaskFolders / $デルタ」、「値」: [{"@odata.id":"https://outlook.office.com/api/beta/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGI5AAAunDbWAAA=')"、"Id":"AAMkAGI5AAAunDbWAAA = 」、 "変更のキー": 」PmebZ1wYAUaTmrKkvU9LIQAALqEkaw = 」「名前」、 =: "Angelbilder"、"IsDefaultFolder": false、"ParentGroupKey":"db0823f2-93bd-4db6-8038-98bbc5f39a45"}]、"@odata.nextLink":"https://outlook.office.com/api/beta/me/TaskFolders/?%24skipToken=x_zCAz5nm2dcGAFGk5qypL1PSyEAAC6cRncCAAAA" ==="@odata.context":」https://outlook.office.com/api/beta/$のメタデータ #Me / TaskGroups ("AAMkADIyAAAhrbe AAA %d 3") /TaskFolders/$ のエンティティ」、"@odata.id":」https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPXAAA=')"、"Id":"AAMkADIyAAAhrbPXAAA = "、" 変更のキー":" hmM7Eb/jgEec8l3 + GkJEawAAIbAOlA = "、" IsDefaultFolder = ": False、「名前」:「調理」、"ParentGroupKey":"63d640cf-946f-4734-9c29-60dda7b76acb"
>>>>>>> ステージング。
```

<<<<<<< HEAD
Continue synchronizing and use in the next GET call the `skiptoken` returned in `@odata.nextLink` of the previous response, 
until the final response contains an `@odata.deltaLink` and a `deltaToken`. In this example, the third request returns a `deltaToken`
and synchronizing is complete for this round.


**Sample third request  (synchronize task folders)**

```
    GET https://outlook.office.com/api/beta/me/TaskFolders/?%24skipToken=x_zCAz5nm2dcGAFGk5qypL1PSyEAAC6cRncCAAAA HTTP/1.1
    Prefer: odata.maxpagesize=1
```

<a name="SyncTaskFoldersSampleSecondResponse"></a>

**Sample third response data  (synchronize task folders)**

```
HTTP/1.1 200 OK

{"@odata.context":「https://outlook.office.com/api/beta/$のメタデータの #me/TaskFolders / $デルタ」、「値」: [{"@odata.id":"https://outlook.office.com/api/beta/Users('5bcd7334-a6c5-4f95-a370-319e077dfe10@e288a0d0-ab74-431b-9699-a3721aabb08f')/TaskFolders('AAMkAGI5AAAunDbVAAA=')"、"Id":"AAMkAGI5AAAunDbVAAA = "、" 変更のキー ": 」PmebZ1wYAUaTmrKkvU9LIQAALqEkZA = = 」「名前」、:「ボランティア」、"IsDefaultFolder":false、"ParentGroupKey":"db0823f2-93bd-4db6-8038-98bbc5f39a45"}]、"@odata.deltaLink":"https://outlook.office.com/api/beta/me/taskfolders/?%24deltaToken=x_zCBD5nm2dcGAFGk5qypL1PSyEAAC6cRncEAAAA"}

```

=======
>>>>>>> staging

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**Required scope**: https://outlook.office.com/tasks.readwrite_

Create a task folder. 

You can create a task folder in the default task group (`My Tasks`) of the user's mailbox:

```no-highlight
POST https://outlook.office.com/api/v2.0/me/taskfolders
```

または、指定したタスク グループの下のタスク フォルダーを作成することができます。
```no-highlight
POST https://outlook.office.com/api/v2.0/me/taskgroups('{group_id}')/taskfolders
```

要求の本体を作成する[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)の JSON 表現を指定します。

**応答**

成功状態コード: 201 作成されました

応答本文: 作成された[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)。


**要求のサンプル**

という名前のタスク フォルダーを作成する例を次`Volunteer`[仕事] で既定値 (`My Tasks`) ユーザーのメールボックスの。
```
POST https://outlook.office.com/api/v2.0/me/taskfolders 
Content-Type: application/json

{
  "Name": "Volunteer"
}
```

**応答の例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/TaskFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPWAAA=')",
  "Id": "AAMkADIyAAAhrbPWAAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAGig==",
  "IsDefaultFolder": false,
  "Name": "Volunteer",
  "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
}
```

**要求のサンプル**

次の例では、作業フォルダーと呼ばれる`Cooking`で指定したタスク グループ。
```
<<<<<<< HEAD
POST https://outlook.office.com/api/beta/me/taskgroups('AAMkADIyAAAhrbe-AAA')/taskfolders 
=======
POST https://outlook.office.com/api/v2.0/me/taskgroups('AAMkADIyAAAhrbe-AAA')/taskfolders 
>>>>>>> staging
Content-Type: application/json

{
  "Name": "Cooking"
}
```

**応答の例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/TaskGroups('AAMkADIyAAAhrbe-AAA%3D')/TaskFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPXAAA=')",
  "Id": "AAMkADIyAAAhrbPXAAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAOlA==",
  "IsDefaultFolder": false,
  "Name": "Cooking",
  "ParentGroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
}
```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="GetTaskFolders"> </a>
##タスク フォルダーを取得します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.read_

複数の作業フォルダーを取得します。 

ユーザーのメールボックス内のすべての作業フォルダーを取得できます。

```no-highlight
GET https://outlook.office.com/api/beta/me/taskfolders
```

または、特定のタスク グループでタスク フォルダーを取得できます。
```no-highlight
GET https://outlook.office365.com/api/beta/me/taskgroups('{group_id}')/taskfolders 
```



**応答**

成功状態コード: 200 OK

応答本文: [Taskfolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)コレクションです。


**要求のサンプル**

次の例では、ユーザーのメールボックス内のすべての作業フォルダーを取得します。
```
GET https://outlook.office.com/api/beta/me/taskfolders
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/TaskFolders",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAAABrJAAA=')",
      "Id": "AAMkADIyAAAAABrJAAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAAAAeAA==",
      "IsDefaultFolder": false,
      "Name": "Monthly tasks",
      "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
    },
    {
      "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAAAAESAAA=')",
      "Id": "AAMkADIyAAAAAAESAAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAAAAAPA==",
      "IsDefaultFolder": true,
      "Name": "Tasks",
      "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
    }
  ]
}
```

次の例では、指定したタスク グループですべての作業フォルダーを取得します。
```
GET https://outlook.office365.com/api/beta/me/taskgroups('AAMkADIyAAAhrbe-AAA=')/taskfolders
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office365.com/api/beta/$metadata#Me/TaskGroups('AAMkADIyAAAhrbe-AAA%3D')/TaskFolders",
  "value": [
    {
      "@odata.id": "https://outlook.office365.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPXAAA=')",
      "Id": "AAMkADIyAAAhrbPXAAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAOlA==",
      "IsDefaultFolder": false,
<<<<<<< HEAD
=======
      "Name": "Cooking",
      "ParentGroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
    }
  ]
}
```

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.read_

複数の作業フォルダーを取得します。 

ユーザーのメールボックス内のすべての作業フォルダーを取得できます。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/taskfolders
```

または、特定のタスク グループでタスク フォルダーを取得できます。
```no-highlight
GET https://outlook.office365.com/api/v2.0/me/taskgroups('{group_id}')/taskfolders 
```



**応答**

成功状態コード: 200 OK

応答本文: [Taskfolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)コレクションです。


**要求のサンプル**

次の例では、ユーザーのメールボックス内のすべての作業フォルダーを取得します。
```
GET https://outlook.office.com/api/v2.0/me/taskfolders
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/TaskFolders",
  "value": [
    {
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAAABrJAAA=')",
      "Id": "AAMkADIyAAAAABrJAAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAAAAeAA==",
      "IsDefaultFolder": false,
      "Name": "Monthly tasks",
      "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
    },
    {
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAAAAESAAA=')",
      "Id": "AAMkADIyAAAAAAESAAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAAAAAPA==",
      "IsDefaultFolder": true,
      "Name": "Tasks",
      "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
    }
  ]
}
```

次の例では、指定したタスク グループですべての作業フォルダーを取得します。
```
GET https://outlook.office365.com/api/v2.0/me/taskgroups('AAMkADIyAAAhrbe-AAA=')/taskfolders
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office365.com/api/v2.0/$metadata#Me/TaskGroups('AAMkADIyAAAhrbe-AAA%3D')/TaskFolders",
  "value": [
    {
      "@odata.id": "https://outlook.office365.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPXAAA=')",
      "Id": "AAMkADIyAAAhrbPXAAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAOlA==",
      "IsDefaultFolder": false,
>>>>>>> staging
      "Name": "Cooking",
      "ParentGroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
    }
  ]
}
```

****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="UpdateTaskFolders"> </a>
##タスク フォルダーを更新します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスク フォルダーの書き込み可能なプロパティを更新します。

既定の作業フォルダーの**Namen**プロパティの値を変更することはできません`Tasks`。
 
タスクのフォルダー ID は、ユーザーのメールボックスに一意です。

```no-highlight
PATCH https://outlook.office.com/api/beta/me/taskfolders('{folder_id}')
```

要求の本文に[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)で更新するのには書き込み可能なプロパティの JSON の形式を指定します。

**応答**

成功状態コード: 200 OK

応答本文: 更新された[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)です。


**要求のサンプル**

次の例を [タスク] フォルダーの名前を変更する`Charity work`。
```
PATCH https://outlook.office.com/api/beta/me/taskfolders('AAMkADIyAAAhrbPWAAA=')
Content-Type: application/json

{
  "Name": "Charity work"
}
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/TaskFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPWAAA=')",
  "Id": "AAMkADIyAAAhrbPWAAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAKfQ==",
  "IsDefaultFolder": false,
<<<<<<< HEAD
=======
  "Name": "Charity work",
  "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
}
```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスク フォルダーの書き込み可能なプロパティを更新します。

既定の作業フォルダーの**Name**プロパティの値を変更することはできません`Tasks`。
 
タスクのフォルダー ID は、ユーザーのメールボックスに一意です。

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/taskfolders('{folder_id}')
```

要求の本文に[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)で更新するのには書き込み可能なプロパティの JSON の形式を指定します。

**応答**

成功状態コード: 200 OK

応答本文: 更新された[TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)です。


**要求のサンプル**

次の例を [タスク] フォルダーの名前を変更する`Charity work`。
```
PATCH https://outlook.office.com/api/v2.0/me/taskfolders('AAMkADIyAAAhrbPWAAA=')
Content-Type: application/json

{
  "Name": "Charity work"
}
```

**応答の例**

```
Status code: 200 OK

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/TaskFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskFolders('AAMkADIyAAAhrbPWAAA=')",
  "Id": "AAMkADIyAAAhrbPWAAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAKfQ==",
  "IsDefaultFolder": false,
>>>>>>> staging
  "Name": "Charity work",
  "ParentGroupKey": "0006f0b7-0000-0000-c000-000000000046"
}
```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="DeleteTaskFolders"> </a>
##タスク フォルダーを削除します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

指定したタスク フォルダーを削除します。

既定のタスク フォルダーを削除しようとしています`Tasks`HTTP 400 正しくない要求を返します。  

```no-highlight
DELETE https://outlook.office.com/api/beta/me/taskfolders('{folder_id}')
```


**応答**

成功状態コード: 204 コンテンツなし

応答本文: です。 [なし]


**要求のサンプル**

```
DELETE https://outlook.office365.com/api/beta/me/taskfolders('AAMkADIyAAAhrbPXAAA=')
```

**応答の例**

```
Status code: 204
```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

指定したタスク フォルダーを削除します。

既定のタスク フォルダーを削除しようとしています`Tasks`HTTP 400 正しくない要求を返します。  

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/taskfolders('{folder_id}')
```


**応答**

成功状態コード: 204 コンテンツなし

応答本文: です。 [なし]


**要求のサンプル**

```
DELETE https://outlook.office365.com/api/v2.0/me/taskfolders('AAMkADIyAAAhrbPXAAA=')
```

**応答の例**

```
Status code: 204
```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="CreateTaskGroups"> </a>
##タスク グループを作成します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

ユーザーのメールボックスでは、タスク グループを作成します。

```no-highlight
POST https://outlook.office.com/api/beta/me/taskgroups
```

要求の本体を作成する[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)の JSON 表現を指定します。

**応答**

成功状態コード: 201 作成されました

応答本文: 作成された[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)。


**要求のサンプル**

```
POST https://outlook.office.com/api/beta/me/taskgroups
Content-Type: application/json

{
  "Name": "Leisure tasks"
}
```

**応答の例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/TaskGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAAhrbe-AAA=')",
  "Id": "AAMkADIyAAAhrbe-AAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAGjg==".
  "IsDefaultGroup": false,
<<<<<<< HEAD
=======
  "Name": "Leisure tasks",
  "GroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
}
```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

ユーザーのメールボックスでは、タスク グループを作成します。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/taskgroups
```

要求の本体を作成する[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)の JSON 表現を指定します。

**応答**

成功状態コード: 201 作成されました

応答本文: 作成された[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)。


**要求のサンプル**

```
POST https://outlook.office.com/api/v2.0/me/taskgroups
Content-Type: application/json

{
  "Name": "Leisure tasks"
}
```

**応答の例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/TaskGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAAhrbe-AAA=')",
  "Id": "AAMkADIyAAAhrbe-AAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAGjg==".
  "IsDefaultGroup": false,
>>>>>>> staging
  "Name": "Leisure tasks",
  "GroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
}
```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="GetTaskGroups"> </a>
##タスク グループを取得します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

ユーザーのメールボックス内のすべてのタスク グループを取得します。

応答には常に既定のタスク グループが含まれています`My Tasks`、およびメールボックス内に作成されたその他のタスク グループ。

```no-highlight
GET https://outlook.office.com/api/beta/me/taskgroups
```


**応答**

成功状態コード: 200 OK

応答本文:[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)のコレクションです。


**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/taskgroups
```

**応答の例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office365.com/api/beta/$metadata#Me/TaskGroups",
  "value": [
    {
      "@odata.id": "https://outlook.office365.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAADJ5pYAAA=')",
      "Id": "AAMkADIyAAADJ5pYAAA=",
<<<<<<< HEAD
=======
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAInHxLA==",
      "IsDefaultGroup": true,
      "Name": "My Tasks",
      "GroupKey": "0006f0b7-0000-0000-c000-000000000046"
    },
    {
      "@odata.id": "https://outlook.office365.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAAhrbe-AAA=')",
      "Id": "AAMkADIyAAAhrbe-AAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAInHxKw==",
      "IsDefaultGroup": false,
      "Name": "Leisure Tasks",
      "GroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
    }
  ]
}

```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

ユーザーのメールボックス内のすべてのタスク グループを取得します。

応答には常に既定のタスク グループが含まれています`My Tasks`、およびメールボックス内に作成されたその他のタスク グループ。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/taskgroups
```


**応答**

成功状態コード: 200 OK

応答本文:[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)のコレクションです。


**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/taskgroups
```

**応答の例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office365.com/api/v2.0/$metadata#Me/TaskGroups",
  "value": [
    {
      "@odata.id": "https://outlook.office365.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAADJ5pYAAA=')",
      "Id": "AAMkADIyAAADJ5pYAAA=",
>>>>>>> staging
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAInHxLA==",
      "IsDefaultGroup": true,
      "Name": "My Tasks",
      "GroupKey": "0006f0b7-0000-0000-c000-000000000046"
    },
    {
<<<<<<< HEAD
      "@odata.id": "https://outlook.office365.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAAhrbe-AAA=')",
=======
      "@odata.id": "https://outlook.office365.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAAhrbe-AAA=')",
>>>>>>> staging
      "Id": "AAMkADIyAAAhrbe-AAA=",
      "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAInHxKw==",
      "IsDefaultGroup": false,
      "Name": "Leisure Tasks",
      "GroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
    }
  ]
}

```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<a name="UpdateTaskGroups"> </a>
##作業グループを更新します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスク グループの書き込み可能なプロパティを更新します。

```no-highlight
PATCH https://outlook.office.com/api/beta/me/taskgroups('{group_id}')
```

要求の本文に、[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)、**名前**プロパティのように更新するための書き込み可能なプロパティの JSON の形式を指定します。

**応答**

成功状態コード: 200 OK

応答本文: 更新された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。


**要求のサンプル**

次の例では、個人のタスク」を作業グループの名前を変更します。 既定のタスク グループ「自分のタスク」の名前を変更できないことに注意してください。

```
PATCH https://outlook.office.com/api/beta/me/taskgroups('AAMkADIyAAAhrbe-AAA=')
Content-Type: application/json

{
  "Name": "Personal Tasks"
}
```

**応答の例**

```
Status code: 200 

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/TaskGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAAhrbe-AAA=')",
  "Id": "AAMkADIyAAAhrbe-AAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAGjw==",
  "IsDefaultGroup": false,
  "Name": "Personal Tasks",
<<<<<<< HEAD
=======
  "GroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
}
```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

タスク グループの書き込み可能なプロパティを更新します。

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/taskgroups('{group_id}')
```

要求の本文に、[タスク グループ](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource)、**名前**プロパティのように更新するための書き込み可能なプロパティの JSON の形式を指定します。

**応答**

成功状態コード: 200 OK

応答本文: 更新された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。


**要求のサンプル**

次の例では、個人のタスク」を作業グループの名前を変更します。 既定のタスク グループ「自分のタスク」の名前を変更できないことに注意してください。

```
PATCH https://outlook.office.com/api/v2.0/me/taskgroups('AAMkADIyAAAhrbe-AAA=')
Content-Type: application/json

{
  "Name": "Personal Tasks"
}
```

**応答の例**

```
Status code: 200 

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/TaskGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('dc2d952a-78ff-4609-b3ae-eb66271747bf@8638a6dc-2d66-40dc-aecb-b2436ec47fc0')/TaskGroups('AAMkADIyAAAhrbe-AAA=')",
  "Id": "AAMkADIyAAAhrbe-AAA=",
  "ChangeKey": "hmM7Eb/jgEec8l3+gkJEawAAIbAGjw==",
  "IsDefaultGroup": false,
  "Name": "Personal Tasks",
>>>>>>> staging
  "GroupKey": "63d640cf-946f-4734-9c29-60dda7b76acb"
}
```


****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<a name="DeleteTaskGroups"> </a>
##タスク グループを削除します。<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

指定したタスク グループを削除します。 

既定のタスク グループを削除しようとしています`My Tasks`HTTP 400 正しくない要求を返します。  

```no-highlight
DELETE https://outlook.office.com/api/beta/me/taskgroups('{group_id}')
```


**応答**

成功状態コード: 204 コンテンツなし

応答本文: 更新された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。


**要求のサンプル**

```
DELETE https://outlook.office365.com/api/beta/me/taskgroups('AAMkADIyAAAhrbe-AAA=')
<<<<<<< HEAD
=======
```

**応答の例**

```
Status code: 204
```

****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**スコープが必要です**: https://outlook.office.com/tasks.readwrite_

指定したタスク グループを削除します。 

既定のタスク グループを削除しようとしています`My Tasks`HTTP 400 正しくない要求を返します。  

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/taskgroups('{group_id}')
```


**応答**

成功状態コード: 204 コンテンツなし

応答本文: 更新された[タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)です。


**要求のサンプル**

```
DELETE https://outlook.office365.com/api/v2.0/me/taskgroups('AAMkADIyAAAhrbe-AAA=')
>>>>>>> staging
```

**応答の例**

```
Status code: 204
```

****

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

- [Outlook の REST-API を使用します。](..\api\use-outlook-rest-api.md)

- [メールの残りの部分の Api を参照します。](..\api\mail-rest-operations.md)

- [REST-Api の予定表を参照します。](..\api\calendar-rest-operations.md)

- [REST-Api リファレンスを取引先担当者します。](..\api\contacts-rest-operations.md)

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

- [Outlook の REST-API を使用します。](..\api\use-outlook-rest-api.md)

- [メールの残りの部分の Api を参照します。](..\api\mail-rest-operations.md)

- [REST-Api の予定表を参照します。](..\api\calendar-rest-operations.md)

- [REST-Api リファレンスを取引先担当者します。](..\api\contacts-rest-operations.md)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]




