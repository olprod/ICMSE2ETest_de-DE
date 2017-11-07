---
title: "モバイル デバイス管理の設計に関する考慮事項のガイド"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7083b6b8-27a3-427b-b505-25d007d63cdd
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 5c52fdf79137819640c306dc2306c2a0bf6666ff
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>モバイル デバイス管理の設計に関する考慮事項のガイド

モバイル デバイス管理 (MDM) ソリューションに設計と構成のさまざまなオプションがあると、組織のニーズに最適なソリューションを判断することが難しい場合があります。 この設計ガイドでは、MDM の設計要件をわかりやすく示すと共に、組織のビジネスおよびテクノロジのニーズに最適な MDM ソリューションを設計するための一連の手順と作業について詳しく説明します。 

## <a name=""></a>概要

レベルの要件を満たすために利用できる関連技術と機能について紹介します。 このガイドでは、手順と作業を通して、組織が機能とサービス品質 (可用性、拡張性、性能、管理容易性、セキュリティなど)

具体的には、このガイドを読むことで次のような質問に回答できるようになります。

- ビジネス要件に最適なモバイル デバイス管理ソリューションの導入を促進するために、どのような質問に答える必要があるか。
- 組織のモバイル デバイス管理ソリューションを設計するために完了する必要がある一連のアクティビティは何か。
- Microsoft 要件を満たすために使用できる モビリティ管理テクノロジと構成のオプションは何か。 それらのオプション間のトレードオフは何か。

**このガイドの対象読者**中規模または大規模組織向けのモバイル デバイス管理ソリューションの設計を担当する情報テクノロジ設計担当者およびプロフェッショナル。

**このガイドの利用方法**このガイドを使用すると、会社所有のデバイスだけでなく、さまざまなフォーム ファクターのユーザー所有のデバイスを管理できるモバイル デバイス管理ソリューションを設計する方法を理解することができます。

![Intune と System Center Configuration Manager のハイブリッド MDM ソリューションの例](./media/MDM_Figure_01.png)
**Intune と System Center Configuration Manager のハイブリッド MDM ソリューションの例**

上の図は、場所を問わずあらゆる種類のデバイスを管理するために、クラウド サービスを利用してオンプレミスの機能と統合しているハイブリッド管理ソリューションの例を示しています。 これは非常に一般的なシナリオですが、組織固有の管理の要件があるため、組織の MDM の設計は例と異なる可能性があります。
 
このガイドでは、組織固有の要件を満たす、カスタマイズされた MDM ソリューションの設計に役立つ一連の手順と作業について説明します。 このガイドでは、次の手順と作業を通じて、MDM の機能とサービス品質レベルの要件を満たすために使用できるテクノロジと機能のオプションについて説明します。 

このガイドは MDM ソリューションの設計に役立ちますが、管理ソリューションの特定の実装または操作のオプションや、既存のサードパーティ製 MDM ソリューションから移行する方法については説明しません。             [Microsoft Intune](/Intune/)、[Office 365 用のモバイル デバイス管理](https://technet.microsoft.com/library/ms.o365.cc.devicepolicy.aspx)、[Microsoft System Center Configuration Manager](https://technet.microsoft.com/library/cc507089.aspx)の展開と構成の詳しい手順については、このガイドの最後にある「**次の手順と追加のリソース**」に用意されているリンクを使用して、docs.microsoft.com と TechNet ライブラリで確認できます。

他の MDM ソリューションから Microsoft Intune に移行する方法のガイダンスについては、[こちら](https://blogs.technet.microsoft.com/intunesupport/2016/02/10/new-guide-on-how-to-migrate-from-other-mdm-technologies-to-microsoft-intune/)をご覧ください。


            **前提:** Microsoft Intune、System Center 2012 R2 Configuration Manager (ConfigMgr)、Windows Server 2012 R2、および Android、iOS、Windows Phone を実行しているモバイル デバイスの使用経験があること。 これらのソリューションのいずれかを初期の MDM テストまたは限定された運用環境で展開したこともあること。 このガイドは、これらのソリューションを自身で、または統合ソリューションでビジネス ニーズに最も適合させる方法を求めているユーザーを想定しています。

## <a name="mdm-"></a>MDM の設計に関する考慮事項
このガイドでは要件に最も適したソリューションを設計するための一連の手順と作業について説明します。 手順は順番に説明します。 ただし、後半の手順で学習する設計上の考慮事項では、設計の完成に伴い、または選択した設計との競合により、前半の手順で決定した内容を変更しなければならなくなることがあります。 このガイドを通じて、設計の競合の可能性を通知します。

このガイドのすべての考慮事項を取り入れるために必要な回数だけ手順を繰り返すことで、初めて要件に最も適したモバイル デバイス管理の設計が完成します。 

- [1 手順: モバイル デバイス管理の要件を特定する](mdm-step-1-identify-your-mobile-device-management-requirements.md)
- [手順 2: モバイル デバイス管理を計画する](mdm-step-2-plan-for-mobile-device-management.md)
- [手順 3: モバイル デバイスの保護を計画する](mdm-step-3-plan-enhancing-mobile-devices-protection.md)
- [手順 4: サービスとしてのソフトウェア (SaaS) モバイル デバイス管理を計画する](mdm-step-4-plan-for-software-as-a-service-mobile-device-management.md)
- [次の手順と追加のリソース](mdm-next-steps-and-additional-resources.md)
        
## <a name=""></a>ダウンロード可能なバージョン
このガイド全体のダウンロード可能なコピーは、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)で入手できます。
