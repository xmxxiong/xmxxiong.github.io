---
layout: post
title: "Optparser模块（python）:为sys.argv中提供的UNIX风格命令行选项提供高级支持"
date: 2018-04-16
excerpt: "2018-04-19 Python_Optparser模块."
tags: [python]
comments: true
---

## **OptionParser([\*\*argv])** 
创建一个新的命令选项解析器，并以Optionparser实例的形式返回。可以提供各种病可选关键字参数来控制配置。一般除非真正需要通过某些方式自定义选项处理，否则创建OptionParser对象时通常不带参数。例如：
{% highlight python %}  
p = optparser.OptionParser
{% endhighlight %}  
