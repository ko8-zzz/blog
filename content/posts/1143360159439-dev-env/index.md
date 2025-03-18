---
title: "Linux開発環境構築メモ"
date: 2025-01-25
draft: false
description: "Linux環境上における初期開発環境の設定メモ"
tags: ["Linux", "WSL2", "Mac"]
---

Linux環境を構築語に設定する内容のメモ

# 環境固有
## Windows
WSL2を使用してUbuntu環境を構築。
Windowsターミナルをダウンロードして、WindowsターミナルからUbuntuを開く。
### プロキシ設定
/etc/apt/配下にapt.confを作成し、下記を記載。
```
Acquire::http::Proxy "http://{proxy}:{port}";
Acquire::https::Proxy "http://{proxy}:{port}";
```

.zshrc(zshシェルの場合)下記を追記
```
export HTTP_PROXY=http://{proxy}:{port}
export HTTPS_PROXY=http://{proxy}:{port}
```

## Mac
標準のターミナルでも問題ないが、[iterm2](https://iterm2.com/)の方が利便性が良い。

## 共通
### ライブラリ

- [neovim](https://github.com/neovim/neovim)
- [fuzzyfinder](https://github.com/junegunn/fzf)
- [lazygit](https://github.com/jesseduffield/lazygit)