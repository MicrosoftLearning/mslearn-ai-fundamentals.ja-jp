---
lab:
  title: Azure OpenAI Service を探索する
---

# Azure OpenAI を確認する

Azure OpenAI Service は OpenAI によって開発された生成 AI モデルを Azure プラットフォームに導入します。これにより、Azure クラウド プラットフォームによって提供されるサービスのセキュリティ、スケーラビリティ、統合の恩恵を受ける強力な AI ソリューションを開発できるようになります。

この演習では、Azure OpenAI Service を確認し、それを使用して生成 AI モデルのデプロイと実験を行います。

この演習には、約 **25** 分かかります。

## 開始する前に

テキストやコードのモデルと、DALL-E イメージ生成モデルの両方に対する Azure OpenAI Service へのアクセスが承認されている Azure サブスクリプションが必要です。

- 無料の Azure サブスクリプションにサインアップするには、[https://azure.microsoft.com/free](https://azure.microsoft.com/free) にアクセスしてください。
- Azure OpenAI Service へのアクセスを要求するには、[https://aka.ms/oaiapply](https://aka.ms/oaiapply) にアクセスしてください。

## Azure OpenAI リソースをプロビジョニングする

Azure OpenAI モデルを使用する前に、Azure サブスクリプションに Azure OpenAI リソースをプロビジョニングする必要があります。

1. [Azure portal](https://portal.azure.com) にサインインします。
2. 次の設定で **Azure OpenAI** リソースを作成します。
    - **[サブスクリプション]**: *Azure OpenAI Service へのアクセスが承認されている Azure サブスクリプション。*
    - **[リソース グループ]**: *既存のリソース グループを選択するか、任意の名前を使用して新規に作成します。*
    - **[リージョン]**: 米国東部\*
    - **[名前]**: "*希望する一意の名前*"
    - **価格レベル**: Standard S0

    > \* リージョンによってモデルの可用性とクォータは異なります。 この演習では、テキスト生成には GPT-35-Turbo モデルを使い、画像生成には DALL-E モデルを使います。どちらも米国東部でサポートされています。

3. デプロイが完了するまで待ちます。 次に、Azure portal でデプロイされた Azure OpenAI リソースに移動します。

## Azure OpenAI スタジオを調べる

Azure OpenAI Studio を使用して、Azure OpenAI Service でモデルをデプロイ、管理、探索できます。

1. Azure OpenAI リソースの **[概要]** ページで、 **[探索]** ボタンを使用して、新しいブラウザー タブで Azure OpenAI Studio を開きます。または、[Azure OpenAI Studio](https://oai.azure.com/) に直接移動します。

    Azure OpenAI Studio を初めて開くと、次のようになります。

    ![Azure OpenAI Studio のスクリーンショット。](./media/generative-ai/ai-studio.png)

1. 左側のペインに使用可能なページが表示されます。 上部で、いつでもホーム ページに戻ることができます。 さらに、OpenAI Studio には次のことができる複数のページがあります。
    - "プレイグラウンド" でモデルを試す。**
    - モデル デプロイとデータを管理する。

## 言語生成用のモデルをデプロイする

自然言語生成を実験するには、まずモデルをデプロイする必要があります。

1. **[モデル]** ページで、Azure OpenAI サービス インスタンスで使用可能なモデルを表示します。
1. **[展開可能]** 状態が **[はい]** である **gpt-35-turbo** モデルのいずれかを選択し、**[デプロイ]** を選択します。

    ![Azure AI Studio の [モデル] ページのスクリーンショット。](./media/generative-ai/deploy-model.png)

1. 次の設定で新しいデプロイを作成します。
    - **モデル**: gpt-35-turbo
    - **モデル バージョン**: 既定値に自動更新
    - **デプロイ名**:"モデル デプロイの一意の名前"**
    - **詳細オプション**
        - **コンテンツ フィルター**: 既定
        - **デプロイの種類**:Standard
        - **1 分あたりのトークンのレート制限**: 5K\*
        - **動的クォータを有効にする**: 有効

    > \* この演習は、1 分あたり 5,000 トークンのレート制限内で余裕を持って完了できます。またこの制限によって、同じサブスクリプションを使用する他のユーザーのために容量を残すこともできます。

## [チャット] プレイグラウンドを使用してモデルを操作する**

モデルをデプロイしたので、[チャット] プレイグラウンドで使用して、チャット インターフェイスで送信するプロンプトから自然言語出力を生成できます。**

1. [Azure OpenAI Studio](https://oai.azure.com/) の左側のペインで、 **[チャット]** プレイグラウンドに移動します。

    [チャット] プレイグラウンドには、次に示すように、デプロイされたモデルと対話できるチャットボット インターフェイスが用意されています。**

    ![Azure OpenAI Studio の [チャット] プレイグラウンドのスクリーンショット。](./media/generative-ai/chat-playground.png)

1. **[構成]** ペインで、モデル デプロイが選択されていることを確認します。
1. **[アシスタント セットアップ]** ペインで、**[既定]** のシステム メッセージ テンプレートを選択し、このテンプレートが作成するシステム メッセージを表示します。 システム メッセージは、チャット セッションでのモデルの動作を定義します。
1. **[Chat session]\(チャット セッション\)** セクションで、次のユーザー メッセージを入力します。

    ```
   What is generative AI?
    ```

1. モデルによって返される出力を確認します。これは、生成 AI の定義を提供するはずです。
1. フォローアップの質問として、次のユーザー メッセージを入力します。

    ```
   What are three benefits it provides?
    ```

1. 出力を確認します。チャット セッションが、コンテキストを提供するために前の入力と応答を追跡していること (つまり、"it" を "生成 AI" であると正しく解釈していること) と、要求された内容に基づいて適切な応答を提供していること (生成 AI の 3 つの利点を返すはずです) を確認します。

## *DALL-E* プレイグラウンドを使用して画像を生成する

Azure OpenAI Service は、言語生成モデルに加えて、イメージ生成のための DALL-E 2 モデルをサポートしています。

> **注**:演習のこのセクションを完了するには、Azure OpenAI Service へのアクセス アプリケーションで DALL-E 機能へのアクセスを申請して受け取っている必要があります。

1. [Azure OpenAI Studio](https://oai.azure.com/) で、左側のペインの **[DALL-E]** プレイグラウンドに移動します。
1. 次のプロンプトを入力します。

    ```
    A robot eating spaghetti
    ```

1. **[生成]** を選択し、結果を表示します。これは、プロンプトに入力した説明に基づく次のような画像で構成されるはずです。

    ![Azure OpenAI Studio の [DALL-E] プレイグラウンドのスクリーンショット。](./media/generative-ai/dall-e-playground.png)

1. プロンプトを次のように変更して、2 つめの画像を生成します。

    ```
    A robot eating spaghetti in the style of Rembrandt
    ```
1. 次のように、新しい画像がプロンプトの要件と一致することを確認します。

    ![Azure OpenAI Studio で DALL-E によって生成されたイメージのスクリーンショット。](./media/generative-ai/dall-e-results.png)

## クリーンアップ

Azure OpenAI リソースでの作業が完了したら、[Azure portal](https://portal.azure.com/?azure-portal=true) 内のデプロイまたはリソース全体を必ず削除してください。
