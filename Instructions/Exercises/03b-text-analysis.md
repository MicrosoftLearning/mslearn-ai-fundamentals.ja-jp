---
lab:
  title: Microsoft Foundry でテキスト分析を開始する
  description: Microsoft Foundry を使用して、さまざまな種類のテキスト分析を試します。
  level: 200
  duration: 25 minutes
  islab: true
  primarytopics:
    - Microsoft Foundry
---

# Microsoft Foundry でテキスト分析を開始する

この演習では、Microsoft の AI アプリケーション作成用プラットフォームである **Microsoft Foundry** を使って、一般的な "テキスト分析手法" を調べます。**

Foundry でテキストを分析するには、"2 つのアプローチ" があります。自然言語プロンプトを使って幅広いタスクを処理する**汎用 AI モデル**と、特定のタスクについての構造化された確定的な結果を返す**専用言語ツール**です。** 両方を調べると、各アプローチを使用すべきときをより明確に理解できます。

この演習の最初の部分では、Foundry ポータルのチャット プレイグラウンドで汎用 AI モデルを使います。 この演習の 2 番目の部分では、Foundry ツールでの Azure Language の機能をいくつか調べます。

この演習は約 **20** 分かかります。

## Microsoft Foundry でプロジェクトを作成する

1. Web ブラウザーで [Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開いてビルドを開始します。Azure の資格情報を使ってサインインします。

2. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。 次に、新しいプロジェクトを作成するための画面が表示された場合は、一意の名前を指定して作成します。このときに **[高度なオプション]** 領域を展開して、プロジェクトの設定を次のとおりに指定します。
    - **Foundry リソース**: *AI Foundry リソースに有効な名前を入力します。*
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **リージョン**: **[こちらの一覧](https://learn.microsoft.com/azure/foundry/openai/how-to/responses#region-availability)**{:target="_blank"}にある、**AI Foundry の推奨**リージョンのいずれかを選択します

    > **注**: Azure サブスクリプションのアクセス許可によっては、推奨されるリソースを設定するオプションをオフにする必要がある場合があります。

3. **［作成］** を選択します プロジェクトが作成されるまで待ちます。 これには数分かかることがあります。 "新しい" Foundry ポータルでプロジェクトを作成または選択すると、それが次の画像のようなページで開かれます。

    ![Foundry プロジェクトのホーム ページのスクリーンショット。](./media/foundry-portal-home.png)

    >**注意**: プロジェクトの Foundry ホーム ページにアクセスするには、クイック スタート ペインをすべて閉じてください。

## 汎用 AI モデルのテキスト分析機能を調べる

まず、チャット インターフェイスを使用して、プロンプ​​トを生成 AI モデルに送信し、一般的なテキスト分析タスク (テキストの要約) を実行してみましょう。

1. これで、モデルを探索する準備ができました。 **[検出]** ページで **[モデル]** タブを選択して Microsoft Foundry モデル カタログを表示します。

    ![AI Foundry モデル カタログのスクリーンショット。](./media/models_page.png)

2. `gpt-5-mini` モデルを検索して選択すると、そのモデルの特徴と機能を説明するページが表示されます。

    ![既定の設定のデプロイ オプションが強調されている gpt-5-mini モデル ページのスクリーンショット。](./media/gpt-5-mini_page.png)

3. **[デプロイ]** ボタンを使い、"既定の設定" を使ってモデルをデプロイします。** デプロイが完了するまで待ちます。 デプロイが完了するとチャット プレイグラウンドに自動的に移動し、そこでモデルの機能をテストできます。

### テキストを要約する

**感情分析**は、一般的な "自然言語処理" (NLP) タスクです。** これは、テキストが肯定的、中立的、または否定的な感情を伝えるかどうかを判断するために使用されます。レビュー、ソーシャル メディアの投稿、その他の主観的なドキュメントを分類するのに役立ちます。

1. [チャット プレイグラウンド] ページで左側のナビゲーション ウィンドウの下部にあるボタンを使ってそれを非表示にし、作業するスペースを増やします。
1. 左側のペインで、既定の **[指示]** を次に設定します。

    ```
   You are an AI assistant that analyzes and summarizes text.
    ```

    ここで、コンピューター業界誌で、1980 年代に発売されたホーム コンピューターのレビューなどの古い記事を見つけたとします

1. 次のプロンプトを入力します (Ctrl + Enter キーを押すと改行できます)。

    ```
   Summarize this review as a single short paragraph:

   Commodore 64: A Strong Contender in the Home Computer Market

   Commodore's long-awaited Commodore 64 has finally arrived on dealers' shelves, and first impressions suggest that the company may have another substantial success on its hands. Priced aggressively and boasting a full 64K of RAM, the machine offers specifications that would have seemed remarkable in a home computer only a short time ago. Its colourful graphics and impressive sound capabilities place it among the most capable entertainment-oriented systems currently available.

   Particularly noteworthy is the SID sound generator, which produces effects and musical output far beyond what users have come to expect from machines in this price bracket. Software houses are already expressing strong interest in the platform, and the combination of advanced graphics and sound should make the Commodore 64 an attractive proposition for both game developers and serious hobbyists alike.

   The machine is not without its shortcomings, however. The keyboard, while serviceable, lacks the solid feel of some competing systems, and Commodore's documentation will do little to reassure newcomers to computing. Furthermore, prospective purchasers may wish to consider the total cost of ownership, as disk drives and other peripherals remain relatively expensive. Nevertheless, the Commodore 64 enters the market as one of the most compelling home computers currently available and is likely to be a significant force in the months ahead.
    ```

    モデルによって、レビューの要約が生成されます。

    ![チャット プレイグラウンドのテキスト要約結果のスクリーンショット。](./media/text_summary.png)

    大規模言語モデル (LLM) は、自然言語処理やテキスト分析を起源とする機械学習技術に基づいて構築されており、テキストの要約、名前のある実体 (人名や地名など) の抽出、そしてセンチメント、トピック、スタイルなどの要素に基づく文書の分類を得意とします。

## 特殊な言語分析ツールを使用する

多くの場合、一般的な生成 AI ワークロード用にトレーニングされた言語モデルを使って優れたテキスト分析ジョブを実行できますが、より特殊なツールをエージェントで使うと、さらに正確な予測結果を得られる場合があります。

**Foundry Tools の Azure Language** は統計的技法を使って構造化された決定論的結果を返す専用のアナライザーを備えており、自動化されたパイプラインでの一貫性のある出力に最適です。

1. Foundry ポータルで画面上部のメニューに移動し、**[ビルド]** を選びます。

1. *[ビルド]* ページで、画面の左側にあるメニューに移動します (展開が必要な場合があります)。 メニューで **[デプロイ]** を選択します。 次に、*[デプロイ]* ページの上部にある **[AI サービス]** を選択します。

    Microsoft Foundry Tools には、音声、翻訳、言語、コンテンツの解釈の一般的なワークロードをサポートする複数の AI サービス (旧 Microsoft Cognitive Services) が含まれています。

    ![Foundry の AI サービス ページのスクリーンショット。](./media/ai_services.png)

    > **ヒント**: 場合によっては、インターフェイスが多少異なり、左側のペインの最上位項目が **[モデル]** で、AI サービスの一覧が **[サービス]** ページに表示されることがあります。

1. 使用可能なサービスに注意してください。これには言語検出や PII 編集のための Azure Language サービスが含まれます。

### 言語を検出する

テキストが複数の言語のいずれかである可能性があるシナリオでは、多くの場合、分析ワークフローの最初のステップは、後続の処理に最適なモデルまたはエージェントにテキストをルーティングできるよう、主言語を決定することです。

1. AI サービスの一覧で、**[Azure Language - 言語検出]** アナライザーを選びます。
1. **[入力テキスト]** の一覧で、提供されているサンプル ドキュメントの 1 つを選びます。 次に、**[検出]** ボタンを使って、サンプルが記述されている言語を検出します。

    ![プレイグラウンドで検出された言語のスクリーンショット](./media/language_detection.png)

1. 検出された言語の詳細を確認した後、**[編集]** ボタン アイコンを使用して、入力テキストを再び編集可能にします。 次のことができるようになりました。
    - 別のサンプルを選びます。
    - 独自のテキストを入力します。
    - テキスト ファイルをアップロードする。

   たとえば、あるヴィンテージ コンピューターを見つけ、その歴史に興味を持ったとしましょう。 コンピューターのケースに次のテキストが書かれたラベルを見つけました。 そのテキストを入力し、それが記述されている言語を検出します。

    ```
   CPC 464
   Art.-Nr.: 31020
   Serien-Nr.: 464-87-041256
   220–240 V ~ 50 Hz
   40 W
   Hergestellt in Korea
   SCHNEIDER RUNDFUNKWERKE AG
   Türkheim/Unterallgäu
   Bundesrepublik Deutschland
    ```

    > **ヒント**: さらに詳しく調べる場合は、Foundry Tools の [AI サービス] ページに **Text Translator** サービスが含まれており、それを使用してテキストを翻訳することができます。

### テキスト内の PII を識別する

プライバシー ポリシーと法律を遵守するため、多くの場合、組織は名前、住所、電話番号、メール アドレス、その他の個人の詳細などの**個人を特定できる情報 (PII)** を検出してリダクトする必要があります。

1. [言語検出プレイグラウンド] ページの **[タイプ]** ドロップダウン リストで **[テキスト PII 抽出]** を選択します (または、AI サービスの一覧に戻って **[Azure Language - テキスト PII 抽出]** を選択します)。
2. **[入力テキスト]** の一覧で、提供されているサンプル ドキュメントの 1 つを選びます。 次に、**[検出]** ボタンを使って、テキスト内の PII の値を検出します。

    ![プレイグラウンドで検出された PII のスクリーンショット](./media/pii_extraction.png)

3. 検出された PII の詳細を確認した後、**[編集]** ボタンを使用して、入力テキストを再び編集可能にします。 次のことができるようになりました。
    - 別のサンプルを選びます。
    - 独自のテキストを入力します。
    - テキスト ファイルをアップロードする。

    たとえば、購入したヴィンテージ コンピューターの箱の中に次の請求書を見つけたとします。

    ```
   Tailspin Toys Ltd
   Invoice
   14 September 1984
    
   Customer:
     Margaret Ellis
     128 High Street, Reading, Berkshire RG1 2AB
     Telephone: 021 685 4215
    
   Item: ZX Spectrum 48K home computer (includes power supply, RF lead, and user manual)
   Price: £79.00
   Payment received:  £79.00
    ```

    このテキストを入力し、その中に含まれている個人を特定できる情報を見つけ出します。

4. 独自の入力で実験します。 Azure Language では、PII の広範な一覧を認識できます。 クラスの全リストは[ここ](https://learn.microsoft.com/azure/ai-services/language-service/personally-identifiable-information/concepts/entity-categories-list)で確認できます。 そのようなエンティティの一部を次に示します。

    - 人名
    - 電子メール アドレス
    - 電話番号
    - 番地

### サンプル コードを確認する

Foundry には、Azure Language のいくつかの機能のサンプル コードが用意されています。 サンプル コードを使って、独自のクライアント アプリケーションの作成を開始できます。

1. 右側の **[コード]** タブを選んで、次のような PII 識別のサンプル コードを表示します。

    ```python
   key = "<your-api-key>"
   endpoint = "https://ai-resrce.cognitiveservices.azure.com/"
    
   from azure.ai.textanalytics import TextAnalyticsClient
   from azure.core.credentials import AzureKeyCredential
    
   # Authenticate the client using your key and endpoint 
   def authenticate_client():
        ta_credential = AzureKeyCredential(key)
        text_analytics_client = TextAnalyticsClient(
                endpoint=endpoint, 
                credential=ta_credential)
        return text_analytics_client
    
   client = authenticate_client()
    
   # Example method for detecting sensitive information (PII) from text 
   def pii_recognition_example(client):
        documents = [
            "$documents"
        ]
        response = client.recognize_pii_entities(documents, language="en")
        result = [doc for doc in response if not doc.is_error]
        for doc in result:
            print("Redacted Text: {}".format(doc.redacted_text))
            for entity in doc.entities:
                print("Entity: {}".format(entity.text))
                print(" Category: {}".format(entity.category))
                print(" Confidence Score: {}".format(entity.confidence_score))
                print(" Offset: {}".format(entity.offset))
                print(" Length: {}".format(entity.length))
   pii_recognition_example(client)
    ```

>**ヒント**: コードをコピーし、好みの Python 開発環境 (Visual Studio Code など) で実行できます。 Azure Language エンドポイントとキーの環境変数を作成する必要があります。コード サンプル ウィンドウで確認できます。

## まとめ

この演習では、生成 AI モデルと Foundry の Azure Language ツールを使用してテキストを分析する方法を調べました。 多くのシナリオでは、生成 AI モデルのネイティブ言語機能によって、必要なすべての自然言語処理機能が提供されます。 より特殊なシナリオでは、Azure Language ツールにより、NLP タスク専用のサービスが提供されます。

> **[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}**<br/>![Anton のアバター。](./media/anton-icon.png)<br/>この演習で取り上げるいくつかのトピックについて疑問がある場合、*[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}* は生成 AI ベースのエージェントであり、AI の概念や Microsoft Foundry について質問することができます。 **[https://aka.ms/azk-anton](https://aka.ms/azk-anton){:target="_blank"}** でアプリを開き、**[構成]** ボタンを使用して Foundry プロジェクトとモデルの詳細を入力します。<br/><br/>"Ask Anton は、サポートされる Microsoft 製品ではなく、Microsoft Learn や AI スキル ナビゲーターのコンポーネントでもありません。AI で何が可能であるかを学ぶ際に探求できる AI エージェントの一例にすぎません。"**<br/><br/>Ask Anton をお試しいただき、"そのご感想をぜひ[こちらのフォーム](https://forms.office.com/r/fC0ndfBQeK){:target="_blank"}にてお寄せください"。****

## クリーンアップ

Microsoft Foundry の調査が完了したら、不要になったリソースをすべて削除します。 これにより、不要なコストが発生することを防ぎます。

1. [https://portal.azure.com](https://portal.azure.com) で **Azure portal** を開き、作成したリソースを含むリソース グループを選択します。
1. **[リソース グループの削除]** を選び、**リソース グループの名前を入力**して、確定します。 これでリソース グループが削除されます。
