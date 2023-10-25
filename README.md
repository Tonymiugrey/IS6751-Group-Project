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

## 准备加的东西
1. 网格搜索超参

## 可能可以在报告里讨论的东西
1. 不同模型在2分类和多分类上的表现
2. 不同模型对长文本/短文本的学习能力
3. FastText性能开销小，只要半min+0.8G就能和CNN训1min多+2.6G达到差不多水平（LSTM待补）

## 一些别的东西
1. 文本预处理代码在第五格（The Dataset下面），目前没做n-gram，注释掉了
2. 如果对数据集处理的代码有改动的话，记得在群里说声
3. CNN用到了一个叫glove的预训练词向量，或许可以试试不使用它？在args里面改；
    ```py
    use_glove=True,  # True 改 False
    ```
    或者继续训练它 (在模型的那格)
    ```py
    self.emb = nn.Embedding.from_pretrained(pretrained_embeddings, freeze=True)  # True 改 False
    ```