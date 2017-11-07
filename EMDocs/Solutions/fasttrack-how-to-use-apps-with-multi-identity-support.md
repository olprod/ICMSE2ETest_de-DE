---
title: "複数の ID をサポートするアプリケーションを使用する方法"
description: "複数の-ID をサポートするアプリを使用する方法"
keywords: 
author: craigcaseyMSFT
manager: jeffgilb
ms.date: 09/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 586ecd93-b097-42a0-9229-bcf3b781021c
ROBOTS: noindex
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: 57157640b6a4d0161de55819e7a0924b58a71255
ms.sourcegitcommit: 45ffbe57b8a2ff1ba6d26efde7f4e2fee8495593
translationtype: MT
---
# <a name="-id-"></a>複数の-ID をサポートするアプリを使用する方法

Word-このシナリオでは、Microsoft を例として使用しています。 この同じ手順は、Office 365 に含まれる他のアプリに適用できます。
1.  デバイスで**Word**アプリを開きます。 この例では、IOS デバイスを使用しています。
2.  
            Word-文書を作成します。 をタップして、新しい**[新規作成]**

  ![説明文](./media/ft-multiID-1-createDoc.png)

3.  自由に文を入力し、**[保存]**をタップします。 文書を保存する場所として、個人用の場所と職場用の場所という 2 つのオプションが表示されます。 文書が職場用か個人用かをまだ設定していないので、アプリ ポリシーはこの段階では有効ではありません。
4.  文書を**職場用の場所**(OneDrive for Business など) に保存します。 OneDrive for Business は職場用の場所として認識されているので、文書は会社のデータとしてタグが付けられ、ポリシーの制限が適用されます。

  ![説明文](./media/ft-multiID-2-saveDoc.png)

5.  職場用の場所に保存した文書を開き、テキストをコピーします。 個人の**Facebook**アカウントを開いて、コピーしたテキストを貼り付けてみてください。 Facebook 新しい の投稿にコンテンツを貼り付けることはできないはずです。 [貼り付け] オプションは灰色表示になっていませんが、 **[貼り付け]**キーを押しても何も起きません。 これは、ポリシーの制限によって、会社のデータを個人用のアプリで共有できないためです。

  ![説明文](./media/ft-multiID-3-copyText.png)

  ![説明文](./media/ft-multiID-4-pasteInFB.png)
6.  2 次に、手順 と手順 3 を繰り返して、新しい 文書を作成します。 Word 任意の文を入力し、 今回は**[OneDrive - 個人用]**などの個人用の場所に保存します。 文書は個人用とタグ付けされているので、会社のポリシー制限は適用されません。

  ![説明文](./media/ft-multiID-5-createDoc.png)

7.  個人用の場所に保存した文書を開き、テキストをコピーします。 ここでも**[Facebook]**を開き、コピーしたテキストを貼り付けます。 Facebook この文書は個人用とタグ付けされているので、内容を の投稿に貼り付けることもできます。

  ![説明文](./media/ft-multiID-6-copyText.png)

### <a name=""></a>詳細な情報をご希望ですか?
「[Enterprise Mobilität Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx)」を参照してください。.
