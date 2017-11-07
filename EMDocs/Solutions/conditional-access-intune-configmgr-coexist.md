---
title: "Intune と Konfigurations-Manager による Exchange での条件付きアクセス"
description: "Exchange lokalen と Exchange Online の組み合わせに加えて Konfigurations-Manager と Intune を使用して、電子メールへのアクセスを管理し、モバイル デバイスで電子メール データを保護します。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5ccd033f-bc31-4fae-b6bf-9e1c2722627f
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 30904851a7d64633fe594d33f40bd1672ce2978a
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="microsoft-intune-configuration-manager-exchange-online-exchange-on-premises-"></a>Microsoft Intune と Konfigurations-Manager を使用した Exchange Online と Exchange lokal の展開

            [会社の電子メールとドキュメントを保護するためのアーキテクチャ ガイダンス](architecture-guidance-for-protecting-company-email-and-documents.md)を確認しました。これでソリューションの展開に進むことができます。

オンプレミスの Exchange Server と Exchange Online の両方を使用して電子メール プロファイルを管理する環境では、会社は、既存のオンプレミスの Microsoft Exchange の組織で保有する機能豊富なエクスペリエンスと管理コントロールをクラウドに拡張することができます。 Exchange Server 2013 の組織と Microsoft Office 365 の Exchange Online の間で、単一の Exchange の組織のシームレスなルック アンド フィールを提供します。-タイプの展開では、オンプレミスの この "ハイブリッド" さらに、このタイプの展開は、Exchange Online 組織に完全に移行する中間のステップとして使用できます。

Konfigurations-Manager をオンプレミスの Exchange Server と Exchange Online の共存と共に既に使用している場合は、電子メールへのアクセスを管理し、モバイル デバイスで電子メール データを保護するために、Intune を組み込むことができます。 このソリューションを実装するには、各ソリューションを実装するための上記の説明に個別に従います。

## <a name=""></a>必要条件
Exchange Online の両方を実装する共存タイプの環境を構成するには、既存の Exchange Server für die オンプレミスの と の組織は特定の要件を満たす必要があります。 Exchange これらの要件を満たしていない場合は、オンプレミスの Exchange の組織と Microsoft Office 365 の Exchange Online の組織の間のハイブリッド展開を構成するために必要な手順を完了できません。

このような環境を作成および構成するための要件を確認するには、「[ハイブリッド展開の前提条件](https://technet.microsoft.com/library/hh534377.aspx)」をご覧ください。

## <a name=""></a>展開の手順
共存ソリューションを展開するには、[オンプレミスの Exchange Server](conditional-access-intune-configmgr-exchange.md)ソリューションと[Exchange Online](conditional-access-intune-configmgr-exchange-online.md)ソリューションの両方を展開するための上記の手順に従います。

## <a name=""></a>この後の対応
モバイル デバイスの会社の電子メールと電子メール データを保護するためのソリューションを展開したら、[条件付きアクセスのエンド ユーザー エクスペリエンス](end-user-experience-conditional-access.md)の詳細を確認します。 これにより、エンド ユーザーが特定のデバイスを登録するときに発生する可能性のある問題に備えることができます。
