---
lab:
  title: Language Studio で質問応答を使用する
---

# Language Studio で質問応答モデルを使用する

この演習では、Language Studio を使用して、カスタマー サービス ボットで使われる質問と回答のナレッジ ベースを作成し、トレーニングします。 ナレッジ ベースのコンテンツは、架空の旅行代理店である Margie's Travel の Web サイトにある既存の FAQ ページから取得されます。 その後、それを顧客が使用したときに役に立つかどうかを、Language Studio を使用して確認します。

ボットを実装する場合の最初の手順は、質問と回答のペアから成るナレッジ ベースを作成することです。 これを組み込みの自然言語処理機能と共に使用することで、ボットは質問を解釈し、ユーザーにとって最も適切な回答を見つけることができます。

Azure AI Language には "質問応答" 機能が含まれています。それを使用してナレッジ ベースを作成します。** ナレッジ ベースは、質問と回答のペアを手動で入力することによって、あるいは既存のドキュメントまたは Web ページから作成できます。 Margie's Travel では既存の FAQ ドキュメントを使用したいと考えています。

言語サービスの質問応答機能を使用すると、質問と回答のペアを入力することによって、あるいは既存のドキュメントまたは Web ページからナレッジ ベースをすばやく作成できます。 その後、組み込みの自然言語処理機能を使用して、質問を解釈し、適切な回答を見つけ出します。

## "言語" リソースを作成する**

質問応答を使用するには、**言語**リソースが必要です。

1. 別のブラウザー タブで Azure portal ([https://portal.azure.com](https://portal.azure.com?azure-portal=true)) を開き、自分の Azure サブスクリプションに関連付けられている Microsoft アカウントを使用してサインインします。

1. **[&#65291;リソースの作成]** ボタンをクリックし、"言語サービス" を検索します。** **言語サービス**を**作成する**プランを選択します。 **[追加機能の選択]** ページが表示されます。 次の設定を使用します。
    - **追加機能の選択**:
        - **既定の機能**: "既定の機能はそのままにしておきます" ** 
        - **カスタム機能**: "カスタム質問応答を選択します"。**
     - **[リソースの作成を続行する]** を選択します
    ![カスタム質問応答を有効にして言語サービス リソースを作成する。](media/create-a-bot/create-language-service-resource.png)

1. **[言語の作成]** ページで、次の設定を指定します。
    - **プロジェクトの詳細**
        - **[サブスクリプション]**: *お使いの Azure サブスクリプション*。
        - **[リソース グループ]**: 既存のリソース グループを選択するか、新しいリソース グループを作成します。**
    - **インスタンスの詳細**
        - **[リージョン]**: *リージョンの選択*      
        - **名前**: "言語リソースの一意の名前"。**
        - **価格レベル**: S (1 分あたり 1,000 通話)
    - **カスタムの質問応答**
        - **Azure Search のリージョン**: "使用可能な任意の場所"。**
        - **Azure Search の価格レベル**: Free F (3 インデックス) - ("このレベルが利用できない場合は、[Basic] を選択します")**
    - **責任ある AI に関する通知**
        - **このボックスをオンにすることで、責任ある AI 通知の条項を承認し、同意したことを確認します**: "選択済み"。**

1. **[確認および作成]** を選択し、次に **[作成]** を選択します。 カスタム質問応答ナレッジ ベースをサポートする言語サービスがデプロイされるのを待ちます。

    > **注** 無料レベルの **Azure Cognitive Search** リソースを既にプロビジョニングしてある場合は、クォータにより、別のリソースを作成できない場合があります。 その場合は、**Free F** 以外のレベルを選択します。

## 新しいプロジェクトの作成

1. 新しいブラウザー タブで Language Studio ポータル ([https://language.azure.com](https://language.azure.com?azure-portal=true)) を開き、お使いの Azure サブスクリプションに関連付けられている Microsoft アカウントを使ってサインインします。
1. 言語リソースの選択を求めるメッセージが表示されたら、次の設定を選択します。
    - **Azure ディレクトリ**: "サブスクリプションを含む Azure ディレクトリ"。**
    - **Azure サブスクリプション**: *使用する Azure サブスクリプション*
    - **言語リソース**: "先ほど作成したリソース"。**

    言語リソースの選択を求めるメッセージが表示***されない***場合、原因として、お使いのサブスクリプションに複数の言語リソースが存在していることが考えられます。その場合は、次の操作を行います。
    1. ページの上部にあるバーで、**[設定] (&#9881;)** を選択します。      
    1. **[設定]** ページで、**[リソース]** タブを表示します。
    1. 先ほど作成した言語リソースを選択し、[**リソースの切り替え**] を選択します。
    1. ページの上部で、[**Language Studio**] を選択して、Language Studio のホーム ページに戻ります。

1. Language Studio ポータルの上部にある **[新規作成]** メニューで、**[カスタム質問応答]** を選択します。

    ![カスタムの質問応答](media/create-a-bot/create-custom-question-answering.png)

1. **[リソース (お使いのリソース) の言語設定を選択する]** ページで、 **[このリソースでプロジェクトを作成するときに言語を選択する]** を選択し、 **[次へ]** をクリックします。**
  ![言語を選択する](media/create-a-bot/create-project.png)

1. **[基本情報の入力]** ページで、次の詳細を入力し、**[次へ]** をクリックします。
    - **言語リソース**: "お使いの言語リソースを選択します"。**  
    - **Azure Search リソース**: "お使いの Azure Search リソースを選択します"。**
    - **名前**: `MargiesTravel`
    - **説明**: `A simple knowledge base`
    - **ソース言語**: 英語
    - **回答が返されない場合の既定の回答**: `No answer found`
1. **[確認と終了]** ページで、**[プロジェクトの作成]** を選択します。
1. **[ソースの管理]** ページが表示されます。 **[&#65291;ソースの追加]** を選択し、**[URL]** を選択します。
1. **[URL の追加]** ボックスで、**[+ URL の追加]** を選択します。 次のように入力し、 **[すべて追加]** を選択します。
    - **URL の名前**: `MargiesKB`
    - **URL**: `https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/main/data/natural-language/margies_faq.docx`
    - **ファイル構造の分類**: "自動検出"**
1. **[すべて追加]** を選択します。  

 ![URL の追加](media/create-a-bot/add-url.png)

## ナレッジ ベースを編集する

ナレッジ ベースは、FAQ ドキュメントの詳細と事前定義の応答に基づいて作成されます。 カスタムの質問と回答のペアを追加して、これらを補完することができます。

1. 左側のパネルを展開し、**[ナレッジ ベースの編集]** を選択します。 次に、**[+]** を選択して新しい質問ペアを追加します。
1. **[新しい質問応答ペアの追加]** ダイアログ ボックスで、**[質問]** に「`Hello`」と入力し、**[回答]** に「`Hi`」と入力して、**[完了]** を選択します。
1. **[Alternate questions]\(代替の質問\)** を展開し、**[+ Add alternate question]\(+ 代替の質問を追加する\)** を選択します。 次に、"Hello" の代替フレーズとして「`Hiya`」を入力します。
1. **[質問応答ペア]** ペインの上部にある **[保存]** を選択してナレッジ ベースを保存します。

## ナレッジ ベースのトレーニングとテスト

ナレッジ ベースが作成されたので、それをテストできます。

1. **[質問応答ペア]** ペインの上部にある **[テスト]** を選択してナレッジ ベースをテストします。
1. テスト ペインの下部に「`Hi`」というメッセージを入力します。 *Hi* という応答が返されます。
1. テスト ペインの下部に「`I want to book a flight`」というメッセージを入力します。 FAQ から適切な応答が返されるはずです。

    > **注** 応答には、"短い回答" とより詳細な "回答文節" が含まれています。回答文節には、最も一致する質問の FAQ ドキュメントの全文が表示され、短い回答は文節からインテリジェントに抽出されます。** ** テスト ペインの上部にある **[短い回答を表示する]** チェック ボックスを使用して、応答から短い回答を得るかどうかを制御できます。

1. `How can I cancel a reservation?` のような別の質問を試してみてください
1. ナレッジ ベースのテストが完了したら、**[テスト]** を選択してテスト ペインを閉じます。

## ナレッジ ベース用のボットを作成する

ナレッジ ベースでは、クライアント アプリケーションが何らかの種類のユーザー インターフェイスを介して質問に回答するために使用できるバック エンド サービスが提供されます。 一般に、これらのクライアント アプリケーションはボットです。 ナレッジ ベースをボットで使用するには、HTTP を使用してアクセスできるサービスとして公開する必要があります。 次に、Azure Bot Service を使用して、ナレッジ ベースを使用してユーザーの質問に回答するボットを作成およびホストできます。

1. 左側のパネルで、**[ナレッジ ベースのデプロイ]** を選択します。
1. ページの上部で、**[デプロイ]** を選択します。 プロジェクトを配置するかどうかを確認するダイアログ ボックスが表示されます。 **[デプロイ]** を選択します。

 ![ナレッジ ベースをデプロイします。](media/create-a-bot/deploy-knowledge-base.png)

1. サービスがデプロイされたら、**[ボットの作成]** を選択します。 これにより、Azure portal が新しいブラウザー タブで開き、お使いの Azure サブスクリプションで Web アプリ ボットを作成できます。
1. Azure portal で **Web アプリ ボット**を作成します。 (テンプレートのソースが信頼できるかどうかをチェックする警告メッセージが表示される場合があります。 そのメッセージに対してアクションを実行する必要はありません。) 次の設定を更新して続行します。

    - **プロジェクトの詳細**
        - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
        - **[リソース グループ]** : *言語リソースを含むリソース グループ*
    - **インスタンスの詳細**
        - **リソース グループの場所**: "*言語サービスと同じ場所*"。
    - **Azure Bot**
        - **[ボット ハンドル]** : "*ボットの一意の名前*" ("*事前に設定済み*")
    - **[料金レベルの選択]**
        - **価格レベル**: Free (F0) ( *[プランの変更]* の選択が必要な場合があります)
    - **Microsoft アプリ ID**
        - **作成の種類**: "**[新しいユーザー割り当てマネージド ID の作成]** を選択します"** 

5. **[次へ]** を選択して、設定の更新を続行します。 
    - **App Service**
        - **[アプリ名]**: ***ボット ハンドル**と同じ名前に **.azurewebsites.net** が自動的に付加されます*
        - **[SDK 言語]**: *C# または Node.js を選択します*
    - **App Service プラン**
        - **作成の種類**: "**[新しい App Service プランの作成]** を選択します"**
    - **アプリ設定**
        - **言語リソース キー**: "言語リソース キーをコピーし、ここに貼り付ける必要があります。"**
            - 別のブラウザー タブを開き、Azure portal ([https://portal.azure.com](https://portal.azure.com?azure-portal=true)) に移動します。
            - 言語サービス リソースに移動します。
            - **[キーとエンドポイント]** ページで、いずれかのキーをコピーします
            - ここに貼り付けます。
        - **言語プロジェクト名**: MargiesTravel
        - **言語サービス エンドポイントのホスト名**: "*言語サービス エンドポイントを使用して事前に設定されています*"
    - **言語サービスの詳細**
        - **サブスクリプション ID**: "*サブスクリプション ID を使用して事前に設定されています*"
        - **リソース グループ名**: "*リソース グループ名を使用して事前に設定されています*"
        - **アカウント名**: "*リソース名を使用して事前に設定されています*"

1. **［作成］** を選択します その後、ボットが作成されるのを待ちます (ベルのように見える右上の通知アイコンが、待つ間アニメーション化されます)。 次に、デプロイが完了したという通知で、**[リソースに移動]** を選択します (または、ホーム ページで **[リソース グループ]** をクリックし、ボットを作成したリソース グループを開いて、**Azure ボット** リソースを選択します)。
1. ボットの左側のペインで、**[設定]** を探し、**[Web チャットでテストする]** を選択して、ボットが **Hello and Welcome** というメッセージを表示するまで待ちます (初期化に数秒かかることがあります)。
1. テスト チャット インターフェイスを使用して、ボットがナレッジ ベースから期待どおりに質問に回答することを確認します。 たとえば、`I need to cancel my hotel` を送信してみます。

ボットを使ってみます。 FAQ にある質問に対しては正確に回答できるはずですが、トレーニングされていない質問を解釈する機能は限られています。 いつでも Language Studio ポータルを使用して、ナレッジベースを編集し、改善して、再公開することができます。

## クリーンアップ

その他の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. [Azure portal]( https://portal.azure.com) を開き、作成したリソースを含むリソース グループを選択します。 
1. リソースを選択し、**[削除]** を、次に **[はい]** を選択して確定します。 これでリソースが削除されます。

## 詳細情報

- 質問応答サービスの詳細については、[こちらのドキュメント](https://docs.microsoft.com/azure/cognitive-services/language-service/question-answering/overview)を参照してください。
- Microsoft Bot Service の詳細については、[Azure Bot Service のページ](https://azure.microsoft.com/services/bot-service/)を参照してください。