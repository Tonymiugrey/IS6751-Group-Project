# IS6751-Group-Project

## 目录结构
```py
├─cnn # 跑CNN用的
├─data # 各种数据
│  ├─glove # 给CNN用的，见下文
│  ├─original # 原数据集
│  └─processed # 处理后数据集
├─data_preparation # 处理数据集用的，处理完的csv在data/processed里
├─lstm # 跑LSTM用的，还没弄
├─model_storage # 存模型的
│  ├─Fake_News
│  └─News_Category
└─sample-groupprojects # 老师给的sample
```
### glove需要自行去老师的wk8-lab\5_3_doc_classification\data\glove里面拷过来!!

## 目前问题 （2023.10.25）
做了cnn的，发现几个问题
1. **切到1000词后acc不变，91.4，但显存占用1.7G，nice** ~~fake news合起来之后文本长度太长，很吃显存（5.8GB），cpy的电脑hold不住（4GB）（lstm估计也差不多，还没试）；我这边简单跑了一下，cnn的acc是91.4，没细调；可以考虑切一下，或者按yhj说的只留标题也行~~ 
2. **换了数据集，CNN acc 88+** ~~新闻分类的类别太多（42个），感觉结果有点emmm（acc只有49多）；由于类别很多，必须也要有很大的数据集支撑才能让结果OK一些；数据集里有20w多条，预处理时间超过10分钟，感觉这个效率对后面调参很不友好；如果在现有数据集上再删会导致结果更加难看，so考虑换数据集，或我们把差不多的类别合并一下？~~
3. FastText**正在做** ~~要做ngram，对长文本不友好，回到第一个问题~~

## 一些别的东西
1. 文本预处理代码在第五格（The Dataset）下面，目前没做n-gram，注释掉了
2. 如果对数据集处理的代码有改动的话，记得在群里说声
3. 之后可能可以在报告里讨论的东西：不同模型在2分类和多分类上的表现；不同模型对长文本/短文本的学习能力
4. CNN用到了一个叫glove的预训练词向量，或许可以试试不使用它？