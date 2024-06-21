---
lab:
  title: Copilot for Microsoft 365 を探索する
---
# Copilot for Microsoft 365 を探索する

この演習では、Microsoft Copilot で生成 AI を使用して、新しいコンテンツを作成する際の生産性を高める方法をいくつか探っていきます。 この演習のシナリオでは、まず、ビジネスのアイデアに関する大まかなメモを作成し、Word、PowerPoint、Excel などの複数のアプリで Copilot for Microsoft 365 を使用して、見込み投資家に向けてビジネス プランとプレゼンテーションを作成できるようにします。

この演習の所要時間は約 **40** 分です。

> **注**:この演習には、ご自身の組織の **Copilot for Microsoft 365** ライセンスが必要です。

## Copilot を使用してドキュメントを探索し、アイデアを調査する

生成 AI の探索を始めるために、Copilot for Word を使用して既存のドキュメントを調べ、そこからいくつかの分析情報を抽出することにします。

1. Web ブラウザーで、`https://github.com/MicrosoftLearning/mslearn-ai-fundamentals/raw/main/data/generative-ai/Business%20Idea.docx` にあるドキュメント [Business Idea.docx](https://github.com/MicrosoftLearning/mslearn-ai-fundamentals/raw/main/data/generative-ai/Business%20Idea.docx) を開きます。 
1. **[ダウンロード]** を選択し、ファイルをお使いの PC の **Downloads** フォルダーに保存します。
1. ダウンロードしたドキュメントを、**OneDrive** フォルダーに**移動**するか**コピーして貼り付け**ます。
1. **OneDrive** フォルダーから、Microsoft Word で **Business Idea.docx** を開き (ウェルカム メッセージや新機能の通知は閉じます)、このドキュメントを確認します。ここには、ニューヨーク市のクリーニング ビジネスに関するおおまかなアイデアがいくつか記載されています。 メッセージが表示されたら、上部の **[編集を有効にする]** を選択します。
1. 次に示すように、Word ツール バーの **[Copilot]** アイコンを見つけて選択し、[Copilot] ペインを開きます (ビジュアル テーマは異なっている場合があります)。

    ![Microsoft Word の [Copilot] ペインのスクリーンショット。](./media/generative-ai/copilot-word-pane.png)

1. [Copilot] ペインで、プロンプトに従って下部のテキスト領域に入力します。

    ```
    What is this document about?
    ```

1. Copilot からの応答を確認します。ここでは、次に示すように、ドキュメントの主要なポイントが要約されています。

    ![応答が記載された Word の [Copilot] ペインのスクリーンショット。](./media/generative-ai/copilot-response-word.png)

    > 受け取る応答の具体的な内容は、生成 AI の性質によって異なる可能性があります。

1. [Copilot] ペインに戻り、Copilot に次の質問を尋ねます。

    ```
    How do I setup a new business in New York?
    ```

1. 応答を確認し、必要に応じて、引き続き追加の質問をします。 応答に満足したら、応答の下にある **[コピー]** (&#128461;) アイコンを使用してクリップボードにコピーします。 それを Word ドキュメントに貼り付け、すべてのテキストを選択してから (選択したテキストの下部にある) [Copilot] アイコンを選択し、テキストをテーブルとして視覚化します。

    ![テーブル形式で視覚化するように Copilot に求めるスクリーンショット。](./media/generative-ai/copilot-rewrite-as-table.png)

1. テーブルを確認し、詳細情報のためのリファレンスなど、より多くの情報を追加するよう Copilot に求めます。  応答は次のようになります (場合によっては **[再生成]** ボタンを使用する必要があります)。

    ![テーブル形式になった Copilot からの応答のスクリーンショット。](./media/generative-ai/copilot-rewrite-as-table-response.png)

    > **重要**: AI によって生成される応答は、Web 上で公開されている情報に基づきます。 これは、ビジネスの立ち上げに必要な手順を理解するのに役立つ可能性がありますが、100% 正確であるという保証はなく、専門家のアドバイスの必要がなくなるわけではありません。

1. Copilot が生成したテーブルに満足したら、**保持する**ためのオプションを選択します。

## Copilot を使用してビジネス プランのコンテンツを作成する

最初の調査を行ったので、Copilot を利用してクリーニング会社のビジネス プランを策定することにします。

1. **Business Idea.docx** ドキュメントを開いたまま、[Copilot] ペインに次のプロンプトを入力します。

    ```
    Can you suggest a name for my cleaning business?
    ```

1. 提案を確認し、クリーニング会社の名前を選びます (または、プロンプトの入力を続けて、好みの名前を探します)。
1. Word ドキュメントで、余白の [Copilot] アイコンを選択して、新しい内容のドラフトを作成します。 次のプロンプトを入力します。**Contoso Cleaning** は任意の会社名に置き換えます。

    ```
    Write a business plan for "Contoso Cleaning" based on the information in this document. Include an executive summary, market overview, and financial projections.
    ```

    ![ビジネス プランのドラフトを作成している Copilot のスクリーンショット。](./media/generative-ai/copilot-draft-business-plan-prompt.png)

1. Copilot によって作成された応答を確認して保持するか、トーン、長さを調整するか、新しいプロンプトを使って再生成するように Copilot に要求します。 適切な見出しとスタイルをドキュメントに適用して、プロフェッショナルに見えるようにします。 応答は次のようになります。

    ![Copilot によって生成されたビジネス プランを含む Word ドキュメントのスクリーンショット。](./media/generative-ai/copilot-draft-business-plan-response.png)

1. ビジネス プランの財務予測がテーブルとして書式設定されていない場合は、それらを選択し、Copilot を使用して予測をテーブルとして視覚化します。
1. 財務予測のテーブルを選択して、クリップボードにコピーします。
1. Word 文書を保存し、閉じます。

## Copilot for Excel で財務予測を視覚化する

ビジネス プランが準備できたので、財務予測のそのデータの一部を取得し、投資家へのメールやプレゼンテーションに含めることができるように、そのデータを視覚化するよう Copilot in Excel に求めます。

1. **Excel** を開き、新しい空白のブックを作成します。 そのブックをすぐに **Financial Projections.xlsx** としてOneDrive に保存してください。そうしないと、Copilot は機能しません。
1. **Business Idea.docx** の売上予測のテーブルを Excel スプレッドシートに貼り付け、**それをテーブルとして書式設定**します。 手順は次のとおりです。
    1. データ内の**セル**を選択します。
    1. **[ホーム]** を選択し、[スタイル] で **[テーブルとして書式設定]** を選択します。 
    1. テーブルのスタイルを選択します。
    1. **[テーブルの作成]** ダイアログ ボックスで、セル範囲を確認または設定します。
    1. テーブルにヘッダーがあるかどうかをマークし、**[OK]** を選択します。
1. 売上予測をテーブルとして書式設定した状態で、Excel リボンの **[ホーム]** タブから [Copilot] ペインを開き、次のプロンプトを入力します。

    ```
    Suggest ways to visualize these financial projections.
    ```
    
1. Copilot から、データを視覚化する方法が提案され、新しいシートにピボット グラフを追加するように提示されます。

    ![財務予測を視覚化する Copilot in Excel のスクリーンショット。](./media/generative-ai/copilot-excel-visualize-projections.png)

1. ピボット グラフを新しいシートに追加して開きます。 グラフを選択し、**[デザイン]** を選択してスタイルの適用、グラフの種類の変更、その他のアクションを行います。 最終的に、次のようになります。

    ![ピボットグラフを追加する Copilot in Excel のスクリーンショット。](./media/generative-ai/copilot-excel-chart-design.png)

1. ブックを保存し、Excel を終了します。

これで、Copilot in Word から作成されたデータを使用して Excel で視覚化しました。 次の演習では、Copilot in Outlook の使用に進み、行った作業に関するメールを作成して送信します。

## Copilot を使用してメールを作成する

ビジネスを始めるための資料をいくつか作成してきました。 次は、スタートアップ企業に資金提供しようとしている投資家にアピールします。

1. **Outlook** を開きます。 Microsoft 365 アカウントで Outlook をセットアップしていない場合は、セットアップします。

    > **ヒント**: 詳細については、「[Outlook を設定して使用する - Microsoft サポート](https://support.microsoft.com/office/set-up-and-use-outlook-4636f361-d5e3-4a87-9cd4-382858de55fa)」を参照してください。

1. ツール バーで、まだアクティブでない場合は、**新しい Outlook **エクスペリエンスに 切り替えます。

    > **注**:Outlook で最新の Copilot 機能を取得するには、"新しい Outlook" エクスペリエンスを使用する必要があります。 使用しているバージョンを確認するには、[Microsoft サポートの「所有している Outlook のバージョンが不明な場合」](https://support.microsoft.com/office/what-version-of-outlook-do-i-have-b3a9568c-edb5-42b9-9825-d48d82b2257c)を参照してください。

1. 新しいメールを作成し、**[宛先]** ボックスにご自分のメール アドレスを入力します。
1. 最初に、メールの下書きを、[Copilot] ペインから、またはメールの本文内から作成できます。

    ![Outlook と、Copilot でメールの下書きを作成するためのオプションを示すスクリーンショット。](./media/generative-ai/copilot-draft-email-outlook.png)
    
1. 次のプロンプトを入力し、トーンを [Formal] (丁寧)、長さを [中間] に調整してオプションを設定します。

    ```
    Request a meeting with an investment bank to discuss funding for a commercial cleaning business.
    ```

    ![Outlook で Copilot を使ってメールの下書きを作成するスクリーンショット。](./media/generative-ai/copilot-draft-email-adjust-tone-outlook.png)

1. **[Generate draft] (下書きの生成)** を選択し、生成された出力を確認します。 トーンを調整するか、メールについて何を変更するかを Copilot に伝えます。

    ![Outlook で Copilot を使って生成されたメールのスクリーンショット。](./media/generative-ai/copilot-draft-email-results-outlook.png)

1. 必要に応じて、自分宛てにメールを送信できます。

## Copilot を使用してプレゼンテーションの内容を作成する

Copilot の支援を得て、クリーニング事業のアイデアに関するビジネス プランのドラフトを作成し、財務予測を準備し、見込み投資家とのミーティングを要請するメールを送信しました。 次に、このビジネスの利点を伝えるために効果的なプレゼンテーションが必要になります。

1. **PowerPoint** を開き、新しい**空白のプレゼンテーション**を作成します。 **[Designer]** ペインが自動的に開いた場合は、閉じます。

    ![PowerPointで新しい空白のプレゼンテーションを作成するスクリーンショット。](./media/generative-ai/powerpoint-create-blank-presentation.png)

1. プレゼンテーションを **Cleaning Company.pptx** として OneDrive フォルダーに保存します。
1. リボンの **[ホーム] タブ**にある **[Copilot] ボタン**を選択し、**[Create presentation about...] (作成するプレゼンテーションの内容)** を選択してから、[Copilot] ペインに次のようにプロンプトを記入します。

    ```
    Create a presentation about a corporate cleaning service in New York City.
    ```

1. Copilot によってプレゼンテーションのスライドが生成されます。  このプロセスには数分かかる場合があり、テーマは異なりますが、出力は次のようになります。

    ![Word ドキュメントから Copilot によって作成された PowerPoint プレゼンテーションのスクリーンショット。](./media/generative-ai/copilot-powerpoint-create-image.png)

1. プレゼンテーションの最後から 2 番目のスライドを選択します。 次に、[Copilot] ペインで、**[...のスライドを追加]** プロンプトを使用して、`the benefits of an eco-friendly approach to cleaning.` に関する新しいスライドを作成します

    ![PowerPoint プレゼンテーションで新しいスライドが作成されたスクリーンショット。](./media/generative-ai/copilot-powerpoint-add-new-slide.png)

1. プレゼンテーションを保存します。

## 課題

これまで、Copilot for Microsoft 365 をいくつかの異なるアプリで 使用してどのようにアイデアを調査し、内容を生成するかを見てきました。それでは、さらに詳しく探っていきましょう。 Copilot を使って、地元の図書館で子どもの読み書きの能力を伸ばすイベントを計画してみてください。 試すことができる内容として、次のようなことが考えられます。

- 幼い年齢からの読書を奨励するためのヒントを調査する。
- イベントのチラシまたはポスターを作成する。
- 地元の児童文学作家をイベントに招待し、講演してもらうためのキャンペーン用メールを作成する。
- イベントを始めるためのプレゼンテーションを作成する。

独創性を自由に発揮しましょう。そして、Copilot が、情報を見つけ、文章を生成して練り上げ、画像を作成し、質問に答えることで、どのように自分を支援してくれるかを探ってください。

## まとめ

この演習では、[Copilot for Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise/copilot-for-microsoft-365) を使用して情報を見つけ、内容を生成しました。 コパイロットで生成 AI を使用することが、どのように生産性と創造性に役立つかを理解していただいていることが大切です。 Microsoft 365 を使用すると、ビジネスのデータとプロセスに生成 AI の能力を取り込むことができ、同時に、既存の IT インフラストラクチャにも統合して、管理可能で安全なソリューションを確保できます。
