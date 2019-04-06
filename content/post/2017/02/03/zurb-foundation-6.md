---
title: Zurb Foundation 6 を使うとサイト構築がとっても楽ちん
type: post
date: 2017-02-03T03:00:00+00:00
excerpt: 会社でも導入したFoundation6の使い方記事です。
categories:
  - CSS
  - Frontend
  - HTML
  - PROGRAMMING
tags:
  - Foundation

---
※ 当記事はFoundation 6.2時代に書かれたものです。現在のバージョンではXY-Gridが導入され、そちらを使用することが推奨されます。

本記事は**Zurb Foundation 6**についての解説書です。

筆者はCSSフレームワークを触ったことがない状態から1年間Foundation 6を試行錯誤している状態です。まだ使いこなせていない機能が幾つかありますが、Foundationは作業効率を上げるのに十分な力を持っているフレームワークです。

<!--more-->

既存WebサイトにFoundationが使用され困っている人や、Foundationを使用して制作をする人に活用していただけば幸いです。

本記事ではCSSフレームワークについては簡単な説明をしますが、Foundationはバックエンドのフレームワークに比べて簡単なため、Foundation 6の主な記法と、メリットが大きい機能を中心に解説します。

Foundationは日本語の情報こそ少ないですが、公式ドキュメントが充実しており、英語が読めなくてもビジュアルでなんとなく分かるので、実際に使う際には必ず公式ドキュメントを参照してください。

[Foundation for Site 6 Docs][1](http://foundation.zurb.com/sites/docs/)[^1][1]

[^1][1]: Foundation は Email用のHTMLテンプレートもありますが、通常はSiteを使用します。

# CSSフレームワーク

CSSフレームワークという言葉を聞いたことはあるでしょうか。

恐らくWEB制作経験者であれば、Normalize.cssやReset.cssなどのノーマライザーを使用したことがあると思います。これらもCSSフレームワークの1つです。

しかし、FoundationやBootstrapはそれらの機能を拡張し、便利なCSS定義の集合体となっています。

どういうことでしょうか。

実際にFoundationでの例を示します。

    // Flex-Gridを使用
    // Foundation、Bootstrap共に、コンテンツの横幅を12分割し、占拠するグリッド数を指定します。
    <div class="row align-middle">
    <div class="small-12 medium-6 large-expand column">BOX1</div>
    <div class="small-12 medium-6 large-expand column text-center">中央寄せのBOX2</div>
    <div class="small-12 large-expand column">BOX3</div>
    </div>
    

Foundationを読み込めば、上の書き方をするだけで

  * スマートフォン（small）ではBOXが縦並び
  * タブレットで（medium）ではBOX1とBOX2が横並び、BOX3はその下へ
  * パソコン（large）では横並びに
  * 真ん中のBOX2の文字は中央寄せに
  * 要素の高さが異なる場合は上下中央寄せ

の条件を満たすことができます。

これをSassまたはCSSで記述すると結構大変ですよね。

これはあくまでFoundationの最も基本な機能です。

この他にも沢山のことがHTMLへマークアップするだけで実装することができます。[^2][1]

[^2][1]: [FoundationのHTMLテンプレート][2]から構築例を見ることができます。これらはFoundationの導入をすればHTMLのみで実現できます。

以下はCSSフレームワークを導入して感じたことです。

  * HTML編集の際に、CSSの編集へと行ったり来たりする回数が減る。
  * HTMLを見ればどのようなCSSが定義されているかひと目で分かる。
  * CSSファイルを再利用すれば、同じ条件で他案件を制作できる。
  * ベンダープレフィクスなどの面倒な記述を隠蔽してくれる。
  * Foundationを理解していれば共通の単語でコミュニケーションを取ることができ、保守やレビュー、指示が楽になる。

それぞれの理由は地味ですが、実際に使ってみれば効果が実感できるはずです。

さあ、Foundationを使ってみましょう。

# Zurb Foundation

CSSフレームワークという言葉を聞いたことはあるでしょうか。

Web制作を経験したことのある方は、Bootstrapなら知っているかもしれませんね。

いわゆるリキッドレイアウト（デバイスの横幅に応じた表示切り替え）を簡単に作ることができます。

## なぜFoundationなのか

Boostrapは普及しすぎました。いかにもBootstrapっぽいデザインを回避するにはフレームワークへの改造が必要になります。

Foundationは日本ではマイナーなため、Bootstrapっぽい見た目を回避できます。

また、Javascriptによる便利なツールがいくつか用意されています。

[^2][1]: Bootstrap3になってからBootstrapにも便利な機能が増えているようです。チェックはしていませんが…

  * 横並びのパネルの要素の高さを揃える
  * アコーディオンメニューの作成

など、顧客からの「言うのは簡単だけど実装するには時間がかかる」要望に対応し易いこともお勧めポイントです。

## どうやって導入するの？

Zurb Foundation公式ページに行くと、ダウンロード項目が4つあり悩んでしまいます。

しかし、大抵必要なのは「Custom」と「Sass」だけです。

実際の使い方は公式や他の紹介記事に譲りますが、大きな違いがありますので簡単に紹介します。

もしWordPressでFoundationを使用する場合は、JointsWPという便利なテーマがありますので、そちらを使いましょう。

### Sassバージョン

出来る限りSass使いましょう。CSSをそのまま触る時代は過ぎてます。

製作中に主要カラーの変更、コンテンツ幅の変更などのFoundationのセッティングを自由自在に行なえます。

特にSassバージョンでしかできない機能として**ブレイクポイントの調整**があります。

通常、small、medium、largeの3種類のブレイクポイントがありますが、「xlargeを追加して其々のブレイクポイントを変える」と言った小技を使用できるようになります。

その他にもSassバージョンの基礎となる_settings.scssで大抵のことは設定できるので、Sassバージョンを導入したらぜひ一度目を通しましょう。_

Sassを知っている人なら公式ドキュメントでわかると思います。

[Install SCSS Version][1](http://foundation.zurb.com/sites/docs/sass.html)

Sassを知らない人はココで説明しきれないくらい説明しないといけないので、

  * SassまたはScss
  * タスクランナー

について調べてください。

Sassを導入したくない人やスマホ対応などのスクラッチでない案件の場合は次へどうぞ

### CSSバージョン

「Custom」は自分で指定できる「Complete」だと思えば大丈夫です。

色々な設定項目がありますが、最初に触るのは枠だけで十分です。

それぞれの項目について解説してからCustomのメリットを纏めていきます。

#### Grid

カラム落ちやグリッドシステムの手法を選びます。

  * `float: left`によるグリッド
  * `display: flex`によるグリッド
  * No Gridは無視

`display: flex`でWeb制作をしたことがあることなら察しが付くかもしれません。

**Flex GridはIE9に対応しません**

とっても大事なので2回書きます。

**Flex GridはIE9に対応しません**

ですので、選択は

  * モダンブラウザ対応のみならFlex Grid
  * IE9などのレガシーに対応するならGrid

だけです。可能な限りFlex Gridがおすすめです。

選択肢によって使えるクラスが変わりますので、仕様を確認して選択しましょう。

**経験上後から変更する作業は、1から対応するより楽ですが、結構大変です。**

#### Set Your Defaults

タイトルどおり、ここでレイアウトや色の設定を行えます。

##### The Grid

単位の`rem`はCSS3から使用されているルートの文字サイズを基準とする単位です。[^3][1]

[^3][1]: remはあくまで文字の縦幅（フォントサイズ）が基準です。**5remは5文字の幅でない**ことに注意

Foundationの初期フォントサイズは16pxですので、デフォルトでは

  * 全体幅 62.5文字 = 1000px
  * カラム同士の余白（ガター） = 30px

となっています。

サイドバーが必要なサイトでは1200pxまで上げることもありますし、

サイドバーがないLPサイトの場合は960pxでも十分です。

仕様に合わせて変更しましょう！

##### Colors

Customを使う理由はこの色設定にあります。

まずは[Kitchen Sink][3]をご覧ください。

ここに「青」「灰」「緑」「黄」「赤」の各色が少しずつ出てきますが、

**初期設定ではその色になります！ポップすぎます！**

これでは楽しいWebサイト以外では使いづらいため、ここで色設定をする。というわけです。

補足ですが、Primary Colorは初期設定のボタンやリンク色など随所で使用されますので慎重に選びましょう。他の色は指定しない限り使用されません。

#### 他の設定は？

それぞれの機能をオンオフできます。

[Kitchen Sink][3]を見て、使わないな〜と思う機能があればチェックを外すだけでOKです。

機能をオフにすればライブラリが軽量になりますが、案外使う機能があるため慣れるまでは下記の手順を踏むとよいでしょう。

  1. 最初は全機能導入して制作
  2. Foundationファイルをいじっていない & 使用していない機能が多かったら、不要な機能を排除したCustomで差し替え

#### 導入

あとはダウンロードしてインポートするだけです。

方法は一般的なjsファイルやcssファイルと変わりません。

### Completeは使わないの？

なぜZurb一押しの「Complete」を使わないのか。それは上記の色の変更機能が提供されていないから。です。

Sassバージョンを見ればわかりますが、随所で`color: primary-color;`の指定が見られ、手で書き直すのが大変です。私の場合、Completeを使うのは以下の条件です。

  * Foundationの初期配色で問題ない場合
  * 既存サイトにFoundationを埋め込むため色設定を使用しない

それでもGridの幅設定は少々面倒なので、できるだけCustomの使用をおすすめします。

### WordPressテーマ「JointsWP」

有志が制作したWordPress用のFoundationブランクテーマです。

SassバージョンにはGulpfileが同梱されており、Node + Gulpでのコンパイル環境が整っていればすぐに開発をスタートできます。また、WordPress独自のClass（`.page-title`など）も定義されているので、書き換えが簡単です。

#### ヘッダーパーツについて

**テーマフォルダの /parts 内に複数種類のヘッダーファイルが用意されています。**

  * `<?php get_template_part( 'parts/nav', 'offcanvas' ); ?>` → Off-canvasを利用したメニューです。
  * `<?php get_template_part( 'parts/nav', 'title-bar' ); ?>` → シンプルなタイトルバーです。

のようにheader.phpの呼び出しファイルを書き換えるだけで、好きなヘッダーレイアウトを簡単に採用することができます。

[JointsWP][4]

## どうやって使うの？

先程も出てきましたが、Foundationの機能は[Kitchen Sink][3]にまとまっています。それでも機能がとっても多いので、重要な機能を説明していきます。

### Grid（Flexではない）

最初の説明にも出てきたGridです。

これはFoundationのコア機能であり、通常のGridとFlex Gridで仕様が異なるため、重点的に解説します。

[Grid][5] ページを見てください。

Gridの大事な機能は以下の点です。

  * 合計値が12を超える場合はカラム落ちする
  * ネストは何回層でも可能
  * ブレイクポイントによってカラム幅を変えられる
  * ブレイクポイントの指定がない場合、**ブレイクポイントが小さい方の指定が適用される**
  * `expanded`でブラウザ幅へ拡張可能
  *  **`column`にサイズ指定がない場合は`small-12`と同じになる**
  * カラムの中央寄せが可能
  * カラム同士の余白を消すことが可能
  * 順番の入れ替えは`[size]-push-*`または`[size]-pull-*`を併用

以下はコード例です。

    <div class="row">
    <div class="small-6 large-4 column">A</div>
    <div class="small-6 large-4 column">B</div>
    <div class="small-12 large-4 column">C</div>
    </div>
    

### Flex Grid

Flex GridはGridを拡張したものです。

[Flex Grid][6]こちらを見てください。

基本的な機能はGridと同じですが、同じ記法が使えない点があります。

  * 順番の入れ替えは`[size]-order-*`で指定
  * **`column`にサイズ指定がない場合は自動的に`small-expand`と同じになる**

順番の入れ替え指定と、classに`column`しか指定がない場合の挙動が変わるため注意してください。

以下はGridから拡張機能として使用できます。

  * `row`に`align-middle`と指定すると**カラムが上下中央寄せになる**
  * `row`に`align-justify`や`align-spaced`などの`justify-content: ***`に相当するプロパティを指定できる
  * `[size]-expand`の指定で、**余った幅を自動で埋めることができる。**（expand同士は等分割され、グリッドは無視される）
  * `column`に`shrink`を指定すると、カラムがコンテンツに合わせた最小幅となる（グリッドは無視される）

先程のコード例をFlex Gridで書くとこうなります。

    <div class="row">
    <div class="column">A</div>
    <div class="column">B</div>
    <div class="small-12 large-expand column">C</div>
    </div>
    

コード量が減っているのがわかると思います。

**カラムは大抵等分割**なので、`column`だけの指定で事足りることが多いのです。

### Visibility Classes

ブレイクポイントによっての表示、非表示を指定できます。**頻繁に使用します。**

    <div class="hide-for-large"></div>
    

これだけでパソコン表示時は要素が`display: none;`になります。

### Callout

ただのボックスですが、`padding`などが度整形されているため、ちょっとした注意書きに重宝します。

デフォルトでは`callout warning`とすれば`warning`を薄くした色が背景に適用されます。

CSSをオーバーライドして使うことが多いです。

### Button

Classに`button`とつけることでフラットなボタンになります。

`button warning large`、`button secondary small`など、色やサイズを変更できます。

### Equalizer

Foundationを使う理由の1つです。

例のようにCalloutを並べる際に「ボックスの高さを揃えたい！」という要望を叶える優れものです。

    <!-- row に data-equalizer -->
    <div class="row" data-equalizer data-equalize-on="medium" id="test-eq">
      <div class="columns">
    <!-- 揃えたい要素に data-equalizer-watch -->
    <div class="callout" data-equalizer-watch>A</div>
      </div>
      <div class="columns">
    <div class="callout" data-equalizer-watch>B</div>
      </div>
      <div class="columns">
    <div class="callout" data-equalizer-watch>C</div>
      </div>
    </div>
    

基本的な機能は↑だけで実装できます。

### Off-canvas

スマートフォンで「メニューを開くをタップすると画面毎横に移動するメニュー」を簡単に実装できます。

[Site Demo][7] このテンプレートで画面幅を狭くすると実際の動きを見ることができます。

高機能に見えるので、単価アップを狙えるかも。

### Sticky

「スクロールをしても画面上部で固定されて付いてくるサイドバー」を実装できます。

### Tabs

クリックで表示内容を切り替える「タブ」を実装できます。

### Toggler

「クリックをすると、指定したDOMに対しClassのAppend、Removeをする」というJavascriptの動作を簡単に実装できます。

### Accordion

「親リストをクリックすると、子リストが開く」というアコーディオンメニューを実装できます。

### Interchange

画面サイズによって表示する画像を切り替えます。

残念ながらRetinaと併用できないので、使用場所は限られます。

他にも沢山ありますが、残りの殆どはPHPやJavascriptアプリケーションに組み合わせると有効なものが多いです。

* * *

 [1]: #
 [2]: http://foundation.zurb.com/templates.html
 [3]: http://foundation.zurb.com/sites/docs/kitchen-sink.html#accordion
 [4]: http://jointswp.com/
 [5]: http://foundation.zurb.com/sites/docs/grid.html
 [6]: http://foundation.zurb.com/sites/docs/flex-grid.html
 [7]: http://foundation.zurb.com/templates-previews-sites-f6/portfolio.html