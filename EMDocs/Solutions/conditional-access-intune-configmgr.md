---
title: "Intune と Configuration Manager による条件付きアクセスの使用"
description: "Konfigurations-Manager ソリューションで Intune を展開します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e65a0662-33ff-4e8c-9305-a21e80ea0f69
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: db5c3899deebf3e85142a653673bf9b0c3a20af5
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="intune-configuration-manager-"></a>Intune と Configuration Manager による条件付きアクセスの使用
このトピックは、電子メールへのアクセスを管理するために、社内でオンプレミスの System Center Configuration Manager と Microsoft Exchange Server、Exchange Online、または両方のハイブリッド展開を既に使用していることを前提としています。 このソリューションでは、場所に関係なくあらゆる種類のデバイスで電子メールへのアクセスを安全に管理するために、既存の Konfigurations-Manager 環境と Intune を組み合わせて使用します。

> [!TIP]
> このトピック全体のダウンロード可能なコピーは、 [TechNet ギャラリー](https://gallery.technet.microsoft.com/Deploying-Enterprise-16499404)から入手できます。

## <a name=""></a>始める前に
条件付きアクセスの使用を開始する前に、次の該当する要件を満たしていることを確認してください。

## <a name="exchange-online-"></a>Exchange Online の場合
Exchange Online への条件付きのアクセスでは、次を実行するデバイスがサポートされます。

-   Windows 8.1 以降 (Intune に登録されている場合)

-   Windows 7.0 以降 (ドメインに参加している場合)

-   Windows Phone 8.1 以降

-   iOS 7.1 以降

-   Android 4.0 以降、Samsung Knox Standard 4.0 以降

さらに、デバイスを Azure Active Directory Gerät-Registrierung Service (AAD DRS) に登録する必要があります。

AAD DRS は、Intune や Office 365 のお客様に対して自動的にアクティブ化されます。 AD FS-Gerät Registrierung Service をデプロイ済みのお客様には、オンプレミスの Active Directory で登録されたデバイスは表示されません。

-   Exchange Online を含む Office 365 サブスクリプション (E3 など) を使用する必要があります。 ユーザーには Exchange Online のライセンスが必要です。

-   オプションの**Microsoft Intune Dienst Webdienstkonnektor**は、Intune を Microsoft Exchange Online に接続します。 これにより、Intune コンソールを使用してデバイス情報を管理できるようになります (「[Exchange ActiveSync および Microsoft Intune を使用したモバイル デバイス管理](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)」を参照してください) 。 コンプライアンス ポリシーまたは条件付きアクセス ポリシーを使用するうえでコネクタを使用する必要はありませんが、条件付きアクセスの影響を評価するためのレポートの実行に必要です。

    コネクタを構成すると、Intune の一部の Exchange ActiveSync ポリシーが Office コンソールに表示される場合がありますが、既定のポリシーとして設定されないため、デバイスへの影響はありません。

    > [!IMPORTANT]
    > Exchange Online と Exchange lokalen の両方で条件付きアクセスを使用する場合は、Service Connector Service を構成しないでください。

    これで、[Intune を使用して Exchange Online を展開する](conditional-access-intune-exchange-online.md)方法を学習する準備が整いました。

## <a name="-exchange-server-"></a>Exchange Server オンプレミスの の場合
Exchange lokalen への条件付きアクセスでは、次のデバイスをサポートします。

-   Windows 8 以降 (Intune に登録されている場合)

-   Windows Phone 8 以降

-   Exchange ActiveSync (EAS) 電子メール クライアントを使用する iOS デバイス

-   Android 4 以降

補足:

-   Exchange 2010 のバージョンは、Exchange 以降である必要があります。 Exchange Server クライアント アクセス サーバー (CAS) 構成がサポートされています。

    > [!TIP]
    > Exchange-環境が CAS サーバー構成の場合は、CAS サーバーのいずれかを指すようにオンプレミスの Exchange-Connectors を構成する必要があります。

-   Exchange ActiveSync: は、証明書ベースの認証またはユーザーの資格情報のエントリで構成できます。

-   Intune をオンプレミスの Microsoft Exchange Server に接続する**オンプレミスの Exchange Connector**を使用する必要があります。 これにより、Intune コンソールからデバイスを管理できるようになります (「[Exchange ActiveSync および Microsoft Intune を使用したモバイル デバイス管理](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)」を参照してください) 。

  > [!IMPORTANT]
> Exchange-Connectors 最新バージョンのオンプレミス を使用していることを確認します。 Intune コンソールで利用可能なオンプレミスの Exchange Connector は、Intune テナントに固有であり、他のテナントでは使用できません。 また、テナントの Exchange Connector は複数ではなく 1 台のコンピューターにのみインストールされるようにしてください。

  これで、[Intune を使用してオンプレミスの Exchange Server を展開する](conditional-access-intune-exchange.md)方法を学習する準備が整いました。

環境に Exchange Online と Exchange lokalen の両方が含まれている場合は、[Microsoft Intune と Konfigurations-Manager を使用した Exchange Online と Exchange lokal の展開](conditional-access-intune-configmgr-coexist.md)についてお読みください。
