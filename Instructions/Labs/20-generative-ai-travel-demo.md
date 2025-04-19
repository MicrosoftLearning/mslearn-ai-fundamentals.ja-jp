---
lab:
  title: Microsoft Copilot と生成 AI について確認する
---
# Microsoft Copilot と生成 AI について確認する

"生成" AI は、AI の機能のうち、コンテンツを作成する機能のカテゴリを表します。 人々は通常、チャット アプリケーションに組み込まれている生成 AI と対話します。 このようなアプリケーションの一般的な例の 1 つが、リアルタイムのインテリジェンスと支援を提供することで、作業エクスペリエンスを向上させるために設計された AI 駆動型の生産性ツールである Microsoft Copilot です。 

この演習では、Microsoft Copilot を使用して旅行プランを生成します。

> **注**: この演習では、[個人用の Microsoft アカウント](https://signup.live.com) (outlook.com アカウントなど) があることを前提としています。

## Microsoft Copilot を使用して旅行プランを生成する

1. Web ブラウザーで、[Microsoft Copilot](https://copilot.microsoft.com) (`https://copilot.microsoft.com`) を開きます。 画面の右側にある **[サインイン]** ボタンをクリックします。 個人用の Microsoft アカウントを使用してサインインします。表示されるウェルカム メッセージやオファーはすべて閉じます。

    >**注**: **職場**または**個人用**のアカウントを使用して続行するように求められる場合があります。 **[個人用]** を選択してサインインします。 

1. 生成 AI アシスタントからの応答を改善するには、次の方法を検討します。
    - アシスタントに何をしてほしいかについて、具体的な目標から始めます
    - 以前のプロンプトと応答に基づいて繰り返し、結果を洗練させます
    - 特定の範囲の情報に基づいて応答できるように情報源を指定する
    - 応答の妥当性と関連性を最大化できるようにコンテキストを追加する
    - 応答に対する明確な期待値を設定します

1. 特定の目標を持つプロンプトを使用して、Microsoft Copilot から応答を生成してみましょう。 [Copilot] ペインの下部にあるチャット ボックスに、次のプロンプトを入力します。

    ```prompt
    I'm planning a trip to Paris in September. Can you help me?
    ```

1. Copilot からの応答を確認します。 

    >**注**: 受け取る応答の具体的な内容は、生成 AI の性質によって異なる可能性があります。
 
1. 別のプロンプトを試してみましょう。 次のように入力します。

    ```prompt
    Where's a good location in Paris to stay? 
    ```

1. 応答を確認します。これには、パリに滞在するための場所がいくつか提示されているはずです。

1. 以前のプロンプトと応答に基づいて繰り返し、結果を洗練させましょう。 次のプロンプトを入力します。
    
    ```prompt
    Can you give me more information about dining options near the first location?
    ``` 

1. 応答を確認します。これには、前の応答の場所の近くの飲食店がいくつか提示されているはずです。 

1. それでは、特定の範囲の情報に基づいて応答できるように情報源を指定しましょう。 次のように入力します。 
    
    ```prompt
    Based on the information at https://en.wikipedia.org/wiki/History_of_Paris, what were the key events in the city's history?
    ```

1. 応答を確認します。これには、提供された Web サイトに基づいた情報が提示されているはずです。 

1. 応答の関連性を最大化するためにコンテキストを追加してみましょう。 次のプロンプトを入力します。 

    ```prompt
    What three places do you recommend I stay in Paris to be within walking distance to historical attractions? Explain your reasoning.
    ```

1. 応答と応答の理由を確認します。  

1. 応答に対する明確な期待を設定します。 次のプロンプトを入力します。
    
    ```prompt
    What are the top 10 sights to see in Paris? Answer with a numbered list in order of popularity.
    ```

1. 応答を確認します。これは、パリで見る観光スポットの番号付きリストが提示されているはずです。

1. 移動する前に、前にスクロールしてチャット履歴を表示できることに注意してください。 チャットウィンドウの横にあるプラス記号 **+** を使用して、*新しい*チャットを開始したり、画像をアップロードしてプロンプトに根拠となるソースを追加したりすることもできます。    

1. 完了したら、ブラウザー ウィンドウを閉じます。 
