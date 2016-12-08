---
title: "データの暗号化の要件を展開する"
description: "このトピックでは、モバイル デバイスでのデータの暗号化における設計上の考慮事項を説明します。 このトピックは、モバイル デバイス管理の設計上の考慮事項に関する一連の記事を構成するものです。"
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1072858e-dc0a-44ad-a512-d938f20310b6
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 224fadb6e679984e1ef39c85cacc6930c8775e27
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>データ暗号化

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

これで、保存中および転送中のデータの暗号化の要件に関するタスク 1 の質問への回答が終わりました。 次に、各要件に対応するために使用できるオプションを評価します。 データが保存中の場合も、次の図に示すように、さまざまな方法で暗号化できます。

![モバイル デバイスのディスク](./media/MDM_Figure_09.png)

## <a name=""></a>さまざまなレベルの暗号化

ディスク全体の暗号化を使用することも、アプリで処理されるデータに基づく暗号化を使用することもできます。             [Configuration Manager](https://technet.microsoft.com/library/dn919655.aspx)では、モバイル デバイスでファイルの暗号化を実行するポリシーを適用できます。 Windows Phone 8 のように自動的に暗号化されるモバイル デバイスもあれば、別のオプションが有効になっている場合にのみデータを暗号化するものもあります。 たとえば、IOS デバイスでは、デバイスでパスワードを要求するように設定を構成した場合にのみ、暗号化が自動的に実行されます。 

10 Windows Mobile では、BitLocker テクノロジに基づくデバイスの暗号化を使用して、オペレーティング システムとデータ ストレージ パーティションを含むすべての内部ストレージを暗号化します。 ユーザーがデバイスの暗号化をアクティブにすることも、IT 部門が MDM ツールを使用して暗号化をアクティブにし、会社で管理されているデバイスに適用することもできます。 デバイスの暗号化を有効にすると、そのモバイル デバイスに保存されているすべてのデータが自動的に暗号化されます。 暗号化を有効にした 10 Windows Mobile デバイスでは、デバイスの紛失または盗難時に、保存されているデータの機密性が保護されます。 詳細については、Windows 10 Mobile のセキュリティ ガイドを参照してください。

>[!TIP] 
> Configuration Manager を使用して暗号化を有効にできるモバイル デバイスの詳細については、「[Konfigurations-Manager でのモバイル デバイスの全般設定](https://technet.microsoft.com/library/dn376523.aspx)」を参照してください。

Intune モバイル アプリケーション管理ポリシーに関連付けられているアプリでは、暗号化は Microsoft によって提供されます。 データは、モバイル アプリケーション管理ポリシーの設定に従ってファイル E/A 操作中に同期的に暗号化されます。 Android デバイスでは、管理対象アプリは、FIPS 140-2 認定ではない、プラットフォーム暗号化ライブラリを利用して暗号ブロック チェーン (CBC) モードで AES-128 暗号化を使用します。 

このオプションを使用すると、SD カードなどの外部メディアに格納されているデータを含め、特定のアプリに関連付けられているすべてのデータが暗号化されるように指定できます。 同じ機能を[Office 365 の MDM](https://technet.microsoft.com/library/ms.o365.cc.devicepolicysupporteddevice.aspx)でも使用できます。 

OneDrive for Business などのパブリック クラウド ストレージ サービスは、Intune スタンドアロンや[System Center 2012 R2 Configuration Manager SP1](https://technet.microsoft.com/library/mt131422.aspx)とも統合できます。 OneDrive for Business アプリをユーザーのデバイスに展開することができ、ユーザーの OneDrive for Business アカウント内のすべてのドキュメントが暗号化されます。 

ほとんどの MDM ソリューションでは SSL を使用して転送中のデータを保護するため、ユーザーは既存の PKI を使用して証明書を発行するか、サーパーティ を使用するかを決定するだけで済みます。 ベンダーの証明機関 (CA) サード パーティの CA を使用する利点は、会社のリソースにアクセスするために自分のデバイスを使用するユーザーがよく知られているパブリック CA を自動的に信頼することです。 

## <a name="intune-"></a>Intune (スタンドアロン)

**長所** 

- Intune 管理ポリシーによって制御されるアプリに関連付けられているデータを暗号化

**短所** 

- モバイル デバイス ストレージのネイティブ暗号化は含まれない
- 現在のオンプレミス MDM プラットフォームと統合されない。 使用する管理インターフェイスの追加が必要

## <a name="office-365-mdm"></a>Office 365 の MDM

**長所**

- モバイル デバイス プラットフォームの機能に基づいてデータを暗号化

**短所**

- Configuration Manager 組織で現在オンプレミス インフラストラクチャが構成されていない場合、統合の前に、このプラットフォームの計画、インストール、構成が必要

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune 管理ポリシーによって制御されるアプリに関連付けられているデータを暗号化
- モバイル デバイス ストレージを暗号化
- 暗号化アルゴリズムの選択を含め、モバイル デバイスで暗号化できるものと暗号化の方法をより細かい制御が可能

**短所**

- Configuration Manager 組織で現在オンプレミス インフラストラクチャが構成されていない場合、統合の前に、このプラットフォームの計画、インストール、構成が必要

Intune と Configuration Manager の機能を組み合わせてデータ保護を強化し、暗号化を構成する方法の詳細については、「[Verwalten von Verschlüsselung auf mobilen Geräten mit Configuration Manager und Intune (Konfigurations-Manager と Intune を使用したモバイル デバイスでの暗号化の管理)](http://blogs.technet.com/b/pauljones/archive/2014/08/04/managing-encryption-on-mobile-devices-with-configuration-manager-and-intune.aspx)」を参照してください。
