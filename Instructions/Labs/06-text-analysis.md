---
lab:
  title: Azure AI Foundry ポータルでテキストを分析する
---

# Azure AI Foundry ポータルでテキストを分析する

自然言語処理 (NLP) は、書き言葉と話し言葉を扱う AI の一分野です。 NLP を使用して、テキストや音声から意味を抽出したり、意味のある応答を自然言語で作成したりするソリューションを構築できます。

Azure AI Language サービスには、エンティティ認識、キー フレーズ抽出、要約、感情分析などの機能を備えた Text Analytics が含まれています。 たとえば、架空の旅行会社 Margie's Travel が、ホテル滞在のレビューを送信するように顧客に勧めているとします。 Language サービスを使用すると、名前付きエンティティの抽出、キー フレーズの識別、テキストの要約などを実行できます。

この演習では、インテリジェントなアプリケーションを作成するための Microsoft のプラットフォームである Azure AI Foundry ポータルで Azure AI Language を使用し、ホテルのレビューを分析します。 

## Azure AI Foundry ポータルでプロジェクトを作成する

1. Web ブラウザーで [Azure AI Foundry ポータル](https://ai.azure.com) (`https://ai.azure.com`) を開き、Azure 資格情報を使用してサインインします。 初めてサインインしたときに開かれたヒントまたはクイック スタート ペインを閉じます。 

1. ブラウザーで `https://ai.azure.com/managementCenter/allResources` に移動し、**[作成]** を選択します。 次に、*新しい Azure AI Foundry リソース*を作成するオプションを選択します。

1. *プロジェクトの作成*ウィザードで、プロジェクトの有効な名前を入力します。

1. *[詳細オプション]* を展開し、プロジェクト用に次の設定を指定します。
    - **サブスクリプション**:お使いの Azure サブスクリプション
    - **リソース グループ**: リソース グループを作成または選択します
    - **リージョン**: 次のいずれかの場所を選択してください。
        * 米国東部
        * フランス中部
        * 韓国中部
        * 西ヨーロッパ
        * 米国西部

    プロジェクトとハブが作成されるまで待ちます。

1. プロジェクトが作成されると、プロジェクトの詳細の*概要*ページに移動します。

1. 画面の左側のメニューで、**[プレイグラウンド]** を選択します。

1. *[プレイグラウンド]* ページで、**[言語プレイグラウンド]** タイルを選択し、Azure AI Language の機能をいくつか試します。

## Azure AI Foundry ポータルで Azure AI Language を使用して名前付きエンティティを抽出する

*名前付きエンティティ*は、固有の名前を持つ人物、場所、オブジェクトを表す単語です。 Azure AI Language の名前付きエンティティ抽出機能を使用して、レビュー内の情報の種類を識別します。

1. 言語プレイグラウンドで、**[情報の抽出]** を選択します。 次に、**[名前付きエンティティの抽出]** タイルを選択します。 

1. *[サンプル]* の下に、次のレビューをコピーして貼り付けます。

    ```
    Tired hotel with poor service
    The Royal Hotel, London, United Kingdom
    5/6/2018
    This is an old hotel (has been around since 1950's) and the room furnishings are average - becoming a bit old now and require changing. The internet didn't work and had to come to one of their office rooms to check in for my flight home. The website says it's close to the British Museum, but it's too far to walk.
    ```

1. **[実行]** を選択します。 出力結果を確認します。 *[詳細]* セクションで、抽出されたエンティティの種類や信頼度スコアなどの追加情報がどのように表示されるかを確認します。 信頼度スコアは、識別された種類が実際にそのカテゴリに属している可能性を表します。

## Azure AI Foundry ポータルで Azure AI Language を使用してキー フレーズを抽出する

*キー フレーズ*は、テキスト内の最も重要な情報です。 Azure AI Language のキー フレーズ抽出機能を使用して、レビューから重要な情報をプルします。

1. 言語プレイグラウンドで、**[情報の抽出]** を選択します。 次に、**[キー フレーズの抽出]** タイルを選択します。 

1. *[サンプル]* の下に、次のレビューをコピーして貼り付けます。

    ```
    Good Hotel and staff
    The Royal Hotel, London, UK
    3/2/2018
    Clean rooms, good service, great location near Buckingham Palace and Westminster Abbey, and so on. We thoroughly enjoyed our stay. The courtyard is very peaceful and we went to a restaurant which is part of the same group and is Indian ( West coast so plenty of fish) with a Michelin Star. We had the taster menu which was fabulous. The rooms were very well appointed with a kitchen, lounge, bedroom and enormous bathroom. Thoroughly recommended.
    ```

1. **[実行]** を選択します。 出力結果を確認します。 *[詳細]* セクションで抽出された様々なフレーズを確認します。 これらのフレーズは、テキストの意味に最も影響を与える可能性が高いです。

## Azure AI Foundry ポータルで Azure AI Language を使用してテキストを要約する
 
1. Azure AI Language の要約機能について確認します。 言語プレイグラウンドで、*[情報の要約]* を選択し、**[テキストの要約]** タイルを選択します。

1. *[サンプル]* の下に、次のレビューをコピーして貼り付けます。
    
    ```
    Very noisy and rooms are tiny
    The Lombard Hotel, San Francisco, USA
    9/5/2018
    Hotel is located on Lombard street which is a very busy SIX lane street directly off the Golden Gate Bridge. Traffic from early morning until late at night especially on weekends. Noise would not be so bad if rooms were better insulated but they are not. Had to put cotton balls in my ears to be able to sleep--was too tired to enjoy the city the next day. Rooms are TINY. I picked the room because it had two queen size beds--but the room barely had space to fit them. With family of four in the room it was tight. With all that said, rooms are clean and they've made an effort to update them. The hotel is in Marina district with lots of good places to eat, within walking distance to Presidio. May be good hotel for young stay-up-late adults on a budget
    ```

1. **[実行]** を選択します。 出力結果を確認します。 *[詳細]* の *[抽出要約]* には、最も重要な文の順位スコアが表示されます。   

## クリーンアップ

これ以上の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. [https://portal.azure.com](https://portal.azure.com) で **Azure portal** を開き、作成したリソースを含むリソース グループを選択します。

1. リソースを選択し、**[削除]** を選択し、**[はい]** を選択して確定します。 これでリソースが削除されます。

## 詳細情報

このサービスで実行できる操作の詳細については、[言語サービスのページ](https://learn.microsoft.com/azure/ai-services/language-service/overview)を参照してください。
