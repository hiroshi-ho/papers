# BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

* これまでのrepresentation model と異なり、全ての層でright, left の両側のコンテクストを加味する。
* 結果、BERTでpre-trainされたrepresentation は、一つoutput層を加えるだけで、これまでのタスクに対してSOTAを達成可能。

* *conceptually simple, empirically powerful*

## 1 Introduction
* feature-based approachとfinee-tuning approach
* ELMoはfeature-based approachであり、*
uses tasks-specific architectures that
include the pre-trained representations as addi-tional features.*

* fine-tuning approachの代表例はtransformer であり、タスクに対してpretrained parameters をfine-tuning する。

## 次に読むべき論文
Transformer \
ELMo
