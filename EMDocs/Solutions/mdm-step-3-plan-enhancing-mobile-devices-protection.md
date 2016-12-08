---
title: "モバイル デバイス保護の強化の計画"
description: 
keywords: 
author: YuriDio
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a4504456-a241-4380-ab92-3bc14c91347c
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 22355a75bb277e5e5e45baa634f93bb6e14796fa
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>モバイル デバイス保護の強化の計画

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

オンプレミスおよびリモート ユーザーは自分のモバイル デバイスから会社のリソースにアクセスすることで生産性を高めることができますが、その場合、会社のデータを保護し、ユーザーのプライバシーを維持するために軽減する必要があるセキュリティ上の脅威も高まります。 会社には、これらのニーズのバランスをとる方法に関する特定の要件がある場合があります。 コンプライアンス規則は、会社が活動している業界によって異なる可能性があります。 たとえば、設計上の決定などが異なる場合があります。
 
ただし、業界に関係なく、モバイル デバイス管理におけるセキュリティには確認および準拠する必要がある一般的な側面がいくつかあります。 これらを次の図に示します。

![MDM プラットフォームの主要なセキュリティ機能](./media/MDM_Figure_08.png)

## <a name="mdm-"></a>MDM ソリューションのセキュリティ機能

この図は、すべての MDM ソリューションで必要なコア セキュリティ機能を示しています。 考慮すべき主な領域は次のとおりです。

1. モバイル デバイス レベルでのデータ保護に関する考慮事項:
    - データの暗号化
    - データ分類
    - クライアントのプライバシー
    - コンテナリゼーション
    - ポリシーの適用
    - Compliance ポリシー
    - セキュリティ強化
2. 転送中のデータの保護に関する考慮事項:
    - データの暗号化
    - 認証
    - 承認
3. オンプレミス組織で保存中のデータの保護に関する考慮事項:
    - データの暗号化
    - 認証
    - 承認
4. クラウドで保存中のデータの保護に関する考慮事項:
    - データの暗号化
    - 認証
    - 承認

各セクションで説明する作業は、特定のセキュリティ ニーズが、ビジネス要件に最適な MDM ソリューションに関する決定に及ぼす影響を理解するのに役立ちます。

## <a name=""></a>この手順について

ガイドのこのセクションには、12 個の手順があります。 すべてのセクションに目を通す場合、所要時間は約 36 分です。 特定のセクションにジャンプしても構いません。

- [データ保護要件の収集](mdm-gather-data-protection-requirements.md)
- [プライバシー要件の指定](mdm-specify-privacy-requirements.md)
- [アクセス要件の指定](mdm-specify-your-access-requirements.md)
- [インシデント レスポンス要件の作成](mdm-develop-incident-response-requirements.md)
- [データ暗号化の計画](mdm-data-encryption.md)
- [データ分離の計画](mdm-data-segregation.md)
- [モバイル デバイスのセキュリティ強化](mdm-hardening-mobile-devices.md)
- [クライアントのプライバシー](mdm-client-privacy.md)
- [データ分類](mdm-data-classification.md)
- [認証と承認](mdm-authentication-authorization.md)
- [リソースへのアクセス制御](mdm-access-control-resources.md)


