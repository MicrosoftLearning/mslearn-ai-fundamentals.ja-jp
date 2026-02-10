---
lab:
  title: Microsoft Foundry で Computer Vision の使用を開始する
  description: 生成 AI モデルを使って、ビジュアル データを解釈および生成します。
  level: 100
  duration: 30 minutes
---

# Microsoft Foundry で Computer Vision の使用を開始する

この演習では、Microsoft Foundry で生成 AI モデルを使って、ビジュアル データを操作します。

この演習の所要時間は約 **30** 分です。

## Microsoft Foundry プロジェクトを作成する

Microsoft Foundry では "プロジェクト" を使って、AI ソリューションの開発に使われるモデル、リソース、データ、その他の資産を整理します。**

1. Web ブラウザーで [Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開き、Azure の資格情報を使ってサインインします。 初めてサインインすると開くヒントやクイック スタートのペインをすべて閉じ、必要な場合は、左上にある **Foundry** のロゴを使ってホーム ページに移動します。
1. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。 次に、新しいプロジェクトを作成するための画面が表示された場合は、一意の名前を指定して作成します。このときに **[高度なオプション]** 領域を展開して、プロジェクトの設定を次のとおりに指定します。
    - **Foundry リソース**: *AI Foundry リソースに有効な名前を入力します。*
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **[リージョン]**: **[AI Foundry 推奨]** のリージョンのいずれかを選択します。

    ![AI Foundry プロジェクトのホーム ページのスクリーンショット。](./media/0-foundry-project.png)

## 生成 AI モデルを使って画像を分析する

Computer Vision のモデルを使うと、AI システムは画像ベースのデータ (写真、ビデオ、その他の視覚要素など) を解釈できます。 この演習では、意欲的なシェフがビジョン対応モデルを使って食材の画像を解釈して関連するレシピを提案するのを、AI エージェントの開発者が支援する方法について説明します。

1. 新しいブラウザー タブで、**[images.zip](https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/images.zip){:target="_blank"}** `https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/images.zip` をローカル コンピューターにダウンロードします。
1. ダウンロードしたアーカイブをローカル フォルダーに抽出し、それに含まれるファイルを確認します。 これらのファイルは、AI を使って分析する画像です。
1. Microsoft Foundry プロジェクトが含まれるブラウザー タブに戻ります。 次に、**[ビルドの開始]** メニューの **[モデルの参照]** を選んで、Microsoft Foundry のモデル カタログを表示します。
1. `gpt-4.1-mini` モデルを検索し、既定の設定を使ってデプロイします。 デプロイには 1 分ほどかかる場合があります。
1. モデルがデプロイされると開くモデル プレイグラウンド ページを確認します。ここでモデルとチャットできます。

    ![モデル プレイグラウンドのスクリーンショット。](./media/0-model-playground.png)

1. 左側のナビゲーション ウィンドウの下部にあるボタンを使ってそれを非表示にし、作業するスペースを増やします。
1. 左側のペインで、**[指示]** を `You are an AI cooking assistant who helps chefs with recipes.` に設定します
1. チャット ペインの **[画像のアップロード]** ボタンを使って、コンピューター上に抽出した画像のいずれかを選びます。 画像がプロンプト領域に追加されます。

    追加した画像を選んで表示できます。

   ![プロンプトに画像が含まれるチャットのスクリーンショット。](./media/0-image-input.png)

1. `What recipes can I use this in?` のようなプロンプト テキストを入力し、アップロードした画像とテキストの両方を含むプロンプトを送信します。
1. 応答を確認します。これには、アップロードした画像に関連するレシピの提案が含まれているはずです。

   ![画像ベースのプロンプトへの応答を含むチャット アプリのスクリーンショット。](./media/0-image-analysis.png)

1. `How should I cook this?` や `What desserts could I make with this?` などの他の画像を含むプロンプトを送信します

### コードの表示

モデルを使って画像を解釈できるクライアント アプリまたはエージェントを開発するには、OpenAI **Responses** API を使用できます。

1. **[チャット]** ペインで **[コード]** タブを選んでサンプル コードを表示します。
1. 次のコード オプションを選びます。
    - **API**:Responses API
    - **言語**: Python
    - **SDK**:OpenAI SDK
    - **認証**: キー認証

    既定のサンプル コードには、テキストベースのプロンプトのみが含まれています。 画像を分析するプロンプトを送信するには、次に示すように **input** パラメーターを変更して、テキストと画像の両方の内容を含めることができます。

    ```python
    from openai import OpenAI
    
    endpoint = "https://your-project-resource.openai.azure.com/openai/v1/"
    deployment_name = "gpt-4.1-mini"
    api_key = "<your-api-key>"
    
    client = OpenAI(
        base_url=endpoint,
        api_key=api_key
    )
    
    response = client.responses.create(
        model=deployment_name,
        input=[{
            "role": "user",
            "content": [
                {"type": "input_text", "text": "what's in this image?"},
                {"type": "input_image", "image_url": "https://an-online-image.jpg"},
            ],
        }],
    )
    
    print(f"answer: {response.output[0]}")
    ```

    > **ヒント**: 職場または学校アカウントを使って Azure にサインインしていて、Azure サブスクリプションに十分なアクセス許可がある場合は、VS Code for Web でサンプル コードを開いて実行し、画像ベースの入力内容を試すことができます。 サービスの **key** は、(サンプル コードの上にある) モデル のプレイグラウンドの **Code** タブで取得できます。また、画像 **[orange.jpg](https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/orange.jpg){:target="_blank"}** を `https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/orange.jpg`で使用できます。 OpenAI API を使用した画像の分析について詳しくは、[OpenAI のドキュメント](https://platform.openai.com/docs/guides/images-vision#analyze-images)をご覧ください。

## 生成 AI モデルを使って新しい画像を作成する

ここまでは、視覚的な入力を処理する生成 AI モデルの機能を調べてきました。 ここでは、AI シェフ エージェントをサポートするための適切な画像を Web サイト上に置きたいものとします。 モデルで視覚的な出力を生成する方法を見てみましょう。

1. **gpt-4.1-mini** ヘッダーの横にある "戻る" 矢印を使って (またはナビゲーション ウィンドウで **[モデル]** ページを選んで)、プロジェクトでのモデル デプロイを表示します。
1. **[基本モデルをデプロイする]** を選んでモデル カタログを開きます。
1. **[コレクション]** ドロップダウン リストで **[Direct from Azure]** を選び、**[推論タスク]** ドロップダウン リストで **[テキストから画像]** を選びます。 次に、画像生成に使用できるモデルを表示します。

   ![モデル カタログでの画像生成モデルのスクリーンショット。](./media/0-image-generation-models.png)

    > **注**:サブスクリプションで使用できるモデルは異なる場合があります。 さらに、モデルをデプロイする機能は、リージョンでの使用可能性とクォータによって異なります。

1. **FLUX-1-Kontext-pro** モデルを選んでデプロイします。

    お使いのサブスクリプションでモデルをデプロイできない場合は、他の画像生成モデルのいずれかを試してください。**

1. モデルがデプロイされると、画像プレイグラウンドでそれが開きます。
1. 目的の画像を説明するプロンプトを入力します (例: `A chef preparing a meal.`)。生成された画像を確認します。

   ![生成された画像を含む画像プレイグラウンドのスクリーンショット。](./media/0-generated-image.png)

### コードの表示

モデルを使って画像を生成するクライアント アプリまたはエージェントを開発したい場合は、OpenAI API を使用できます。

1. **[チャット]** ペインで **[コード]** タブを選んでサンプル コードを表示します。
1. 次のコード オプションを選びます。
    - **言語**: Python
    - **SDK**:OpenAI SDK
    - **認証**: キー認証

    既定のサンプル コードは次のようになります。

    ```python
    import base64
    from openai import OpenAI
    
    endpoint = "https://your-project-resource.openai.azure.com/openai/v1/"
    deployment_name = "FLUX.1-Kontext-pro"
    api_key = "<your-api-key>"
    
    client = OpenAI(
        base_url=endpoint,
        api_key=api_key
    )
    
    img = client.images.generate(
        model=deployment_name,
        prompt="A cute baby polar bear",
        n=1,
        size="1024x1024",
    )
    
    image_bytes = base64.b64decode(img.data[0].b64_json)
    with open("output.png", "wb") as f:
        f.write(image_bytes)
    ```

## 生成 AI モデルを使ってビデオを作成する

静的な画像に加えて、AI シェフ エージェントの Web サイトにビデオ コンテンツを含めることができます。

1. 画像生成モデルのヘッダーの横にある "戻る" 矢印を使って (またはナビゲーション ウィンドウで **[モデル]** ページを選んで)、プロジェクトでのモデル デプロイを表示します。
1. **[基本モデルをデプロイする]** を選んでモデル カタログを開きます。
1. **[コレクション]** ドロップダウン リストで **[Direct from Azure]** を選び、**[推論タスク]** ドロップダウン リストで **[ビデオ生成]** を選びます。 次に、ビデオ生成に使用できるモデルを表示します。

   ![モデル カタログでのビデオ生成モデルのスクリーンショット。](./media/0-video-generation-models.png)

    > **注**:サブスクリプションで使用できるモデルは異なる場合があります。 さらに、モデルをデプロイする機能は、リージョンでの使用可能性とクォータによって異なります。

1. **Sora** モデルを選んでデプロイします。

    お使いのサブスクリプションでモデルをデプロイできない場合は、他のビデオ生成モデルのいずれかを試してください。**

1. モデルがデプロイされると、ビデオ プレイグラウンドでそれが開きます。
1. 目的のビデオを説明するプロンプトを入力します (例: `A chef in a busy kitchen.`)。生成された画像を確認します。

   ![生成されたビデオを含むビデオ プレイグラウンドのスクリーンショット。](./media/0-generated-video.png)

### コードの表示

モデルを使ってビデオを生成するクライアント アプリまたはエージェントを開発したい場合は、REST API を使用できます。

1. **[チャット]** ペインで **[コード]** タブを選んでサンプル コードを表示します。

    既定のサンプル コードでは、*curl* コマンドを使って REST エンドポイントが呼び出されます。次のようになります。

    ```bash
    curl -X POST "https://your-project-resource.openai.azure.com/openai/v1/video/generations/jobs" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $AZURE_API_KEY" \
    -d '{
        "prompt" : "A video of a cat",
         "height" : "1080",
         "width" : "1080",
         "n_seconds" : "5",
         "n_variants" : "1",
        "model": "sora"
        }'
    ```

## まとめ

この演習では、視覚データを入力として受け入れることができるモデル、テキストの説明に基づいて静的な画像を生成できるモデル、ビデオを生成できるモデルなど、Microsoft Foundry でのビジョン対応モデルの使用について調べました。