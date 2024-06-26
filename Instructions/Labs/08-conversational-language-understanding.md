---
lab:
  title: Language Studio で会話言語理解を使用する
---

# Language Studio で会話言語理解を使用する

話されたか入力されたかに関係なく、AI を活用して自然言語を理解できるコンピューターへの期待が高まっています。 たとえば、ホーム オートメーション システムで、"照明をつけて"、"換気扇を回して" などの音声コマンドを使用して、自宅のデバイスを制御できます。 AI 搭載デバイスは、これらのコマンドを理解し、適切なアクションを実行できます。

この演習では、Language Studio を使用して、照明や換気扇などのデバイスに指示を送信するプロジェクトを作成してテストします。 会話言語理解サービスの機能を使用して、プロジェクトを構成します。 

## "言語" リソースを作成する**

多くの Azure AI Language 機能は、**言語**リソースと **Azure AI サービス** リソースのいずれかで使用できます。 言語リソースのみを使用できるものもあります。 以下の演習では、**言語**リソースを使用します。 まだ作成していない場合は、Azure サブスクリプションで**言語**リソースを作成します。

1. 別のブラウザー タブで Azure portal ([https://portal.azure.com](https://portal.azure.com?azure-portal=true)) を開き、ご使用の Azure サブスクリプションに関連付けられている Microsoft アカウントを使用してサインインします。

1. **[&#65291;リソースの作成]** ボタンをクリックし、*言語サービス*を検索します。 **言語サービス**を**作成する**プランを選択します。 **[追加機能の選択]** ページに転送されます。 既定の選択をそのまま使用し、**[続行] をクリックしてリソースを作成します**。 

1. **[言語リソースの作成]** ページを次の設定で構成します。
    - **[サブスクリプション]**: *お使いの Azure サブスクリプション*。
    - **[リソース グループ]**: *一意の名前のリソース グループを選択するか、作成します*。
    - **[リージョン]**: "地理的に最も近いリージョンを選びます。** 米国東部の場合は、[米国東部 2] を使用します"。
    - **[名前]**: *一意の名前を入力します*。
    - **価格レベル**: *Free F0 または S (Free F0 を使用できない場合)*
    - **[このボックスをオンにすることにより、以下のすべてのご契約条件を読み、同意したものとみなされます]**:*オン*。

1. **[確認 + 作成]**、**[作成]** の順に選択し、デプロイが完了するまで待ちます。


### 会話言語理解アプリを作成する

会話言語理解を使って自然言語を理解できるようにするには、アプリを作成し、次にエンティティ、意図、発話を追加して、アプリで実行するコマンドを定義します。

1. 新しいブラウザー タブで Language Studio ポータル ([https://language.azure.com](https://language.azure.com?azure-portal=true)) を開き、お使いの Azure サブスクリプションに関連付けられている Microsoft アカウントを使ってサインインします。

1. 言語リソースの選択を求めるメッセージが表示されたら、次の設定を選択します。
    - **Azure ディレクトリ**:*サブスクリプションを含む Azure ディレクトリ*。
    - **Azure サブスクリプション**: *使用する Azure サブスクリプション*
    - **言語リソース**:*前に作成したリソース。*

   言語リソースの選択を求めるメッセージが表示***されない***場合、原因として、お使いのサブスクリプションに複数の言語リソースが存在していることが考えられます。その場合は、次の操作を行います。
    1. ページの上部にあるバーで、**[設定] (&#9881;)** ボタンを選択します。
    2. **[設定]** ページで、**[リソース]** タブを表示します。
    3. 先ほど作成した言語リソースを選択し、[**リソースの切り替え**] を選択します。
    4. ページの上部で、[**Language Studio**] を選択して、Language Studio のホーム ページに戻ります。

1. ポータルの上部にある **[新規作成]** メニューで、**[会話言語理解]** を選択します。

1. **[プロジェクトの作成]** ダイアログ ボックスの **[基本情報の入力]** ページで、次の詳細を入力し、**[次へ]** を選択します。
    - **名前**: *一意の名前を作成する*
    - **発話の主要言語**:*英語*
    - **プロジェクトで複数の言語を有効にする**: 選択しない**
    - **説明**: `Simple home automation`

    > **ヒント**: "プロジェクト名" を書き留めてください。後で使用します。**

1. **[確認と完了]** ページで、**[作成]** を選択します。

### 意図、発話、エンティティの作成

"意図" は、実行するアクションです。たとえば、照明のスイッチを入れたり、ファンの電源を切ったりすることができます。** ここでは、2 つの意図を定義します。1 つはデバイスをオンに切り替える意図で、もう 1 つはデバイスをオフに切り替える意図です。 それぞれの意図には、その意図を示すために使用する言語の種類を表すサンプル*発話*を指定します。

1. **[スキーマ定義]** ペインで **[意図]** が選ばれていることを確かめます。次に、**[追加]** をクリックし、(小文字で) `switch_on` という名前の意図を追加して、**[意図の追加]** をクリックします。

    ![[Build Schema]\(スキーマのビルド\) ペインの [意図] の下にある [追加] をクリックします。](media/conversational-language-understanding/build-schema.png)

    ![switch_on 意図を追加し、[意図の追加] を選択します。](media/conversational-language-understanding/add-intent.png)

1. **switch_on** 意図を選択します。 これにより、**[データのラベル付け]** ページに移動します。 **[意図]** ドロップダウンで、 **[switch_on]** を選択します。 **switch_on** 意図の横に、発話 `turn the light on` を入力し、**Enter** キーを押して、この発話を一覧に送信します。

    ![発話の下に「turn the light on」と入力して、トレーニング セットに発話を追加します。](media/conversational-language-understanding/add-utterance-on.png)

1. 言語サービスでは、言語モデルを十分にトレーニングするために、意図ごとに少なくとも 5 つの異なる発話の例が必要です。 **switch_on** 意図に、さらに 5 つの発話の例を追加します。  
    - `switch on the fan`
    - `put the fan on`
    - `put the light on`
    - `switch on the light`
    - `turn the fan on`

1. 画面の右側にある **[トレーニング用のエンティティのラベル付け]** ペインで、**[ラベル]** を選び、**[エンティティの追加]** を選択します。 (小文字で) `device` と入力し、**[リスト]** を選び、**[エンティティの追加]** を選択します。

    ![[トレーニング] パネルの [タグ付けエンティティ] で [タグ] を選択してエンティティを追加し、[エンティティの追加] を選択します。](media/conversational-language-understanding/add-entity.png)

    ![[エンティティ名] に「device」と入力し、[リスト] を選択してから、[エンティティの追加] を選択します。](media/conversational-language-understanding/add-entity-device.png)

1. ***"扇風機の電源を入れる"*** 発話で、"扇風機" という単語を強調表示します。 次に、表示される一覧の *[Search for an entity](エンティティの検索)* ボックスで **"デバイス"** を選びます。

    ![発話でファンという単語を強調表示し、[デバイス] を選択します。](media/conversational-language-understanding/switch-on-entity.png)

1. すべての発話に対して同じ操作を行います。 残りの ''*扇風機*'' または ''*照明*'' 発話に、"**デバイス**" エンティティのラベルを付けます。 完了したら、以下の発話があることを確認して、必ず **[変更の保存]** を選択します。

    | **意図** | **発話** | **エンティティ** |
    | --------------- | ------------------ | ------------------ |
    | switch_on   | 扇風機をオンにする      | デバイス - "ファンを選択する" **  |
    | switch_on   | 照明を点ける    | デバイス - "照明を選択する" **  |
    | switch_on   | 照明のスイッチを入れる | デバイス - "照明を選択する" **  |
    | switch_on   | 扇風機の電源を入れる     | デバイス - "ファンを選択する" **  |
    | switch_on   | ファンのスイッチを入れる   | デバイス - "ファンを選択する" **  |
    | switch_on   | 照明の電源を入れる   | デバイス - "照明を選択する" **  |

    ![完了したら、[変更の保存] を選択します。](media/conversational-language-understanding/save-changes.png) 

1. 左側のペインで、**[スキーマ定義]** をクリックし、**switch_on** 意図が一覧表示されていることを確認します。 次に **[追加]** を選択し、(小文字で) `switch_off` という名前の新しい意図を追加します。

    ![[スキーマのビルド] 画面に戻り、switch_off 意図を追加します。](media/conversational-language-understanding/add-switch-off.png) 

1. **switch_on** 意図を選択します。 これにより、**[データのラベル付け]** ページに移動します。 **[意図]** ドロップダウンで、 **[switch_off]** を選択します。 **switch_off** 意図の横に、発話 `turn the light off` を追加します。

1. **switch_off** 意図に、さらに 5 つの発話の例を追加します。
    - `switch off the fan`
    - `put the fan off`
    - `put the light off`
    - `turn off the light`
    - `switch the fan off`

1. 単語の ''*照明*'' または ''*扇風機*'' に **device** エンティティのラベルを付けます。 完了したら、以下の発話があることを確認して、必ず **[変更の保存]** を選択します。  

    | **意図** | **発話** | **エンティティ** | 
    | --------------- | ------------------ | ------------------ |
    | switch_off   | ファンをオフにする    | デバイス - "ファンを選択する" **  | 
    | switch_off   | 照明をオフにする  | デバイス - "照明を選択する" **  |
    | switch_off   | 照明の電源を切る | デバイス - "照明を選択する" **  |
    | switch_off   | 扇風機のスイッチを切る | デバイス - "ファンを選択する" **  |
    | switch_off   | 扇風機のスイッチを切る | デバイス - "ファンを選択する" **  |
    | switch_off   | 照明の電源を切る | デバイス - "照明を選択する" **  |

### モデルをトレーニングする

これで、定義した意図とエンティティを使って、アプリの会話言語モデルをトレーニングする準備ができました。

1. Language Studio の左側で、[**ジョブのトレーニング**] を選び、[**ジョブのトレーニングの開始**] を選択します。 次の設定を使用します。
    - **新しいモデルのトレーニング**: モデル名を選ぶ**
    - **トレーニング モード**: 標準トレーニング (無料)
    - **データ分割**: *[テスト セットをトレーニング データから自動的に分割する] を選択し、既定のパーセンテージを保持する*
    - ページの下部にある **[トレーニングする]** を選択します。

1. トレーニングが完了するまで待ちます。

### モデルをデプロイしてテストする

クライアント アプリケーションでトレーニング済みのモデルを使用するには、クライアント アプリケーションが新しい発話を送信できるエンドポイントとしてそのモデルをデプロイする必要があります。そのエンドポイントから、意図とエンティティが予測されます。

1. Language Studio の左側で、**[モデルのデプロイ]** を選択します。

1. モデル名を、次に **[デプロイの追加]** を選択します。 次の設定を使用します。
    - **デプロイ名を作成または既存のものを選択する**: '' *[新しいデプロイ名の作成] を選択します。一意の名前を追加します*''。
    - **トレーニング済みモデルをデプロイ名に割り当てる**: ''*トレーニング済みモデルの名前を選択します*''。
    - **[デプロイ]** を選択します

    > **ヒント**: ''デプロイ名'' を書き留めてください。後で使用します。** 

1. モデルがデプロイされたら、ページの左側で **[デプロイのテスト]** を選択し、次に **[デプロイ名]** でデプロイ済みモデルを選択します。

1. 次のテキストを入力し、**[テストの実行]** を選択します。

    `switch the light on`

    ![デプロイしたモデルを選択し、テキストを入力して [テストの実行] を選択して、モデルをテストします。](media/conversational-language-understanding/test-model.png) 

    返された結果を確認します。予測された意図 (**switch_on** の必要がある) および予測されたエンティティ (**デバイス**) と、予測された意図とエンティティに対してモデルで計算された確率を示す信頼度スコアが含まれていることに注意してください。 [JSON] タブには、考えられる各意図の信頼度の比較が表示されます (信頼度スコアが最も高いものが予測された意図です)

1. テキスト ボックスをクリアし、 *[独自のテキストを入力するかテキスト ドキュメントをアップロードする]* で次の発話を使用してモデルをテストします。
    - `turn off the fan`
    - `put the light on`
    - `put the fan off`

これで、会話言語プロジェクト、定義されたエンティティ、意図、発話を正常に構成しました。 Language Studio でモデルをトレーニングしてデプロイする方法を確認しました。 また、定義した発話と、明示的に定義していないがモデルが判断できた発話の両方を試しました。

> **注**:会話言語理解は、入力の意図を解釈するためのインテリジェンスを提供します。照明や換気扇の電源を入れるなどの操作は実行しません。 開発者は、会話言語理解モデルを使用してユーザーの意図を判断し、適切なアクションを自動化するアプリケーションを構築する必要があります。

## クリーンアップ

これ以上の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. [Azure portal]( https://portal.azure.com) を開き、作成したリソースを含むリソース グループを選択します。 1. リソースを選択し、**[削除]** を、次に **[はい]** を選択して確定します。 これでリソースが削除されます。

## 詳細情報

このアプリでは、言語サービスの会話言語理解の一部の機能しか示されていません。 このサービスで実行できる操作の詳細については、[会話言語理解のページ](https://docs.microsoft.com/azure/cognitive-services/language-service/conversational-language-understanding/overview)を参照してください。
