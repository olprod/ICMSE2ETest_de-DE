---
title: "Konfigurations-Manager でのモバイル アプリ管理ポリシーの使用"
description: "モバイル アプリ管理 (MAM) ポリシーを使用して、Configuration Manager でアプリを作成し展開します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74288276-84d3-4d24-8307-7875491be9c9
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 40db520e40d54d75c436c52c1495a9b133d38b28
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="configuration-manager-"></a>Konfigurations-Manager でのモバイル アプリ管理ポリシーの使用
System Center 2012 Configuration Manager SP2 以降では、アプリ管理ポリシーにより、会社のコンプライアンス ポリシーやセキュリティ ポリシーに合わせて、展開するアプリの機能を変更できるようになりました。 たとえば、制限付きアプリでの切り取り、コピー、および貼り付け操作を制限することや、管理対象ブラウザー内ですべての リンクを開くようにアプリを構成することができます。 Web アプリ管理ポリシーでは以下をサポートします。

- Android 4 以降を実行するデバイス。
- iOS 7 以降を実行するデバイス。

> [!TIP]
> 管理対象のデバイスだけでなく、モバイル アプリ管理ポリシー (MAM) を使用して、Intune で管理されていないデバイス上のアプリを保護することができます。 この新機能を使用して、Office 365 サービスに接続するアプリに対してモバイル アプリ管理ポリシーを適用できます。 これは、オンプレミスの Exchange や SharePoint に接続するアプリではサポートされていません。 この新機能を使用するには、Azure ポータルを使用する必要があります。 使い始めるにあたり、次のトピックを参考にしてください。
- [Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)
- [Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

Konfigurations-Manager の構成項目および基準とは異なり、アプリケーションの管理ポリシーは直接展開しません。 代わりに、制限するアプリ展開の種類 (DT) にポリシーを関連付けます。 アプリ DT がデバイスに展開され、インストールされると、指定された設定が有効になります。

アプリに制限を適用するには、アプリに Microsoft Intune アプリ ソフトウェア開発キット (SDK) を組み込む必要があります。 この種類のアプリを取得するには、次の 2 つの方法があります。

- 
            **ポリシー管理型アプリを使用する** (Android および iOS): アプリ SDK が組み込まれています。 この種類のアプリを追加するには、iTunes ストアや Google wiedergeben などのアプリ ストアからアプリへのリンクを指定します。 それ以上の処理は、この種類のアプリには必要ありません。 iOS デバイスと Android デバイスで使用可能なポリシー管理型アプリの一覧については、「[Microsoft Intune mobilen Anwendung Gallery](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)」 (Microsoft Intune モバイル アプリケーション ギャラリー) をご覧ください。
- 
            **"ラップされた" アプリを使用する** (Android および iOS): Microsoft Intune アプリ ラッピング ツールを使用して、アプリ SDK を含むように再パッケージされたアプリ。 通常、このツールは、社内で作成された企業アプリの処理に使用されます。 このツールを使用して、アプリ ストアからダウンロードされたアプリを処理することはできません。 「[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために iOS アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)」および「[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために Android アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)」をご覧ください。

## <a name="-configuration-manager-"></a>モバイル アプリ管理ポリシーを使用して、Configuration Manager でアプリを作成し展開する

- 手順 1: ポリシー管理型アプリへのリンクを取得するか、ラップされたアプリを作成する。
- 2 手順: アプリが含まれた アプリケーションを作成する。 Konfigurations-Manager
- 手順 3: モバイル アプリ管理ポリシーを作成する。
- 手順 4: アプリケーション管理ポリシーと展開の種類を関連付ける。
- 手順 5: アプリの展開を監視する。

### <a name="-1-"></a>手順 1: ポリシー管理型アプリへのリンクを取得するか、ラップされたアプリを作成する。
- 
            **ポリシー管理型アプリへのリンクを取得するには**- アプリ ストアから、展開するポリシー管理型アプリの URL を見つけてメモします。 たとえば、Microsoft Word für iPad アプリの URL は、[https://itunes.apple.com/jp/app/microsoft-word-for-ipad/id586447913?mt=8](https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8)です。
- 
            **ラップされたアプリを作成するには**- 「[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために iOS アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)」と「[Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために Android アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)」の各トピックの情報を活用して、ラップされたアプリを作成します。 このツールは、処理済みのアプリと関連するマニフェスト ファイルを作成します。 アプリが含まれている アプリケーションの作成時にこれらのファイルを使用します。-Konfigurations-Manager

### <a name="-2-configuration-manager-"></a>手順 2: アプリが含まれた アプリケーションを作成する。-Konfigurations-Manager
Konfigurations-Manager アプリケーションの作成手順は、ポリシー管理型アプリ (外部リンク) であるか、iOS 用 Microsoft Intune アプリ ラッピング ツール を使用して作成されたアプリかによって異なります。 (iOS 用アプリ パッケージ)

アプリを含む Configuration Manager アプリケーションを作成するために必要なすべての手順は、「[-Konfigurations-Manager のモバイル アプリケーション管理ポリシーを使用してアプリを制御する方法](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396#BKMK_Step2)」をご覧ください。

アプリケーションは作成すると [**ソフトウェア ライブラリ**] ワークスペースの [**アプリケーション**] ノードに表示されます。

### <a name="-3-"></a>手順 3: モバイル アプリケーション管理ポリシーを作成する。
次に、アプリケーションと関連付ける[アプリケーション管理ポリシーを作成](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396#bkmk_step3)します。 全般ポリシーまたは管理対象ブラウザー ポリシーを作成することができます。

作成した新しいポリシーは、 [**ソフトウェア ライブラリ**] [**アプリケーション管理ポリシー**] ワークスペースの ノードに表示されます。

### <a name="-4-"></a>手順 4: アプリケーション管理ポリシーと展開の種類を関連付ける。
アプリケーション管理ポリシーを必要とするアプリ用に展開の種類を作成する場合、Configuration Manager は、関連付けられたアプリが展開されるときにアプリケーション管理ポリシーがこの展開の種類とリンクし、アプリケーション管理ポリシーと関連付けるよう求めるメッセージを表示する必要があることを認識します。 管理対象ブラウザーでは、全般ポリシーと管理対象ブラウザー ポリシーの両方を関連付ける必要があります 詳細については、「[-Konfigurations-Manager でモバイル デバイス用アプリケーションを作成して展開する方法](https://technet.microsoft.com/library/dn469410.aspx)」をご覧ください。

> [!TIP]
> iOS 7.1 以前のオペレーティング システムを実行しているデバイスの場合、関連付けられているポリシーはアプリのアンインストール時に削除されません。

> デバイスが から登録解除された場合、ポリシーはアプリから削除されません。-Konfigurations-Manager ポリシーが適用されたアプリは、アプリがアンインストールされ、再インストールされた後でもポリシー設定を保持します。


### <a name="-5-"></a>手順 5: アプリの展開を監視する。
MAM ポリシーに関連付けられたアプリを作成し、展開すると、[アプリを監視し、ポリシーの競合を解決することができます](https://technet.microsoft.com/library/mt131414.aspx?f=255&MSPPError=-2147217396#BKMK_Step5)。

アプリケーションの監視の概要については、「[-Konfigurations-Manager でのアプリケーションの監視方法](https://technet.microsoft.com/library/gg682201.aspx)」をご覧ください。

## <a name=""></a>この後の対応

MAM ポリシーに関連付けられているアプリを作成および展開したら、「[MAM のエンド ユーザー エクスペリエンス](end-user-experience-mam.md)」を参照してください。 これで、発生する可能性のあるすべての問題に備えることができます。
