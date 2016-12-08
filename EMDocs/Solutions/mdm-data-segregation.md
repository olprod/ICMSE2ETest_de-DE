---
title: "データの分離"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 50bd37fe-30b5-4a45-9c36-0b907dd13cc2
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: e4e57dedb95b792a06fa92ea56484636b9e76bef
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>データの分離

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

データの分離は、組織だけでなく、ユーザーの個人情報を非公開にするためにも重要です。 。 データの分離により、ユーザーの個人データに影響を与えずに、ユーザーの所有物であるデバイスから会社のすべてのアプリとデータを削除できます (次の図を参照)

![データの分離](./media/MDM_Figure_10.png)

## <a name=""></a>会社のデータから分離されたユーザーの個人データ

すべてのアプリ、会社のデータ、および MDM ソリューションで展開されたポリシーを分離しておくことで、選択的ワイプを使用してユーザー個人のコンテンツやアプリに影響を与えずに、必要に応じてデバイスから削除することができます。 

>[!TIP] 
> iOS や Android などの他のプラットフォームでのリモート ワイプの動作の詳細については、「[Microsoft Intune のフル ワイプまたは選択的ワイプを使用してデータを保護する](/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune)」を参照してください。 

モバイル デバイス データ管理のための選択的ワイプは、Windows Server 2012 R2 および Windows 8.1 に含まれています。 これは、Exchange Server と Microsoft Intune の管理者がデバイスで企業データを管理する場合や、[Windows の選択的ワイプ](https://technet.microsoft.com/library/dn486874.aspx)機能を使用できるアプリを開発する場合に役立つリソースをリンクすることで機能します。  Windows Phone 8 以降では、内部ストレージのデータの分離がサポートされています。

![データの分離](./media/MDM_Figure_11.png)

Windows Phone 8.1 のセキュリティ機能の詳細については、[Windows Phone 8.1 のセキュリティの概要](http://www.microsoft.com/download/details.aspx?id=42509)に関するドキュメントをダウンロードして参照してください。

ユーザーが自分のモバイル デバイスで個人のアカウントと企業のアカウントを切り替える場合、データの分離が難しくなることがあります。 BYOD シナリオでは、通常、ユーザーは複数の資格情報を使用して自分のデバイスでさまざまなタスクを実行します。 

エンタープライズ データ保護 (EDP) ではデータの分離が行われますが、コンテナーは使用されません。 また、ビジネス データにはアプリの特別なバージョンでアクセスし、個人データにはアプリの別のインスタンスでアクセスするということも不要です。 個人データとビジネス データを物理的に分離するためのコンテナー、パーティション、特別なフォルダーはありません。 Mobile がアクセス制御ブローカーとして企業データを識別します。 企業データは企業に対して暗号化されているため、Windows 10 

EDP では、企業データの暗号化によってデータの分離を実現します。 詳細については、「[エンタープライズ データ保護 (EDP) の概要](https://technet.microsoft.com/library/dn985838.aspx)」を参照してください。 Intune の EDP ポリシーは、EDP で保護されているアプリ、エンタープライズ ネットワークの場所、保護レベル、および暗号化設定の一覧を管理します。

ユーザーが Outlook などの Intune 管理対象デバイスで複数の-ID (マルチ ID) をサポートするアプリをインストールしてサインインするときに、Intune はユーザーが使用しているアカウントがデバイスの管理アカウントと一致しているかどうかを確認します。 アカウントが管理されており、アプリとユーザーのポリシーもある場合は、ポリシー設定によりそのアカウントのデータが保護されます。 ユーザーが個人のアカウントをアプリに追加した場合、それらのアカウントは Intune の管理と保護の対象外となります。 これにより、企業の保護を損なうことなく、アプリケーションを個人で使用できるようになります。 Intune の複数の ID 機能の詳細については、「[Microsoft Intune でモバイル アプリケーション管理ポリシーを使用してデータを保護する](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)」を参照してください。 

次の表では、さまざまな MDM ソリューションで使用可能な選択的ワイプ機能を比較しています。 これは、組織のデータ分離要件に最適な MDM ソリューションを選択するうえで役立ちます。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- モバイル デバイス上にある会社のデータのみを削除する選択的ワイプの実行が可能
- 工場出荷時のリセットを実行し、モバイル デバイスを完全にワイプすることが可能
- マルチ-ID アプリのサポート

**短所**

- モバイル デバイス ストレージのネイティブ暗号化は含まれない
- 現在のオンプレミス MDM プラットフォームと統合されない。 使用する管理インターフェイスの追加が必要

## <a name="mdm-office-365"></a>MDM を使用する Office 365

**長所**

- 工場出荷時のリセットを実行し、Android、Windows Phone、および iOS デバイスを完全にワイプすることが可能
- Android、Windows Phone、iOS デバイスで選択的ワイプを実行して、モバイル デバイスから会社のデータのみを削除することが可能

**短所**

- 現在のオンプレミス MDM プラットフォームと統合されない。 使用する管理インターフェイスの追加が必要

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- モバイル デバイスから会社のデータのみを削除する選択的ワイプの実行が可能
- 工場出荷時のリセットを実行し、モバイル デバイスを完全にワイプすることが可能
- マルチ ID アプリのサポート
- 1 つの管理コンソールでクラウド ベースとオンプレミス モバイル デバイスを管理

**短所**

- Configuration Manager 組織で現在オンプレミス インフラストラクチャが構成されていない場合、統合の前に、このプラットフォームの計画、インストール、構成が必要

「[Microsoft Intune のフル ワイプまたは選択的ワイプを使用してデータを保護する](/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune)」を必ず確認して、各モバイル デバイス プラットフォームの選択的ワイプの後、データが削除および保持されるしくみを理解してください。. ハイブリッド環境を使用している場合、ConfigMgr を使用してこのタスクを実行する方法については、「[-Konfigurations-Manager によるリモート ワイプ、リモート ロック、パスコードのリセットを使用したデータの保護](https://technet.microsoft.com/library/dn956981.aspx)」を参照してください。
