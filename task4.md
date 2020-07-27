本节采用的是深度学习文本分类的方法

深度学习采取的是端到端的解决方式，既能够提供特征提取功能，也能够完成分类功能。

传统的文本表示方法有：
One-hot
Bag of Words
N-gram
TF-IDF

但是维度较高，而且没有办法表示词之间的关系。

深度学习，则可以将词映射到低维空降，其中比较典型的例子有：FastText、Word2Vec和Bert。

fasttext有工具包，安装后

具体实现代码如下：
、、、
import pandas as pd
from sklearn.metrics import f1_score

# 转换为FastText需要的格式
train_df = pd.read_csv('../input/train_set.csv', sep='\t', nrows=15000)
train_df['label_ft'] = '__label__' + train_df['label'].astype(str)
train_df[['text','label_ft']].iloc[:-5000].to_csv('train.csv', index=None, header=None, sep='\t')

import fasttext
model = fasttext.train_supervised('train.csv', lr=1.0, wordNgrams=2, 
                                  verbose=2, minCount=1, epoch=25, loss="hs")

val_pred = [model.predict(x)[0][0].split('__')[-1] for x in train_df.iloc[-5000:]['text']]
print(f1_score(train_df['label'].values[-5000:].astype(str), val_pred, average='macro'))
、、、