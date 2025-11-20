+++
title = "SAEs Are Good for Steering - If You Select the Right Features"
author = ["keimoriyama"]
description = "description"
date = 2025-11-18T00:00:00+09:00
tags = ["paper"]
categories = ["paper"]
draft = false
+++

## 📄論文情報 {#論文情報}

-   [SAEs Are Good for Steering – If You Select the Right Features](https://aclanthology.org/2025.emnlp-main.519/)
-   EMNLP 2025 main
-


## 🔑この論文のキーメッセージ {#この論文のキーメッセージ}

-   （1, 2文でまとめる）


## 🎓どういう問題に取り組んだのか {#どういう問題に取り組んだのか}

-   SAEを用いた特徴量選択において、入力と出力の特徴量のそれぞれに影響がある特徴量を見つけること


## 🧑‍🎓その問題に取り組むことがなぜ重要なのか {#その問題に取り組むことがなぜ重要なのか}

-   Sparse AutoEncoder(SAE)は介入するための特徴量を選択する時に有効な手法である
-   だが、介入のために有効な特徴を選択することはまだ未知の問題である


## 💡問題解決に向けたキーアイデアは何か {#問題解決に向けたキーアイデアは何か}

-   特徴量を以下の二種類に分類し、分類するための指標を提案した
    -   Input features：モデルに入力されたパターンを認識する特徴量
    -   Output features：モデルが生成するトークンに影響する特徴量
-   これらの分析には、Logit Lensが使用されている
    -   Logit Lengsはモデルのパラメータを語彙空間に射影し、その出力分布を見てパラメータを分析する方法のこと
-   Input featuresのスコアの計算には、任意の文章集合を用いる
    -   この文章集合において最も大きくSAEのトークンを発火させたトークンと、Logit Lensにより予測されたトークンの一致率をスコアとしている
-   Output Featuresのスコアの計算にはLogit Lensにより予測されたトークンのスコアと順位、確率を使用する
    -   その特徴量に介入を行った時のモデルの出力分布と介入をする前の分布の差をスコアとしている
    -   Logit Lensによる予測結果を用いて介入する前の出力分布を計算しているが、よく分からなかった


## 👀新たに分かったことは何か {#新たに分かったことは何か}

-   上記のスコアをGemmaやLlamaに適用した所、Gemmaにおいては入力に近い層ではInput features、出力に近い層ではOutput Featuresのスコアが大きくなっていた。
    -   それ以外のモデルにおいては、この傾向は当てはまっていない
-   Output featuresが高いパラメータに介入することによる出力文章の変化を計算した
    -   実験では、スコアに閾値を用意し介入する特徴量を選択している
    -   評価には、Generation Success@Kを使用している。
    -   Logit Lensにより予測されたTop-kのトークンと文章に含まれるトークンの一致率を計算している。
-   閾値を上げると、Generation Success@Kが上昇することが分かった


## ❓疑問点は何か {#疑問点は何か}

-   スコアの計算結果で、きれいな結果が出ているのがGemmaだけなのが気になる
    -   介入の結果は同様の傾向を示している
-   結局Output featuresが高いものが良い特徴であるのか？
-   介入の方法が良く分からなかった
    -   方向を決める方法が知りたい
