MS-です。 TocTitle: Outlook ユーザーの写真の残りの部分の API リファレンス タイトル: Outlook ユーザーの写真の残りの部分の API リファレンスの説明: Office 365 のユーザーの写真の REST API を使用して、組織内のユーザーの写真を取得し、サイズとタイプを含む画像のメタデータを取得する方法を参照します。  
MS-です。 ContentId: 1bc24940-25ef-43fa-8602-be6df30439f7 <<<<<<< ヘッド ms.topic: ms.date 参照 (API): 2016 年 6 月 21 日

=======
MS.Date: 2016 年 7 月 12 日

---

>>>>>>> ステージング[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="a-nameoutlook-user-photo-rest-api-referenceaoutlook-api-"></a><a name="outlook-user-photo-rest-api-reference"></a>Outlook ユーザーの写真の残りの部分の API リファレンス  


[!INCLUDE [Add the Outlook REST API filters--v2 default v1 disabled](../includes/controls/addOutlookversion_v2default_v1disabled.html)]


 _**に適用されます:**オンライン交換 | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->


[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<p class="previewnote">このドキュメントでは、ベータ版のプレビューでは、ユーザー写真 API について説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 可能な場合、バージョン 2.0 は現在推奨されるバージョンです。</p>

ユーザーの写真の API では、ダウンロードするか、またはこれらのドメインのいずれかの Microsoft アカウントに、Office 365 では、Azure Active Directory でメールボックスを持つがセキュリティで保護されたユーザーの写真を設定できます。 : Hotmail.com、Live.com である MSN.com、Outlook.com、および Passport.com。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。

**API のベータ版では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

ユーザーの写真の API では、ダウンロードするか、またはこれらのドメインのいずれかの Microsoft アカウントに、Office 365 では、Azure Active Directory でメールボックスを持つがセキュリティで保護されたユーザーの写真を設定できます。 : Hotmail.com、Live.com である MSN.com、Outlook.com、および Passport.com。

**メモ**参照のわかりやすくするため、この資料の残りの部分は、**これらの Microsoft アカウントのドメインを含めるには、「Outlook.com」**を使用します。


**API のバージョン 2.0 では関係ないですか?** 右上隅にコントロールを使用し、バージョンを選択します。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


## <a name="a-nameusing-the-user-photo-rest-apia-rest-api-"></a><a name="using-the-user-photo-rest-api"></a>ユーザーの写真の REST-API を使用します。

### <a name="a-nameauthenticationa"></a><a name="authentication"></a>認証

他の[REST-API の Outlook](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)、Outlook ユーザーのフォト API へのすべての要求のように、有効なアクセス トークンを含める必要があります。 アクセス トークンを取得するには、登録されていると、アプリケーションを識別し、適切な承認を取得する必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。 ユーザーの写真の API では、特定の操作を続行するには、この点に留意してください。

###<a name="a-nameversion-of-apiaapi-"></a><a name="version-of-api"></a>API のバージョン

この API は、一般的な可用性 (GA) の状態に、プレビューから昇格されています。 Outlook の REST-API 2.0 のバージョン とベータ版のバージョンでサポートされています。 

###<a name="a-nametarget-usera-"></a><a name="target-user"></a>ターゲット ユーザー

サインインしているユーザー、またはユーザー ID で指定されたユーザーを対象ユーザーとして使用することができます。 

REST-API のサブセットのすべてに共通の情報を使用して、 [Outlook の REST-API-の使用](..\api\use-outlook-rest-api.md)を参照してください。 詳細についてはこの API、および Outlook の 

****

<a name="UserPhotoOperations"> </a>

## <a name="a-nameuser-photo-operationsa"></a><a name="user-photo-operations"></a>ユーザーの写真の操作

ユーザーの写真の操作を使用すると、ユーザーの写真のメタデータとフォト ストリームをバイナリ形式で取得し、ユーザーの写真を設定します。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

だけでなく、**写真**のエンティティは、ユーザーのフォト API は、プレビューおよびベータ版でのみ使用可能である**写真**のコレクションを提供します。 **写真**のコレクションを使用して、興味のあるユーザーの写真の特定のサイズを指定できます。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<a name="GetPhotoMetadataOperations"> </a>
###写真のメタデータを取得します。

コンテンツ タイプ、eTag を幅と高さ (ピクセル単位) が含まれていますが、要求されたユーザーの写真に関する情報を取得します。

**スコープが必要**サインイン中のユーザーになることを指定したユーザーの写真のメタデータを取得するのにには、範囲は、次のいずれかを使用します。
- _User.readbasic.All_
- _User.Read.All_
- _User.ReadWrite.All_

具体的には、サインイン中のユーザーの写真のメタデータを取得するのに次のスコープを使用することもできます。 
- _User.Read_ 

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


**最大の使用可能な写真のメタデータを取得します。**

```no-highlight
GET https://outlook.office.com/api/beta/me/photo
GET https://outlook.office.com/api/beta/Users('{user_id}')/photo
```

**すべての使用可能な写真のサイズのメタデータを取得します。**
```no-highlight
GET https://outlook.office.com/api/beta/me/photos
GET https://outlook.office.com/api/beta/Users('{user_id}')/photos
```

**メタデータを特定の写真のサイズを取得します。**
```no-highlight
GET https://outlook.office.com/api/beta/me/photos('{size}')
GET https://outlook.office.com/api/beta/Users('{user_id}')/photos('{size}')
```

|**省略可能なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL パラメーター_|
|USER_ID|string|ユーザーの電子メール アドレスです。|
|size|string| 写真のサイズです。 ' 1 対 1" の値は、メールボックスと Active Directory 内の場合は写真を自動的に生成されていません。 <br/> 写真が、メールボックスに格納されているかどうか、定義済みのサイズ: ' 48 x 48 "、" 64 x 64"、 '96 X 96 '、' X 120 120' 、'240 x 240", "360 360 x '、 ' 432 x 432' 、'504 504 X '、および' x 648 648' です。 ユーザーは、十分な大きさの写真をアップロードしない、する場合、事前定義された小さいサイズで表すことができるサイズだけを利用できます。 などの場合は、ユーザーが写真をアップロードする 504 x 504 ピクセルは、すべてが 648 648 x サイズの写真がダウンロードできます。 <br/> 写真は、Active Verzeichnis に格納されている場合、任意の次元でできます。  

**要求のサンプル**この要求は、サインイン中のユーザーに対する 240 x 240 ピクセルのイメージのメタデータを取得します。

```
GET https://outlook.office.com/api/beta/me/photos('240x240')
```

**応答データのサンプル**

次の応答データは、写真のメタデータを示します。 HTTP-応答コードは、200 です。
```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/photo/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/jpeg",
    "@odata.mediaEtag": "\"BA09D118\"",
    "Id": "240X240",
    "Width": 240,
    "Height": 240
}
```
次の応答データは、写真は、ユーザーに既にアップロードされていない場合、応答の内容を示しています。 HTTP-応答コードは、200 です。
```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/photo/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/gif",
    "@odata.mediaEtag": "",
    "Id": "1X1",
    "Width": 1,
    "Height": 1
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


**最大の使用可能な写真のメタデータを取得します。**

```no-highlight
GET https://outlook.office.com/api/v2.0/me/photo
GET https://outlook.office.com/api/v2.0/Users('{user_id}')/photo
```


|**省略可能なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL パラメーター_|
|USER_ID|string|ユーザーの電子メール アドレスです。|
 

**要求のサンプル**この要求では、サインイン中のユーザーのユーザーの写真のメタデータを取得します。

```
GET https://outlook.office.com/api/v2.0/me/photo
```

**応答データのサンプル**

次の応答データは、写真のメタデータを示します。 HTTP-応答コードは、200 です。
```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/photo/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/jpeg",
    "@odata.mediaEtag": "\"BA09D118\"",
    "Id": "240X240",
    "Width": 240,
    "Height": 240
}
```
次の応答データは、写真は、ユーザーに既にアップロードされていない場合、応答の内容を示しています。 HTTP-応答コードは、200 です。
```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/photo/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/gif",
    "@odata.mediaEtag": "",
    "Id": "1X1",
    "Width": 1,
    "Height": 1
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




****

<a name="GetPhotoOperations"> </a>
### <a name="a-nameget-photoa"></a><a name="get-photo"></a>写真を取得します。

指定したユーザーのユーザーの写真を取得します。

この操作では、テナントのすべてのユーザーのユーザーの写真を取得するアプリケーションをできるようにするには、テナント管理者が実行できます。

**スコープが必要**サインイン中のユーザーになることを指定したユーザーの写真を取得するのにには、範囲は、次のいずれかを使用します。
- _User.readbasic.All_
- _User.Read.All_
- _User.ReadWrite.All_

具体的には、サインイン中のユーザーの写真を取得するのには次のスコープを使用することもできます。 
- _User.Read_ 
- _User.ReadWrite_



<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


**使用可能な最大サイズを取得します。**

```no-highlight
GET https://outlook.office.com/api/beta/me/photo/$value
GET https://outlook.office.com/api/beta/Users('{user_id}')/photo/$value
```

**特定のサイズの写真を取得します。**
```no-highlight
GET https://outlook.office.com/api/beta/me/photos('{size}')/$value
GET https://outlook.office.com/api/beta/Users('{user_id}')/photos('{size}')/$value
```

|**省略可能なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL パラメーター_|
|USER_ID|string|ユーザーの電子メール アドレスです。|
|size|string| 写真のサイズです。 ' 1 対 1" の値は、メールボックスと Active Directory 内の場合は写真を自動的に生成されていません。 <br/> 写真が、メールボックスに格納されているかどうか、定義済みのサイズ: ' 48 x 48 "、 ' 64 x 64" 、 '96 X 96 '、' X 120 120' 、'240 x 240', ' 360 360 x '、 ' 432 x 432' 、'504 504 X '、および' x 648 648' です。 ユーザーは、十分な大きさの写真をアップロードしない、する場合、事前定義された小さいサイズで表すことができるサイズだけを利用できます。 などの場合は、ユーザーが写真をアップロードする 504 x 504 ピクセルは、すべてが 648 648 x サイズの写真がダウンロードできます。 <br/> 写真は、Active Verzeichnis に格納されている場合、任意の次元でできます。  


**要求のサンプル**

この要求では、サインイン中のユーザーの写真を取得します。

```
GET https://outlook.office.com/api/beta/me/photo/$value
Content-Type: image/jpg
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


**使用可能な最大サイズを取得します。**

```no-highlight
GET https://outlook.office.com/api/v2.0/me/photo/$value
GET https://outlook.office.com/api/v2.0/Users('{user_id}')/photo/$value
```


|**省略可能なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL パラメーター_|
|USER_ID|string|ユーザーの電子メール アドレスです。|


**要求のサンプル**

この要求では、サインイン中のユーザーの写真を取得します。

```
GET https://outlook.office.com/api/v2.0/me/photo/$value
Content-Type: image/jpg
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



**応答データ**

要求された写真のバイナリ データが含まれています。 HTTP-応答コードは、200 です。

****


###<a name="a-nameset-user-photoa"></a><a name="set-user-photo"></a>セットのユーザーの写真

<a name="a-name-heada-"></a><a name="-head"></a><<<<<<< ヘッド
=======

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

写真を指定したユーザーに割り当てます。 写真は、バイナリ形式でなければなりません。 そのユーザーの既存の写真が置き換えられます。

この操作では、テナントのすべてのユーザーのユーザーの写真を設定するアプリケーションをできるようにするには、テナント管理者が実行できます。 使用は、ベータ版では、この操作にのみ配置します。


**必要なスコープ** 
>>>>>>> ステージング

テナント内のユーザーまたはログインしているユーザーになることを指定したユーザーの写真を設定するのには次のスコープを使用します。
- _User.ReadWrite.All_ 


<<<<<<< ヘッドでは、サインイン中のユーザーに写真を割り当てます。 写真は、バイナリ形式でなければなりません。 そのユーザーの既存の写真が置き換えられます。

<!--
Assign a photo to the specified user. The photo should be in binary. It replaces any existing photo for that user.

This operation allows a tenant administrator to let an app set the user photo of any user in the tenant.
--> 

使用は、ベータ版では、この操作にのみ配置します。



**必要なスコープ** 

<!-- 
Use the following scope to set the photo of the specified user, who can be any user in the tenant or the signed-in user:
- _user.readwrite.all_ 
-->

<a name="use-the-following-scope-to-set-the-photo-of-specifically-the-signed-in-user"></a>具体的には、サインイン中のユーザーの写真を設定するのにには、次のスコープを使用します。 === 具体的には、サインイン中のユーザーの写真を設定するのには次のスコープを使用することもできます。 >>>>>>> ステージング- _user.readwrite_

```no-highlight
PUT https://outlook.office.com/api/beta/me/photo/$value
PUT https://outlook.office.com/api/beta/users('{user_id}')/photo/$value
```

|**省略可能なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL パラメーター_|
|USER_ID|string|ユーザーの電子メール アドレスです。|


**要求のサンプル**

```
PUT https://outlook.office.com/api/beta/me/photo/$value
Content-Type: image/jpeg
```

要求の本文に写真のバイナリ データが含まれます。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

写真をサインイン中のユーザーに割り当てます。 写真は、バイナリ形式でなければなりません。 そのユーザーの既存の写真が置き換えられます。 

どちらかのパッチを使用することができますバージョン 2.0 ではこの操作をしたりします。


**スコープが必要**次のスコープを使用すると、サインイン中のユーザーの写真を設定します。
- _User.ReadWrite_ 

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/photo/$value
PATCH https://outlook.office.com/api/v2.0/users('{user_id}')/photo/$value

PUT https://outlook.office.com/api/v2.0/me/photo/$value
PUT https://outlook.office.com/api/v2.0/users('{user_id}')/photo/$value
```

|**省略可能なパラメーター**|**タイプ**|**説明**|
|:-----|:-----|:-----|
|_URL パラメーター_|
|USER_ID|string|ユーザーの電子メール アドレスです。|


**要求のサンプル**

```
PATCH https://outlook.office.com/api/v2.0/me/photo/$value
Content-Type: image/jpeg
```

要求の本文に写真のバイナリ データが含まれます。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


**応答データ**

200 要求が成功するには、HTTP が返されます。

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





[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]



<<<<<<< ヘッド
                        
=======
        
      
>>>>>>> ステージング
