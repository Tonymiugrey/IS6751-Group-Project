# IS6751-Group-Project

## 环境
```sh
conda env create -f environment.yml
```
## 目录结构
```sh
├─cnn # 跑CNN用的
├─data # 各种数据
│  ├─glove # 见下文
│  ├─original # 原数据集
│  └─processed # 处理后数据集
├─data_preparation # 处理数据集用的，处理完的csv在data/processed里
├─fasttext # 跑FastText用的
├─lstm # 跑LSTM用的
├─model_storage # 存模型的
│  ├─Fake_News
│  └─News_Category
└─sample-groupprojects # 老师给的sample
```
### glove是一个已经训练好的词向量，因为太大传不上来，需要自行去老师的wk8-lab\5_3_doc_classification\data\glove里面拷过来!!

## 自动调参 (credit. 唐开元)
反正大家都忙，调参这种费时间的事情让它自动搜就好了

在Grid Search那格

在前面设定好每个参数的搜索范围后直接跑就行，可能会跑很久就是了，可以一边跑一边做别的事情

跑完之后会在notebook文件同目录下建一个日志txt，看看最后面best test acc的参数是哪些，直接填到后面args里面，然后最后正式跑一遍就可以了

### eg. FastText

#### 搜索结果：
```py
--------------Best Test Acc--------------
embedding_dim: 100
hidden_dim: 128
output_dim: 4
output_dim: True
is_pretrained_embeddings: False
emb_freeze: 128
batch_size: 0.36116317385121394
```
#### 参数：
```py
args.embedding_dim=100
args.hidden_dim=128
args.output_dim=4
args.use_glove=True
args.emb_freeze=False
args.batch_size=128
```

## 一些别的东西
1. 文本预处理代码在第五格（The Dataset下面），有时间的话可以试试改n-gram和词数限制
2. 如果对数据集处理的代码有改动的话，记得在群里说声

## 报告
### 1. Intro
- 背景
- 目标 
- 文献综述 **（要吗）**
### 2. Data Processing - SHY
- 数据集介绍
- 预处理
### 3. Methods
- CNN - CPY
    - 模型
    - 参数（CNN里面dropout用了0.2和0.5，是从别的地方看来的，来源我之后找一下）
    - 训练过程（搜超参等）
- LSTM - YKY
- FastText - SHY
### 4. Results & Findings（可以等最后跑完了加上，各写各的）
- 模型结果
- 发现
#### 可能可以讨论的东西
- 不同模型在2分类和多分类上的表现
- 不同模型对长文本/短文本的学习能力
- FastText性能开销小，新闻类别分类只要半min+0.8G就能和CNN训1min多+2.6G达到差不多水平（LSTM待补）（这点待定，因为测试的时候预处理不一样）
### 5. Conclusion
### 6. Limitations（要吗）

