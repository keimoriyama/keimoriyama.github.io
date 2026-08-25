+++
title = "Tool Calling for Arabic LLMs: Data Strategies and Instruction Tuning"
author = ["keimoriyama"]
date = 2026-08-25T00:00:00+09:00
tags = ["paper"]
categories = ["paper"]
draft = false
+++

## 📄論文情報 {#論文情報}

-   [Tool Calling for Arabic LLMs: Data Strategies and Instruction Tuning](https://aclanthology.org/2025.arabicnlp-main.28/)
-   ArabicNLP main


## 🔑この論文のキーメッセージ {#この論文のキーメッセージ}

-   言語間でツール呼び出しは転移するが、その言語のツール呼び出しデータを用意することで更なる性能向上が期待できる


## 🎓どういう問題に取り組んだのか {#どういう問題に取り組んだのか}

-   英語以外の言語におけるTool Callingデータセットの必要条件を分析すること


## 🧑‍🎓その問題に取り組むことがなぜ重要なのか {#その問題に取り組むことがなぜ重要なのか}

-   既存のTool Callingデータセットは英語がメインの言語である
-   アラビア語のTool CallをLLMに学習する上で、英語のデータだけで学習するのが良いのか、翻訳データも必要なのかなどの条件を分析する必要がある


## 💡問題解決に向けたキーアイデアは何か {#問題解決に向けたキーアイデアは何か}

-   Gemimiを使って、英語のデータセットを翻訳し、英語とアラビア語のTool Callを評価した
-   評価項目としては、Tool Callに対するrecallとprecisionを使用している
    -   正確なツールが選択できているのかを評価している
-   加えて、Tool Callが完全に正しい割合で評価している


## 👀新たに分かったことは何か {#新たに分かったことは何か}

-   言語間のTool Callingは転移するが、引数の生成には言語依存性がある
    -   英語だけのデータで学習してもアラビア語のRecallは英語ベンチマークと同じスコアであった
-   適切なtool callingをする（Toolを呼ぶなどの判断など）ためには、その言語のデータが必要になる
    -   アラビア語のデータを混ぜることで、アラビア語ベンチマークにおけるrecallが向上する
-   翻訳データにおいて重要になるのは、Toolの種類になる
    -   OODにどれくらい適応するか？という話になるのか？


## ❓疑問点は何か {#疑問点は何か}
