---
layout: post
title: "Selective Search"
date: 2018-04-13
excerpt: "Object Detection Selective Search 算法."
tags: [object detection, Deep learning, Selective Search]
comments: true
---

## **Selective Search 算法**  

* &ensp;&ensp;1. 使用图像分割的方法对图像作初始分割，提出分层分组的方法：  
&ensp;&ensp;&ensp;&ensp;step1:计算区域集R里面的每个相邻区域的相似度S={s1,s2,...}；  
&ensp;&ensp;&ensp;&ensp;step2:找出相似度最高的两个区域，将其合并并为新集；  
&ensp;&ensp;&ensp;&ensp;step3:从S中移除所有与step2中相关的子集；  
&ensp;&ensp;&ensp;&ensp;step4:计算新集与所有子集的相似度；  
&ensp;&ensp;&ensp;&ensp;step5:跳至step2，直至S为空。  
&ensp;&ensp;2. 相似度的计算：考虑了颜色、纹理、尺寸和空间交叠4个参数。  


* 优先合并以下四种区域：  
&ensp;&ensp;&ensp;&ensp;  1. 颜色（颜色直方图）相近;   
&ensp;&ensp;&ensp;&ensp;  2. 纹理（梯度直方图直方图）相近;   
&ensp;&ensp;&ensp;&ensp;  3. 合并后总面积最小;    
&ensp;&ensp;&ensp;&ensp;  4. 合并后，总面积在其BBOX中所占比例大的。   


* 保证合并操作的尺度较为均匀，避免一个大区域陆续“吃掉”其他小区域。  


* 保证合并后形状规则。  
