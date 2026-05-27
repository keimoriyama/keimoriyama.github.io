+++
title = "Personalized Steering of Large Language Models: Versatile Steering Vectors Through Bi-directional Preference Optimization"
author = ["keimoriyama"]
description = "description"
date = 2026-04-23T00:00:00+09:00
tags = ["paper"]
categories = ["paper"]
draft = false
+++

## 📄論文情報 {#論文情報}

-   [Personalized Steering of Large Language Models: Versatile Steering Vectors Through Bi-directional Preference Optimization](https://arxiv.org/abs/2406.00045)
-   NeurIPS 2026


## 🔑この論文のキーメッセージ {#この論文のキーメッセージ}

-   （1, 2文でまとめる）


## 🎓どういう問題に取り組んだのか {#どういう問題に取り組んだのか}

-   LLMの内部表現に介入する良いベクトルを学習にすること


## 🧑‍🎓その問題に取り組むことがなぜ重要なのか {#その問題に取り組むことがなぜ重要なのか}

-   既存の内部表現に介入する手法は、出力のトークンとの関係を考慮しきれていないため


## 💡問題解決に向けたキーアイデアは何か {#問題解決に向けたキーアイデアは何か}

-   DPOと類似した報酬モデル損失関数を提案する
    -   この損失において、参照モデルは介入前のモデル、学習するモデルは介入後のモデルとして介入ベクトルを学習する
-   学習においては、正例と負例の報酬値の差が大きくなるように学習を進める


## 👀新たに分かったことは何か {#新たに分かったことは何か}

-   ペルソナを考慮したタスクやTruthfulnessなどのタスクを対象として評価した
-   学習した介入ベクトルを用いて正の方向に介入するとスコアが良くなり、負の方向にするとスコアが低下した
    -   既存手法よりもスコアが大きく変化しているので、良いベクトルが学習できていると言える
-   また、アンサンブルしても上手く動作することが分かった
