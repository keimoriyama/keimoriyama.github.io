+++
title = "AxBench: Steering LLMs? Even Simple Baselines Outperform Sparse Autoencoders"
author = ["keimoriyama"]
description = "description"
date = 2025-11-22T00:00:00+09:00
tags = ["paper"]
categories = ["paper"]
draft = false
+++

## 📄論文情報 {#論文情報}

-   [AxBench: Steering LLMs? Even Simple Baselines Outperform Sparse Autoencoders](https://openreview.net/forum?id=K2CckZjNy0)
-   ICML 2025


## 🔑この論文のキーメッセージ {#この論文のキーメッセージ}

-   （1, 2文でまとめる）


## 🎓どういう問題に取り組んだのか {#どういう問題に取り組んだのか}

-   LLMの内部表現に介入する手法の評価をするためのベンチマークデータセットを構築した


## 🧑‍🎓その問題に取り組むことがなぜ重要なのか {#その問題に取り組むことがなぜ重要なのか}

-   LLMの内部表現に介入する様々な手法が提案されている。
-   だが、統一したベンチマークが存在しないため公平な評価ができていないという課題がある。


## 💡問題解決に向けたキーアイデアは何か {#問題解決に向けたキーアイデアは何か}

-   Concept DetectionとModel Steeringの二つの指標を評価するためのデータセットを構築した
    -   Concept Detectionはシンプルな分類問題
    -   Model Steeringは、生成した文章をLLMが評価するものになる
-   データの用意のために、GPT-4oを使用したデータ拡張が行なわれている
-   Concept Dataset Generation
    -   データセットの形式はPreferenceデータセットと同じ形式になっている
    -   指示とポジティブなデータはLLMにより生成されている
    -   ネガティブなデータには、異なるコンセプトに属するレスポンスを使用している
    -   タスクの評価指標には、特定のレイヤーの各トークンの中間表現を用いて分類器が予測した確率の最大値を用いている
        -   分類器の予測は[0-1]の一次元の出力になる
-   Model Steering
    -   評価指標
        -   LLMが応答を0、1、2のいずれかで評価する
        -   スコアは、Concept、Instructoin、Fluencyの3つを使用する
        -   最終スコアは、調和平均を使用している
-   論文中で報告されているのは、特定のレイヤーにおけるスコアになっている
    -   Model Steeringでは特定のレイヤーに介入した時のスコアになっている


## 👀新たに分かったことは何か {#新たに分かったことは何か}

-   Concept DetectionではProbeベースの手法が、SAEを使用する手法よりも良い性能であった
    -   評価指標は、AUROCを用いている
    -   特に、SAEはデータのバランスが悪いと性能が低下する傾向がある
-   Model Steeringにおいては、SAEの方が良い性能であるがLoRAやSFTよりも性能が低い結果であった


## ❓疑問点は何か {#疑問点は何か}

-   Model Steeringのスコアにおいて、定量的なものが採用されていないのが気になる
    -   LLMによる評価だけで良いのかはとても疑問
-   Gemma以外のモデルの性能はどうなのだろう
