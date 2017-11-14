---
title: "データ ソースとフローの追加 (Common Data Service) | Microsoft Docs"
description: "追加のデータを取り込んでアプリからフローをトリガーします"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: Y057qUJ2NNk
courseduration: 11m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 42f0d43984c88dc9a5e6ffe67ca3b7ff6cedf8b7
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2017
---
# <a name="add-a-data-source-and-flow-common-data-service"></a>データ ソースとフローの追加 (Common Data Service)
ここまでこのセクションでは、Common Data Service の Case (ケース) エンティティをベースにしてアプリを生成し、生成されたアプリを詳しく確認してその構成をチェックし、いくつかの方法でアプリをカスタマイズしてきました。 このセクションの最後のトピックでは、もう 1 つの標準エンティティを取り込み、Microsoft Flow を使用してメールを送信します。 アプリはフローをトリガーするため、ケースを開いたユーザーは、ケースが更新されると通知を受けるようになります。 このトピックでは特定のシナリオに沿って進めますが、ここで学習したスキルはさまざまな種類のアプリに適用できます。 では、エンティティからはじめましょう。

## <a name="review-entity-relationships"></a>エンティティ間のリレーションシップを確認する
この後 Contact (連絡先) エンティティを追加しますが、はじめに Case (ケース) エンティティと Contact (連絡先) エンティティの間の関係を見てみましょう。 Case (ケース) エンティティのフィールドの 1 つに **CurrentContact** があります。データ型は **Lookup** です。 つまり、このフィールドは別のテーブルと関連した状態で使用されているということです。

![Case (ケース) エンティティのフィールド](./media/learning-case-app-add-source/case-fields.png)

**[Relationships]** (リレーションシップ) タブを見ると、関連するエンティティは**Contact** (連絡先) であることが分かります。 トピックの後半でこのリレーションシップを使用するので、この関係を覚えておいてください。

![Case (ケース) エンティティのリレーションシップ](./media/learning-case-app-add-source/case-relationships.png)

## <a name="add-an-entity-to-the-app"></a>エンティティをアプリに追加する
PowerApps では簡単にデータ ソースを追加できます。 右側のウィンドウで、**[Data sources]** (データ ソース) > **[Add data source]** (データ ソースの追加) の順にクリックまたはタップします。 ここでは、**[Common Data Service]** 接続を選択して、**[Contact]** (連絡先) エンティティを選択します。 **[Connect]** (接続) をクリックまたはタップすると、エンティティがアプリに追加されます。 

![Contact (連絡先) エンティティを追加する](./media/learning-case-app-add-source/contact-entity.png)

この例では別のエンティティからデータを追加していますが、アプリのさまざまなソースからデータを組み合わせることができます。 

## <a name="look-up-contact-information"></a>連絡先情報を検索する
アプリで Contact (連絡先) エンティティ データにアクセスできるようになったところで、実際に使ってみましょう。 冒頭で説明したとおり、ケース更新のタイミングでメールを送信します。 これを実現するには、数式を 2 つとフローを 1 つ使用します。 最初の数式は編集画面、具体的には保存ボタンの OnSelect プロパティに対して使用します。

![アプリの編集画面](./media/learning-case-app-add-source/edit-screen.png)

既定では、このボタンは数式 `SubmitForm(EditForm1)` を使用して、ユーザーがフォーム内のデータを編集したときに更新情報を送信します。 まずは、現在のケースを開いたユーザーの連絡先情報を検索し、その情報をアプリにローカルに格納できるように、数式に情報を追加する必要があります。 

```UpdateContext({contact:LookUp(Contact, ContactId=BrowseGallery1.Selected.CurrentContact.ContactId)}); SubmitForm(EditForm1)```

少し複雑ですが、ビデオの 2:04 から、James がこの数式の詳細をうまく説明してくれています。

## <a name="trigger-a-flow-from-the-app"></a>アプリからフローをトリガーする
これで各ケースの連絡先が分かったので、メールを送信できます。 アプリから直接メールを送信することもできますが、この例では、アプリからフローをトリガーする方法を説明します。 フローはとてもシンプルです。アプリのアクションに基づいてメールを送信するだけです。 ここでフローの詳細には触れませんが、Microsoft Flow にはガイド学習シリーズがあるので、そちらを参照してください。 

![メールを送信するフロー](./media/learning-case-app-add-source/email-flow.png)

アプリに戻ります。はじめにイベントに基づいてフローを呼び出す必要があります。 編集フォームの OnSuccess プロパティを使用して、編集が成功するとフローがトリガーされるようにします。 編集フォームをクリックまたはタップして、リボンで **[Action]** (アクション) > **[Flows]** (フロー) をクリックまたはタップします。 使用するフローを選択します。 

![メールを送信するフロー](./media/learning-case-app-add-source/add-flow-action.png)

フローが編集フォームの OnSuccess イベントに関連付けられ、メールの連絡先を参照できるようになりました。 次の数式は、ケースを開いたユーザーのメール アドレス、件名の行、メールの本文を指定してフローを呼び出します。 

```CaseResolvedEmailConfirmation.Run(contact.EmailPrimary, "Your case has been updated", "Check it out")```

これだけで、アプリにデータ ソースを追加し、メールを送信するフローをトリガーできます。 このセクションのビデオをまだ見ていない場合は、ぜひご覧になってください。 ビデオでは、このトピックで十分に触れなかったことを詳しく説明しています。

## <a name="wrapping-it-all-up"></a>まとめ
このセクションは以上です。 楽しく学習し、多くの知識を得たのではないでしょうか。 エンティティから基本的なアプリを生成することからはじめて、生成されたアプリの詳細を少し確認してその構造について学びました。 アプリのカスタマイズにはかなり時間を割いて、次にデータ ソースを追加して、フローをトリガーする方法を確認しました。 このセクションでは特定のケース管理アプリを構築しましたが、ここで学習したスキルはさまざまな種類のアプリに適用できます。 セクションの冒頭で説明したように、もっと複雑なケース管理アプリについて学習したい場合は、PowerApps Studio for Windows で入手できるテンプレートをチェックしてください。 

次は、アプリの管理に進みます。 管理のセクションでは、アプリを共有しバージョン管理する方法を示し、アプリ、データ、およびその他のリソースのコンテナーとなる環境について説明します。 
