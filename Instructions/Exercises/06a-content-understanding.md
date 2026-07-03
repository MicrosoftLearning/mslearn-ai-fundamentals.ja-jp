---
lab:
  title: Microsoft Foundry での情報抽出に関する概要
  description: AI モデルを使用して、ビジュアル データから情報を抽出します。
  level: 200
  duration: 25 minutes
  islab: true
  primarytopics:
    - Microsoft Foundry
---

# Microsoft Foundry での情報抽出に関する概要

この演習では、インテリジェント アプリケーションを作成するための Microsoft のプラットフォームである Foundry で、Azure Content Understanding を使用します。

Azure Content Understanding は Foundry サービスの 1 つであり、AI モデルを使用して、構造化されていないマルチモーダル コンテンツ (ドキュメント、画像、ビデオ、オーディオ) を JSON などの構造化された使用可能な出力に変換します。 信頼度スコアとソースの典拠を使用してフィールドの抽出、分類、生成を行って、コンテンツを処理します。

この演習の所要時間はおよそ **25** 分です。

>**注**: この演習では、"新しい" Foundry ポータルのエクスペリエンスを利用します。**

## Microsoft Foundry プロジェクトを作成する

1. Web ブラウザーで [Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開いてビルドを開始します。Azure の資格情報を使ってサインインします。

2. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。 次に、メッセージが表示されたら、一意の名前で "新しいプロジェクト" を作成し、**[高度なオプション]** 領域を展開して、プロジェクトの設定を次のとおりに指定します。**
    - **Foundry リソース**: *AI Foundry リソースに有効な名前を入力します。*
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **リージョン**: [米国西部]、[スウェーデン中部]、[オーストラリア東部]、または**[こちらの一覧](https://learn.microsoft.com/azure/ai-services/content-understanding/language-region-support)** のいずれかのリージョンを選択します {:target="_blank"}******

    > **注**: Azure サブスクリプションのアクセス許可によっては、推奨されるリソースを設定するオプションをオフにする必要がある場合があります。

3. プロジェクトが作成されるまで待ちます。 これには数分かかることがあります。 *新しい* Foundry ポータルでプロジェクトを作成すると、プロジェクト一覧に移動するはずです (*注*: ページをリフレッシュしないと、新しく作成したプロジェクトが表示されない場合があります)。 今作成したプロジェクトを選択すると、次の画像のようなページが開きます。

    ![Foundry プロジェクトのホーム ページのスクリーンショット。](./media/foundry-portal-home.png)

    >**ヒント**: ホーム ページに表示される提案や '入門' チュートリアルは閉じてください。

## 新しい Foundry ポータルでドキュメントから情報を抽出する

1. Foundry ポータルで画面の上部にあるツール バーに移動し、**[ビルド]** を選択します。
2. *[ビルド]* ページで、画面の左側のメニュー (展開が必要な場合があります) で、**[デプロイ]** を選択します。 次に、[デプロイ] ページの上部にある **[AI サービス]** を選択します。**
3. Foundry プレイグラウンドの設定で試すことができる **Content Understanding** 機能を確認します。
   - "Content Understanding - 読み取り": 生テキストの抽出のみ。** "ここにどんなテキストがありますか" という質問に答えます。
   - "Content Understanding - レイアウト": 構造、階層、配置を追加します。** "このコンテンツはどのように整理されていますか" という質問に答えます。
   - *Content Understanding*: フィールドと構造を抽出し、分析情報を生成して、完全なアナライザー機能を提供します。 "このコンテンツは何を意味し、どのように扱えばよいのでしょうか" という質問に答えます。

#### Content Understanding の "読み取り" 機能を試す**

1. **[Content Understanding - 読み取り]** を選択します。 "読み取り" 機能は、コンテンツの解釈の最初のステップであり、テキストの読み取りと抽出を行いますが、まだ構造や意味を理解しようとはしません。**

2. サンプルの **[read_barcode.pdf]** を選択し、**[分析の実行]** ボタンを使用して情報をドキュメントから抽出します。 分析が完了したら、結果を表示します。

    ![サンプルの請求書の分析結果のスクリーンショット。](./media/new-portal-read-barcode.png)

3. [戻る] ボタンを選択して前のページに戻り、他の機能をテストします。

#### Content Understanding の "レイアウト" 機能を試す**

1. [AI サービス] タブで、**[Content Understanding - レイアウト]** を選択します。**

2. サンプルの **[layout_checklist.jpg]** を選択し、**[分析の実行]** ボタンを使用して、そこから情報を抽出します。 分析が完了したら、結果を表示します。

    ![layout_checklist の分析結果のスクリーンショット。](./media/content-understanding-layout-analysis.png)

3. コンテンツ出力で、**[テーブル]** タブを選択します。"レイアウト" アナライザーでコンテンツのテキストと構造の両方をどのようにキャプチャできるかを確認します。**

    ![layout_checklist の分析結果の表のスクリーンショット。](./media/content-understanding-layout-table.png)

4. [戻る] ボタンを選択して前のページに戻り、他の機能をテストします。

#### Content Understanding の他のアナライザー機能を試す

1. [AI サービス] タブで **[Content Understanding]** を選択して、別の Azure Content Understanding アナライザーをテストします。**

2. [Content Understanding] ページで、**[ドキュメント]** モダリティを選択します。**

    ![[ドキュメント モダリティ] が選択されている完全なアナライザーのスクリーンショット。](./media/full-content-analzyer-document.png)

3. [ドキュメント] モダリティの横にあるドロップダウン メニューから [ドキュメント フィールド] を選択します。**** まだ構成されていないモデルをデプロイするように求められた場合は、**[モデルのデプロイ]** を選択します。

    >**ヒント**: "ドキュメント フィールド" およびその他の複雑な抽出ニーズでは、各デプロイが特定のモデルのバージョンまたは機能に関連付けられているため、複数の AI モデルをデプロイする必要があります。** Azure AI Foundry で複数のモデルを使用すると、さまざまな種類の処理タスクをより効果的に処理でき、各ニーズに適したモデルを柔軟に選択できます。

4. ドロップダウン メニューから推奨される [チャットの入力候補モデル] と [埋め込みモデル] を選択します。**** 次に、**[変更の適用]** を選択します。 変更が適用されたら、[構成] パネルを閉じます。**

5. 自身の請求書で完全なアナライザーを使用してみましょう。 新しいブラウザー ウィンドウを開きます。 URL `https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/refs/heads/main/data/content-understanding/contoso-invoice-1.pdf` を入力して、**[contoso-invoice-1.pdf](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/refs/heads/main/data/content-understanding/contoso-invoice-1.pdf){:target="_blank"}** をダウンロードします。

6. Foundry ポータルの Content Understanding プレイグラウンドに戻り、**[ファイルの参照]** リンクを使用して、今ダウンロードした **contoso-invoice-1.pdf** ドキュメントをアップロードします。 **[分析の実行]** を選択し、結果を確認します。 テキストがレンダリングされるだけでなく、そのレイアウトもキャプチャされ、フィールドがまとまりのあるカテゴリに整理されていることに注意してください。  

    ![ドキュメント フィールド アナライザーを使用して Contoso の請求書を分析した結果のスクリーンショット。](./media/contoso-invoice-analysis-document-fields.png)

7. 抽出されたフィールドが表示されている右側のペインで、**[結果]** タブを表示すると、JSON 形式の生の結果が表示されます。 **analyzerID** フィールドを確認します。このフィールドには、使用されたアナライザーの種類が含まれています。 事前構築済みの Content Understanding アナライザーの一覧については、[こちら](https://learn.microsoft.com/azure/ai-services/content-understanding/concepts/prebuilt-analyzers)を参照してください。

     ![請求書に対してドキュメント アナライザーを使用した際の JSON 結果のスクリーンショット。](./media/content-understanding-layout-json.png)

>**ヒント**: [フィールド] タブには、[結果] タブの生の JSON データから得られた情報が、ユーザー フレンドリな形式で表示されると考えてください。****

## Python SDK を使用してコンテンツを抽出する方法を理解する

開発者として、コードを使用してコンテンツから意味を抽出することもできます。 Foundry プレイグラウンドでは、Azure Content Understanding で情報抽出を始めるためのさまざまなサンプル コードが提供されています。

![Foundry プレイグラウンドで提供されているサンプル コードのスクリーンショット。](./media/content-understanding-code-example.png)

1. ドキュメント レイアウト分析のための Python コードについて詳しく見てみましょう。 Content Understanding プレイグラウンドで **[コード]** タブを選択し、**[モダリティ: ドキュメント]** と **[レイアウト]** アナライザーを選択します。 次のコードが提供されます。

    ```python
        import sys
        import json
        
        from azure.ai.contentunderstanding import ContentUnderstandingClient
        from azure.ai.contentunderstanding.models import AnalysisInput, AnalysisResult
        from azure.core.credentials import AzureKeyCredential
        from azure.core.exceptions import AzureError
        from azure.identity import DefaultAzureCredential
        
        
        def main() -> None:
            # Insert the following configurations.
            # 1) AZURE_CONTENT_UNDERSTANDING_ENDPOINT - the endpoint to your Content Understanding resource.
            endpoint = "https://<your-resource>.services.ai.azure.com/"
        
            # 2) CONTENT_UNDERSTANDING_KEY - your Content Understanding API key (optional if using DefaultAzureCredential).
            key = "{{CONTENT_UNDERSTANDING_KEY}}"
        
            # 3) FILE_URL - you can replace this with your own URL.
            file_url = "https://contentunderstanding.ai.azure.com/assets/prebuilt/layout_checklist.jpg"
        
            # ANALYZER_ID - the ID of the analyzer to use.
            analyzer_id = "prebuilt-layout"
        
            # API_VERSION - the API version to use.
            api_version = "2025-11-01"
        
            # Set up Content Understanding client.
            credential = AzureKeyCredential(key) if key and "{{CONTENT_UNDERSTANDING_KEY}}" not in key else DefaultAzureCredential()
            client = ContentUnderstandingClient(endpoint=endpoint, credential=credential, api_version=api_version)
        
            # [START analyze]
            print(f"Analyzing with {analyzer_id} analyzer...")
            print(f"  File URL: {file_url}\n")
        
            try:
                poller = client.begin_analyze(
                    analyzer_id=analyzer_id,
                    inputs=[AnalysisInput(url=file_url)],
                )
                result: AnalysisResult = poller.result()
            except AzureError as err:
                print(f"[Azure Error]: {err.message}")
                sys.exit(1)
            except Exception as ex:
                print(f"[Unexpected Error]: {ex}")
                sys.exit(1)
            # [END analyze]
        
            # [START output_result]
            print("=" * 50)
            print("Analysis result:")
            print("=" * 50 + "\n")
        
            max_display_lines = 50
            result_str = json.dumps(result.as_dict(), indent=2)
            ret_lines = result_str.splitlines()
        
            if len(ret_lines) > max_display_lines:
                print("\n".join(ret_lines[:max_display_lines]))
                print(f"\n {len(ret_lines) - max_display_lines} more lines to be displayed...\n")
            else:
                print(result_str)
            # [END output_result]
        
        
        if __name__ == "__main__":
            main()
    ```

2. コードで何を構成する必要があるかを検討しましょう。
   - Content Understanding リソースのエンドポイント
   - 自分のリソース キー
   - 分析したいファイルの URL
  
3. サンプル コードで提供されている内容のうち、変更の必要があるものを検討しましょう。
   - アナライザー ID ([異なる事前構築済みモデル](https://learn.microsoft.com/azure/ai-services/content-understanding/concepts/prebuilt-analyzers#content-extraction-analyzers)を使用するように変更できます)
   - API バージョン

4. 構成の設定後、コードで Azure Content Understanding と通信するクライアントが作成されます。 コードによって認証方法が決まります。実際の API キーを提供した場合は、そのキーが直接使用されます。 そうでなければ、`DefaultAzureCredential()` にフォールバックし、環境 (たとえば Azure CLI のログイン) から自動的に認証情報が見つかります。 その後、エンドポイント、選択した認証情報、API バージョンを使用してクライアントが作成されます。

    ```python
        # Set up Content Understanding client.
        credential = AzureKeyCredential(key) if key and "{{CONTENT_UNDERSTANDING_KEY}}" not in key else DefaultAzureCredential()
        client = ContentUnderstandingClient(endpoint=endpoint, credential=credential, api_version=api_version)
    ```

5. 次に、コードによって内容が分析されます。 SDK は分析を長期実行の演算として開始します。 関数 `begin_analyze()` は演算の状態 (分析が成功したかどうか) をチェックするポーラーを返します。 SDK のポーラーは `poller.result()` が呼び出されると自動的に全演算を処理します。

    ```python
        # [START analyze]
        print(f"Analyzing with {analyzer_id} analyzer...")
        print(f"  File URL: {file_url}\n")
        
        try:
            poller = client.begin_analyze(
                analyzer_id=analyzer_id,
                inputs=[AnalysisInput(url=file_url)],
            )
            result: AnalysisResult = poller.result()
        except AzureError as err:
            print(f"[Azure Error]: {err.message}")
            sys.exit(1)
        except Exception as ex:
            print(f"[Unexpected Error]: {ex}")
            sys.exit(1)
        # [END analyze]
    ```

6. 分析の出力は、次のコードで JSON としてフォーマットされ、表示されます。

    ```python
        # [START output_result]
        print("=" * 50)
        print("Analysis result:")
        print("=" * 50 + "\n")
    
        max_display_lines = 50
        result_str = json.dumps(result.as_dict(), indent=2)
        ret_lines = result_str.splitlines()
    
        if len(ret_lines) > max_display_lines:
            print("\n".join(ret_lines[:max_display_lines]))
            print(f"\n {len(ret_lines) - max_display_lines} more lines to be displayed...\n")
        else:
            print(result_str)
        # [END output_result]
    ```

    >**注**: 上記のコードの多くは、出力を読みやすく見せます。 その目的は非常にシンプルで、分析結果を出力することです。

7. ステップ 1 のコード全体を実行すると、ラボで先に見たような JSON が返ってきます。 次に例を示します。

    ```json
    {

 "id": "",
 "status": "Succeeded",
 "result": {
  "analyzerId": "prebuilt-layout",
  "apiVersion": "2025-11-01",
  "createdAt": "",
  "warnings": [],
  "contents": [
   {
    "path": "input1",
    "markdown": "",
    "kind": "document",
    "startPageNumber": 1,
    "endPageNumber": 1,
    "unit": "pixel",
    "pages": [
     {
      "pageNumber": 1,
      "angle": 0,
      "width": 2580,
      "height": 3433,
      "spans": [
       {
        "offset": 0,
        "length": 2269
       }
      ],
      "words": [
       {
        "content": "Documents",
        "span": {
         "offset": 2,
         "length": 9
        },
        "confidence": 0.996,
        "source": "D(1,213,217,768,201,768,296,214,310)"
       },
       {
        "content": "to",
        "span": {
         "offset": 12,
         "length": 2
        },
        "confidence": 0.999,
        "source": "D(1,802,200,906,197,906,293,803,295)"
       },
       {
        "content": "Store",
        "span": {
         "offset": 15,
         "length": 5
        },
        "confidence": 0.998,
        "source": "D(1,947,196,1218,189,1219,285,947,292)"
       }
    ...
    ```

    >**ヒント**: 自分の環境で実際にコードを実行するには、サンプル コードの冒頭で共有されたセットアップと構成の指示に従う必要があります。
    ><details>
    ><summary>クリックすると、その指示が表示されます。</summary>
    >Visual Studio Code のようなコード エディターで Python ファイルを作成し、sample.py と名前を付けます。 お使いのマシンに Python 3.9 以降がインストールされていることを確認します。 ターミナルでこのファイルを含むディレクトリに移動します。 `python -m pip install azure-ai-contentunderstanding azure-identity` コマンドを使用して、ターミナルで依存関係をインストールします。 次に、コマンド `python sample.py` を使用して、ターミナルでスクリプトを実行します。
    > </details>

## まとめ

この演習では、Foundry の Azure Content Understanding を調べ、非構造化コンテンツを構造化された使用可能なデータに変換する方法について学習しました。 各アナライザーを前のアナライザーの機能を基に構築し、次の 3 つのアナライザーを試しました。

- **読み取り**: 構造や意味を解釈することなく、ドキュメントから生のテキストを抽出します。"ここにはどんなテキストがありますか" という質問に答えます。
- **レイアウト**: 構造、階層、配置 (テーブルを含む) をキャプチャしてさらに一歩進みます。"このコンテンツはどのように構成されているか" という質問に答えます。
- **ドキュメント フィールド**: 機能の組み合わせを使用してフィールドを抽出し、それらをまとまりのあるカテゴリに整理し、分析情報を生成するアナライザー。"このコンテンツは何を意味し、どのように扱えばよいのでしょうか" という質問に答えます。 このような Content Understanding アナライザーでは、複雑な抽出のニーズに対応するために、追加の AI モデル (チャット入力候補モデルや埋め込みモデルなど) のデプロイが必要になる場合があります。

開発者がどのようにして **Python SDK** を使用して Content Understanding をアプリケーションに統合するのかについても学習しました。これによって、Foundry プレイグラウンドの外部にあるドキュメントをプログラムで分析できるようになります。

> **[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}**<br/>![Anton のアバター。](./media/anton-icon.png)<br/>この演習で取り上げるいくつかのトピックについて疑問がある場合、*[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}* は生成 AI ベースのエージェントであり、AI の概念や Microsoft Foundry について質問することができます。 **[https://aka.ms/azk-anton](https://aka.ms/azk-anton){:target="_blank"}** でアプリを開き、**[構成]** ボタンを使用して Foundry プロジェクトとモデルの詳細を入力します。<br/><br/>"Ask Anton は、サポートされる Microsoft 製品ではなく、Microsoft Learn や AI スキル ナビゲーターのコンポーネントでもありません。AI で何が可能であるかを学ぶ際に探求できる AI エージェントの一例にすぎません。"**<br/><br/>Ask Anton をお試しいただき、"そのご感想をぜひ[こちらのフォーム](https://forms.office.com/r/fC0ndfBQeK){:target="_blank"}にてお寄せください"。****

## クリーンアップ

コンテンツ解釈サービスの操作が終わったら、不要な Azure コストが発生しないように、この演習で作成したリソースを削除する必要があります。

- Azure portal において、この演習で作成したリソース グループを削除します。
