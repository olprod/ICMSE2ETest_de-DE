---
title: "条件付きアクセスのエンド ユーザー エクスペリエンス"
description: "デバイスを登録したり、準拠に関する問題を解決したりするエンド ユーザー エクスペリエンスです。"
keywords: 
author: craigcaseyMSFT
manager: swadhwa
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e186dd2-e17c-40d8-b160-48038b2c6593
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 7c0722f510fa9ea669e6828d90d08cf2b0e94d6c
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-"></a>条件付きアクセスのエンド ユーザー エクスペリエンス
ユーザーがデバイスで最初に電子メールにアクセスするとき、またはその後同期を試みるとき、デバイスの登録状態とコンプライアンス対応状態がチェックされます。 登録やコンプライアンス対応の問題の修正は、画面の指示に従って処理します。 エンド ユーザーは、ヘルプ デスクに連絡する必要なく、デバイスの登録とコンプライアンス対応に必要な手順を確認できます。

-   
            **デバイスが登録されていない場合**、アクセスが拒否されたことがサインイン ページに表示され、登録が求められます。 登録時、デバイスは Azure Active Directory に自動的に登録されます。 Intune は、デバイスのコンプライアンス対応を確認し、非対応の問題を解決する修復の手順を提供します。 デバイスが対応すると、Intune は、Azure Active Directory にデバイスのコンプライアンス対応状態を設定します。

-   
            **デバイスは登録されているがポリシーに準拠していない場合**、問題を修復する手順のリンクがデバイスに送信されます。 エンド ユーザーが問題 (パスワードの設定、暗号化など) を修正すると、コンプライアンス ポリシーを管理する Intune で、Azure AD のデバイスのコンプライアンス対応状態が更新されます。

デバイスが登録済みで対応していると評価されると、電子メールの同期が数分内に始まります。

## <a name="android"></a>Android


            [このトピック](end-user-experience-conditional-access-android.md)では、条件付きアクセスが有効になり、エンド ユーザーが最初に Android モバイル デバイスで電子メールにアクセスしようとしたときの登録操作について説明します。

## <a name="ios"></a>iOS


            [このトピック](end-user-experience-conditional-access-ios.md)では、条件付きアクセスが有効になり、エンド ユーザーが最初に iOS モバイル デバイスで電子メールにアクセスしようとしたときのユーザー エクスペリエンスについて説明します。

## <a name="windows-phone"></a>Windows Phone


            [このトピック](end-user-experience-conditional-access-winphone.md)では、条件付きアクセスが有効になり、エンド ユーザーが Windows Phone で電子メールにアクセスしようとしたときのエンド ユーザー エクスペリエンスについて説明します。
