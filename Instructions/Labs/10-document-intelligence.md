---
lab:
  title: Document Intelligence Studio でフォーム データを抽出する
---

# Document Intelligence Studio でフォーム データを抽出する

Azure AI Document Intelligence は、フォームとドキュメントから情報を分析して抽出し、次にフィールド名とデータを識別できます。 

Document Intelligence は光学式文字認識 (OCR) を基盤としてどのように構築されているでしょうか? OCR は印刷されたドキュメントや手書きのドキュメントを読み取ることができますが、非構造化形式でテキストを抽出します。これはデータベースへの保存や分析が困難です。 Document Intelligence は、キーと値のペアや表形式の情報などのテキストの構造をキャプチャすることによって、非構造化データの意味を解明します。 

この演習では、レシートのデータを認識するようにトレーニングされた Document Intelligence の事前構築済みモデルを見てみます。 

> **注** Azure AI Document Intelligence は、Azure Form Recognizer の新しい名前です。 Azure portal や Document Intelligence Studio には、Azure Form Recognizer が引き続き表示されることがあります。

## *Document Intelligence* リソースを作成する

Azure AI Document Intelligence は、*Document Intelligence* リソースまたは *Azure AI サービス* リソースを作成することで使用できます。 この演習では、*Document Intelligence* リソースを作成します (まだ持っていない場合)。

1. 別のブラウザー タブで [Document Intelligence Studio](https://formrecognizer.appliedai.azure.com/studio) を開き、Microsoft アカウントでサインインします。
1. **[設定]** を選択し、**[リソース]** タブを選択します。**[新しいリソースを作成]** を選択します。
1. [リソースの作成] ダイアログ ボックスで、次のように入力します。
    - **[サブスクリプション]**: *お使いの Azure サブスクリプション*。
    - **[リソース グループ]**: *一意の名前のリソース グループを選択するか、作成します*。
    - **新しいリソースの名前**:*一意の名前を入力します*。
    - **[場所]**: *リージョンを選択します*。
    - **価格レベル**: *Fee F0 (使用可能な場合。それ以外の場合は Standard S0 を選択)*。
1. **[続行]** を、次に **[完了]** を選択します。 リソースがデプロイされるまで待ちます。

    >**注** リソースがまだ表示されない場合は、ページを **[更新]** することが必要な場合があります。

Document Intelligence Studio を開いたままにします。

## Document Intelligence Studio でレシートを分析する

これで、架空の Northwind Traders 小売企業のレシートを分析する準備ができました。

1. [**https://aka.ms/mslearn-receipt**](https://aka.ms/mslearn-receipt) を選択して、サンプル ドキュメントをコンピューターにダウンロードします。  フォルダーを開きます。 
1. **Document Intelligence Studio** を選択して **[Document Intelligence Studio の利用を始める]** ページに戻り、[Receipts] の **[Try It Out]\(試してみる\)** を選択します。
1. [事前構築済み] ドロップダウン リストで、**[Receipts]** が選択されていることを確認します。
1. **[ファイルを参照する]** を選び、画像を保存したフォルダーに移動します。 レシートの画像を、次に **[開く]** を選択します。 画像が画面の左側に表示されます。

    ![Northwind のレシート。](media/document-intelligence/northwind-receipt.jpg)

1. 右側にある **[分析を実行する]** を選択します。
1. 解析が実行されると、結果が返されます。 サービスが、販売者の名前、住所、電話番号、トランザクションの日時、品目、小計、税金、合計金額などの特定のデータ フィールドを認識しています。 各フィールドの横には、フィールドが正しい確率のパーセンテージが表示されています。

この演習では、Document Intelligence Studio を使用して Document Intelligence リソースを作成しました。 次に、サービスを使用してレシートを分析しました。 返された結果から、Document Intelligence がどれだけ特定のフィールドを識別できて、日常のドキュメントのデータをより簡単に処理できるようにするかを確認しました。 Document Intelligence Studio を閉じる前に、さまざまな言語のレシートを含むサンプル レシートをいくつか試してみてください。

## クリーンアップ

これ以上の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. [Azure portal]( https://portal.azure.com) を開き、作成したリソースを含むリソース グループを選択します。
1. リソースを選択し、**[削除]** を、次に **[はい]** を選択して確定します。 これでリソースが削除されます。

## 詳細情報

この演習では、AI Document Intelligence サービスの一部の機能のみを示しました。 このサービスで実行できる操作の詳細については、[Document Intelligence](https://learn.microsoft.com/azure/ai-services/document-intelligence/overview?view=doc-intel-3.1.0) のページを参照してください。
