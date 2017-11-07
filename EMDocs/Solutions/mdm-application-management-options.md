---
title: "アプリケーション管理オプション"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f77eba2-8e27-4e08-b2f2-e71e3d776cf4
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: b9f65c73de627916837817cbceba675720a87432
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>アプリケーション管理オプション

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

モバイル アプリケーション管理 (MAM) ポリシーは、モバイル デバイス上のコンシューマー アプリまたはサービスへの企業データの漏洩を防ぎます。 通常、これらのポリシーは、モバイル デバイス管理ソリューションに登録されているデバイスでのみ適用されます。 Intune の MAM 機能は、他のモバイル デバイス管理ソリューションで管理されているデバイスのほか、どのデバイス管理システムにも登録されていないデバイスも対象とするように拡張されました。

次の図に示すように、MDM ソリューションが既に準備できている場合は、Office アプリケーションと Office 365 のデータの管理と保護に Intune MAM を利用できます。 その際、共存または移行のシナリオで従業員のデバイスの登録を解除し、Intune MDM で再登録する必要はありません。

![Intune MAM ポリシーを使用したモバイル デバイスのアプリケーション管理の分離の概要](./media/Intune_without_enrollment.png)

**Intune MAM ポリシーを使用したモバイル デバイスのアプリケーション管理の分離の概要**

Intune MAM 機能は、MDM ソリューション全体に代わるものではありません。 MDM プロトコルは、VPN、Wi Fi、証明書の管理、アプリケーションの配置、およびデバイス レベルのセキュリティ設定の構成など、包括的なデバイス管理シナリオに必要です。

Configuration Manager と Intune によるハイブリッド展開については、モバイル アプリ管理ポリシーを使用して、Intune で管理されていないデバイス上のアプリを保護できます。 この新機能を使用して、Office 365 サービスに接続するアプリに対してモバイル アプリ管理ポリシーを適用できます。 これは、オンプレミスの Exchange や SharePoint に接続するアプリではサポートされていません。 この機能を使用するには、Azure プレビュー ポータルを使用する必要があります。

手順 1 の確認事項の結果によっては、モバイル デバイス管理ソリューションでのアプリケーションの管理方法を決定できます。 次の一覧は、各アプリ管理オプションの長所と短所を示しています。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- Intune に登録されているデバイス、他の管理ソリューションに登録されているデバイス、またはどの管理ソリューションにも登録されていないデバイスで、アプリケーション管理をサポート
- Intune 対応アプリ内で企業データをコンシューマー データから分離。 Intune 対応アプリには、Office Mobile アプリ、Intune SDK を採用しているサードパーティ製アプリ、Intune によってラップされた基幹業務アプリなどがあります
- 切り取り/コピー/貼り付け機能を使って会社のデータを会社のアプリ間で共有しながら、個人のアプリでの共有を防止
- アプリ単位の PIN、別名保存の制御、アプリ間での管理対象データの共有など、主要なデータ損失防止ポリシー
- Microsoft Word、Excel、PowerPoint、Outlook、OneNote、および OneDrive for Business でこれらの機能をサポート
- Apple Volume Purchase Program für Business ボリューム購入プログラムで購入された iOS アプリの管理
- Android デバイスおよび iOS デバイスでのサポート

**短所**

- Windows Phone デバイスではサポートされていない

## <a name="mdm-for-office-365"></a>MDM für Office 365

- 現在のところ、サポートされていません

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune スタンドアロンのすべての長所

**短所**

- Intune をオンプレミスの Configuration Manager インフラストラクチャと接続するには追加の構成が必要
- 現在 Configuration Manager インフラストラクチャが構成されていない組織の場合、Intune と統合する前に、ConfigMgr インフラストラクチャの計画、インストール、構成が必要

モバイル アプリケーション管理のオプションの詳細については、「Configure und Bereitstellen von Informationsverwaltungsrichtlinien in der Microsoft Intune-Konsole (Microsoft Intune コンソールでモバイル アプリケーション管理ポリシーを構成および展開する) 」で mobilen Anwendung Intune と Configuration Manager に関する説明を参照してください。 また、Intune MAM ポリシーで使用できる Microsoft アプリの一覧と、Intune 対応パートナー アプリの一覧も確認してください。
