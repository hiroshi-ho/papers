# Show and Tell : A neural Image Caption generator

## Abstract
* deep RNN ベースのキャプション生成で恐らく一番有名な論文

* given : training image, output : caption として、MLE ベースでモデルをtrain する。

* 評価使用はBLEU,当時でSOTA

* train データにはPascal dataset とFlicker 30 を使用。

## 1. Introduction
* 当時の文脈ではimage to caption はいくつかのsubproblemに分割して、それを組み合わせる手法が主だった。

* このモデルでは、input を$I$ : image, output を *word* の集合　$S = \{S_1,S_2,...\}$ とする問題として定式化し、各文章 $S_t$ を構成するword は与えられた辞書から取ってくる。


* hint はMT（machine translation）から来ている。　MT の場合は, $T$ : target , $S$ : source として、　確率　$p(T|
  S)$ を最大化する問題として捉える。

* 当時はまだ、機械翻訳でRNNを用いる手法は出始めた頃？RNNでSOTAが達成できてしまうと記述がある。

* 本論文では、MTでいうencoderの部分を、CNNに置き換える。
* CNN を、Image representation を得るencoder として考えpretrainし、CNNで得た特徴量をRNN に突っ込む。手法の概略は以下である。
  * 問題に対するend-to-endモデルを提案する。modelはSGDベースのneural networkである。
  * SoTAであるvision and language model を提案する。
  * 今までのSoTAと比較して更に良いパフォーマンス

## 2. Related work
* これまでの問題設定は大半がranking problemへの落とし込み[11,8,24]
* ranking問題へ落とし込む場合、image embedding及びtext embedding のco-embeddingベースが普通
* この時代のNNでは、image retrieval やsubsentenceの取得にNNは使われて履いたものの、新しい文章生成までは成されていなかった。

* Kiros[15],Mao[21]らと似ている部分が多いが、重要な違いを以下に記述する。
  * visual input を直にRNN にinput として与える。
  * SoTA of established benchmarks
  * Kirosらの場合は、joint embedding を使用。つまり、image と textでそれぞれtrain path を用意していた、本手法ではCNN to RNN と一本道である。

## 3. model
* MT をhintに: 可変長の文章を、固定次元のベクトルに落とし込む際にRNNが使われる。その後、このrepresentation を、outputとなる文章へとdecodeする。

* アナロジーはMTである。つまり、今回の場合は、imageを与えられたら、固定長のvectorを得た後、RNNに導入しsentenceをgenerate する。

$$\theta^{★} = \mathrm{argmax}_{\theta} \sum_{(I,S)} \mathrm{log} p(S|I;\theta) \tag{1}$$

ここで\theta はモデルのパラメータである。また文章の長さ $S$ は決められていない。よって、、ある特定の文章長を $N$として

$$\mathrm{log} p(S|I) = \sum_{t=0}^{N} \mathrm{log} p(S_t| I, S_0,...S_{t-1}) \tag{2}$$

が、画像からある長さ$N$ の文章を得る確率となる。

* 結局のところ、encoder にCNN, decoder にRNNを用いたモデルとして、最初のモデルであるというのが、重要である。

* 隠れベクトルのinitに、CNNでencodeしたimage vectorを用いる。

### Inference
 * SamplingとBeam Searchの2つを述べている。この論文ではBeam searchを用いる。

## 4. Experiments
* metricsにはbleu,meteor,ciderを使用。
* dataset にはPascal, Flicker, MSCOCOを主に使用

議論としてGeneration Diversity, Ranking results, Human Evaluation の3つを報告している。

## Conclusion
結局のところ、最初にCNN+LSTMベースのcaption generatorを作り、実験したというのが重要だと思う。
