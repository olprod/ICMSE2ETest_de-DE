---
ms.TocTitle: Outlook Contacts REST API reference
title: "Outlook の連絡先の REST API リファレンス"
Description: "Office 365 の取引先担当者の REST API およびクライアント ライブラリ Api では、ユーザーの連絡先へのアクセスを提供し、連絡先フォルダーには、Exchange オンラインと対話する方法を参照してください。"
ms.ContentId: dcfb466f-0faf-4015-971f-aab4f8fc9c07
ms.date: July 20, 2016
ms.openlocfilehash: 4b7dc71667b12ae162dab1743bb634768e2f0d70
ms.sourcegitcommit: 3f7951e0d1cd486dcad11b39b27f2fb7d8b41d14
translationtype: MT
---
[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="a-nameoutlook-contacts-rest-api-referenceaoutlook-rest-api-"></a><a name="outlook-contacts-rest-api-reference"></a>Outlook の連絡先の REST API リファレンス

[!INCLUDE [Add the Outlook REST API filters--v2 default](../includes/controls/addOutlookVersion_v2default.html)]


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<p class="previewnote">このドキュメントでは、ベータ版のプレビューでは、連絡先フォルダーの連絡先を同期するについて説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 可能な場合、バージョン 2.0 は現在推奨されるバージョンです。</p>

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->

  
 _**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_


<a name="Overview"></a>[Outlook 連絡先の API には、ユーザーの連絡先と連絡先フォルダーが、Office 365 で、Azure Active Directory によってセキュリティで保護およびこれらのドメインで具体的には Microsoft アカウントの類似したデータへのアクセスが用意されています: Hotmail.com、Live.com である MSN.com、Outlook.com、および Passport.com。


<!-- Can add the following sentence back once the client libraries have been updated for converged auth and outlook.com
You can access the Contacts API by calling the corresponding REST APIs directly in your apps, or by using the Office 365 client libraries and SDKs.
-->

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**API のベータ版では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**API のバージョン 2.0 では関係ないですか?** 右上のコントロールを使用し、使用バージョンを選択します。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

**API の 1.0 では関係ないですか?** 右上のコントロールを使用し、使用バージョンを選択します。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->




##<a name="a-nameall-contacts-api-operationsa-api-"></a><a name="all-contacts-api-operations"></a>連絡先 API のすべての操作

<a name="ContactOperations"></a> 
**操作にお問い合わせください**連絡先は、連絡先フォルダーに格納されています。 ことができますを取得、作成、変更、および連絡先を削除します。

[連絡先を取得する](#GetContacts) | 。[同期の連絡先や連絡先フォルダー](#SyncContacts) (プレビュー) [連絡先の作成](#CreateContacts)  | [連絡先を更新する](#UpdateContacts) | [の連絡先を削除](#DeleteContacts)

<a name="ContactFoldersOperations"></a> 
**フォルダーの管理にお問い合わせください**連絡先フォルダーは、連絡先およびその他の連絡先フォルダーを含めることができます。 連絡先フォルダーを取得し、連絡先フォルダーに連絡先を作成できます。

[連絡先フォルダーを取得します。](#GetContactFolders)

**連絡先の写真の操作**各連絡先には、省略可能な連絡先の写真を持つことができます。 取得または、連絡先の写真を設定することができます。

[Abrufen von 連絡先の写真を](#GetContactPhotoandMetadata) | [セットの連絡先の写真](#SetContactPhoto)

参照してください。

[REST-API 連絡先のリソースの](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource) |
には、フォルダーのリソースがお問い合わせください。[REST-API ](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)


## <a name="a-nameusing-the-contacts-rest-apia-rest-api-"></a><a name="using-the-contacts-rest-api"></a>連絡先の REST-API を使用します。

###<a name="a-nameauthenticationa"></a><a name="authentication"></a>認証

他の[REST-API の Outlook](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)で連絡先 API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 連絡先 API では、特定の操作を続行するには、この点に留意してください。

<a name="SupportedVersions"> </a>

###<a name="a-nameversion-of-apiaapi-"></a><a name="version-of-api"></a>API のバージョン

連絡先の REST-API は、Outlook の REST-API のすべてのバージョンでサポートされてです。 機能は、特定のバージョンによって異なる場合があります。

###<a name="a-nametarget-usera-"></a><a name="target-user"></a>ターゲット ユーザー

連絡先 API 要求は、現在のユーザーに代わって実行されます。 

Outlook-REST-API の詳細についてはすべてのサブセットに一般的な[Outlook の REST-API の使用](..\api\use-outlook-rest-api.md)を参照してください。

****

<a name="GetContacts"> </a>
##<a name="a-nameget-contactsa"></a><a name="get-contacts"></a>連絡先を取得します。

連絡先のコレクション、または個々 の連絡先を連絡先フォルダーから取得できます。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

<a name="GetContactCollection"> </a>
###<a name="a-nameget-a-contact-collectiona"></a><a name="get-a-contact-collection"></a>連絡先のコレクションを取得します。

サインインしているユーザーのメールボックス内のすべての連絡先を取得する (`.../me/contacts`) 、または連絡先フォルダーを指定したからです。

```no-highlight
GET https://outlook.office.com/api/beta/me/contacts
GET https://outlook.office.com/api/beta/me/contactfolders/{contact_folder_id}/contacts
```


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定のフォルダーから連絡先を取得している場合です。|

**メモ**既定では、応答では、各連絡先には、すべてのプロパティが含まれています。 **$Select**を使用すると、パフォーマンスを最適化する必要があるプロパティだけを指定します。 **ID**プロパティが常に返されます。 フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/contacts?$select=EmailAddresses,GivenName,Surname
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Contacts(EmailAddresses,GivenName,Surname)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGI2THk3AAA=')",
            "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa7\"",
            "Id": "AAMkAGI2THk3AAA=",
            "GivenName": "Rob",
            "Surname": "Young",
            "EmailAddresses": [
                {
                    "Name": "roby@a830edad9050849NDA1.onmicrosoft.com",
                    "Address": "roby@a830edad9050849NDA1.onmicrosoft.com"
                }
            ]
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGI2THkzAAA=')",
            "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa3\"",
            "Id": "AAMkAGI2THkzAAA=",
            "GivenName": "Janet",
            "Surname": "Schorr",
            "EmailAddresses": [
                {
                    "Name": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com"
                }
            ]
        }
    ]
}
```


**応答の種類**

[連絡先](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の要求されたコレクションです。

*****

<a name="GetContact"> </a>
###<a name="a-nameget-a-contacta"></a><a name="get-a-contact"></a>連絡先を取得します。

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_


連絡先を使用して連絡先を取得する id。

```no-highlight
GET https://outlook.office.com/api/beta/me/contacts/{contact_id}
```


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|

 **応答の種類**

要求[にお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。


**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/contacts/AAMkADlkAAAMRFUEAAA=
```

**応答の例**

```
Status code: 200

{
    "@odata.context":"https://outlook.office365.com/api/beta/$metadata#Me/Contacts/$entity",
    "@odata.id":"https://outlook.office365.com/api/beta/Users('af183ae6-7efa-41e4-aa87-fe8790598625@9ac5b33f-49cf-45f7-9ef1-b581dce364d8')/Contacts('AAMkADlkAAAMRFUEAAA=')",
    "@odata.etag":"W/\"EQAAABYAAADDii8zlkFETIcBiRn8yAbgAAAMRdhl\"",
    "Id":"AAMkADlkAAAMRFUEAAA=",
    "CreatedDateTime":"2016-07-16T06:43:15Z",
    "LastModifiedDateTime":"2016-07-16T06:43:15Z",
    "ChangeKey":"EQAAABYAAADDii8zlkFETIcBiRn8yAbgAAAMRdhl",
    "Categories":[
    ],
    "ParentFolderId":"AAMkADlk8yAbgAAAAAAEkAAA=",
    "Birthday":null,
    "FileAs":"",
    "DisplayName":"Garret Vargas",
    "GivenName":"Garret",
    "Initials":null,
    "MiddleName":null,
    "NickName":null,
    "Surname":"Vargas",
    "Title":null,
    "YomiGivenName":null,
    "YomiSurname":null,
    "YomiCompanyName":null,
    "Generation":null,
    "EmailAddresses":[
        {
            "Name":"Garret Vargas",
            "Address":"GarretV@contoso.onmicrosoft.com"
        }
    ],
    "Websites":[
    ],
    "ImAddresses":[
        "sip:garretv@contoso.onmicrosoft.com"
    ],
    "JobTitle":"CVP Operations",
    "CompanyName":"",
    "Department":"Operations",
    "OfficeLocation":"36/2121",
    "Profession":null,
    "AssistantName":null,
    "Manager":null,
    "Phones":[
        {
            "Type":"Home",
            "Number":""
        },
        {
            "Type":"Business",
            "Number":"+1 206 555 0105"
        },
        {
            "Type":"Mobile",
            "Number":""
        }
    ],
    "PostalAddresses":[
        {
            "Type":"Business",
            "City":"Seattle"
        }
    ],
    "SpouseName":null,
    "PersonalNotes":null,
    "Children":[
    ],
    "Gender":null,
    "IsFavorite":null,
    "Flag":{
        "FlagStatus":"NotFlagged"
    }
}
```



**メモ**既定では、応答には、連絡先のすべてのプロパティが含まれています。 **$Select**を使用すると、パフォーマンスを最適化する必要があるプロパティだけを指定します。 **ID**プロパティが常に返されます。 フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**$Select**を使用して応答に連絡先の**EmailAddresses**、**名**と**姓**のプロパティのみを返すことを指定するのには次の例を次に示します。


**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/contacts/AAMkAGI2THk0AAA=?$select=EmailAddresses,GivenName,Surname
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Contacts(EmailAddresses,GivenName,Surname)/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('af183ae6-7efa-41e4-aa87-fe8790598625@9ac5b33f-49cf-45f7-9ef1-b581dce364d8')/Contacts('AAMkADlkAAAMRFUEAAA=')",
    "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa4\"",
    "Id": "AAMkADlkAAAMRFUEAAA=",
    "GivenName": "Garth",
    "Surname": "Vargas",
    "EmailAddresses": [
       {
            "Name":"Garret Vargas",
            "Address":"GarretV@contoso.onmicrosoft.com"
        }
    ]
}
```


****

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

<a name="GetContactCollection"> </a>
###<a name="a-nameget-a-contact-collectiona"></a><a name="get-a-contact-collection"></a>連絡先のコレクションを取得します。

サインイン中のユーザーの既定の連絡先フォルダーから連絡先のコレクションを取得する (`.../me/contacts`) 、または連絡先フォルダーを指定したからです。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/contacts
GET https://outlook.office.com/api/v2.0/me/contactfolders/{contact_folder_id}/contacts
```


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定のフォルダーから連絡先を取得している場合です。|

**メモ**既定では、応答では、各連絡先には、すべてのプロパティが含まれています。 **$Select**を使用すると、パフォーマンスを最適化する必要があるプロパティだけを指定します。 **ID**プロパティが常に返されます。 フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。


**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/contacts?$select=EmailAddresses,GivenName,Surname
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Contacts(EmailAddresses,GivenName,Surname)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGI2THk3AAA=')",
            "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa7\"",
            "Id": "AAMkAGI2THk3AAA=",
            "GivenName": "Rob",
            "Surname": "Young",
            "EmailAddresses": [
                {
                    "Name": "roby@a830edad9050849NDA1.onmicrosoft.com",
                    "Address": "roby@a830edad9050849NDA1.onmicrosoft.com"
                }
            ]
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGI2THkzAAA=')",
            "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa3\"",
            "Id": "AAMkAGI2THkzAAA=",
            "GivenName": "Janet",
            "Surname": "Schorr",
            "EmailAddresses": [
                {
                    "Name": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com"
                }
            ]
        }
    ]
}
```


**応答の種類**

[連絡先](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の要求されたコレクションです。

****

<a name="GetContact"> </a>
###<a name="a-nameget-a-contacta"></a><a name="get-a-contact"></a>連絡先を取得します。

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_


連絡先を使用して連絡先を取得する id。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/contacts/{contact_id}
```


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|


**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/contacts/AAMkAGI2THk0AAA=
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Contacts/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGI2THk0AAA=')",
    "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa4\"",
    "Id": "AAMkAGI2THk0AAA=",
    "CreatedDateTime": "2014-10-19T23:08:24Z",
    "LastModifiedDateTime": "2014-10-19T23:08:24Z",
    "ChangeKey": "EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa4",
    "Categories": [],
    "ParentFolderId": "AAMkAGI2AAEOAAA=",
    "Birthday": null,
    "FileAs": "Fort, Garth",
    "DisplayName": "Garth Fort",
    "GivenName": "Garth",
    "Initials": "G.F.",
    "MiddleName": null,
    "NickName": "Garth",
    "Surname": "Fort",
    "Title": null,
    "YomiGivenName": null,
    "YomiSurname": null,
    "YomiCompanyName": null,
    "Generation": null,
    "EmailAddresses": [
        {
            "Name": "Garth",
            "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
    ],
    "ImAddresses": [
        "sip:garthf@a830edad9050849nda1.onmicrosoft.com"
    ],
    "JobTitle": "Web Marketing Manager",
    "CompanyName": "Contoso, Inc.",
    "Department": "Sales & Marketing",
    "OfficeLocation": "20/1101",
    "Profession": null,
    "BusinessHomePage": "http://www.contoso.com",
    "AssistantName": null,
    "Manager": null,
    "HomePhones": [],
    "MobilePhone1": null,
    "BusinessPhones": [
        "+1 918 555 0101"
    ],
    "HomeAddress": {},
    "BusinessAddress": {
      "Street": "10 Contoso Way",
      "City": "Redmond",
      "State": "WA",
      "CountryOrRegion": "USA",
      "PostalCode": "98075"  
    },
    "OtherAddress": {},
    "SpouseName": null,
    "PersonalNotes": null,
    "Children": []
}
```


 **応答の種類**

要求[にお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。

**メモ**既定では、応答には、連絡先のすべてのプロパティが含まれています。 **$Select**を使用すると、パフォーマンスを最適化する必要があるプロパティだけを指定します。 **ID**プロパティが常に返されます。 フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**$Select**を使用して応答に連絡先の**EmailAddresses**、**名**と**姓**のプロパティのみを返すことを指定するのには次の例を次に示します。

**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/contacts/AAMkAGI2THk0AAA=?$select=EmailAddresses,GivenName,Surname
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Contacts(EmailAddresses,GivenName,Surname)/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGI2THk0AAA=')",
    "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa4\"",
    "Id": "AAMkAGI2THk0AAA=",
    "GivenName": "Garth",
    "Surname": "Fort",
    "EmailAddresses": [
        {
            "Name": "garthf@a830edad9050849NDA1.onmicrosoft.com",
            "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
    ]
}
```

****

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]


REST-API: の[連絡先のコレクション (残りの部分) を取得する](#GetContactCollection) | の取引先担当者を取得します。[(残りの部分) ](#GetContact)

クライアント ライブラリ:[既定の連絡先フォルダー (クライアント) から連絡先を取得します。 ](#GetContactsClient)

<a name="GetContactCollection"> </a>
###<a name="a-nameget-a-contact-collection-restarest-"></a><a name="get-a-contact-collection-rest"></a>(REST) 連絡先のコレクションを取得します。

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

サインイン中のユーザーの既定の連絡先フォルダーから連絡先のコレクションを取得する (`.../me/contacts`) 、または連絡先フォルダーを指定したからです。

```no-highlight
GET https://outlook.office.com/api/v1.0/me/contacts
GET https://outlook.office.com/api/v1.0/me/contactfolders/{contact_folder_id}/contacts
```


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定のフォルダーから連絡先を取得している場合です。|

**メモ**既定では、応答では、各連絡先には、すべてのプロパティが含まれています。 **$Select**を使用すると、パフォーマンスを最適化する必要があるプロパティだけを指定します。 **ID**プロパティが常に返されます。 フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**$Select**を使用して応答に各取引先担当者の**EmailAddresses**、**名**と**姓**のプロパティのみを返すことを指定するのには次の例を次に示します。 **$Select**を使用しない場合の連絡先に対して返されるプロパティの完全なリストの[連絡先 (残りの部分) を取得](#GetContact)することでサンプルの応答を参照してください。

[!code-REST-i[contacts_api_get_contacts.JSON](./_data/contacts_api_get_contacts.json)]


 **応答の種類**

[連絡先](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の要求されたコレクションです。


****


<a name="GetContact"> </a>
###<a name="a-nameget-a-contact-resta-"></a><a name="get-a-contact-rest"></a>を取得します。 連絡先 (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_


連絡先を使用して連絡先を取得する id。

```no-highlight
GET https://outlook.office.com/api/{version}/me/contacts/{contact_id}
```


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|version|string|API の[バージョン](#SupportedVersions)です。|
|contact_id|string|連絡先の id。|


[!code-REST-i[contacts_api_contact_get_contact_by_id](./_data/contacts_api_contact_get_contact_by_id.json)]

 **応答の種類**

要求[にお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。

**メモ**既定では、応答には、連絡先のすべてのプロパティが含まれています。 **$Select**を使用すると、パフォーマンスを最適化する必要があるプロパティだけを指定します。 **ID**プロパティが常に返されます。 フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**$Select**を使用して応答に連絡先の**EmailAddresses**、**名**と**姓**のプロパティのみを返すことを指定するのには次の例を次に示します。

[!code-REST-i[contacts_api_contact_get_contact_by_id_select](./_data/contacts_api_contact_get_contact_by_id_select.json)]

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

****

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



<a name="GetContactsClient"> </a>
###から連絡先を取得します。 既定の連絡先フォルダー (クライアント)

既定の連絡先フォルダーから連絡先を取得します。 連絡先を指定して特定の連絡先を取得するには、 **GetById**メソッドを使用して、**取引先担当者**のコレクションのインデックスとしての-ID です。

例:`outlookClient.Me.Contacts[contactId].ExecuteAsync()`


**注意** Outlook.com 上のメールボックス データにアクセスする場合はクライアント ライブラリを使用されず、REST API を直接呼び出します。


**メモ**連絡先のコレクションは、**選択**、**並べ替え**、および**実行**のようなクエリ式をサポートします。

次の使用例は、 [Outlook のサービス クライアントを作成](#GetClient)するメソッドを呼び出します。

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Contacts" -->

```cs-i
var outlookClient = await CreateOutlookClientAsync("Contacts");
var contacts= await outlookClient.Me.Contacts
  .OrderBy(c => c.DisplayName)
  .Take(10)
  .ExecuteAsync();

foreach(var contact in contacts.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine(contact.DisplayName);
  foreach(var emailAddress in contact.EmailAddresses)
  {
    if (emailAddress != null)
    {
      System.Diagnostics.Debug.WriteLine("*  {0}", emailAddress.Address);
    }
  }
}

```
```javascript-i
outlookClient.me.contacts.getContacts().orderBy('DisplayName asc').fetch().then(
function (result) {
    result.currentPage.forEach(function (contact) {
        console.log(contact.displayName);
contact.emailAddresses.forEach(function(emailAddress) {
console.log('*  ' + emailAddress.address);
});
    });
}, function(error) {
    console.log(error);
}
);
```

<!-- ENDSECTION -->


****

<a name="SyncContacts"> </a>
##<a name="a-namesynchronize-contacts-and-contact-folders-previewa-"></a><a name="synchronize-contacts-and-contact-folders-preview"></a>連絡先を同期して、連絡先フォルダー (プレビュー)

ローカルの連絡先の一覧は、サーバー上の連絡先と同期できます。 連絡先の同期は、フォルダーごとの操作のすべての連絡先をルートの連絡先フォルダーに同期するなどです。 その他の連絡先フォルダーがある場合は、各フォルダーを個別に同期する必要があります。

同期は、完全同期のみサポートしています。 各要求には、指定したフォルダー内のすべての連絡先が返されます。

通常、 [連絡先] フォルダーを同期するには、2 つまたは複数の GET 要求が必要です。 取得を行う要求より方法と同じようにして[連絡先を取得する](#GetContacts)には、以下の要求ヘッダーを追加することを除いて。

- 指定する必要があります、_選択: odata.track 変更_のすべての同期要求のヘッダーです。
- 指定することは、_選択: odata.maxpages={n}_連絡先の最大数を設定するのにはヘッダーが各要求で返されます。
  
  2 番目およびそれ以降の GET 要求は、 _DeltaToken_または前の応答で受信した_SkipToken_のいずれかを含めることにより最初の GET 要求とは異なります。
  
  同期要求に対する初回の応答は、常に、 _DeltaToken_を返します。 常に_DeltaToken_を使用して、追加の連絡先があるかどうかを決定する 2 つ目の GET 要求をする必要があります。 2 番目の要求を返します他の連絡先とするか、 _SkipToken_がある場合複数の連絡先、または、 _DeltaToken_最後の連絡先に送信された場合。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

```no-highlight
GET https://outlook.office.com/api/beta/me/Contacts
GET https://outlook.office.com/api/beta/me/ContactFolders/{folderName}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_ヘッダーのパラメーター_|
|好む|OData.Track 変更|要求が同期要求であることを示します。|
|好む|OData.MaxPageSize|各応答で返される連絡先の数を設定します。|
|_URL-パラメーター_|
|フォルダー名|string|同期するフォルダーの名前。|
|odata.deltaLink|String|このトークンは、最後に、フォルダーが同期されていることを示します。|
|OData.skiptoken|String|このトークンより多くのメッセージをダウンロードすることを示します。|

**応答の種類**

要求された取引先担当者とサーバーから他のページの連絡先データを要求して、差分同期を要求するために使用する_DeltaToken_を含むコレクションです。 連絡先の数が返された場合は、複数のページで、応答が返されます_odata.maxpagesize_ヘッダーで指定された値を超えるです。

応答が含まれます、_の設定で適用した: Odata Trackchanges_ヘッダー。 サポートされていないリソースを同期しようとすると、このヘッダーは、応答で返されません。 エラーを回避するのには応答を処理する前に、このヘッダーを確認します。

**メモ**既定では、応答には、指定した連絡先のプロパティのすべてが含まれます。 _$Select_を使用してプロパティだけを指定する最適なパフォーマンスの必要性。 **ID**プロパティが常に返されます。 連絡先の同期はサポートされていません、または、連絡先フォルダーには、 $Filter、$ Orderby、$ Search または $top を使用しません。 詳細については、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**例**

完全な同期の開始要求

 ```no-highlight
GET https://outlook.office.com/api/beta/Me/Contacts
```

次のヘッダーが含まれます。
* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

完全な同期要求の後サーバーに 2 番目の要求。

```no-highlight
https://outlook.office.com/api/beta/Me/Contacts/?%24deltatoken=169ca50467d34d9fb8adb664961b9836
```
次のヘッダーが含まれます。

* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

利用可能なその他のページを使用してサーバーから 2 番目の応答します。

ヘッダー

OData.Track 変更の優先順位が適用されます。

Body

@odata.deltaLink=https://Outlook.Office.com/API/Beta/Me/Contacts/Messages/?%24skiptoken=169ca50467d34d9fb8adb664961b9836

_ペイロードのメッセージ_

すべての連絡先が送信されたときにサーバーから 2 番目以降の応答です。

ヘッダー

OData.Track 変更の優先順位が適用されます。

Body

@odata.deltaLink=https://Outlook.Office.com/API/Beta/Me/Contacts/?%24deltatoken=169ca50467d34d9fb8adb664961b9836

_ペイロードのメッセージ_

追加のページが利用できる場合は、サーバーに要求します。

```no-highlight
https://outlook.office.com/api/beta/Me/Contacts/?%24skiptoken=169ca50467d34d9fb8adb664961b9836
```
次のヘッダーが含まれます。

* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

```no-highlight
GET https://outlook.office.com/api/v2.0/me/Contacts
GET https://outlook.office.com/api/v2.0/me/ContactFolders/{folderName}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_ヘッダーのパラメーター_|
|好む|OData.Track 変更|要求が同期要求であることを示します。|
|好む|OData.MaxPageSize|各応答で返される連絡先の数を設定します。|
|_URL-パラメーター_|
|フォルダー名|string|同期するフォルダーの名前。|
|odata.deltaLink|String|このトークンは、最後に、フォルダーが同期されていることを示します。|
|OData.skiptoken|String|このトークンより多くのメッセージをダウンロードすることを示します。|

**応答の種類**

要求された取引先担当者とサーバーから他のページの連絡先データを要求して、差分同期を要求するために使用する_DeltaToken_を含むコレクションです。 連絡先の数が返された場合は、複数のページで、応答が返されます_odata.maxpagesize_ヘッダーで指定された値を超えるです。

応答が含まれます、_の設定で適用した: Odata Trackchanges_ヘッダー。 サポートされていないリソースを同期しようとすると、このヘッダーは、応答で返されません。 エラーを回避するのには応答を処理する前に、このヘッダーを確認します。

**メモ**既定では、応答には、指定した連絡先のプロパティのすべてが含まれます。 _$Select_を使用してプロパティだけを指定する最適なパフォーマンスの必要性。 **ID**プロパティが常に返されます。 連絡先の同期はサポートされていません、または、連絡先フォルダーには、 $Filter、$ Orderby、$ Search または $top を使用しません。 詳細については、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**例**

完全な同期の開始要求

 ```no-highlight
GET https://outlook.office.com/api/v2.0/Me/Contacts
```

次のヘッダーが含まれます。
* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

完全な同期要求の後サーバーに 2 番目の要求。

```no-highlight
https://outlook.office.com/api/v2.0/Me/Contacts/?%24deltatoken=169ca50467d34d9fb8adb664961b9836
```
次のヘッダーが含まれます。

* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

利用可能なその他のページを使用してサーバーから 2 番目の応答します。

ヘッダー

OData.Track 変更の優先順位が適用されます。

Body

@odata.deltaLink=https://Outlook.Office.com/API/v2.0/Me/Contacts/Messages/?%24skiptoken=169ca50467d34d9fb8adb664961b9836

_ペイロードのメッセージ_

すべての連絡先が送信されたときにサーバーから 2 番目以降の応答です。

ヘッダー

OData.Track 変更の優先順位が適用されます。

Body

@odata.deltaLink=https://Outlook.Office.com/API/v2.0/Me/Contacts/?%24deltatoken=169ca50467d34d9fb8adb664961b9836

_ペイロードのメッセージ_

追加のページが利用できる場合は、サーバーに要求します。

```no-highlight
https://outlook.office.com/api/v2.0/Me/Contacts/?%24skiptoken=169ca50467d34d9fb8adb664961b9836
```
次のヘッダーが含まれます。

* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

```no-highlight
GET https://outlook.office.com/api/v1.0/me/Contacts
GET https://outlook.office.com/api/v1.0/me/ContactFolders/{folderName}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_ヘッダーのパラメーター_|
|好む|OData.Track 変更|要求が同期要求であることを示します。|
|好む|OData.MaxPageSize|各応答で返される連絡先の数を設定します。|
|_URL-パラメーター_|
|フォルダー名|string|同期するフォルダーの名前。|
|odata.deltaLink|String|このトークンは、最後に、フォルダーが同期されていることを示します。|
|OData.skiptoken|String|このトークンより多くのメッセージをダウンロードすることを示します。|

**応答の種類**

要求された取引先担当者とサーバーから他のページの連絡先データを要求して、差分同期を要求するために使用する_DeltaToken_を含むコレクションです。 連絡先の数が返された場合は、複数のページで、応答が返されます_odata.maxpagesize_ヘッダーで指定された値を超えるです。

応答が含まれます、_の設定で適用した: Odata Trackchanges_ヘッダー。 サポートされていないリソースを同期しようとすると、このヘッダーは、応答で返されません。 エラーを回避するのには応答を処理する前に、このヘッダーを確認します。

**メモ**既定では、応答には、指定した連絡先のプロパティのすべてが含まれます。 _$Select_を使用してプロパティだけを指定する最適なパフォーマンスの必要性。 **ID**プロパティが常に返されます。 連絡先の同期はサポートされていません、または、連絡先フォルダーには、 $Filter、$ Orderby、$ Search または $top を使用しません。 詳細については、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。

**例**

完全な同期の開始要求

 ```no-highlight
GET https://outlook.office.com/api/v1.0/Me/Contacts
```

次のヘッダーが含まれます。
* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

完全な同期要求の後サーバーに 2 番目の要求。

```no-highlight
https://outlook.office.com/api/v1.0/Me/Contacts/?%24deltatoken=169ca50467d34d9fb8adb664961b9836
```
次のヘッダーが含まれます。

* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

利用可能なその他のページを使用してサーバーから 2 番目の応答します。

ヘッダー

OData.Track 変更の優先順位が適用されます。

Body

@odata.deltaLink=https://Outlook.Office.com/API/v1.0/Me/Contacts/Messages/?%24skiptoken=169ca50467d34d9fb8adb664961b9836

_ペイロードのメッセージ_

すべての連絡先が送信されたときにサーバーから 2 番目以降の応答です。

ヘッダー

OData.Track 変更の優先順位が適用されます。

Body

@odata.deltaLink=https://Outlook.Office.com/API/v1.0/Me/Contacts/?%24deltatoken=169ca50467d34d9fb8adb664961b9836

_ペイロードのメッセージ_

追加のページが利用できる場合は、サーバーに要求します。

```no-highlight
https://outlook.office.com/api/v1.0/Me/Contacts/?%24skiptoken=169ca50467d34d9fb8adb664961b9836
```
次のヘッダーが含まれます。

* OData.Track の変更を希望します。
* 好む: odata.maxpagesize=100

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->
 
 ****

<a name="CreateContacts"> </a>
##<a name="a-namecreate-contactsa"></a><a name="create-contacts"></a>連絡先を作成します。

指定した連絡先フォルダーに連絡先を作成します。

REST-API:[の連絡先を作成 (残りの部分)](#CreateAContact)

クライアント ライブラリ:[での連絡先を作成 既定の連絡先フォルダー (クライアント)](#CreateContactsClient)

<a name="CreateAContact"></a>
###<a name="a-namecreate-a-contact-resta-"></a><a name="create-a-contact-rest"></a>を作成します。 連絡先 (残りの部分)

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

ルートの連絡先フォルダーまたは連絡先を追加する、`contacts`連絡先フォルダーを別のエンドポイントです。

```no-highlight
POST https://outlook.office.com/api/beta/me/contacts
POST https://outlook.office.com/api/beta/me/contactfolders/{contact_folder_id}/contacts
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定の連絡先フォルダーに連絡先を作成する場合です。|
|_本文パラメーター_|
|Vorname|string|連絡先の名前。|

要求の本文で、**一定**のパラメーターとの[連絡](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の書き込み可能なプロパティを指定します。


**要求のサンプル**

```
POST https://outlook.office.com/api/beta/me/contacts
Content-Type: application/json

{
  "GivenName": "Pavel",
  "Surname": "Bansky",
  "EmailAddresses": [
    {
      "Address": "pavelb@contoso.onmicrosoft.com",
      "Name": "Pavel Bansky"
    }
  ],
  "Phones": [
    {
      "Type": "Business",
      "Number": "+1 732 555 0102"
    }
  ]
}
```

**応答の例**

```
Status code: 201

{
  "@odata.context":"https://outlook.office365.com/api/beta/$metadata#Me/Contacts/$entity",
  "@odata.id":"https://outlook.office365.com/api/beta/Users('af183ae6-7efa-41e4-aa87-fe8790598625@9ac5b33f-49cf-45f7-9ef1-b581dce364d8')/Contacts('AAMkADlkAAARKMK7AAA=')",
  "@odata.etag":"W/\"EQAAABYAAADDii8zlkFETIcBiRn8yAbgAAARKpia\"",
  "Id":"AAMkADlkAAARKMK7AAA=",
  "CreatedDateTime":"2016-07-20T23:59:37Z",
  "LastModifiedDateTime":"2016-07-20T23:59:38Z",
  "ChangeKey":"EQAAABYAAADDii8zlkFETIcBiRn8yAbgAAARKpia",
  "Categories":[
  ],
  "ParentFolderId":"AAMkADlk8yAbgAAAAAAEOAAA=",
  "Birthday":null,
  "FileAs":"",
  "DisplayName":"Pavel Bansky",
  "GivenName":"Pavel",
  "Initials":null,
  "MiddleName":null,
  "NickName":null,
  "Surname":"Bansky",
  "Title":null,
  "YomiGivenName":null,
  "YomiSurname":null,
  "YomiCompanyName":null,
  "Generation":null,
  "EmailAddresses":[
    {
      "Name":"Pavel Bansky",
      "Address":"pavelb@contoso.onmicrosoft.com"
    }
  ],
  "Websites":[
  ],
  "ImAddresses":[
  ],
  "JobTitle":null,
  "CompanyName":null,
  "Department":null,
  "OfficeLocation":null,
  "Profession":null,
  "AssistantName":null,
  "Manager":null,
  "Phones":[
    {
      "Type":"Business",
      "Number":"+1 732 555 0102"
    }
  ],
  "PostalAddresses":[
  ],
  "SpouseName":null,
  "PersonalNotes":null,
  "Children":[
  ],
  "Gender":null,
  "IsFavorite":null,
  "Flag":{
    "FlagStatus":"NotFlagged"
  }
}
```


 **応答の種類**

新規[にお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

ルートの連絡先フォルダーまたは連絡先を追加する、`contacts`連絡先フォルダーを別のエンドポイントです。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/contacts
POST https://outlook.office.com/api/v2.0/me/contactfolders/{contact_folder_id}/contacts
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定の連絡先フォルダーに連絡先を作成する場合です。|
|_本文パラメーター_|
|Vorname|string|連絡先の名前。|

要求の本文で、**一定**のパラメーターとの[連絡](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の書き込み可能なプロパティを指定します。


**要求のサンプル**

```
POST https://outlook.office.com/api/v2.0/me/contacts
Content-Type: application/json

{
  "GivenName": "Pavel",
  "Surname": "Bansky",
  "EmailAddresses": [
    {
      "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Pavel Bansky"
    }
  ],
  "BusinessPhones": [
    "+1 732 555 0102"
  ]
}
```

**応答の例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Contacts/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGE0M4xqVAAA=')",
  "@odata.etag": "W/\"EQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAV41eC\"",
  "Id": "AAMkAGE0M4xqVAAA=",
  "ChangeKey": "EQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAV41eC",
  "Categories": [],
  "CreatedDateTime": "2014-10-22T20:38:18Z",
  "LastModifiedDateTime": "2014-10-22T20:38:19Z",
  "ParentFolderId": "AAMkAGE0MAAEOAAA=",
  "Birthday": null,
  "FileAs": "",
  "DisplayName": "Pavel Bansky",
  "GivenName": "Pavel",
  "Initials": null,
  "MiddleName": null,
  "NickName": null,
  "Surname": "Bansky",
  "Title": null,
  "Generation": null,
  "EmailAddresses": [
    {
      "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Pavel Bansky"
    },
    null,
    null
  ],
  "ImAddresses": [
    null,
    null,
    null
  ],
  "JobTitle": null,
  "CompanyName": null,
  "Department": null,
  "OfficeLocation": null,
  "Profession": null,
  "BusinessHomePage": null,
  "AssistantName": null,
  "Manager": null,
  "HomePhones": [
    null,
    null
  ],
  "BusinessPhones": [
    "+1 732 555 0102",
    null
  ],
  "MobilePhone1": null,
  "HomeAddress": {
    "Street": null,
    "City": null,
    "State": null,
    "CountryOrRegion": null,
    "PostalCode": null
  },
  "BusinessAddress": {
    "Street": null,
    "City": null,
    "State": null,
    "CountryOrRegion": null,
    "PostalCode": null
  },
  "OtherAddress": {
    "Street": null,
    "City": null,
    "State": null,
    "CountryOrRegion": null,
    "PostalCode": null
  },
  "SpouseName": null,
  "PersonalNotes": null,
  "Children": [],
  "YomiSurname": null,
  "YomiGivenName": null,
  "YomiCompanyName": null
}
```


 **応答の種類**

新規[にお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

ルートの連絡先フォルダーまたは連絡先を追加する、`contacts`連絡先フォルダーを別のエンドポイントです。

```no-highlight
POST https://outlook.office.com/api/v1.0/me/contacts
POST https://outlook.office.com/api/v1.0/me/contactfolders/{contact_folder_id}/contacts
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定の連絡先フォルダーに連絡先を作成する場合です。|
|_本文パラメーター_|
|Vorname|string|連絡先の名前。|

要求の本文で、**一定**のパラメーターとの[連絡](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の書き込み可能なプロパティを指定します。

[!code-REST-i[contacts_api_create_contact](./_data/contacts_api_create_contact.json)]

 **応答の種類**

新規[にお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。




[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

****

<a name="CreateContactsClient"> </a>
###<a name="a-namecreate-a-contact-in-the-default-contacts-folder-clienta-"></a><a name="create-a-contact-in-the-default-contacts-folder-client"></a>で連絡先を作成します。 既定の連絡先フォルダー (クライアント)

既定の連絡先フォルダーに連絡先を作成します。


**注意** Outlook.com 上のメールボックス データにアクセスする場合はクライアント ライブラリを使用されず、REST API を直接呼び出します。


この例では、既に[Outlook サービス クライアントを取得](#GetClient)します。


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
Contact newContact = new Contact
{
    GivenName = "Katie",
    Surname = "Jordan",
    JobTitle = "Auditor",
    Department = "Finance",
    BusinessPhones = { "+1 412 555 0109" },
    MobilePhone1 = "+1 412 555 9010",
    EmailAddresses = new List<EmailAddress>
    {
        new EmailAddress
        {
            Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    }
};
await client.Me.Contacts.AddContactAsync(newContact);

// Get the contact ID.
string contactId = newContact.Id;
```

<!-- ENDSECTION -->


****

<a name="UpdateContacts"> </a>
##<a name="a-nameupdate-contactsa"></a><a name="update-contacts"></a>連絡先を更新します。

連絡先のプロパティを変更します。

REST-API:[を更新 連絡先 (残りの部分)](#UpdateAContact)

クライアント ライブラリ:[の更新 取引先担当者 (クライアント)](#UpdateContactsClient)

<a name="UpdateAContact"></a>
###<a name="a-nameupdate-a-contact-restarest-"></a><a name="update-a-contact-rest"></a>(REST) 連絡先を更新します。

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

要求の本文に[お問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の書き込み可能なプロパティを指定します。 指定したプロパティのみが変更されます。

```no-highlight
PATCH https://outlook.office.com/api/beta/me/contacts/{contact_id}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|


**要求のサンプル**

```
PATCH https://outlook.office.com/api/beta/me/contacts/AAMkADlkAAARKMK7AAA=
Content-Type: application/json

{
  "PostalAddresses": [
    {
      "Type": "Business",
      "Street": "Some street",
      "City": "Seattle",
      "State": "WA",
      "PostalCode": "98121"
    }
  ]
  "Birthday": "1974-07-22"
}
```

**応答の例**

```
Status code: 200

{
  "@odata.context":"https://outlook.office365.com/api/beta/$metadata#Me/Contacts/$entity",
  "@odata.id":"https://outlook.office365.com/api/beta/Users('af183ae6-7efa-41e4-aa87-fe8790598625@9ac5b33f-49cf-45f7-9ef1-b581dce364d8')/Contacts('AAMkADlkAAARKMK7AAA=')",
  "@odata.etag":"W/\"EQAAABYAAADDii8zlkFETIcBiRn8yAbgAAARKpia\"",
  "Id":"AAMkADlkAAARKMK7AAA=",
  "CreatedDateTime":"2016-07-20T23:59:37Z",
  "LastModifiedDateTime":"2016-07-20T23:59:38Z",
  "ChangeKey":"EQAAABYAAADDii8zlkFETIcBiRn8yAbgAAARKpia",
  "Categories":[
  ],
  "ParentFolderId":"AAMkADlk8yAbgAAAAAAEOAAA=",
  "Birthday":"1974-07-22T00:00:00Z",
  "FileAs":"",
  "DisplayName":"Pavel Bansky",
  "GivenName":"Pavel",
  "Initials":null,
  "MiddleName":null,
  "NickName":null,
  "Surname":"Bansky",
  "Title":null,
  "YomiGivenName":null,
  "YomiSurname":null,
  "YomiCompanyName":null,
  "Generation":null,
  "EmailAddresses":[
    {
      "Name":"Pavel Bansky",
      "Address":"pavelb@contoso.onmicrosoft.com"
    }
  ],
  "Websites":[
  ],
  "ImAddresses":[
  ],
  "JobTitle":null,
  "CompanyName":null,
  "Department":null,
  "OfficeLocation":null,
  "Profession":null,
  "AssistantName":null,
  "Manager":null,
  "Phones":[
    {
      "Type":"Business",
      "Number":"+1 732 555 0102"
    }
  ],
  "PostalAddresses":[
    {
      "Type": "Business",
      "Street": "Some street",
      "City": "Seattle",
      "State": "WA",
      "PostalCode": "98121"
    }
  ],
  "SpouseName":null,
  "PersonalNotes":null,
  "Children":[
  ],
  "Gender":null,
  "IsFavorite":null,
  "Flag":{
    "FlagStatus":"NotFlagged"
  }
}
```

 **応答の種類**

更新[に問い合わせてください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

要求の本文に[お問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の書き込み可能なプロパティを指定します。 指定したプロパティのみが変更されます。

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/contacts/{contact_id}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|


**要求のサンプル**

```
PATCH https://outlook.office.com/api/v2.0/me/contacts/AAMkAGI2THkzAAA=
Content-Type: application/json

{
  "HomeAddress": {
    "Street": "Some street",
    "City": "Seattle",
    "State": "WA",
    "PostalCode": "98121"
  },
  "Birthday": "1974-07-22"
}
```

**応答の例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Contacts/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Contacts('AAMkAGI2THkzAAA=')",
  "@odata.etag": "W/\"EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa3\"",
  "Id": "AAMkAGI2THkzAAA=",
  "ChangeKey": "EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa3",
  "Categories": [],
  "CreatedDateTime": "2014-10-19T23:08:18Z",
  "LastModifiedDateTime": "2014-10-19T23:08:18Z",
  "ParentFolderId": "AAMkAGI2AAEOAAA=",
  "Birthday": "1974-07-22T00:00:00Z",
  "FileAs": "Schorr, Janet",
  "DisplayName": "Janet Schorr",
  "GivenName": "Janet",
  "Initials": null,
  "MiddleName": null,
  "NickName": null,
  "Surname": "Schorr",
  "Title": null,
  "Generation": null,
  "EmailAddresses": [
    {
      "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "janets@a830edad9050849NDA1.onmicrosoft.com"
    },
    null,
    null
  ],
  "ImAddresses": [
    "sip:janets@a830edad9050849nda1.onmicrosoft.com",
    null,
    null
  ],
  "JobTitle": "Product Marketing Manager",
  "CompanyName": null,
  "Department": "Sales &amp; Marketing",
  "OfficeLocation": "18/2111",
  "Profession": null,
  "BusinessHomePage": null,
  "AssistantName": null,
  "Manager": null,
  "HomePhones": [
    null,
    null
  ],
  "BusinessPhones": [
    "+1 425 555 0109",
    null
  ],
  "MobilePhone1": null,
  "HomeAddress": {
    "Street": "Some street",
    "City": "Seattle",
    "State": "WA",
    "CountryOrRegion": null,
    "PostalCode": "98121"
  },
  "BusinessAddress": {
    "Street": null,
    "City": null,
    "State": null,
    "CountryOrRegion": null,
    "PostalCode": null
  },
  "OtherAddress": {
    "Street": null,
    "City": null,
    "State": null,
    "CountryOrRegion": null,
    "PostalCode": null
  },
  "SpouseName": null,
  "PersonalNotes": null,
  "Children": [],
  "YomiSurname": null,
  "YomiGivenName": null,
  "YomiCompanyName": null
}
```

 **応答の種類**

更新[に問い合わせてください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

要求の本文に[お問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)の書き込み可能なプロパティを指定します。 指定したプロパティのみが変更されます。

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/contacts/{contact_id}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|


[!code-REST-i[contacts_api_update_contact_by_id](./_data/contacts_api_update_contact_by_id.json)]

 **応答の種類**

更新[に問い合わせてください](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)。



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

****

<a name="UpdateContactsClient"> </a>
###<a name="a-nameupdate-a-contact-clienta-"></a><a name="update-a-contact-client"></a>の更新します。 連絡先 (クライアント)


**注意** Outlook.com 上のメールボックス データにアクセスする場合はクライアント ライブラリを使用されず、REST API を直接呼び出します。


この例では、既に[Outlook サービス クライアントを取得](#GetClient)し、 [、連絡先を取得しました-ID](#GetContactsClient)。


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IContact contact = await client.Me.Contacts[contactId].ExecuteAsync();
contact.HomeAddress = new PhysicalAddress
{
    Street = "Some Street St",
    City = "Seattle",
    State = "WA",
    PostalCode = "98121"
};
await contact.UpdateAsync();

// Get an updated property.
string contactPostalCode = contact.HomeAddress.PostalCode;
```

<!-- ENDSECTION -->

、以下のパターンを使用しています。 複数の更新プログラムでクライアント側を定義し、要求を送信するすべてを一度に (それらのバッチ)
1. 呼び出す`UpdateAsync(true)`の各エンティティを更新します。 指定する`true`、クライアント上でローカルに更新プログラムを登録するが、サーバーにポストされません。
2. 呼び出す`client.Context.SaveChangesAsync()`ローカルに登録されているすべての更新プログラムを投稿します。

****


<a name="DeleteContacts"> </a>
##<a name="a-namedelete-contactsa"></a><a name="delete-contacts"></a>連絡先を削除します。

連絡先を削除します。 削除した内容は、回復できない場合があります。 詳細については、[要素を削除する](http://msdn.microsoft.com/library/c81e3160-e12b-47e0-b3d6-4be28537f301%28Office.15%29.aspx)を参照してください。
 
REST-API: の[を削除します。 連絡先 (残りの部分) ](#DeleteAContact)

クライアント ライブラリ:[連絡先 (クライアント) を削除します。 ](#DeleteContactsClient)

<a name="DeleteAContact"></a>
###<a name="a-namedelete-a-contact-restarest-"></a><a name="delete-a-contact-rest"></a>(REST) 連絡先を削除します。

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

```no-highlight
DELETE https://outlook.office.com/api/beta/me/contacts/{contact_id}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|


**要求のサンプル**

```
DELETE https://outlook.office.com/api/beta/me/contacts/AAMkAGE0Myy2hAAA=
```

**応答の例**

```
Status code: 204
```



[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/contacts/{contact_id}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|


**要求のサンプル**

```
DELETE https://outlook.office.com/api/v2.0/me/contacts/AAMkAGE0Myy2hAAA=
```

**応答の例**

```
Status code: 204
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]



_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/contacts/{contact_id}
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|連絡先の id。|


[!code-REST-i[contacts_api_delete_contact_by_id](./_data/contacts_api_delete_contact_by_id.json)]






[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


****

<a name="DeleteContactsClient"> </a>
###<a name="a-namedelete-a-contact-clienta-"></a><a name="delete-a-contact-client"></a>を削除します。 連絡先 (クライアント)


**注意** Outlook.com 上のメールボックス データにアクセスする場合はクライアント ライブラリを使用されず、REST API を直接呼び出します。


この例では、既に[Outlook サービス クライアントを取得](#GetClient)し、 [、連絡先を取得しました-ID](#GetContactsClient)。


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IContact contact = await client.Me.Contacts[contactId].ExecuteAsync();
await contact.DeleteAsync();
```

<!-- ENDSECTION -->

****

<a name="GetContactFolders"> </a>
##<a name="a-nameget-contact-foldersa"></a><a name="get-contact-folders"></a>連絡先フォルダーを取得します。

連絡先フォルダーのコレクションを取得するか、連絡先フォルダーを取得します。

REST-API:[の連絡先フォルダーのコレクションを取得 (残りの部分)](#GetContactFolderCollection)の | の連絡先フォルダーを取得します。 [(残りの部分) ](#GetContactFolder)

クライアント ライブラリ:[を取得 連絡先フォルダー (クライアント)](#GetContactFoldersClient)

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]



<a name="GetContactFolderCollection"> </a>
###<a name="a-nameget-a-contact-folder-collection-restarest-"></a><a name="get-a-contact-folder-collection-rest"></a>(REST) の連絡先フォルダーのコレクションを取得します。

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

サインインしているユーザーのメールボックス内のすべての連絡先フォルダーを取得する (`.../me/contactfolders`) 、または指定した連絡先フォルダーの下。

```no-highlight
GET https://outlook.office.com/api/beta/me/contactfolders
GET https://outlook.office.com/api/beta/me/contactfolders/{contact_folder_id}/childfolders
```

**メモ**フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定の連絡先フォルダーから連絡先フォルダーを取得している場合です。|


**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/contactfolders
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/ContactFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/ContactFolders('AAMkAGI2TKI5AAA=')",
            "Id": "AAMkAGI2TKI5AAA=",
            "ParentFolderId": "AAMkAGI2AAEOAAA=",
            "DisplayName": "Finance",
            "WellKnownName": null
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/ContactFolders('AQMkADA1MTgAAAA==')",
            "Id": "AQMkADA1MTgAAAA==",
            "ParentFolderId": "AAMkAGI2AAEOAAA=",
            "DisplayName": "Contacts",
            "WellKnownName": "contacts"
        }
    ]
}
```

**応答の種類**

要求された[連絡先フォルダー](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)のコレクションです。

****


<a name="GetContactFolder"> </a>
###<a name="a-nameget-a-contact-folder-resta-"></a><a name="get-a-contact-folder-rest"></a>を取得します。 連絡先フォルダー (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

連絡先フォルダーの ID を使用する連絡先フォルダーを取得します。

```no-highlight
GET https://outlook.office.com/api/beta/me/contactfolders/{contact_folder_id}
```

**メモ**フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダーの id。|


**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/contactfolders/AAMkAGI2TKI5AAA=
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/ContactFolders/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/ContactFolders('AAMkAGI2TKI5AAA=')",
    "Id": "AAMkAGI2TKI5AAA=",
    "ParentFolderId": "AAMkAGI2AAEOAAA=",
    "DisplayName": "Finance",
    "WellKnownName": null
}
```

 **応答の種類**

要求された[フォルダーにお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


<a name="GetContactFolderCollection"> </a>
###<a name="a-nameget-a-contact-folder-collection-restarest-"></a><a name="get-a-contact-folder-collection-rest"></a>(REST) の連絡先フォルダーのコレクションを取得します。

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

サインイン中のユーザーの既定の連絡先フォルダーの下にある連絡先フォルダーのコレクションを取得する (`.../me/contactfolders`) 、または指定した連絡先フォルダーの下。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/contactfolders
GET https://outlook.office.com/api/v2.0/me/contactfolders/{contact_folder_id}/childfolders
```

**メモ**フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定の連絡先フォルダーから連絡先フォルダーを取得している場合です。|


**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/contactfolders
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/ContactFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/ContactFolders('AAMkAGI2TKI5AAA=')",
            "Id": "AAMkAGI2TKI5AAA=",
            "ParentFolderId": "AAMkAGI2AAEOAAA=",
            "DisplayName": "Finance"
        }
    ]
}
```

**応答の種類**

要求された[連絡先フォルダー](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)のコレクションです。

****


<a name="GetContactFolder"> </a>
###<a name="a-nameget-a-contact-folder-resta-"></a><a name="get-a-contact-folder-rest"></a>を取得します。 連絡先フォルダー (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

連絡先フォルダーの-ID を使用する連絡先フォルダーを取得します。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/contactfolders/{contact_folder_id}
```

**メモ**フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダーの id。|


**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/contactfolders/AAMkAGI2TKI5AAA=
```

**応答の例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/ContactFolders/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/ContactFolders('AAMkAGI2TKI5AAA=')",
    "Id": "AAMkAGI2TKI5AAA=",
    "ParentFolderId": "AAMkAGI2AAEOAAA=",
    "DisplayName": "Finance"
}
```

 **応答の種類**

要求された[フォルダーにお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]



<a name="GetContactFolderCollection"> </a>
###<a name="a-nameget-a-contact-folder-collection-restarest-"></a><a name="get-a-contact-folder-collection-rest"></a>(REST) の連絡先フォルダーのコレクションを取得します。

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

サインイン中のユーザーの既定の連絡先フォルダーの下にある連絡先フォルダーのコレクションを取得する (`.../me/contactfolders`) 、または指定した連絡先フォルダーの下。

```no-highlight
GET https://outlook.office.com/api/v1.0/me/contactfolders
GET https://outlook.office.com/api/v1.0/me/contactfolders/{contact_folder_id}/childfolders
```

**メモ**フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダー ID、特定の連絡先フォルダーから連絡先フォルダーを取得している場合です。|


[!code-REST-i[contacts_api_contact_folder_get_collection_folder_path](./_data/contacts_api_contact_folder_get_collection_folder_path.json)]

 **応答の種類**

要求された[連絡先フォルダー](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)のコレクションです。

****


<a name="GetContactFolder"> </a>
###<a name="a-nameget-a-contact-folder-resta-"></a><a name="get-a-contact-folder-rest"></a>を取得します。 連絡先フォルダー (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

連絡先フォルダーの ID を使用する連絡先フォルダーを取得します。

```no-highlight
GET https://outlook.office.com/api/v1.0/me/contactfolders/{contact_folder_id}
```

**メモ**フィルター処理、並べ替え、およびページングのパラメーターには、 [OData クエリのパラメーター](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)を参照してください。


|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_folder_id|string|連絡先フォルダーの id。|

[!code-REST-i[contacts_api_contact_get_contact_folder_by_id](./_data/contacts_api_contact_get_contact_folder_by_id.json)]


 **応答の種類**

要求された[フォルダーにお問い合わせください](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource)。


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


****

<a name="GetContactFoldersClient"> </a>
###<a name="a-nameget-contact-folders-clienta-"></a><a name="get-contact-folders-client"></a>を取得します。 連絡先フォルダー (クライアント)

既定の連絡先フォルダーの連絡先フォルダーを取得します。 特定の連絡先フォルダーを取得するには、 **ContactFolders**コレクションのインデックスとしてフォルダー ID を指定または**GetById**メソッドを使用します。

例:`client.Me.ContactFolders[folderId].ExecuteAsync()`


**注意** Outlook.com 上のメールボックス データにアクセスする場合はクライアント ライブラリを使用されず、REST API を直接呼び出します。


**メモ**連絡先フォルダー コレクション サポート クエリのような式**を選択**、**並べ替え**、および**実行**します。

次の使用例は、 [Outlook のサービス クライアントを取得](#GetClient)するメソッドを呼び出します。

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Contacts" -->

```cs
var outlookClient = await CreateOutlookClientAsync("Contacts");
var contactFolders = await outlookClient.Me.ContactFolders
  .Take(10)
  .ExecuteAsync();

foreach(var contactFolder in contactFolders.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Contact folder '{0}'.", contactFolder.Id);
}

```
```javascript-i
outlookClient.me.contactFolders.getContactFolders().orderBy('DisplayName asc').fetch().then(
function (result) {
    result.currentPage.forEach(function (folder) {
        console.log('Folder "' + folder.displayName + '"');
    });
}, function(error) {
    console.log(error);
}
);
```

<!-- ENDSECTION -->

<!--Write not supported for GA
<a name="CreateContactFolders"> </a>
## Create contact folders

Create a contact folder in the default Contacts folder.

This example assumes you already [got the Outlook Services client](#GetClient).


```cs
ContactFolder newContactFolder = new ContactFolder
{
    DisplayName = "Company"
};
await client.Me.ContactFolders.AddContactFolderAsync(newContactFolder);

// Get the ID of the contact folder.
string contactFolderId = newContactFolder.Id;
```



<a name="UpdateContactFolders"> </a>
## Update contact folders

Change a contact folder's display name.

This example assumes you already [got the Outlook Services client](#GetClient) and [got the folder ID](#GetContactFolders).



```cs
IContactFolder contactFolder = await client.Me.ContactFolders[contactFolderId].ExecuteAsync();
contactFolder.DisplayName = "Business";
await contactFolder.UpdateAsync();

// Get the updated property.
string newContactFolderName = contactFolder.DisplayName;
```



You can define multiple updates client-side and send the requests all at once (batch them) by using the following pattern:
1. Call `UpdateAsync(true)` for each entity you want to update. Specifying `true` registers the updates locally on the client but doesn't post them to the server.
2. Call `client.Context.SaveChangesAsync()` to post all updates that are registered locally.



<a name="DeleteContactFolders"> </a>
## Delete contact folders

Delete a contact folder.
This example assumes you already [got the Outlook Services client](#GetClient) and [got the folder ID](#GetContactFolders).



```cs
IContactFolder contactFolder = await client.Me.ContactFolders[contactFolderId].ExecuteAsync();
await contactFolder.DeleteAsync();
```

-->



****

<a name="GetContactPhotoandMetadata"></a>
##<a name="a-nameget-contact-photo-and-metadataa"></a><a name="get-contact-photo-and-metadata"></a>連絡先の写真とメタデータを取得します。

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

[Abrufen von 連絡先の写真を](#GetContactPhoto) | [連絡先の写真のメタデータを取得します。 ](#GetContactPhotoMetadata)

<a name="GetContactPhoto"></a>

###<a name="a-nameget-contact-photo-resta-"></a><a name="get-contact-photo-rest"></a>を取得します。 連絡先の写真 (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

指定したサインインしているユーザーの連絡先の写真を取得します。 


```no-highlight
GET https://outlook.office.com/api/beta/me/contacts('{contact_id}')/photo/$value
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|サインインしているユーザーの特定の連絡先を指定する-ID です。|

**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/contacts('AAMkAGE1M2IyNGNm===')/photo/$value
Content-Type: image/jpg
```

**応答データ**

要求された写真のバイナリ データが含まれています。 HTTP-応答コードは、200 です。

操作は、連絡先にまだない連絡先の写真は、Exchange Online の場合に、HTTP 404 を返します。

****

<a name="GetphotoMetadata"></a>

###<a name="a-nameget-contact-photo-metadata-resta-"></a><a name="get-contact-photo-metadata-rest"></a>を取得します。 連絡先の写真のメタデータ (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

コンテンツの種類、幅および高さをピクセル単位で含まれていますが、連絡先の写真のメタデータを取得します。 


```no-highlight
GET https://outlook.office.com/api/beta/me/contacts('{contact_id}')/photo
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|サインインしているユーザーの特定の連絡先を指定する ID です。|

**要求のサンプル**

```
GET https://outlook.office.com/api/beta/me/contacts('AAMkAGE1M2IyNGNm')/photo
```

**応答データのサンプル**

200 要求が成功するには、HTTP が返されます。

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Contacts('AAMkAGE1M2IyNGNm')/photo/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-b826-40d7-b48b-57002df800e5@1717622f-49d1-4d0c-9d74-709fad664b77')/contacts('AAMkAGE1M2IyNGNm')/photo",
    "@odata.readLink": "https://outlook.office.com/api/beta/Users('ddfcd489-b826-40d7-b48b-57002df800e5@1717622f-49d1-4d0c-9d74-709fad664b77')/contacts('AAMkAGE1M2IyNGNm')/photo",
    "@odata.mediaContentType": "image/jpeg",
    "Id": "103X77",
    "Width": 103,
    "Height": 77
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

[Abrufen von 連絡先の写真を](#GetContactPhoto) | [連絡先の写真のメタデータを取得します。 ](#GetContactPhotoMetadata)

<a name="GetContactPhoto"></a>

###<a name="a-nameget-contact-photo-resta-"></a><a name="get-contact-photo-rest"></a>を取得します。 連絡先の写真 (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

指定したサインインしているユーザーの連絡先の写真を取得します。 


```no-highlight
GET https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/photo/$value
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|サインインしているユーザーの特定の連絡先を指定する ID です。|

**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/contacts('AAMkAGE1M2IyNGNm===')/photo/$value
Content-Type: image/jpg
```

**応答データ**

要求された写真のバイナリ データが含まれています。 HTTP-応答コードは、200 です。

操作は、連絡先にまだない連絡先の写真は、Exchange Online の場合に、HTTP 404 を返します。

****

<a name="GetContactPhotoMetadata"></a>

###<a name="a-nameget-contact-photo-metadata-resta-"></a><a name="get-contact-photo-metadata-rest"></a>を取得します。 連絡先の写真のメタデータ (残りの部分)

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.Read_
- _WL.Basic_

コンテンツの種類、幅および高さをピクセル単位で含まれていますが、連絡先の写真のメタデータを取得します。 


```no-highlight
GET https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/photo
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|サインインしているユーザーの特定の連絡先を指定する-ID です。|

**要求のサンプル**

```
GET https://outlook.office.com/api/v2.0/me/contacts('AAMkAGE1M2IyNGNm')/photo
```

**応答データのサンプル**

200 要求が成功するには、HTTP が返されます。

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Contacts('AAMkAGE1M2IyNGNm')/photo/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-b826-40d7-b48b-57002df800e5@1717622f-49d1-4d0c-9d74-709fad664b77')/contacts('AAMkAGE1M2IyNGNm')/photo",
    "@odata.readLink": "https://outlook.office.com/api/v2.0/Users('ddfcd489-b826-40d7-b48b-57002df800e5@1717622f-49d1-4d0c-9d74-709fad664b77')/contacts('AAMkAGE1M2IyNGNm')/photo",
    "@odata.mediaContentType": "image/jpeg",
    "Id": "103X77",
    "Width": 103,
    "Height": 77
}
```



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

この機能は、バージョン 2.0 とベータ版で利用可能です。 詳細については、記事の右上隅のコントロールを使用し、これらのバージョンのいずれかを選択します。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

****


<a name="SetContactPhoto"></a>

##<a name="a-nameset-contact-photoa"></a><a name="set-contact-photo"></a>連絡先の写真のセット



<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

指定したサインインしているユーザーの連絡先に写真を割り当てます。 写真は、バイナリ形式でなければなりません。 そのため、既存の写真が置き換えられます  
お問い合わせください。 

使用は、ベータ版では、この操作にのみ配置します。


```no-highlight
PUT https://outlook.office.com/api/beta/me/contacts('{contact_id}')/photo/$value
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|サインインしているユーザーの特定の連絡先を指定する-ID です。|


**要求のサンプル**

```
PUT https://outlook.office.com/api/beta/me/contacts('AAMkAGE1M2IyNGNm===')/photo/$value
Content-Type: image/jpeg
```

要求の本文に写真のバイナリ データが含まれます。
 

**応答データ**

200 要求が成功するには、HTTP が返されます。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**必要な範囲の最小値**: 次のいずれか。_
- _https://Outlook.Office.com/Contacts.ReadWrite_
- _WL.contacts_create_

指定したサインインしているユーザーの連絡先に写真を割り当てます。 写真は、バイナリ形式でなければなりません。 そのため、既存の写真が置き換えられます  
お問い合わせください。 

修正プログラムを使用することができますバージョン 2.0 ではこの操作をしたりします。


```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/photo/$value

PUT https://outlook.office.com/api/v2.0/me/contacts('{contact_id}')/photo/$value
```

|**必要なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL-パラメーター_|
|contact_id|string|サインインしているユーザーの特定の連絡先を指定する-ID です。|


**要求のサンプル**

```
PUT https://outlook.office.com/api/v2.0/me/contacts('AAMkAGE1M2IyNGNm===')/photo/$value
Content-Type: image/jpeg
```

要求の本文に写真のバイナリ データが含まれます。
 

**応答データ**

200 要求が成功するには、HTTP が返されます。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

この機能は、バージョン 2.0 とベータ版で利用可能です。 詳細については、記事の右上隅のコントロールを使用し、これらのバージョンのいずれかを選択します。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

****

<a name="NextSteps"> </a>
## <a name="a-namenext-stepsa"></a><a name="next-steps"></a>次のステップ

アプリケーションの構築を開始、あるいは詳細については、準備が整ったら、かどうかお任せします。


- [メール、カレンダー、および連絡先の他の Api を使用](http://dev.outlook.com/RestGettingStarted)します。

- 対話型の[API のサンド ボックス](http://apisandbox.msdn.microsoft.com/)を使用して Office 365 の Api について説明します。

- サンプルをしますか。 [きました](..\howto\starter-projects-and-code-samples.md)。


または、Office 365 のプラットフォームを使用する方法の詳細について説明します。

- [REST-API を Outlook で Outlook のデベロッパー センター](http://dev.outlook.com/RestGettingStarted/Overview)

- [Office 365 のプラットフォーム上での開発の概要](..\howto\platform-development-overview.md)

- [Office 365 アプリケーションの認証およびリソースの承認](..\howto\common-app-authentication-tasks.md)

- [Azure AD で Office 365 の Api にアクセスできるように、アプリケーションを手動で登録します。](..\howto\add-common-consent-manually.md)

- [メール API リファレンス](..\api\mail-rest-operations.md)

- [カレンダー API リファレンス](..\api\calendar-rest-operations.md)

- [タスクの残りの部分の-API (プレビュー)](..\api\task-rest-operations.md)

- [OneDrive-API](https://dev.onedrive.com/)

- [探索サービスの REST-API の操作を参照します。](..\api\discovery-service-rest-operations.md)

- [メール、予定表、連絡先、およびタスクの残りの部分の Api のリソースの参照](..\api\complex-types-for-mail-contacts-calendar.md)   

[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]






