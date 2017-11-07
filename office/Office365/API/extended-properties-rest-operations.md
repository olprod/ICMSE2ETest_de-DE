<<<<<<< ヘッド ms です。 TocTitle: Outlook の拡張プロパティ REST-API-リファレンス (プレビュー) タイトル: Outlook の拡張プロパティ REST-API-リファレンス (プレビュー) 説明: 拡張プロパティを Office 365 と Outlook.com の REST-API-を使用して、動的に作成し、拡張のカスタム データを格納するプロパティを取得する方法を参照します。 MS-です。 ContentId: 69a1ae02-3060-40c6-ad5e-2c23b0f00827 ms.topic: ms.date を参照 (API): 2016 年 6 月 29 日

<a name=""></a>=======
---
MS-です。 TOCTitle: Outlook の拡張プロパティ REST API リファレンス タイトル: Outlook の拡張プロパティ REST API リファレンスの説明: 拡張プロパティを Office 365 と Outlook.com の REST-API-を使用して、動的に作成し、拡張のカスタム データを格納するプロパティを取得する方法を参照します。 MS-です。 ContentId: 69a1ae02-3060-40c6-ad5e-2c23b0f00827 ms.date: 2016 年 9 月 19 日

---

>>>>>>> ステージング[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="a-nameoutlook-extended-properties-rest-api-referenceaoutlook-api-"></a><a name="outlook-extended-properties-rest-api-reference"></a>Outlook の拡張プロパティの他の API リファレンス

[!INCLUDE [Add the Outlook REST API filters--v2 default](../includes/controls/addOutlookversion_v2default_v1disabled.html)]


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


 _**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

<p class="previewnote">ドキュメントのこのバージョンでは、Outlook を拡張プロパティ REST-API のプレビューについて説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 可能な場合、バージョン 2.0 は現在推奨されるバージョンです。</p>

Outlook 拡張プロパティの REST API は、カスタム データを格納するアプリケーションし、これらのプロパティは、 _REST-API の Outlook メタデータで公開されていない_ときの Outlook MAPI-プロパティのカスタム データにアクセスするための[フォールバック メカニズム](#ExtendedPropsOrDataExtensions)を提供します。 プロパティの拡張 API を使用して、格納したり、メッセージ、メールのフォルダー、イベント、予定表、連絡先、そのようなカスタム データを取得するには  
フォルダー、タスク、またはログインしているユーザーのアカウントでタスク フォルダーにお問い合わせください。 アカウントは、Office 365 または Microsoft アカウント (Hotmail.com、Live.com、MSN.com、Outlook.com、Passport.com) に配置できます。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。 

**API のベータ版では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

 _**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

Outlook 拡張プロパティの REST API は、カスタム データを格納するアプリケーションし、これらのプロパティは、 _REST-API の Outlook メタデータで公開されていない_ときの Outlook MAPI-プロパティのカスタム データにアクセスするための[フォールバック メカニズム](#ExtendedPropsOrDataExtensions)を提供します。 プロパティの拡張 API を使用して、格納したり、メッセージ、メールのフォルダー、イベント、予定表、連絡先、そのようなカスタム データを取得するには  
フォルダー、タスク、またはログインしているユーザーのアカウントでタスク フォルダーにお問い合わせください。 アカウントは、Office 365 または Microsoft アカウント (Hotmail.com、Live.com、MSN.com、Outlook.com、Passport.com) に配置できます。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。 

**API のバージョン 2.0 では関係ないですか?** 右上のコントロールを使用し、使用バージョンを選択します。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


## <a name="a-nameusing-the-extended-properties-rest-apiarest-api-"></a><a name="using-the-extended-properties-rest-api"></a>REST-API の拡張プロパティを使用してください。

<a name="ExtendedPropsOrDataExtensions"></a>

###<a name="a-nameextended-properties-or-data-extensionsa"></a><a name="extended-properties-or-data-extensions"></a>拡張プロパティ、またはデータの拡張機能ですか。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

REST-API の Outlook メタデータを通じて公開されていない Outlook MAPI-プロパティのカスタムのデータにアクセスする必要がある場合にのみ、拡張プロパティ、およびこの REST API を使用します。 ほとんどのシナリオでは、ユーザーのメールボックス内のアイテムのカスタム データを格納および[API für Office 365 のデータ拡張機能およびその他の](..\api\extensions-rest-operations.md)を使用してください。 メタデータを公開するプロパティを確認することができます`https://outlook.office.com/api/{version}/$metadata`、置き換えて {バージョン} v2. 0 やベータ版などで、任意のバージョンに対応します。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

REST-API の Outlook メタデータを通じて公開されていない Outlook MAPI-プロパティのカスタムのデータにアクセスする必要がある場合にのみ、拡張プロパティ、およびこの REST API を使用します。 ほとんどのシナリオでは、ユーザーのメールボックス内のアイテムのカスタム データを格納および[API für Office 365 のデータ拡張機能およびその他の](..\api\extensions-rest-operations.md)を使用してください。 メタデータを公開するプロパティを確認することができます`https://outlook.office.com/api/{version}/$metadata`、置き換えて {バージョン} v2. 0 やベータ版などで、任意のバージョンに対応します。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



###<a name="a-nameauthenticationa"></a><a name="authentication"></a>認証

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

他の[Outlook の REST-API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)を拡張プロパティ、API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 プロパティの拡張 API では、特定の操作を続行するには、この点に留意してください。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

他の[Outlook の REST-API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)を拡張プロパティ、API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 プロパティの拡張 API では、特定の操作を続行するには、この点に留意してください。


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


<a name="SupportedResources"></a>

###<a name="a-namesupported-rest-resourcesa"></a><a name="supported-rest-resources"></a>サポートされている他のリソース

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

拡張プロパティを作成する次のリソースのインスタンス。 
- [メッセージ](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)
- [イベント](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)
- [連絡先](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)
- [タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)
- [MailFolder](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)
- [予定表](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource)
- [ContactFolder](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)
- [TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)

Office 365 または Outlook.com には、サインインしているユーザーのメールボックスのリソースである必要があります。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

拡張プロパティを作成する次のリソースのインスタンス。 
- [メッセージ](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)
- [イベント](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)
- [連絡先](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)
- [タスク](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource)
- [MailFolder](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)
- [予定表](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource)
- [ContactFolder](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)
- [TaskFolder](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource)

Office 365 または Outlook.com には、サインインしているユーザーのメールボックスのリソースである必要があります。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




###<a name="a-nameurl-parametersaurl-"></a><a name="url-parameters"></a>URL-パラメーター

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

残りのパラメーターでこの資料の次の ID を使用してプレース ホルダーの例では、Url を要求します。 拡張機能を作成するリソースのインスタンスの ID を指定する必要があります。

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|calendar_id|string|カレンダーの id。 |
|contact_id|string|連絡先の id。 |
|contactFolder_id|string|連絡先フォルダーの id。 |
|event_id|string|イベント-Id です。 |
|mailFolder_id|string|メール フォルダーの id。 |
|メッセージ-id|string|メッセージ id。 |
|propertyId_value|string|**PropertyId**値はいずれかの[形式がサポートされている](#ExtendedPropertyIdFormats)します。|
|プロパティ _ 値|string|拡張プロパティの値です。|
|TASK_ID|string|タスクの id。|
|taskFolder_id|string|タスク フォルダーの id。|


Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

残りのパラメーターでこの資料の次の ID を使用してプレース ホルダーの例では、Url を要求します。 拡張機能を作成するリソースのインスタンスの ID を指定する必要があります。

|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|calendar_id|string|カレンダーの id。 |
|contact_id|string|連絡先の id。 |
|contactFolder_id|string|連絡先フォルダーの id。 |
|event_id|string|イベント-Id です。 |
|mailFolder_id|string|メール フォルダーの id。 |
|メッセージ-id|string|メッセージ id。 |
|propertyId_value|string|**PropertyId**値はいずれかの[形式がサポートされている](#ExtendedPropertyIdFormats)します。|
|プロパティ _ 値|string|拡張プロパティの値です。|
|TASK_ID|string|タスクの id。|
|taskFolder_id|string|タスク フォルダーの id。|


Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




****

## <a name="a-nameoverviewa"></a><a name="overview"></a>概要

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

動的に作成し、エンティティ インスタンスの_拡張プロパティ_にデータを格納することができます。 (1 同じ型の つまたは複数の値を格納するかどうかによって、 [SingleValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#SingleValueLegacyExtendedPropertyResource)、または[MultiValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#MultiValueLegacyExtendedPropertyResource)としての拡張プロパティを作成できます。

各タイプの**PropertyId**でプロパティを識別し、**値**のデータを格納します。 

**PropertyId**を使用すると、拡張プロパティ、特定のエンティティ インスタンスを取得またはそのプロパティを持つすべてのインスタンスを取得するプロパティを拡張する単一値にフィルターを適用します。 

**メモ**1 回の呼び出しで特定のインスタンスのすべての拡張プロパティを取得するのには、REST API を使うことはできません。  

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

動的に作成し、エンティティ インスタンスの_拡張プロパティ_にデータを格納することができます。 (1 同じ型の つまたは複数の値を格納するかどうかによって、 [SingleValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#SingleValueLegacyExtendedPropertyResource_v2)、または[MultiValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#MultiValueLegacyExtendedPropertyResource_v2)としての拡張プロパティを作成できます。

各タイプの**PropertyId**でプロパティを識別し、**値**のデータを格納します。 

**PropertyId**を使用すると、拡張プロパティ、特定のエンティティ インスタンスを取得またはそのプロパティを持つすべてのインスタンスを取得するプロパティを拡張する単一値にフィルターを適用します。 

**メモ**1 回の呼び出しで特定のインスタンスのすべての拡張プロパティを取得するのには、REST API を使うことはできません。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




<a name="ExtendedPropertyIdFormats"></a>

### <a name="a-namepropertyid-formatsapropertyid-"></a><a name="propertyid-formats"></a>PropertyId の形式

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

単一値または複数値の拡張プロパティを作成する場合は、数値識別子、または文字列の名前と値またはプロパティの値の実際の型に基づいて、2 つの形式のいずれかで**PropertyId**を指定できます。 REST-API メタデータで公開されていない MAPI プロパティを定義するほとんどの場合に拡張プロパティがあるために、対応する MAPI プロパティが[MAPI プロパティ識別子](https://msdn.microsoft.com/en-us/library/office/cc815528.aspx)の文字の文字列または数値の値を使うかどうかを選択する形式が反映されます。 間動作して、わかりやすくするため、Outlook の プロパティ識別子と GUID など、既存の MAPI プロパティに拡張プロパティをマップする必要がある情報を検索できます\[MS OXPROPS\]マイクロソフト、 [「Exchange Server プロトコル マスター プロパティ] ボックスの一覧」] です。 (https://msdn.microsoft.com/en-us/library/cc433490%28v=exchg.80%29.aspx)

**メモ *** PropertyId**の 1 つの形式を選択した後、その形式のみで、その拡張プロパティをアクセスすること。


**拡張プロパティを単一値の有効な PropertyId の形式**

|**形式**|**使用例**|**説明**|
|:---------|:----------|:--------------|
| [*{タイプ}, {Guid} **名前** Name*] | ```"String {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | と、名前でプロパティを識別します。 、属している名前空間 (GUID)         |
| [ *Id* *{Id}**{タイプ}, {Guid} *]     | ```"Integer {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8012"```        | 識別子プロパティを識別します。 属している名前空間 (GUID)  |


**複数値の有効な PropertyId の形式の拡張プロパティ**

|**形式**|**使用例**|**説明**|
|:---------|:----------|:--------------|
| [*{タイプ} {Guid} **名前** Name*] | ```"StringArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | の名前空間と名前でプロパティを識別します。 (GUID)         |
| [ *Id* *{Id}**{タイプ}, {Guid} *]     | ```"IntegerArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8013"```        | の名前空間によってプロパティを識別します。 識別子 (GUID)   |


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

単一値または複数値の拡張プロパティを作成する場合は、数値識別子、または文字列の名前と値またはプロパティの値の実際の型に基づいて、2 つの形式のいずれかで**PropertyId**を指定できます。 REST-API メタデータで公開されていない MAPI プロパティを定義するほとんどの場合に拡張プロパティがあるために、対応する MAPI プロパティが[MAPI プロパティ識別子](https://msdn.microsoft.com/en-us/library/office/cc815528.aspx)の文字の文字列または数値の値を使うかどうかを選択する形式が反映されます。 間動作して、わかりやすくするため、Outlook の プロパティ識別子と GUID など、既存の MAPI プロパティに拡張プロパティをマップする必要がある情報を検索できます\[MS OXPROPS\]マイクロソフト、 [「Exchange Server プロトコル マスター プロパティ] ボックスの一覧」] です。 (https://msdn.microsoft.com/en-us/library/cc433490%28v=exchg.80%29.aspx)

**メモ *** PropertyId**の 1 つの形式を選択した後、その形式のみで、その拡張プロパティをアクセスすること。


**拡張プロパティを単一値の有効な PropertyId の形式**

|**形式**|**使用例**|**説明**|
|:---------|:----------|:--------------|
| [*{タイプ}, {Guid} **名前** Name*] | ```"String {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | と、名前でプロパティを識別します。 、属している名前空間 (GUID)         |
| [ *Id* *{Id}**{タイプ}, {Guid} *]     | ```"Integer {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8012"```        | 識別子プロパティを識別します。 属している名前空間 (GUID)  |


**複数値の有効な PropertyId の形式の拡張プロパティ**

|**形式**|**使用例**|**説明**|
|:---------|:----------|:--------------|
| [*{タイプ}, {Guid} **名前** Name*] | ```"StringArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | の名前空間と名前でプロパティを識別します。 (GUID)         |
| [ *Id* *{Id}**{タイプ}, {Guid} *]     | ```"IntegerArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8013"```        | の名前空間によってプロパティを識別します。 識別子 (GUID)   |


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




****

<a name="ExtendedPropertyOperations"> </a>
## <a name="a-nameextended-property-operationsa"></a><a name="extended-property-operations"></a>拡張プロパティの操作

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

[既存の項目の拡張プロパティを作成する](#CreateExtendedPropertyInExistingItem) | [、新しい項目の拡張プロパティを作成します。 ](#CreateExtendedPropertyInNewItem) | 

[取得項目の拡張プロパティを使用して展開されている](#GetExpandedExtendedProperty) | [単一値の拡張プロパティのフィルター](#GetItemByFilteringExtendedProperty) 


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

[既存の項目の拡張プロパティを作成する](#CreateExtendedPropertyInExistingItem) | [、新しい項目の拡張プロパティを作成します。 ](#CreateExtendedPropertyInNewItem) | 

[取得項目の拡張プロパティを使用して展開されている](#GetExpandedExtendedProperty) | [単一値の拡張プロパティのフィルター](#GetItemByFilteringExtendedProperty) 


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




<a name="CreateExtendedPropertyInExistingItem"> </a>

### <a name="a-namecreate-extended-property-in-an-existing-itema"></a><a name="create-extended-property-in-an-existing-item"></a>拡張プロパティを既存のアイテムを作成します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

[サポート リソース](#SupportedResources)の指定したインスタンスの 1 つまたは複数の拡張プロパティを作成します。 各拡張プロパティには、単一値または複数値を指定できます。 

```no-highlight
PATCH https://outlook.office.com/api/beta/me/messages('{message_id}')
PATCH https://outlook.office.com/api/beta/me/events('{event_id}')
PATCH https://outlook.office.com/api/beta/me/contacts('{contact_id}')
PATCH https://outlook.office.com/api/beta/me/tasks('{task_id}')
PATCH https://outlook.office.com/api/beta/me/mailfolders('{mailFolder_id}')
PATCH https://outlook.office.com/api/beta/me/calendars('{calendar_id}')
PATCH https://outlook.office.com/api/beta/me/contactfolders('{contactFolder_id}')
PATCH https://outlook.office.com/api/beta/me/taskfolders('{taskFolder_id}')
```

_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _https://Outlook.Office.com/Tasks.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_本文パラメーター_|
|SingleValueExtendedProperties|コレクション ([SingleValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#SingleValueLegacyExtendedPropertyResource))| 1 つまたは複数の値を持つ単一の拡張プロパティの配列。 |
|PropertyId|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを単一値のいずれかに従う必要があります。 必須。|
|値|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティ値を指定します。 必須。|
|MultiValueExtendedProperties|コレクション ([MultiValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#MultiValueLegacyExtendedPropertyResource)) | 複数値を持つ 1 つまたは複数の拡張プロパティの配列。|
|PropertyId|string|**MultiValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを複数値のいずれかに従う必要があります。 必須。|
|値|Collection(String)|**MultiValueExtendedProperties**コレクション内の各プロパティについては、そのプロパティの値を指定します。 必須。|


 
**要求のサンプル**

最初の例では、1 つの単一値プロパティを指定したメッセージを拡張を作成します。 **SingleValueExtendedProperties**配列内の唯一の要素は、プロパティを拡張します。 要求の本体には、拡張プロパティは、次が含まれています。
- **PropertyId**としてプロパティの型を指定する`string`、GUID、および名前付きプロパティ`Color`。
- **値**を指定`Green`の値として、`Color`プロパティ。

```
PATCH https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')

Content-Type: application/json

{
  "SingleValueExtendedProperties": [
      {
         "PropertyId":"String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
         "Value":"Green"
      }
    ]
}
```

**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード、し、[メッセージの更新](..\api\mail-rest-operations.md#UpdateAMessage)からの応答のような応答の本文に指定したメッセージが含まれています。 応答に含まれない、新しく作成されたプロパティを拡張します。


**要求のサンプル**

2 番目の例では、1 つの複数値を指定したメッセージのプロパティを拡張を作成します。 プロパティが**MultiValueExtendedProperties**配列内の唯一の要素であります。 要求の本体が含まれています。
- GUID と名前の指定した文字列のプロパティを配列で指定している**PropertyId** `Palette`。 
- **値**を指定する`Palette`、3 つの文字列値の配列として`["Green", "Aqua", "Blue"]`。

```
PATCH https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2_as77AACHsLrBBBA=')

Content-Type: application/json

{
  "MultiValueExtendedProperties": [
      {
         "PropertyId":"StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette",
         "Value":["Green", "Aqua", "Blue"]
      }
    ]
}
```

**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード、し、[メッセージの更新](..\api\mail-rest-operations.md#UpdateAMessage)からの応答のような応答の本文に指定したメッセージが含まれています。 応答に含まれない、新しく作成されたプロパティを拡張します。

[拡張プロパティを使用して展開されているメッセージを取得する](#GetExpandedExtendedProperty)、新しく作成された拡張プロパティを参照してください。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

[サポート リソース](#SupportedResources)の指定したインスタンスの 1 つまたは複数の拡張プロパティを作成します。 各拡張プロパティには、単一値または複数値を指定できます。 

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/messages('{message_id}')
PATCH https://outlook.office.com/api/v2.0/me/events('{event_id}')
PATCH https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')
PATCH https://outlook.office.com/api/v2.0/me/tasks('{task_id}')
PATCH https://outlook.office.com/api/v2.0/me/mailfolders('{mailFolder_id}')
PATCH https://outlook.office.com/api/v2.0/me/calendars('{calendar_id}')
PATCH https://outlook.office.com/api/v2.0/me/contactfolders('{contactFolder_id}')
PATCH https://outlook.office.com/api/v2.0/me/taskfolders('{taskFolder_id}')
```

_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _https://Outlook.Office.com/Tasks.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_本文パラメーター_|
|SingleValueExtendedProperties|コレクション ([SingleValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#SingleValueLegacyExtendedPropertyResource_v2))| 1 つまたは複数の値を持つ単一の拡張プロパティの配列。 |
|PropertyId|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを単一値のいずれかに従う必要があります。 必須。|
|値|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティ値を指定します。 必須。|
|MultiValueExtendedProperties|コレクション ([MultiValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#MultiValueLegacyExtendedPropertyResource_v2)) | 複数値を持つ 1 つまたは複数の拡張プロパティの配列。|
|PropertyId|string|**MultiValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを複数値のいずれかに従う必要があります。 必須。|
|値|Collection(String)|**MultiValueExtendedProperties**コレクション内の各プロパティについては、そのプロパティの値を指定します。 必須。|


 
**要求のサンプル**

最初の例では、1 つの単一値プロパティを指定したメッセージを拡張を作成します。 **SingleValueExtendedProperties**配列内の唯一の要素は、プロパティを拡張します。 要求の本体には、拡張プロパティは、次が含まれています。
- **PropertyId**としてプロパティの型を指定する`string`、GUID、および名前付きプロパティ`Color`。
- **値**を指定`Green`の値として、`Color`プロパティ。

```
PATCH https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')

Content-Type: application/json

{
  "SingleValueExtendedProperties": [
      {
         "PropertyId":"String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
         "Value":"Green"
      }
    ]
}
```

**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード、し、[メッセージの更新](..\api\mail-rest-operations.md#UpdateAMessage)からの応答のような応答の本文に指定したメッセージが含まれています。 応答に含まれない、新しく作成されたプロパティを拡張します。


**要求のサンプル**

2 番目の例では、1 つの複数値を指定したメッセージのプロパティを拡張を作成します。 プロパティが**MultiValueExtendedProperties**配列内の唯一の要素であります。 要求の本体が含まれています。
- GUID と名前の指定した文字列のプロパティを配列で指定している**PropertyId** `Palette`。 
- **値**を指定する`Palette`、3 つの文字列値の配列として`["Green", "Aqua", "Blue"]`。

```
PATCH https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2_as77AACHsLrBBBA=')

Content-Type: application/json

{
  "MultiValueExtendedProperties": [
      {
         "PropertyId":"StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette",
         "Value":["Green", "Aqua", "Blue"]
      }
    ]
}
```

**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード、し、[メッセージの更新](..\api\mail-rest-operations.md#UpdateAMessage)からの応答のような応答の本文に指定したメッセージが含まれています。 応答に含まれない、新しく作成されたプロパティを拡張します。

[拡張プロパティを使用して展開されているメッセージを取得する](#GetExpandedExtendedProperty)、新しく作成された拡張プロパティを参照してください。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




****

<a name="CreateExtendedPropertyInNewItem)"></a>

### <a name="a-namecreate-extended-property-in-a-new-itema-"></a><a name="create-extended-property-in-a-new-item"></a>拡張プロパティを [新しい項目を作成します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

1 つを作成するか、[サポート リソース](#SupportedResources)の新しいインスタンスを作成中に複数の拡張プロパティ、すべてに同じ投稿を呼び出します。 POST-要求の本文に、拡張プロパティ、またはプロパティが含まれます。


```no-highlight
POST https://outlook.office.com/api/beta/me/messages
POST https://outlook.office.com/api/beta/me/events
POST https://outlook.office.com/api/beta/me/contacts
POST https://outlook.office.com/api/beta/me/tasks
POST https://outlook.office.com/api/beta/me/mailfolders
POST https://outlook.office.com/api/beta/me/calendars
POST https://outlook.office.com/api/beta/me/contactfolders
POST https://outlook.office.com/api/beta/me/taskfolders
```

_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _https://Outlook.Office.com/Tasks.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_本文パラメーター_|
|SingleValueExtendedProperties|コレクション ([SingleValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#SingleValueLegacyExtendedPropertyResource))| 1 つまたは複数の値を持つ単一の拡張プロパティの配列。 |
|PropertyId|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを単一値のいずれかに従う必要があります。 必須。|
|値|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティ値を指定します。 必須。|
|MultiValueExtendedProperties|コレクション ([MultiValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#MultiValueLegacyExtendedPropertyResource)) | 複数値を持つ 1 つまたは複数の拡張プロパティの配列。|
|PropertyId|string|**MultiValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを複数値のいずれかに従う必要があります。 必須。|
|値|Collection(String)|**MultiValueExtendedProperties**コレクション内の各プロパティについては、そのプロパティの値を指定します。 必須。|


 
**サンプル リクエスト**

最初の例では、新しいイベントと単一値の拡張プロパティを作成します。 新しいイベントは、通常のプロパティとは別は、要求の本体には、1 つの単一値の拡張プロパティ、およびプロパティは、次を含む**SingleValueExtendedProperties**の配列が含まれています。
- **PropertyId**としてプロパティの型を指定する`string`、GUID、および名前付きプロパティ`Fun`。
- **値**を指定`Food`の値として、`Fun`プロパティ。

```
POST https://outlook.office.com/api/beta/me/events

Content-Type: application/json

{
  "Subject": "Celebrate Thanksgiving",
  "Body": {
    "ContentType": "HTML",
    "Content": "Let's get together!"
  },
  "Start": {
      "DateTime": "2015-11-26T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2015-11-26T23:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "Terrie@contoso.com",
        "Name": "Terrie Barrera"
      },
      "Type": "Required"
    }
  ],
  "SingleValueExtendedProperties": [
     {
           "PropertyId":"String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun",
           "Value":"Food"
     }
  ]
}
```

**応答の例**

によって正常な応答が示されている、 `HTTP 201 Created` 、応答コードと新しいイベントを[イベントだけを作成する](..\api\calendar-rest-operations.md#Createevents)からのような応答に、応答本体に含まれています。 拡張プロパティを新しく作成された応答は含まれません。

[拡張プロパティを使用して展開されているアイテムを取得する](#GetExpandedExtendedProperty)、新しく作成された拡張プロパティを参照してください。


**要求のサンプル**

2 番目の例では、POST 操作を同時にすべての新しいイベントのプロパティを拡張する複数の値を作成します。 新しいイベントは、通常のプロパティとは別は、要求の本体には、1 つの拡張プロパティを含む**MultiValueExtendedProperties**の配列が含まれています。 要求の本体には、その複数の値の拡張プロパティは、次が含まれています。
- GUID と名前の指定した文字列のプロパティを配列で指定している**PropertyId** `Recreation`。 
- **値**を指定する`Recreation`、3 つの文字列値の配列として`["Food", "Hiking", "Swimming"]`。

```
POST https://outlook.office.com/api/beta/me/events

Content-Type: application/json

{
  "Subject": "Family reunion",
  "Body": {
    "ContentType": "HTML",
    "Content": "Let's get together this Thanksgiving!"
  },
  "Start": {
      "DateTime": "2015-11-26T09:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2015-11-29T21:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "Terrie@contoso.com",
        "Name": "Terrie Barrera"
      },
      "Type": "Required"
    },
    {
      "EmailAddress": {
        "Address": "Lauren@contoso.com",
        "Name": "Lauren Solis"
      },
      "Type": "Required"
    }
  ],
  "MultiValueExtendedProperties": [
     {
           "PropertyId":"StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
           "Value": ["Food", "Hiking", "Swimming"]
     }
  ]
}
```

**応答の例**

によって正常な応答が示されている、 `HTTP 201 Created` 、応答コードと新しいイベントを[イベントだけを作成する](..\api\calendar-rest-operations.md#Createevents)からのような応答に、応答本体に含まれています。 拡張プロパティを新しく作成された応答は含まれません。

[拡張プロパティを使用して展開されているアイテムを取得する](#GetExpandedExtendedProperty)、新しく作成された拡張プロパティを参照してください。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

1 つを作成するか、[サポート リソース](#SupportedResources)の新しいインスタンスを作成中に複数の拡張プロパティ、すべてに同じ投稿を呼び出します。 POST-要求の本文に、拡張プロパティ、またはプロパティが含まれます。


```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages
POST https://outlook.office.com/api/v2.0/me/events
POST https://outlook.office.com/api/v2.0/me/contacts
POST https://outlook.office.com/api/v2.0/me/tasks
POST https://outlook.office.com/api/v2.0/me/mailfolders
POST https://outlook.office.com/api/v2.0/me/calendars
POST https://outlook.office.com/api/v2.0/me/contactfolders
POST https://outlook.office.com/api/v2.0/me/taskfolders
```

_**必要な範囲の最小値**: 次の読み取り/書き込みのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _https://Outlook.Office.com/Tasks.ReadWrite_
- _WL.IMAP_
- _WL.Calendars\_を更新_
- _WL.Events\_の作成_
- _WL.Contacts\_の作成_


|**パラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_本文パラメーター_|
|SingleValueExtendedProperties|コレクション ([SingleValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#SingleValueLegacyExtendedPropertyResource_v2))| 1 つまたは複数の値を持つ単一の拡張プロパティの配列。 |
|PropertyId|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを単一値のいずれかに従う必要があります。 必須。|
|値|string|**SingleValueExtendedProperties**コレクション内の各プロパティのプロパティ値を指定します。 必須。|
|MultiValueExtendedProperties|コレクション ([MultiValueLegacyExtendedProperty](..\api\complex-types-for-mail-contacts-calendar.md#MultiValueLegacyExtendedPropertyResource_v2)) | 複数値を持つ 1 つまたは複数の拡張プロパティの配列。|
|PropertyId|string|**MultiValueExtendedProperties**コレクション内の各プロパティのプロパティを識別するのにはこれを指定します。 [形式がサポートされている](#ExtendedPropertyIdFormats)拡張プロパティを複数値のいずれかに従う必要があります。 必須。|
|値|Collection(String)|**MultiValueExtendedProperties**コレクション内の各プロパティについては、そのプロパティの値を指定します。 必須。|


 
**サンプル リクエスト**

最初の例では、新しいイベントと単一値の拡張プロパティを作成します。 新しいイベントは、通常のプロパティとは別は、要求の本体には、1 つの単一値の拡張プロパティ、およびプロパティは、次を含む**SingleValueExtendedProperties**の配列が含まれています。
- **PropertyId**としてプロパティの型を指定する`string`、GUID、および名前付きプロパティ`Fun`。
- **値**を指定`Food`の値として、`Fun`プロパティ。

```
POST https://outlook.office.com/api/v2.0/me/events

Content-Type: application/json

{
  "Subject": "Celebrate Thanksgiving",
  "Body": {
    "ContentType": "HTML",
    "Content": "Let's get together!"
  },
  "Start": {
      "DateTime": "2015-11-26T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2015-11-26T23:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "Terrie@contoso.com",
        "Name": "Terrie Barrera"
      },
      "Type": "Required"
    }
  ],
  "SingleValueExtendedProperties": [
     {
           "PropertyId":"String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun",
           "Value":"Food"
     }
  ]
}
```

**応答の例**

によって正常な応答が示されている、 `HTTP 201 Created` 、応答コードと新しいイベントを[イベントだけを作成する](..\api\calendar-rest-operations.md#Createevents)からのような応答に、応答本体に含まれています。 拡張プロパティを新しく作成された応答は含まれません。

[拡張プロパティを使用して展開されているアイテムを取得する](#GetExpandedExtendedProperty)、新しく作成された拡張プロパティを参照してください。


**要求のサンプル**

2 番目の例では、POST 操作を同時にすべての新しいイベントのプロパティを拡張する複数の値を作成します。 新しいイベントは、通常のプロパティとは別は、要求の本体には、1 つの拡張プロパティを含む**MultiValueExtendedProperties**の配列が含まれています。 要求の本体には、その複数の値の拡張プロパティは、次が含まれています。
- GUID と名前の指定した文字列のプロパティを配列で指定している**PropertyId** `Recreation`。 
- **値**を指定する`Recreation`、3 つの文字列値の配列として`["Food", "Hiking", "Swimming"]`。

```
POST https://outlook.office.com/api/v2.0/me/events

Content-Type: application/json

{
  "Subject": "Family reunion",
  "Body": {
    "ContentType": "HTML",
    "Content": "Let's get together this Thanksgiving!"
  },
  "Start": {
      "DateTime": "2015-11-26T09:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2015-11-29T21:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "Terrie@contoso.com",
        "Name": "Terrie Barrera"
      },
      "Type": "Required"
    },
    {
      "EmailAddress": {
        "Address": "Lauren@contoso.com",
        "Name": "Lauren Solis"
      },
      "Type": "Required"
    }
  ],
  "MultiValueExtendedProperties": [
     {
           "PropertyId":"StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
           "Value": ["Food", "Hiking", "Swimming"]
     }
  ]
}
```

**応答の例**

によって正常な応答が示されている、 `HTTP 201 Created` 、応答コードと新しいイベントを[イベントだけを作成する](..\api\calendar-rest-operations.md#Createevents)からのような応答に、応答本体に含まれています。 拡張プロパティを新しく作成された応答は含まれません。

[拡張プロパティを使用して展開されているアイテムを取得する](#GetExpandedExtendedProperty)、新しく作成された拡張プロパティを参照してください。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




****

<a name="GetExpandedExtendedProperty"> </a>

### <a name="a-nameget-item-expanded-with-extended-propertya"></a><a name="get-item-expanded-with-extended-property"></a>拡張プロパティを使用して展開されているアイテムを取得します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

[リソースがサポートされている](#SupportedResources) **PropertyId**のフィルターによって指定されている拡張プロパティを使用して拡張のインスタンスを取得します。 

**PropertyId**のフィルターで指定した文字列*{PropertyId_value}*は、 [PropertyId 形式をサポート](#ExtendedPropertyIdFormats)するのいずれかに従う必要があります。 Die[URL エンコード](http://www.w3schools.com/tags/ref_urlencode.asp)を適用することを確認します。 フィルター文字列内のスペース文字を

**拡張プロパティを単一値が一致するアイテムを展開します。**

```no-highlight
GET https://outlook.office.com/api/beta/me/messages('{message_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/events('{event_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/contacts('{contact_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/tasks('{task_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/mailfolders('{mailFolder_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/calendars('{calendar_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/contactfolders('{contactFolder_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/taskfolders('{taskfolder_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')
```

**拡張プロパティを複数の値が一致するアイテムを展開します。**

```no-highlight
GET https://outlook.office.com/api/beta/me/messages('{message_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/events('{event_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/contacts('{contact_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/tasks('{task_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/mailfolders('{mailFolder_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/calendars('{calendar_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/contactfolders('{contactFolder_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/beta/me/taskfolders('{taskfolder_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')
```


_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _https://Outlook.Office.com/Tasks.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_

 
**要求のサンプル**

最初の例では、取得し、単一値の拡張プロパティを含めることによって指定されたメッセージを展開します。 フィルター文字列と一致する、 **PropertyId**の拡張プロパティを取得する`String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color`。 (URL エンコードを使用して削除ここでの読みやすさ)

```
GET https://outlook.office.com/api/beta/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')?$expand=SingleValueExtendedProperties($filter=PropertyId%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、指定したメッセージのすべてのプロパティとフィルターから返される拡張のプロパティが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE1M2_bs88AACHsLqWAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AACbyS4H\"",
    "Id": "AAMkAGE1M2_bs88AACHsLqWAAA=",
    "CreatedDateTime": "2015-11-11T02:41:24Z",
    "LastModifiedDateTime": "2015-12-09T04:07:57Z",
    "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AACbyS4H",
    "Categories": [
    ],
    "ReceivedDateTime": "2015-11-11T02:41:24Z",
    "SentDateTime": "2015-11-11T02:41:24Z",
    "HasAttachments": false,
    "InternetMessageId": "<SN2SR0101MB002977E7C30F9CA9AA55961484130@SN2SR0101MB0029.contoso.com>",
    "Subject": "RE: Talk about emergency prep",
    "Body": {
        "ContentType": "HTML",
        "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=iso-8859-1\">\r\n<style type=\"text/css\" style=\"\">\r\n<!--\r\np\r\n\t{margin-top:0;\r\n\tmargin-bottom:0}\r\n-->\r\n</style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<hr tabindex=\"-1\" style=\"display:inline-block; width:98%\">\r\n<div id=\"divRplyFwdMsg\" dir=\"ltr\"><font face=\"Calibri, sans-serif\" color=\"#000000\" style=\"font-size:11pt\"><b>From:</b> Christine Irwin<br>\r\n<b>Sent:</b> Sunday, November 8, 2015 12:28:31 AM<br>\r\n<b>To:</b> Terrie Barrera<br>\r\n<b>Subject:</b> Talk about emergency prep<br>\r\n<b>When:</b> Sunday, November 8, 2015 7:00 PM-8:00 PM.<br>\r\n<b>Where:</b> The Commons</font>\r\n<div>&nbsp;</div>\r\n</div>\r\n<div>\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt; color:#000000; background-color:#FFFFFF; font-family:Calibri,Arial,Helvetica,sans-serif\">\r\n<p>Please see the attached before you come to the meeting.<br>\r\n</p>\r\n</div>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "BodyPreview": "________________________________",
    "Importance": "Normal",
    "ParentFolderId": "AQMkAGE1M2jgxCloXP1JupQN7j5uzzwAAAIBDwAAAA==",
    "Sender": {
        "EmailAddress": {
            "Name": "Christine Irwin",
            "Address": "christine@contoso.com"
        }
    },
    "From": null,
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Christine Irwin",
                "Address": "christine@contoso.com"
            }
        }
    ],
    "CcRecipients": [
    ],
    "BccRecipients": [
    ],
    "ReplyTo": [
    ],
    "ConversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVlLTY0YjcxZWUzNTE1MAAQAHWT1sRiMChEmlQCIZUadoU=",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsRead": true,
    "IsDraft": true,
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2%2Bbs88AACHsLqWAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "MentionedMe": null,
    "HashtagDetailsPreview": null,
    "LikesPreview": null,
    "Mentioned": [
    ],
    "InferenceClassification": "Focused",
    "UnsubscribeData": [
    ],
    "UnsubscribeEnabled": false,
    "SingleValueExtendedProperties@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGE1M2_bs88AACHsLqWAAA%3D')/SingleValueExtendedProperties",
    "SingleValueExtendedProperties": [
        {
            "PropertyId": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
            "Value": "Green"
        }
    ]
}
```


**要求のサンプル**

2 番目の例では、取得し、複数の値の拡張プロパティを含めることで指定したイベントを展開します。 フィルター文字列と一致する、 **PropertyId**の拡張プロパティを取得する`StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation`。 (URL エンコードを使用して削除ここでの読みやすさ)

```
GET https://outlook.office.com/api/beta/me/events('AAMkAGE1M2_bs88AACbuFiiAAA=')?$expand=MultiValueExtendedProperties($filter=PropertyId%20eq%20'StringArray%20{66f5a359-4659-4830-9070-00050ec6ac6e}%20Name%20Recreation')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、指定されたイベントのすべてのプロパティとフィルターから返される拡張のプロパティが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE1M2_bs88AACbuFiiAAA=')",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAm8k15A==\"",
    "Id": "AAMkAGE1M2_bs88AACbuFiiAAA=",
    "CreatedDateTime": "2015-12-09T05:18:05.9477979Z",
    "LastModifiedDateTime": "2015-12-09T05:18:06.197802Z",
    "ChangeKey": "mODEKWhc/Um6lA3uPm7PPAAAm8k15A==",
    "Categories": [
    ],
    "OriginalStartTimeZone": "Pacific Standard Time",
    "OriginalEndTimeZone": "Pacific Standard Time",
    "ResponseStatus": {
        "Response": "Organizer",
        "Time": "0001-01-01T00:00:00Z"
    },
    "iCalUId": "04000000828A332796D9",
    "ReminderMinutesBeforeStart": 15,
    "IsReminderOn": true,
    "HasAttachments": false,
    "Subject": "Family reunion",
    "Body": {
        "ContentType": "HTML",
        "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nLet's get together this Thanksgiving!\r\n</body>\r\n</html>\r\n"
    },
    "BodyPreview": "Let's get together this Thanksgiving!",
    "Importance": "Normal",
    "Sensitivity": "Normal",
    "Start": {
        "DateTime": "2015-11-26T17:00:00.0000000",
        "TimeZone": "UTC"
    },
    "End": {
        "DateTime": "2015-11-30T05:00:00.0000000",
        "TimeZone": "UTC"
    },
    "Location": {
        "DisplayName": ""
    },
    "IsAllDay": false,
    "IsCancelled": false,
    "IsOrganizer": true,
    "Recurrence": null,
    "ResponseRequested": true,
    "SeriesMasterId": null,
    "ShowAs": "Busy",
    "Type": "SingleInstance",
    "Attendees": [
        {
            "Status": {
                "Response": "None",
                "Time": "0001-01-01T00:00:00Z"
            },
            "Type": "Required",
            "EmailAddress": {
                "Name": "Terrie Barrera",
                "Address": "Terrie@contoso.com"
            }
        },
        {
            "Status": {
                "Response": "None",
                "Time": "0001-01-01T00:00:00Z"
            },
            "Type": "Required",
            "EmailAddress": {
                "Name": "Lauren Solis",
                "Address": "Lauren@contoso.com"
            }
        }
    ],
    "Organizer": {
        "EmailAddress": {
            "Name": "Christine Irwin",
            "Address": "christine@contoso.com"
        }
    },
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2%2Bbs88AACbuFiiAAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
    "MultiValueExtendedProperties@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events('AAMkAGE1M2_bs88AACbuFiiAAA%3D')/MultiValueExtendedProperties",
    "MultiValueExtendedProperties": [
        {
            "PropertyId": "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
            "Value": [
                "Food",
                "Hiking",
                "Swimming"
            ]
        }
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

[リソースがサポートされている](#SupportedResources) **PropertyId**のフィルターによって指定されている拡張プロパティを使用して拡張のインスタンスを取得します。 

**PropertyId**のフィルターで指定した文字列*{PropertyId_value}*は、 [PropertyId 形式をサポート](#ExtendedPropertyIdFormats)するのいずれかに従う必要があります。 Die[URL エンコード](http://www.w3schools.com/tags/ref_urlencode.asp)を適用することを確認します。 フィルター文字列内のスペース文字を

**拡張プロパティを単一値が一致するアイテムを展開します。**

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages('{message_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/events('{event_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/tasks('{task_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/mailfolders('{mailFolder_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/calendars('{calendar_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/contactfolders('{contactFolder_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/taskfolders('{taskfolder_id}')?$expand=SingleValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')
```

**拡張プロパティを複数の値が一致するアイテムを展開します。**

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages('{message_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/events('{event_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/tasks('{task_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/mailfolders('{mailFolder_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/calendars('{calendar_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/contactfolders('{contactFolder_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')

GET https://outlook.office.com/api/v2.0/me/taskfolders('{taskfolder_id}')?$expand=MultiValueExtendedProperties($filter=PropertyId eq '{propertyId_value}')
```


_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _https://Outlook.Office.com/Tasks.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_

 
**要求のサンプル**

最初の例では、取得し、単一値の拡張プロパティを含めることによって指定されたメッセージを展開します。 フィルター文字列と一致する、 **PropertyId**の拡張プロパティを取得する`String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color`。 (エンコードを使用して削除ここでの読みやすさ URL)

```
GET https://outlook.office.com/api/v2.0/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')?$expand=SingleValueExtendedProperties($filter=PropertyId%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、指定したメッセージのすべてのプロパティとフィルターから返される拡張のプロパティが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE1M2_bs88AACHsLqWAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AACbyS4H\"",
    "Id": "AAMkAGE1M2_bs88AACHsLqWAAA=",
    "CreatedDateTime": "2015-11-11T02:41:24Z",
    "LastModifiedDateTime": "2015-12-09T04:07:57Z",
    "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AACbyS4H",
    "Categories": [
    ],
    "ReceivedDateTime": "2015-11-11T02:41:24Z",
    "SentDateTime": "2015-11-11T02:41:24Z",
    "HasAttachments": false,
    "InternetMessageId": "<SN2SR0101MB002977E7C30F9CA9AA55961484130@SN2SR0101MB0029.contoso.com>",
    "Subject": "RE: Talk about emergency prep",
    "Body": {
        "ContentType": "HTML",
        "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=iso-8859-1\">\r\n<style type=\"text/css\" style=\"\">\r\n<!--\r\np\r\n\t{margin-top:0;\r\n\tmargin-bottom:0}\r\n-->\r\n</style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<hr tabindex=\"-1\" style=\"display:inline-block; width:98%\">\r\n<div id=\"divRplyFwdMsg\" dir=\"ltr\"><font face=\"Calibri, sans-serif\" color=\"#000000\" style=\"font-size:11pt\"><b>From:</b> Christine Irwin<br>\r\n<b>Sent:</b> Sunday, November 8, 2015 12:28:31 AM<br>\r\n<b>To:</b> Terrie Barrera<br>\r\n<b>Subject:</b> Talk about emergency prep<br>\r\n<b>When:</b> Sunday, November 8, 2015 7:00 PM-8:00 PM.<br>\r\n<b>Where:</b> The Commons</font>\r\n<div>&nbsp;</div>\r\n</div>\r\n<div>\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt; color:#000000; background-color:#FFFFFF; font-family:Calibri,Arial,Helvetica,sans-serif\">\r\n<p>Please see the attached before you come to the meeting.<br>\r\n</p>\r\n</div>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "BodyPreview": "________________________________",
    "Importance": "Normal",
    "ParentFolderId": "AQMkAGE1M2jgxCloXP1JupQN7j5uzzwAAAIBDwAAAA==",
    "Sender": {
        "EmailAddress": {
            "Name": "Christine Irwin",
            "Address": "christine@contoso.com"
        }
    },
    "From": null,
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Christine Irwin",
                "Address": "christine@contoso.com"
            }
        }
    ],
    "CcRecipients": [
    ],
    "BccRecipients": [
    ],
    "ReplyTo": [
    ],
    "ConversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVlLTY0YjcxZWUzNTE1MAAQAHWT1sRiMChEmlQCIZUadoU=",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsRead": true,
    "IsDraft": true,
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2%2Bbs88AACHsLqWAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "MentionedMe": null,
    "HashtagDetailsPreview": null,
    "LikesPreview": null,
    "Mentioned": [
    ],
    "InferenceClassification": "Focused",
    "UnsubscribeData": [
    ],
    "UnsubscribeEnabled": false,
    "SingleValueExtendedProperties@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGE1M2_bs88AACHsLqWAAA%3D')/SingleValueExtendedProperties",
    "SingleValueExtendedProperties": [
        {
            "PropertyId": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
            "Value": "Green"
        }
    ]
}
```


**要求のサンプル**

2 番目の例では、取得し、複数の値の拡張プロパティを含めることで指定したイベントを展開します。 フィルター文字列と一致する、 **PropertyId**の拡張プロパティを取得する`StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation`。 (URL エンコードを使用して削除ここでの読みやすさ)

```
GET https://outlook.office.com/api/v2.0/me/events('AAMkAGE1M2_bs88AACbuFiiAAA=')?$expand=MultiValueExtendedProperties($filter=PropertyId%20eq%20'StringArray%20{66f5a359-4659-4830-9070-00050ec6ac6e}%20Name%20Recreation')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード。

応答の本体には、指定されたイベントのすべてのプロパティとフィルターから返される拡張のプロパティが含まれています。

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE1M2_bs88AACbuFiiAAA=')",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAm8k15A==\"",
    "Id": "AAMkAGE1M2_bs88AACbuFiiAAA=",
    "CreatedDateTime": "2015-12-09T05:18:05.9477979Z",
    "LastModifiedDateTime": "2015-12-09T05:18:06.197802Z",
    "ChangeKey": "mODEKWhc/Um6lA3uPm7PPAAAm8k15A==",
    "Categories": [
    ],
    "OriginalStartTimeZone": "Pacific Standard Time",
    "OriginalEndTimeZone": "Pacific Standard Time",
    "ResponseStatus": {
        "Response": "Organizer",
        "Time": "0001-01-01T00:00:00Z"
    },
    "iCalUId": "04000000828A332796D9",
    "ReminderMinutesBeforeStart": 15,
    "IsReminderOn": true,
    "HasAttachments": false,
    "Subject": "Family reunion",
    "Body": {
        "ContentType": "HTML",
        "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nLet's get together this Thanksgiving!\r\n</body>\r\n</html>\r\n"
    },
    "BodyPreview": "Let's get together this Thanksgiving!",
    "Importance": "Normal",
    "Sensitivity": "Normal",
    "Start": {
        "DateTime": "2015-11-26T17:00:00.0000000",
        "TimeZone": "UTC"
    },
    "End": {
        "DateTime": "2015-11-30T05:00:00.0000000",
        "TimeZone": "UTC"
    },
    "Location": {
        "DisplayName": ""
    },
    "IsAllDay": false,
    "IsCancelled": false,
    "IsOrganizer": true,
    "Recurrence": null,
    "ResponseRequested": true,
    "SeriesMasterId": null,
    "ShowAs": "Busy",
    "Type": "SingleInstance",
    "Attendees": [
        {
            "Status": {
                "Response": "None",
                "Time": "0001-01-01T00:00:00Z"
            },
            "Type": "Required",
            "EmailAddress": {
                "Name": "Terrie Barrera",
                "Address": "Terrie@contoso.com"
            }
        },
        {
            "Status": {
                "Response": "None",
                "Time": "0001-01-01T00:00:00Z"
            },
            "Type": "Required",
            "EmailAddress": {
                "Name": "Lauren Solis",
                "Address": "Lauren@contoso.com"
            }
        }
    ],
    "Organizer": {
        "EmailAddress": {
            "Name": "Christine Irwin",
            "Address": "christine@contoso.com"
        }
    },
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2%2Bbs88AACbuFiiAAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
    "MultiValueExtendedProperties@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events('AAMkAGE1M2_bs88AACbuFiiAAA%3D')/MultiValueExtendedProperties",
    "MultiValueExtendedProperties": [
        {
            "PropertyId": "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
            "Value": [
                "Food",
                "Hiking",
                "Swimming"
            ]
        }
    ]
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->





****

<a name="GetItemByFilteringExtendedProperty"> </a>

### <a name="a-nameget-item-by-filtering-on-extended-propertya"></a><a name="get-item-by-filtering-on-extended-property"></a>拡張プロパティにフィルターを使用してアイテムを取得します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**PropertyId**と**値**のフィルターによって指定されたプロパティが拡張されている[サポートのリソース](#SupportedResources)のインスタンスを取得します。 フィルターは、サインインしているユーザーのメールボックス内のリソースのすべてのインスタンスに適用されます。 このフィルターは、単一値が複数値ではなく拡張プロパティのみをサポートします。

**PropertyId**のフィルターで指定した文字列*{PropertyId_value}*は、 [PropertyId 形式をサポート](#ExtendedPropertyIdFormats)するのいずれかに従う必要があります。 フィルター文字列内の次の文字を[URL エンコード](http://www.w3schools.com/tags/ref_urlencode.asp)を適用するかどうかを確認: スラッシュと領域を転送します。 

```no-highlight
GET https://outlook.office.com/api/beta/me/messages?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/beta/me/events?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/beta/me/contacts?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/beta/me/tasks?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/beta/me/mailfolders?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/beta/me/calendars?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/beta/me/contactfolders?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/beta/me/taskfolders?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')
```


_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _https://Outlook.Office.com/Tasks.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_

 
**要求のサンプル**

最初の例では、フィルターで指定されたプロパティを拡張する単一の値を持つメッセージを取得します。 フィルターでは、拡張のプロパティを返します。
- 文字列と一致する、 **PropertyId** `String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color` 。 (URL エンコードを使用して削除ここでの読みやすさ)
- その**値**が`Green`。

```
GET https://outlook.office.com/api/beta/Me/Messages?$filter=SingleValueExtendedProperties%2FAny(ep%3A%20ep%2FPropertyId%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color'%20and%20ep%2FValue%20eq%20'Green')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード、および応答の本体に、フィルターに一致する拡張プロパティを持つメッセージのすべてのプロパティが含まれています。 応答の本体では、応答[メッセージのコレクションを取得する](..\api\mail-rest-operations.md#GetMessages)からと同様です。 応答では、一致する拡張プロパティは含まれません。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**PropertyId**と**値**のフィルターによって指定されたプロパティが拡張されている[サポートのリソース](#SupportedResources)のインスタンスを取得します。 フィルターは、サインインしているユーザーのメールボックス内のリソースのすべてのインスタンスに適用されます。 このフィルターは、単一値が複数値ではなく拡張プロパティのみをサポートします。

**PropertyId**のフィルターで指定した文字列*{PropertyId_value}*は、 [PropertyId 形式をサポート](#ExtendedPropertyIdFormats)するのいずれかに従う必要があります。 フィルター文字列内の次の文字を[URL エンコード](http://www.w3schools.com/tags/ref_urlencode.asp)を適用するかどうかを確認: スラッシュと領域を転送します。 

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/v2.0/me/events?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/v2.0/me/contacts?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/v2.0/me/tasks?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/v2.0/me/mailfolders?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/v2.0/me/calendars?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/v2.0/me/contactfolders?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')

GET https://outlook.office.com/api/v2.0/me/taskfolders?$filter=SingleValueExtendedProperties/Any(ep: ep/PropertyId eq '{propertyId_value}' and ep/Value eq '{property_value}')
```


_**必要な範囲の最小値**: 次の読み取りのいずれかのスコープとは、対象となるリソースに対応します。_
- _https://Outlook.Office.com/Mail.Read_
- _https://Outlook.Office.com/calendars.Read_
- _https://Outlook.Office.com/Contacts.Read_
- _https://Outlook.Office.com/Tasks.Read_
- _WL.IMAP_
- _WL.calendars_
- _WL.Contacts\_カレンダー_
- _WL.Basic_

 
**要求のサンプル**

最初の例では、フィルターで指定されたプロパティを拡張する単一の値を持つメッセージを取得します。 フィルターでは、拡張のプロパティを返します。
- 文字列と一致する、 **PropertyId** `String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color` 。 (URL エンコードを使用して削除ここでの読みやすさ)
- その**値**が`Green`。

```
GET https://outlook.office.com/api/v2.0/Me/Messages?$filter=SingleValueExtendedProperties%2FAny(ep%3A%20ep%2FPropertyId%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color'%20and%20ep%2FValue%20eq%20'Green')
```


**応答の例**

によって正常な応答が示されている、`HTTP 200 OK`応答コード、および応答の本体に、フィルターに一致する拡張プロパティを持つメッセージのすべてのプロパティが含まれています。 応答の本体では、応答[メッセージのコレクションを取得する](..\api\mail-rest-operations.md#GetMessages)からと同様です。 応答では、一致する拡張プロパティは含まれません。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->





****


<a name="NextSteps"> </a>
## <a name="a-namenext-stepsa"></a><a name="next-steps"></a>次のステップ

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

アプリケーションの構築を開始、あるいは詳細については、準備が整ったら、かどうかお任せします。

- [メール、カレンダー、および連絡先の他の Api を使用](http://dev.outlook.com/RestGettingStarted)します。

- 対話型の[API のサンド ボックス](https://apisandbox.msdn.microsoft.com/)を使用して Office 365 の Api について説明します。

- サンプルをしますか。 [きました](..\howto\starter-projects-and-code-samples.md)。


または、Office 365 のプラットフォームを使用する方法の詳細について説明します。

- [REST-API を Outlook で Outlook のデベロッパー センター](http://dev.outlook.com/RestGettingStarted/Overview)

- [Office 365 のプラットフォーム上での開発の概要](..\howto\platform-development-overview.md)

- [メールの残りの部分の Api を参照します。](..\api\mail-rest-operations.md)

- [REST-Api の予定表を参照します。](..\api\calendar-rest-operations.md)

- [REST-Api リファレンスを取引先担当者します。](..\api\contacts-rest-operations.md)

- [REST-API のタスク](..\api\task-rest-operations.md)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)

- [ユーザーの API リファレンス](..\api\people-rest-operations.md) (プレビュー)

- [データ拡張機能 API リファレンス](..\api\extensions-rest-operations.md)

- [通知の残りの部分の API リファレンス](..\api\notify-rest-operations.md)

- [ユーザーの写真の残りの部分の API リファレンス](..\api\photo-rest-operations.md) 

- [バッチ Outlook の他の要求](#..\api\batch-outlook-rest-requests.md) (プレビュー)



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

- [メールの残りの部分の Api を参照します。](..\api\mail-rest-operations.md)

- [REST-Api の予定表を参照します。](..\api\calendar-rest-operations.md)

- [REST-Api リファレンスを取引先担当者します。](..\api\contacts-rest-operations.md)

- [REST-API のタスク](..\api\task-rest-operations.md)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)

- [ユーザーの API リファレンス](..\api\people-rest-operations.md) (プレビュー)

- [データ拡張機能 API リファレンス](..\api\extensions-rest-operations.md)

- [通知の残りの部分の API リファレンス](..\api\notify-rest-operations.md)

- [ユーザーの写真の残りの部分の API リファレンス](..\api\photo-rest-operations.md) 

- [バッチ Outlook の他の要求](#..\api\batch-outlook-rest-requests.md) (プレビュー)



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]


