# 对抗学习论文2019
## 防守
### IBP方法
- Certiﬁed Robustness to Adversarial Word Substitutions (nips19)
   - 概要：运用Interval Bound Propagation的方法提高NLP模型的鲁棒性
   - 方法：对于每个训练的样本，运用Interval Bound Propagation找到样本附近空间在模型输出空间的对应空间，然后在训练中尽量保证这个对应的输出空间和样本对应的标签一致。
   - 结果：数据集为IMDB和SNLI。Data-augmentation的方法在对抗攻击数据集上的准确率为35%左右，而用论文所提方法训练后准确率提升到75%左右
   - 不足：IBP方法只能估计输入对应的输出空间，误差随着模型层数的增加而增大，因此RNN等模型使用IBP方法会强迫离输入较远的空间对应输出也具有相同的标签，造成错误；即使在模型层数较少的模型中，运用IBP会降低普通测试数据的准确率，欠拟合问题严重。
   - 改进思路：在bound上增加采样点，减小bound传递误差（这里可以考虑一些优化的算法，比如如果激励函数都是Relu，那么每一层的边界都是多边形，可以寻找多边形的顶点，再将增加的采样点设置为这些顶点）；根据距离采样点的距离减小训练权重；不采取与坐标轴平行的bounding box，根据高维多面体的形状确定一个更优的bounding box.
### 预处理输入
- ComDefend: An Efﬁcient Image Compression Model to Defend Adversarial(cvpr 2019)
把输入经过一个压缩CNN和复原CNN来出去噪声，然后再输入到NN
- Barrage of Random Transforms for Adversarially Robust Defense(cvpr 2019)
通过几个不同类型预处理图片的方式的随机组合来处理图片再输入进NN，使攻击者无法获得有效梯度信息而无法攻击
- Feature Denoising for Improving Adversarial Robustness(cvpr 2019)
在NN的中间层提取feature map，并通过训练的神经网络对feature map 降噪
### 多模型共同学习
- Improving Adversarial Robustness via Promoting Ensemble Diversity
多个模型共同学习，并且通过最大化模型输出之间差异的方式提高不同模型的diversity，来提高整体的鲁棒性。
## 攻击
- Adversarial Reprogramming of Neural Network (nips19)
   - 概要：给定数据集X（图片）以及原有对应标签Y以及perturb标签Y'，假设Y=f(X)，数据集拼接额外像素块θ，论文目标是训练θ，使得Y'=f(X+θ)（此处+不是对应位置相加而是两个图片拼接成一个图片）
   - 方法：有点类似deep dream的方法，训练额外像素块θ每个像素点的颜色
   - 结果：在MNIST，CIFAR-10，counting三个数据集上获得perturb后99%，95%，65%的测试准确率。说明通过拼接额外训练后的像素块，可以将原有输入集和输出集的映射关系转换为拼接后输入集和perturb输出集的对应关系。
   - future work：可以尝试在语言模型上进行reprogramming测试；
- Metric Learning for Adversarial Robustness
   - 概要：给定输入x，输出y，x的对抗样本a，训练模型使x和同类样本距离尽量减小，a和x所在样本团体距离尽量增大，以此提高模型鲁棒性。
   - 方法：定义regularizer，来实现同类样本的聚集以及不同类样本的远离。
   - 结果：比以往的方法在鲁棒性上有提升。
