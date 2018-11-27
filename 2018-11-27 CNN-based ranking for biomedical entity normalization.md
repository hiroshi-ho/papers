# CNN based ranking for biomedical entity normalizaiton
* baselineになりうる？この文献を引用している文献を更に調査
* corpus はword2vec, unannotated PubMedでtrain
* ShaRE2013についてはSNOMED-CT,NCBIについてはMESH&OMIM をKBとして、それを当てに行く。つまりentity linkingが広義のタスク
* CNN でsemantic information と候補先のembeddingのsimilalityを全てCNNで取ってsoftmax?
* コード git-clone 済
