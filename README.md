# 对抗学习论文2019
- Certiﬁed Robustness to Adversarial Word Substitutions (nips19)  
   对于每个训练的样本，运用Interval Bound Propagation找到样本附近空间在模型输出空间的对应空间，然后在训练中尽量保证这个对应的输出空间和样本对应的标签一致。不足：IBP方法只能估计输入对应的输出空间，误差随着模型层数的增加而增大，因此RNN等模型使用IBP方法会强迫离输入较远的空间对应输出也具有相同的标签，造成错误；即使在模型层数较少的模型中，运用IBP会降低普通测试数据的准确率，欠拟合问题严重。
- ComDefend: An Efﬁcient Image Compression Model to Defend Adversarial(cvpr 2019)  
   把输入经过一个压缩CNN和复原CNN来出去噪声，然后再输入到NN
- Barrage of Random Transforms for Adversarially Robust Defense(cvpr 2019)  
   通过几个不同类型预处理图片的方式的随机组合来处理图片再输入进NN，使攻击者无法获得有效梯度信息而无法攻击
- Feature Denoising for Improving Adversarial Robustness(cvpr 2019)  
   在NN的中间层提取feature map，并通过训练的神经网络对feature map 降噪
- Adversarial Defense by Stratiﬁed Convolutional Sparse Coding  (cvpr2019)
   没太看得懂，先放在这里先
- Improving Adversarial Robustness via Promoting Ensemble Diversity  (ICML2019)
   多个模型共同学习，并且通过最大化模型输出之间差异的方式提高不同模型的diversity，来使得一个模型被误导的时候其它模型能不被误导，以此来提高整体的鲁棒性。
- Metric Learning for Adversarial Robustness  (nips19)
   给定输入x，输出y，x的对抗样本a，训练模型使x和同类样本距离尽量减小，a和x所在样本团体距离尽量增大，以此提高模型鲁棒性。

