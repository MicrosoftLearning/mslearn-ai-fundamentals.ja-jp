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

![Anton の画像。](./media/anton-icon.png)<br/>**こんにちは、Anton です。**<br/>このラボで、Foundry の Azure Content Understanding を使って画像からデータを抽出する手順を進められるよう、ヒントやコツを使ってサポートします。

より対話型のヘルプが必要な場合は、*[Ask Anton](https://aka.ms/choose-anton){:target="_blank"}* アプリで私とチャットできます。

<details>
<strong><i><a href="https://aka.ms/choose-anton" target="_blank">Ask Anton</a></i></strong> は、AI の概念や Microsoft Foundry の技術に関する質問に答えることができる生成 AI エージェントです。 <code>https://aka.ms/choose-anton</code> から、2 つのバージョンで使用できます。
<ul>
<li><strong>Azure ベースの</strong>: 最適なエクスペリエンスです (Azure サブスクリプションと Foundry プロジェクト内のモデルのデプロイが必要です)。<i></i></li>
<li><strong>ブラウザーベース</strong>: ブラウザーで小さな言語モデルを使用します (機能は制限されています。古い、または低スペックのデバイスでは動作が遅くなるか "ベーシック" モードでしか動作しないことがあります)。<i></i></li>
</ul>
<blockquote><i>Ask Anton は、サポートされている Microsoft 製品、Microsoft Learn、AI スキル ナビゲーターのコンポーネントのいずれでも<u>ありません</u>。</i>
</blockquote>
</details>
<hr/>

この演習の所要時間はおよそ **25** 分です。

## Microsoft Foundry プロジェクトを作成する

1. Web ブラウザーで [Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開いてビルドを開始します。Azure の資格情報を使ってサインインします。
1. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。
1. 既存のプロジェクトがない場合は、プロジェクトを作成するようにダイアログが表示されます。 一意の名前で新しいプロジェクトを作成します。**[詳細オプション]** 領域を展開して、プロジェクトの次の設定を指定します (または、既存のプロジェクトがある場合は選択できます)。
    - **Foundry リソース**: *AI Foundry リソースに有効な名前を入力します。*
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **リージョン**: [米国西部]、[スウェーデン中部]、[オーストラリア東部]、または**[こちらの一覧](https://learn.microsoft.com/azure/ai-services/content-understanding/language-region-support)** のいずれかのリージョンを選択します {:target="_blank"}******

    > ![Anton の画像。](./media/anton-icon.png)<br/>**ヒント**: Azure サブスクリプションのアクセス許可によっては、推奨されるリソースを設定するオプションをオフにする必要がある場合があります。

1. プロジェクトが作成されるまで待ちます。 これには数分かかることがあります。 "新しい" Foundry ポータルでプロジェクトを作成または選択すると、それが次の画像のようなページで開かれます。

    ![Foundry プロジェクトのホーム ページのスクリーンショット。](./media/foundry-portal-home.png)

## *Content Understanding* を使用してドキュメントから情報を抽出する

Azure Content Understanding は Foundry サービスの 1 つであり、AI モデルを使用して、構造化されていないマルチモーダル コンテンツ (ドキュメント、画像、ビデオ、オーディオ) を JSON などの構造化された使用可能な出力に変換します。 信頼度スコアとソースの典拠を使用してフィールドの抽出、分類、生成を行って、コンテンツを処理します。

### Foundry ポータルでコンテンツの解釈プレイグラウンドを開く

1. Foundry ポータルで画面の上部にあるツール バーに移動し、**[ビルド]** を選択します。
1. *[ビルド]* ページで、画面の左側のメニュー (展開が必要な場合があります) で、**[デプロイ]** を選択します。 次に、[デプロイ] ページの上部にある **[AI サービス]** を選択します。**

    > ![Anton の画像。](./media/anton-icon.png)<br/>**ヒント**: 場合によっては、インターフェイスが多少異なり、左側のペインの最上位項目が **[モデル]** で、AI サービスの一覧が **[サービス]** ページに表示されることがあります。

1. **[Content Understanding]** を選択して *Content Understanding* ツールのプレイグラウンドを開きます。

    ![[Content Understanding] プレイグラウンドのスクリーンショット。](./media/content-understanding.png)

### OCR を使用して画像内のテキストを読み取る

たとえば、コンピューターのハードウェアの一部に関連する情報、または情報が印字された他の品目を見つけ出したいとします。 最初の手順として、テキストをデジタル化し、それを使用してインターネットや AI アシスタントで詳細を検索できるようにしました。 光学式文字認識 (OCR) という AI 手法を使用して、画像内のテキストを "読み取る" ことができます。

1. **[OCR/読み取り]** を選択し、**[モダリティ]** 一覧で **[ドキュメント]** が選択され、アナライザーの一覧で **[OCR/読み取り]** が選択されていることを確認してください。

1. 任意のサンプル画像を選択し、**[分析を実行する]** ボタンを使用して画像からテキストを抽出します。 分析が完了したら、結果を表示します。

    ![OCR の分析結果のスクリーンショット。](./media/new-portal-read-barcode.png)

1. 右側のペインで、**[Markdown]**、**[段落]**、**[結果]** のタブをレビューし、アナライザーがドキュメントから読み取ったデータを確認します。

1. `https://aka.ms/pcb-images` から **[pcbs.zip](https://aka.ms/pcb-images){:target="_blank"}** をダウンロードし、zip 形式のアーカイブをローカル コンピューター (の任意のフォルダー) に抽出します。 これらのファイルは、テキストを含むプリント基板の画像です。
1. PCB の画像のいずれかをアップロードし、アプリのメイン コンテンツ領域に表示します。
1. アップロードした画像に対して分析を実行し、結果を確認します。

    ![入荷の分析結果テーブルのスクリーンショット。](./media/content-understanding-pcb.png)

1. プロセスを繰り返して、ダウンロードした他の PCB の画像を分析します。

    > ![Anton の画像。](./media/anton-icon.png)<br/>**ヒント**: 読みやすいテキストを含む画像をアップロードしてみてください。

    *[OCR/読み取り]* アナライザーは、画像からテキストを抽出します。 ただし、時には、画像内のテキストの "レイアウト" に関する追加情報を抽出することが有用な場合もあります。**

1. アナライザーの一覧から **[レイアウト]** を選択します。 次に、任意のサンプル画像を選択し、**[分析を実行する]** ボタンを使用して、そこから情報を抽出します。 分析が完了したら、**[Markdown]**、**[段落]**、**[テーブル]**、**[結果]** の各タブを確認し、ドキュメント内のデータのレイアウトがアナライザーによってどのように解釈されたかを確認します。

    テキストやページのレイアウトを抽出すると、スキャンするドキュメントに一貫性のある明確に定義した構造が必要な場合に役立ちます。 しかし多くの場合、どのテキスト値がどのデータ フィールドに対応するかを識別する必要があるため、より具体的なアナライザーが必要です。

### ドキュメントからフィールドを抽出する

ここで、経費請求ソリューションを自動化するために、スキャンした領収書からデータ フィールドを抽出する必要があるとします。 OCR を使用して画像内のテキストとその位置を特定でき、生成 AI モデルを使用して個々のテキスト値を企業名、電話番号、日付、金額などの特定のデータ フィールドに関連付けることができます。

1. アナライザーの種類の一覧で **[調達]** を選択し、次に **[入荷]** アナライザーを選択します。

    > ![Anton の画像。](./media/anton-icon.png)<br/>**ヒント**: フィールド抽出にはカスタム モデルが必要なため、このプロセス中にモデルのデプロイを促されることがあります。 これが起きた場合は、**[キャンセル]** をクリックしてください。<br><br>分析は実行<u>しないでください</u>。ここでは、事前に準備した分析結果をレビューします。

    ![入荷の分析結果テーブルのスクリーンショット。](./media/content-understanding-receipt.png)

1. 右側のペインで、**[フィールド]**、**[Markdown]**、**[段落]**、**[結果]** のタブを確認し、アナライザーによってドキュメントから抽出されたデータを確認します。

    **[フィールド]** タブには、**[結果]** タブにある未加工の JSON からの情報のユーザーフレンドリなバージョンが表示されます。クライアント アプリケーションはこの方法で分析結果を受け取ります。

## Python SDK を使用してコンテンツを抽出する方法を理解する

開発者として、コードを使用してコンテンツから意味を抽出することもできます。 Foundry プレイグラウンドでは、Azure Content Understanding で情報抽出を始めるためのさまざまなサンプル コードが提供されています。

![Foundry プレイグラウンドで提供されているサンプル コードのスクリーンショット。](./media/content-understanding-code-example.png)

1. ドキュメント レイアウト分析のための Python コードについて詳しく見てみましょう。 Content Understanding プレイグラウンドで、**[入荷]** アナライザーの結果を表示する際に **[コード]** タブを選択します。次のコードが提供されています。

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
        endpoint = "<https://content-project-resource.services.ai.azure.com/>"
    
        # 2) CONTENT_UNDERSTANDING_KEY - your Content Understanding API key (optional if using DefaultAzureCredential).
        key = "{{CONTENT_UNDERSTANDING_KEY}}"
    
        # 3) FILE_URL - you can replace this with your own URL.
        file_url = "{{FILE_URL}}"
    
        # ANALYZER_ID - the ID of the analyzer to use.
        analyzer_id = "prebuilt-receipt"
    
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
    
    if **name** == "**main**":
        main()
    ```

    コードは Foundry リソース内の Content Understanding ツールに接続し、ドキュメント ファイルを *prebuilt-receipt* アナライザーに送信します。 このアナライザーは非同期で動作し、**[結果]** タブに表示された分析結果を JSON 形式で返します。

## まとめ

この演習では、Foundry の Azure Content Understanding を調べ、非構造化コンテンツを構造化された使用可能なデータに変換する方法について学習しました。 各アナライザーを前のアナライザーの機能を基に構築し、次の 3 つのアナライザーを試しました。

- **[読み取り]**: 構造や意味の解釈はせずにドキュメントから未加工のテキストを抽出します。
- **[レイアウト]**: さらに一歩進んで、構造や階層をキャプチャします。
- **[入荷]**: 複数の機能を組み合わせてテキスト値を抽出し、それをデータ フィールドにマッピングするドキュメント固有のアナライザーです。

開発者がどのようにして **Python SDK** を使用して Content Understanding をアプリケーションに統合するのかについても学習しました。これによって、Foundry プレイグラウンドの外部にあるドキュメントをプログラムで分析できるようになります。

## クリーンアップ

コンテンツ解釈サービスの操作が終わったら、不要な Azure コストが発生しないように、この演習で作成したリソースを削除する必要があります。

1. [https://portal.azure.com](https://portal.azure.com) で **Azure portal** を開き、作成したリソースを含むリソース グループを選択します。
1. **[リソース グループの削除]** を選び、**リソース グループの名前を入力**して、確定します。 これでリソース グループが削除されます。

> ![Anton のアバター。](./media/anton-icon.png)<br/>このラボで [*Ask Anton*](https://aka.ms/choose-anton){:target="_blank"} アプリを使用した場合は、[そのエクスペリエンスについてお聞かせください。](https://forms.office.com/r/fC0ndfBQeK){:target="_blank"}
