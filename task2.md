今天是 新闻本文分类的 第二天任务 数据读取和数据分析

主要参考的资料是：
Baseline(TD-IDF + LR/XGB) 0.93


读取文件：
pd.read_csv

TD-IDF做特征提取：
TfidfVectorizer

分类用到了逻辑回归和XGB两种方案
分别为LogisticRegression 和 XGBClassifier

保存到本地 df.to_csv()


-----
xgboost安装还是有问题，代码baseline没有跑得起来，明天再看。