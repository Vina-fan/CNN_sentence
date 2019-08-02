# CNN Sentence Classification

Sentence Classification是CNN在NLP中的重要应用之一。

传统Sentence Classification一般使用SVM或者Naive Bayes。文本表示方式大多是Bag of Words，但是没有考虑文本中单词出现的顺序。

CNN主要用于图像的处理，但是借鉴思路可以用在NLP中：根据系统自身的特征，每一个时刻的输出都和之前的输入相关，考虑了单词的顺序。

![1564714949472](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564714949472.png)

## 输入层

输入层将1个sentence转化为一个二维的图像。其中每一行表示一个词语的Word2Vec向量，将单词按照顺序排序即得到一个矩阵，类似于图像的像素值。n个词语按照顺序可以组成n*k维的矩阵，k为word Embedding的维度。

其中，CNN的Word Vector是随机初始化的，在训练的时候可以是固定不变的，也可以是微调的。Kernel的size可以不同，可以获取不同范围内词之间的关系，和图像中的CNN的filter有所区别。

## 卷积层

经过kernel卷积后的卷积层为一个宽度为1的长条。

## 池化层

论文中使用的是Maxpooling， 选择并保留feature map中最大值作为特征。

## 全连接层

带有dropout 和softmax的全连接

## 论文试验

**数据**中word2vec使用谷歌预训练的GoogleNews-vectors-negative300.bin

![1564714628785](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564714628785.png)



## 附（卷积的理解）

从数学的角度讲，卷积是一种运算方法，涉及到积分和级数等高等数学。

对于卷积的定义，在离散情况下：

![1564715885055](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564715885055.png)

在连续情况下：

![1564715907104](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1564715907104.png)

对于图像，由于图像中有很多噪点，属于高频信号，需要对这些信号进行平滑，得到相对平滑的像素。

图像的像素可以看作一个像素矩阵，通过矩阵的运算可以实现卷积，对于指定点附近的矩阵范围内的点，卷积得到相对平滑的值。







































