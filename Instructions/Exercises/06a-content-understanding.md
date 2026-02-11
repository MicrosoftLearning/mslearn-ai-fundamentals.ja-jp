---
lab:
  title: Microsoft Foundry での情報抽出に関する概要
  description: AI モデルを使用して、ビジュアル データから情報を抽出します。
  level: 100
  duration: 40 minutes
---

# Microsoft Foundry での情報抽出に関する概要

Azure Content Understanding を使用すると、ドキュメント、オーディオ ファイル、ビデオ、画像のマルチモーダル分析を行って情報を抽出することができます。

この演習では、インテリジェント アプリケーションを作成するための Microsoft のプラットフォームである Foundry で、Azure Content Understanding を使用して、請求書から情報を抽出します。 次に、REST API を使用して Foundry Tools の Azure Content Understanding を試します。

この演習は約 **40** 分かかります。

>**注**:この演習では、クラシック Foundry ポータルのエクスペリエンスを利用します。 新しい Foundry ポータルを使用している場合は、クラシックに戻す必要があります。 

## コンテンツの解釈用の Microsoft Foundry プロジェクトを作成する

1. Web ブラウザーで、[Microsoft Foundry](https://ai.azure.com) (`https://ai.azure.com`) を開き、Azure 資格情報を使用してサインインします。 初めてサインインする場合に開かれるヒントまたはクイック スタートのペインを閉じ、必要に応じて、左上にある **[Foundry]** ロゴを使用してホーム ページに移動します。次の図のようなページが表示されます (**[ヘルプ]** ペインが表示される場合は閉じます)。

    ![Foundry のホーム ページのスクリーンショット。](./media/ai-foundry-portal.png)

1. ページの下部までスクロールし、**[Azure AI サービスを探す]** タイルを選択します。

    ![[Azure AI サービスを探す] タイルのスクリーンショット。](./media/ai-services.png)

1. [Azure AI サービス] ページで、**[コンテンツの解釈を試す]** を選択します。

    ![[コンテンツの解釈を試す] ボタンのスクリーンショット。](./media/try-content-understanding.png)

1. [コンテンツの解釈] ページで、**[開始するプロジェクトの作成]** を選択します。 次に、**[プロジェクトの作成]** ダイアログで、推奨されるリソースの種類 (**[Foundry リソース]**) を選択します。

    ![分析結果のスクリーンショット。](./media/resource-type.png)

1. **[次へ]** ページで、自分のプロジェクトに有効な名前を入力します。 **[詳細オプション]** を選択して、次の設定を指定します。
    - **Foundry リソース**: "Foundry リソースの有効な名前"**
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **[リージョン]**: 次のいずれかの場所を選択してください\*: 
        * 米国西部
        * スウェーデン中部
        * オーストラリア東部

    \**執筆時点では、コンテンツの解釈はこれらのリージョンでのみ使用できます。*

    ![プロジェクト設定のスクリーンショット。](./media/content-project-settings.png)

1. **［作成］** を選択します セットアップ プロセスが完了するまで待ちます。 これには数分かかることがあります。

## Foundry ポータル (クラシック) で請求書から情報を抽出する

1. [コンテンツの解釈] ページで、**[試してみる]** タブを選択してから、**[請求書データ抽出]** タイルを選択します。

    ![[コンテンツの解釈] の [試してみる] ページのスクリーンショット。](./media/content-understanding-invoice.png)

    サンプルの請求書が提供されます。

1. サンプルの請求書を選択し、**[分析を実行する]** ボタンを使用して、そこから情報を抽出します。 分析が完了したら、結果を表示します。

    ![サンプルの請求書の分析結果のスクリーンショット。](./media/sample-invoice-analysis.png)

1. `https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/refs/heads/main/data/content-understanding/contoso-invoice-1.pdf` から **[contoso-invoice-1.pdf](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/refs/heads/main/data/content-understanding/contoso-invoice-1.pdf) {:target="_blank"}** をダウンロードします。 

1. Foundry で、**[ファイルの参照]** リンクを使用して、前にダウンロードした **contoso-invoice-1.pdf** ドキュメントをアップロードし、そのファイルに対して分析を実行します。

    ![Contoso の請求書の分析結果のスクリーンショット。](./media/contoso-invoice-analysis.png)

    コンテンツの解釈アナライザーは、サンプルとは異なる形式でも、この請求書から情報を抽出できることに注意してください。

1. 抽出されたフィールドが表示されている右側のペインで、**Result** タブを表示して、クライアント アプリケーションに送信される JSON 応答を確認します。 開発者が、この応答を処理し、抽出されたフィールドを利用するためのコードを記述します。

    ![Contoso の請求書の分析結果のスクリーンショット。](./media/invoice-analysis-json.png)

    開発者が REST API を使用して構築したアプリで分析対象のドキュメントを送信することができ、これには POST 操作を使用します。 たとえば、請求書を分析するには次のような cUrl コマンドを使用します。

    ```bash
   curl -i -X POST "{endpoint}/contentunderstanding/analyzers/{analyzerId}:analyze?api-version=2025-11-01" \
      -H "Ocp-Apim-Subscription-Key: {key}" \
      -H "Content-Type: application/json" \
      -d '{
            "inputs":[
              {
                "url": "https://{url_path}/invoice.png"
              }          
            ]
          }'
    ```

    分析は非同期で実行されるため、次のように応答には結果をポーリングして取得するのに使用できる **id** の値が含まれています。

    ```json
   {
      "id": {resultId},
      "status": "Running",
      "result": {
        "analyzerId": {analyzerId},
        "apiVersion": "2025-11-01",
        "createdAt": "YYYY-MM-DDTHH:MM:SSZ",
        "warnings": [],
        "contents": []
      }
    }
    ```

    この ID を使用して結果を取得するには、次のようにクライアントが GET 要求を送信する必要があります。

    ```bash
   curl -i -X GET "{endpoint}/contentunderstanding/analyzerResults/{resultId}?api-version=2025-11-01" \
      -H "Ocp-Apim-Subscription-Key: {key}"
    ```
## クリーンアップ

コンテンツ解釈サービスの操作が終わったら、不要な Azure コストが発生しないように、この演習で作成したリソースを削除する必要があります。

- Azure portal において、この演習で作成したリソース グループを削除します。
