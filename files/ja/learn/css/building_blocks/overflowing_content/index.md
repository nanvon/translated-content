---
title: 要素のはみ出し（オーバーフロー）
slug: Learn/CSS/Building_blocks/Overflowing_content
---
{{LearnSidebar}}{{PreviousMenuNext("Learn/CSS/Building_blocks/Handling_different_text_directions", "Learn/CSS/Building_blocks/Values_and_units", "Learn/CSS/Building_blocks")}}

このレッスンでは、CSS のもう 1 つの重要な概念である **オーバーフロー（overflow）を見ていきます。オーバーフローは、ボックス内にコンテンツが収まりきらないときに発生します。このガイドでは、その詳細とそれらについてどのように対処するかを学びます。

| 前提条件: | 基本的なコンピューターリテラシー、[基本的なソフトウェアがインストールされている](/ja/Learn/Getting_started_with_the_web/Installing_basic_software)こと、[ファイルの扱い](/ja/Learn/Getting_started_with_the_web/Dealing_with_files)、HTML の基本（[HTML 入門](/ja/docs/Learn/HTML/Introduction_to_HTML)）および CSS に関するアイデア（[CSS の第一歩](/ja/docs/Learn/CSS/First_steps)）に関する基本的な知識を得ている。 |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 目的:     | オーバーフローとその管理方法を理解する。                                                                                                                                                                                                                                                                                                                                                                               |

## オーバーフロー (overflow) とは？

CSS のすべてがボックスであり、 {{cssxref("width")}} と {{cssxref("height")}}（または {{cssxref("inline-size")}} や {{cssxref("block-size")}}) の値を与えることにより、これらのボックスのサイズを制御できることを見てきました。オーバーフローはボックス内のコンテンツが多すぎる場合に発生し、快適に収まらないという状態です。CSS はこのオーバーフローを管理するためのさまざまなツールを提供しますが、早めに理解しておくと役立つ概念でもあります。CSS を書いていると、とりわけ CSS によるレイアウトを深く理解していくにつれ、オーバーフローによく出くわします。

## CSS のデータ損失の回避

オーバーフローが発生した場合の CSS の既定の動作を示す 2 つの例を見てみましょう。

1 つめの例です。まずブロックに `height` でボックスの高さを制限します。そしてそのスペースよりも多くのコンテンツを追加します。コンテンツはボックスからはみ出し、下の段落にかぶさってしまいます。

{{EmbedGHLiveSample("css-examples/learn/overflow/block-overflow.html", '100%', 600)}}

2 つめに、インラインとして制限されているボックス内の単語の例です。ボックスは単語が収まらないほど小さいため、ボックスからはみ出てしまいます。

{{EmbedGHLiveSample("css-examples/learn/overflow/inline-overflow.html", '100%', 500)}}

CSS のこの既定のアプローチは、コンテンツをかなり乱雑にオーバーフローさせているように感じられるかもしれません。追加のコンテンツを非表示にしたり、ボックスを大きくさせたりしないのはなぜなのでしょう。

CSS は可能な限りコンテンツを隠しません。これをやってしまうと、通常は問題となりうるデータ損失が発生するためです。CSS はこのようにコンテンツが消えることを懸念します。コンテンツが消失したことに気付かない可能性があるのは問題だからです。見ている人は消えたことに気付かないかもしれません。フォーム上の送信ボタンが消えてしまい、フォームが完了できない場合それは大きな問題です。代わりに CSS は目に見える方法でオーバーフローしようとします。あなたもしくは訪問者がコンテンツが重なっているという状況に気づき、修正が必要であることを知ることができます。

ボックスを `width` または `height` で制御している場合、CSS はオーバーフローの可能性が管理されていると想定します。一般にボックスにテキストがある場合、ブロックのサイズを制御することは問題になりがちです。例えば、想定していたよりも多くのテキストになってしまったか、フォントサイズを大きくした場合などです。

次のいくつかのレッスンでは、オーバーフローを起こしにくいサイジング方法を見ていきます。固定サイズが必要な場合は、オーバーフローの動作を制御することもできます。読み進めましょう。

## overflow プロパティ

{{cssxref("overflow")}} プロパティは要素のオーバーフローを制御し、ブラウザーにどのように動作させるかを伝えます。既定値は `visible` のため、オーバーフロー時にコンテンツは表示されます。

オーバーフロー時にコンテンツをトリミングしたい場合、`overflow: hidden` をボックスに指定します。これは文字通り、はみ出たものを見えなくします。これにより内容が隠れてしまうことが起こりうるため、コンテンツが非表示になっても問題にならない場合にのみに限定した方がいいでしょう。

{{EmbedGHLiveSample("css-examples/learn/overflow/hidden.html", '100%', 600)}}

コンテンツのオーバーフロー時にスクロールバーを表示したいこともあるでしょう。 `overflow: scroll` を指定すればコンテンツがオーバーフローしない場合でも、ブラウザーはスクロールバーを表示します。コンテンツに応じてスクロールバーが表示されたり消えたりするのを防ぐため、これが必要な場合があります。

**下のボックスからコンテンツの一部を削除すると、スクロールするものがなくてもスクロールバー（または少なくともトラック部品）が残っていることがわかります。**

{{EmbedGHLiveSample("css-examples/learn/overflow/scroll.html", '100%', 600)}}

上記の例では `y` 軸のスクロールバーだけがあればいいのですが、横スクロールバーも表示されてしまいます。{{cssxref("overflow-y")}} プロパティを使えば、`y` 軸のみのスクロールバーを指定できます。

{{EmbedGHLiveSample("css-examples/learn/overflow/scroll-y.html", '100%', 600)}}

{{cssxref("overflow-x")}} を使用して、x 軸のみのスクロールバーを表示できますが、文字が見切れてしまうことの回避策としては推奨されません。小さなボックスで長い文字列を処理する場合は、{{cssxref("word-break")}} や {{cssxref("overflow-wrap")}} を検討してください。[CSS によるサイズ設定](/ja/docs/Learn/CSS/Building_blocks/Sizing_items_in_CSS) で説明した方法のいくつかは、さまざまな量のコンテンツに適切に対応するボックスを作成するのに役立つ場合があります。

{{EmbedGHLiveSample("css-examples/learn/overflow/scroll-x.html", '100%', 500)}}

`scroll` にしておけばコンテンツが少ないとしても、それとは関係なくスクロールバーは常に表示されます。

> **Note:** `overflow` プロパティでは x と y の 2 つの値を渡すことができることに注意してください。2 つのキーワードが指定されている場合、ひとつめは `overflow-x`、2 つめは `overflow-y` として適用されます。それ以外の場合は `overflow-x` と `overflow-y` の両方に同じ値が設定されます。例えば、`overflow: scroll hidden` とした場合は、`overflow-x` は `scroll`、`overflow-y` は `hidden` となります。

コンテンツがボックスに収まらない場合にのみ、スクロールバーを表示する場合は `overflow: auto` を使用します。この場合、スクロールバーを表示するかどうかはブラウザーによります。通常、デスクトップブラウザーはコンテンツがオーバーフローする場合にのみそうします。

**以下の例では、ボックスに収まるまでコンテンツを削除していくとスクロールバーが消えます。**

{{EmbedGHLiveSample("css-examples/learn/overflow/auto.html", '100%', 600)}}

## オーバーフローとブロック整形コンテキスト

CSS には **ブロック整形コンテキスト** (BFC = Block Formatting Context) の概念があります。これは今のところあまり気にする必要はありませんが、`scroll` や `auto` などのオーバーフローの設定で BFC が作成されることを知っておくと便利です。結果として `overflow` の値を変更したボックスのコンテンツは、独自のミニレイアウトになります。コンテナの外側の物は中に突っ込むことができず、ボックスから周囲のレイアウトに突き出すこともできません。これによってボックスにはすべてのコンテンツが含まれており、かつ、ページ上の他のアイテムと重ならないという、一貫したスクロール体験を生み出します。

## オーバーフローの望ましくないウェブデザイン

モダンなレイアウト手法（[CSS レイアウト](/ja/docs/Learn/CSS/CSS_layout) モジュールで説明）では、オーバーフローを管理します。これらの方法は、ウェブページ上にどれだけのコンテンツが存在するかについての仮定や依存関係なしに大きく機能します。

しかし過去には開発者は多くの場合、固定された高さを使用して、実際には互いに関係のないボックスの底を揃えようとしました。それは脆く、レガシーなアプリケーションでは、コンテンツが他のコンテンツに重なってしまっているのを見かけることがあります。それによってオーバーフローが起きていることがわかります。理想としては、ボックスサイズの固定に依存しないようにレイアウトを調整します。

サイトを開発するときは、常にオーバーフローの問題に留意する必要があります。大量のコンテンツと少量のコンテンツを含むデザインをテストし、テキストのフォントサイズを大きくし、CSS が堅牢に対処できていると確認する必要があります。オーバーフローの値を変更してコンテンツを非表示にしたりスクロールバーを追加したりするのは、特別な場合（例えばスクロールが本当に必要な場合など）にのみ使うべきです。

## あなたのスキルをテストしてみてください!

このレッスンで吸収すべきことはたくさんあります！ あなたは最も重要な情報を覚えていますか？ あなたの理解度を確認するには、[Test your skills: overflow](/ja/docs/Learn/CSS/Building_blocks/Overflow_Tasks) を参照してください。

## まとめ

この短いレッスンではオーバーフローの概念を紹介しました。CSS はオーバーフローしたコンテンツが見えなくなることによる、データ損失の回避を試みることを理解しました。潜在的なオーバーフローを管理できること、また、問題のあるオーバーフローを引き起こしてしまわないかを確認する必要があることもわかりました。

{{PreviousMenuNext("Learn/CSS/Building_blocks/Handling_different_text_directions", "Learn/CSS/Building_blocks/Values_and_units", "Learn/CSS/Building_blocks")}}

## このモジュール

1. [カスケードと継承](/ja/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)
2. [CSS セレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors)

    - [要素・クラス・ID によるセレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors)
    - [属性によるセレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors)
    - [擬似クラスおよび疑似要素によるセレクター](/ja/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements)
    - [結合子](/ja/docs/Learn/CSS/Building_blocks/Selectors/Combinators)

3. [ボックスモデル](/ja/docs/Learn/CSS/Building_blocks/The_box_model)
4. [背景と枠線](/ja/docs/Learn/CSS/Building_blocks/Backgrounds_and_borders)
5. [テキスト方向の操作](/ja/docs/Learn/CSS/Building_blocks/Handling_different_text_directions)
6. [要素のはみ出し（オーバーフロー）](/ja/docs/Learn/CSS/Building_blocks/Overflowing_content)
7. [CSS の値と単位](/ja/docs/Learn/CSS/Building_blocks/Values_and_units)
8. [CSS によるサイズ設定](/ja/docs/Learn/CSS/Building_blocks/Sizing_items_in_CSS)
9. [画像・メディア・フォーム要素](/ja/docs/Learn/CSS/Building_blocks/Images_media_form_elements)
10. [表のスタイリング](/ja/docs/Learn/CSS/Building_blocks/Styling_tables)
11. [CSS のデバッグ](/ja/docs/Learn/CSS/Building_blocks/Debugging_CSS)
12. [CSS の整理](/ja/docs/Learn/CSS/Building_blocks/Organizing)
