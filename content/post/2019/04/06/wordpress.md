---
title: 脱Wordpressした話
type: post
date: 2018-04-06T00:16:49+09:00
categories:
  - WEB
tags:
  - Wordpress
  - Hugo
  - Blog
---

## まとめ

- Wordpressの保守は面倒くさい
- データベースレス最高
- Markdown最高

## Wordpressは面倒

WordpressはとてもメジャーなCMSで頻繁にアップデートがあります。しかも無料。

プラグインも大量にあり、知識がなくともブログを運営できます。しかも無料。

が、それゆえに逆に面倒なことがたくさんあります。

- データベース
- Wordpress本体
- プラグイン
- テーマ

これが密に絡み合って、少し凝ったことをしようとすると、全部の管理をしないいけません。

しかもメンテナンスを怠ればWordpressを狙った攻撃に晒されるオマケ付き。

数ヶ月に1回記事を書くようなブログには荷が重すぎるのが現状なのです。

今回は、「WPのメンテナンスが面倒 → 更新しない」という負の連鎖から逃れるため、**Hugo**という静的サイトジェネレータと**Netlify**というホスティングサービスに乗り換えた話をします。

## 静的サイトジェネレータ

そこで静的サイトジェネレータ。

WordpressのようにPHPで動的にサイトを生成するのではなく、手元で生成したHTMLをアップロードする男気あふれる手法です。

管理画面がないので攻撃に強く（サーバーへの直接攻撃は除く）、アップロードしたらほぼ放置で大丈夫というわけ。

物臭な私にぴったりな方法です。

### ホームページビルダーとHugo

「それってホームページビルダーでは？」

というツッコミが聞こえてきます。

そう。静的サイトHTMLを作ってアップロードするならホームページビルダーと同じです。

ホームページビルダーは、実際に表示される見た目のまま編集し、HTMLを生成してアップロードします。

しかし、最近注目されている静的サイトジェネレータ＋CIでの運営方法は従来の方法とは大きく異なります。

- Markdownで記事をかける
- 管理画面、GUI一切なし
- Git と CI で更新する

### Markdown

プレーンテキストで整形方法を指定できるテキストフォーマットです。

```
## 見出し

こんな感じで、文字の装飾一切なしで記述していきます。

- 箇条書きはこんなかんじ
- 太字は**これ**で囲むだけ
```

こんな書き方で記事を書けるので、HTMLでタグを囲う手間もなく、Wordのようにいちいち太字指定する手間がありません。

そしてただの文字なので**どんな環境でも編集**できることが大きなメリットです。

### 管理画面、GUIなし

ログインする管理画面はありません。必要なのは**テキストエディタ**と**ターミナル**。

Wordpressは管理画面の初期URLが /wp-admin となっており、IDとパスワードさえ知っていればログインできてしまいます。

そもそもそんな管理画面がなければ、攻撃される恐れはありません。

そして**テキストエディタ**と**ターミナル**は大抵の環境にあるため、**どんな環境でも編集**できることが大きなメリットです。（2回目）

### Git と CI で更新する

FTPはもう使いません。

Git Push するだけで、Netlifyが勝手に更新をしてくれます。

前述の環境が整っていれば Git 環境は整えられるため、**どんな環境でも編集**できることが大きなメリットです。（3回目）

## 一旦まとめ

Hugo + Netlify という更新環境へ移行できたのは、Wordpress並に編集環境を選ばないことと、メンテナスの手間が大幅に減らせるからです。

次回は、Markdownで編集する静的サイトジェネレータのうち、Hugoを選んだ理由について書きたいと思います。