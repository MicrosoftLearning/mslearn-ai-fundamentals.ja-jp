---
lab:
  title: Microsoft Foundry で生成 AI とエージェントの使用を開始する
  description: Microsoft Foundry を使用して、生成 AI モデルをデプロイし、エージェントを作成します。
---

# Microsoft Foundry で生成 AI とエージェントの使用を開始する

この演習では、Microsoft Foundry を使用して、生成 AI モデルをデプロイし、確認します。 次に、ユーザーの質問に回答するナレッジ ツールを備えたエージェントでモデルを使用します。

この演習の所要時間は約 **45** 分です。

## Microsoft Foundry プロジェクトを作成する

Microsoft Foundry で "プロジェクト" を使用して、AI ソリューションの開発に使用されるモデル、リソース、データ、その他の資産を整理します。**

1. Web ブラウザーで [Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開き、Azure の資格情報を使ってサインインします。 初めてサインインすると開くヒントやクイック スタートのペインをすべて閉じ、必要な場合は、左上にある **Foundry** のロゴを使ってホーム ページに移動します。
1. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。 次に、メッセージが表示されたら、既定のオプションを使用して、任意の一意の名前で新しいプロジェクトを作成します。 新しい Foundry ポータルでプロジェクトを作成または選択すると、それが次の画像のようなページで開かれます。

    ![AI Foundry プロジェクトのホーム ページのスクリーンショット。](./media/0-foundry-project.png)

## モデルをデプロイする

あらゆる生成 AI アプリまたはエージェントの中心には言語モデルがあります。通常は大規模言語モデル (LLM) ですが、場合によってはよりコンパクトな小規模言語モデル (SLM) が使用されることもあります。

1. **[ビルドの開始]** メニューの **[モデルの参照]** を選択して、Microsoft Foundry のモデル カタログを表示します。

    Microsoft Foundry には、AI アプリとエージェントで使用できる、Microsoft、OpenAI、その他のプロバイダーによる豊富なモデル コレクションが用意されています。

    ![AI Foundry モデル カタログのスクリーンショット。](./media/0-foundry-models.png)

1. `gpt-4.1-mini` モデルを検索して選択すると、そのモデルの特徴と機能を説明するページが表示されます。

    ![gpt-4.1-mini モデル ページのスクリーンショット。](./media/0-gpt-4.1-mini.png)

1. **[デプロイ]** ボタンを使用して、既定の設定を使用してモデルをデプロイします。 デプロイには 1 分ほどかかる場合があります。
1. モデルがデプロイされると開くモデル プレイグラウンド ページを確認します。ここでモデルとチャットできます。

    ![モデル プレイグラウンドのスクリーンショット。](./media/0-model-playground.png)

## モデルとチャットする

プレイグラウンドを使用すると、モデルとチャットし、指示 ("システム プロンプト" とも呼ばれます) やパラメーターなどの設定の変更による影響を観察して、モデルを確認することができます。**

1. 左側のナビゲーション ウィンドウの下部にあるボタンを使ってそれを非表示にし、作業するスペースを増やします。
1. **[チャット]** ペインで、`Who was Ada Lovelace?` などのプロンプトを入力し、応答を確認します。

    ![応答が表示されている [チャット] ペインのスクリーンショット。](./media/0-chat-response.png)

1. `Tell me more about her work with Charles Babbage.` などのフォローアップ プロンプトを入力し、応答を確認します。

    > **注**:多くの場合、生成 AI のチャット アプリケーションでは、プロンプトに会話履歴が含まれます。そのため、会話のコンテキストは後続のメッセージにも引き継がれます。 この場合、"her" は Ada Lovelace を指していると解釈されます。

1. チャット ペインの右上にある **[新しいチャット]** ボタンを使用して、会話を再開します。 こうすることで、すべての会話履歴は削除されます。
1. `Who was Alan Turing?` などの新しいプロンプトを入力し、応答を確認します。
1. `What is the Turing test?` や `What is a Turing machine?` などのプロンプトを使用して会話を続けます。

## システム プロンプトを試す

システム プロンプトは、応答をガイドする指示をモデルに提供するために使用します。 システム プロンプトを使用して、モデルの応答が何を含む必要があり、何を含んではならないかについて、形式、スタイル、制約に関するガイドラインを提供できます。

1. チャット ペインの上部にある **[新しいチャット]** ボタンを使用して、会話を再開します。 次に、`What was ENIAC?` などの新しいプロンプトを入力し、応答を確認します。
1. 左側のペインの **[指示]** テキスト領域で、システム プロンプトを次のように変更します: `You are an AI assistant that provides short and concise answers using simple language. Limit responses to a single sentence.`
1. 次に、前と同じプロンプト (`What was ENIAC?`) を試し、出力を確認します。
1. さまざまなシステム プロンプトを続けて試し、モデルによって返される応答の種類に影響を与えてみましょう。
1. 実験が終わったら、システム プロンプトを `You are an AI assistant that helps people find information.` に戻します

## モデル パラメーターを試す

モデル パラメーターはモデルがどのように動作するかを制御するもので、応答のサイズ ("トークン単位" で測定される) を制限し、応答の "創造性" の程度を制御するのに役立ちます。**

1. **[新しいチャット]** ボタンを使用して会話を再開します。
1. 左ペインのモデル名の横にある **[パラメーター]** を選択します。

    ![[パラメーター] アイコンの場所を示すスクリーンショット。](./media/0-chat-parameters.png)

1. *(i)* リンクを使用して説明を表示し、パラメーター設定を確認します。 次に、変更せずに `What is Moore's law?` のようなプロンプトを入力し、応答を確認します
1. パラメーター値を変更し、同じプロンプトを繰り返して実験します。 モデルと動作に違いがある場合があります。 たとえば、"**Temperature**" を変更すると、モデルの "次の単語" の選択のランダム性が変わり、温度を下げると "創造的な" 応答の構成が少なくなります。

    ***ヒント**:実行時間の長い応答は、チャット ペインの **[生成の停止]** ボタンを使用して停止できます。*

1. 実験が終わったら、パラメーターを元の値にリセットします。

## モデルとチャットするクライアント コードを表示する

プレイグラウンドでモデルから返された応答に満足したら、それを利用するクライアント アプリケーションを開発できます。 Microsoft Foundry には、デプロイされたモデルに接続してチャットするために使用できる REST API と複数の言語固有の SDK が用意されています。

1. **[チャット]** ペインで、**[コード]** タブを表示します。このタブには、クライアント アプリケーションがモデルとチャットするために使用できるサンプル コードが表示されます。 サンプル コードの上部で、次の設定を選択できます。
    - **API**:OpenAI API は、生成 AI モデルとの会話を実装するための一般的な標準です。 使用できる OpenAI API には 2 つのバリアントがあります。
        - **補完**:モデルにプロンプトを送信するために広く使用されているプログラム構文。
        - **応答**:スタンドアロン モデルと "エージェント" の両方と対話するアプリを構築する際に、より柔軟に対応できる新しい構文。**
    - **言語**:さまざまなプログラミング言語で、モデルを使用するコードを記述できます。具体的には、Python、 Microsoft C#、JavaScript などです。
    - **SDK**:クライアントとモデル間でやり取りされる低レベルな通信の詳細をカプセル化する各言語固有の SDK を使用することや、REST API を直接操作して、クライアントがモデルに送信する HTTP 要求メッセージを完全に制御することができます。
    - **認証**: Microsoft Foundry にデプロイされたモデルを使用するには、クライアント アプリケーションを認証する必要があります。 以下を使用して認証を実装できます。
        - **キーベースの認証**:クライアント アプリはセキュリティ キーを提示する必要があります (コード サンプルの上にあるキー アイコンを選択すると確認できます)
        - **Microsoft Entra ID 認証**:クライアント アプリは、そのアプリ (または現在のユーザー) に割り当てられている ID に基づいて認証トークンを提示します。

1. 次のコード オプションを選択します。
    - **API**:Responses API
    - **言語**: Python
    - **SDK**:OpenAI SDK
    - **認証**: キー認証

    結果のサンプルは次のコードのようになります。

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
        input="What is the capital of France?",
    )
    
    print(f"answer: {response.output[0]}")
    ```

    コードは、シークレット認証キー (**api_key** 変数を設定するためにコードにコピーする必要があります) を使用して、Microsoft Foundry プロジェクトのリソース エンドポイントに接続します。 次に、デプロイされたモデルを使用して、入力プロンプト (この場合は、ハードコーディングされた質問 "What is the capital of France?") からの応答を生成し、出力コンソールに応答を出力します。

    > **ヒント**: 職場または学校アカウントを使用して Azure にサインインしていて、Azure サブスクリプションに十分なアクセス許可がある場合は、VS Code for Web でサンプル コードを開いて実行し、編集を試すことができます。

1. コードの確認が完了したら、**[チャット]** タブに戻ります。

## モデル構成をエージェントとして保存する

スタンドアロン モデルを使用して生成 AI アプリを実装することもできますが、完全にエージェント化された AI エクスペリエンスを実現するには、モデル、その指示、追加機能を提供するツール構成を*エージェント*にカプセル化する必要があります。 この演習では、モデルを使用して、従業員の経費精算を支援するエージェントを強化します。

1. モデル プレイグラウンドの右上にある **[エージェントとして保存]** を選択します。 次に、プロンプトが表示されたら、新しいエージェントに `expenses-agent` という名前を付けます。

    エージェントが作成されると、エージェントを操作するための新しいプレイグラウンドが開きます。

    ![エージェント プレイグラウンドのスクリーンショット。](./media/0-agent-playground.png)

1. **[指示]** を `You are a helpful AI assistant who supports employees with expense claims.` に変更します
1. エージェント プレイグラウンドの上部にある **[保存]** を選択します。
1. 右ペインで、エージェントの定義が含まれている **[YAML]** タブを表示します。 定義には、次のように、モデル、そのパラメーター設定、指定した指示が含まれていることに注意してください。

    ```yml
    metadata:
      logo: Avatar_Default.svg
      description: ""
      modified_at: "1767997310"
    object: agent.version
    id: expenses-agent:2
    name: expenses-agent
    version: "2"
    description: ""
    created_at: 1767997284
    definition:
      kind: prompt
      model: gpt-4.1-mini
      instructions: You are a helpful AI assistant who supports employees with expense claims.
      temperature: 0.98
      top_p: 1
      tools: []
    ```

1. **[チャット]** タブに戻り、プロンプト `What can you do?` を入力します

    応答には、経費精算アドバイザーとしての役割をエージェントが "認識している" ことが示されるはずです。

    ![エージェントの機能を説明する応答のスクリーンショット。](./media/0-agent-capabilities.png)

1. 経費関連のプロンプトを入力します (例: `How much can I claim for a taxi?`)

    応答は一般的な内容になるでしょう。 正確ではあるものの、従業員にとって特に役立つ内容ではありません。 エージェントに会社の経費ポリシーと手順に関する知識を与える必要があります。

## エージェントにナレッジ ツールを追加する

エージェントは、タスクを実行したり情報を検索したりするために "ツール" を使用します。** 一般的な Web 検索ツールまたは単純なファイル検索ツールを使用してナレッジ ソースを提供できます。また、より包括的なエージェント ソリューションが必要な場合は、エージェントを企業内のデータ ソースに接続する *Microsoft Foundry IQ* ナレッジ ストアを作成することもできます。 この演習では、簡単なファイル検索ツールを使用します。

1. 新しいブラウザー タブを開き、**[expenses_policy.docx](https://graememalcolm.github.io/ai-labs/data/expenses_policy.docx){:target="_blank"}** (`https://graememalcolm.github.io/ai-labs/data/expenses_policy.docx`) を表示します。 これを使用して、エージェントが経費精算に関する質問に回答できるようになるナレッジ ソースを提供します。
1. **expenses_policy.docx** をローカル コンピューターにダウンロードします。
1. エージェント プレイグラウンドを含むタブに戻り、左ペインで、まだ展開されていない場合は **[ツール]** セクションを展開します。
1. **expenses_policy.docx** ファイルをアップロードし、既定のインデックス名で新しいインデックスを作成します。 インデックスが作成されたら、それをエージェントにアタッチします。
1. エージェント プレイグラウンドの上部にある **[保存]** ボタンを使用して、エージェントの定義を更新します。
1. 右ペインで、エージェントの定義が含まれている **[YAML]** タブを表示します。 定義には、追加したファイル検索ツールが含まれていることに注意してください。

    ```yml
    metadata:
      logo: Avatar_Default.svg
      description: ""
      modified_at: "1767999261"
    object: agent.version
    id: expenses-agent:3
    name: expenses-agent
    version: "3"
    description: ""
    created_at: 1767999232
    definition:
      kind: prompt
      model: gpt-4.1-mini
      instructions: You are a helpful AI assistant who supports employees with expense claims.
      temperature: 0.98
      top_p: 1
      tools:
        - type: file_search
          vector_store_ids:
            - vs_sYs3SP17fUcc3E7eJqWfgxBW
    ```

1. **[チャット]** タブに戻り、前と同じ経費関連のプロンプト (たとえば、`How much can I claim for a taxi?`) を入力して応答を表示します。

    今回は、経費データ ソースの情報に基づいた応答が表示されるはずです。

1. `What about a hotel?` や `Can I claim the cost of my dinner?` など、経費関連のプロンプトをいくつか試してみてください

## エージェントを使用するオプションを確認する

エージェントを作成したので、次は従業員が経費精算のガイダンスを受けられるようにクライアント アプリケーションを強化できます。

1. エージェント プレイグラウンドの上部にある **[プレビュー]** ドロップダウン リストで、**[エージェントのプレビュー]** を選択します。
1. 新しいタブに表示されるプレビュー Web ページで、`How do I submit an expense claim?` などのプロンプトを入力し、応答を確認します。

    ![エージェントのプレビュー ページのスクリーンショット。](./media/0-agent-preview.png)

1. さらにいくつかのプロンプトを送信して、エージェントのプレビューを確認します。 完了したら、プレビュー アプリを含むブラウザー タブを閉じて、エージェント プレイグラウンドに戻ります。
1. エージェント プレイグラウンドでは、**[発行]** ボタンを使用してエージェントを Azure のエンタープライズ アプリケーションとして発行し、Microsoft 365 および Teams 内で使用できることに注意してください。

    多くの場合、エージェント ソリューションを実装するには、経費精算サポート エージェントをエンタープライズ アプリケーションのエコシステム内で使用できるように発行するのが理想的な方法です。 ただし、カスタム アプリケーションからエージェントを使用したい場合もあるでしょう。 

1. **[チャット]** タブから **[コード]** タブに切り替えて、エージェントを使用するためのサンプル コードを表示します。 このコードには OpenAI Responses API を使用しますが、先ほど確認したモデルとチャットするコードとはエージェント固有の違いがいくつかあります。

    ```python
    # Before running the sample:
    #    pip install --pre azure-ai-projects>=2.0.0b1
    #    pip install azure-identity
    
    from azure.identity import DefaultAzureCredential
    from azure.ai.projects import AIProjectClient
    
    myEndpoint = "https://your-project-resource.services.ai.azure.com/api/projects/ai-project-123"
    
    project_client = AIProjectClient(
        endpoint=myEndpoint,
        credential=DefaultAzureCredential(),
    )
    
    myAgent = "expenses-agent"
    # Get an existing agent
    agent = project_client.agents.get(agent_name=myAgent)
    print(f"Retrieved agent: {agent.name}")
    
    openai_client = project_client.get_openai_client()
    
    # Reference the agent to get a response
    response = openai_client.responses.create(
        input=[{"role": "user", "content": "Tell me what you can help with."}],
        extra_body={"agent": {"name": agent.name, "type": "agent_reference"}},
    )
    
    print(f"Response output: {response.output_text}")
    ```

    > **ヒント**: 職場または学校アカウントを使用して Azure にサインインしていて、Azure サブスクリプションに十分なアクセス許可がある場合は、VS Code for Web でサンプル コードを開いて実行し、編集を試すことができます。

## まとめ

この演習では、Microsoft Foundry ポータルで生成 AI モデルを使用してチャットをデプロイする方法について説明しました。 次に、モデルをエージェントとして保存し、指示とツールを使用してエージェントを構成してから、エージェントをデプロイして使用するためのオプションを確認しました。

この演習で確認したエージェントは、Microsoft Foundry を使用すると生成 AI アプリとエージェントの開発をいかに迅速かつ簡単に開始できるかを示す簡単な例です。 この基盤から、エージェントがツールを使用して情報を検索し、タスクを自動化し、相互に連携して複雑なワークフローを実行する、包括的なエージェント ソリューションを構築できます。

## クリーンアップ

Microsoft Foundry について調べ終わったら、不要な利用料金が発生しないように、この演習で作成したリソースを削除する必要があります。

1. [Azure portal](https://portal.azure.com){:target="_blank"} (`https://portal.azure.com`) を開き、この演習で使ったプロジェクトをデプロイしたリソース グループの内容を表示します。
1. ツール バーの **[リソース グループの削除]** を選びます。
1. リソース グループ名を入力し、削除することを確認します。