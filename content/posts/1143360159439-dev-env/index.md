---
title: "Linux開発環境構築メモ"
date: 2025-01-25
draft: false
description: "Linux環境上における初期開発環境の設定メモ"
tags: ["Linux", "WSL2", "Mac"]
---

Linux環境上における開発環境構築の手順メモを記載しています。

# 開発環境構築
## Windows
WSL2を使用してUbuntu環境を構築。
UbuntuはLTSバージョンを入れておけば良い。
Windowsターミナルをダウンロードして、WindowsターミナルからUbuntuを開くと便利。

### プロキシ設定
/etc/apt/配下にapt.confを作成し、下記を記載。
```
Acquire::http::Proxy "http://{proxy}:{port}";
Acquire::https::Proxy "http://{proxy}:{port}";
```

.zshrc(zshシェルの場合 / bashシェルの場合.bashrc)下記を追記
```
export HTTP_PROXY=http://{proxy}:{port}
export HTTPS_PROXY=http://{proxy}:{port}
```

### ターミナルをおしゃれに
[oh-my-zsh](https://ohmyz.sh/)をインストール(zshシェルの場合)。
[powerlevel10k](https://github.com/romkatv/powerlevel10k)でターミナルのデザインをおしゃれにできます。
フォントが文字化けする場合、公式から出ている[font](https://github.com/romkatv/powerlevel10k#fonts)からMesloLGSフォントをダウンロードして、ターミナルのデフォルトフォントとして設定すれば解決できます。

### バージョン管理パッケージ

[homebrew](https://brew.sh/)をインストールし、homebrew経由で様々なライブラリをインストールすると便利。

### プログラミング言語のバージョン管理

[asdf](https://asdf-vm.com/)が便利。Python,nodejs,go等基本的なプログラミング言語毎にバージョンを簡単に変更できる。

[mise](https://github.com/jdx/mise)もあるが、試していない。
rustの恩恵なのかasdfよりもオーバーヘッドが少ないようです。
実行コマンドも少なくバージョン管理ができるようなので、asdfから乗り換えても良さそう。

[sdkman](https://sdkman.io/)はJavaのバージョンを管理するのに便利。
Eclipseを使用せずに、CLIベースでJavaアプリケーションを開発する場合、Javaバージョンの切り替えを簡単にしてくれます。

### 便利なLinuxライブラリ
- [neovim](https://github.com/neovim/neovim)
- [fuzzyfinder](https://github.com/junegunn/fzf)
- [lazygit](https://github.com/jesseduffield/lazygit)

#### Neovimのカスタマイズ設定

Neovimの設定は[Lua](https://neovim.io/doc/user/lua-guide.html)で書いていきます。
WSL2のUbuntu環境上で動かしている場合、下記ファイルを作成する
~/.config/nvim/init.lua
作成したluaファイルにneovimの設定を記載する。

```lua

-- 行番号を表示
vim.opt.number = true

-- 相対行番号も表示（オプション）
vim.opt.relativenumber = true

```

# asdfのセットアップ

※asdfはバージョン1.16.0から後方互換性無しのバージョンアップがされています。
以降、バージョン1.16.0以降のコマンドです。
