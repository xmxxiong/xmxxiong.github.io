---
layout: post
title: "Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift"
date: 2018-06-13
excerpt: "2018-06-13 优化算法."
tags: [优化算法]
comments: true
---
## **Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift** 

 ![](https://github.com/xmxxiong/xmxxiong.github.io/blob/master/assets/img/Batch_normolaization/batch_normolization.PNG?raw=true){: .image-center}  

*batch normolization*:批标准化（批规范化）：防止梯度弥散和梯度爆炸，本质上解决反向传播过程中的梯度问题

#### 优点：
* 可以使用更高的学习率，如果每层的scale不一致，则每层需要的学习率是不一样的，同一层不同维度的scale往往需要不同大小的学习率，通常需要使用最小的学习率才能保证损失函数有效下降，batch normalization将每层、每维的scale保持一致，那么就可以用较高的学习率进行优化。
* 移除或使用较低的dropout.dropout是常用的防止overfitting的方法，而导致overfit的位置往往在数据边界处，如果初始化权重就落在数据内部，overfit现象可以得到一定的缓解。
* 降低L2的权重系数。边界的局部最优往往有几维的权重（斜率）较大，使用L2权重衰减可以缓解这一问题，使用了BN可以使权重衰减系数降低。
* 取消Local Response Normalization.
* 减少图像扭曲的使用。

* 在卷积层这种具有权值共享的层，Wx+b的均值和方差是对整张map求得的，在batch_size * channel * height * width 这么大一层中，对总共 batch_size * height * width 个像素点统计得到一个均值和一个标准差，共得到chane组的参数。




[原论文:https://arxiv.org/pdf/1502.03167.pdf](https://arxiv.org/pdf/1502.03167.pdf)  
