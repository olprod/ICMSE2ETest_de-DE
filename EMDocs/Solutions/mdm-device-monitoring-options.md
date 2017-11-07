---
title: "デバイス監視オプション"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 23cfc12a-fa96-4fb3-8de1-af4569e8cb71
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: b3b84b77efde354d9b622ae42aa08865943622a1
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>デバイス監視オプション

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

組織によって管理されるすべてのモバイル デバイスの状態と構成を監視して把握することは、問題や非コンプライアンスの検出、およびデバイスのインベントリの管理に役立ちます。 ハードウェア、ソフトウェア、およびコンプライアンスの状態の詳細なレポートがないと、デバイスのポリシーが実際に適用されていて正常に動作しているかどうかを確認できません。 プロアクティブな監視により、小さな問題が大きくてコストのかかるものになるのを防ぐことができます。


            [Intune](/Intune/deploy-use/monitoring-and-reports-with-microsoft-intune)、[Office 365 の MDM](https://technet.microsoft.com/library/faa7d8e5-645d-4d59-839c-c8d4c1869e4a(v=technet.10).aspx)、Intune と ConfigMgr の[ハイブリッド展開](https://technet.microsoft.com/library/gg699377.aspx)には、いずれも組織のポリシーと手順を使用したデバイス、ユーザー、コンプライアンスの管理に役立つ監視およびレポート作成機能があります。 組み込みのレポートとカスタマイズされたレポートを使用して、次のような領域のモバイル デバイス管理を監視できます。

- ソフトウェアの更新レポート
- ソフトウェア インベントリ レポート
- ハードウェア インベントリ レポート
- ライセンス レポート
- 非コンプライアンス レポート

インフラストラクチャのセットアップ方法により、組織の監視に役立つさまざまなレポートを作成できます。 Intune ベースの監視およびレポート作成機能は、Office 365 の MDM と Intune スタンドアロン展開のレポートの基になっています。 ハイブリッド展開で Intune に接続すると、これらのレポートを Configuration Manager のレポート作成機能と緊密に統合することもできます。 以下に示すように、各製品には異なりますが補完的なレポート機能があります。 必要なレポートが含まれるソリューションを選択するには、各モバイル デバイス管理ソリューションのレポート機能の微妙な差異を調べることが重要です。

![統合されたモバイル デバイスの監視とレポート作成](./media/MDM_Figure_05.png)

**統合されたモバイル デバイスの監視とレポート作成**

作業 2 の確認事項は、モバイル デバイスの監視とレポートの要件の決定に役立ちます。 次の表では、各 MDM ソリューションでの監視およびレポート作成機能の長所と短所を示します。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- 監視の概要/ダッシュボード
- 直接管理されているネットワーク デバイスでエラーが検出されるとアラートが発生
- Intune サービスの RSS-フィードから、サービスと今後のメンテナンスに関する問題を通知することが可能
- 3 しきい値に関する レベルのアラート (重大、警告、情報) と電子メール アラート通知
- デバイスの種類でアラートをフィルター処理
- すべての管理対象デバイスの状態を確認
- IT-ポリシーを満たしていないデバイスに関するレポートを提供
- 次の領域の詳細を監視
 - システム
 - BETRIEBSSYSTEM
 - 記憶域
 - Exchange ActiveSync
 - システム格納装置
 - Netzwerk (ネットワーク)
 - サービス

**短所**

- 電子メールのアラートのみであり、テキスト ベースまたは音声のアラートはない

## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- 監視の概要/ダッシュボード
- しきい値に関する 3 レベルのアラート (重大、警告、情報) と電子メール アラート通知
- デバイスの種類でアラートをフィルター処理
- すべての管理対象デバイスの状態を確認
- IT-ポリシーを満たしていないデバイスに関するレポートを提供

**短所**

- モバイル デバイスのコンプライアンス状態レポートのみ

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune スタンドアロンのすべての監視およびレポート作成機能に加え、次の長所がある。
 - 非モバイル デバイスや Intune に登録されていないデバイスも含め、組織のすべてのデバイスの包括的なしきい値ベースの統合された監視とレポート作成
 - SQLServer Reporting Services (SSRS) の高度なレポート機能と、Reporting Services レポート ビルダーによる充実したオーサリング エクスペリエンス

**短所**

- Intune をオンプレミスの Configuration Manager インフラストラクチャと接続するには追加の構成が必要
- 現在 Configuration Manager インフラストラクチャが構成されていない組織の場合、Intune と統合する前に、ConfigMgr インフラストラクチャの計画、インストール、構成が必要

モバイル デバイス監視オプションの詳細は以下を参照してください。

- Intune:**[モバイル デバイスを監視する方法](https://technet.microsoft.com/library/jj733634.aspx)**と[レポートを管理する方法](/Intune/deploy-use/monitoring-and-reports-with-microsoft-intune)
- Configuration Manager:[モバイル デバイスの監視](https://technet.microsoft.com/library/gg682128.aspx)と[レポートの管理](https://technet.microsoft.com/library/gg699377.aspx)
- Office 365 の MDM:[概要とデバイス管理タスク](https://technet.microsoft.com/en-us/library/ms.o365.cc.devicepolicy.aspx)
