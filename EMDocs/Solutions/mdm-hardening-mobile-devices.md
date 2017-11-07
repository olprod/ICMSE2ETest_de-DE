---
title: "モバイル デバイスのセキュリティ強化"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ade57c73-a8a2-497f-ad8d-5dfc3cba9e70
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 3c3112e9f17e55bc49c070a2f3076548b16004c9
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>モバイル デバイスのセキュリティ強化

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

ビジネス ニーズに応じてモバイル デバイスの機能を強化するために構成基準を作成する際には、必ず、使いやすさとセキュリティのバランスをとるようにしてください。 非常に厳密なセキュリティ強化テンプレートでは、従業員の使いやすさとアクセスに問題が発生する可能性があり、ユーザーが自分のデバイスで会社のリソースにアクセスして生産性を高めるのに役立たせるという目的が損なわれます。 

また、すべてのセキュリティ ポリシーがすべてのモバイル デバイス プラットフォームで使用できるわけではないことに注意してください。 デバイスのセキュリティ強化に関するセキュリティ コンプライアンス要件と、組織内のモバイル デバイス プラットフォームを許可する優先順位とのバランスをとる必要がある場合があります。 モバイル デバイスのセキュリティを強化する 1 つの方法は、さまざまな層のセキュリティを設定することです。 各層で使用可能な設定は、MDM ソリューションによって異なる場合もあります。 次の図に、この階層型アプローチの設定方法の例を示します。

![セキュリティ層](./media/MDM_Figure_12.png)

## <a name="-"></a>モバイル デバイスのセキュリティ強化のさまざまな領域

各層を使用して、ビジネス セキュリティ要件に準拠する必要がある領域をグループ化できます。 たとえば、システムのセキュリティ強化設定専用であり、暗号化を有効にする、デバイスの[セキュリティ ポリシー](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)を展開するように Intune を構成できます。 また、ポリシーでは、アクセス ホワイト リストを作成することで、モバイル デバイスにインストールできるアプリを[コンプライアンス遵守アプリ](https://technet.microsoft.com/library/dn818906.aspx)に限定することもできます。

Windows 8.1 Enterprise を実行している BYOD デバイスでは、AppLocker を使用することで、アプリのファイル パス、ハッシュ、またはアプリケーションの更新プログラムに保持されているプロパティ (発行者名、製品名、ファイル名、ファイルのバージョンなど) に基づいてアプリを許可または禁止することができます。 Windows 10 では、MDM サーバーを使用して AppLocker のルールを有効化できるようにするために、新しい AppLocker 構成サービス プロバイダーが追加されました。 Windows-10 のこの新しい機能の詳細については、「[AppLocker CSP](https://msdn.microsoft.com/library/windows/hardware/dn920019(v=vs.85).aspx)」を参照してください。

制御する必要があるもう 1 つの領域は、ユーザーのモバイル ブラウジング エクスペリエンスです。 管理対象ブラウザー ポリシーには、管理対象ブラウザーのユーザーがアクセスできる Web サイトを制限する許可または禁止リストが含まれます。 Intune でこれらのポリシーを構成する方法の詳細については、「[Microsoft Intune と verwaltete Browser のポリシーを使用したインターネット アクセスの管理](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)」を参照してください。

オンプレミスの Configuration Manager とのハイブリッド環境では、管理対象モバイル デバイスの基本的なセキュリティ強化状態を設定した[構成基準](https://technet.microsoft.com/library/gg712268.aspx?WT.mc_id=Blog_EntMob_Showcase_PCIT)を作成できます。 この基準をカスタマイズして必要なすべての設定を含め、モバイル デバイスに展開できます。 コンプライアンス設定のオプションは、モバイル デバイス プラットフォームによって異なります。 各デバイスで使用可能なオプションの詳細については、「[-Konfigurations-Manager でのモバイル デバイスの全般設定](https://technet.microsoft.com/library/dn376523.aspx)」を参照してください。


            [Office 365 の MDM](https://technet.microsoft.com/library/ms.o365.cc.devicepolicy.aspx) にも、モバイル デバイスのセキュリティ強化に役立つ次のカテゴリの一連の機能があります。

- セキュリティ
- 暗号化
- 脱獄
- 管理対象電子メール プロファイル

これらのオプションを適用するためのセキュリティ ポリシーの設定方法の詳細については、「[Office 365 用の組み込みモバイル デバイス管理の機能](https://technet.microsoft.com/library/ms.o365.cc.devicepolicysupporteddevice.aspx)」を参照してください。

モバイル デバイス プラットフォームのセキュリティ強化は、会社のデータを保護したままで、セキュリティを損なうことなくユーザーが自分のモバイル デバイスを使用できるようにする上で重要な役割を果たします。 次の表は、組織のデータ セキュリティ強化要件に最適な MDM オプションを選択する上で役立ちます。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- 登録済みのデバイスに、暗号化、マルウェア、アプリ、電子メール、電子メール プロファイル、脱獄、システム、セキュリティの各ポリシーを適用可能
- 主なモバイル デバイス プラットフォーム (Android、iOS、Windows 10、Windows 8.x、Windows Telefon など) のポリシー展開をサポート

**短所**

- 現在のオンプレミス MDM プラットフォームと統合されないため、モバイル デバイスを管理する際に使用する管理インターフェイスを追加が必要
- 一部のモバイル プラットフォームで一部のポリシーが使用できない可能性あり

## <a name="mdm-for-office-365"></a>MDM für Office 365

**長所**

- 登録済みのデバイスに、暗号化、アプリ、脱獄、セキュリティの各ポリシーを適用可能
- 主なモバイル デバイス プラットフォーム (Android、iOS、Windows 10、Windows 8.x、Windows Telefon など) のポリシー展開をサポート

**短所**

- 現在のオンプレミス MDM プラットフォームと統合されないため、モバイル デバイスを管理する際に使用する管理インターフェイスを追加が必要
- 一部のモバイル プラットフォームで一部のポリシーが使用できない可能性あり
- Intune ほど大きい粒度は使用できない

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- 登録済みのデバイスに、暗号化、マルウェア、アプリ、電子メール、システム、セキュリティ、脱獄の各ポリシーを適用可能
- 主なモバイル デバイス プラットフォーム (Android、iOS、Windows 10、Windows 8.x、Windows Telefon など) のポリシー展開をサポート
- クラウドおよびオンプレミス デバイスから登録されたモバイル デバイス用の 1 つの管理コンソール

**短所**

- 会社で現在オンプレミス Configuration Manager インフラストラクチャが構成されていない場合、統合の前に、ConfigMgr を計画、インストール、構成するためのリソースが必要

>[!TIP] 
> Microsoft Intune のモバイル デバイス セキュリティ ポリシーで構成できるモバイル デバイス管理設定の詳細については、「[Microsoft Intune のモバイル デバイス セキュリティ ポリシー設定](https://technet.microsoft.com/library/dn913730.aspx)」を参照してください。 
