+++
title = "Faithful Bi-Directional Model Steering via Distribution Matching and Distributed Interchange Interventions"
author = ["keimoriyama"]
description = "description"
date = 2026-04-17T00:00:00+09:00
tags = ["paper"]
categories = ["paper"]
draft = false
+++

## 📄論文情報 {#論文情報}

-   [Faithful Bi-Directional Model Steering via Distribution Matching and Distributed Interchange Interventions](https://openreview.net/forum?id=LoisXFZL3k)
-   ICLR 2026
-


## 🔑この論文のキーメッセージ {#この論文のキーメッセージ}

-   情報量を目的関数として使用することで、介入の結果と生成される文章の分布のマッチングを考慮した学習ができる


## 🎓どういう問題に取り組んだのか {#どういう問題に取り組んだのか}

-   勾配法を用いてLLMの内部表現に介入するベクトルを学習するための新しい目的関数を提案した
-   介入するベクトルにはコンセプトという情報を持たせる必要がある


## 🧑‍🎓その問題に取り組むことがなぜ重要なのか {#その問題に取り組むことがなぜ重要なのか}

-   勾配法を使用して介入ベクトルを学習する手法は、過学習や性能低下の問題があるため？
-   学習したいのは、ある入力に対して適切に介入ベクトルを計算するためのモデル
    -   このモデルをコンセプトベクトルと言っているのか？


## 💡問題解決に向けたキーアイデアは何か {#問題解決に向けたキーアイデアは何か}

-   情報量ベースの目的関数を提案して学習する
-   学習に使用するデータはコンセプトを保持している入力と応答のペアと保持していないペアから構成される
-   これらのトークン列に対すJS Divergenceを最小にするように学習を行う
    -   計算においては、入力を入れ変えてかつ介入を行う時の分布と、基のペアの分布との間で計算されている


## 👀新たに分かったことは何か {#新たに分かったことは何か}

-   評価にはAxBenchのConcept500を使用している
-   2Bのモデルの性能は既存手法よりも低い結果であるが、介入する場所毎のスコアの差が小さくなっている
    -   介入する場所に依存しない手法になっていると言える


## ❓疑問点は何か {#疑問点は何か}
