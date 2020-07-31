本节学习目标三个：
学习Word2Vec的使用和基础原理
学习使用TextCNN、TextRNN进行文本表示
学习使用HAN网络结构完成文本分类


word2vec两种模型：CBOW 和 Skip-Gram
两种近似解法：Hierarchical Softmax 和 Negative Sampling

可以使用gensim进行word2vec的训练，具体的参见：https://www.cnblogs.com/pinard/p/7278324.html

TextCNN
TextCNN利用CNN（卷积神经网络）进行文本特征抽取，不同大小的卷积核分别抽取n-gram特征，
卷积计算出的特征图经过MaxPooling保留最大的特征值，然后将拼接成一个向量作为文本的表示。

TextRNN利用RNN（循环神经网络）进行文本特征抽取，由于文本本身是一种序列，而LSTM天然适合建模序列数据。TextRNN将句子中每个词的词向量依次输入到双向双层LSTM，分别将两个方向最后一个有效位置的隐藏层拼接成一个向量作为文本的表示。

使用HAN用于文本分类
Hierarchical Attention Network for Document Classification(HAN)基于层级注意力，在单词和句子级别分别编码并基于注意力获得文档的表示，然后经过Softmax进行分类。其中word encoder的作用是获得句子的表示，可以替换为上节提到的TextCNN和TextRNN，也可以替换为下节中的BERT