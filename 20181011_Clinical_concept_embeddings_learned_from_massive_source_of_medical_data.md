# Clinical concept embeddigs learned from massive sources of multimodal medical Datasets

## Abstract

* large clinical notes, biomedical journal などを用いた　pretrained embeddings for clinical concept の獲得

## 1 Introduction
* Word2vec 含めて　embeddig は　transfer learninig ,つまり、ラベルなし大量テキストを用いて通常は初期　embedding を獲得する。そして、そのembeddingが何らかの教師あり学習に用いられる。

* transfer learning は画像にも有用である[19]

* privacy concern などの事情があり、大量のunlabeledな,medical domain のテキストを得ることは難しい

* cui2vec: comprehensive set of embeddigs for medical concept の提供

## 2 Overview of word2vec and GloVe

word2vec, GloVe  の簡潔なまとめがなされている。

Embeddigの作り方と用意の仕方、ベンチマーク評価について書かれているが、ここでは省略する。
