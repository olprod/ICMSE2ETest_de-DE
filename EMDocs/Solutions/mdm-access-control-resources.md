---
title: "リソースへのアクセス制御"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5967876b-3c08-4498-a0a6-0225b562d35f
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: ae56b300828631b85188982b80fa3fbf224b6a56
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>リソースへのアクセス制御

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

既に Active Directory を使用してユーザーの認証と承認を行っている組織では、Active Directory のグループを使用してリソースへのアクセスをセグメント化し、制御することで、特定のリソースへのアクセス制御が既に管理されています。  

特定のリソースへの制御を管理するには、まず、ユーザーのアクセスを認証および承認してから、ターゲット リソースでのユーザーの制御の種類を確認します。 次の図に、Bob というユーザーがフォルダーにアクセスする場合の例を示します。

![認証フロー](./media/MDM_Figure_13.png)

## <a name=""></a>基本認証と承認のフロー

従来のアクセス制御リスト (ACL) は非常に限定的であるため、Bob がこのリソースにアクセスしようとしたときにどこにいたかなど、ユーザーの状態の他の側面は考慮されません。 組織でリソースへのアクセスを許可する前にさらに変数が必要な場合は、Windows Server 2012 でネイティブに使用可能な[ダイナミック アクセス制御](https://technet.microsoft.com/library/dn408191.aspx)を使用できます。 Windows 10 では、正常性構成証明書がサポートされます。 これにより、データへのアクセスを提供する前に、IT 担当者がデバイスの正常性状態を制御できます。 リモートの正常性認証サービスは測定値の一連のチェックを行い、 ブート状態 (セキュア ブート、デバッグ モードなど) やセキュリティを管理するコンポーネント (BitLocker、Device schützen など) の状態を含め、セキュリティ関連のデータ ポイントを検証します。 続いて、デバイスに正常性暗号化 BLOB を送ることで、デバイスの正常性状態を伝えます。 詳細については、「[Steuerelement die Integrität der Devices」 Windows 10-basierte](https://technet.microsoft.com/library/mt592023.aspx) (Windows 10 ベースのデバイスの正常性の制御) を参照してください。

Intune 管理者は、[Intune 管理コンソール](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)で Windows 10 デバイス正常性構成証明書の状態を確認できます。 デバイス正常性構成証明書により、管理者はクライアント コンピューターの BIOS、TPM、ブート ソフトウェア構成が信頼のおけるものであることを確認できます。 デバイス正常性構成証明書をサポートするには、クライアント デバイスが TPM 2 を有効にして Windows 10 を実行している必要があります。 

プライベート クラウドを使用できるようにするテクノロジを使用して、クラウド プロバイダー自体として機能する多くの会社では、ロール ベース アクセス制御 (RBAC) を使用することもできます。             [Azure AD では、IT 担当者は RBAC を使用](http://azure.microsoft.com/documentation/articles/role-based-access-control-configure/)してリソースへのアクセスを制御できます。 Azure AD はオンプレミス Active Directory と統合できるため、この機能を活用して、ユーザーがリソースにアクセスする方法を決定できます。

リソースとしてアプリを使用することもできます。 これは、リソースへのアクセス制御を実装するために、MDM ソリューションでアプリのインストールとアクセス方法も制御できる必要があることを意味します。             [Intune のモバイル アプリケーション管理ポリシー](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)では、会社のコンプライアンスとセキュリティ ポリシーに必ず準拠するように、展開するアプリの機能を変更できます。 

次の表を参考にしながら、組織のアクセス制御要件に最適な MDM オプションを選択してください。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- アプリのアクセス制御 (インストールおよび管理)
- 正常性構成証明書サービスによる条件付きアクセス

**短所**

- 現在のオンプレミス MDM プラットフォームと統合されないため、使用する管理インターフェイスを追加する必要あり
- 一部のモバイル プラットフォームで一部のポリシーが使用できない可能性あり
 
## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- 電子メール、Office Mobile、Office アプリ、および OneDrive for Business へのアクセス制御

**短所**

- リソースへのアクセス制御の小さなサブセットのみを許可
- 現在のオンプレミス MDM プラットフォームと統合されないため、使用する管理インターフェイスを追加する必要あり
- 一部のモバイル プラットフォームで一部のポリシーが使用できない可能性あり

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- アプリのアクセス制御 (インストールおよび管理)
- 正常性構成証明書サービスによる条件付きアクセス

**短所**

- Intune サブスクリプションの購入時に Azure AD クラウド サービスが含まれない

## <a name="-"></a>エンタープライズ モビリティ スイート

**長所**

- アプリのアクセス制御 (インストールおよび管理)
- Azure AD-Premium を活用して、RBAC ベースのアクセス制御を提供
- 正常性構成証明書サービスによる条件付きアクセス

**短所**

- Configuration Manager 組織で現在オンプレミス インフラストラクチャが構成されていない場合、統合の前に、このプラットフォームの計画、インストール、構成が必要
