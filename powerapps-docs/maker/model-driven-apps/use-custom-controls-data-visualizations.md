---
title: PowerApps におけるモデル駆動型アプリのデータのビジュアル化のためのカスタム コントロールの使用 | MicrosoftDocs
description: フィールド用カスタム コントロールの使用方法について学習します
ms.custom: ''
ms.date: 06/07/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 0d6064cd-4d38-4fc2-a564-735cb453a4b2
caps.latest.revision: 8
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-custom-controls-for-model-driven-app-data-visualizations"></a>モデル駆動型アプリのデータのビジュアル化のためのカスタム コントロールの使用

このトピックでは、フィールドのカスタム コントロールを構成する方法を説明します。 

カスタム コントロールでは、従来テキストが含含まれるフィールドなどのアプリケーション ユーザー インターフェイス コンポーネントをビジュアル化に変換することができます。 カスタム コントロールは、フィールド、フォーム、ダッシュボード、ビュー、グリッドで構成できます。 たとえば、スライダー コントロールは数値フィールドで構成できます。

   > [!div class="mx-imgBorder"] 
   > ![カスタム スライダー コントロール](media/slider-control.PNG "フィールドのスライダー コントロール")

または編集可能なグリッド コントロールは、ビューに設定できます。 

   > [!div class="mx-imgBorder"] 
   > ![編集可能グリッド コントロール](media/editable-grid-example.png)

別のユーザー定義コントロールを Dynamics 365 の電話またはタブレット PC モバイル アプリ上に表示しながら、1 つの種類のカスタム コントロールを Web ブラウザー クライアント内に表示するように設定することができます。 たとえば、Web ブラウザー クライアント内のフィールドでは数値入力用カスタム コントロールを使用し、電話用アプリではスライダー カスタム コントロールを使用することができます。 カスタマイズを公開した後は、直線スライダー カスタム コントロールを使用するときにコントロールをスライドするなど、コントロールを駆使して値を変換することができます。 ユーザーがフォーム上の従来のフィールドを変更するときと同様、フォームが閉じる時に変更が自動的に保存されます。  
  
## <a name="use-a-custom-control-to-add-visualizations-to-a-field"></a>カスタム コントロールを使用してビジュアル化をフィールドに追加する  
 この手順のステップに従うと、**予算金額**フィールドの既定のラベルとテキスト ボックス フィールドが、営業案件エンティティ上のスライダー カスタム コントロールに変更されます。 同様のステップを使用して、既存のフィールドをカスタム コントロールに置き換え、またはカスタム フィールド用カスタム コントロールを構成することができます。  
  
1.  [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) にサインインします。  

     

2.  **データ**を展開して**エンティティ**を選択し、目的のエンティティを選択して**フォーム** タブを選択します。  
  
2.  営業案件エンティティの **主要** フォームなどのフォームを開きます。 
  
3.  フォーム エディターで、営業案件のメイン フォーム上の**予算金額**フィールドなどの、カスタム コントロールを追加するフィールドをダブルクリックします。 または、カスタム フィールドを作成することができます。 
  
4.  **フィールドのプロパティ**ページで、**コントロール**タブを選択してから、**コントロールの追加**を選択します。  
  
5.  コントロールの追加ページで、ここに示す**線形スライダー** コントロールなどの、目的のコントロールを選択してから、**追加**を選択します。  

   > [!div class="mx-imgBorder"] 
   > ![線形スライダー コントロールの追加](media/add-slider.PNG "線形スライダー コントロールの追加")  
  
6.  コントロールを表示するクライアントを選択します。  
  
    - **Web**。 任意の Web ブラウザーからカスタム コントロールを使用できるようにするには、コントロールの隣にある **Web** オプションを選択します。 **Web** オプションの設定には PC、Mac、およびモバイル デバイス上の Web ブラウザー内でのコントロールの表現も含まれることに注意してください。  
  
    - **電話**:  Dynamics 365 for phones を実行する電話でカスタム コントロールを利用可能にするには、コントロールの横の**電話**オプションを選択します。  
  
    - **タブレット PC**。 Dynamics 365 for tablets を実行するタブレット PC デバイスでカスタム コントロールを利用可能にするには、コントロールの横の**タブレット PC** オプションを選択します。  
  
   > [!div class="mx-imgBorder"] 
   > ![クライアント アプリを選択してカスタム コントロールを表示する](media/choose-client.png "クライアント アプリを選択してカスタム コントロールを表示する")  
  
7.  **最小**、**最大**、および**ステップ**の横の ![カスタム コントロール プロパティの編集アイコン](media/ccf-pencil-icon.png "カスタム コントロール プロパティの編集アイコン") 鉛筆アイコンを選択して、以下に説明されるプロパティ オプションを設定してから、**OK** を選択します。  
  
   > [!div class="mx-imgBorder"] 
   > ![カスタム コントロールのプロパティを追加](media/ccf-add-properties.png "カスタム コントロールのプロパティを追加")
  
   - **最小**。 許容される最小値を設定します。 入力する静的な値をバインド、または既存のフィールドに値をバインドすることができます。 この例で、**静的な値にバインド**は**通貨**で、入力することができる最小値は [*ゼロ*] です。  
  
       - **静的な値にバインド**。 整数 (Whole.None)、通貨、浮動小数点数 (FP)、または小数などの、データの種類を選択します。 次に、フィールドで許容される最小値を示す数を入力します。  
  
       - **フィールドの値にバインド**。 許容される最小値として使用されるフィールドを一覧から選択します。  
  
   - **最大**。 フィールドの許容される最大値を設定します。 最小値と同様に、以前説明したように、入力する静的値をバインドまたは既存のフィールドに値をバインドすることができます。 この例で、**静的な値にバインド**は**通貨**で、入力することができる最大値は **1,000,000,000** です。  
  
   - **ステップ**。 これは、現在の値に対して追加または差し引くときにの増加または減少する単位を表します。 たとえば、予算金額の場合、100 ドルの increments\decrements を選択することができます。  
  
   - **既定のコントロールを表示しない**。 このオプションを選択するとコントロールを非表示にするため、カスタム コントロールをサポートしないすべてのクライアントでコントロールもデータも表示されません。 従来の Dynamics 365 Web クライアントでは大半のカスタム コントロールをサポートしないことに注意してください。 既定では、このオプションは選択されず、従来の Dynamics 365 Web クライアントは既定の、通常はテキスト ベースのコントロールを表示します。  
  
       > [!NOTE]
       >  既定のコントロールは、コントロール名に続く **(既定)** で識別されます。  
       >   
       > > [!div class="mx-imgBorder"] 
       > > ![既定のコントロール](media/default-control.png "既定のコントロール")  
  
8.  **OK** を選択して、**フィールドのプロパティ** ページを閉じます。  
  
9. カスタマイズをアクティブにするには、エンティティ フォーム上で**保存**を選択してから、**公開**を選択します。  
  
10. **保存して閉じる**を選択してフォーム エディターを閉じます。  
  
### <a name="see-the-custom-control-in-action"></a>アクション中のカスタム コントロールを表示  
 前の例の営業案件フォームなどの、カスタム コントロールを持つフィールドを含むレコードをオープンし、フィールドが変更される様子を確認します。  
  
   > [!div class="mx-imgBorder"] 
   > ![フォーム上に表示されるスライダー コントロール](media/slider-control.PNG "フォーム上に表示されるスライダー コントロール")  
  
 フィールドはテキスト フィールドではなくスライダー コントロールとして表示されるようになりました。 

## <a name="use-the-editable-grid-control-on-a-view-or-sub-grid"></a>ビューまたはサブグリッドで編集可能なグリッド コントロールを使用します。

編集可能なグリッドを使用すると、ユーザーは、Web アプリ、タブレット PC、電話を使用している場合でもビューおよびサブグリットから直接豊富なインライン編集を実行できます。 詳細情報: [編集可能グリッド カスタム コントロールを使用してグリッド (リスト) を編集可能にする](make-grids-lists-editable-custom-control.md) 
  
## <a name="next-steps"></a>次のステップ  
[フィールドの作成および編集](../common-data-service/create-edit-fields.md)
