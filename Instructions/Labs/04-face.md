---
lab:
  title: Vision Studio で顔を検出する
---

# Vision Studio で顔を検出する

Vision ソリューションは、多くの場合、AI が人間の顔を検出できることを必要とします。 架空の小売企業 Northwind Traders が、最適な支援を提供するために、顧客が店舗内のどこに立っているかを特定するとします。 これを実現する 1 つの方法は、画像内に顔があるかどうかを判別し、ある場合は、その場所を示す境界ボックス座標を返すことです。

Azure AI Face サービスの顔検出機能をテストするために、[Azure Vision Studio](https://portal.vision.cognitive.azure.com/) を使用します。 これは UI ベースのプラットフォームであり、コードを記述しなくても Azure AI Vision の機能を確認できます。

## "Azure AI サービス" リソースを作成する**

Azure AI Face サービスは、**Azure AI サービス**のマルチサービス リソースで使用できます。 まだ作成していない場合は、Azure サブスクリプションで **Azure AI サービス** リソースを作成します。

1. 別のブラウザー タブで Azure portal ([https://portal.azure.com](https://portal.azure.com?azure-portal=true)) を開き、ご使用の Azure サブスクリプションに関連付けられている Microsoft アカウントを使用してサインインします。

1. **[&#65291;リソースの作成]** ボタンをクリックし、「Azure AI サービス」を検索してください。** **[Azure AI** **サービスの作成]** プランを選択してください。 Azure AI サービス リソースを作成するためのページに移動します。 これを以下の設定で構成します。
    - **[サブスクリプション]**: *お使いの Azure サブスクリプション*。
    - **[リソース グループ]**: *一意の名前のリソース グループを選択するか、作成します*。
    - **[リージョン]**: "地理的に最も近いリージョンを選びます。** 米国東部の場合は、[米国東部 2] を使用します"。
    - **[名前]**: *一意の名前を入力します*。
    - **価格レベル**: *Standard S0。*
    - **[このボックスをオンにすることにより、以下のすべてのご契約条件を読み、同意したものとみなされます]**:*オン*。

1. **[確認 + 作成]**、**[作成]** の順に選択し、デプロイが完了するまで待ちます。

## Azure AI サービス リソースを Vision Studio に接続する

次に、上記でプロビジョニングした Azure AI サービス リソースを Vision Studio に接続します。

1. 別のブラウザー タブで、**Vision Studio** ([https://portal.vision.cognitive.azure.com](https://portal.vision.cognitive.azure.com?azure-portal=true)) にアクセスします。

1. ご使用のアカウントでサインインし、Azure AI サービス リソースを作成したのと同じディレクトリを使用していることを確認します。

1. Vision Studio のホーム ページで、**[Vision の利用を始める]** 見出しの下にある **[すべてのリソースを表示]** を選択します。

    ![[すべてのリソースを表示] リンクが、Vision Studio の [Vision の利用を始める] の下で強調表示されています。](./media/analyze-images-vision/vision-resources.png)

1. **[Select a resource to work with]\(操作するリソースの選択\)** ページで、上記で作成した一覧内のリソース上にマウス カーソルを置き、リソース名の左側にあるチェック ボックスをオンにしてから、**[Select as default resource]\(既定のリソースとして選択\)** を選択します。

    > **注**:リソースが一覧にない場合は、ページを **[更新]** することが必要な場合があります。

    ![[Select a resource to work with]\(操作するリソースの選択\) ダイアログが表示され、cog-ms-learn-vision-SUFFIX Cognitive Services リソースが強調表示されてオンになっています。 [Select as default resource]\(既定のリソースとして選択\) ボタンが強調表示されています。](./media/analyze-images-vision/default-resource.png)

1. 画面の右上にある [x] を選択して、設定ページを閉じます。

## Vision Studio で顔を検出する 

1. Web ブラウザーで、**Vision Studio** ([https://portal.vision.cognitive.azure.com](https://portal.vision.cognitive.azure.com?azure-portal=true)) に移動します。

1. **[Vision の使用を始める]** ランディング ページで、**[Face]** タブを選択し、次に **[Detect Faces in an image]\(画像内の顔を検出する\)** タイルを選択します。

1. **[Try It Out]\(試してみる\)** 小見出しで、リソース利用ポリシーを読んでチェック ボックスをオンにすることで承諾します。  

1. 各サンプル画像を選択し、返される顔検出データを確認します。

1. ここで、独自の画像をいくつか試してみましょう。 [**https://aka.ms/mslearn-detect-faces**](https://aka.ms/mslearn-detect-faces) を選択して、**detect-faces.zip** をダウンロードします。 次に、ご使用のコンピューターでそのフォルダーを開きます。

1. **store-camera-1.jpg** という名前のファイルを見つけます。これには次の画像が含まれています。

    ![店舗内の人物の画像。](./media/create-face-solutions/store-camera-1.jpg)

1. **store-camera-1.jpg** をアップロードし、返される顔検出の詳細を確認します。

1. **store-camera-2.jpg** という名前のファイルを見つけます。これには次の画像が含まれています。

    ![店舗内の人物が増えた画像。](./media/create-face-solutions/store-camera-2.jpg)

1. **store-camera-2.jpg** をアップロードし、返される顔検出の詳細を確認します。

1. **store-camera-3.jpg** という名前のファイルを見つけます。これには次の画像が含まれています。

    ![植物が顔を隠している店舗内の人物の画像。](./media/create-face-solutions/store-camera-3.jpg)

1. **store-camera-3.jpg** をアップロードし、返される顔検出の詳細を確認します。 隠れている顔が Azure AI Face によってどのように検出されなかったかについて注目してください。

この演習では、Azure AI サービスが画像内の顔をどれだけ検出できるかについて説明しました。 時間がある場合は、サンプル画像や独自の画像をいくつか自由にお試しください。

## クリーンアップ

これ以上の演習を行わない場合は、不要になったリソースを削除します。 これにより、不要なコストが発生することを防ぎます。

1. **Azure portal** ([https://portal.azure.com](https://portal.azure.com?azure-portal=true)) を開き、作成したリソースを含むリソース グループを選択します。
1. リソースを選択し、**[削除]** を、次に **[はい]** を選択して確定します。 これでリソースが削除されます。

## 詳細情報

このサービスでできることについて詳しくは、[Azure AI Face サービスに関するページ](https://learn.microsoft.com/azure/ai-services/computer-vision/overview-identity)を参照してください。
