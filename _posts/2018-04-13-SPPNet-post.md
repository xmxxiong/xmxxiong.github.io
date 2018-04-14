---
layout: post
title: "Object Detection SPPNET"
date: 2018-04-13
excerpt: "RCNN 算法."
tags: [object detection, Deep learning, SPPNET]
comments: true
---
## **SPP_Net 算法** 

&ensp;&ensp;&ensp;&ensp;1. 提出了空间金字塔池化层，用于固定网络位于全连接层的输入大小；  
&ensp;&ensp;&ensp;&ensp;2. 在特征图上找对应的候选区。  

* **流程:**   

&ensp;&ensp;&ensp;&ensp;1. 通过select search从一张图片生成1K~2K个候选区；  
&ensp;&ensp;&ensp;&ensp;2. 特征提取先把待测图片整张进行特征提取，然后在feature map上 找到各个候选框的区域，然后对每个候选框采用空间金字塔池化，得到固定长度的特征向量；  
&ensp;&ensp;&ensp;&ensp;3. 特征送入每一类的SVM分类器，判断是否属于该类别。  

* ![](https://github.com/xmxxiong/xmxxiong.github.io/blob/master/assets/img/Spp_Net/spp_1.png?raw=true){: .image-center}  
共采用了3中池化视图，分别是{4\*4,2\*2,1\*1}，但是他们步长和窗的大小由输入图片决定。假设经过最后一层卷积得到的feature map的大小为a\*a,想得到的池化视图为n\*n,那么窗口win=a/n,步长=a/n.
* ![](https://github.com/xmxxiong/xmxxiong.github.io/blob/master/assets/img/Spp_Net/spp_3.png?raw=true){: .image-center}  
* ![](https://github.com/xmxxiong/xmxxiong.github.io/blob/master/assets/img/Spp_Net/spp_2.png?raw=true){: .image-center}  

* **存在的问题:**   

&ensp;&ensp;&ensp;&ensp;1. 和RCNN一样，训练过程仍然是隔离的，提取候选框 | 计算CNN特征| SVM分类 | Bounding Box回归独立训练，大量的中间结果需要转存，无法整体训练参数；  

&ensp;&ensp;&ensp;&ensp;2. SPP-Net在无法同时Tuning在SPP-Layer两边的卷积层和全连接层，很大程度上限制了深度CNN的效果；  

&ensp;&ensp;&ensp;&ensp;3. 在整个过程中，Proposal Region仍然很耗时。  
