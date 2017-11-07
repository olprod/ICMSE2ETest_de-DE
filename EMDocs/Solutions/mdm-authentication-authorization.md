---
title: "認証と承認"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 31b98333-5a3d-49ba-a25e-66447df68035
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 7d25c722d3f90e3db7139d3bf5af6e0df5815e28
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>認証と承認

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

会社のデータを適切に保護するには、ユーザーを識別する必要があります。 そうすることで、ユーザーが要求しているリソースへのアクセスが承認されていることを確認できます。 オンプレミス Active Directory サービスを既に使用している組織は、モバイル ユーザーの認証と承認に活用する必要があります。 すべての Microsoft モバイル デバイス管理ソリューションで、既存の Active Directory インフラストラクチャを使用してこれを行うことができます。 

認証と承認に関するもう 1 つの決定ポイントは、ディレクトリ サービスを配置する場所です。 ほとんどの組織がオンプレミス Active Directory サービスを使用していますが、[Azure AD](http://azure.microsoft.com/documentation/articles/active-directory-whatis/)などのクラウドベースのディレクトリ サービスによるオンプレミス ディレクトリ サービスの拡張を検討している組織もあります。 

Configuration Manager により、[Microsoft Passport für die Arbeit](https://technet.microsoft.com/library/mt488797.aspx)と統合できます。 Microsoft Passport für Arbeit は、Active Directory または Azure Active Directory アカウントを使用した代替サインイン方法であり、Windows 10 を実行しているデバイスのパスワード、スマート カード、または仮想スマート カードに代わるものです。 ハイブリッド シナリオでは、両方のディレクトリの統合により、次のような Azure AD の機能を活用できます。

- 
            **セルフサービス グループ管理**: ユーザーはグループを作成し、他のグループへのアクセスを要求して、他のユーザーが要求を承認できるようにグループの所有権を委任し、グループ メンバーシップを維持できます。
- 
            **99,9 % のエンタープライズ SLA**: Microsoft は、Azure Active Directory Premium サービスの 99,9 % 以上の可用性を保証しています。
- 
            **ライトバック可能なパスワード リセット**: セルフサービスのパスワード リセットをオンプレミス ディレクトリにライトバックできます。

さまざまなオプションと機能の詳細については、[Azure Active Directory](https://msdn.microsoft.com/library/azure/dn532272.aspx)に関するページをご覧ください。 2 種類の認証 (多要素認証、つまり、MFA) を必要とすることは、モバイル デバイス管理ソリューションを計画する場合などに、考慮すべきもう 1 つの戦略です。 Intune では、[ディレクトリ サービスを Multi-Factor Authentication (mehrstufiger Authentifizierung DAS) と統合](https://technet.microsoft.com/library/dn889751.aspx)できます。 これにより、認証プロセスの別のセキュリティ層が追加されます。 

組織に Active Directory フェデレーション サービス (AD FS) が構成された Active Directory ドメインを含むオンプレミス IT インフラストラクチャがある場合、フェデレーション サーバーで mehrstufiger Authentifizierung DAS を構成し、Intune への登録用に mehrstufiger Authentifizierung DAS を有効にすることができます。 フェデレーション サーバーで mehrstufiger Authentifizierung DAS を構成しても、Intune への登録用に mehrstufiger Authentifizierung DAS を有効にしていない場合、ユーザーは、デバイスから企業リソースにアクセスするたびに mehrstufiger Authentifizierung DAS を使用する必要があります。 

また、Azure AD mehrstufiger Authentifizierung DAS を使用して、ユーザーが企業リソースにアクセスするたびに mehrstufiger Authentifizierung DAS を要求することもできます。 これはユーザーごとに有効にすることができます。 Azure AD mehrstufiger Authentifizierung DAS は、オンプレミス IT インフラストラクチャを必要としないクラウド サービスです。

次の表は、組織の認証と承認の要件に最適な MDM オプションを選択する際に役立ちます。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- 認証にオンプレミス ディレクトリ サービス (Active Directory など) を使用できる
- 認証にクラウドベースのディレクトリ サービス (Azure AD など) を使用できる
- 多要素認証と統合が可能

**短所**

- Intune サブスクリプションの購入時に Azure AD クラウド サービスは含まれていない

## <a name="mdm-for-office-365"></a>Für Office 365 MDM

**長所**

- 認証にオンプレミス ディレクトリ (Active Directory など) を使用できる
- 認証にクラウドベースのディレクトリ (Azure AD など) を使用できる
- 多要素認証と統合が可能
- ロールベースのアクセス制御 (RBAC) アクセス許可モデルを使用するコンプライアンス センターを活用できる

**短所**

- Office 365 サブスクリプションの購入時に Azure AD クラウド サービスは含まれていない

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- 認証にオンプレミス ディレクトリ (Active Directory など) を使用できる
- 認証にクラウドベースのディレクトリ (Azure AD など) を使用できる

**短所**

- Intune サブスクリプションの購入時に Azure AD クラウド サービスは含まれていない

## <a name="-"></a>エンタープライズ モビリティ スイート

**長所**

- Azure AD Premium を活用してアクセスを制御できる
- Azure AD Premium ライセンスが zur Abstimmung に既に含まれている
- オンプレミス ディレクトリ サービスは不要
- Active Directory オンプレミス サービスと同期できる
- ZUR ABSTIMMUNG で MEHRSTUFIGER AUTHENTIFIZIERUNG DAS をネイティブに使用できる

**短所**

- クラウドベースのソリューションを採用していない顧客は使用できない

