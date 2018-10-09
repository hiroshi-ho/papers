# Image Generation from Scene Graphs
## submitted 4, 2018
## 被引用数 6

## Abstract
* 自然言語からの画像生成はexcitingですよね
* bird , flowerのdomain では成功しているが、それ以外のdomainでの画像生成は以前としてchallenging である。

* この困難、つまり、domain limitationを克服しより多様な画像を自然言語から生成する方法として、scene-graph からの画像生成が考えられる。

* 本論文でじゃ、グラフ畳み込みを用いてinput graph を処理。

* 更に、情景のレイアウト、つまり構成については、objectのバウンディングボックスとsegmentation mask を予測することで計算した。

* 最後に、カスケード型のrefinement networkを用いて レイアウトを画像に変換する。

* networkは、現実的な出力を保証するために、敵対的生成を用いる。

* 本論文の手法を用いた、複雑な画像の生成について検証する。

* Visual Genome やCOCO-Stuffを用いた我々の提案手法について、検討する。

## 1.Introduction
 Richard Feynman の有名なことわざから始まるIntroduction で、洒落ている。

 * visual なものに深い理解を与えることの他院、現実的な画像の生成もまた、実用上有用である。

 * 最近の潮流について、追う必要がある、この点この文献はありがたい。[41,42,53,59]

 * しかし、依然として、複雑な文からの画像生成には困難が伴っているのが現状である。

 * 文章は、linear structure を持つものである。つまり、一つのwordに対して、別の言語が続いている。これを画像を比較する。

 * 画像については、

 ## 今後読むべき論文
 [59] [59] H. Zhang, T. Xu, H. Li, S. Zhang, X. Huang, X. Wang, and D. Metaxas. Stackgan: Text to photo-realistic image synthe- sis with stacked generative adversarial networks. In ICCV, 2017
