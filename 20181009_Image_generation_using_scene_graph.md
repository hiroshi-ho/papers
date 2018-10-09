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

計算式は、あまり出てこないので読みやすいと言える。

## 1.Introduction
 Richard Feynman の有名なことわざから始まるIntroduction で、洒落ている。

 * visual なものに深い理解を与えることの他院、現実的な画像の生成もまた、実用上有用である。

 * 最近の潮流について、追う必要がある、この点この文献はありがたい。[41,42,53,59]

 * しかし、依然として、複雑な文からの画像生成には困難が伴っているのが現状である。

 * 文章は、linear structure を持つものである。つまり、一つのwordに対して、別の言語が続いている。これを画像を比較する。

 * しかし、画像については、scene graph を用いてより明確に関係を明示することが可能である。

 * 今回の生成に限らず、scene graphの有用な例について、先行文献を数多く紹介している。

 * 文章をscene graphへと変換する手法[47],画像からscene grraph を予測する手法などが先行ぶん研究に存在する。

 * この論文では今流行り？のgraph convolution networkを使っている。

 * graphを二次元画像のアウトプットへと変換するためには、scene layout を用いたbounding boxとsegmentation maskの予測を用いている。

 * [6] Cascade refinement network (CRN) を用いている。


* 最後に、よりrealistic な画像生成のために敵対的生成を用いている。

### Datasets
 Visual Genome と、　COCO stuffの2つを用いている。


### evaluation
 生成された画像を評価することもまた困難の一つである。
 StackGAN[59] と比較して、recognizableなobjectがどれくらい生成画像内に存在しているかを評価の指標としている。

## 2. Related network
### Generative Image models
画像生成は、更に3つのカテゴリに分けられる。

* Generative Adversarial Networks
* Variational Autoencoders
* autoregressive approaches

### Conditional Image Synthesis
* ? 条件場下での画像生成は、追加のインプットについて条件付けを行う。
* GAN は、generator及びdiscriminatorに対して、追加のインプットとしてカテゴリラベルを提供することで、条件付けが成される。

* または、discriminatorに無理やり、ラベルの予測を強いることでも、GANは条件付けが成される。

* 今回の手法では、後者を用いる。

* Reed, Zhang らの、GANを用いた画像生成の先行文献。

### Scene graph
Visual Genome に詳しく書いてある。

### Deep Learning on Graphs
* 単graphからembeddingを得る手法についても、先行研究はいくつか存在し、その手法はword2vecと似ている。

* これらのアプローチは、今回のものとは異なる。なぜなら、我々は新しいグラフを生成しなくてはならないからである。

* GNN の先行文献について、これでもかというほど書いてあるので、要チェック。

## 3 Method

　克服しなくてはいけない点が3つ存在する。
* まず、graphの形をしたinputに、inputを整えてあげないといけない

* inputのgraphを尊重しなくてはいけない。つまり、inputに与えるobject,object 間の関係を尊重しなくては行けない。

* 合成された画像は、現実的でなくてはならない。

figure 2 で示されているような画像生成ネットワークを用いる。　ここでは $f$ をそのネットワークとして表記する。

詳しくはfig 2を見ること。

最終的なoutput image はcascade refinement network (CRN)[6] を用いて生成されるので、[6]の文献を見ておく必要がある。

fig2 について、訳しておく必要があるでしょう。

* Input は scene graphであって、自然言語文でないことに注意する。

* input のグラフについては、graph convolution network (fig3)を用いた処理が成される。

* GCNが伝える情報は、全てのobject  のembedding vectorを計算するエッジに沿った情報である。

* layout はCRN を用いた変換が成される。

* train時はbounding box とsegmentation maskを覗いても良い。テスト時には隠す。

### Scene graph (to embedding)
　言語モデルの場合と近く、Scene graph もまた、エッジを用いてembedding を獲得することが可能である。

### Graph convolutional network
　結局のところ、end-to-end での画像生成が必要なので、NNの力を借りる必要がある。
