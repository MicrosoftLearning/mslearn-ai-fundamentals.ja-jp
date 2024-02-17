---
lab:
  title: Language Studio でテキストを分析する
---

# Language Studio でテキストを分析する

この演習では、ホテル レビューの例を分析して、Azure AI Language の機能を確認します。 Language Studio を使用して、レビューがおおよそ肯定的か否定的かを理解します。

自然言語処理 (NLP) は、書き言葉と話し言葉を扱う AI の一分野です。 NLP を使用して、テキストや音声から意味を抽出したり、意味のある応答を自然言語で作成したりするソリューションを構築できます。

たとえば、架空の旅行会社 Margie's Travel が、ホテル滞在のレビューを送信するように顧客に勧めているとします。 言語サービスを使用して、キー フレーズを抽出して特定したり、肯定的なレビューと否定的なレビューを判別したり、場所や人物などの既知のエンティティへの言及についてレビュー テキストを分析したりできます。

Azure AI Language サービスには、テキスト解析と NLP 機能が含まれています。 これには、テキスト内のキー フレーズの識別と、感情に基づくテキストの分類が含まれます。

## "言語" リソースを作成する**

多くの Azure AI Language 機能は、**言語**リソースと **Azure AI サービス** リソースのいずれかで使用できます。 言語リソースのみを使用できるものもあります。 以下の演習では、**言語**リソースを使用します。 まだ作成していない場合は、Azure サブスクリプションで**言語**リソースを作成します。

1. 別のブラウザー タブで Azure portal ([https://portal.azure.com](https://portal.azure.com?azure-portal=true)) を開き、ご使用の Azure サブスクリプションに関連付けられている Microsoft アカウントを使用してサインインします。

1. **[&#65291;リソースの作成]** ボタンをクリックし、*言語サービス*を検索します。 **言語サービス**を**作成する**プランを選択します。 **[追加機能の選択]** ページに転送されます。 既定の選択をそのまま使用し、**[続行] をクリックしてリソースを作成します**。 

1. **[言語リソースの作成]** ページを次の設定で構成します。
    - **[サブスクリプション]**: *お使いの Azure サブスクリプション*。
    - **[リソース グループ]**: *一意の名前のリソース グループを選択するか、作成します*。
    - **[リージョン]**: 米国東部。
    - **[名前]**: *一意の名前を入力します*。
    - **価格レベル**: *Free F0 または S (Free F0 を使用できない場合)*
    - **[このボックスをオンにすることにより、以下のすべてのご契約条件を読み、同意したものとみなされます]**:*オン*。

1. **[確認 + 作成]**、**[作成]** の順に選択し、デプロイが完了するまで待ちます。

## Azure AI Language Studio でリソースを構成する

1. 別のブラウザー タブで、**Language Studio** ([https://language.cognitive.azure.com](https://language.cognitive.azure.com?azure-portal=true)) を開き、サインインします。

1. **[Azure リソースを選択します]** で入力を求められたら、次の構成を行います。
    - **Azure ディレクトリ**:*既定のディレクトリ (使用しているディレクトリ)*
    - **Azure サブスクリプション**: *使用するサブスクリプションを選択します*
    - **リソースの種類**: 言語
    - **リソース名**: *直前に作成した言語リソースを選択します*

**[完了]** を選択します。

> **重要**: 2023 年 7 月の時点で、Azure AI サービスには、以前 Cognitive Services と Azure Applied AI Services と呼ばれていたものがすべて含まれています。 一部のユーザー インターフェイスでは、`Cognitive Services` から `Azure AI services` への言及の更新がまだ進行中です。 この 2 つの名前は、同じ種類のリソースに言及しています。

> **注**:言語リソースの選択を求めるメッセージが表示***されない***場合、原因として、お使いのサブスクリプションに複数の言語リソースが存在していることが考えられます。その場合は、次の操作を行います。
> 1. ページの上部にあるバーで、**[設定] (&#9881;)** ボタンを選択します。 
> 1. **[設定]** ページで、**[リソース]** タブを表示します。
> 1. 直前に作成したリソースを選択し、**[リソースの切り替え]** を選択します。 マネージド ID が **[有効]** であることを確認します。
> ![言語リソースを有効にします。](media/analyze-text-language-service/language-resource-enabled.png)
> 1. ページの上部で、[**Language Studio**] を選択して、Language Studio のホーム ページに戻ります。

## Language Studio でレビューを分析する

1. Web ブラウザーで、**Language Studio** ([https://language.cognitive.azure.com](https://language.cognitive.azure.com?azure-portal=true)) に移動します。

1. **[Language Studio へようこそ]** ランディング ページで、**[テキストの分類]** タブを選択し、**[感情と意見の分析]** タイルを選択します。

1. [テキスト言語の選択] で、**[English]** を選択します。**

1. [Select your Azure resource]\(Azure リソースの選択\) で、リソースを選択します。**

1. *[Enter your own text, upload a file, or use one of our sample texts]\(独自のテキストを入力するか、ファイルをアップロードするか、サンプル テキストのいずれかを使用する\)* に、次のレビューをコピーして貼り付けます。

    ```
    Tired hotel with poor service
    The Royal Hotel, London, United Kingdom
    5/6/2018
    This is an old hotel (has been around since 1950's) and the room furnishings are average - becoming a bit old now and require changing. The internet didn't work and had to come to one of their office rooms to check in for my flight home. The website says it's close to the British Museum, but it's too far to walk.
    ```

1. デモで使用量が追加され、コストが発生する可能性があることを確認するチェック ボックスをオンにして、**[実行]** を選択します。

1. 出力結果を確認します。 各 "文" だけでなく、"ドキュメント" についても感情が分析されています。**** **[Sentence 1]\(文 1\)** を選択すると、その文の感情分析が表示されます。 

全体的な感情の後に、"肯定的なスコア"、"中立的なスコア"、"否定的なスコア" の 3 つのカテゴリのスコアが続きます。****** 各カテゴリでは、0 から 1 までのスコアが提供されます。 これらの自信度スコアは、指定されたテキストが特定の感情である確率を示します。 

**[Sentence 1]\(文 1\)** を再度選択して閉じます。

1. 上にスクロールして **[テキスト ボックスを消去]** を選択し、次のレビューをコピーして貼り付けます。

    ```
    Good Hotel and staff
    The Royal Hotel, London, UK
    3/2/2018
    Clean rooms, good service, great location near Buckingham Palace and Westminster Abbey, and so on. We thoroughly enjoyed our stay. The courtyard is very peaceful and we went to a restaurant which is part of the same group and is Indian ( West coast so plenty of fish) with a Michelin Star. We had the taster menu which was fabulous. The rooms were very well appointed with a kitchen, lounge, bedroom and enormous bathroom. Thoroughly recommended.
    ```
    
    
1. **[実行]** を選択します。 出力を確認し、感情と自信度レベルを確認します。

1. **[テキスト ボックスを消去]** を再度選択し、次のレビューをコピーして貼り付けます。

    >Very noisy and rooms are tiny The Lombard Hotel, San Francisco, USA 9/5/2018 Hotel is located on Lombard street which is a very busy SIX lane street directly off the Golden Gate Bridge. (非常に騒音が多く、部屋は狭い。米国、サンフランシスコ、The Lombard Hotel、2018 年 9 月 5 日。ホテルはロンバート街にあり、ゴールデンゲートブリッジと直接つながっている 6 車線の非常に交通量の多い地区です。) Traffic from early morning until late at night especially on weekends. (早朝から深夜まで、特に週末はずっと車が通ります。) Noise would not be so bad if rooms were better insulated but they are not. (客室が適切に防音されていれば騒音もそれほど気にならなかったかもしれませんが、防音されていませんでした。) Had to put cotton balls in my ears to be able to sleep--was too tired to enjoy the city the next day. (耳の中に綿ボールを入れなければ眠ることができず、疲れが取れなかったので、次の日に街を楽しむことができませんでした。) Rooms are TINY. (部屋は非常に狭いです。) I picked the room because it had two queen size beds--but the room barely had space to fit them. (2 台のクイーン サイズのベッドがあるため、その部屋を選んだのですが、部屋のサイズはその 2 台のベッドがかろうじて収まる程度のものでした。) With family of four in the room it was tight. (家族 4 人で泊まるには、狭すぎました。) With all that said, rooms are clean and they've made an effort to update them. (そうは言っても、客室は清潔で、きれいに保とうと努力していました。) The hotel is in Marina district with lots of good places to eat, within walking distance to Presidio. (ホテルは Marina 地区にあり、Presidio までの徒歩圏内にたくさんの良いレストランがあります。) May be good hotel for young stay-up-late adults on a budget. (おそらく、夜更かしをする若い成人層には予算的に良いホテルと言えるでしょう。)

1. **[実行]** を選択し、自信度レベルとあわせて感情を確認します。 テキストを見て、そのテキストをサービスが返した感情分析と比較します。

この演習では、Language Studio を使用して、新しい言語リソースを作成するか、既存の言語リソースを使用しました。 感情と意見の分析サービスを試す前に、[設定] でリソースを有効にしました。 次に、3 つのテキストでサービスをテストしました。

## クリーンアップ

これ以上の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. **Azure portal** ([https://portal.azure.com](https://portal.azure.com)) を開き、作成したリソースを含むリソース グループを選択します。
1. リソースを選択し、**[削除]** を、次に **[はい]** を選択して確定します。 これでリソースが削除されます。

## 詳細情報

このサービスで実行できる操作の詳細については、[言語サービスのページ](https://learn.microsoft.com/azure/ai-services/language-service/overview)を参照してください。
