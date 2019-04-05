---
title: Windows10でRuby on Rails開発はつらい
type: post
date: 2017-01-25T12:36:43+00:00
categories:
  - Ruby

---
最近Ruby on Railsの勉強を始めました。

Pro Gateという学習サイトで一通り流れをつかみ、Rails TutorialはCloud9で数章進めました。

そうなってくると、「できるだけ実際の開発環境でRails Tutorialやりたいな！」と思うものです。

手元にあるのはIntteliJ IDEAとWindows10とMac Book Air 11inch。本当はMacでやりたいけど11inchだから開発にはつらい…

そこでやむを得ずWindows10へ環境を構築することにしたのですが…

  * RubyInstallerからRubyを入れる
  * Rails 5.0.0.1を入れる
  * Ruby 2.3系がSQLiteと相性が悪いらしく、そのまま2.2系を再インストール
  * Ruby切り替えできないじゃん。Rumix入れてみよう

上の流れの間にもHerokuへ `git push heroku master`するとgemのバージョン違いでエラーを吐くなど、たくさんの問題が発生しました。

もう後戻りが出来ないくらい環境が汚染されて来たので、Virtual Boxにelementary OSを入れて環境構築しようかな…

<div class="kirin_box">
  教訓：WindowsでRuby，Pythonの開発をしようなんてしちゃだめだぞ！
</div>