---
title: "データ分類"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f3486381-66d5-469a-93a3-013eaaa17c07
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 1986dfd573a7141b770efafa66ee22851d2a4f9d
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>データ分類

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

ほとんどの会社が[データ分類](http://blogs.microsoft.com/cybertrust/2014/01/28/the-importance-of-data-classification/)ポリシーを既に定めているので、モバイル デバイス管理ソリューションの展開がこのポリシーに及ぼす影響を理解する必要があります。 会社に現在のデータ分類ポリシーがない場合は、モバイル デバイス管理ソリューションを計画すると共に、この機能を導入する必要があります。 一部の組織では、[Active Directory-Rechteverwaltungsdienste (ADRMS)](https://technet.microsoft.com/windowsserver/dd448611.aspx)を使用して、ファイル サーバー レベルでオンプレミスのデータ分類を実行しています。 また、ファイル サーバー上のデータを識別、分類、および保護することができる[Microsoft Data Klassifizierung Toolkit](http://www.microsoft.com/download/details.aspx?id=27123)という別のツールを使用している会社もあります。 

Office 365 は、保護する必要がある機密情報を表出させるおそれのある電子メールの自動データ分類を提供します。 Office 365 では、メール フロー処理に組み込まれているトランスポート ルールを使用して、機密情報を検出します。 次に、[DLP 機能](http://blogs.office.com/2013/10/28/office-365-compliance-controls-data-loss-prevention/)によって、キーワード照合、ディクショナリ照合、正規式の評価、クレジット カード番号のチェックサム検証などの内部機能、およびその他のコンテンツ調査による詳細なコンテンツ分析が実行され、メッセージ本文や添付ファイル内の特定のコンテンツ タイプが検出されます。 

Intune と Configuration Manager にはデータ分類が組み込まれていないため、Azure RMS を使用したクラウドベースの分類または ADRMS を使用したオンプレミスの分類を利用します。             [Enterprise Mobilität Suite (zur Abstimmung)](http://www.microsoft.com/server-cloud/enterprise-mobility/overview.aspx)を MDM ソリューションとして使用することもできます。 Zur Abstimmung を使用すると、データの分類に使用できる、[Azure AD Premium](https://msdn.microsoft.com/library/azure/dn532272.aspx)と[Azure RMS](https://technet.microsoft.com/library/jj585026.aspx)にアクセスできます。 ハイブリッド環境では、Azure RMS を使用したデータ分類をオンプレミス管理ソリューションと統合できます。 

Intune を使用すると、IT 部門はコンプライアンス ポリシーを使用してポリシーを遵守できます。 コンプライアンス ポリシーは、デバイスが条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある一連のルールと設定です。 コンプライアンス ポリシーは、条件付きアクセスとは別に、デバイスの準拠の問題を監視したり修復したりするために使用することもできます。 詳細については、「[Microsoft Intune のデバイス コンプライアンス ポリシーの管理](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)」を参照してください。

次の表は、組織の*データ分類*要件に最適な MDM オプションを選択するうえで役立ちます。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- 利用不可

**短所**

- 利用不可

## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- Exchange トランスポート ルールを使用して、機密情報を検出できる
- コンプライアンス センターの[データ損失防止 (DLP)](https://technet.microsoft.com/library/ms.o365.cc.DLPLandingPage.aspx)ポリシーを活用して、さまざまな場所で機密情報を特定する

**短所**

- ファイル自体ではデータ分類は実行されない ファイルがモバイル デバイスに配置されたら、制限なく使用可能

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- 利用不可

**短所**

- 利用不可

## <a name="-"></a>エンタープライズ モビリティ スイート

**長所**

- Azure RMS を活用してデータ分類を実行する
- Azure RMS サブスクリプションは zur Abstimmung に含まれる
- データの分類にオンプレミス インフラストラクチャは不要
- 既存のオンプレミス AD RMS ソリューションと統合できる
- ファイル自体で保護が実行されるため、ファイルを別の場所に保存した場合でも、ファイルの分類を維持

**短所**

- クラウドベースのソリューションを採用していない顧客は使用できない
