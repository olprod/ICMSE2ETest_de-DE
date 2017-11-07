---
title: "SaaS モバイル デバイス管理戦略の作成"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b3cefcc5-b045-48f9-91f5-6d282a4428f3
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 37c2e005f37757d95950b3321549a5b027cf387a
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="saas-"></a>SaaS モバイル デバイス管理戦略の作成

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

## <a name="saas-"></a>SaaS ソリューションの要件を特定する

タスク 1 のチェック項目の結果に応じて、SaaS ソリューションがモバイル デバイス管理ソリューションでサポートする必要があることを判断できます。 20 次の表 は、各 SaaS ソリューション シナリオの長所と短所の比較です。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- マルチテナントのパブリック クラウド アーキテクチャとして提供
- 50.000 最大 台のモバイル デバイスをサポート
- オンプレミス インフラストラクチャ、ハードウェア、またはソフトウェアに追加の投資は不要
- 更新と機能の改善は日単位。 主要な特性と機能の強化は月単位。
- 特定の地域にあるデータセンターにサービスの割り当てが可能
- 特定の地域にデータセンターのフェールオーバーの制限が可能
- ほとんどの業界および政府機関の標準に準拠した認定サービス レベル アグリーメント (SLA) に金銭的な裏付けがあり、サービスまたは機能を利用できない場合に月額料金が無料になる

**短所**

- プライベート クラウド インスタンスがサポート対象外
- 50.000 Configuration Manager 台を超えるモバイル デバイスをサポートする必要がある場合、Intune を に接続して追加のデバイスを管理する必要がある

## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- の単一の管理コンソールを提供 für Office 365 の商用テナントと緊密に統合されており、モバイル デバイスと Office 365 テナント サービス (Exchange Online、SharePoint Online、Skype für Unternehmen Online)
- Office 365 のマルチテナント (パブリック) プラットフォームまたはプライベート (専用) プラットフォームで提供
- Office 365 の商用プラン (Business、Enterprise、Education、Government) に既定で含まれているので、ユーザーまたはデバイスの追加のライセンス コストが不要

**短所**

- モバイル以外のオペレーティング システムの管理をサポートしていない
- モバイル以外のデバイスにオンプレミス管理プラットフォームを使用する場合、モバイル デバイス (のみ) をプロビジョニングする追加の管理インターフェイスが必要。

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune スタンドアロンのすべての長所に加え、次の長所がある。 Intune (クラウドベースのデバイス管理サービス) と Configuration Manager (オンプレミスのデバイス管理プラットフォーム) のネイティブな統合
- Intune 接続を介したモバイル デバイスの高度なデバイス プロビジョニング オプションをサポート
- Intune サービスの新しい機能が、プラットフォーム拡張機能によって自動的またはカスタマイズされた方法でオンプレミス Configuration Manager にも適用される

**短所**

- Intune をオンプレミス Configuration Manager インフラストラクチャと接続するために追加の構成要件が必要
- 現在 Configuration Manager インフラストラクチャが構成されていない組織の場合、Intune と統合する前に、ConfigMgr インフラストラクチャの計画、インストール、構成が必要

プラットフォームごとの選択的ワイプの後、デバイスから削除されるデータと、デバイスに保持されるデータに対する影響については、「**[Microsoft Intune によるリモート ワイプ、リモート ロック、パスコードのリセットを使用したデータの保護](https://technet.microsoft.com/library/jj676679.aspx)**」を参照してください。 ハイブリッド環境を使用している場合、ConfigMgr を使用してこのタスクを実行する方法については、「[-Konfigurations-Manager によるリモート ワイプ、リモート ロック、パスコードのリセットを使用したデータの保護](https://technet.microsoft.com/library/dn956981.aspx)」を参照してください。

SaaS ソリューションの機能と要件の詳細については、「**[Microsoft Intune サービスの説明](https://technet.microsoft.com/library/dn600286.aspx)**」を参照し、[Office 365 の MDM](https://technet.microsoft.com/library/faa7d8e5-645d-4d59-839c-c8d4c1869e4a(v=technet.10).aspx)と、Intune/Configuration Manager[ハイブリッド](https://technet.microsoft.com/library/jj884158.aspx)インフラストラクチャの SaaS サポートの違いを理解してください。
