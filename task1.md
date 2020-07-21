任务：新闻文本的多分类任务，就是对不同的新闻分不同的类别，候选类别有：财经、彩票、房产、股票、家居、教育、科技、社会、时尚、时政、体育、星座、游戏、娱乐的文本数据。
学习目标：
1、理解赛题背景与赛题数据
2、完成赛题报名和数据下载，理解赛题的解题思路

评测指标：评价标准为类别f1_score的均值

解题思路：官方给到了4个。
赛题思路分析：赛题本质是一个文本分类问题，需要根据每句的字符进行分类。但赛题给出的数据是匿名化的，不能直接使用中文分词等操作，这个是赛题的难点。
因此本次赛题的难点是需要对匿名字符进行建模，进而完成文本分类的过程。由于文本数据是一种典型的非结构化数据，因此可能涉及到特征提取和分类模型两个部分。

思路1：TF-IDF + 机器学习分类器
直接使用TF-IDF对文本提取特征，并使用分类器进行分类。在分类器的选择上，可以使用SVM、LR、或者XGBoost。

思路2：FastText
FastText是入门款的词向量，利用Facebook提供的FastText工具，可以快速构建出分类器。

思路3：WordVec + 深度学习分类器
WordVec是进阶款的词向量，并通过构建深度学习分类完成分类。深度学习分类的网络结构可以选择TextCNN、TextRNN或者BiLSTM。

思路4：Bert词向量
Bert是高配款的词向量，具有强大的建模学习能力。

配套的第一个思路有Baseline还没有来得及看，先根据四个思路，整理下接下来需要学习的知识点。

-------


TF-IDF文本提取特征：
https://www.cnblogs.com/caiyishuai/p/9511567.html  python使用scikit-learn计算TF-IDF

词向量FastText：
https://zhuanlan.zhihu.com/p/32965521 fastText原理及实践
https://vel.life/fastText%E4%BD%93%E9%AA%8C%E7%AC%94%E8%AE%B0/ Fasttext体验笔记


词向量WordVec + BiLSTM
https://yifdu.github.io/2019/05/30/%E8%8F%9C%E9%B8%9F%E5%AD%A6NLP%EF%BC%88%E4%B8%83%EF%BC%89/ 菜鸟学NLP文本分类专题

Bert词向量
https://zhuanlan.zhihu.com/p/46652512【NLP】Google BERT详解