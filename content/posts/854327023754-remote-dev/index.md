---
title: "ローカルマシンスペックに依存しないクラウド開発環境"
date: 2025-01-25
draft: true
description: "ローカル開発マシンに依存しないクラウド上での開発環境構築"
tags: ["AWS", "VScode", EC2]
---

- 20万以上は固定資産
- 低スペックノートPCでの動作
- [Cloud9サービスの廃止](https://aws.amazon.com/jp/blogs/news/how-to-migrate-from-aws-cloud9-to-aws-ide-toolkits-or-aws-cloudshell/)


## クラウド上マシンでの開発
### SSH接続
クラウド上のマシンにssh接続をしてvim等のCLI上でコードを編集して開発が考えられると思います。
ファイルのアップロードやダウンロードもコマンドでできるので軽微な修正等であればこれで問題ないと思います。
...

### VSCodeのRemote-ssh

拡張機能の[Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)をインストール


## 背景


