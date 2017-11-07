---
title: "電子メール管理オプション"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b89da63-039f-4831-b204-28c0681478fe
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 904c808fb5efb90929be2ee7b73338853395510d
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>電子メール管理オプション

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

モバイル デバイス管理ソリューションを実装する主な理由は、モバイル デバイスから会社の電子メールへの管理されたアクセスを提供することです。 たとえば、Office 365 の MDM では、Exchange Online でホストされている電子メール メールボックスへの基本的な管理アクセス、または Office アプリ (iOS および Android 上) からのアクセスを提供する[セキュリティ ポリシー](https://technet.microsoft.com/library/ms.o365.cc.newdevicepolicy.aspx)を作成できます。 このポリシーは、ユーザーのメールボックスへの接続をデバイスに許可する前に、デバイスのパスワードやデバイスの暗号化を要求するなど、基本的なモバイル デバイスのコンプライアンス設定を適用します。

Intune、および Intune と Configuration Manager のハイブリッド展開でも、同様のプロセスに従って電子メール管理オプションを構成します。 主な違いは、Office 365 の MDM で実装できるものよりも高度な電子メール管理オプションを実装できることです。 たとえば、Intune スタンドアロンを使用すると、Exchange Online と Exchange lokale の両方でホストされているメールボックスへのアクセスを許可するように条件付き電子メール アクセスを構成したり、カスタマイズされた電子メール プロファイルを構成したりできます。 Intune では、構成ポリシーとコンプライアンス ポリシーを使用してこれらの機能を有効にします。  Intune と Configuration Manager のハイブリッド展開も条件付き電子メール アクセスをサポートしていますが、Exchange Online でホストされているメールボックスの場合だけです。

次の図 6 に示すシナリオでは、ユーザーは Intune にデバイスを登録していますが、Office 365 または Exchange lokalen を使用して会社の電子メールにアクセスしようとしています。 IT-管理者によって定義された設定に基づいて、Intune はポリシー検証プロセスを実行します。 このシナリオでは、デバイスが暗号化されていて、パスコードが設定されていて、デバイスが脱獄またはルート化されていない場合、ユーザーのアクセスが許可されます。 会社の電子メールにアクセスしようとしたユーザーのデバイスが登録されていない場合、または IT 管理者によって定義された設定に準拠していない場合、ユーザーは、アクセスがブロックされた理由と問題解決手順が説明された電子メールを受け取ります。 

![条件付きアクセス](./media/MDM_Figure_06.png)

**条件付きアクセス**

モバイル デバイス管理ソリューションでデバイスを管理する方法を決定するときには、手順 1 での確認事項が役立ちます。 次の表では、各 MDM ソリューションでの電子メール管理の長所と短所を示します。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- すべての主要なモバイル デバイス オペレーティング システム (Android、iOS、Windows 10、Windows 8.x、Windows Telefon) の電子メール管理をサポート
- Exchange ActiveSync との統合により、ネイティブなモバイル デバイス電子メール アプリケーションを利用可能
- Um den Dienst Connector による Exchange Online との統合により、Intune と Office 365 間でのクロス プラットフォームの監視とレポート作成が可能
- モバイル デバイスで Exchange ActiveSync ベースの設定を管理するための電子メール プロファイルの構成をサポート
- リソースへの条件付き電子メール アクセス

**短所**

- Android ベースのモバイル デバイスに対する電子メール プロファイルはサポート対象外

## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- Exchange ActiveSync: によるパスワード、暗号化、ルート化されたデバイスのコンプライアンスのサポートが可能
- デバイス管理ポリシーおよび Office と OneDrive for Business アプリ (iOS および Android) へのアクセスを許可する前のデバイス登録要求を使用可能
- リソースへの条件付き電子メール アクセス

**短所**

- 一部の高度な電子メール管理オプションはサポート対象外 
- 電子メール プロファイルの展開はサポート対象外 (iOS を除く)

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune On-Premises Connector を Exchange Online とのハイブリッド接続に使用
- Exchange ActiveSync: との統合 (最も厳しいポリシー設定を適用)
- 電子メール プロファイル
- Exchange Online への電子メール アクセスを制限する条件付きアクセス
- サービスへのアクセスが許可されるためにデバイスが従う必要がある規則と設定を定義するためのコンプライアンス ポリシー
- セキュリティ グループ、Intune グループ、または未登録デバイスの管理方法のルールを定義する、デバイスごとの条件付きアクセス ポリシー

**短所**

- 電子メールへの管理されたアクセスは、Exchange Online でホストされているメールボックスにのみ使用可能であり、Exchange lokalen でホストされているメールボックスには使用できない
- Exchange Online と Exchange auf Prmises の両方に対して条件付きアクセスを有効にする場合は、Service Dienst Connector を構成することはできない

モバイル デバイスの電子メール構成管理オプションの詳細は以下を参照してください。

- Intune:[電子メール プロファイルを有効にする](/Intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)方法と[条件付き電子メール アクセスを有効にする](/Intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)方法
- Configuration Manager:[電子メール プロファイル](https://technet.microsoft.com/library/dn554227.aspx)と[条件付き電子メール アクセス](https://technet.microsoft.com/library/dn919655.aspx)の有効化
- Office 365 の MDM:[モバイル デバイス管理の機能](https://technet.microsoft.com/library/ms.o365.cc.devicepolicysupporteddevice.aspx)
