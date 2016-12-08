---
title: "ネットワーク接続管理オプション"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 8/1/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bc7cdb8f-3485-45ae-9493-f840ad9ed3ea
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: eac4a658b7baffa3221fbc99d20868bb0c1f16ab
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name=""></a>ネットワーク接続管理オプション

>[!NOTE]
>このトピックは、大規模な設計の考慮事項ガイドの一部です。 ガイドの先頭から開始する場合は、[メイン トピック](mdm-design-considerations-guide.md)を参照してください。 このガイド全体のダウンロード可能なコピーを入手する場合は、[TechNet ギャラリー](https://gallery.technet.microsoft.com/Mobile-Device-Management-7d401582)にアクセスしてください。

インフラストラクチャ次第で、モバイル デバイスはさまざまなインターネット接続サービスから企業のリソースに接続できる可能性があり、それはしばしば VPN で保護されたエンドポイントによって保護されています。


            [Intune](/Intune/deploy-use/wi-fi-connections-in-microsoft-intune) または ConfigMgr との[ハイブリッド展開](https://technet.microsoft.com/library/dn261221.aspx)を使用して Wi-Fi プロファイルを展開することで、Wi-Fi ネットワークをプロビジョニングできます。これにより、ネットワークの範囲内にあるデバイスは、ネットワークに自動接続できます。 たとえば、移動しながら最寄りの Wi-Fi ネットワーク セグメントに接続するようにモバイル デバイスを構成できます。 ユーザーはパスワードの入力またはネットワークの選択の必要はありません。接続が自動的に動作します。


            [Intune](/Intune/deploy-use/vpn-connections-in-microsoft-intune) と [ConfigMgr](https://technet.microsoft.com/library/dn261217.aspx) では、モバイル デバイスに VPN プロファイルを直接展開することもできます。これにより、ユーザーは、余分な構成や手動作業を行わなくても企業リソースにアクセスできます。 さらに、Intune は、リソースの種類やアクセス方法に基づく VPN 接続を自動的に開始するようにモバイル デバイスを構成できます。 ただし、モバイル デバイス オペレーティング システムが異なると構成要件も異なることに注意してください。

3 作業 での確認事項が、企業リソースへのデバイスの接続方法の決定に役に立ちます。 現在、<token>MDM für Office 365</token>はモバイル デバイスについてはワイヤレスおよび VPN ネットワーク リソースの管理をサポートしないことに注意してください。

次の表に、Intune スタンドアロンおよび Intune と Configuration Manager のハイブリッドを使用してワイヤレスおよび VPN-ネットワークを管理する長所と短所を示します。

## <a name="intune-"></a>Intune (スタンドアロン)

**長所**

- すべての主要なモバイル デバイス オペレーティング システム (Android、iOS、Windows 10、Windows 8.x、Windows Telefon) でワイヤレスおよび VPN-プロファイルをサポート 
- Cisco、Juniper、Dell SonicWall、Checkpoint、その他、業界トップ レベルの VPN-接続の種類をサポート
- ワイヤレスおよび VPN プロファイルを SCEP 証明書プロファイルと統合して、セキュリティを強化
- 異なる種類のユーザー、デバイス、デバイス オペレーティング システム、ユーザー グループおよび役割に対してカスタマイズされたワイヤレスおよび VPN プロファイルの構成をサポート
- Windows 10、Windows 8.1、Windows Telefon 8.1、iOS での DNS-名ベースの開始のサポート
- Windows 10 および Windows 8.1 に対するアプリケーション ID に基づく開始のサポート
- VPN-経由で企業ネットワークに自動的に接続するアプリを VPN プロファイルで選択

**短所**

- VPN-プロファイルをサポートするには、オンプレミスの VPN-インフラストラクチャを展開と管理が必要

## <a name="mdm-for-office-365"></a>MDM für Office 365

Office 365 の MDM では Wi-Fi および VPN-ポリシーはサポートされていない

## <a name="-intune-configmgr"></a>ハイブリッド (Intune と Configuration Manager)

**長所**

- Intune スタンドアロンのすべての長所に加え、次の長所がある。
    - VPN-プロファイルは、既存のオンプレミスのエンタープライズ VPN-インフラストラクチャでサポート

**短所**

- VPN-プロファイルをサポートするには、オンプレミスの VPN インフラストラクチャを展開と管理が必要 
- Configuration Manager で[Wi-Fi プロファイル](https://technet.microsoft.com/library/dn408646.aspx)と[VPN プロファイル](https://technet.microsoft.com/library/dn408643.aspx)を管理するには、特定のセキュリティ アクセス許可の付与が必要

モバイル デバイスの電子メール構成管理オプションの詳細は以下を参照してください。

- Intune:[ワイヤレス プロファイル](/Intune/deploy-use/wi-fi-connections-in-microsoft-intune)および[VPN](/Intune/deploy-use/vpn-connections-in-microsoft-intune)プロファイルを有効にする
- Configuration Manager:[ワイヤレス プロファイル](https://technet.microsoft.com/library/dn261221.aspx)および[VPN](https://technet.microsoft.com/library/dn261217.aspx)プロファイルを有効にする
