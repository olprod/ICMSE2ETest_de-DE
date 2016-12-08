---
title: "デバイスのプロビジョニング オプション"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 991cd722-089c-4e8c-80b9-b82e405cc891
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: a93cc53cb99ba51b42da60750df716b6724523a0
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>デバイスのプロビジョニング オプション

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

ユーザーが個人所有のデバイスを使用および登録できると、IT とユーザーの両方に対する要件が増え、複数の領域に影響があります。 たとえば、次の図は、Intune と Configuration Manager の両方を使用する組織の登録プロセスの概要を示しています。 この例では、ソリューションを計画するときに考慮する必要がある証明書、Web アプリケーション、および同期に関する考慮事項について説明します。

![Intune と Configuration Manager のハイブリッドを使用するモバイル デバイスの登録プロセスの概要](./media/MDM_Figure_04.png)

**Intune と Configuration Manager のハイブリッドを使用するモバイル デバイスの登録プロセスの概要**

1. 
            <token>Windows Server 2012 R2 では、デバイス登録と呼ばれる新しい概念が導入されました。  ユーザーはシングル サインオン用に自分のデバイスを登録し、社内参加を使用して企業データにアクセスできます。  この登録プロセスの一環として、証明書がデバイスにインストールされます。 デバイスを登録してデバイス管理ソリューションに認識させると、ユーザーは、以前はドメイン参加 PC の外部では利用できなかった企業のリソースにアクセスできるようになります。
2. ユーザーがデバイスを登録すると、[ポータル サイトを使用](/Intune/deploy-use/enroll-devices-in-microsoft-intune)して Intune で管理できるようにデバイスが構成されます。 ユーザーは、Microsoft Intune ポータル サイトを利用して、会社のアプリケーションやデータに簡単にアクセスしたり、各自のデバイスを管理したりできます。 また、デバイスの紛失、盗難、または交換時に、リモート ワイプなどのタスクを実行することもできます。
3. デバイスの認識 (つまり登録されていること) とユーザー ID に基づいて、[Web アプリケーション プロキシ](https://technet.microsoft.com/library/dn584107.aspx)と呼ばれる Windows Server 2012 R2 の組み込み機能を使用して企業リソースへのアクセスを公開できます。 Enterprise-Mobilität Suite を使用している場合は、Azure AD アプリケーション プロキシを使用してアプリケーションを公開することもできます。          [Azure Active Authentifizierung](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/)により、多要素認証を使用できます。
4. 環境全体の統一されたビューを管理者に提供するために、Intune のデータは Configuration Manager と同期され、オンプレミスとクラウドの両方での統一された管理が実現されます。
5. 登録プロセスの一環として、Active Verzeichnis に新しいデバイス オブジェクトが作成されます。  このデバイス オブジェクトは、ユーザーとデバイスの間のリンクを確立し、それをデバイス管理ソリューションに認識させて、デバイスを認証できるようにします。 これは実質的にシームレスな 2 要素認証です。

手順 1 の確認事項の結果によっては、モバイル デバイス管理ソリューションでのデバイスの管理方法を決定することができます。 次の表では、各プロビジョニング オプションの長所と短所を示します。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- すべての主要なモバイル デバイス オペレーティング システム (Android、iOS、Windows 10、Windows 8.x、Windows Telefon) の登録とプロビジョニングをサポート
- クラウド ベース サービスであり、インターネットにアクセスすることでどこからでもモバイル デバイスの登録が可能
- 集中管理されたカスタマイズ可能な会社のポータルを使用してデバイスの登録が可能
- モバイル デバイスの高度なデバイス プロビジョニング オプション

**短所**

- モバイル以外のデバイスにオンプレミス管理プラットフォームを使用する場合、モバイル デバイス (のみ) をプロビジョニングする追加の管理インターフェイスが必要
- クラウド ベースのサービスとオンプレミスの管理プラットフォームに、別のデバイス コンプライアンスおよびセキュリティ ポリシーが必要 

## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- Office 365 テナントと統合されており、モバイル デバイスと Office 365 テナント サービス (Exchange Online、SharePoint Online、Skype für Unternehmen) の単一の管理コンソールを提供
- すべての主要なモバイル デバイス オペレーティング システム (Android、iOS、Windows 10、Windows 8.1、Windows Telefon) の登録とプロビジョニングをサポート
- モバイル デバイスの基本的なデバイス プロビジョニング オプションです

**短所**

- モバイル以外のデバイスにオンプレミス管理プラットフォームを使用する場合、モバイル デバイス (のみ) をプロビジョニングする追加の管理インターフェイスが必要
- クラウド ベースのサービスとオンプレミスの管理プラットフォームに、別のデバイス コンプライアンスおよびセキュリティ ポリシーが必要
- 高度ではないデバイス プロビジョニング オプションです

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune (クラウドベースのデバイス管理サービス) と System Center 2012 Configuration Manager および System Center 2012 R2 Configuration Manager (オンプレミスのデバイス管理プラットフォーム) のネイティブな統合
- すべての主要なモバイル デバイス オペレーティング システム (Android、iOS、Windows Telefon) の登録とプロビジョニングをサポートし、すべての主要な非モバイル デバイス オペレーティング システムのプロビジョニングを含みます
- Intune 接続を介したモバイル デバイスの高度なデバイス プロビジョニング オプションをサポート

**短所**

- 現在 Configuration Manager インフラストラクチャが構成されていない組織の場合、Intune と統合する前に、ConfigMgr インフラストラクチャの計画、インストール、構成が必要
- Intune をオンプレミスの Configuration Manager インフラストラクチャと接続するには追加の構成が必要

モバイル デバイスの登録とプロビジョニングのオプションの詳細については、Intune で[モバイル デバイスの登録を有効にする](/Intune/deploy-use/enroll-devices-in-microsoft-intune)方法を確認し、その要件と手順を、ConfigMgr および Office 365 の MDM で[モバイル デバイスの登録を有効にする](https://technet.microsoft.com/library/jj884158.aspx)場合と比較してください。
