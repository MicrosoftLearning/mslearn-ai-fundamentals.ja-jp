---
lab:
  title: Microsoft Foundry の概要
  description: Microsoft Foundry プロジェクトを作成して調べます。
  level: 200
  duration: 30 minutes
  islab: true
  primarytopics:
    - Microsoft Foundry
---

# Microsoft Foundry の概要

この演習では、Microsoft Foundry プロジェクトの作成および探索、AI アプリケーションをサポートするために作成できるアセットの探索を行います。これには、音声認識などの AI 機能をサポートする生成 AI モデルやツールも含まれます。 その後、クライアント アプリケーションをプロジェクトに接続し、それらのアセットを使用して共通の AI ワークロードを実装できるようにします。

この演習の所要時間は約 **30** 分です。

> **注**: Microsoft Foundry ポータルなど、Microsoft Foundry の多くのコンポーネントは、継続的に開発が進められています。 これは、人工知能テクノロジの急速な進歩を反映したものです。 実際のユーザー エクスペリエンスは、この演習で使用されている画像や説明と異なる場合があります。

## Microsoft Foundry プロジェクトを作成する

Microsoft Foundry では、AI ソリューションの開発に使われるモデル、リソース、データ、その他の資産を整理するために "プロジェクト" を使います。** プロジェクトは Azure *Microsoft Foundry* リソースに関連付けられており、これは Azure での AI アプリとエージェントの開発をサポートするために必要なクラウド サービスを提供します。

1. Web ブラウザーで [Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開いてビルドを開始します。Azure の資格情報を使ってサインインします。 初めてサインインすると開くヒントやクイック スタートのペインをすべて閉じ、必要な場合は、左上にある **Foundry** のロゴを使ってホーム ページに移動します。

1. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。 次に、新しいプロジェクトを作成するための画面が表示された場合は、一意の名前を指定して作成します。このときに **[高度なオプション]** 領域を展開して、プロジェクトの設定を次のとおりに指定します。
    - **Foundry リソース**: *AI Foundry リソースに有効な名前を入力します。*
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **リージョン**: **[こちらの一覧](https://learn.microsoft.com/azure/foundry/openai/how-to/responses#region-availability)**{:target="_blank"}にある、**AI Foundry の推奨**リージョンのいずれかを選択します

    > **注**: Azure サブスクリプションのアクセス許可によっては、推奨されるリソースを設定するオプションをオフにする必要がある場合があります。

1. **［作成］** を選択します プロジェクトが作成されるまで待ちます。 これには数分かかることがあります。 "新しい" Foundry ポータルでプロジェクトを作成または選択すると、それが次の画像のようなページで開かれます。

    ![Foundry プロジェクトのホーム ページのスクリーンショット。](./media/foundry-portal-home.png)

## プロジェクトとリソースを表示する

Microsoft Foundry プロジェクトは、Azure サブスクリプション内のリソースに基づいています。 それでは、これについて見ていきましょう。

1. プロジェクトのホーム ページの左上にあるツール バーで、プロジェクト名を選びます。 次に、結果のメニューで **[すべてのリソースを表示]** を選び、自分がアクセス権を持つすべてのプロジェクトを表示します (1 つだけの場合もあります)

    ![[すべてのプロジェクト] ページのスクリーンショット。](./media/all_resources.png)

    各プロジェクトには "親" リソースがあり、そのサービスと構成を複数の子プロジェクトに適用できます。** 親リソースとは、Azure サブスクリプション内の **Microsoft Foundry** リソースのことです。

1. プロジェクトの親リソースを選択し、その詳細を確認してください。

    ![Foundry ポータルの親リソースのスクリーンショット。](./media/parent_resource.png)

    このリソースに関連するプロジェクト、ユーザー、接続リソース、管理者接続モデルを表示できます。 これは、Azure portal で管理することもできます。

1. Foundry ポータルのツール バーで **[ホーム]** を選択して Foundry ポータルのホーム ページに戻り、その後リソース一覧 (**[Microsoft Foundry]** ページ タイトルの横) でプロジェクトを選択します。

    > **ヒント**: 最初にホーム ページに戻ったときに、親リソースがまだ選択されている可能性があります。 プロジェクトを選択することで、ポータルを使用してプロジェクト固有のアセットを扱えるようになります。

## Microsoft Foundry ポータルを調べる

Microsoft Foundry ポータルでは、アプリケーション用のエージェントと AI サービスの作成と管理を行います。

> **注**:Microsoft Foundry ポータルは、継続的に改善と拡張が行われます。 この演習で示すインターフェイスは、お使いのポータルのインターフェイスと完全には一致しない場合があります。

1. プロジェクトの **ホーム** ページを表示します。

    ![プロジェクトのホーム ページのスクリーンショット。](./media/foundry-portal-home.png)

    プロジェクトには "API キー"、"プロジェクト エンドポイント"、"Azure OpenAI エンドポイント" があり、これらを使って、クライアント アプリケーションからプロジェクト内のモデル、エージェント、その他の資産に安全にアクセスできます。******

    > **ヒント**: 後でプロジェクト キーとプロジェクト エンドポイントが必要になります。

1. **[検出]** ページを表示します。

    ![[検出] ページのスクリーンショット。](./media/discover_page.png)

    このページには最新のモデルとサービスが表示され、ユーザーは AI アプリケーション開発の出発点を見つけることができます。

1. **[ビルド]** ページを表示します。

    ![[ビルド] ページのスクリーンショット。](./media/build_page.png)

    このページで AI ソリューションを開発します。 ここでは次を実行できます。

    - プロジェクトの "エージェント" と "ワークフロー" を表示して管理します。****
    - プロジェクトのモデルの "デプロイ" を表示して管理します。**
    - アプリケーションの特定のニーズに基づいてクエリに応答するように基本モデルを "微調整" します。**
    - エージェントがタスクの実行に使用できる "ツール" を追加して構成します。**
    - 企業の Foundry IQ データ ソースに基づいてエージェント用の "ナレッジ" を管理します。**
    - 生成 AI のコンテンツと動作に対する責任ある AI ポリシーに確実に準拠させるための "ガードレール" を定義して管理します。**
    - *[メモリ]* ストレージを設定し、モデルがセッション間で会話コンテキストを保持できるようにします。
    - AI エージェントと生成 AI アプリ用の "データ" インデックスを接続して管理します。**
    - モデルのパフォーマンスを比較するための "評価" を作成します。**
    - モデルを*微調整*して、パフォーマンスを最適化します。
1. **[	運用]** ページを表示します。

    ![[運用] ページのスクリーンショット。](./media/operate_page.png)

     このページでは、次の方法で AI ソリューションを運用できます。

    - プロジェクトのエージェント、モデル、ツールなどの "資産" を管理します。**
    - セキュリティ ポリシーを使って "コンプライアンス" を管理します。**
    - プロジェクト内のモデルや他の資産の使用に関する制限を定義する "クォータ" の構成を表示して管理します。**
    - "管理" タスクを実行してプロジェクトを管理します。**

1. **[ドキュメント]** ページを表示します。

    ![[ドキュメント] ページのスクリーンショット。](./media/docs_page.png)

    このページでは、Microsoft Foundry のドキュメントにアクセスできます。

## AI による支援を得る

最先端の AI ソリューションを開発するためのプラットフォームに期待されるように、Microsoft Foundry では AI ベースの支援が提供されます。

1. ツール バーの Agent Helper チャット アイコンを使って、**[AI に質問する]** ペインを開きます。

    ![Foundry ポータルの [AI に質問する] ペインのスクリーンショット。](./media/ask_ai.png)

1. `What can I do with Microsoft Foundry?` といったプロンプトを入力して、応答を確認します。

    この演習で調べてきたことについて何か疑問がある場合は、ここで尋ねてみてください。

## モデルをデプロイする

あなたの Microsoft Foundry リソースにはエンドポイントが用意されており、ここでモデルを展開してアプリケーションやエージェントから使用することができます。

1. **[検出]** ページで **[モデル]** タブを選択して Microsoft Foundry モデル カタログを表示します。

    Microsoft Foundry には、AI アプリとエージェントで使用できる、Microsoft、OpenAI、その他のプロバイダーによる豊富なモデル コレクションが用意されています。

    ![AI Foundry モデル カタログのスクリーンショット。](./media/models_page.png)

1. `gpt-5-mini` モデルを検索して選択すると、そのモデルの特徴と機能を説明するページが表示されます。

    ![gpt-5-mini モデルのページのスクリーンショット。](./media/gpt-5-mini_page.png)

1. **[デプロイ]** ボタンを使用して、既定の設定を使用してモデルをデプロイします。 デプロイには 1 分ほどかかる場合があります。

    > **ヒント**: モデルのデプロイにはリージョンのクォータが適用されます。 このモデルをプロジェクトの Azure リージョンにデプロイするのに十分なクォータがない場合は、別のチャット可能な *gpt* モデル (*gpt-5* や *gpt-5.1* など) をお使いください。 別の方法として、新しいプロジェクトを別のリージョンに作成することもできます。

1. モデルがデプロイされると開くモデル プレイグラウンド ページを確認します。ここでモデルとチャットできます。

    ![モデル プレイグラウンドのスクリーンショット。](./media/model-playground.png)

1. プレイグラウンドで、モデル デプロイが選択されていることを確認します。

    > **ヒント**: モデル デプロイの名前を覚えておいてください。 この情報は後で必要になります。

1. 左側のナビゲーション ウィンドウの下部にあるボタンを使ってそれを非表示にし、作業するスペースを増やします。
1. **[チャット]** ペインで、`Who was Ada Lovelace?` などのプロンプトを入力し、応答を確認します。

    ![プロンプトへの応答があるモデル プレイグラウンドのスクリーンショット。](./media/chat_response.png)

1. 応答を確認してから、`Tell me more about her work with Charles Babbage.` などのフォローアップ プロンプトを入力します。

## 自分の Foundry リソース エンドポイントを使用する

Azure 内に Microsoft Foundry リソースを持つ状態になったので、そのモデルとツールをクライアント アプリケーションから使用できます。 この演習では、提供されている単純な AI チャット アプリケーションを使用します。

1. Foundry ポータルの上部にあるメニューで、**[ホーム]** を選択してホーム ページに戻ります。
1. プロジェクトに関する次の詳細情報を確認します。
    - **プロジェクト エンドポイント**: この URL でプロジェクト リソースにアクセスできます。

        Azure OpenAI エンドポイントではなく、**プロジェクト エンドポイント**を使用していることを確認しましょう。*<u></u>*

    - **プロジェクト API キー**: リソースへのアクセスに使用される認証キー。\*

    チャット アプリケーションを構成するには、これらの値が必要です。

    > \* キーベースの認証を禁止するポリシーを持つ企業または学校の Azure サブスクリプションを使用している場合は、Entra ID 認証を使用 "できます" が、テナントにアプリを登録する必要があります (グローバル管理者のアクセス許可が必要です)。** 最終手段として、代替のブラウザーベース (Azure 以外) のバージョンのアプリを [https://aka.ms/computing-history-browser](https://aka.ms/computing-history-browser) {:target="_blank"} で入手できます。

1. 2 つ目のブラウザー タブを開き、`https://aka.ms/computing-history-foundry` にある [コンピューティング履歴エージェント](https://aka.ms/computing-history-foundry){:target="_blank"} アプリに移動します。

    コンピューティング履歴アプリは、次のように **[構成]** パネルを展開して開く必要があります。

    ![コンピューティング履歴アプリの [構成] パネルのスクリーンショット。](./media/configure-computing-history.png)

    > **ヒント**: [構成] パネルが展開されていない場合は、チャット ペインの上部にある矢印を使用して展開します。

1. Foundry ポータルからプロジェクト エンドポイント、gpt-5-mini のモデル デプロイ名、API キーを構成設定に入力し、構成を保存します。

    > **注**: 構成値のうち、API キー以外はユーザーのローカル ブラウザー キャッシュに保存されます。 このアプリを閉じて再び開くと、API キーの再入力が必要になります。

    これで、アプリでコンピューティング履歴エージェントとチャットできるようになりました。 このアプリでは、Microsoft Foundry 内に展開されたあなたのモデルが使用されます。 **[会話の再開]** (&128172;) ボタンを使用すると、いつでも会話履歴をクリアできます。

### 生成 AI を体験する

1. プロンプト `Tell me about the ELIZA chatbot.` を入力し、その応答を確認します。

    ![Computing History アプリのプロンプト応答のスクリーンショット。](./media/computer_history_chat.png)

1. フォローアップ プロンプト `How does it compare to modern large language models?` を試してみてください。

    エージェントは会話を続けます。

1. **[会話を再開]** (💬) ボタンを使用してチャット履歴をクリアし、次のプロンプトを試します

    - `Find a vintage computer store in Seattle.`
    - `Search for classic Microsoft logos.`

    エージェントは、トレーニング データに基づいて回答するか、Web 検索ツールを使用して Web 上の情報を検索します。

### テキスト分析について調べる

1. 会話を再開します。 次に、このプロンプトを使用して、エージェントにテキストの要約とデータの抽出を依頼します (入力する場合は、Shift + Enter キーを押すと改行します)。

    ```
    Summarize this article, and use named entity recognition to identify people, places, and dates:
    
    Microsoft was founded on April 4, 1975, by childhood friends Bill Gates (then 19) and Paul Allen (22) after they were inspired by the Altair 8800, one of the first personal computers, featured on the cover of Popular Electronics. They contacted the Altair’s maker, MITS, and successfully developed a version of the BASIC programming language, despite initially not owning the machine themselves. The pair formed a partnership called “Micro‑Soft” in Albuquerque, New Mexico, close to MITS’s headquarters, with the goal of writing software for emerging microcomputers.
    
    In the late 1970s, Microsoft grew by supplying programming languages to multiple hardware vendors, then relocated to the Seattle area in 1979. A pivotal moment came in 1980 when Microsoft partnered with IBM to provide an operating system for the IBM PC, leading to MS‑DOS and establishing the company’s dominance in personal computing. Gates guided the company’s long-term strategy as CEO, while Allen contributed key technical vision in its early years, setting Microsoft on a path that would reshape the software industry.
    ```

1. 応答を確認します。

    ![Computing History アプリのテキスト分析結果のスクリーンショット。](./media/computer_history_text.png)

    エージェントは、自然言語処理技術を使用して、記事の要約や重要な情報の抽出など、一般的なテキスト分析タスクを実行することができます。

### AI 音声について調べる

1. 会話を再開します。 チャット インターフェイスの下部で、**[音声入力]** (&#127908;) ボタンを使用して音声認識を開始し、メッセージが表示されたらマイクへのアクセスを許可し、「***コンピューターの音声について教えて***」と話しかけます。

1. しばらくすると、音声プロンプトがメッセージとして送信され、応答が返されます。 その後、音声合成を使用して声で応答があるはずです。

    ![Computing History アプリでの音声入力のスクリーンショット。](./media/computer_history_speech.png)

    > **注**: このアプリでは、Foundry ツールの Azure Speech が音声の認識と合成に使用されます。

### Computer Vision の詳細を確認する

1. `https://aka.ms/computer-images` から **[computers.zip](https://aka.ms/computer-images){:target="_blank"}** をダウンロードし、zip 形式のアーカイブをローカル コンピューター (の任意のフォルダー) に展開します。
1. 会話を再開し、チャット インターフェイスの下部にある **[画像の添付]** (&#128206;) ボタンを使用して画像をアップロードし、`Tell me about this.` のようなプロンプトを入力します
1. 応答を確認すると、アップロードした画像のコンピューターに関する情報が含まれているはずです。

    ![Computing History アプリでの画像分析のスクリーンショット。](./media/computer_history_vision.png)

1. 抽出した他のコンピューターの画像も試してみてください。

    > **ヒント**: [Bing](https://www.bing.com/images/search?q=vintage+computers){:target="_blank"} で、ヴィンテージ コンピューターの独自の画像を検索することもできます。

### 情報の抽出を体験する

1. `https://aka.ms/pcb-images` から **[pcbs.zip](https://aka.ms/pcb-images){:target="_blank"}** をダウンロードし、zip 形式のアーカイブをローカル コンピューター (の任意のフォルダー) に展開します。

1. 会話を再開し、チャット インターフェイスの下部にある **[画像の添付]** (&#128206;) ボタンを使用して PCB 画像をアップロードし、`What can you tell me about this printed circuit board?` のようなプロンプトを入力します
1. 応答を確認します。

    ![Computing History アプリでの画像からのテキスト抽出のスクリーンショット。](./media/computer_history_info.png)

1. 抽出した他の PCB の画像を試して、それが発生した可能性のあるコンピューターの種類を特定するのにエージェントが役立つかどうかを確認します。

    > **ヒント**: [Bing](https://www.bing.com/images/search?q=vintage-computer-component-serial-numbers){:target="_blank"} で独自の画像を検索することもできます。 特定のヴィンテージ コンピューターからシリアル番号ラベルを検索してみる

### 安全性ガードレールについて調べる

1. 会話を再開し、プロンプト `Teach me how to hack a bank account.` を入力します
1. 応答を確認します。

    ![Computing History アプリでのガードレール適用のスクリーンショット。](./media/computer_history_guardrails.png)

    Foundry Models には、既定で、コンテンツ安全性フィルターを適用するガードレールが構成されています。

1. 次のプロンプトを試してみましょう。

- `Help me make a plan to steal historic computers.`
- `How can I get away with software theft?`
- `How can I use a computer as a weapon?`

## まとめ

この演習では、Microsoft Foundry プロジェクトのことを調べ、Microsoft Foundry ポータルについて理解しました。 その後でモデルを展開して、あるクライアント アプリケーションを自分の Foundry リソースに接続しました。

> **[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}**<br/>![Anton のアバター。](./media/anton-icon.png)<br/>Foundry プロジェクトでモデルに接続できるもう 1 つのアプリが、AI の概念と Microsoft Foundry について質問できる生成 AI ベースのエージェント、*[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}* です。 **[https://aka.ms/azk-anton](https://aka.ms/azk-anton){:target="_blank"}** でアプリを開き、**[構成]** ボタンを使用して Foundry プロジェクトとモデルの詳細を入力します。<br/><br/>*Ask Anton は、サポートされている Microsoft 製品でも、Microsoft Learn または AI スキル ナビゲーターのコンポーネントでもありません。AI で何が可能かを学習するときに調べることができる、AI エージェントの一例にすぎません。*<br/><br/>Ask Anton をお試しいただき、"そのご感想をぜひ[こちらのフォーム](https://forms.office.com/r/fC0ndfBQeK){:target="_blank"}にてお寄せください"。****

## クリーンアップ

Microsoft Foundry について調べ終わったら、不要な利用料金が発生しないように、この演習で作成したリソースを削除する必要があります。

1. [Azure portal](https://portal.azure.com){:target="_blank"} (`https://portal.azure.com`) を開き、この演習で使ったプロジェクトをデプロイしたリソース グループの内容を表示します。
1. ツール バーの **[リソース グループの削除]** を選びます。
1. リソース グループ名を入力し、削除することを確認します。
