# Condensed Memory Networks for CLincal Diagnostic Inferencing

## Abstract
* Wikipedia をknowledge source として利用する。
* Condensed memory neural networks を用いた、diagnoses のprediction を行った。

ざっと読んだ感じでは、wikipedia を用いたMemory networkの構成に重きを置いていて、textからのfeatureにはbowだけを用いており、textに寄り添った方法と言えないのでは。

## Introduction
* EHRにまつわる歴史をざっと紹介。
* "Our goal is to combine such an external clinical knowledge source with the free-text clinical notes and use the learning capability of memory networks to correctly infer the most probable di- agnosis."

* Memory network の紹介。memory network はinput source とknowledge source を何度かinput し、その都度内部状態を更新する。

* Memory Network はQAにも用いられる。

* memory が巨大である一方で、hashingも用いられる。hashingは、選択的に、関連する情報のみを抽出するために用いられるが、記憶された情報の状態を改善することに、先行研究ではこれまで重きは置かれていなかった。

* Condensed MN の紹介。より効率的な状態で、記憶の分散状態を保有することがCondensed MN の売りである。

* 本手法では、LSTMによるマルチラベルdiagnoses problem ではなくMN を用いたラベル割りあてを行なう。

###一旦保留　この論文はmemory network の更新がメインであるので。
### メインのFigure 2 も正直、これだけではよくわからない。
