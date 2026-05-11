# saigaikun

インタラクティブなテキストベースの防災ゲームを作成するための、シンプルなWebベースのフレームワークです。[Code for FUKUI](https://github.com/code4fukui)によって作成されたこのプロジェクトは、シンプルな選択肢ベースの物語を通じて、緊急時の対応戦略を学ぶための複数のシナリオを提供します。

## デモ

[**Saigaikunをプレイする**](https://code4fukui.github.io/saigaikun/)

![Saigaikunのメインメニュー。「なにと戦う？」と表示され、さまざまな災害シナリオの選択肢が並んでいる。](https://user-images.githubusercontent.com/1715217/156316472-5b6ed81d-18c4-4674-ac59-0e48cc2624ac.png)

## 特徴

-   **インタラクティブなシナリオ**: 地震、火事、台風などのさまざまな災害に直面し、選択によって異なる結果を導きます。
-   **教育的コンテンツ**: 学校での地震時に机の下に隠れたり、台風の時にヘルメットを使ったりするなど、実践的なサバイバルのヒントを学べます。
-   **シンプルなゲームエンジン**: 最小限のコードでテキストベースのアドベンチャーを作成できる軽量モジュール `egadv.js` をベースに構築されています。
-   **簡単に拡張可能**: シンプルなHTMLとJavaScriptファイルを記述するだけで、新しい災害シナリオを作成して追加できます。

## 自分のシナリオを作成する方法

オンラインエディタの [ES-Jam](https://code4fukui.github.io/htmlprac/) を使って、独自のシナリオを作成できます。

1.  **基本的なセットアップ**: 背景とテキストを表示します。
    ```html
    <script type="module">
    import { bg, show } from "https://js.sabae.cc/egadv.js";

    await bg();
    await show("A strong earthquake is coming!");
    await show("Make the right choices to survive.");
    </script>
    ```

2.  **選択肢の追加**: `show` 関数に文字列の配列を渡してプレイヤーに選択肢を提示します。関数は選択されたオプションを返します。
    ```javascript
    const ans = await show("What do you do?", ["Fight", "Run", "Use Item"]);
    if (ans == "Fight") {
        await show("You fought.");
    } else if (ans == "Run") {
        await show("You ran away.");
    } else if (ans == "Use Item") {
        await show("You used an item.");
    }
    ```

3.  **ループの作成**: `for` または `while` ループを使用して、条件が満たされるまでセクションを繰り返します。
    ```javascript
    for (;;) {
        const ans = await show("What do you do?", ["Continue", "End"]);
        if (ans == "End") {
            break;
        }
    }
    await show("Loop ended.");
    ```

4.  **別のページへのリンク**: 他のシナリオまたはメインメニューにリダイレクトします。
    ```javascript
    // Redirects to the main menu
    document.location = "./";
    ```

## 含まれるシナリオ

-   **地震**: モンスター「地震」が現れた。どうやって逃げる？
-   **火事**: 火事が現れた。たたかう、にげる、それともスマートフォンを使う？
-   **調理中の火事**: 調理中に火事が現れた。消火する最良の方法は？
-   **学校での地震**: 授業中に地震が現れた。
-   **台風**: 台風が現れた。外に出るのは安全？
-   **超強い台風**: 超強い台風が現れた。安全のためにどこへ行く？

## 詳細情報

このプロジェクトは、高専生とのワークショップの一環として開発されました。制作の背景については、以下のブログ記事（日本語）で詳しく読むことができます。

-   [高専生作、防災RPG「サイガイクン」とオープンソース入門ハンズオン](https://fukuno.jig.jp/3507)
-   [高専の先輩から学ぶ人生戦略と、シビックテック入門「サイガイクン」](https://fukuno.jig.jp/3533)

## ライセンス

このプロジェクトはMIT Licenseの下で利用可能です。
