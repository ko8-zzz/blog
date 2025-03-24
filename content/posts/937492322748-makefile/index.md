---
title: "MakefileによるCLIコマンド省略"
date: 2025-01-25
draft: false
description: "Makefileを使って良く使うコマンドをメモして楽をしよう"
tags: ["streamline"]
---

# 概要

よく使用する長いCLIコマンドをメモして簡易的に使用できます。
過去に使用していたコマンド等はhistory等で探して覚えずにすんでいましたが限界があります。
```
history | grep hogehoge
```
Makefileを使用することでどんなに長いコマンドでも省略して実行できるので使わない手は無いです。
特にbuild test deploy等、特定の順序毎に個別で実行しなければいけないシェルスクリプトやDockerコマンド等の使用の際に使えると思います。

## 事前準備

Ubuntu上(WSL2でも可)で使用する場合、下記でmakeをインストールします。
gcc等も同時にインストールされるので、不必要な型は個別にmakeをインストールしてください。
```
sudo apt install build-essential
```

## 使い方
下記のMakefileの雛形をCLIを実行するルートディレクトに作成します。
ファイル名は拡張子無しのMakefileです。

Makefileに記載したコマンドをmake {コマンド名}で実行できます。
make と打った後にTab補完もできます。
下記の雛形はmakeとコマンドを打つとデフォルトでhelpが実行され、各コマンドのリストと説明を表示するようにしています。
makeは実行するタスク名と同名のファイルが存在すると実行できません。
それを回避するために.PHONYを記載しています。

- Makefileの雛形
```make
.PHONY: clean　start-ec2-qa
.DEFAULT_GOAL := help

#####################
# 環境変数
#####################
profile-qa := gaia-qa
EC2-Instance-QA := i-xxxxxxxxxxxxxx

start-ec2-qa: ## EC2を起動させるサンプルコマンド
    aws ec2 start-instances --instance-id ${EC2-Instance-QA} --profile ${profile-qa}

clean: ## sample
	rm -rf ./bin

help:
    @grep -E '^[0-9a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | \
        awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}'
```
