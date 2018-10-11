# Towards Diverse and Natural Image Descriptions via a Conditional GAN

## Abstract

* 凄まじい進歩にも関わらず、imape caption の生成はまた完全には程遠い。

* RNN-basedなcaption generation については、trainによって、ground-truth と高い類似性を持つキャプション生成が得意になる一方で、他の似たdescriptionの生成を抑えてしまうという欠点がある。

* この論文では、キャプション表現のnaturalness と diversity を向上させることを目的とする。

* Conditinal GAN に基づく新しいフレームワークを提唱する。

## 1 Introduction

* 直近のcaption generator をベースにした生成キャプションのダメ出しから入る。

* *has the problem
of generating image descriptions been solved?*

* Figure 1 を例に、sota caption generator[29]を紹介。rigid,lacking in vitality.

* これまでのcaption は、fidelity すなわち、画像に対する事実の尤もらしさに注力してきた.LSTM[8]らがその良い例

* 結局、既存のtrain では、train データ内n-gramにきわめて似たキャプションの生成に終止してしまう。

* 既存の評価指標についても、ダメ出しを行っている、BLEU,METEOR,ROUGE,CIDErらは既存のキャプションが生成する、 *safe* な文章に対してスコアをつける傾向にある。

* 極めて単純なことで、人間が生み出すキャプションが、これらの評価指標の前では低いスコアになってしまうという事実そのものが、これらの評価基準の脆弱性を露呈していることになる。

この流れを受けて、本論文では、　*FIdelity, Naturalness,Diversity* の3つを新しい評価基準として提唱している。

かつ、新しいフレームワークとして、conditional GAN を提唱している。
理由として
 * 自然言語の生成は、*sequential sampling* 手続きであり、
 * サンプルは各手続きにおいて *discrete* なサンプルであって、　
 * *non-differentiable*

であるから、と述べている。

これらの問題について、強化学習戦略の一つであるPolicy gradient を用いた解決を試みる。

Introのまとめとして、本論文の寄与を3点にまとめている。

* naturalness まで加味したcaption生成手法の提示
* MLEではなくconditional GAN を用いた
* 人間の評価に近いevaluatorの実現

## 2 Related Work
 Figure.3 に出てくるようなダメ出し。Evaluationの方法や、似た文の似たn-gramに対して、類似系列を吐き出してしまう問題について。

### Our Alternative Way
 * 何度も強調しているように、これまでのtrain sampleの問題点は　resemblance にともきを置いていることであった。つまり、 *safe* ではあるが *limited* な文章ばかりが生成されてしまっていた。
 * 本論文では、その代替手法として、conditional-GAN を用いる。


## 3.Framework
手法 \
  $G$: generator \
  $E$: evaluator\
  $I$: image \
  とした場合に、generatorは、より　*natural* かつ　*semantically  relevant* な説明文生成を行い、 evaluatorは、その文章がどれだけよく画像の説明を成しているかの評価を行う。

* single sentence をまず実験し、次にparagraph generation を行う。

### 3.1 overall Formulation
 * given : $I$ (image)
  この時、$G$は2つのインプット



## 次に見るべき論文
[29],[22],[7]
22: conditional GAN
7 : GAN
34 : GAN for text generation
