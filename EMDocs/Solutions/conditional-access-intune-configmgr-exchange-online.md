---
title: "条件付きアクセス - Exchange-Online、Intune、Configuration-Manager"
description: "Konfiguration Manager、Exchange Online、および Intune を使用して、電子メールへのアクセスを管理し、モバイル デバイスで電子メールのデータを保護します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 06921361-9475-46e6-9368-3cc44c84b22f
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: e7c9d1112e0b30a51e41e7344b3cd1d487b7b5bb
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="microsoft-intune-configuration-manager-exchange-online-"></a>Microsoft Intune と を使用した Konfigurations-Manager für Exchange Online の展開

            [会社の電子メールとドキュメントを保護するためのアーキテクチャ ガイダンス](architecture-guidance-for-protecting-company-email-and-documents.md)を確認しました。これでソリューションの展開に進むことができます。

System Center Configuration Manager と Exchange Online を既に使用している場合は、Intune を組み込んで、電子メールへのアクセスを管理し、モバイル デバイスで電子メール データを保護することができます。 このソリューションを実装する高度なプロセスは次のとおりです。

-   デバイスが条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある規則および設定を定義するコンプライアンス ポリシーを作成します。

-   条件付きアクセスの適用を開始します。

-   必要に応じて、Exchange Online に対して Exchange Server コネクタを構成します。 このコネクタはレポートのためにのみ必要です。 条件付きアクセスを有効にするために必要となるわけではありません。

## <a name="exchange-online-"></a>Exchange Online の条件付きアクセス制御の流れ
次の図は、Exchange Online で電子メールにアクセスしようとするクライアントの制御フローを示しています。 条件付きアクセスを適用する前に、A と B を実行することができます。

![Intune と Exchange Online での ダイアグラム の条件付きアクセスの制御フロー-Konfigurations-Manager](./media/ProtectEmail/Hybrid-Exchange-Online-CA-architecture.png)

-   Microsoft Intune: デバイスの準拠と条件付きアクセス ポリシーを管理します。

-   Microsoft Azure Active Directory: ユーザーを認証し、デバイスの準拠状況を提供します。

-   Konfigurations-Manager: 有効になっている場合、デバイスの登録を管理し、レポートを提供します。

-   Exchange Online: デバイスの状態に基づいて電子メールへのアクセスを許可します。

## <a name=""></a>始める前に
このソリューションを実装するための要件が環境に含まれていることを確認します。

-   Exchange サービスをインストールし、信頼できる公的な証明機関から購入した[有効なデジタル証明書](https://technet.microsoft.com/library/dd351044.aspx)に割り当てます。

-   1 累積的な更新プログラム 以降が適用された System Center 2012 R2 Configuration Manager SP1 を実行していることを確認します。

-   次の Exchange Server コマンドレットを実行する権限を持つアカウント (ローカルまたはドメイン管理者) を構成します。

    Clear-ActiveSyncDevice

    Get-ActiveSyncDevice

    Get-ActiveSyncDeviceAccessRule

    Get-ActiveSyncDeviceStatistics

    Get-ActiveSyncMailboxPolicy

    Get-ActiveSyncOrganizationSettings

    Get-ExchangeServer

    Get-Recipient

    Set-ADServerSettings

    Set-ActiveSyncDeviceAccessRule

    Set-ActiveSyncMailboxPolicy

    Set-CASMailbox

    Neue ActiveSyncDeviceAccessRule

    Neue ActiveSyncMailboxPolicy

    Remove-ActiveSyncDevice

## <a name=""></a>展開の手順
Exchange Online ソリューションを展開するには、次の手順に従います。

### <a name="-1-"></a>手順 1: コンプライアンス ポリシーを作成し、ユーザーに展開します。
コンプライアンス ポリシーは、デバイスが条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある規則および設定を定義します。 「[-Konfigurations-Manager のコンプライアンス ポリシー](https://technet.microsoft.com/library/mt131417.aspx)」の手順に従ってコンプライアンス ポリシーを作成します。.

不要になった、会社のすべての電子メールを iOS デバイスから削除する機能が必要な場合は、電子メール プロファイルを作成して展開し、電子メール プロファイルを Intune で管理することを指定するコンプライアンス ポリシーを設定する必要があります。 このコンプライアンス ポリシーの対象にする一連の同じユーザーに電子メール プロファイルを展開する必要があります。

![電子メール プロファイルを Intune で管理する必要があることを指定できる、コンプライアンス ポリシーの作成ウィザードの [ルール] ページのスクリーンショット](./media/ProtectEmail/Hybrid-Onprem-ExchSrvr-Wizard6.PNG)

このコンプライアンス ポリシーを指定した場合、電子メール アカウントを既に設定しているユーザーはアカウントを手動で削除する必要があります。 その後、アカウントは「[条件付きアクセスのエンドユーザー エクスペリエンス](end-user-experience-conditional-access.md)」で説明する登録プロセスで Intune によって再度追加されます。

コンプライアンス ポリシーを作成した後、ボックスの一覧でコンプライアンス ポリシーの名前を選択し、 **[展開]**をクリックします。

### <a name="-2-"></a>手順 2: 条件付きアクセス ポリシーを構成します。
最初に、条件付きアクセスを適用する方法とタイミング、および影響を受ける従業員を決定します。 次に、「[-Konfigurations-Manager での Exchange 電子メールの条件付きアクセス](https://technet.microsoft.com/library/mt131421.aspx)」の手順に従って Exchange Online の条件付きアクセス ポリシーを有効にします。

> [!NOTE]
> 条件付きアクセス ポリシーは、Intune コンソールで構成する必要があります。 Intune コンソールに Configuration Manager を介してアクセスし、次の手順を開始します。 指示された場合は、Configuration Manager と Intune 間のコネクタを設定するために使用されたのと同じ資格情報を使用してログインします。

### <a name="-3-exchange-server-"></a>手順 3: Exchange-Server (*省略可能*) コネクタをインストールし、構成します。
Konfigurations-Manager では、1 つの Exchange 組織に設定できるコネクタは 1 つのみです。

> [!IMPORTANT]
> Exchange Server コネクタをインストールする前に、使用する Microsoft Exchange のバージョンが でサポートされているかどうかを確認してください。-Konfigurations-Manager 詳細については、「[-Konfigurations-Manager のサポートされている構成](https://technet.microsoft.com/library/gg682077.aspx)」をご覧ください。

「[-Konfigurations-Manager と Exchange を使用してモバイル デバイスを管理する方法](https://technet.microsoft.com/library/gg682001.aspx)」の手順に従って Exchange Server コネクタをインストールし、構成します。

## <a name=""></a>検証手順
このソリューションで任意の Exchange Server コネクタを構成した場合は、Configuration Manager のトレース ログ ツールを使用して EasDisc.log ファイル (Konfigurations-Manager をインストールした Microsoft Configuration Manager/protokolliert フォルダーにあります) を開くことができます。 ログ ファイルで "Exchange Connector" を検索し、Exchange Connector が実行されているかどうか、および接続されているデバイスの数に関する情報を見つけます。

![Konfigurations-Manager のトレース ログ ツールで開いた EasDisc.log ファイルのスクリーンショット](./media/ProtectEmail/Hybrid-Onprem-Eas-DiscLog-Sample.PNG)

Konfigurations-Manager のトレース ログ ツールは、[System Center 2012 R2 Configuration Manager ツールキット](https://www.microsoft.com/download/details.aspx?id=50012)に含まれています。

## <a name=""></a>レポート
任意の Exchange Server コネクタを構成した場合は、Configuration Manager コンソールを使用して、Exchange Connector によって検出されたデバイスに関する特定の情報を表示できます。 Exchange-Server 条件付きアクセスを適用するデバイスについて、各デバイスの現在のステータス、デバイスが最後に に接続された日時などを表示できます。

Konfigurations-Manager コンソールで、 **[資産とコンプライアンス]**をクリックし、 **[デバイス]**をクリックします。  **[MS exchange のアクセス状態]**列で各デバイスの現在のステータス (検疫済みまたは許可) を確認できます。 この列がまだ表示されていない場合は、列のタイトル バー領域で右クリックして追加します。  **Für exchange Server への前回同期成功時間**列を追加して、Exchange によって報告された各デバイスの前回同期が成功した時刻を表示することもできます。

![Konfigurations-Manager コンソールのデバイスの一覧のスクリーンショット](./media/ProtectEmail/Hybrid-Onprem-Verify-Devices-State.png)

SQLServer Reporting Services (SSRS) を実行している場合、デバイスのコンプライアンス対応状態を表示する条件付きアクセス レポート、Exchange Connector がインストールされ、実行されているかどうか、および EAS アクセス状態を表示できます。 Active Directory の登録、EAS のアクティブ化、およびデバイスの所有者に関する情報も提供されます。

![レポートのサンプルのスクリーンショット SQL Server Reporting Services](./media/ProtectEmail/Hybrid-Reports-CA.png)

SSRS レポートを表示するには、プライマリ サーバーにレポート ロールをインストールしておく必要があります。

1.  Konfigurations-Manager で、 [**管理] &gt; [階層の構成] &gt; [サイトの構成] &gt; [サーバーとサイト システムの役割]**をクリックします。

2.  サーバーを選択し、 **[サイト システムの役割の追加]**をクリックして、サイト システムの役割の追加ウィザードを開きます。

3.  [システムの役割の選択] ページで、 **[レポート サービス ポイント]**チェックボックスを選択します。 レポート サービス ポイントにクライアント管理に関するレポートが表示されます。

4.   をクリックします。 **[次へ]**

構成ポリシーの展開状態を次に示します。

![構成ポリシーの展開状態のスクリーンショット](./media/ProtectEmail/Hybrid-Reports-Deployment-Status.png)

### <a name=""></a>遅延
最新の認証を使用するデバイスでは、条件付きアクセスがすぐに適用されます。 EAS プロトコルを介して接続するデバイスの場合、既定の設定に基づいて、条件付きアクセスが適用されるまでに最大 6 時間の時間差があることがあります。 この期間中、デバイスは準拠していると見なされる可能性があります。

## <a name=""></a>この後の対応
モバイル デバイスの会社の電子メールと電子メール データを保護するためのソリューションを展開したら、[条件付きアクセスのエンド ユーザー エクスペリエンス](end-user-experience-conditional-access.md)の詳細を確認します。 これにより、エンド ユーザーが特定のデバイスを登録するときに発生する可能性のある問題に備えることができます。
