---
title: "クロスアカウントにおけるkinesis streamへのデータ投入"
date: 2025-02-15
draft: false
description: "別テナントにあるkinesis Streamにデータを送信する設定方法"
tags: ["kinesis", "AWS", "クロスアカウント"]
---

Lambdaを使用して別テナントにあるkinesis streamにデータを挿入する方法の記事が無かったのでメモ。

# 方法
Kinesis Stream設定の共有ストリームのポリシー設定にて、許可するロール/ユーザーを追加。

