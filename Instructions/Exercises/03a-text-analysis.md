---
lab:
  title: Microsoft Foundry でテキスト分析を開始する
  description: Microsoft Foundry を使用して、さまざまな種類のテキスト分析を試します。
---

# Microsoft Foundry でテキスト分析を開始する

Azure Language サービスには、エンティティ認識、キー フレーズ抽出、要約、感情分析などの機能を備えた Text Analytics が含まれています。 この演習では、AI アプリケーションを作成するための Microsoft のプラットフォームである Microsoft Foundry を使用して、AI を使ってテキストを分析します。 Azure Language の自然言語処理機能を使用して、テキストを分析します。 この演習の目的は、テキスト分析手法の一般的なアプリケーションを詳しく知ることです。

この演習は約 **20** 分かかります。

>**注**:このラボでは、**従来の** Foundry インターフェイスを使用します。 新しい Foundry インターフェイスを使用している場合は、従来の Foundry インターフェイスに戻る必要があります。  

## Microsoft Foundry でプロジェクトを作成する

1. Web ブラウザーで、[Microsoft Foundry](https://ai.azure.com) (`https://ai.azure.com`) を開き、Azure 資格情報を使用してサインインします。 初めてサインインする場合に開かれるヒントまたはクイック スタートのペインを閉じ、必要に応じて、左上にある **[Foundry]** ロゴを使用してホーム ページに移動します。次の図のようなページが表示されます (**[ヘルプ]** ペインが表示される場合は閉じます)。

    ![Foundry のホーム ページのスクリーンショット。](./media/ai-foundry-portal.png)

1. ページの下部までスクロールし、**[Azure AI サービスを探す]** タイルを選択します。

    ![[Azure AI サービスを探す] タイルのスクリーンショット。](./media/ai-services.png)

1. [Azure AI サービス] ページで、**[言語 + トランスレーター]** タイルを選択します。

    ![[言語 + トランスレーター] タイルのスクリーンショット。](./media/language-tile.png)

1. **[言語 + トランスレーター]** ページで、**[言語プレイグラウンドを試す]** を選択します。 次に、メッセージが表示されたら、次の設定で新しいプロジェクトを作成します。
    - **プロジェクト名**:*プロジェクトに有効な名前を入力します。*
    - **[詳細設定]**:
        - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
        - **リソース グループ**: *リソース グループを作成または選択します*
        - **[リージョン]**: "いずれかの **[Foundry 推奨]** リージョンを選択します"**
        - **AI Foundry または Azure OpenAI** "有効な名前で新しい Foundry リソースを作成します"**

1. **［作成］** を選択します プロジェクトが作成されるまで待ちます。 これには数分かかることがあります。

1. プロジェクトが作成されると、**言語**プレイグラウンドに移動します (移動しない場合は、左側の作業ペインで **[プレイグラウンド]** を選択し、そこから言語プレイグラウンドを開きます)。

    Language プレイグラウンドは、いくつかの Azure Language 機能を試用できるユーザー インターフェイスです。  

## テキスト分析の準備

1. `https://aka.ms/ai-text` で **[text.zip](https://aka.ms/ai-text){:target="_blank"}** をダウンロードして展開します。 このアーカイブには、この演習で使用する複数のテキスト ドキュメントが含まれています。
1. プレイグラウンド言語に戻り、Azure Language のテキスト分析機能の一部を試します。

## 感情を分析する

**感情分析**は、一般的な NLP タスクです。 これは、テキストが肯定的、中立的、または否定的な感情を伝えるかどうかを判断するために使用されます。レビュー、ソーシャル メディアの投稿、その他の主観的なドキュメントを分類するのに役立ちます。

1. 言語プレイグラウンドで、**[テキストの分類]** を選択します。 次に、**[センチメントの分析]** タイルを選択します。
1. ダウンロードしたテキスト ファイルを抽出したフォルダーから **document-1.txt** をアップロードします。
1. **[実行]** を選択します。 出力結果を確認します。

    >**ヒント**: 分析によって、各文の全体的なセンチメント スコアと個々のスコアが生成されることに注目してください。

    ![Language プレイグラウンドの感情分析インターフェイスのスクリーンショット。](./media/sentiment-analysis.png)

1. 鉛筆アイコンをクリックしてテキストを編集します。 **document-2.txt** と **document-3.txt** について分析を繰り返します。

## キー フレーズを抽出する

**キー フレーズ**は、テキスト内の最も重要な情報です。 Azure Language のキー フレーズ抽出機能を使用して、レビューから重要な情報をプルしてみましょう。

1. 言語プレイグラウンドで、**[情報の抽出]** を選択します。 次に、**[キー フレーズの抽出]** タイルを選択します。 
1. ダウンロードしたテキスト ファイルを抽出したフォルダーから **document-1.txt** をアップロードします。
1. **[実行]** を選択します。 出力結果を確認します。

    >**ヒント**: *[詳細]* セクションで抽出されたさまざまなフレーズを確認します。 これらのフレーズは、テキストの意味に最も影響を与える可能性が高いです。

    ![言語プレイグラウンドの [キー フレーズの抽出] インターフェイスのスクリーンショット。](./media/key-phrases.png)

1. 鉛筆アイコンをクリックしてテキストを編集します。 **document-2.txt** と **document-3.txt** について分析を繰り返します。

## 名前付きエントリの抽出

**名前付きエンティティ**は、固有の名前を持つ人物、場所、オブジェクトを表す単語です。 Azure Language の名前付きエンティティ抽出機能を使用して、レビューで情報の種類を識別してみましょう。

1. 言語プレイグラウンドで、**[情報の抽出]** を選択します。 次に、**[名前付きエンティティの抽出]** タイルを選択します。 
1. ダウンロードしたテキスト ファイルを抽出したフォルダーから **document-1.txt** をアップロードします。
1. **[実行]** を選択します。 出力結果を確認します。

    >**ヒント**: *[詳細]* セクションで、抽出されたエンティティの種類や信頼度スコアなどの追加情報がどのように表示されるかを確認します。 信頼度スコアは、識別された種類が実際にそのカテゴリに属している可能性を表します。

    ![言語プレイグラウンドの [名前付きエンティティの抽出] インターフェイスのスクリーンショット。](./media/entity-extraction.png)

1. 鉛筆アイコンをクリックしてテキストを編集します。 **document-2.txt** と **document-3.txt** について分析を繰り返します。

## テキストを要約する

**[要約]** を使うと、ドキュメントの主要なポイントを、より短い文章にまとめることができます。

1. 言語プレイグラウンドで、**[情報の要約]** を選択し、**[テキストの要約]** タイルを選択します。
1. ダウンロードしたテキスト ファイルを抽出したフォルダーから **document-1.txt** をアップロードします。
1. **[実行]** を選択します。 出力結果を確認します。

    >**ヒント**: *[詳細]* の *[抽出要約]* には、最も重要な文の順位スコアが表示されます。

    ![言語プレイグラウンドの [テキストの要約] インターフェイスのスクリーンショット。](./media/summarize-text.png)

1. 鉛筆アイコンをクリックしてテキストを編集します。 **document-2.txt** と **document-3.txt** について分析を繰り返します。

#### サンプル コードを確認する

1. **[コードの表示]** タブを選択して、テキスト要約のサンプル コードを表示します。 Python での参照用の同じサンプル コードを以下に示します。

```python

# This example requires environment variables named "AZURE_AI_KEY" and "ENDPOINT_TO_CALL_LANGUAGE_API"
key = os.environ.get('AZURE_AI_KEY')
endpoint = os.environ.get('ENDPOINT_TO_CALL_LANGUAGE_API')

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

# Example method for summarizing text
def sample_extractive_summarization(client):
    from azure.core.credentials import AzureKeyCredential
    from azure.ai.textanalytics import (
        TextAnalyticsClient,
        ExtractiveSummaryAction
    ) 

    document = [
        "The extractive summarization feature uses natural language processing techniques to locate key sentences in an unstructured text document. "
        "These sentences collectively convey the main idea of the document. This feature is provided as an API for developers. " 
        "They can use it to build intelligent solutions based on the relevant information extracted to support various use cases. "
        "Extractive summarization supports several languages. It is based on pretrained multilingual transformer models, part of our quest for holistic representations. "
        "It draws its strength from transfer learning across monolingual and harness the shared nature of languages to produce models of improved quality and efficiency. "
    ]

    poller = client.begin_analyze_actions(
        document,
        actions=[
            ExtractiveSummaryAction(max_sentence_count=4)
        ],
    )

    document_results = poller.result()
    for result in document_results:
        extract_summary_result = result[0]  # first document, first result
        if extract_summary_result.is_error:
            print("...Is an error with code '{}' and message '{}'".format(
                extract_summary_result.code, extract_summary_result.message
            ))
        else:
            print("Summary extracted: 
{}".format(
                " ".join([sentence.text for sentence in extract_summary_result.sentences]))
            )

sample_extractive_summarization(client)

```

> **ヒント**: 職場または学校アカウントを使用して Azure にサインインしていて、Azure サブスクリプションに十分なアクセス許可がある場合は、VS Code for Web でサンプル コードを開いて実行し、編集を試すことができます。

## クリーンアップ

これ以上の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. [https://portal.azure.com](https://portal.azure.com) で **Azure portal** を開き、作成したリソースを含むリソース グループを選択します。
1. **[リソース グループの削除]** を選び、**リソース グループの名前を入力**して、確定します。 これでリソース グループが削除されます。

## 詳細情報

このサービスで実行できる操作の詳細については、[言語サービスのページ](https://learn.microsoft.com/azure/ai-services/language-service/overview)を参照してください。