---
title: "Intune でのモバイル アプリ管理ポリシーの使用"
description: "Intune でモバイル アプリ管理ポリシーを使用してアプリを作成し展開します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d7c4104-b85f-407e-8832-0e6bbac934f5
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: c66a8f31c11062ecaff9d6f9c2a58ca7bca27832
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="intune-"></a>Intune でのモバイル アプリ管理ポリシーの使用
多くの企業が Microsoft Intune を利用する主な理由の 1 つは、ユーザーの仕事の完了に必要なアプリを展開するためです。 アプリを展開する前に、[デバイスを管理対象にする](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)必要があります。

たとえば、勤務先で Microsoft Word が使われている場合、Windows 用、iOS 用、Android 用など、さまざまなバージョンが存在します。 IT-管理者は、社内データのセキュリティを確保しながら、ユーザーに仕事ができる環境を提供するという目的で、さまざまなデバイスやコンピューター プラットフォーム上の多数のアプリを管理するという難題に直面します。

Intune を Configuration Manager とともに使用している場合は、「[-Konfigurations-Manager のモバイル アプリケーション管理ポリシーを使用してアプリを制御する方法](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396)」をご覧ください。

モバイル アプリ管理ポリシー (MAM) は以下をサポートします。
- Android 4 以降を実行するデバイス。
- iOS 7 以降を実行するデバイス。

> [!NOTE]
> MAM ポリシーでは、Intune に登録されているデバイスがサポートされます。 Intune で管理されていないデバイスのアプリ管理ポリシーを作成する方法については、「[Microsoft Intune でモバイル アプリケーション管理ポリシーを使用してデータを保護する](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)」をご覧ください。

他の Intune ポリシーとは異なり、MAM ポリシーは直接展開しません。 代わりに、制限するアプリにポリシーを関連付けます。 アプリがデバイスにデプロイされ、インストールされると、指定した設定が有効になります。

アプリに制限を適用するには、アプリに Microsoft Intune アプリ ソフトウェア開発キット (SDK) を組み込む必要があります。 この種類のアプリを取得するには、次の 2 つの方法があります。

- 
            **ポリシー管理型アプリを使用する**- アプリ SDK が組み込まれています。 この種類のアプリを追加するには、iTunes ストアや Google wiedergeben などのアプリ ストアからアプリへのリンクを指定します。 それ以上の処理は、この種類のアプリには必要ありません。 サポートされている Microsoft アプリの完全な一覧については、Microsoft Intune アプリケーション パートナー ページの[Microsoft Intune モバイル アプリケーション ギャラリー](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)をご覧ください。 アプリをクリックし、サポートされるシナリオ、プラットフォーム、アプリのマルチ ID 対応を確認してください。
- 
            **"ラップされた" アプリを使用する**- Microsoft Intune アプリ ラッピング ツールを使用して、アプリ SDK を含むように再パッケージされたアプリ。 通常、このツールは、社内で作成された企業アプリの処理に使用されます。 このツールを使用して、アプリ ストアからダウンロードされたアプリを処理することはできません。 次を参照してください。
  - [Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために iOS アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
  - [Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために Android アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

iOS や Android 用の Outlook アプリなど、管理対象アプリの一部は**複数の ID**をサポートしています。 つまり、Intune により、アプリでは管理設定が会社のアカウントまたはデータのみに適用されます。

Outlook アプリの使用例を次に示します。
- ユーザーが会社と個人の電子メール アカウントを構成した場合、Intune は、会社のアカウントのみに管理設定を適用し、個人のアカウントは管理しません。
- Outlook デバイスが廃止された場合や登録解除された場合は、会社の データだけがデバイスから削除されます。
- 使用する会社のアカウントは、デバイスを Intune に登録するときに使用したものと同じアカウントにする必要があります。

Word、Excel、および PowerPoint も複数の ID をサポートしていますが、企業のものと特定できるデータを OneDrive や SharePoint などのサービスから編集している場合にのみポリシーによる制限があります。

## <a name="-intune-"></a>モバイル アプリ管理ポリシーを使用した Intune でのアプリの作成と展開

- 手順 1: ポリシー管理型アプリへのリンクを取得するか、ラップされたアプリを作成する。
- 手順 2: クラウド ストレージにアプリを公開する。
- 手順 3: モバイル アプリ管理ポリシーを作成する。
- 手順 4: アプリを展開し、アプリをモバイル アプリ管理ポリシーに関連付けるオプションを選択する。
- 手順 5: アプリの展開を監視する。

### <a name="-1-"></a>手順 1: ポリシー管理型アプリへのリンクを取得するか、ラップされたアプリを作成する
- 
            **ポリシー管理型アプリへのリンクを取得するには**- アプリ ストアから、展開するポリシー管理型アプリの URL を見つけてメモします。 たとえば、Microsoft Word für iPad アプリの URL は、[https://itunes.apple.com/jp/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)です。
- 
            **ラップされたアプリを作成するには**- 「[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために iOS アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)」と「[Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために Android アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)」の各トピックの情報を活用して、ラップされたアプリを作成します。 このツールでは、クラウド ストレージにアプリを発行するときに使用する処理済みのアプリが作成されます。

### <a name="-2-"></a>手順 2: クラウド ストレージにアプリをアップロードする
管理対象アプリを公開する手順は、公開するのがポリシー管理型アプリであるか、Microsoft Tool Textumbruch für Intune App für iOS を使用して処理されたアプリであるかによって異なります。

クラウド ストレージにアプリをアップロードする完全な手順については、「[Microsoft Intune でモバイル デバイスのアプリを追加する](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune#add-the-app)」をご覧ください。

### <a name="-3-"></a>手順 3: モバイル アプリ管理ポリシーを作成する
Azure ポータルは MAM ポリシーを作成するために推奨される管理コンソールです。 Azure ポータルでは、次の MAM シナリオをサポートします。
- Intune に登録されたデバイス
- サードパーティの MDM ソリューションで管理されるデバイス
- MDM ソリューション (BYOD) で管理されないデバイス

MAM ポリシーの作成に Azure ポータルを使用する場合の詳細については、「[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)」をご覧ください。

現在、Intune 管理コンソールを使用してデバイスを管理している場合は、Intune に登録済みのデバイスのアプリをサポートする MAM ポリシーを[Intune 管理コンソール](https://docs.microsoft.com/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console#-step-3-create-a-mobile-application-management-policy)を使用して作成できます。


### <a name="-4-"></a>手順 4: アプリを展開し、アプリをモバイル アプリケーション管理ポリシーに関連付けるオプションを選択する
Azure ポータルを使用している場合、[ユーザーに MAM ポリシーを展開](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune#deploy-a-policy-to-users)します。

Intune ポータルを使用している場合、モバイル アプリの管理ページでモバイル アプリ管理ポリシーを選択して、ポリシーをアプリに関連付けた上で、[アプリを展開します](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune#deploy-an-app)。

Intune からデバイスの登録を解除すると、ポリシーはアプリからは削除されません。 ポリシーが適用されているアプリは、アプリのアンインストールおよび再インストール後もポリシー設定を保持します。

#### <a name=""></a>アプリが既にデバイスに展開されている場合の対処方法

アプリを展開するときに、対象とするユーザーやデバイスのいずれかにアプリの管理対象外バージョンが既にインストールされている (例: ユーザーがアプリ ストアから Microsoft Word をインストールしている) 状況が発生する場合があります。

この場合は、構成した管理対象バージョンをインストールできるように、管理対象外バージョンを手動でアンインストールするようにユーザーに依頼する必要があります。

ただし、IOS 9 以降を実行するデバイスの場合は、Intune が自動的に、既存アプリの管理を引き継ぐための権限を与えるようユーザーに要求します。 ユーザーが同意すると、アプリは Intune による管理の対象になり、アプリに関連付けられたすべての MAM ポリシーも適用されます。


### <a name="-5-mam-"></a>手順 5: MAM ポリシーでアプリの展開を監視する
次の手順を使用し、Intune コンソールからのアプリの展開を監視し、ポリシーの競合を解決します。

1. 
            [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]**をクリックします。
2. 次の手順のいずれかを実行します。
  -  
            をクリックし、デバイスを確認するユーザーをダブルクリックします。 **[すべてのユーザー]** [ユーザー プロパティ] ページで、**[デバイス]**をクリックし、確認するデバイスをダブルクリックします。
  -  
            **[すべてのデバイス] > [すべてのモバイル デバイス]**の順にクリックします。 [デバイス グループのプロパティ] ページで、**[デバイス]**をクリックし、確認するデバイスをダブルクリックします。
3. [モバイル デバイスのプロパティ] ページで、**[ポリシー]**をクリックして、デバイスに展開されている MAM ポリシーの一覧を表示します。
4. 状態を表示する MAM ポリシーを選択します。 下のペインで、ポリシーの詳細を表示し、ノードを展開してその設定を表示します。
5.  各 MAM ポリシーの [状態] 列に、 [準拠] 、 [準拠 (保留中)] [エラー] 、または が表示されます。 選択したポリシーに 1 つまたは複数の設定の競合がある場合、このフィールドに [エラー] が表示されます。
6.  競合を識別したら、競合するポリシー設定を変更して同じ設定を使用するようにしたり、アプリとユーザーにポリシーを 1 つだけデプロイしたりできます。

> [!NOTE]
> アプリケーションを[Azure ポータル](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)、または[Intune コンソール](https://docs.microsoft.com/intune/deploy-use/monitor-apps-in-microsoft-intune)を使用して監視するときの概要情報を参照してください。

## <a name=""></a>この後の対応

MAM ポリシーに関連付けられているアプリを作成および展開したら、「[MAM のエンド ユーザー エクスペリエンス](end-user-experience-mam.md)」を参照してください。 これで、発生する可能性のあるすべての問題に備えることができます。
