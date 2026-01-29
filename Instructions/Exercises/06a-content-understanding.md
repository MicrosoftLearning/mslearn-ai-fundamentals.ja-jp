---
lab:
  title: Microsoft Foundry での情報抽出に関する概要
  description: AI モデルを使用して、ビジュアル データから情報を抽出します。
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

## REST API を使用して情報を抽出する

情報を抽出するクライアント アプリまたはエージェントを開発するために、いくつかの Foundry モデルと REST API を使用できます。

>**注**:演習のこのセクションでは、Visual Studio Code (VS Code) にアクセスできる必要があります。  

1. Foundry のリソース キーとエンドポイントを特定します。 (クラシック) Foundry ポータルの、左側のメニューに移動します。 上部のアイコンをクリックしてメニューを*展開*し、オプションを表示します。 **[概要]** を選択して、Foundry プロジェクトのホーム ページに移動します。 プロジェクトのホーム ページで、プロジェクトの API キーをコピーして貼り付けられるか、またはサブスクリプションにこれらのアクセス許可がないことを示すメモが表示されます。 参照用にページを開いたままにします。 

>**注**:演習のこのセクションを実行するには、API キーを使用するためのアクセス許可を持つ Azure サブスクリプションが必要になります。 アクセス許可がない場合は、モデルを自分でテストすることができません。 ただし、ステップを確認するために、演習の残りの部分を読むことはできます。 

1. Visual Studio Code (VS Code) を開きます。 VS Code で、**Ctrl + Shift + P** キー(Windows/Linux) または [表示] メニューのコマンド パレットを押して、コマンド パレットを開きます。 「**Git:Clone**」と入力して選択します。 リポジトリの URL `https://github.com/MicrosoftLearning/mslearn-ai-fundamentals.git` を貼り付け、**Enter** キーを押します。  

1. リポジトリをクローンするローカル フォルダーを選択します。 メッセージが表示されたら **[開く]** をクリックして、VS Code でクローンされたプロジェクトの作業を開始します。 

1. VS Code エクスプローラーで、**[data]** フォルダーを選択してから、**[content-understanding]** フォルダーを選択します。 

    ![VS Code のエクスプローラーのスクリーンショット。](./media/0-content-understanding-file-navigation.png)

1. *[content-understanding]* フォルダーで、**[.env]** ファイルを開きます。 Foundry プロジェクトの API キーをコピーして貼り付けます。 Foundry プロジェクトのエンドポイントをコピーして貼り付けます。 *ai.azure.com* の後のテキストを削除して、エンドポイントを編集します。 エンドポイントは、`https://...ai.azure.com` のようになるはずです。 ファイルを保存します。 

1. Foundry ポータルに戻り、Foundry リソースに GPT-4.1、GPT-4.1-mini、text-embedding-3-large の Foundry モデル デプロイを作成します。 (クラシック) Foundry ポータルで、左側のメニューから **[モデルとエンドポイント]** を選択します (注: メニューを展開して項目の名前を表示するには、上部にある最初のアイコンを選択しなければならない場合があります)。 **[モデル デプロイ]** 画面で、**[+ モデルのデプロイ]** を選択してから、**[基本モデルのデプロイ]** を選択します。 **[GPT-4.1]** を検索して選択してから、**[確認]** を選択します。 既定の名前と既定のデプロイの種類をそのまま使用します。 **[デプロイ]** を選択します。 

    >**ヒント**: モデルがデプロイされると、モデルの詳細ページが表示されます。 左側のメニューに戻り、その他のモデルのデプロイを続けます。

1. 左側のメニューから **[モデルとエンドポイント]** を選択して、**[モデル デプロイ]** ページに戻ります。 **GPT-4.1-mini** と **text-embedding-3-large** でも繰り返します。 モデルがデプロイされたら、モデルの名前をメモします (名前をカスタマイズしない限り、GPT-4.1、GPT-4.1-mini、text-embedding-3-large になるはずです)。 

    ![モデル名のスクリーンショット。](./media/0-content-understanding-model-names.png)

1. Content Understanding を使用してコンテンツから情報を抽出するには、*curl* コマンドを使用して REST エンドポイントを呼び出します。 次の 3 つの呼び出しを行う必要があります。 
    - Content Understanding と Foundry のモデルの間に接続を設定するため 
    - コンテンツを分析するため 
    - 分析の結果を取得するため  

1. Foundry リソースで Content Understanding と Foundry のモデルの間に接続を設定しましょう。 VS Code に戻ります。 VS Code エクスプローラーで、**[set-up-connection.sh]** ファイルを開きます。 プロジェクト エンドポイント、キー、およびモデル デプロイ名の変数がスクリプトのどこに含まれているかを確認してください。 スクリプトは次のようになります。

    ![set-up-connection スクリプトのスクリーンショット。](./media/0-setup-curl-1.png)

    >**注**:.sh ファイルの上部に、.env からスクリプトの環境にすべてをエクスポートするスクリプトも含まれています。 この情報は、**.sh** ファイルの上部の **#!/bin/bash** の後に表示されます。 ファイルのこの部分は編集しないでください。  
    
1. `{myGPT41Deployment}`、`{myGPT41MiniDeployment}`、`{myEmbeddingDeployment}` のプレースホルダーをデプロイ済みのモデルの名前に置き換えて、curl スクリプトを更新します。 

    >**ヒント**: 変更を加えない限り、モデル名はそれぞれ `gpt-4.1`、`gpt-4.1-mini`、および `text-embedding-3-large` になるはずです。 変更を保存。

1. VS Code で、新しい bash ターミナルを開きます。 **Ctrl + Shift + P** (または [表示] メニューのコマンド パレット) を押します。 タイプ:「**Terminal: Create New Terminal (With Profile)**」と入力します。 一覧から **[Git Bash]** プロファイルを選択します。 ターミナルが VS Code 画面の下部に表示されます。 

1. ターミナルで、[content-understanding] フォルダーに移動します。 次をコピーしてターミナルに貼り付けます。 

    ```bash
    cd data/content-understanding
    ```
    
    その後、*Enter* キーを押してコマンドを実行し、適切なフォルダーに移動します。
 
1. 次をコピーしてターミナルに貼り付けて、スクリプトを実行します。 

    ```bash
    bash set-up-connection.sh
    ```

    その後、*Enter* キーを押して、Content Understanding とプロファイルにデプロイ済みのモデルの間に接続を形成するスクリプトを実行します。

1. 次は、prebuilt-invoice アナライザーを使用してコンテンツを分析し、請求書ドキュメントから構造化データを抽出してみましょう。 ポータルで行ったのと同じドキュメント `https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/refs/heads/main/data/content-understanding/contoso-invoice-1.pdf` を分析します。 

1. VS Code エクスプローラーで、**[extract-data.sh]** ファイルを開きます。 プロジェクト エンドポイントとキーの変数がスクリプトのどこに含まれているかを確認してください。 *ドキュメントの URL* が入力のどこに含まれているかを特定します。 スクリプトは次のようになります。

    ![extract-data スクリプトのスクリーンショット。](./media/0-extract-data-curl-1.png)

1. 次をコピーしてターミナルに貼り付けて、スクリプトを実行します。 

    ```bash
    bash extract-data.sh
    ```

    次に、*Enter* キーを押して、コンテンツを分析する POST 要求を行うスクリプトを実行します。

1. POST 応答は次のようになるはずです。 

    ![request-id が強調表示されている POST 応答のスクリーンショット。](./media/0-content-post-response-1.png)

1. POST 応答から `request-id` をコピーします。 

1. VS Code エクスプローラーで、**[get-results.sh]** を開き、ファイルをレビューします。 プロジェクト エンドポイントとキーの変数がスクリプトのどこに含まれているかを確認してください。 スクリプトは次のようになります。 

    ![request-id のプレースホルダーが強調表示されている get-results スクリプトのスクリーンショット。](./media/0-get-results-curl-1.png)


1. *[get-results.sh]* ファイルで、`{request-id}` を削除し、POST 応答から `request-id` を貼り付けます。 忘れずにファイルを保存してください。  
    
1. 次をコピーしてターミナルに貼り付けて、スクリプトを実行します。 

    ```bash
    bash get-results.sh
    ```

    次に、*Enter* キーを押して、GET 結果スクリプトを実行します。 POST 応答から `request-id` を使用すると、分析の結果を取得できます。
 
1. 返された JSON を確認します。 同じドキュメントを分析した後、Foundry ポータルの *[結果]* タブで確認したのと同じ情報がどのように提供されるかを確認します。

## クリーンアップ

コンテンツ解釈サービスの操作が終わったら、不要な Azure コストが発生しないように、この演習で作成したリソースを削除する必要があります。

- Azure portal において、この演習で作成したリソース グループを削除します。
