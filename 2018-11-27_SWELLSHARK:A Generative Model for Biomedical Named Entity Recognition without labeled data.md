# SwellShark: A Generative Model for Biomedical Named Entity Recognition without Labeled Data

* 弱教師ありNERでcompetitive scoreをbiomedical domain でのNERで達成。
* recognition タスクのみで、normalization には触れない。"We focus on the recognition part of
named entity extraction and do not address normalization."
* toolとして、applicationとしてつくった意義は大きいが、研究でこれを用いれるかというと。。。
* NCBI disease coorpus, BioCreative CDR corpus, i2b2 2009 Medication Extraction Challenge でそれぞれtrainとtestを分けて、弱教師NER
* BioASQ 2015(Tsatsaronis et al) がPubMedも同梱してデータセットを配っているらしい
* Stanford CoreNLPによるpreprocessing
* LSTM-CRF が使用モデル
