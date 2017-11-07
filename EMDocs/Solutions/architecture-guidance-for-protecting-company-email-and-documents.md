---
title: "会社の電子メールとドキュメントを保護するためのアーキテクチャ ガイダンス"
description: "会社のデータを保護しながら、エンド ユーザーのエクスペリエンスをシンプルに保ち、生産性に影響を与えないようにします。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc9c7d79-d2ca-4cb2-8456-c7a88cbbf6fd
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 9540311442cd0df6a038a41b0e1d5cdf83ebfccf
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>会社の電子メールとドキュメントを保護するためのアーキテクチャ ガイダンス
このトピックでは、はじめに、会社のデータを保護しながら、エンド ユーザーのエクスペリエンスをシンプルに保ち、生産性に影響を与えないようにする方法についての概要を説明します。 次に、Microsoft Enterprise Mobilität Suite ソリューションを使用して、会社の電子メールへのセキュリティで保護されたアクセスを実現し、電子メールと添付ファイルに含まれる会社のデータを保護できるようにする方法について詳しく説明します。

このセクションでは、会社の電子メールとドキュメントを保護するためのアーキテクチャについて説明します。 ソリューションの展開に関するガイダンスは、「[会社のメールとドキュメントを保護するためのソリューションを展開する方法](learn-how-to-deploy-a-solution-for-protecting-company-email-and-documents.md)」を参照してください。

> [!TIP]
> このトピック全体のダウンロード可能なコピーは、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Managing-Access-and-Help-b7a05d0d/file/140056/1/Managing%20Access%20and%20Help%20Protect%20Corporate%20Email%20Data%20on%20Mobile%20Devices.pdf)から入手できます。

従業員が自分のデバイスを使用して会社のリソースと生産性向上ツールにアクセスすることを希望している場合、 IT 部門は、これを実現しつつ、会社の機密データを保護する必要があります。 には、個人のデバイス上で個人のデータと仕事のデータを分離し、意図的か否かにかかわらず会社のデータが共有されないようにするという固有の課題が伴います。 BYOD ([schalten Sie Ihr eigenes Gerät](byod-design-considerations-guide.md))

**調査により以下のことが明らかになりました。**

-   世界中の従業員の 37 % がモバイルを使用している

-   2014 年第 3 四半期の電子メールの開封の 53 % が携帯電話またはタブレットで行われている

-   労働者の 61 % が、個人のタスクと仕事のタスクを自分のデバイスで混在させている

次の点を考慮してください。

-   電子メールは、あらゆるデバイス上で最も使用されているアプリケーションである。

-   電子メールと電子メールの添付ファイルのコンテンツは、IT 部門の管轄外の場所にコピー、共有、移動することができる。 これにより、会社のセキュリティが損なわれる可能性がある。

エンド ユーザーは自分の個人デバイスを使用して会社の作業を実行することを望み、電子メールは最も頻繁にアクセスされるアプリケーションであるため、IT 部門が最初にとるべき措置は、電子メール内の機密データが損なわれないようにしつつ、エンド ユーザーが自分のデバイスで会社の電子メールにアクセスできるように保証することです。

## <a name=""></a>概要
Microsoft は、Enterprise Mobilität Suite (zur Abstimmung) という、ID、モバイル デバイス管理、アプリ管理、データ保護のための包括的なソリューションを提供します。 ZUR ABSTIMMUNG は、ほぼすべてのデバイスから電子メール、データ、会社のアプリケーションへのアクセスを IT 部門が管理できる多層型セキュリティ モデルを提供します。

ZUR ABSTIMMUNG は、次のクラウド サービスで構成されます。

![Zur Abstimmung に含まれるクラウド サービス、Microsoft Azure AD Premium、Microsoft Intune、および Microsoft Azure Rights Management を示すグラフィック](./media/ProtectEmail/Enterprise-Mobility-Suite.png)

ZUR ABSTIMMUNG を使用すると、会社のネットワーク内外両方のデータが保護される

-   従業員は、会社の機密情報の漏えいを心配せずに、任意のデバイスで会社の電子メール、作業に関連するアプリケーション、会社のデータにアクセスできます。

-   会社のデータは、ユーザー、デバイス、アプリケーション、さらにはデータ自体の各レベルで保護されます。

-   IT-管理者は会社のデータが、信頼されたユーザーによって、管理対象の準拠デバイスを使用して、管理対象のアプリケーションのコンテキストでのみアクセスされるように徹底できます。

Intune の管理対象のアプリには、このソリューションの中心である Office モバイル アプリが含まれます。 Office モバイル アプリを使用して、データの漏えいを防止しながら、従業員の生産性を最大限まで高めることができます。 たとえば、IT 管理者は Ablage などの個人クラウド ストレージへの会社のデータのコピーを防止するポリシーを設定することができます。

従業員の異動や職務変更、デバイスの紛失の際には、デバイスから会社のデータをリモートで選択的にワイプするための ZUR ABSTIMMUNG のオプションを利用できます。 これは、エンド ユーザーまたは IT 管理者が実行できます。

## <a name="ems-"></a>ZUR ABSTIMMUNG がデータを保護するしくみ
4 ID、デバイス、アプリ、データの 階層のセキュリティ モデルにより、会社のリソースは、所定のユーザーによって、構成された一連のコンプライアンス ポリシーをすべて満たすデバイスから、管理対象アプリの境界内でのみ、アクセスされることが保証されます。

![4 ID、デバイス、アプリ、およびデータの 階層のセキュリティ モデルを示すグラフィック](./media/ProtectEmail/Protecting_your_data.png)

データを保護するにはまず、ユーザー-ID を作成し確認します。 エンタープライズ レベルの-ID およびおアクセス管理ツール*Azure AD /*は、シングル サインオン、多要素認証、パスワードのセルフ サービスなどを提供します。 これは、セキュリティ モデルの**ID 層**の機能を提供します。

IT 管理者は、ID ベースラインを基盤として、 *Microsoft Intune*を使用し、モバイル デバイスが登録および管理され、会社のポリシーに準拠するように徹底できます。 これが、**デバイス層**です。

3 番目の層は**アプリ管理層**で、Intune による管理対象アプリのエコシステムを備えています。 このエコシステムにより、ユーザーの生産性が高められ、Office のような不可欠で習熟済みのツールを使用できる一方、IT 部門は管理対象アプリのエコシステム内で機密データを保持することもできます。


            *Azure Rights Management (Azure RMS)* は、ファイル レベルでデータを保護することで、完全なセキュリティ モデルを実現しています。 データや、データを携えた移動に適用されるセキュリティ ポリシーは、アクセスに使用されるデバイスに関係なく、送信中データと保存データをセキュリティで保護します。 これが、セキュリティ モデルの**データ層**です。

## <a name=""></a>この後の対応
- このビデオを[視聴](https://www.youtube.com/watch?v=ltcZvm4VOFU)し、試用版アカウントにサインアップして使用する方法について確認してください。

- 「[モバイル デバイス管理の設計に関する考慮事項のガイド](mdm-design-considerations-guide.md)」で、モバイル デバイス管理の設計要件を確認してください。.

- 
            [会社のメールとドキュメントを保護するためのソリューションを展開する方法について確認してください](learn-how-to-deploy-a-solution-for-protecting-company-email-and-documents.md)。

また、EMS と Azure Active Directory の詳細について確認する場合は、次の記事のいずれかで詳細情報を入手できます。
- [ZUR ABSTIMMUNG アーキテクチャ](https://azure.microsoft.com/documentation/infographics/enterprise-mobility/)

- [Azure Active Directory とは](/active-directory/active-directory-whatis)

- [Azure Active Directory による Office 365、Microsoft Intune、その他の Microsoft サービスのサポート](/active-directory/active-directory-administer#what-is-an-azure-ad-tenant)

- [Azure Active Directory を使用した ID の管理方法](/active-directory/active-directory-administer)

- [Azure Rights Management とは](/rights-management/understand-explore/what-is-azure-rms)

- [アプリケーションによる Azure Rights Management のサポート](/rights-management/understand-explore/applications-support)
