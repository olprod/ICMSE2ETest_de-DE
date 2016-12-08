---
title: "証明書管理オプション"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3d350b5-4437-4f3d-907f-57ce6a819a74
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 80bd93b82f054eaa25d2166c610890644d1cc71f
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>証明書管理オプション

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

デジタル証明書管理と証明書プロファイルの使用は、[Intune](/Intune/deploy-use/secure-resource-access-with-certificate-profiles)スタンドアロンおよび[Intune と Configuration Manager のハイブリッド](https://technet.microsoft.com/library/dn261202.aspx)の両方の展開シナリオでサポートされています。 Registrierung von これらの機能を使うと、信頼されるルート証明書と、組織内の NDES サーバーから追加証明書を取得するようモバイル デバイスに指示する einfache Zertifikaten-Protokoll (SCEP) ベースのプロファイルを、モバイル デバイスに展開できます。

SCEP は、iOS、Windows 10 と 8.1、Windows Telefon 10 と 8.1 でネイティブにサポートされ、Android 用 Microsoft Intune ポータル サイト アプリでもサポートされているので、この登録プロトコルを使用すると、モバイル デバイスで秘密キーを直接生成できるというメリットがあります。 Configuration Manager と Intune はどちらも秘密キーを生成、キャッシュ、保存することはないため、モバイル デバイスのセキュリティを維持できます。

次の図は、Intune と Configuration Manager が NDES を使用して SCEP を使用するモバイル デバイスにセキュリティで保護された証明書のプロビジョニングを提供するしくみを示しています。

![セキュリティで保護された証明書のプロビジョニング](./media/MDM_Figure_07.png)

**セキュリティで保護された証明書のプロビジョニング**

1. Intune サービスで、SCEP 登録用の証明書のプロパティを含むポリシーが作成されます。
2. Intune は、ポリシーをプラットフォームのモバイル デバイス管理プロトコル (Windows 10 および Windows 8.1 の OMA DM など) に変換してデバイスに送信します。
3. モバイル デバイスは、ポリシーを受け取り、NDES からの登録要求を開始します
4. NDES は要求を Configuration Manager に転送します。
5. Configuration Manager は SCEP 要求の要求属性を比較して認証と照合し、NDES に確認を返送します。
6. NDES は証明書発行要求を ZERTIFIZIERUNGSSTELLE に送信し、CA は証明書を NDES の役割に送信します。
7. NDES の役割は、デバイスに証明書を送信します。

作業 3 の確認事項の結果によっては、モバイル デバイス管理ソリューションでの証明書の管理方法を決定できます。 現在、MDM für Office 365 はモバイル デバイスの証明書プロファイルの管理をサポートしていません。 

次の表は、Intune および Intune と Configuration Manager のハイブリッドの展開シナリオでの証明書プロファイル管理の長所と短所を理解するうえで役立ちます。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- すべての主要なモバイル デバイス オペレーティング システム (Android、iOS、Windows 10、Windows 8.x、Windows Telefon) で証明書プロファイルをサポート
- Registrierung von プラットフォームは Simple Zertifikaten Protokoll (SCEP) をサポート
- 証明書プロファイルは、証明書を手動でインストールしたり承認されていないセキュリティ プロセスを使用したりしなくても、会社のリソースにアクセスできるように、モバイル デバイスを自動的に構成が可能
- デバイスが管理対象外になったとき、選択的に消去されたとき、または管理階層からブロックされたときは、証明書を自動的に失効が可能

**短所**

- 証明書プロファイルを使用するには、何らかの既存のオンプレミス インフラストラクチャが必要 次のオンプレミス インフラストラクチャと Intune の統合が必要:
 - ネットワーク デバイス登録サービスを実行するサーバー
 - エンタープライズ証明機関
 - NDES を実行しているサーバーにインストールされる Intune NDES コネクタ

## <a name="mdm-for-office-365"></a>MDM für Office 365

- MDM für Office 365 で証明書プロファイルはサポートされていない

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune スタンドアロンのすべての長所に加え、次の長所がある。
 - 非モバイル デバイスの証明書の管理をサポート

**短所**

- 証明書プロファイルを使用するには、何らかの既存のオンプレミス インフラストラクチャが必要 
- 次のオンプレミス インフラストラクチャと Intune の統合が必要:
 - ネットワーク デバイス登録サービスを実行するサーバー
 - エンタープライズ証明機関
 - NDES を実行しているサーバーにインストールされる Intune NDES コネクタ

モバイル デバイス証明書管理オプションの詳細については、Intune で[証明書プロファイルを有効にする](/Intune/deploy-use/secure-resource-access-with-certificate-profiles)方法を読み、その要件と手順を System Center 2012 R2 Configuration Manager での[証明書プロファイルの有効化](https://technet.microsoft.com/library/dn261202.aspx)と比較してください。
