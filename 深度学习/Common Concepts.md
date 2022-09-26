# Commnon Concepts

## Deep Learning

| Chinese                   | English                         | Meaning                                                      |
| ------------------------- | ------------------------------- | ------------------------------------------------------------ |
| 损失函数（误差函数）      | loss function                   | 用于衡量算法的运行情况，即预测值和真实值的接近程度。**损失函数是在单个训练样本中定义的，它衡量的是算法在单个训练样本中的表现。** |
| 代价函数（成本函数）      | cost function                   | **衡量算法在全部训练样本上的表现**                           |
| 修正线性单元              | Rectified     linear unit，ReLU | 激活函数，$f(x)=\max(0,x)$                                   |
| 卷积神经网络              | CNN                             |                                                              |
| 循环神经网络              | RNN                             |                                                              |
| 监督学习                  | Supervised  Learning            |                                                              |
| sigmoid函数/logistic 函数 | ——                              | 激活函数，$f(x)=\frac{1}{1+e^{-x}}$                          |
| 链式法则                  | Chain Rule                      | 微积分                                                       |
| 反向传播                  | Back propagation                | BP算法的学习过程由正向传播过程和反向传播过程组成。在正向传播过程中，输入信息通过逐层处理并传向输出层。如果在输出层得不到期望的输出值，则通过构造输出值与真实值的损失函数作为目标函数，转入反向传播，逐层求出目标函数对各神经元权值的偏导数，构成目标函数对权值向量的梯度，作为修改权值的依据，网络的学习在权值修改过程中完成。输出值与真实值的误差达到所期望值时，网络学习结束。 |
|                           | dropout                         | 在深度学习网络的训练过程中，对于神经网络单元，按照一定的概率将其暂时从网络中丢弃 |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |
|                           |                                 |                                                              |

## Statistics

精度和召回率呈负相关，证明：

一个数据集的样本数量是固定的，正样本和负样本的数量也是固定，公式表达如下：

$正样本 = TP+TN = constant1$

$负样本 = FP + FN = constant2$

$constant1 + constant2 = 样本总数量$

![img](https://upload-images.jianshu.io/upload_images/6404778-0cd55fe36ceadfa6.png?imageMogr2/auto-orient/strip|imageView2/2/w/400/format/webp)

| Chinese      | English                       | Meaning                                                      |
| ------------ | ----------------------------- | ------------------------------------------------------------ |
| 极大似然估计 | maximum likelihood estimation | 求出一组参数，使式子取最大值                                 |
| 真阳性       | TP/true positive              | 正确地检测到阳性结果                                         |
| 假阳性       | FP/false positive             | 错误地检测到阳性结果                                         |
| 真阴性       | TN/true negative              | 正确地检测到阴性结果                                         |
| 假阴性       | FN/false negative             | 错误地检测到阴性结果                                         |
| 准确率       | accuracy                      | $\mathrm{\frac{TP+TN}{TP+TN+FP+FN}}$，在全部预测中，正确预测结果占的比例 |
| 精度         | P/precision                   | $\mathrm{\frac{TP}{TP+FP}}$，在全部阳性预测中，正确预测结果占的比例（找得对） |
| 召回率       | R/recall                      | $\mathrm{\frac{TP}{TP+FN}}$，在全部阳性事件中，正确预测结果占的比例（找得全） |
| PR曲线       | ——                            | ![在这里插入图片描述](https://img-blog.csdnimg.cn/1809afd4f2f14be8a607160d1c74cff3.png#pic_center) |
| 平均精度     | AP/average precision          | PR曲线与坐标轴围成的面积，$\mathrm{AP=\int_0^1P(r)dr}$       |
|              | mAP                           | 在所有类别上的AP求平均值                                     |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |
|              |                               |                                                              |

