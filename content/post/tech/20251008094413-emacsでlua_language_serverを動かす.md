+++
title = "Emacsでlua-language-serverを動かす"
author = ["keimoriyama"]
description = "emacs-lsp-lua-ls"
date = 2025-10-08T00:00:00+09:00
tags = ["tech"]
categories = ["tech"]
draft = false
+++

Emacsのlsp-modeでlua-language-serverを動かそうとしたら、ハマったのでメモ。

[モテるターミナルにカスタマイズしよう（WezTerm）](https://zenn.dev/mozumasu/articles/mozumasu-wezterm-customization)を見て、weztermを設定しようとした。

設定ファイルである `wezterm.lua` をEmacsで編集するためにluaの環境を整えようとしたら、Lua-language-serverを `lsp-mode` が認識しなかった。

加えて、自動でインストールしようとしたら、emacsがフリーズしてしまった。

動作させるために必要だった設定は以下の通り。

```emacs-lisp
(setq lsp-clients-lua-language-server-bin (format "%s/.nix-profile/bin/lua-language-server" (getenv "HOME"))
      lsp-clients-lua-language-server-main-location (format "%s/.lua-language-server/main.lua" (getenv "HOME")))
; reference : https://github.com/emacs-lsp/lsp-mode/issues/4688#issuecomment-3138937688
(defun my/lsp-clients-lua-language-server-test ()
  "(Improved) Test Lua language server binaries and files."
  (or (and (f-exists? lsp-clients-lua-language-server-main-location)
           (f-exists? lsp-clients-lua-language-server-bin))
      (f-exists? (car (split-string lsp-clients-lua-language-server-command)))))

(advice-add #'lsp-clients-lua-language-server-test
            :override #'my/lsp-clients-lua-language-server-test)

```

lsp-mode自体にもIssueが上っていたためそれを参考にして設定したら動作した。

私はnixを使用してlua-language-serverをインストールしている。
インストールする時に、lua-language-serverの `main.lua` を適当な場所に配置する。

この `main.lua` の場所を `lsp-clients-lua-language-server-main-location` に設定し、 `lsp-clients-lua-language-server-bin` にlua-language-serverをインストールしたPathを設定する。

最後に、[このIssueコメント](https://github.com/emacs-lsp/lsp-mode/issues/4688#issuecomment-3138937688)にある関数をコピペしたら動いた。

参考 : [Externally provided lua-language-server is not recognized #4688](https://github.com/emacs-lsp/lsp-mode/issues/4688)
