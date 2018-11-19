# ENhancing Automatic ICD-9-CM Code Assignment for medical texts with Pubmed

## Abstruct
* 既存のICD-9 autoclassifier は、dataのimbalanceに起因する問題に直面している。
* 低頻度出現のICD-9 が、重要ではないかというと、そんなことはない。
* 特に低頻度のICD-9 がに対処するために、戦略的にPubMedからデータを引いてくる。
* CMC dataset を用いた、ICD割当のパフォーマンスの改善が見られた。

## 1 Introduction and background
* 既存のICD auto classifier における研究をざっと紹介
* この論文では、ICD-9-CM code に焦点を置く。ただ、本研究はICD-10-CMにも適用可能である。
* SoTA手法と比べるために、本論文ではICD-9を選択した。
* ICD-9-CM codes are organized hierarchically, and each code corresponds to a textual description, such as "786.2, cough".

* 既存の研究はmicro--average measure を用いたものが多く、unbalanced なtrain data が及ぼしうる影響について、隠してしまっている。

* 主な第一のモチベーションは上記の、imbalanced data と、その　imbalanceness がclassifier に及ぼしうる影響の調査である。

* 実際の手に入れることが可能なデータは大変、ICD-9-CM distributuion が偏っているという問題がある。

* ICD-9 Data のimbalancenessについて分析した先行研究の紹介。例えばcommon disease であるcough が266個　train data に含まれるのに対して、train data 全体で一回しか出現しないICD-9-CM codeも存在する。

* imnalanced なデータについて、PubMedから情報をretrieve することで対処することを提案する。

## 2 Related work
* 既存研究がルールベース及び、教師あり学習の問題下でICD-9 code割当問題を解いていることについて。
* 教師あり機械学習の先行研究でも、imbalanced train data が精度に強く影響していることの指摘。
* 本論文では、データのimbalancenessに対処することをここでも主張。

## 3 Methods
### 3.1 Datasets
* 提案手法のvalidate には、2007 computational medicine challengge(CMC  datasets) を使用する。

### 3.2 Method I retrieval problemへの定式化
* クエリをICD-9-CMコードの説明部分、ドキュメントの集合が、PubMed Dataset内の文書集合　であると考えれば、情報retrieval 問題になる。
* Pubmedに投げるクエリには、適当なcleanup preprocessing を走らせる。（論文参照）

### 3.3 retrieval pubmed articles with both official and synonyms icd-9-cm code description
* 結局のところ、ICD コードとPubmed datasetは別々の人が別々の目的で書いているので、ICDとPubmedの間でterm mis-match problem が生じることがある。

* 普通のpubmed searchに加えて　synonyms of the description をクエリとした探索も行なう。


## 4 Experiments
* 評価指標はmicro-f1
* 前処理についての詳細な記述。
* ベースラインはLR 及びSVM
* Deep は使っていない
