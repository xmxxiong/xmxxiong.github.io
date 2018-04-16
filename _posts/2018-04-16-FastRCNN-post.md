---
layout: post
title: "Fast RCNN"
date: 2018-04-16
excerpt: "2018-04-16 Object Detection Fast RCNN 算法."
tags: [object detection, Deep learning, Fast RCNN]
comments: true
---
## **Fast RCNN 算法** 
* **解决的问题:**  

&ensp;&ensp;&ensp;&ensp;1. 避免了R-CNN中的冗余的特征提取操作，只对整张图像全区域进行一次特征提取；    
&ensp;&ensp;&ensp;&ensp;2. 用Rol pooling层取代最后一层max pooling层，同时在此处引入建议框信息，提取相应建议框特征；  
&ensp;&ensp;&ensp;&ensp;3. 网络末尾采用并行的不同的全连接层，可同时输出分类结果和回归结果，实现了end-to-end的多任务训练；  
&ensp;&ensp;&ensp;&ensp;4. 无需额外的磁盘空间缓存特征；  
&ensp;&ensp;&ensp;&ensp;5. 比R CNN和SPPNet有着更高的目标检测精度和更快的检测速度。

* **流程:**   
* ![](https://github.com/xmxxiong/xmxxiong.github.io/blob/master/assets/img/FastRCNN/FastRCNN1.png?raw=true){: .image-center}  
* ![](https://github.com/xmxxiong/xmxxiong.github.io/blob/master/assets/img/FastRCNN/FastRCNN2.png?raw=true){: .image-center} 
&ensp;&ensp;&ensp;&ensp;1. 任意size的图像输入CNN，经过卷积和池化得到特征图；  
&ensp;&ensp;&ensp;&ensp;2. 在任意size图片上采用selective search算法提取约2K个建议框；  
&ensp;&ensp;&ensp;&ensp;3. 根据图中建议框到特征图映射关系，在特征图中找到建议框对应特征框，并利用Rol池化层将每个特征框池化到H*W的大小；  
&ensp;&ensp;&ensp;&ensp;4. 将固定了大小的特征框经过全连接层得到固定大小的特征向量；  
&ensp;&ensp;&ensp;&ensp;5. 将第4步中的特征向量经过不同的全连接层，分别得到两个输出向量：一个softmax的分类得分，一个是Bounding-box窗口回归；  
&ensp;&ensp;&ensp;&ensp;6. 利用窗口得分分别对每一类物体进行非极大抑制提出重复建议框，最终得到每个类别中回归修正后的得分最高的窗口。  

* **存在的问题:**   

&ensp;&ensp;&ensp;&ensp;1. 每张图片由ss算法产生的约2000的建议框消耗了大量的计算资源和时间；  
&ensp;&ensp;&ensp;&ensp;2. 没有实现真正意义上的end-to-end的训练模式。  
   
* ![](https://github.com/xmxxiong/xmxxiong.github.io/blob/master/assets/img/FastRCNN/FastRCNN3.png?raw=true){: .image-center}   

  参考：[ Fast R-CNN 简单梳理](https://blog.csdn.net/xg123321123/article/details/53067518)  
  [ Fast R-CNN论文详解](https://blog.csdn.net/WoPawn/article/details/52463853)