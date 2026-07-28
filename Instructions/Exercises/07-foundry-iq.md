---
lab:
  title: Microsoft Foundry で Foundry IQ の使用を開始する
  description: Foundry IQ を使用して、エージェントをナレッジに接続します。
  level: 200
  duration: 20 minutes
  islab: true
  primarytopics:
    - Microsoft Foundry
---

# Microsoft Foundry で Foundry IQ の使用を開始する

![Anton の画像。](./media/anton-icon.png)<br/>**こんにちは、Anton です。**<br/>このラボでは、私がヒントを出しながらサポートします。Microsoft Foundry IQ で経費ポリシー ドキュメントに含まれるナレッジを使用して経費申請のガイドラインと手続きについて従業員にアドバイスする AI エージェントを作成します。

より対話型のヘルプが必要な場合は、*[Ask Anton](https://aka.ms/choose-anton){:target="_blank"}* アプリで私とチャットできます。

<details>
<strong><i><a href="https://aka.ms/choose-anton" target="_blank">Ask Anton</a></i></strong> は、AI の概念や Microsoft Foundry の技術に関する質問に答えることができる生成 AI エージェントです。 <code>https://aka.ms/choose-anton</code> から、2 つのバージョンで使用できます。
<ul>
<li><strong>Azure ベースの</strong>: 最適なエクスペリエンスです (Azure サブスクリプションと Foundry プロジェクト内のモデルのデプロイが必要です)。<i></i></li>
<li><strong>ブラウザーベース</strong>: ブラウザーで小さな言語モデルを使用します (機能は制限されています。古い、または低スペックのデバイスでは動作が遅くなるか "ベーシック" モードでしか動作しないことがあります)。<i></i></li>
</ul>
<blockquote><i>Ask Anton は、サポートされている Microsoft 製品、Microsoft Learn、AI スキル ナビゲーターのコンポーネントのいずれでも<u>ありません</u>。</i>
</blockquote>
</details>
<hr/>

この演習の所要時間は約 **20** 分です。

> **注**: Microsoft Foundry ポータルなど、Microsoft Foundry の多くのコンポーネントは、継続的に開発が進められています。 これは、人工知能テクノロジの急速な進歩を反映したものです。 実際のユーザー エクスペリエンスは、この演習で使用されている画像や説明と異なる場合があります。

## Microsoft Foundry プロジェクトを作成する

Microsoft Foundry では "プロジェクト" を使って、AI ソリューションの開発に使われるモデル、リソース、データ、その他の資産を整理します。**

1. Web ブラウザーで、[Microsoft Foundry](https://ai.azure.com){:target="_blank"} (`https://ai.azure.com`) を開いてビルドを開始します。Azure の資格情報を使ってサインインします。 初めてサインインすると開くヒントやクイック スタートのペインをすべて閉じ、必要な場合は、左上にある **Foundry** のロゴを使ってホーム ページに移動します。
1. まだ有効になっていない場合は、ページ上部のツール バーで **[新しい Foundry]** オプションを有効にします。
1. 既存のプロジェクトがない場合は、プロジェクトを作成するようにダイアログが表示されます。 一意の名前で新しいプロジェクトを作成します。**[詳細オプション]** 領域を展開して、プロジェクトの次の設定を指定します (または、既存のプロジェクトがある場合は選択できます)。
    - **Foundry リソース**: "Foundry リソースの有効な名前"。**
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
    - **リソース グループ**: *リソース グループを作成または選択します*
    - **リージョン**: [こちらの一覧](https://learn.microsoft.com/azure/foundry/openai/how-to/responses#supported-regions){:target="_blank"}にある、**AI Foundry の推奨**リージョンのいずれかを選択します

    > ![Anton の画像。](./media/anton-icon.png)<br/>**ヒント**: Azure サブスクリプションのアクセス許可によっては、推奨されるリソースを設定するオプションをオフにする必要がある場合があります。

1. プロジェクトが作成されるまで待ちます。 これには数分かかることがあります。 次に、表示されているウェルカム ダイアログを閉じます。

    "新しい" Foundry ポータルでプロジェクトを作成または選択すると、それが次の画像のようなページで開かれます。

    ![Foundry プロジェクトのホーム ページのスクリーンショット。](./media/foundry-portal-home.png)


## AI エージェントを作成する

これで、従業員の経費申請を支援するエージェントを作成する準備ができました。

1. **ホーム** ページの **[エージェントのビルド]** タイルで **[ビルド開始]** を選択し (または **[ビルド]** ページで **[エージェント]** タブを選択し)、`expenses-agent` という新しいエージェントを作成します。

     準備ができると、エージェントがエージェント プレイグラウンドで開きます。

    ![エージェント プレイグラウンドのスクリーンショット。](./media/expenses-agent.png)

1. モデルのドロップダウン リストで、モデルがデプロイされ、エージェントに選択されていることを確認します。
1. エージェントに次の**指示**を割り当てます。

    ```
   You are an AI agent that advises employees on expenses policies and expense claim processes.
    ```

1. **[保存]** ボタンを押して、変更を保存します。
1. **[チャット]** ペインに次のプロンプトを入力して、エージェントをテストします。

    ```
   What can you help me with?
    ```

    エージェントは、指示に基づいた適切な応答で返信する必要があります。

1. 次にこれを試してみます。

    ```
   How much can I claim for a taxi?
    ```

    エージェントは、正しい応答の*ように見える*もので応答する場合があります。 しかし、エージェントには現在、会社の経費のポリシーと手続きに関するナレッジがないため、応答が正確な情報に典拠していません。

    これを修正しましょう。

## Foundry IQ のナレッジ ベースを追加する

Foundry IQ は、エージェントがナレッジ ベースとして使用できるデータ ソースの一元的な接続ポイントです。 複数のエージェントが使用できるナレッジのコレクションを作成および管理できます。エージェントごとにデータ アクセスとクエリ ロジックをコーディングする必要はありません。

### 経費ポリシーのドキュメントをダウンロードする

1. 新しいブラウザー タブを開き、**[expenses_policy.docx](https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/expenses_policy.docx){:target="_blank"}** (`https://microsoftlearning.github.io/mslearn-ai-fundamentals/data/expenses_policy.docx`) に移動します。 これを使用して、エージェントが経費精算に関する質問に回答できるようになるナレッジ ソースを提供します。

    > ![Anton の画像。](./media/anton-icon.png)<br/>**ヒント**: このラボで使用するのは、非常に小さなドキュメントです。 実際には、エンタープライズのナレッジ ベースは大量のデータで構成されており、多くの場合、1 つ以上のデータベースや他のエンタープライズ システムに存在します。

1. **expenses_policy.docx** をローカル コンピューター (どこでも構いません) にダウンロードします。

### Foundry IQ を構成する

1. Foundry ポータル エージェント プレイグラウンドを含むブラウザー タブに戻り、左側のメイン ナビゲーション ウィンドウで **[ナレッジ]** を選択して Foundry IQ ページを開きます。

    ![[Foundry IQ] ページのスクリーンショット。](./media/foundry_iq.png)

1. ページの下部で **[新しいリソースの作成]** リンクを選択して、Azure サブスクリプション内で新しい Foundry IQ (Azure AI 検索) リソースを作成します。

    ![[Foundry IQ リソース] ダイアログのスクリーンショット。](./media/foundry_iq_resource.png)

    次の値を入力し、コスト確認を受け入れてリソースを作成します。

    - **[リソース名]**: *Foundry IQ リソースの一意の名前。*
    - **[サブスクリプション]**: *お使いの Azure サブスクリプション*。
    - **[リソース グループ]**: *Microsoft Foundry リソースを含んでいるリソース グループ。*
    - **[リージョン]**: 利用可能ないずれかの Azure リージョン。
    - **価格レベル**: Basic

1. Foundry IQ リソースが作成され、セキュア アクセス用に設定されるまで待ちます。

    Foundry IQ リソースが準備できたら、ページにナレッジ ベースが掲載されます (現在は何もありません)。

    ![Foundry IQ ナレッジ ベースのページのスクリーンショット。](./media/foundry_iq_knowledge_bases.png)

### ナレッジ ベースの作成

1. **[ナレッジ ベースの作成]** を選択し、次の値を割り当ててナレッジ ベースの基本構成を完了します。
    - **名前**: `expenses-documentation`
    - **説明**: `Expense guidelines for employees`
    - **[チャット入力候補モデル]**: *既存のモデル デプロイを選択します*
    - **[取得の推論作業]**:低
    - **[出力モード]**:応答の合成
    - **[応答の指示]**: `Answer concisely, based on the available context`
    - **[取得の指示]**: `Use the expenses-documentation source for all questions related to expense claim policies and procedures`

    > **注**:*[出力モード]* は、Foundry IQ がエージェントにナレッジを返す方法を決定します。 *[抽出データ]* はナレッジ ソースから逐語的テキストを返し、*[応答の合成]* は生成 AI モデルを使用して適切な応答を作成します。 *[応答の指示]* は、応答の書式を指定するシステム プロンプトとして機能し、*[取得の指示]* は Foundry IQ が使用可能なナレッジ ベースでナレッジをどのように検索するかを指示します (この場合、ナレッジ ベースは 1 つだけですが、さらに多い場合があります)。

1. **[ナレッジ ソースの追加]** ペインで、**[ファイルのアップロード]** を選択し、以前ダウンロードした **expenses_policy.docx** ファイルをコンピューターにアップロードします。名前は `expenses-policy` を割り当て、既定の埋め込みモデルを使用します。

    ![[ナレッジ ソースの作成] ダイアログのスクリーンショット。](./media/foundry_iq_file.png)

1. ファイルがアップロードされ、処理されるまで待ってから、ナレッジ ベースを保存します。

### アクセス許可のコンフィギュレーション

1. 新しいブラウザー タブを開いて [Azure portal](https://portal.azure.com){:target="_blank"} (`https://portal.azure.com`) に移動し、Azure の資格情報でサインインします。
1. Foundry IQ リソースを作成したリソース グループに移動し、Microsoft Foundry リソースとプロジェクトと一緒に表示されていることを確認します。

    ![Foundry ポータルのリソースのスクリーンショット。](./media/azure_resource_group_with_search.png)

1. Foundry IQ 検索サービスのリソースを選択して開き、その **[アクセスの制御 (IAM)]** ページを表示します。

    ![AI Search のアクセスの制御ページのスクリーンショット。](./media/ai_search_iam.png)

1. **[追加]** ドロップダウン リストで、**[ロールの割り当ての追加]** を選択します。 その後、**[ロール]** タブで `Search Data Index Reader` ロールを検索して選択し、**[次へ]** を選択します。

    ![[ロールの割り当ての追加] (ロール) ページのスクリーンショット。](./media/add_role_assignment_role.png)

1. **[メンバー]** タブで **[マネージド ID]** を選択し、**[+ メンバーの選択]** リンクを使用して **Foundry プロジェクト**の ID を検索して選択します。

    ![[ロールの割り当ての追加] (メンバー) ページのスクリーンショット。](./media/add_role_assignment_member.png)

1. **[レビューと割り当て]** のロール メンバーシップのプロセスを完了し、Foundry プロジェクトのマネージド ID を *[検索インデックス データ閲覧者]* ロールに追加します。 あなたの Foundry IQ 検索リソース。
1. Azure portal のタブを閉じて Foundry ポータルに戻ります。そこではナレッジ ストアのページがまだ開いているはずです。

## 経費エージェントでナレッジ ストアを使用する

これで、経費エージェントで新しいナレッジ ストアを使用する準備ができました。

1. ナレッジ ストアを保存したページの、**[エージェント内で使用する]** ドロップダウン リストで経費エージェントを選択します。

    エージェント プレイグラウンドでエージェントが開き、ナレッジ ストアがアタッチされています。

1. チャット ペインで、次のクエリを入力します。

    ```
   How much can I claim for a taxi?
    ```

1. エージェントからの応答をレビューし、応答の最後に経費ドキュメントの引用が記載されていることを確認します。

    ![エージェントの応答のスクリーンショット。](./media/expenses_agent_with_knowledge.png)

    経費エージェントは、Foundry IQ を使用してユーザーの質問に答えるために必要な経費ドキュメントのナレッジ ストアにアクセスするようになりました。

## まとめ

この演習では、Foundry IQ を使用してエージェントをナレッジ ソースに接続する方法について説明しました。 この演習の例はシンプルですが、応答の精度と関連性を高めるために、エージェントがコンテキスト ナレッジを典拠とできることが示されています。

Foundry IQ を使用すると、生成 AI ソリューションで普及している検索拡張生成 (RAG) パターンのカスタム実装よりも多くの利点があります。 ナレッジへのアクセスを 1 つのツールに一元化することで、データ ソースの選択と取得ロジックを Foundry IQ にオフロードでき、コードやデータ アクセス ロジックを複製することなく、複数のエージェント間でナレッジ ソースを再利用できます。

## クリーンアップ

Microsoft Foundry について調べ終わったら、不要な利用料金が発生しないように、この演習で作成したリソースを削除する必要があります。

1. [Azure portal](https://portal.azure.com){:target="_blank"} (`https://portal.azure.com`) を開き、この演習で使ったプロジェクトをデプロイしたリソース グループの内容を表示します。
1. ツール バーの **[リソース グループの削除]** を選びます。
1. リソース グループ名を入力し、削除することを確認します。

> ![Anton のアバター。](./media/anton-icon.png)<br/>このラボで [*Ask Anton*](https://aka.ms/choose-anton){:target="_blank"} アプリを使用した場合は、[そのエクスペリエンスについてお聞かせください。](https://forms.office.com/r/fC0ndfBQeK){:target="_blank"}