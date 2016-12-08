---
title: "条件付きアクセス - オンプレミスの Exchange、Intune、Configuration-Manager"
description: "Konfiguration Manager、オンプレミスの Exchange Server、および Intune を使用して、電子メールへのアクセスを管理し、モバイル デバイスで電子メールのデータを保護します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56b6cd2d-3dea-468b-9f1c-92717c9ec5f5
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 51c6f7fa170382fa38c1cd098b4fb28b2cc8da3d
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="microsoft-intune-configuration-manager-exchange-server-"></a>Exchange-Server von Microsoft Intune と Configuration Manager を使用したオンプレミスの の展開

            [会社の電子メールとドキュメントを保護するためのアーキテクチャ ガイダンス](architecture-guidance-for-protecting-company-email-and-documents.md)を確認しました。これでソリューションの展開に進むことができます。

オンプレミス インフラストラクチャで System Center Configuration Manager と Exchange を既に使用している場合は、Intune を組み込んで、電子メールへのアクセスを管理し、モバイル デバイスで電子メール データを保護することができます。 このソリューションを実装する高度なプロセスは次のとおりです。

-   Konfigurations-Manager コンソールを使用して、オンプレミスの Intune Exchange Connector を構成します。 これにより Konfigurations-Manager-はモバイル デバイスのメールボックスをホストする Exchange Server と通信できるようになります。

-   Exchange Server コネクタの完全な同期を実行して、ユーザーを検出し、オンプレミスの Exchange Server に接続しているすべてのモバイル デバイス Exchange ActiveSync-ID (EASID) のインベントリを実行します。

-   条件付きアクセス ポリシーの対象とするか、除外するユーザー グループのユーザー コレクションを作成します。 次に、デバイスが条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある規則および設定を定義するコンプライアンス ポリシーを作成します。

-   条件付きアクセスの適用を開始します。

## <a name="-exchange-server-"></a>Exchange Server オンプレミスの の条件付きアクセス制御の流れ
Exchange Server 次の図は、オンプレミスの で電子メールにアクセスしようとするクライアントの制御フローを示しています。

![Konfigurieren der Intune とオンプレミスの Exchange Server での Manager の条件付きアクセスの制御フロー ダイアグラム](./media/ProtectEmail/Hybrid-on-prem-CA-architecture.png)

-   Microsoft Intune: デバイスの準拠と条件付きアクセス ポリシーを管理します。

-   Microsoft Azure Active Directory: ユーザーを認証し、デバイスの準拠状況を提供します。

-   Konfigurations-Manager: デバイスの登録を管理し、レポートを提供します。

-   Exchange-Server オンプレミスの: デバイスの状態に基づいて電子メールへのアクセスを許可します。

## <a name=""></a>始める前に
このソリューションを実装するための要件が環境に含まれていることを確認します。

> [!NOTE]
> Konfigurations-Manager が Intune サービスを使用してモバイル デバイスを管理するように既に構成されている場合は、[展開の手順](#deployment-steps)に進むことができます。

-   
            [オンプレミス コネクタのハードウェア要件](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)を満たしていることを確認します。

-   1 累積的な更新プログラム 以降が適用された System Center 2012 R2 Configuration Manager SP1 を実行していることを確認します。

-   
            [Exchange Web サービス (EWS) エンドポイント](https://technet.microsoft.com/library/hh529912.aspx)が検出用に正しく構成されていることを確認します。 必要に応じて、EWS 接続の問題を特定するのに役立つツールについて チームに問い合わせてください。 サポート-Konfigurations-Manager EWS により、開発者は標準の HTTP を使用して Exchange のメールボックスとコンテンツを対話操作できます。

-   Exchange サービスをインストールし、信頼できる公的な証明機関から購入した[有効なデジタル証明書](https://technet.microsoft.com/library/dd351044.aspx)に割り当てます。

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

> [!IMPORTANT]
> 必要なコマンドレットを使用せずに Exchange Server コネクタをインストールまたは使用しようとした場合、サイト サーバー コンピューターの EasDisc.log ログ ファイルに、「_Invoke-Cmdlet &lt;Cmdlet&gt; Failed」というメッセージが記録されます_。

## <a name=""></a>展開の手順
Exchange Server オンプレミスの のソリューションを展開するには、次の手順に従います。

### <a name="-1-intune-"></a>手順 1: Intune コネクタ ロールがインストールされていることを確認します。
Konfigurations-Manager が Intune と対話できるように、Intune コネクタ ロールがインストールされていることを確認します。 詳細については、「[-Konfigurations-Manager と Microsoft Intune を使用してモバイル デバイスを管理する](https://technet.microsoft.com/library/JJ884158.aspx)」をご覧ください。

### <a name="-2-exchange-server-"></a>手順 2: Exchange Server コネクタをインストールし、構成します。
Konfigurations-Manager では、1 つの Exchange 組織に設定できるコネクタは 1 つのみです。

> [!IMPORTANT]
> Exchange Server コネクタをインストールする前に、使用する Microsoft Exchange のバージョンが でサポートされているかどうかを確認してください。-Konfigurations-Manager 詳細については、「[-Konfigurations-Manager のサポートされている構成](https://technet.microsoft.com/library/gg682077.aspx)」をご覧ください。

「[-Konfigurations-Manager と Exchange を使用してモバイル デバイスを管理する方法](https://technet.microsoft.com/library/gg682001.aspx)」の手順に従って Exchange Server コネクタをインストールし、構成します。

### <a name="-3"></a>手順 3:完全同期を実行してユーザーを検出します。

1.  Konfigurations-Manager コンソールで**[管理]**をクリックし、 **[階層の構成]**を展開して、 **[für Exchange Server コネクタ]**を選択します。

2.  でインストールした 手順 2 für Exchange Server コネクタを選択します。

3.   をクリックします。 **[今すぐ同期]**

    ![完全な同期を実行する場所を示す ショット コンソールのスクリーン-Konfigurations-Manager](./media/ProtectEmail/Hybrid-Onprem-Run-FullSync.png)

この完全な同期は、デバイスの数によっては、完了に数時間かかります。 24 完全な同期は、既定で 時間ごとに実行されます。 差分同期は、前回の完全同期以降のデバイスの接続を検出し、Exchange Server コネクタのインストール時に設定した間隔ごとに実行されます。 これにより、条件付きアクセスを適用できるように、新しいユーザーと新しい Exchange ユーザーが迅速に検出されます。

Konfigurations-Manager のトレース ログ ツールを使用して EasDisc.log ファイル (Konfigurations-Manager をインストールした**Microsoft Configuration Manager/Protokolle**フォルダーにあります) を開き、コネクタが実行され、デバイス接続に対してクエリを実行していることを確認できます。 完全同期が完了したら、オンプレミスの Exchange Server に接続しているすべてのモバイル デバイス Exchange ActiveSync-ID (EASID) のインベントリが実行されます。

### <a name="-4-"></a>手順 4: ユーザー コレクションを作成します。
条件付きアクセス ポリシーの対象となる Intune ユーザー グループを決定します。 次に、条件付きアクセス ポリシーの対象とするか、除外するユーザー グループのユーザー コレクションを作成します。 条件付きアクセスを後で適用する場合は、これらのグループを指定します。

「[-Konfigurations-Manager でのコレクションの作成方法](https://technet.microsoft.com/library/gg712295.aspx)」の手順に従ってユーザー コレクションを作成します。.

### <a name="-5-"></a>手順 5: コンプライアンス ポリシーを作成し、ユーザーに展開します。
コンプライアンス ポリシーは、デバイスが条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある規則および設定を定義します。 「[-Konfigurations-Manager のコンプライアンス ポリシー](https://technet.microsoft.com/library/mt131417.aspx)」の手順に従ってコンプライアンス ポリシーを作成します。.

不要になった、会社のすべての電子メールを iOS デバイスから削除する機能が必要な場合は、電子メール プロファイルを作成して展開し、電子メール プロファイルを Intune で管理することを指定するコンプライアンス ポリシーを設定する必要があります。 このコンプライアンス ポリシーの対象にする一連の同じユーザーに電子メール プロファイルを展開する必要があります。

![電子メール プロファイルを Intune で管理する必要があることを指定できる、コンプライアンス ポリシーの作成ウィザードの [ルール] ページのスクリーンショット](./media/ProtectEmail/Hybrid-Onprem-ExchSrvr-Wizard6.PNG)

このコンプライアンス ポリシーを指定した場合、電子メール アカウントを既に設定しているユーザーはアカウントを手動で削除する必要があります。 その後、アカウントは「[条件付きアクセスのエンドユーザー エクスペリエンス](end-user-experience-conditional-access.md)」で説明する登録プロセスで Intune によって再度追加されます。

コンプライアンス ポリシーを作成した後、ボックスの一覧でコンプライアンス ポリシーの名前を選択し、 **[展開]**をクリックします。

### <a name="-6-"></a>手順 6: 条件付きアクセス ポリシーを構成します。
最初に、条件付きアクセスを適用する方法とタイミング、および影響を受ける従業員を決定します。 次に、「[-Konfigurations-Manager での Exchange 電子メールの条件付きアクセス](https://technet.microsoft.com/library/mt131421.aspx)」の手順に従って、オンプレミスの Exchange Server の条件付きアクセス ポリシーを構成します。

### <a name="-7-"></a>手順 7: 登録を監視し、条件付きアクセスを適用します。
既に多数のユーザーが Intune に登録され、かつ準拠している場合は、1 日あたり約 500 人のユーザーにロールアウトすることによって、条件付きアクセスの適用を開始できます。 この場合、70 000 人のユーザーに対して約 4 から 5 か月を要し、非常に多数のユーザーに対して同時に電子メール アクセスを制限することなく、発生する可能性のある問題を整理することができます。

多数のユーザーが Intune にまだ登録されていない場合は、「[条件付きアクセスのエンドユーザー エクスペリエンス](end-user-experience-conditional-access.md)」で説明するように、ユーザーが画面の指示に従って条件付きアクセスに登録できます。

## <a name=""></a>検証手順
Konfigurations-Manager のトレース ログ ツールを使用して EasDisc.log ファイル (Konfigurations-Manager をインストールした Microsoft Configuration Manager/protokolliert フォルダーにあります) を開きます。 ログ ファイルで "Exchange Connector" を検索し、Exchange Connector が実行されているかどうか、および接続されているデバイスの数に関する情報を見つけます。

![Konfigurations-Manager のトレース ログ ツールで開いた EasDisc.log ファイルのスクリーンショット](./media/ProtectEmail/Hybrid-Onprem-Eas-DiscLog-Sample.PNG)

Konfigurations-Manager のトレース ログ ツールは、[System Center 2012 R2 Configuration Manager ツールキット](http://www.microsoft.com/download/details.aspx?id=50012)に含まれています。

## <a name=""></a>レポート
Konfigurations-Manager コンソールを使用して、Exchange Connector によって検出されたデバイスに関する特定の情報を表示できます。 Exchange-Server 条件付きアクセスを適用するデバイスについて、各デバイスの現在のステータス、デバイスが最後に に接続された日時などを表示できます。

Konfigurations-Manager コンソールで、 **[資産とコンプライアンス]**をクリックし、 **[デバイス]**をクリックします。  **[MS exchange のアクセス状態]**列で各デバイスの現在のステータス (ブロック済みまたは許可) を確認できます。 この列がまだ表示されていない場合は、列のタイトル バー領域で右クリックして追加します。  **Für exchange Server への前回同期成功時間**列を追加して、Exchange によって報告された各デバイスの前回同期が成功した時刻を表示することもできます。

![Konfigurations-Manager コンソールのデバイスの一覧のスクリーンショット](./media/ProtectEmail/Hybrid-Onprem-Verify-Devices-State.png)

SQLServer Reporting Services (SSRS) を実行している場合、デバイスのコンプライアンス対応状態を表示する条件付きアクセス レポート、Exchange Connector がインストールされ、実行されているかどうか、および EAS アクセス状態を表示できます。 Active Directory の登録、EAS のアクティブ化、およびデバイスの所有者に関する情報も提供されます。

![レポートのサンプルのスクリーンショット SQL Server Reporting Services](./media/ProtectEmail/Hybrid-Reports-CA.png)

SSRS レポートを表示するには、プライマリ サーバーにレポート ロールをインストールしておく必要があります。

1.  Konfigurations-Manager で、 **[管理]**、 **[階層の構成]**、 **[サイトの構成]**の順にクリックし、 **[サーバーとサイト システムの役割]**をクリックします。

2.  サーバーを選択し、 **[サイト システムの役割の追加]**をクリックして、サイト システムの役割の追加ウィザードを開きます。

3.  [システムの役割の選択] ページで、 **[レポート サービス ポイント]**チェックボックスを選択します。 レポート サービス ポイントにクライアント管理に関するレポートが表示されます。

4.   をクリックします。 **[次へ]**

構成ポリシーの展開状態を次に示します。

![構成ポリシーの展開状態のスクリーンショット](./media/ProtectEmail/Hybrid-Reports-Deployment-Status.png)

### <a name=""></a>遅延
デバイスは、Exchange Connector によって検出されるとすぐにブロックされます。 Die Exchange Server ブロックの遅延は、設定された完全同期と差分同期の間隔、およびデバイスが に接続するときのこれらの間隔間の時間に応じて異なります。 既定では、完全同期は 24 時間ごとに実行され、デルタ同期は 240 分ごとに実行されます。 この遅延期間中、デバイスは準拠していると見なされる可能性があります。

## <a name=""></a>この後の対応
モバイル デバイスの会社の電子メールと電子メール データを保護するためのソリューションを展開したら、[条件付きアクセスのエンド ユーザー エクスペリエンス](end-user-experience-conditional-access.md)の詳細を確認します。 これにより、エンド ユーザーが特定のデバイスを登録するときに発生する可能性のある問題に備えることができます。
