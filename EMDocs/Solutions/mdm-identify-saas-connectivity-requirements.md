---
title: "SaaS の接続要件の特定"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6afbce4c-7500-4387-a19c-dff52c152097
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: b02f3f667d930f25f74443790f07fb7c53ed87fc
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="saas-"></a>SaaS の接続要件の特定

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

オンプレミス インフラストラクチャを接続する方法は、すべての MDM ソリューション (365 Intune、Office の MDM、Intune と Configuration Manager のハイブリッド展開) でユーザーとデバイスの-ID を管理する方法に影響します。 Intune と Office 365 の MDM では、Azure Active Directory サービスによって提供されるディレクトリ サービス アーキテクチャを利用します。 Azure とのこの統合により、モバイル デバイス管理ソリューションで ID 管理のサポートを設計するときの柔軟性が大幅に向上します。

次の図に示すように、オンプレミス ディレクトリ サービスと Azure の接続は、シングル サインオンとディレクトリ アカウントの一元管理を実現する上で重要な要件です。 シングル サインオンによって、オンプレミスとクラウドにある会社のリソースにユーザーが簡単に接続できるようになります。 アカウントを管理する 1 つの場所ができるので、管理者の作業も簡単になります。 モバイル アクセスの場合、Azure とオンプレミス ディレクトリ サービス間でディレクトリ アカウント属性と資格情報を同期することで、ユーザーは Office 365 の MDM または Intune で管理されるリソースにアクセスするためにモバイル デバイスで認証することができます。

![統合された ID 管理の概要](./media/MDM_Figure_15.png)

**統合された ID 管理の概要**

2 タスク のチェック項目の結果に応じて、モバイル デバイス管理ソリューションのために必要な、SaaS ソリューションとオンプレミス クライアント管理プラットフォームを接続する方法を判断できます。 次の表は、オンプレミス インフラストラクチャを SaaS ソリューションと接続する長所と短所を理解するのに役立ちます。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- ユーザーとデバイスの ID と認証を管理するために、Azure Active Directory と緊密に統合されている
- 既存のオンプレミス アカウントの資格情報を利用できるユーザー資格情報の自己管理とシングル サインオン エクスペリエンスをサポートしている
- 数千個の統合済み SaaS アプリケーションへのシングル サインオン アクセスをサポートしている
- オンプレミス アプリケーションとクラウド アプリケーションの両方に対して、ルールベースの多要素認証 (MEHRSTUFIGER AUTHENTIFIZIERUNG DAS) を適用することで、アプリケーションのアクセス セキュリティをサポートしている

**短所**

- 高度なディレクトリ サービス接続の機能を Azure Active Directory Premium と組み合わせる必要がある

## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- ユーザーとデバイスの ID と認証の管理に Azure Active Directory のバックボーンを使用する Office 365 テナントと統合されている
- サービスと Office 365 の接続の一環として、オンプレミス ディレクトリ サービスを接続できる
- 既存のオンプレミス アカウントの資格情報を利用できるユーザーの自己管理とシングル サインオン エクスペリエンスをサポートしている
- Azure mehrstufiger Authentifizierung DAS サービスを使用してデバイス登録で多要素認証をサポートする

**短所**

- モバイル アプリケーション管理と他の SaaS ソリューションまたはアプリケーションとの統合をサポートしていない

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune スタンドアロンのすべての長所に加え、次の長所がある。
 - Configuration Manager インフラストラクチャを使用した、オンプレミス ディレクトリ サービスとの直接統合

**短所**

- 現在 Configuration Manager インフラストラクチャが構成されていない組織の場合、Intune と統合する前に、ConfigMgr インフラストラクチャの計画、インストール、構成が必要
- Configuration Manager を使用する組織の場合、追加のオンプレミス展開要件と構成の変更が必要
