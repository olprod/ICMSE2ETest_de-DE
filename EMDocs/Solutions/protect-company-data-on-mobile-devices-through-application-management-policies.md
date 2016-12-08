---
title: "MAM と MDM を使用した会社のデータの保護"
description: "社内データが最適に保護されるように、モバイル アプリ管理 (MAM) ポリシーでアプリを作成および展開します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 05/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 6c7088a9-ca88-4ff2-97a6-f842691fd3c7
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 7c9f05638b3fcffdc88dd3cfb1970de3de26fc4d
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>モバイル デバイス上の社内データをアプリケーション管理ポリシーで保護する
社内のデータ保護は非常に重要ですが、メールやメールの添付ファイルも含めた社内リソースへのアクセスに個人のモバイル デバイスを利用する従業員がますます増加しており、非常に困難な作業になっています。 モバイル デバイスが物理的に社内になくても、IT 管理者は社内データを確実に保護する必要があります。

このガイドでは、次の 2 つの Intune MDM の展開で使用される管理対象のアプリケーションの有効化に焦点を当てて説明を行います。

- Intune が使用されているクラウドの管理ソリューションとして
- Konfigurations-Manager と統合されたサービスとして

これは、社内データが最適に保護されるように、モバイル アプリ管理 (MAM) ポリシーでアプリを作成および展開することを可能にします。

このドキュメントでは、エンドユーザーのデバイスに Intune が MDM 用に登録されているときに、これらの MAM ベース ポリシーを作成することに焦点を当てます。 Intune に MDM 用にデバイス自体が登録されていない場合に、これらの MAM ポリシーを構成する方法の詳細については、「[基幹業務アプリケーションおよび Microsoft Intune に登録されていないデバイス上のデータを保護する](https://docs.microsoft.com/intune/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune)」をご覧ください。

> [!TIP]
> このトピック全体のコピーは、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Protect-Company-Data-on-d972f4f4/file/154240/1/Protect%20Company%20Data%20on%20Mobile%20Devices%20through%20Application%20Management%20Policies.pdf)からダウンロードできます。

## <a name=""></a>概要
管理対象アプリとは、MAM 管理ポリシーが適用されているアプリであり、会社のセキュリティ要件に準拠するものです。 モバイル アプリの管理には、2 つオプションがあります。
- Apple verwaltet In などの**既定の機能**。 öffnen 特定のドキュメントやメールの添付ファイルを開くことが許可されているアプリを制御して企業データを保護します。
- 
            **Intune アプリ SDK**。 Intune アプリ SDK が有効になっているすべてのアプリで機能を制限したり、データの共有を制限したりすることができます。 Intune アプリ SDK の主要機能の一部は次のとおりです。
  - 名前を付けて保存機能の管理
  - 切り取り、コピー、貼り付けの阻止
  - アプリへのアクセス時の認証の要求
  - Intune で管理されているアプリからの企業データの消去

  SDK のすべての機能の詳細については、「[Intune アプリ SDK の概要](https://docs.microsoft.com/intune/develop/intune-app-sdk)」をご覧ください。

## <a name=""></a>始める前に
- 
            **Microsoft Intune を使用したアプリの展開について学習する:** Intune アプリの展開の[基本事項について学習](https://docs.microsoft.com/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)します。

- 
            **希望の実装を評価する:**モバイル デバイスの管理の設計と構成オプションは多岐にわたるため、会社のニーズに最適な組み合わせを決定することは困難な場合があります。 「[モバイル デバイス管理の設計に関する考慮事項のガイド](https://docs.microsoft.com/enterprise-mobility/Solutions/mdm-design-considerations-guide)」は、モバイル デバイス管理の設計要件の理解を助け、自社のビジネスやテクノロジに最適なソリューションを設計するための一連の手順やタスクについて詳しく説明しています。.
- 
            **エンド ユーザー エクスペリエンスの概要を理解する:**このソリューションを実装したら、会社でそれを管理しているかどうかに関係なく、デバイス上のデータを保護できます。 単にアプリレベル ポリシーを実装するだけで、会社のリソースへのアクセスを制限し、データを IT 部門の管理範囲内に保つことができます。

   > [!NOTE]
   > このソリューションのエンドユーザー エクスペリエンスの詳細については、「[エンドユーザー エクスペリエンス](end-user-experience-mam.md)」をご覧ください。

- 
            **アプリのライフサイクルを理解する:**というライフサイクルがあります。 デバイスの管理と同様、アプリにも、準備、展開、監視、更新、削除 (退役) Intune は、そのライフサイクルのすべての段階を支援します。 アプリのライフサイクルの詳細については、「[アプリのライフサイクルの概要](https://docs.microsoft.com/intune/deploy-use/overview-of-app-lifecycle-in-microsoft-intune)」をご覧ください。
- 
            **MAM ポリシーで使用できる Microsoft アプリについて学習する:** [Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)ページには、Microsoft をはじめとする会社が提供しているアプリのうち、モバイル アプリ管理ポリシーで使用できるものについて最新情報が掲載されています。

  Microsoft Intune アプリ ラッピング ツールを使用して社内アプリの動作を変更すると、アプリ自体のコードを変更しなくてもアプリの機能を構成できます。 具体的には、次の各トピックを参照してください。
 - [Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために iOS アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
 - [Intune アプリ ラッピング ツールでモバイル アプリケーションを管理するために Android アプリを準備する](https://docs.microsoft.com/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

- 
            **ポリシーの競合がどのように解決されるか理解する:**ユーザーまたはデバイスへの最初の展開で、モバイル アプリ管理ポリシーの競合がある場合、競合している特定の設定値が、アプリにデプロイされたポリシーから削除され、アプリは組み込みの競合値を使用します (既定は**最も厳しい制限**です) 。

  アプリまたはユーザーへの以降のデプロイでモバイル アプリ管理ポリシーの競合がある場合、競合している特定の設定値は、アプリにデプロイされたモバイル アプリ管理ポリシーで更新されず、アプリはその設定の既存の値を使用します。

  2 デバイスまたはユーザーが つの競合するポリシーを受け取った場合は、次の動作が適用されます。
  - ポリシーがデバイスに既にデプロイされている場合、既存のポリシー設定は上書きされません。
  - ポリシーが既にデバイスにデプロイされておらず、2 つの競合する設定がデプロイされている場合、デバイスに組み込まれている既定の設定が使用されます。

## <a name=""></a>この後の対応
ここまでで MAM の全体的なプロセスを確認しました。 次は「[Intune でのモバイル アプリ管理ポリシーの使用](mam-intune.md)」または「[-Konfigurations-Manager でのモバイル アプリ管理ポリシーの使用](mam-configmgr.md)」に進みます。 または、「[MAM ポリシーのエンド ユーザー エクスペリエンス](end-user-experience-mam.md)」をご覧ください。
