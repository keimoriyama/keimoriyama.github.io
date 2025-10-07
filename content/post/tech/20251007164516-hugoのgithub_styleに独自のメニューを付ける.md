+++
title = "HugoのGithub Styleに自作のメニューを付ける"
author = ["keimoriyama"]
description = "description"
date = 2025-10-07T00:00:00+09:00
tags = ["tech"]
categories = ["tech"]
draft = false
+++

このブログは[Hugo](https://gohugo.io)の[Github Style](https://themes.gohugo.io/themes/github-style/)を少し設定している。

デフォルトだと、自己紹介などがブログに埋もれてしまうためメニューバーに追加した。

現状、一つ加える度にhtmlを触らないといけない実装になっているのが気になるが、動いているからヨシ!

`config.toml` に以下の要素を追加して、設定ファイルに追記すれば要素が追加されるようにした。

```toml
[[params.self]]
  name = 'Self'
  url="introduction/introduction"
```

そして、作成したHugoプロジェクト以下に `layouts/partial/menu.html` を作る。

`menus.html` の追加のメニューとして以下の変更を加えた。

```html
{{ range .Site.Params.projects }}
<a class="UnderlineNav-item
          {{ if .IsSection }}  selected  {{ end }}
          {{ if eq .Type " tags" }} selected {{ end }}"
   href="{{ absURL .url }}">
  {{ .name}}
</a>
{{ end }}
```

既存の実装では、リンクを貼る実装が `{{urls.JoinPath .Site.BaseURL url}}` になってる。

だが、上手く動作してくれなかったので `{{absURL .url}}` という実装にしている。
