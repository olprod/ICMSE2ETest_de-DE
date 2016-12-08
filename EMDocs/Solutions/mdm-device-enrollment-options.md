---
title: "デバイス登録オプション"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 54082b94-1d21-44d5-9fba-af6e04397def
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: fe4e4fd5bc06b842592ba8234ee25115019a4df7
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>デバイス登録オプション

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

Microsoft Intune にデバイスを登録するには、スタンドアロンでも、System Center 2012 R2 Configuration Manager (Configuration Manager) に接続する場合でも、デバイス用にサービスを準備する必要があります。 Office 365 の MDM にモバイル デバイスを登録する場合も、MDM をアクティブ化して基本的な設定を構成し、各ユーザーを[セキュリティ ポリシー](https://technet.microsoft.com/library/ms.o365.cc.newdevicepolicy.aspx)に含めて、ユーザーが次回モバイル デバイスで Office 365 にサインインするときに登録メッセージに対応する必要があります。 ユーザーは、Office 365 の電子メールやドキュメントへのアクセスに使用する各モバイル デバイスで、登録とアクティブ化の手順を実行する必要があります。

モバイル デバイス管理機関ソリューションを定義するために、Intune スタンドアロンを構成する必要があります。 モバイル デバイス管理機関ソリューションは、Intune とオンプレミス Configuration Manager インフラストラクチャのどちらでもかまいません。 これは単に、「Intune に登録されたデバイスの管理に Intune と**Configuration Manager のどちらの管理プラットフォームを使用するか」を意味しています。 管理ソリューションを一度選択すると、簡単に変更することはできないので、組織に[最適なオプションを選択する効果](/Intune/deploy-use/enroll-devices-in-microsoft-intune)を理解することが*非常に重要*です。 後でこの構成を変更する必要がある場合は、Microsoft サポートに連絡して支援を求める必要があります。 Office 365 テナントの場合、Office 365 の MDM と Intune の間で MDM 機関を簡単に指定し、変更することができます。 ユーザー レベルの管理機関は、ユーザーのライセンスの割り当てを変更することで簡単に切り替えることができます。 

既に Configuration Manager を使用して PC、サーバー、その他のデバイスを管理しているほとんどの組織では、オンプレミス ソリューションを Intune に接続し、ConfigMgr でデバイスを管理するのが通常は最良の選択です。 モバイル デバイス管理機関を Configuration Manager に割り当てるには、[Intune サブスクリプション](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)を作成し、ConfigMgr で Intune サブスクリプションと Intune に登録されたデバイスを管理できるオプションを選択します。 Intune サブスクリプションは、[Configuration Manager コンソール](https://technet.microsoft.com/library/jj884158.aspx)から作成することもできます。

さらに、さまざま種類のモバイル オペレーティング システムを実行する特定の種類のモバイル デバイスを登録するには、特定の構成要件で Intune サービスまたは Office 365 の MDM を準備しておく必要があります。 たとえば、Apple iOS ベースのデバイスを登録する場合、iOS ベースのデバイスを登録する前に、**[Apple Push Notification (APN) サービス証明書で Intune を構成](https://technet.microsoft.com/library/dn408185.aspx)**する必要があります。 これが構成されていない場合、Intune は APN サービスおよび iOS ベースのデバイスと通信できません。             ** 
Android**または**[Windows Phone](https://technet.microsoft.com/library/dn764959.aspx)**オペレーティング システムを実行しているモバイル デバイスには、別の登録要件があります。

モバイル デバイス管理ソリューションにデバイスを登録する方法を決定するときには、手順 1 での確認事項が役立ちます。 次の表では、各登録シナリオの長所と短所を比較しています。

| 領域  | 管理者がデバイスを登録する | ユーザーがデバイスを自己登録する |
| ------------- | ------------- | ------------ |
| コスト | 経験豊富な管理者がデバイスの登録を実行するので、サポート/ヘルプ デスクのコストが削減される可能性があります。 | 経験の浅いユーザーは登録に個人的援助を必要とすることがあるため、サポート コストやヘルプ デスクの呼び出しが増加する可能性があります |
| 利便性  | 各デバイスはユーザーによる操作なしに登録されるので、デバイス登録エラーが減ります。 ユーザーは管理者とモバイル デバイスを使用する時間を調整することが必要な場合があり、デバイス登録のスケジュール設定と追跡が必要です。| ほとんどの場合、一元的登録プロセスよりデバイス登録に時間がかかりません。 デバイスの所有者/ユーザーの利便性と柔軟性が向上する可能性があります。 |
| Administration | デバイス登録が複雑である/自動化されている/一括処理される/大幅にカスタマイズされている場合も、簡単にサポートできます。 管理者がすべてのデバイスの登録を厳密に管理し、登録プロセスの初めにすべてのデバイスまたはユーザーを効果的に事前スクリーニングします。 | 比較的簡単な管理作業はユーザーに委譲されるので、時間、スケジュール設定、追跡、管理のオーバーヘッド コストが減ります。 |
| セキュリティ | BYOD 戦略をサポートする場合、適切なセキュリティ管理を実施しないと、管理者が機密性の高いユーザーの個人情報を見たり公開したりする可能性が高くなります。 | 今のユーザーはこのような一元化を厄介で面倒と感じて、登録のセキュリティとコンプライアンス プロセスを損なうような回避策をユーザーが勝手に考える可能性があります |

部門や状況によって柔軟に異なる方法を選択できるよう、両方の登録シナリオを使用することもできます。 その場合、モバイル デバイス管理ソリューションは両方のシナリオをサポートできる必要があります。
