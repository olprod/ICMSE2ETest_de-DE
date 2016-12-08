---
title: "Intune とオンプレミスの Exchange Server での条件付きアクセスの使用"
description: "Intune ソリューションを使用して Exchange lokalen を展開します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2a64e898-4c60-48bf-ae14-b05e091e0533
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 7982e0bc78b535998981bee88c0f585d060e1452
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="intune-exchange-on-premises-"></a>Intune を使用した Exchange lokalen の展開


            [会社の電子メールとドキュメントを保護するためのアーキテクチャ ガイダンス](architecture-guidance-for-protecting-company-email-and-documents.md)を確認しました。これでソリューションの展開に進むことができます。

Intune でモバイル デバイスを直接管理するには、ユーザーがデバイスを Intune に登録する必要があります。

## <a name=""></a>展開の手順
Intune ソリューションを使用して Exchange lokalen を展開するには、次の手順に従います。

### <a name="-1-microsoft-intune-exchange-server-"></a>手順 1: Microsoft Intune のオンプレミスの Exchange Server コネクタをインストールして構成する

ユーザーが登録していないモバイル デバイスの場合、Exchange Connector を使用して Exchange ActiveSync 管理を有効にすることができます。 Exchange Connector を使用して Exchange 展開に接続すると、Intune コンソールを使用してモバイル デバイスを管理できます。

「[内部設置型またはホスト型 Exchange 用に Microsoft Intune の内部設置型コネクタを構成する](/intune/deploy-use/intune-on-premises-exchange-connector)」の手順に従って、Microsoft Intune Exchange Connector をダウンロードしてインストールし、構成します。

> [!IMPORTANT]
> Intune アカウントごとに Exchange 接続を 1 つだけセットアップできます。 接続をもう 1 つ構成しようとすると、構成済みの接続が新しい接続で置き換えられます。

### <a name="-2-"></a>2 手順: コンプライアンス ポリシーを作成し、ユーザーに展開する
コンプライアンス ポリシーは、デバイスが条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある規則および設定を定義します。 「[Microsoft Intune でのコンプライアンス ポリシーの作成](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune)」の手順に従って、コンプライアンス ポリシーを作成し、展開します。.

不要になった、会社のすべての電子メールを iOS デバイスから削除する機能が必要な場合は、電子メール プロファイルを作成して展開し、電子メール プロファイルを Intune で管理することを指定するコンプライアンス ポリシーを設定する必要があります。 このコンプライアンス ポリシーの対象にする一連の同じユーザーに電子メール プロファイルを展開する必要があります。 ![電子メール プロファイルを Intune で管理する必要があることを指定できる、コンプライアンス ポリシーの作成ウィザードの [ルール] ページのスクリーンショット](./media/ProtectEmail/Hybrid-Onprem-ExchSrvr-Wizard6.PNG)

このコンプライアンス ポリシーを指定した場合、電子メール アカウントを既に設定しているユーザーはアカウントを手動で削除する必要があります。 その後、アカウントは「[条件付きアクセスのエンドユーザー エクスペリエンス](end-user-experience-conditional-access.md)」で説明する登録プロセスで Intune によって再度追加されます。

> [!IMPORTANT]
> コンプライアンス ポリシーを展開していない状態で、Exchange 条件付きアクセス ポリシーを有効にすると、すべての対象デバイスによるアクセスが許可されます。

### <a name="-3-"></a>3 手順: 条件付きアクセス ポリシーの影響を受けるユーザーを特定する
Exchange Server コネクタが正常に構成されると、Intune にまだ登録されておらず、Exchange Active Sync を使用して組織の Exchange リソースに接続しているデバイスがインベントリに登録されます。  

「[条件付きアクセス ポリシーの効果を評価する](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access)」の手順に従って、条件付きアクセス ポリシーの影響を受けるユーザーを特定します。.


### <a name="-4-"></a>手順 4: 条件付きアクセス ポリシーのユーザー グループを構成する
条件付きアクセス ポリシーは、ポリシーの種類に応じて、さまざまなユーザーのグループを対象とします。 これらのグループには、ポリシーの対象となるユーザーや、ポリシーから除外されるユーザーが含まれます。 ユーザーがポリシーの対象となる場合、ユーザーに使用される各デバイスが電子メールにアクセスするには、ポリシーを遵守している必要があります。

詳細については、「[条件付きアクセス ポリシーのユーザー グループを構成する](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access)」を参照してください。

### <a name="-5-"></a>手順 5: 条件付きアクセス ポリシーを構成する
Exchange lokale 環境の条件付きアクセス ポリシーは、次のフローを使用して、デバイスを許可するかブロックするかを評価します。

![デバイスを許可するかブロックするかを評価するオンプレミスの Exchange Server の条件付きアクセス ポリシーを示すフローチャート](./media/ProtectEmail/conditional-access-8-2.png)

「[条件付きアクセス ポリシーを構成する](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune#configure-conditional-access)」に記載されている情報に従って、条件付きアクセス ポリシーを設定します。.

## <a name=""></a>レポート

### <a name="-"></a>コンプライアンスと条件付きアクセス ポリシーを監視する
Exchange-からブロックされているデバイスを表示するには

Intune ダッシュボードで、**[からブロックされているデバイス Exchange]**タイルをクリックすると、ブロックされているデバイスの数と詳細情報へのリンクが表示されます。 ![Intune ダッシュボードの [Exchange からブロックされているデバイス] タイルのスクリーンショット](./media/ProtectEmail/intune-sa-6blocked-devices.PNG)

## <a name=""></a>この後の対応
モバイル デバイスの会社の電子メールと電子メール データを保護するためのソリューションを展開したら、[条件付きアクセスのエンド ユーザー エクスペリエンス](end-user-experience-conditional-access.md)の詳細を確認します。 これにより、エンド ユーザーが特定のデバイスを登録するときに発生する可能性のある問題に備えることができます。
