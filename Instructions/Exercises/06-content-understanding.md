---
lab:
  title: Microsoft Foundry で Content Understanding を使用してデータを抽出する
---

# Microsoft Foundry で Content Understanding を使用してデータを抽出する

Azure Content Understanding を使用すると、ドキュメント、オーディオ ファイル、ビデオ、画像のマルチモーダル分析を行って情報を抽出することができます。

この演習では、インテリジェント アプリケーションを作成するための Microsoft のプラットフォームである Foundry で、Azure Content Understanding を使用して、請求書から情報を抽出します。 

この演習の所要時間はおよそ **25** 分です。

## コンテンツの解釈用の Microsoft Foundry プロジェクトを作成する

1. Web ブラウザーで、[Microsoft Foundry](https://ai.azure.com) (`https://ai.azure.com`) を開き、Azure 資格情報を使用してサインインします。 初めてサインインする場合に開かれるヒントまたはクイック スタートのペインを閉じ、必要に応じて、左上にある **[Foundry]** ロゴを使用してホーム ページに移動します。次の図のようなページが表示されます (**[ヘルプ]** ペインが表示される場合は閉じます)。

    ![Foundry のホーム ページのスクリーンショット。](./media/ai-foundry-portal.png)

1. ページの下部までスクロールし、**[Azure AI サービスを探す]** タイルを選択します。

    ![[Azure AI サービスを探す] タイルのスクリーンショット。](./media/ai-services.png)

1. [Azure AI サービス] ページで、**[コンテンツの解釈を試す]** を選択します。

    ![[コンテンツの解釈を試す] ボタンのスクリーンショット。](./media/try-content-understanding.png)

1. [コンテンツの解釈] ページで、**[開始するプロジェクトの作成]** を選択します。 次に、**[プロジェクトの作成]** ダイアログで、推奨されるリソースの種類 (**[Foundry リソース]**) を選択します。

1. **[次へ]** ページで、自分のプロジェクトに有効な名前を入力します。 **[詳細オプション]** を選択して、次の設定を指定します。
    - **Foundry リソース**: "Foundry リソースの有効な名前"**
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **[リージョン]**: 次のいずれかの場所を選択してください\*: 
        * 米国西部
        * スウェーデン中部
        * オーストラリア東部

    \**執筆時点では、コンテンツの解釈はこれらのリージョンでのみ使用できます。*

1. **［作成］** を選択します セットアップ プロセスが完了するまで待ちます。 これには数分かかることがあります。

## 請求書から情報を抽出する

1. `https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/refs/heads/main/data/contoso-invoice-1.pdf` から [contoso-invoice-1.pdf](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/refs/heads/main/data/contoso-invoice-1.pdf) をダウンロードします。 

1. [コンテンツの解釈] ページで、**[試してみる]** タブを選択してから、**[請求書データ抽出]** タイルを選択します。

    ![[コンテンツの解釈] の [試してみる] ページのスクリーンショット。](./media/content-understanding-invoice.png)

    サンプルの請求書が提供されます。

1. サンプルの請求書を選択し、**[分析を実行する]** ボタンを使用して、そこから情報を抽出します。 分析が完了したら、結果を表示します。

    ![サンプルの請求書の分析結果のスクリーンショット。](./media/sample-invoice-analysis.png)

1. **[ファイルの参照]** リンクを使用して、前にダウンロードした **contoso-invoice-1.pdf** ドキュメントをアップロードし、そのファイルに対して分析を実行します。

    ![Contoso の請求書の分析結果のスクリーンショット。](./media/contoso-invoice-analysis.png)

    コンテンツの解釈アナライザーは、サンプルとは異なる形式でも、この請求書から情報を抽出できることに注意してください。

1. 抽出されたフィールドが表示されている右側のペインで、**Result** タブを表示して、クライアント アプリケーションに送信される JSON 応答を確認します。 開発者は、この応答を処理し、抽出されたフィールドで何かを行うためのコードを記述します。

    ![Contoso の請求書の分析結果のスクリーンショット。](./media/invoice-analysis-json.png)

## クリーンアップ

コンテンツ解釈サービスの操作が終わったら、不要な Azure コストが発生しないように、この演習で作成したリソースを削除する必要があります。

- Azure portal において、この演習で作成したリソース グループを削除します。
