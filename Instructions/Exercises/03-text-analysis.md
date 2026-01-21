---
lab:
  title: Microsoft Foundry でテキストを分析する
---

# Microsoft Foundry でテキストを分析する

Azure Language サービスには、エンティティ認識、キー フレーズ抽出、要約、感情分析などの機能を備えた Text Analytics が含まれています。 たとえば、架空の旅行会社 Margie's Travel が、ホテル滞在のレビューを送信するように顧客に勧めているとします。 Language サービスを使用すると、名前付きエンティティの抽出、キー フレーズの識別、テキストの要約などを実行できます。

この演習では、インテリジェント アプリケーションを作成するための Microsoft のプラットフォームである Foundry で Azure Language を使用してホテルのレビューを分析します。 

この演習は約 **20** 分かかります。

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

## Azure Language を使用してテキストを分析する

Azure Language には、さまざまなテキスト分析機能が用意されています。

### Foundry で Azure Language を使用して名前付きエンティティを抽出する

*名前付きエンティティ*は、固有の名前を持つ人物、場所、オブジェクトを表す単語です。 Azure Language の名前付きエンティティ抽出機能を使用して、レビューで情報の種類を識別してみましょう。

1. 言語プレイグラウンドで、**[情報の抽出]** を選択します。 次に、**[名前付きエンティティの抽出]** タイルを選択します。 

1. *サンプル*に、次のレビューを入力します。

    ```
    Tired hotel with poor service
    The Royal Hotel, London, United Kingdom
    5/6/2018
    This is an old hotel (has been around since 1950's) and the room furnishings are average - becoming a bit old now and require changing. The internet didn't work and had to come to one of their office rooms to check in for my flight home. The website says it's close to the British Museum, but it's too far to walk.
    ```

1. **[実行]** を選択します。 出力結果を確認します。

    ![言語プレイグラウンドの [名前付きエンティティの抽出] インターフェイスのスクリーンショット。](./media/entity-extraction.png)

    *[詳細]* セクションで、抽出されたエンティティの種類や信頼度スコアなどの追加情報がどのように表示されるかを確認します。 信頼度スコアは、識別された種類が実際にそのカテゴリに属している可能性を表します。

### Foundry で Azure Language を使用してキー フレーズを抽出する

*キー フレーズ*は、テキスト内の最も重要な情報です。 Azure Language のキー フレーズ抽出機能を使用して、レビューから重要な情報をプルしてみましょう。

1. 言語プレイグラウンドで、**[情報の抽出]** を選択します。 次に、**[キー フレーズの抽出]** タイルを選択します。 

1. *サンプル*に、次のレビューを入力します。

    ```
    Good Hotel and staff
    The Royal Hotel, London, UK
    3/2/2018
    Clean rooms, good service, great location near Buckingham Palace and Westminster Abbey, and so on. We thoroughly enjoyed our stay. The courtyard is very peaceful and we went to a restaurant which is part of the same group and is Indian ( West coast so plenty of fish) with a Michelin Star. We had the taster menu which was fabulous. The rooms were very well appointed with a kitchen, lounge, bedroom and enormous bathroom. Thoroughly recommended.
    ```

1. **[実行]** を選択します。 出力結果を確認します。

    ![言語プレイグラウンドの [キー フレーズの抽出] インターフェイスのスクリーンショット。](./media/key-phrases.png)

    *[詳細]* セクションで抽出された様々なフレーズを確認します。 これらのフレーズは、テキストの意味に最も影響を与える可能性が高いです。

### Foundry で Azure Language を使用してテキストを要約する
 
Azure Language の要約機能を見てみましょう。

1. 言語プレイグラウンドで、**[情報の要約]** を選択し、**[テキストの要約]** タイルを選択します。

1. *サンプル*に、次のレビューを入力します。
    
    ```
    Very noisy and rooms are tiny
    The Lombard Hotel, San Francisco, USA
    9/5/2018
    Hotel is located on Lombard street which is a very busy SIX lane street directly off the Golden Gate Bridge. Traffic from early morning until late at night especially on weekends. Noise would not be so bad if rooms were better insulated but they are not. Had to put cotton balls in my ears to be able to sleep--was too tired to enjoy the city the next day. Rooms are TINY. I picked the room because it had two queen size beds--but the room barely had space to fit them. With family of four in the room it was tight. With all that said, rooms are clean and they've made an effort to update them. The hotel is in Marina district with lots of good places to eat, within walking distance to Presidio. May be good hotel for young stay-up-late adults on a budget
    ```

1. **[実行]** を選択します。 出力結果を確認します。

    ![言語プレイグラウンドの [テキストの要約] インターフェイスのスクリーンショット。](./media/summarize-text.png)

    *[詳細]* の *[抽出要約]* には、最も重要な文の順位スコアが表示されます。

### テキスト内のセンチメントを分析する

感情分析は、ホテルのレビューなどのテキストを分析する場合に一般的なタスクです。

1. 言語プレイグラウンドで、**[テキストの分類]** を選択します。 次に、**[センチメントの分析]** タイルを選択します。

1. *サンプル*に、次のレビューを入力します。
    
    ```
    Disappointing Stay at The City Hotel
    The City Hotel, London
    9/5/2018
    My experience at The City Hotel in London was far from pleasant. The constant noise from nearby train tracks made it nearly impossible to sleep, with vibrations felt throughout the building. The rooms were outdated, dusty, and poorly maintained—dripping faucets, squeaky beds, and broken fixtures were just the beginning. Sound insulation was nonexistent, so every conversation from neighboring rooms was clearly audible. While the location near public transport was convenient and the staff were friendly, these positives couldn't make up for the overall discomfort and lack of value. I wouldn’t recommend this hotel to anyone seeking a restful or enjoyable stay.
    ```

1. **[実行]** を選択します。 出力結果を確認します。

    ![Language プレイグラウンドの感情分析インターフェイスのスクリーンショット。](./media/sentiment-analysis.png)

    分析によって、各文の全体的なセンチメント スコアと個々のスコアが生成されることに注目してください。

## 言語の検出とテキストの翻訳

Azure Language を使用すると、テキストが記述されている言語を検出できます。 さらに、Azure Translator を使用すると、テキストをある言語から別の言語に簡単に翻訳できます。

### 言語を検出する

まず、レビューが書き込まれている言語を検出してみましょう。

1. **[テキストの分類]** ペインで、**[言語の検出]** タイルを選択します。

1. *サンプル*に、次のレビューを入力します。
    
    ```
    Un séjour mémorable à l’Hôtel d’Ville
    l’Hôtel d’Ville, Paris
    9/5/2018
    J’ai passé un excellent séjour à l’Hôtel d’Ville à Paris. L’emplacement est idéal, en plein cœur de la ville, ce qui permet de découvrir facilement les principaux sites touristiques. Le personnel était chaleureux, professionnel et toujours prêt à aider. La chambre était propre, confortable et bien équipée, avec une vue charmante sur les rues parisiennes. Le petit-déjeuner était varié et délicieux, parfait pour commencer la journée. Je recommande vivement cet hôtel à tous ceux qui recherchent une expérience parisienne authentique et agréable.
    ```

1. **[実行]** を選択します。 出力結果を確認します。

    ![言語プレイグラウンドの [言語の検出] インターフェイスのスクリーンショット。](./media/detect-language.png)

    言語がフランス語であると検出されています。 

### テキストを翻訳する

それでは、フランス語のレビューを英語に翻訳しましょう。

1. ページの上部で、**言語プレイグラウンド**のページ タイトルの横にある **&larr;**(戻る) リンクを使用して、使用可能なすべてのプレイグラウンドを表示します。
1. プレイグラウンドの一覧で、**[トランスレーター プレイグラウンド]** を開きます。
1. トランスレーター プレイグラウンドで、**[テキスト翻訳]** を選択します。
1. **[構成]** ペインで、次の言語オプションを選択します。
    - **[原文]**: フランス語
    - **[訳文]**: 英語
1. *[サンプル]* に、フランス語のレビューを入力します。
    
    ```
    Un séjour mémorable à l’Hôtel d’Ville
    l’Hôtel d’Ville, Paris
    9/5/2018
    J’ai passé un excellent séjour à l’Hôtel d’Ville à Paris. L’emplacement est idéal, en plein cœur de la ville, ce qui permet de découvrir facilement les principaux sites touristiques. Le personnel était chaleureux, professionnel et toujours prêt à aider. La chambre était propre, confortable et bien équipée, avec une vue charmante sur les rues parisiennes. Le petit-déjeuner était varié et délicieux, parfait pour commencer la journée. Je recommande vivement cet hôtel à tous ceux qui recherchent une expérience parisienne authentique et agréable.
    ```

1. **翻訳** を選択します。 出力結果を確認します。

    ![Translator プレイグラウンドの [テキスト翻訳] インターフェイスのスクリーンショット。](./media/text-translation.png)

    フランス語のレビューが英語に翻訳されています。

## クリーンアップ

これ以上の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. [https://portal.azure.com](https://portal.azure.com) で **Azure portal** を開き、作成したリソースを含むリソース グループを選択します。
1. **[リソース グループの削除]** を選び、**リソース グループの名前を入力**して、確定します。 これでリソース グループが削除されます。

## 詳細情報

このサービスで実行できる操作の詳細については、[言語サービスのページ](https://learn.microsoft.com/azure/ai-services/language-service/overview)を参照してください。