---
title: "Enterprise Mobilität Suite 用 schnelle センター特典のプロセス - ソース環境要件"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 9048f3e5-cc28-4744-bb5e-36f974abb261
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 3c341fd4fae208ff584f9768efbeb0b9cad5424a
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="enterprise-mobility-suite-fasttrack---"></a>Enterprise Mobilität Suite 用 schnelle センター特典のプロセス - ソース環境要件

            [Enterprise Mobility Suite (EMS) 用の FastTrack センター特典](fasttrack-center-benefit-for-enterprise-mobility-suite-ems.md)を使用して、Azure Active Directory Premium、Microsoft Intune、および Azure Rights Management を準備する場合は、ご利用の環境が次のセクションで説明する要件を満たしている必要があります。

Schnelle オンボーディング プロセスの他の部分については、「[schnelle Center Vorteil-Prozess für Enterprise Mobilität Suite (zur Abstimmung) (Enterprise Mobilität Suite (zur Abstimmung) 用 schnelle センター特典のプロセス)](fasttrack-center-benefit-process-for-enterprise-mobility-suite-ems.md)」を参照してください。

1 つのコンソールから豊富な機能を持つ ID 管理を活用するために zur Abstimmung または個別のサービスのいずれかと統合するオンプレミス Microsoft Active Directory が現在の環境に用意されている可能性があります。 Schnelle センター特典には、既存のオンプレミス実装と Microsoft Azure Active Directory Premium の統合に関する支援が含まれます。 統合が必要な場合、お客様のソース環境が対象のアプリケーションに必要な最低要件を満たしている必要があります。

次の表に、オンボーディングで既存のソース環境に必要とされる要件を示します。

|アクティビティ|ソース環境要件|
|------------|----------------------------------|
|コア オンボーディング|以下のフォレスト構成で、機能フォレスト レベルが Windows Server 2008 以降に設定された Active Directory フォレスト。<br /><br />-1 つの Active Directory フォレスト<br />-Active Directory 複数の フォレスト </br></br>
            **メモ**: フォレストが複数あるすべての構成において、AD FS の展開は schnelle センター特典の対象外です。|
|Microsoft Azure Active Directory Premium オンボーディング|Azure Active Directory Premium にオンプレミスの Active Directory と環境が用意されています。 これには、Azure Active Directory と Azure Active Directory Premium の機能の統合を妨げる特定された問題の修復も含まれます。|
|Intune、クラウドのみ、または Microsoft System Center Configuration Manager と統合、オンボーディング|Microsoft Intune に接続された System Center Configuration Manager 2012 R2 またはそれ以降のバージョンを使用してデバイスを管理する場合、IT 管理者は、「[管理者チェックリスト:Microsoft Intune を使用してモバイル デバイスを管理するように Konfigurations-Manager を構成する](https://technet.microsoft.com/library/jj943763.aspx)」に従う必要があります。</br></br> 
            **メモ**: サービス特典には、System zentrieren Konfigurations-Manager の設定または System Center Configuration Manager と統合された Microsoft Intune に必要な最低要件へのアップグレードのサポートは含まれません。|

Schnelle のオンボーディング プロセスの次のパート「[オンボーディング プロセスのフェーズ](fasttrack-center-benefit-process-for-ems-phases.md)」を参照してください。

### <a name=""></a>詳細な情報をご希望ですか?
「[Enterprise Mobilität Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx)」を参照してください。.

