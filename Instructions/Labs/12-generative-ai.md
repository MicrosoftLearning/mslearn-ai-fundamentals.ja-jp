---
lab:
  title: Microsoft Edge で Copilot を探索する
---
# Microsoft Edge で Microsoft Copilot を探索する

この演習では、Microsoft Copilot で生成 AI を使用して、新しいコンテンツを作成する際の生産性を高める方法をいくつか探っていきます。 この演習のシナリオでは、まず、ビジネスのアイデアに関する大まかなメモを作成し、Microsoft Edge で Copilot を使用して、見込み投資家に向けてビジネス プランとプレゼンテーションを作成できるようにします。

この演習の所要時間は約 **40** 分です。

> **注**:この演習では、[個人用の Microsoft アカウント](https://signup.live.com) (outlook.com アカウントなど) があり、それを使用して、コンピューター上の [Microsoft Edge](https://www.microsoft.com/edge/download) にサインインしていることを前提としています。

## Copilot を使用してドキュメントを調べ、アイデアをリサーチする

生成 AI の探索を始めるために、Edge で Microsoft Copilot を使用して既存のドキュメントを調べ、そこから分析情報を抽出することにします。

1. Microsoft Edge で、`https://onedrive.live.com` の [OneDrive](https://onedrive.live.com) を参照し、個人用の Microsoft アカウントを使用してサインインします。表示されるウェルカム メッセージやオファーはすべて閉じます。
1. 他のブラウザー タブで、`https://github.com/MicrosoftLearning/mslearn-ai-fundamentals/raw/main/data/generative-ai/Business%20Idea.docx` にある [Business Idea.docx](https://github.com/MicrosoftLearning/mslearn-ai-fundamentals/raw/main/data/generative-ai/Business%20Idea.docx) ドキュメントを開きます。 そして、Edge でドキュメントが開いたら、**OneDrive にコピーを保存**するオプションを選択し、OneDrive の **[ドキュメント]** フォルダーにドキュメントを保存します。 その後、ドキュメントは Microsoft Word で自動的にオンラインで開きます。

    > **ヒント**: ファイルのコピーを OneDrive に保存するオプションが表示されない場合は、ローカル コンピューターにダウンロードします。 その後、OneDrive で **[ドキュメント]** フォルダーを開き、[**+ 新規追加]** ボタンを使用して、**Business Idea.docx** ファイルをローカル コンピューターから OneDrive にアップロードします。

1. **Business Idea.docx** でテキストを表示します。これには、ニューヨーク市のクリーニング ビジネスに関する大まかなアイデアが記載されています。
1. 次に示すように、Edge ツール バーの **Copilot** アイコンを使用して、[Copilot] ペインを開きます。

    ![Microsoft Edge の [Copilot] ペインのスクリーンショット。](./media/generative-ai/edge-copilot.png)

1. [Copilot] ペインで、必要に応じて下にスクロールしてすべてのコンテンツを確認し、**[チャット]** タブが選択されていること、および会話スタイルが **[More Balanced] (バランス優先)** に設定されていることを確認します。これにより、Copilot は、創造性と事実の精度のバランスを取りながら応答するようになります。
1. [Copilot] ペインの下部にあるチャット ボックスに、次のプロンプトを入力します。

    ```
    What is this document about?
    ```

    メッセージが表示されたら、Copilot によるページへのアクセスを許可することを確認します。

1. Copilot からの応答を確認します。次に示すように、ドキュメントの要点がここに要約されています。

    ![応答が示されている [Copilot] ペインのスクリーンショット。](./media/generative-ai/copilot-response.png)

    > **注**:実際の応答は異なる場合があります。

1. 次のプロンプトを入力します。

    ```
    How do I go about setting up a business in New York?
    ```

1. 応答を確認します。この応答には、ニューヨークでビジネスを始めるのに役立つアドバイスと、リソースへのリンクがいくつか含まれているはずです。また、詳細情報を取得するための推奨フォローアップ プロンプトが含まれる場合があります。

    > **重要**: AI によって生成される応答は、Web 上で公開されている情報に基づきます。 これは、ビジネスを開始するうえで必要な手順を理解するのに役立つ場合がありますが、100% 正確であるという保証はなく、専門家のアドバイスの必要がなくなるわけではありません。

## Copilot を使用してビジネス プランのコンテンツを作成する

最初の調査を行ったので、Copilot を利用してクリーニング会社のビジネス プランを策定することにします。

1. Microsoft Edge で **Business Idea.docx** ドキュメントを開いたまま、[Copilot] ペインに次のプロンプトを入力します。

    ```
    Suggest a name for my cleaning business
    ```

1. 提案を確認し、クリーニング会社の名前を選びます (または、プロンプトの入力を続けて、好みの名前を探します)。
1. 次のプロンプトを入力します。*Contoso Cleaning* は任意の会社名に置き換えます。

    ```
    Write a business plan for "Contoso Cleaning" based on the information in this document. Include an executive summary, market overview, and financial projections.
    ```

1. 応答を確認し、出力の下にある **[コピー]** (&#128461;) アイコンを使用して、それをクリップボードにコピーします。 次に、**Business Ideas.docx** ドキュメント内のすべてのテキストを選択し、コピーしたテキストをドキュメントに貼り付けて置き換えます。 最後に、応答の最初のテキスト (Copilot が指示を確認したテキスト) を、クリーニング会社名の見出しに置き換えて、貼り付けたテキストを整理します。 最終的には、次のようなビジネス プラン ドキュメントになります。

    ![Copilot によって生成されたビジネス プランを含む Word ドキュメントのスクリーンショット。](./media/generative-ai/generated-content.png)

1. [Copilot] ペインで、次のプロンプトを入力します。

    ```
    Create a corporate logo for the cleaning company. The logo should be round and include an iconic New York landmark.
    ```

1. 応答を確認します。Microsoft Designer によって作成されたロゴに 4 つのオプションが表示されているはずです。
1. 他のプロンプトを使用しながらデザインを繰り返し (`Make it green and blue` など)、納得のいくロゴに仕上げていきます。
1. 好みのロゴ デザインを右クリックし、クリップボードにコピーします。 そして、次のように、ビジネス プラン ドキュメントの先頭にそれを貼り付けます。

    ![Copilot によって生成された画像を含む Word ドキュメントのスクリーンショット。](./media/generative-ai/generated-image.png)

1. [Microsoft Word] タブを閉じ、OneDrive の **[ドキュメント]** フォルダーに戻ります。

## Copilot を使用してプレゼンテーションの内容を作成する

Copilot のサポートを利用し、クリーニング ビジネス アイデアのビジネス プランのドラフトを作成しました。 次に必要なのは、ビジネスを始めるための資金を提供してもらえるよう投資家を説得する効果的なプレゼンテーションです。

1. OneDrive の **[ドキュメント]** フォルダーに、新しい **PowerPoint プレゼンテーション**を追加します。

    **[Designer]** ペインが自動的に開いた場合は、閉じます。

1. プレゼンテーションのタイトル スライドで、クリーニング会社の名前をタイトルとして、`Investor Opportunity` をサブタイトルとして入力します。
1. (タイトルと、2 つのコンテンツ プレースホルダーが含まれる) **[2 つのコンテンツ]** スライド レイアウトを使用して、新しいスライドを追加します。
1. スライドのタイトルを `Benefits of Hiring a Commercial Cleaner` に変更します。
1. [Copilot] ペインで、次のプロンプトを入力します。

    ```
    Write a summary of the benefits of using a corporate cleaning company for your business. The summary should consist of five short bullet points.
    ```

1. Copilot の応答をクリップボードにコピーし、左側のコンテンツ プレースホルダーに貼り付けます。 次に、要求を確認する最初の文を削除し、納得がいくまでプレースホルダー内のテキストを再フォーマットします。
1. [Copilot] ペインで、次のプロンプトを入力します。

    ```
    Create a photorealistic image of a clean office.
    ```

1. 好みの画像が Copilot によって生成されたら、それをクリップボードにコピーし、スライドの右側にあるコンテンツ プレースホルダーに貼り付けます。

    **[デザイナー]** ペインが自動的に開いた場合は、好みのスライド デザインを選択します。 その後、**[デザイナー]** ペインを閉じます。

1. 次のようなスライドが作成されるまで、必要と思われる追加の再フォーマットを適用します。

    ![Copilot によって生成されたコンテンツを含む PowerPoint プレゼンテーションのスクリーンショット。](./media/generative-ai/powerpoint-slide.png)

1. PowerPoint タイトル バーで、既定のプレゼンテーション名 (**プレゼンテーション**) を選択し、名前を `Business Presentation.pptx` に変更します。
1. [PowerPoint] タブを閉じ、OneDrive の **[ドキュメント]** フォルダーに戻ります。

## Copilot を使用してメールを作成する

ビジネスを始めるための資料をいくつか作成してきました。 次は、スタートアップ企業に資金提供しようとしている投資家にアピールします。

1. OneDrive タイトル バーの左端にある**アプリ起動ツール**を使用して、**Outlook** を開きます。
1. 新しいメールを作成し、**[宛先]** ボックスにご自分のメール アドレスを入力します。
1. [Copilot] ペインで **[作成]** タブを選択します。その後、次のオプションを設定して、新しいコンテンツを作成します。
    - **内容**: `Request a meeting with an investment bank to discuss funding for a commercial cleaning business.`
    - **トーン**: Professional
    - **形式**: メール
    - **長さ**: 中
1. **[Generate draft] (下書きの生成)** を選択し、生成された出力を確認します。
1. 次に示すように、生成されたコンテンツを使用してメールを完成させます。

    ![Copilot によって生成されたメールのスクリーンショット。](./media/generative-ai/generated-email.png)

    必要に応じて、自分宛てにメールを送信できます。

## 課題

これまで、Copilot を使用してどのようにアイデアを調査し、内容を生成するかを見てきました。それでは、さらに詳しく探っていきましょう。 新しい Copilot セッションを開始するために、**[チャット]** タブで、プロンプト ボックスの横にある **[新しいトピック]** アイコンを選択し、Copilot を使って、地域の図書館で児童の読み書き能力を向上させるイベントを計画してみてください。 たとえば、次のようなことを試すことができます。

- 幼い年齢からの読書を奨励するためのヒントを調査する。
- イベントのチラシまたはポスターを作成する。
- 地元の児童文学作家をイベントに招待し、講演してもらうためのキャンペーン用メールを作成する。
- イベントを始めるためのプレゼンテーションを作成する。

独創性を自由に発揮しましょう。そして、Copilot が、情報を見つけ、文章を生成して練り上げ、画像を作成し、質問に答えることで、どのように自分を支援してくれるかを探ってください。


## まとめ

この演習では、Microsoft Edge で Copilot を使用して情報を見つけ、内容を生成しました。 Copilot で生成 AI を使用すると、生産性と創造性の向上に役立つことが、おわかりいただけたと思います。

この演習で使用した無料のサービスが非常に強力であることは間違いありません。しかし、[Copilot for Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise/copilot-for-microsoft-365) などのサービスを使用すれば、さらに多くのことを実現できます。この Copilot for Microsoft 365 では、Microsoft Copilot は、Windows および Microsoft Office の生産性向上アプリケーションに統合され、一般的なタスクに関する高度にコンテキスト化されたヘルプを提供します。 Microsoft 365 を使用すると、ビジネスのデータとプロセスに生成 AI の能力を取り込むことができ、同時に、既存の IT インフラストラクチャにも統合して、管理可能で安全なソリューションを確保できます。