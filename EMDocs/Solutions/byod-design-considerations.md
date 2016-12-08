---
title: "設計に関する考慮事項"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 639dfd46-33ea-4cfd-918d-f3d8e57645ed
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: d221333fb0b867ce96a3cb8343db935cc6e66230
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>設計に関する考慮事項

このドキュメントの「BYOD インフラストラクチャ ソリューションの構想」で詳細に説明されている要件を理解すると、BYOD インフラストラクチャ設計の要件を実装するための適切な製品とテクノロジを選択できます。 次の表は、BYOD インフラストラクチャ ソリューションの実装に使用できるマイクロソフトの製品、テクノロジ、サービスの一覧です。

このガイドで説明する BYOD インフラストラクチャ ソリューション向け Microsoft の製品、テクノロジ、サービスは次のとおりです。

## <a name=""></a>ユーザーとデバイス

- Windows Server 2012 R2
- Windows 10
- 社内参加
- デバイス登録サービス
- デバイスの登録
- Wi-Fi プロファイル
- [ポータル サイト]
- HTTPS-プロトコル

## <a name=""></a>データのアクセスと保護

- Windows Server 2012 R2
- Active Directory ドメイン サービス (AD DS)
- Azure Active Directory (AD Azure)
- Azure 多要素認証 (Azure mehrstufiger Authentifizierung DAS)
- Active Directory-Verbunddienste (AD FS)
- ダイナミック アクセス制御
- Verwaltung von Informationsrechten Microsoft サービス
- Azure-Rechteverwaltung 
- SMB 暗号化
- シングル サインオン (SSO
- 作業フォルダー
- Web アプリケーション プロキシ (WAP)

## <a name="management"></a>Verwaltung

- Microsoft Intune
- デバイス管理ポリシー
- 統合管理インフラストラクチャ
- 選択的なワイプ
- ソフトウェアの配布
- 配布ポイントの使用状況レポートと管理
- System Center 2012 R2 Configuration Manager

## <a name=""></a>アプリ

- Web アプリケーション プロキシ
- 自動 VPN-接続
- RemoteApp
- セッション シャドウ
- クイック再接続
- 重複除去記憶域
- Security Development Lifecycle (SDL)
- フェデレーション サービス für die Active Directory (AD FS)
- HTTPS-プロトコル

以下のセクションでは設計プロセスの概要を説明しますが、このドキュメントの「BYOD インフラストラクチャ ソリューションの構想」で示されているように、設計および要件定義のプロセスは完了するまで繰り返します。 ドキュメントの残りの部分では、設計に関する考慮事項および前の表に挙げられている製品、テクノロジ、サービスについて説明します。 マイクロソフトの複数の製品、テクノロジ、サービスを使用して設計に関する異なる考慮事項に対処するときは、それらの間のトレードオフについて説明します。

このインフラストラクチャは、BYOD が、この記事に示された質問に対する回答、および利用可能なテクノロジ機能とオプションをまとめることをサポートするよう設計されています。 このドキュメントで説明されている設計は、Microsoft ベースのテクノロジを使用します。 ただし、設計オプションと考慮事項は、BYOD モデルを採用するために使われる任意のインフラストラクチャに適用できます。


