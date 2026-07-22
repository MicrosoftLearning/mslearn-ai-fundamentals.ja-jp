---
lab:
  title: Microsoft Foundry で生成 AI とエージェントの使用を開始する
  description: Microsoft Foundry を使用して、生成 AI モデルをデプロイし、エージェントを作成します。
  level: 200
  duration: 35 minutes
  islab: true
  primarytopics:
    - Microsoft Foundry
---

# Microsoft Foundry で生成 AI とエージェントの使用を開始する

このラボでは、Microsoft Foundry を使用して、コンピューティングの歴史に関する情報や専門知識を提供する AI エージェントを開発します。

> **注**: Microsoft Foundry ポータルなど、Microsoft Foundry の多くのコンポーネントは、継続的に開発が進められています。 これは、人工知能テクノロジの急速な進歩を反映したものです。 実際のユーザー エクスペリエンスは、この演習で使用されている画像や説明と異なる場合があります。

このラボの完了には約 **35** 分かかります。

## Microsoft Foundry プロジェクトを作成する

Microsoft Foundry では "プロジェクト" を使って、AI ソリューションの開発に使われるモデル、リソース、データ、その他の資産を整理します。**

1. Web ブラウザーで、[Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開いてビルドを開始します。Azure の資格情報を使ってサインインします。 初めてサインインすると開くヒントやクイック スタートのペインをすべて閉じ、必要な場合は、左上にある **Foundry** のロゴを使ってホーム ページに移動します。

1. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。 次に、新しいプロジェクトを作成するための画面が表示された場合は、一意の名前を指定して作成します。このときに **[高度なオプション]** 領域を展開して、プロジェクトの設定を次のとおりに指定します。
    - **Foundry リソース**: "Foundry リソースの有効な名前"。**
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **リージョン**: [こちらの一覧](https://learn.microsoft.com/azure/foundry/openai/how-to/responses#region-availability){:target="_blank"}にある、**AI Foundry の推奨**リージョンのいずれかを選択します

    > **注**: Azure サブスクリプションのアクセス許可によっては、推奨されるリソースを設定するオプションをオフにする必要がある場合があります。

1. プロジェクトが作成されるまで待ちます。 これには数分かかることがあります。 次に、表示されているウェルカム ダイアログを閉じます。

    "新しい" Foundry ポータルでプロジェクトを作成または選択すると、それが次の画像のようなページで開かれます。

    ![Foundry プロジェクトのホーム ページのスクリーンショット。](./media/foundry-portal-home.png)

## モデルをデプロイする

すべての AI エージェントの中心には、大規模言語モデル (LLM) があります。 その 1 つを Foundry のモデル カタログで探してみましょう。

1. これで、モデルを探索する準備ができました。 **[検出]** ページで **[モデル]** タブを選択して Microsoft Foundry モデル カタログを表示します。

    Microsoft Foundry には、AI アプリとエージェントで使用できる、Microsoft、OpenAI、その他のプロバイダーによる豊富なモデル コレクションが用意されています。

    ![AI Foundry モデル カタログのスクリーンショット。](./media/0-foundry-models.png)

1. `gpt-5-mini` モデルを検索して選択すると、そのモデルの特徴と機能を説明するページが表示されます。

    ![gpt-5-mini モデルのページのスクリーンショット。](./media/gpt-5-mini.png)

1. **[デプロイ]** ボタンを使用して、既定の設定を使用してモデルをデプロイします。 デプロイには 1 分ほどかかる場合があります。

    > **ヒント**: モデルのデプロイにはリージョンのクォータが適用されます。 このモデルをプロジェクトのリージョンにデプロイするのに十分なクォータがない場合は、別の *gpt* チャット対応モデル (*gpt-5-nano*、*gpt-5.4-mini* など) を使用できます。 別の方法として、新しいプロジェクトを別のリージョンに作成することもできます。

1. モデルがデプロイされると開くモデル プレイグラウンド ページを確認します。ここでモデルとチャットできます。

    ![モデル プレイグラウンドのスクリーンショット。](./media/0-model-playground.png)

## モデルとチャットする

プレイグラウンドを使用して、モデルとチャットすると、モデルを探索できます。

1. 左側のナビゲーション ウィンドウの下部にあるボタンを使ってそれを非表示にし、作業するスペースを増やします。
1. **[チャット]** ペインで、`Who was Ada Lovelace?` などのプロンプトを入力し、応答を確認します。

    ![応答が表示されている [チャット] ペインのスクリーンショット。](./media/0-chat-response.png)

1. `Tell me more about her work with Charles Babbage.` などのフォローアップ プロンプトを入力し、応答を確認します。

    > **注**:多くの場合、生成 AI のチャット アプリケーションでは、プロンプトに会話履歴が含まれます。そのため、会話のコンテキストは後続のメッセージにも引き継がれます。 この場合、"her" は Ada Lovelace を指していると解釈されます。

## "指示" を指定する**

特定のユース ケースをサポートするには、"システム プロンプト" を使用して応答をガイドする手順をモデルに提供する必要があります。** システム プロンプトを使用して、モデルに特定のフォーカスまたはロールを与え、モデルの応答に含める必要がある、および含めてはならない内容について、形式、スタイル、制約に関するガイドラインを提供できます。

1. モデル プレイグラウンドで、チャット ペインの右上にある **[新しいチャット]** ボタンを使用して会話を再開し、会話履歴を削除します。
1. 左側のペインの **[指示]** テキスト領域で、システム プロンプトを次のように変更します:

    ```
   You are an expert in the history of computing and AI. You only answer questions about significant people and events in the development of computing, and about notable vintage computers. Do not engage in conversations on any topic that is unrelated to computing history.
    ```

1. `Tell me about ELIZA.` などの新しいプロンプトを入力し、応答を確認します。
1. `How does it compare with modern LLMs?` などのプロンプトを使用して会話を続けます。
1. トピック外の質問 (たとえば、`What's the capital of Spain?` など) を試してみて、その応答を表示します。

## web_search ツールを追加する

これまでのところ、このモデルはトレーニングに使用されたデータに基づいて質問に回答してきました。 これは有用ではありますが、Web 上の最新情報の多くが除外されています。それらの情報は、モデルがより関連性の高い回答を提示するのに役立つ可能性があります。

"ツール" を使用して、モデルに外部データ ソースへのアクセスを付与したり、カスタム タスクを実行したりすることができます。** モデルが Web で最新の情報を検索できるようにするツールを追加してみましょう。

1. 左側のペインで、指示の下にある **[ツール]** セクションがまだ展開されていない場合は展開します。
1. **[追加]** ドロップダウン リストで、**[Web 検索]** を有効にします。 次に、ツールに関する情報を読みます。
1. モデル プレイグラウンドで、チャット ペインの右上にある **[新しいチャット]** ボタンを使用して、会話を再開します。
1. 左側のペインに一覧表示されている *web_search* ツールを使用し、チャット ペインでプロンプト `Find a vintage computer store near Seattle` ("または最寄りの都市") を入力し、応答を確認します。**

    モデルは、Web で特定の都市に近いヴィンテージ コンピューター ストアを検索しました。

## ナレッジの追加

モデルのトレーニング データと Web 検索ツールの組み合わせは、多くの場合、包括的かつ汎用的なチャット エージェントをサポートするのに十分です。 ただし、多くの場合、エージェントは特定のビジネスまたはシナリオのコンテキストで動作する必要があり、その場合、応答する際に推論する必要がある専門的または機密の情報があります。

この演習では、ヴィンテージ コンピューターのプリント基板 (PCB) に見られる一般的な製造元のシリアル番号に関する情報にアクセスできる "ファイル検索" ツールをモデルに提供します。**

1. 新しいブラウザー タブを開き、**[vintage_computer_identifiers.docx](https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/vintage_computer_identifiers.docx){:target="_blank"}** (`https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/vintage_computer_identifiers.docx`) を表示します。 これを使用して、シリアル番号、製品 ID、その他の一般的に印刷されている詳細に基づいてコンピューターを識別するためにエージェントが使用できるナレッジ ソースを提供します。
1. **vintage_computer_identifiers.docx** をローカル コンピューターにダウンロードします。
1. エージェント プレイグラウンドを含むタブに戻り、左側のペインの **[ツール]** セクションで **vintage_computer_identifiers.docx** ファイルをアップロードし、既定のインデックス名で新しいインデックスを作成します。 インデックスが作成されたら、それをエージェントにアタッチします。
1. モデル プレイグラウンドで、チャット ペインの右上にある **[新しいチャット]** ボタンを使用して、会話を再開します。
1. **[チャット]** ペインで、プロンプト `I have a printed circuit board with the "ASSY 250425" on it. What can you tell me about it?` を入力し、応答を表示します。

    今回は、経費データ ソースの情報に基づいた応答が表示されるはずです。

1. たとえば、`What kind of computer does a PCB with "820-001A" come from?` や `What about "i386"?` など、他にもいくつかのプロンプトを試してみてください。

    ファイルに関連情報がある場合、モデルはそれを使用して回答します。 情報が見つからない場合、モデルは、独自のトレーニング知識または web_search ツールを使用します。

## モデル構成をエージェントとして保存する

スタンドアロンのモデルを使用して生成 AI アプリを実装できますが、完全にエージェント型の AI エクスペリエンスを作成するには、モデル、その指示、ツール構成を "エージェント" にカプセル化する必要があります。** 指示とツールをエージェントにカプセル化すると、クライアント アプリケーションをエンドポイントに接続でき、システム プロンプトを指定したり、独自の "検索拡張生成" (RAG) ロジックを実装してコンテキスト知識を追加したりする必要はありません。**

1. モデル プレイグラウンドの右上にある **[エージェントとして保存]** を選択します。 次に、プロンプトが表示されたら、新しいエージェントに `computing-historian` という名前を付けます。

    エージェントが作成されると、エージェントを操作するための新しいプレイグラウンドが開きます。

    ![エージェント プレイグラウンドのスクリーンショット。](./media/agent-playground.png)

1. 右ペインで、エージェントの定義が含まれている **[YAML]** タブを表示します。 定義には、次のように、モデル、そのパラメーター設定、指定した指示が含まれていることに注意してください。

    ```yml
    metadata:
      logo: Avatar_Default.svg
      microsoft.voice-live.enabled: "false"
    object: agent.version
    id: computing-historian:1
    name: computing-historian
    version: "1"
    description: ""
    created_at: 1784419039
    definition:
      kind: prompt
      model: gpt-5-mini
      instructions: You are an expert in the history of computing and AI. You only answer questions about significant people and events in the development of computing, and about notable vintage computers. Do not engage in conversations on any topic that is unrelated to computing history.
      tools:
        - type: web_search
        - type: file_search
          vector_store_ids:
            - vs_qpRG020jZSewWHPI7B06q2V4
    status: active
    instance_identity:
      principal_id: 0000000-0000000-000000000
      client_id: 0000000-0000000-000000000
    blueprint:
      principal_id: 0000000-0000000-000000000
      client_id: 0000000-0000000-000000000
    blueprint_reference:
      type: ManagedAgentIdentityBlueprint
      blueprint_id: computing-historian-c9996
    agent_guid: c0000000-0000000-000000000
    ```

1. **[チャット]** タブに戻り、プロンプト `Who are you?` を入力します

    応答は、エージェントがコンピューティング歴史家としての自身の役割を "認識している" ことを示します。

## エージェントをプレビューする

これで作業エージェントが作成されたので、基本的な Web チャット アプリケーションでプレビューできます。

1. チャット ペインの上部にある **[公開]** ドロップダウン リストで、**[Web アプリのプレビュー]** を選択します。

    プレビュー チャット インターフェイスが新しいブラウザー タブで開きます。

1. `What can you tell me about the Altair 8800?` などの新しいプロンプトを入力し、エージェントからの応答を表示します。

    ![エージェントのプレビュー チャット インターフェイスのスクリーンショット。](./media/agent-preview.png)

## プロジェクト内のエージェントにアクセスするためのクライアント コードを表示する

エージェントは Foundry プロジェクト内で定義されており、それに接続するアプリを開発する便利な方法があります。エージェントとクライアント アプリの両方を繰り返し調整して、必要なソリューションを作成できます。

1. エージェント プレイグラウンドで、**[チャット]** タブから **[エージェントの呼び出し]** タブに切り替え、エージェントを使用するためのサンプル コードを表示します。次のようになるはずです。

    ```python
    # Before running the sample:
    # pip install azure-ai-projects>=2.1.0
    
    from azure.identity import DefaultAzureCredential
    from azure.ai.projects import AIProjectClient
    
    endpoint = "<https://ai-resrce.services.ai.azure.com/api/projects/ai-project>"
    
    project_client = AIProjectClient(
        endpoint=endpoint,
        credential=DefaultAzureCredential(),
    )
    
    my_agent = "computing-historian"
    my_version = "1"
    
    openai_client = project_client.get_openai_client()
    
    # Reference the agent to get a response
    
    response = openai_client.responses.create(
        input=[{"role": "user", "content": "Tell me what you can help with."}],
        extra_body={"agent_reference": {"name": my_agent, "version": my_version, "type": "agent_reference"}},
    )
    
    print(f"Response output: {response.output_text}")
    ```

    エージェントに接続するコードでは、**Azure.AI.Projects** ライブラリを使用して、Foundry プロジェクトに接続された **AIProjectClient** オブジェクトを作成します。 これには特権リソースが含まれている可能性があるプロジェクトへの接続が含まれているため、キーベースの認証はサポート<u>されておらず</u>、アプリケーションで認証するには Entra ID を使用する必要があります。

    プロジェクトに接続した後、コードはプロジェクト クライアントの **get_openai_client** メソッドを使用して OpenAI クライアント オブジェクトを取得します。これにより、前にモデルとのチャットに使用されていたのと同じ、**Responses** API を使用してエージェントにプロンプトを送信できます。 プロジェクトには複数のエージェントとモデルを含めることができるため、個別のエージェントの詳細は、**responses.create** メソッドで **extra_body** として指定されます。

## まとめ

この演習では、Microsoft Foundry ポータルで生成 AI モデルを使用してチャットをデプロイする方法について説明しました。 その後、モデルを指示やツールと共にエージェントとして保存しました。

この演習で確認したエージェントは、Microsoft Foundry を使用すると生成 AI アプリとエージェントの開発をいかに迅速かつ簡単に開始できるかを示す簡単な例です。 この基盤から、エージェントがツールを使用して情報を検索し、タスクを自動化し、相互に連携して複雑なワークフローを実行する、包括的なエージェント ソリューションを構築できます。

> **[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}**<br/>![Anton のアバター。](./media/anton-icon.png)<br/>この演習で取り上げるいくつかのトピックについて疑問がある場合、*[Ask Anton](https://aka.ms/azk-anton){:target="_blank"}* は生成 AI ベースのエージェントであり、AI の概念や Microsoft Foundry について質問することができます。 **[https://aka.ms/azk-anton](https://aka.ms/azk-anton){:target="_blank"}** でアプリを開き、**[構成]** ボタンを使用して Foundry プロジェクトとモデルの詳細を入力します。<br/><br/>"Ask Anton は、サポートされる Microsoft 製品ではなく、Microsoft Learn や AI スキル ナビゲーターのコンポーネントでもありません。AI で何が可能であるかを学ぶ際に探求できる AI エージェントの一例にすぎません。"**<br/><br/>Ask Anton をお試しいただき、"そのご感想をぜひ[こちらのフォーム](https://forms.office.com/r/fC0ndfBQeK){:target="_blank"}にてお寄せください"。****

## クリーンアップ

Microsoft Foundry について調べ終わったら、不要な利用料金が発生しないように、この演習で作成したリソースを削除する必要があります。

1. [Azure portal](https://portal.azure.com){:target="_blank"} (`https://portal.azure.com`) を開き、この演習で使ったプロジェクトをデプロイしたリソース グループの内容を表示します。
1. ツール バーの **[リソース グループの削除]** を選びます。
1. リソース グループ名を入力し、削除することを確認します。
