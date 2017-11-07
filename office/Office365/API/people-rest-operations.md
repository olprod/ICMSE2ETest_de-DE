MS-です。 TocTitle: Outlook ユーザー REST-API-を参照 (プレビュー) タイトル: Outlook ユーザーの残りの部分の API リファレンスの説明: サービス経由で他のユーザーに関する情報へのアクセスを提供する人の他の Api と対話する方法を参照します。 MS-です。 ContentId: 99aec234-31a1-46bd-8a01-3f0d2fea22f8 ms.topic: ms.date を参照 (API): 2016 5 月 16 日

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="a-nameoutlook-people-rest-api-reference-previewaoutlook-rest-api-"></a><a name="outlook-people-rest-api-reference-preview"></a>Outlook ユーザーの REST-API-リファレンス (プレビュー)

[!INCLUDE [Add the Outlook REST API filters--beta default v1 v2 disabled](../includes/controls/addOutlookversion_betadefault_v1v2disabled.html)]    

<p class="previewnote">このドキュメントでは、プレビューではユーザーの API について説明します。 プレビュー機能では、ファイナライズする前に変更されることし、それらを使用するコードを中断することがあります。 このため、一般的にする必要がありますを使用する API の生産バージョンのみ、実稼働コードで。 は現在推奨されるバージョンに 可能な場合、バージョン 2.0.</p>


Outlook ユーザーの API では、メール、連絡先、およびソーシャル ネットワークの間でするのに重要な他のユーザーに関する情報を取得することができます。 単一のエンドポイントを 1 つの要求の多くのソースからユーザーに関する情報を組み合わせることができます。 Office 365 で、Azure Active Directory によってセキュリティで保護された情報にアクセスする API を使用することができます。 これらのドメイン内の Microsoft アカウントへのアクセスも用意されています: office.com、hotmail.com、live.com と office365.com。

**メモ**この資料と同じ方法では、サポートされているすべてのドメインに適用されます。 簡略化のため、この資料の残りの部分を使用して**内のすべてのドメインのアカウントを参照するには、"outlook.office.com"です**。

## <a name="a-nameall-people-api-operationsa-api-"></a><a name="all-people-api-operations"></a>ユーザー API のすべての操作

人 API には、関連要求のたびに、_ユーザー_エンティティが返されます。 _人_は、メール、連絡先、ソーシャル ネットワークの間での情報を集約します。 結果は、_関連性の高い_順に並べ替えられます。 複数のコミュニケーション、コラボレーション、およびビジネスの関係に基づく要求で指定し、ランク付けの条件によって決定されます。

[ユーザーの一覧を参照する](#BrowsePeople) | [検索を使用するユーザーの一覧を取得](#SearchPeople)

##<a name="a-nameuse-the-people-rest-apia-rest-api-"></a><a name="use-the-people-rest-api"></a>人の REST-API を使用します。

###<a name="a-nameauthenticationa"></a><a name="authentication"></a>認証

他の[Outlook の他の API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)、ユーザー api では、すべての要求のように、有効なアクセス トークンが含まれます。 登録しアプリを識別し、アクセス トークンを取得するのには適切な承認を得る必要があります。 一部簡素化された登録および承認オプションについての[詳細を確認](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)できます。

###<a name="a-namesupported-rest-actions-and-endpointsa"></a><a name="supported-rest-actions-and-endpoints"></a>サポートされている残りの部分の動作とエンドポイント

人の REST-API と対話すると、サポートされているエンドポイントの HTTP GET 要求を送信します。 

URL リソースのパス名とクエリ パラメーターは、大文字小文字を区別します。 ただし、値を割り当てる、エンティティの Id、および base64 でエンコードされた値は、大文字と小文字が区別されます。

REST-API のユーザーのすべての要求は、次のルートの URL の形式を使用します。

`https://outlook.office.com/api/{version}/{user context}`

###<a name="a-nameversion-of-the-apiaapi-"></a><a name="version-of-the-api"></a>API のバージョン

`{version}`ルートの指定した URL で REST-API のバージョンを表します。 指定できる唯一のバージョンは、 `beta`。

* `beta`: このバージョンでは、プレビューでは、実稼働コードでは使用しない必要があります。 URL-の例で、 `https://outlook.office.com/api/beta/me/people`。 このバージョンには、追加の API のセットをプレビューでは、ファイナライズする前に変更することがあり、同様に、ga の時点での最新の Api が含まれています。
  
###<a name="a-nametarget-usera-"></a><a name="target-user"></a>ターゲット ユーザー

`{user_context}`現在サインイン中のユーザーは、します。 ユーザーの API では、現在のユーザーのためのすべての要求を実行します。 _要求_の残りの部分でユーザー コンテキストを指定するには次のようにします。

- `me`のショートカット: `/api/{version}/me`。 Die URL になります ルートの`https://outlook.office.com/api/{version}/me`。

この形式で識別されるユーザー コンテキストでサーバーの_応答_: `users/{AAD_userId@AAD_tenantId}`。

<a name="BrowsePeople"> </a>
###<a name="a-namebrowse-peoplea"></a><a name="browse-people"></a>ユーザーを参照します。

[ページングの応答](#BrowsePaging) | 
[応答の並べ替え](#BrowseSort) | 
[応答内のユーザーの数を設定する](#BrowsePageSize) | 
[フィールドが返される選択](#BrowseSelecting) |
[応答をフィルタ リング](#BrowseFiltering) |
[フィルタ リングされ返されるフィールドを選択します。 ](#BrowseSelectingAndFiltering)

_**スコープが必要です**: https://outlook.office.com/people.read_

<a name="DefaultBrowse"></a>次のような要求が通信、コラボレーション、およびビジネスの関係に基づいて、ユーザーに最も関連するユーザーを取得します。 既定では、各応答に 10 個のレコードが返されますが、[変更](#BrowsePageSize) _$top_パラメーターを使用することができます。

```no-highlight
https://outlook.office.com/api/beta/me/people/
```
要求への応答は、以下のようです。

```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMPSuxK9KrREk1tt36xsca8=')",
          "Id": "AAUQAMPSuxK9KrREk1tt36xsca8=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Stuart Bui",
          "GivenName": "Stuart",
          "Surname": "Bui",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "sbui@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMLasTGasi1NmGqss0adMLI=')",
          "Id": "AAUQAMLasTGasi1NmGqss0adMLI=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Phillip Wooley",
          "GivenName": "Phillip",
          "Surname": "Wooley",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "phillipw@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACfUjORcHM1Juw-lAPzHFIk=')",
          "Id": "AAUQACfUjORcHM1Juw-lAPzHFIk=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Nestor Kellum",
          "GivenName": "Nestor",
          "Surname": "Kellum",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "nestork@contoso.com"
            },
             {
              "Address": "nestork@hotmail.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQADSJ952xczZGkD0tsvxPomg=')",
          "Id": "AAUQADSJ952xczZGkD0tsvxPomg=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Lacey Burns",
          "GivenName": "Lacey",
          "Surname": "Burns",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "laceyb@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMJuQ5gE3IdFl1lpkykoJeY=')",
          "Id": "AAUQAMJuQ5gE3IdFl1lpkykoJeY=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Ralph Foret",
          "GivenName": "Ralph",
          "Surname": "Foret",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "ralphf@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMrt5YwDXhJIlWoRZX9ebnw=')",
          "Id": "AAUQAMrt5YwDXhJIlWoRZX9ebnw=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Emery Hixson",
          "GivenName": "Emery",
          "Surname": "Hixson",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "emeryh@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAOFizzhIt3ZCh4pW33s_iOQ=')",
          "Id": "AAUQAOFizzhIt3ZCh4pW33s_iOQ=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Stephanie Ray",
          "GivenName": "Stephanie",
          "Surname": "Ray",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "stephanier@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 12"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKirlq5lgdFHuhZ8O9FI8XA=')",
          "Id": "AAUQAKirlq5lgdFHuhZ8O9FI8XA=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Natalie Roach",
          "GivenName": "Natalie",
          "Surname": "Roach",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "natalier@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKAXFd--O4lGr6RNJzbBXwE=')",
          "Id": "AAUQAKAXFd--O4lGr6RNJzbBXwE=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Ignacio Slayton",
          "GivenName": "Ignacio",
          "Surname": "Slayton",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "ignacios@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 3"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAAxHEg0Rus9CmXr0FE4muco=')",
          "Id": "AAUQAAxHEg0Rus9CmXr0FE4muco=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Clayton Flanigan",
          "GivenName": "Clayton",
          "Surname": "Flanigan",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "claytonf@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        }
      ],
      "@odata.nextLink": "https://outlook.office.com/api/beta/me/people/?%24top=10&%24skip=10"
    }

```

****

<a name="BrowsePaging"></a> 
**人の後続のページを要求します。**

最初の応答に関連する人の完全な一覧が含まれていない場合は、 _$top_と_$skip_を使用して他のページの情報を要求する 2 番目の要求を行うことができます。 [前の要求](#DefaultBrowse)に追加情報がある場合は、次のような要求は、サーバーからユーザーの次のページを取得します。

```no-highlight
https://outlook.office.com/api/beta/me/people/?$top=10&$skip=10
```

サーバーからの応答を次に示します。

```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQADrqbKGdhxdNkjXAVQHEvMQ=')",
          "Id": "AAUQADrqbKGdhxdNkjXAVQHEvMQ=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Monte Lafferty",
          "GivenName": "Monte",
          "Surname": "Lafferty",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "montel@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAHiSySeJLAtAo6t0FuPmns0=')",
          "Id": "AAUQAHiSySeJLAtAo6t0FuPmns0=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Madelyn Cooley",
          "GivenName": "Madelyn",
          "Surname": "Cooley",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "madelync@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 11"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACQ-gdlH_4hPvR5o7cUkm7A=')",
          "Id": "AAUQACQ-gdlH_4hPvR5o7cUkm7A=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Leo Scholl",
          "GivenName": "Leo",
          "Surname": "Scholl",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "leos@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAHc2322QSPBJtxkeVUcXPGs=')",
          "Id": "AAUQAHc2322QSPBJtxkeVUcXPGs=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Lucinda Burke",
          "GivenName": "Lucinda",
          "Surname": "Burke",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "shoebm@exchange.contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAEld1zm_6W9Covp5NAGvszw=')",
          "Id": "AAUQAEld1zm_6W9Covp5NAGvszw=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Ernesto Fellows",
          "GivenName": "Ernesto",
          "Surname": "Fellows",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "ernestof@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACgDLi02r8RDmtK-40rUPXE=')",
          "Id": "AAUQACgDLi02r8RDmtK-40rUPXE=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Margret Nash",
          "GivenName": "Margret",
          "Surname": "Nash",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "margretn@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKXZsceAVjRDiUASCswoQxY=')",
          "Id": "AAUQAKXZsceAVjRDiUASCswoQxY=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Wendy Monroe",
          "GivenName": "Wendy",
          "Surname": "Monroe",
          "Title": "ARCHITECT",
          "EmailAddresses": [
            {
              "Address": "wendym@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAO-ckLra2wFBjbgc1-F5yyQ=')",
          "Id": "AAUQAO-ckLra2wFBjbgc1-F5yyQ=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Alberta Johns",
          "GivenName": "Alberta",
          "Surname": "Johns",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "albertaj@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAO-Giffc5HxMibij3YNPuvU=')",
          "Id": "AAUQAO-Giffc5HxMibij3YNPuvU=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Leticia Bullock",
          "GivenName": "Leticia",
          "Surname": "Bullock",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "leticiab@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAE6BF792ae9KoMQeDZbxDK0=')",
          "Id": "AAUQAE6BF792ae9KoMQeDZbxDK0=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Angelita Dillard",
          "GivenName": "Angelita",
          "Surname": "Dillard",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "angelitad@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 3"
        }
      ],
      "@odata.nextLink": "https://outlook.office.com/api/beta/me/people/?%24skip=20&%24top=10"
    }
```

****

<a name="BrowseSort"></a> 
**応答の並べ替え**

既定では、応答内のユーザーは、クエリに関連性で並べ替えられます。 _$Orderby_パラメーターを使用して応答内のユーザーの順序を変更することができます。 このクエリは最も関連するユーザーを選択、表示名の順に並べ替えられて、および並べ替えられたリストの最初の 10 人を返します。

```no-highlight
https://outlook.office.com/api/beta/me/people/?$orderby=DisplayName 
```
サーバーからの応答を次に示します。

```no-highlight
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People",
      "value": [
        {
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAO46ZoZRt65Ajfvu2d8atiw=')",
          "Id": "AAUQAO46ZoZRt65Ajfvu2d8atiw=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Angelina Blackwell",
          "GivenName": "Angelina",
          "Surname": "Blackwell",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "angelinab@exchange.contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 5"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAGaI4BZyQURDtuk0nNvBYGk=')",
          "Id": "AAUQAGaI4BZyQURDtuk0nNvBYGk=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Benita Wilkerson",
          "GivenName": "Benita",
          "Surname": "Wilkerson",
          "Title": "RESEARCHER",
          "EmailAddresses": [
            {
              "Address": "benitaw@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building C"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKOPqJuLWk9NtmwOx29rbew=')",
          "Id": "AAUQAKOPqJuLWk9NtmwOx29rbew=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Callie Sweet",
          "GivenName": "Callie",
          "Surname": "Sweet",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "callies@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 2"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxMjF2cmVxdWVzdC5zdXBwb3J0QG9lLjIxdmlhbmV0LmNvbQ==')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxMjF2cmVxdWVzdC5zdXBwb3J0QG9lLjIxdmlhbmV0LmNvbQ==",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "contoso.support",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "contoso.support@outlook.office.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACtCaoUN6WdNgpyCSeKSP6E=')",
          "Id": "AAUQACtCaoUN6WdNgpyCSeKSP6E=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Dianne Frederick",
          "GivenName": "Dianne",
          "Surname": "Frederick",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "diannef@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 3"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKNvearlKU1PsHmDb-xmDrQ=')",
          "Id": "AAUQAKNvearlKU1PsHmDb-xmDrQ=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Jenifer Dotson",
          "GivenName": "Jenifer",
          "Surname": "Dotson",
          "Title": "SENENGINEER",
          "EmailAddresses": [
            {
              "Address": "jeniferd@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAAVBb0xn3ctFiZreqwDwZf0=')",
          "Id": "AAUQAAVBb0xn3ctFiZreqwDwZf0=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Nancy Washington",
          "GivenName": "Nancy",
          "Surname": "Washington",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "nancyw@exchange.contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 3"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKirlq5lgdFHuhZ8O9FI8XA=')",
          "Id": "AAUQAKirlq5lgdFHuhZ8O9FI8XA=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Natalie Roach",
          "GivenName": "Natalie",
          "Surname": "Roach",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "natalier@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKVYmyKcnQ9Njw5bvInrWYI=')",
          "Id": "AAUQAKVYmyKcnQ9Njw5bvInrWYI=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Natalie Roach's Team",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "ntteam@contoso.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAFcMhzA6m4pBlHmc3Qa_PpA=')",
          "Id": "AAUQAFcMhzA6m4pBlHmc3Qa_PpA=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Queen Duncan",
          "GivenName": "Queen",
          "Surname": "Duncan",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "queend@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 3"
        }
      ],
      "@odata.nextLink": "https://outlook.office.com/api/beta/me/people/?%24orderby=DisplayName&%24top=10&%24skip=10"
    }
```

****

<a name="BrowsePageSize"></a> 
**が返されるユーザーと返されるフィールドの数を変更します。**

_$Top_パラメーターを設定することによって応答で返されるユーザーの数を変更することができます。 

次の例では、1 000 の最も適切な人を要求します。 要求は、ユーザーの表示名だけを要求することによって、サーバーから送信されるデータの量も制限されます。

```no-highlight
https://outlook.office.com/api/beta/me/people/?$top=1000&$Select=DisplayName
```

サーバーからの応答を次に示します。

```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People(DisplayName)",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMPSuxK9KrREk1tt36xsca8=')",
          "Id": "AAUQAMPSuxK9KrREk1tt36xsca8=",
          "DisplayName": "Brian Remick"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMLasTGasi1NmGqss0adMLI=')",
          "Id": "AAUQAMLasTGasi1NmGqss0adMLI=",
          "DisplayName": "Phillip Wooley"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACfUjORcHM1Juw-lAPzHFIk=')",
          "Id": "AAUQACfUjORcHM1Juw-lAPzHFIk=",
          "DisplayName": "Nestor Kellum"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQADSJ952xczZGkD0tsvxPomg=')",
          "Id": "AAUQADSJ952xczZGkD0tsvxPomg=",
          "DisplayName": "Lacey Burns"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMJuQ5gE3IdFl1lpkykoJeY=')",
          "Id": "AAUQAMJuQ5gE3IdFl1lpkykoJeY=",
          "DisplayName": "Ralph Foret"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMrt5YwDXhJIlWoRZX9ebnw=')",
          "Id": "AAUQAMrt5YwDXhJIlWoRZX9ebnw=",
          "DisplayName": "Emery Hixson"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAOFizzhIt3ZCh4pW33s_iOQ=')",
          "Id": "AAUQAOFizzhIt3ZCh4pW33s_iOQ=",
          "DisplayName": "Stephanie Ray"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKirlq5lgdFHuhZ8O9FI8XA=')",
          "Id": "AAUQAKirlq5lgdFHuhZ8O9FI8XA=",
          "DisplayName": "Natalie Roach"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKAXFd--O4lGr6RNJzbBXwE=')",
          "Id": "AAUQAKAXFd--O4lGr6RNJzbBXwE=",
          "DisplayName": "Ignacio Slayton"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAAxHEg0Rus9CmXr0FE4muco=')",
          "Id": "AAUQAAxHEg0Rus9CmXr0FE4muco=",
          "DisplayName": "Clayton Flanigan"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQADrqbKGdhxdNkjXAVQHEvMQ=')",
          "Id": "AAUQADrqbKGdhxdNkjXAVQHEvMQ=",
          "DisplayName": "Monte Lafferty"
        },
        ... etc
```

****

<a name="BrowseSelecting"></a> 
**取得先のフィールドを選択します。**

_$Select_パラメーターを使用して 1 つまたは複数のフィールドを選択するのには、サーバーから返されるデータの量を制限することができます。 _@Odata.id_フィールドは常に返されます。

次の例では、_表示名_およびユーザーが、最も関連性の 10 人の_EmailAddress_への応答を制限します。

```no-highlight
https://outlook.office.com/api/beta/me/people/?$select=DisplayName,EmailAddresses
```
サーバーからの応答を次に示します。

```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People(DisplayName,EmailAddresses)",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMPSuxK9KrREk1tt36xsca8=')",
          "Id": "AAUQAMPSuxK9KrREk1tt36xsca8=",
          "DisplayName": "Brian Remick",
          "EmailAddresses": [
            {
              "Address": "bremick@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMLasTGasi1NmGqss0adMLI=')",
          "Id": "AAUQAMLasTGasi1NmGqss0adMLI=",
          "DisplayName": "Phillip Wooley",
          "EmailAddresses": [
            {
              "Address": "phillipw@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACfUjORcHM1Juw-lAPzHFIk=')",
          "Id": "AAUQACfUjORcHM1Juw-lAPzHFIk=",
          "DisplayName": "Nestor Kellum",
          "EmailAddresses": [
            {
              "Address": "nestork@contoso.com"
            },
             {
              "Address": "nestork@outlook.office.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQADSJ952xczZGkD0tsvxPomg=')",
          "Id": "AAUQADSJ952xczZGkD0tsvxPomg=",
          "DisplayName": "Lacey Burns",
          "EmailAddresses": [
            {
              "Address": "laceyb@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMJuQ5gE3IdFl1lpkykoJeY=')",
          "Id": "AAUQAMJuQ5gE3IdFl1lpkykoJeY=",
          "DisplayName": "Ralph Foret",
          "EmailAddresses": [
            {
              "Address": "ralphf@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMrt5YwDXhJIlWoRZX9ebnw=')",
          "Id": "AAUQAMrt5YwDXhJIlWoRZX9ebnw=",
          "DisplayName": "Emery Hixson",
          "EmailAddresses": [
            {
              "Address": "emeryh@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAOFizzhIt3ZCh4pW33s_iOQ=')",
          "Id": "AAUQAOFizzhIt3ZCh4pW33s_iOQ=",
          "DisplayName": "Stephanie Ray",
          "EmailAddresses": [
            {
              "Address": "stephanier@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKirlq5lgdFHuhZ8O9FI8XA=')",
          "Id": "AAUQAKirlq5lgdFHuhZ8O9FI8XA=",
          "DisplayName": "Natalie Roach",
          "EmailAddresses": [
            {
              "Address": "natalier@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAKAXFd--O4lGr6RNJzbBXwE=')",
          "Id": "AAUQAKAXFd--O4lGr6RNJzbBXwE=",
          "DisplayName": "Ignacio Slayton",
          "EmailAddresses": [
            {
              "Address": "ignacios@contoso.com"
            }
          ]
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAAxHEg0Rus9CmXr0FE4muco=')",
          "Id": "AAUQAAxHEg0Rus9CmXr0FE4muco=",
          "DisplayName": "Clayton Flanigan",
          "EmailAddresses": [
            {
              "Address": "claytonf@contoso.com"
            }
          ]
        }
      ],
      "@odata.nextLink": "https://outlook.office.com/api/beta/me/people/?%24select=DisplayName%2cEmailAddresses&%24top=10&%24skip=10"
    }
```

****

<a name="BrowseFiltering"></a> 
**応答を制限するフィルターを使用します。**

_$Filter_パラメーターを使用するにはのレコードに指定された条件が含まれているユーザーのみへの応答を制限します。 

次のクエリは、「通信の履歴」のソースとユーザーへの応答を制限します。

```no-highlight
https://outlook.office.com/api/beta/me/people/?$Filter=Sources/Any (source: source/Type  eq 'Communications History') 
```

```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxcGVvcGxlcmVsZXZhbmNlQHNlcnZpY2UuZXhjaGFuZ2UubWljcm9zb2Z0LmNvbQ==')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxcGVvcGxlcmVsZXZhbmNlQHNlcnZpY2UuZXhjaGFuZ2UubWljcm9zb2Z0LmNvbQ==",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "People Relevance",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "peoplerelevance@service.exchange.contoso.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxcmNoaUByY2hpbGF3LmNvbQ==')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxcmNoaUByY2hpbGF3LmNvbQ==",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "Edna Dickson",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "ednad@outlook.office.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxMjF2cmVxdWVzdC5zdXBwb3J0QG9lLjIxdmlhbmV0LmNvbQ==')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxMjF2cmVxdWVzdC5zdXBwb3J0QG9lLjIxdmlhbmV0LmNvbQ==",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "contoso.support",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "contoso.support@contoso.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxUGVvcGxlOTExMUBzZXJ2aWNlLmV4Y2hhbmdlLm1pY3Jvc29mdC5jb20=')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxUGVvcGxlOTExMUBzZXJ2aWNlLmV4Y2hhbmdlLm1pY3Jvc29mdC5jb20=",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "gethelp@contoso.com",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "gethelp@contoso.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxc21hcnRhbGVydHNAbWljcm9zb2Z0LmNvbQ==')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxc21hcnRhbGVydHNAbWljcm9zb2Z0LmNvbQ==",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "smartalerts@contoso.com",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "smartalerts@contoso.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxam9lQG9saXZlYW5kZ29vc2UuY29t')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxam9lQG9saXZlYW5kZ29vc2UuY29t",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "Emily Burnett",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "emilyb@contoso.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxYS1jYW1hbm5AbWljcm9zb2Z0LmNvbQ==')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxYS1jYW1hbm5AbWljcm9zb2Z0LmNvbQ==",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "Bridgett Baxter",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "bridgettb@contoso.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxc3RlZmFuLmJ1cmFrQGluc2lkZXZpZXcuY29t')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxc3RlZmFuLmJ1cmFrQGluc2lkZXZpZXcuY29t",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "Charlotte Stark",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "charlottes@insideview.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxbWFyaWFuYXN0ZXBwQG91dGxvb2suY29t')",
          "Id": "MkU4MDBGNDUtMEY3OS00MzM4LTg3RUUtNENFOTFBRURCODcxbWFyaWFuYXN0ZXBwQG91dGxvb2suY29t",
          "Sources": [
            {
              "Type": "Communication History"
            }
          ],
          "DisplayName": "herminiah@outlook.office.com",
          "GivenName": null,
          "Surname": null,
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "herminiah@outlook.office.com"
            }
          ],
          "CompanyName": null,
          "OfficeLocation": null
        }
      ],
      "@odata.nextLink": "https://outlook.office.com/api/beta/me/people/?%24Filter=Sources%2fAny+(source%3a+source%2fType++eq+%27Communication+History%27)&%24top=10&%24skip=10"
    }
```

****

<a name="BrowseSelectingAndFiltering"></a> 
**のフィルター処理された応答を取得するフィールドを選択します。**

ユーザーに関連するユーザーのユーザー設定リストを作成し、アプリケーションに必要なフィールドだけを取得する_$select_および_$filter_パラメーターを組み合わせることができます。 

次の使用例は、_表示名_との表示名が指定された名前と同じ人の_EmailAddress_を取得します。 この例での表示名が "Nestor Kellum" と等しいユーザーのみが返されます。 

```no-highlight
https://outlook.office.com/api/beta/me/people/?$select=DisplayName,EmailAddresses&$Filter=DisplayName eq 'Nestor Kellum' 
```

サーバーからの応答を次に示します。

```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People(DisplayName,EmailAddresses)",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACfUjORcHM1Juw-lAPzHFIk=')",
          "Id": "AAUQACfUjORcHM1Juw-lAPzHFIk=",
          "DisplayName": "Nestor Kellum",
          "EmailAddresses": [
            {
              "Address": "nestork@contoso.com"
            },
             {
              "Address": "nestork@outlook.office.com"
            }
          ]
        }
      ]
    }
```

****

<a name="SearchPeople"> </a>
###<a name="a-namesearch-peoplea"></a><a name="search-people"></a>人を検索します。

[トピックの検索](#SearchTopic) |
<!-- [Limiting a search response by topic](#SearchFilter) | -->
[あいまい検索を実行します。](#FuzzySearch)

_**スコープが必要です**: https://outlook.office.com/people.read_

**検索を使用してユーザーを選択するには**

_$Search_パラメーターを使用すると、特定の一連の条件を満たすユーザーを選択します。 

次の検索クエリを_名_または_姓_を持つが、文字 "j" で始まる関連する人を返します。

```no-highlight
https://outlook.office.com/api/beta/me/people/?$search=j
```
サーバーからの応答を次に示します。

```no-highlight
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAC4PuXFfR6pAin18WlyOqxI=')",
          "Id": "AAUQAC4PuXFfR6pAin18WlyOqxI=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Jacquelyn Cox",
          "GivenName": "Jacquelyn",
          "Surname": "Cox",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "jacquelync@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building S"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAFE5-QvXOi1KhbNrQQaV-dk=')",
          "Id": "AAUQAFE5-QvXOi1KhbNrQQaV-dk=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Julie Yates",
          "GivenName": "Julie",
          "Surname": "Yates",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "juliey@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 2"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAChuH75CMB5NsGP0QBDcX2g=')",
          "Id": "AAUQAChuH75CMB5NsGP0QBDcX2g=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Juliette Mitchell",
          "GivenName": "Juliette",
          "Surname": "Mitchell",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "juliettem@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAMsDacKpHNpFj7ViBXFiRZI=')",
          "Id": "AAUQAMsDacKpHNpFj7ViBXFiRZI=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Katheryn Johns",
          "GivenName": "Katheryn",
          "Surname": "Johns",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "katherynj@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building T"
        }
      ],
      "@odata.nextLink": "https://outlook.office.com/api/beta/me/people/?%24search=d&%24top=10&%24skip=10"
    }
```

****

<a name="SearchTopic"></a> 
**に関連するトピックを指定を使用する検索**

次のような要求に返す関連する人の名前を持つには、 "Ma" が含まれているし、人によると、好きなもので、コメディアンで「ボランティア Ansari」です。

```no-highlight
 https://outlook.office.com/api/beta/me/people/?$search="ma topic: Aziz Ansari" 
 ```
 サーバーからの応答を次に示します。
 
 ```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQACgDLi02r8RDmtK-40rUPXE=')",
          "Id": "AAUQACgDLi02r8RDmtK-40rUPXE=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Margret Nash",
          "GivenName": "Margret",
          "Surname": "Nash",
          "Title": "ENGINEER",
          "EmailAddresses": [
            {
              "Address": "margretn@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAHiSySeJLAtAo6t0FuPmns0=')",
          "Id": "AAUQAHiSySeJLAtAo6t0FuPmns0=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Madelyn Cooley",
          "GivenName": "Madelyn",
          "Surname": "Cooley",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "madelync@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 11"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAAebvnx4LnNKsFWppdcopJw=')",
          "Id": "AAUQAAebvnx4LnNKsFWppdcopJw=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Albert Raley",
          "GivenName": "Albert",
          "Surname": "Raley",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "albertr@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Bulding T"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAPqWcitEhEFNuvaSLteeN9M=')",
          "Id": "AAUQAPqWcitEhEFNuvaSLteeN9M=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Emanuel Grider",
          "GivenName": "Emanuel",
          "Surname": "Grider",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "edh@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAIqrTSzA3N1BglLTWFzgql4=')",
          "Id": "AAUQAIqrTSzA3N1BglLTWFzgql4=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Frederick Magnuson",
          "GivenName": "Frederick",
          "Surname": "Magnuson",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "fredrickm@service.exchange.contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 3"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAId9cw-r_cZDtd5mU6QVvR4=')",
          "Id": "AAUQAId9cw-r_cZDtd5mU6QVvR4=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Beryl Maddox",
          "GivenName": "Beryl",
          "Surname": "Maddox",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "berylm@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 3"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAPbEMn4Y_EhPoPJIAfe9-v4=')",
          "Id": "AAUQAPbEMn4Y_EhPoPJIAfe9-v4=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Vilma Young",
          "GivenName": "Vilma",
          "Surname": "Young",
          "Title": "LEAD",
          "EmailAddresses": [
            {
              "Address": "vilmay@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building T"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQANxLXO4NLchEiyteaLb_HNM=')",
          "Id": "AAUQANxLXO4NLchEiyteaLb_HNM=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Edna Foreman",
          "GivenName": "Edna",
          "Surname": "Foreman",
          "Title": null,
          "EmailAddresses": [
            {
              "Address": "ednaf@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building L"
        },
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAQkADA5OWM3MmE5LTNmYmItNDk1NS1hZDY0LTAwYjBhZjc4MTg3YwAQABMxxzYk20pLinJq19EtuKc=')",
          "Id": "AAQkADA5OWM3MmE5LTNmYmItNDk1NS1hZDY0LTAwYjBhZjc4MTg3YwAQABMxxzYk20pLinJq19EtuKc=",
          "Sources": [
            {
              "Type": "Outlook Contacts"
            }
          ],
          "DisplayName": "Tammi Pickett",
          "GivenName": "Tammi",
          "Surname": "Pickett",
          "Title": "Engineer",
          "EmailAddresses": [
            {
              "Address": "tammip@contoso.com"
            }
          ],
          "CompanyName": "Contoso",
          "OfficeLocation": null
        },
      "@odata.nextLink": "https://outlook.office.com/api/beta/me/people/?%24search=%22ed+topic%3a+Aziz+ansari%22&
%24top=10&%24skip=10"
    }
```
 
 ****
 
 <a name="FuzzySearch"></a> 
 **あいまい検索を実行します。**
 
 次のような要求には検索者「Hermaini ホール」です。 「Herminia 船体」という名前の関連する人があるため、「Herminia 船体」の情報が返されます。
 
 ```no-highlight
 https://outlook.office.com/api/beta/me/people/?$search="hermaini hall"
 ```
 
 サーバーからの応答を次に示します。
 
 ```no-highlight
    {
      "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/People",
      "value": [
        {
          "@odata.id": "https://outlook.office.com/api/beta/users/4579DA25-3624-44CD-AE44-9777EEB9D292@F56380F1-06A5-4239-B31E-C8B44DF1F05A/People('AAUQAL5wQK1L1MNNsL4qzoFWZiQ=')",
          "Id": "AAUQAL5wQK1L1MNNsL4qzoFWZiQ=",
          "Sources": [
            {
              "Type": "Directory"
            }
          ],
          "DisplayName": "Herminia Hull",
          "GivenName": "Herminia",
          "Surname": "Hull",
          "Title": "MANAGER",
          "EmailAddresses": [
            {
              "Address": "herminiah@contoso.com"
            }
          ],
          "CompanyName": "CONTOSO",
          "OfficeLocation": "Building 4"
        }
      ]
    }
```

****

[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]

