---
layout: post
title: "Optparser模块（python）:为sys.argv中提供的UNIX风格命令行选项提供高级支持"
date: 2018-04-19
excerpt: "2018-04-19 Python_Optparser模块."
tags: [python, parser]
comments: true
---

## **OptionParser([\*\*argv])** 
创建一个新的命令选项解析器，并以Optionparser实例的形式返回。可以提供各种病可选关键字参数来控制配置。一般除非真正需要通过某些方式自定义选项处理，否则创建OptionParser对象时通常不带参数。例如：
{% highlight python %}
p = optparser.OptionParser
{% endhighlight %}  

OptionParser的实例p支持一下方法：  
{% highlight python %}
p = p.add_option(name1,...,nameN [, **parms])
{% endhighlight %}
给p添加一个新的选项。参数name1,name2等分别是所有选项的名称。例如，包含的选项名称无论长短都可以，如'-f'和'--file'。紧随选项名称后的是一组可选关键字，用于指定解析时如何处理的选项。部分描述如下表所示：  

|**关键字参数**|**描述**|
|:---------------|:------------------------------------------------------------------------------------------------------------------------|
|action:         |  1. store: 选项有一个参数需要读取和保存                                                                                   |
|                |  2. store_const:选项不带任何参数，但当遇到选项时，保存const关键字指定的常量值。                                              |
|                |  3. store_true:解析选项时保存布尔类型的True值。                                                                            |
|                |  4. store_false:解析选项时保存布尔类型的False值。                                                                          |
|                |  5. append:选项有一个参数，解析时被附加到一个列表中，如果使用相同的命令行参数指定多个值，就要使用这个值。                        |
|                |  6. count:选项不带任何参数，但保存一个计数器值。每次遇到参数时，计数器的值就会增加。                                           |
|                |  7. callback:遇到选项时，使用callback关键字参数指定的一个回调函数。                                                          |
|                |  8. help:解析选项时打印一条帮助信息。只有需要通过标准的-h或--help选择之外的选项帮助时，才需要使用这个值。                        |
|                |  9. version:打印提供给OptionParser()的参数，如果有的话，只需要通过标注的-v或--version选择之外的选项显示帮助是，才需要使用这个值。|
|----
|callback:       |  指定遇到选项时调用的回调函数。                                                                                             |
|callback_args:  |  提供给callback参数指定的回调函数的可选位置参数 。                                                                           |
|callback_kargs: |  提供给callback参数指定的回调函数的可选关键字参数。                                                                          |
|choice:         |  指定所有可能的选项值的字符串列表。当选项只有一组有限值(['small','medium','large'])时使用。                                    |
|const:          |  通过'store_const'动作保存常量值。                                                                                         |
|default:        |  如果未提供，设置选项的默认值。默认情况下，默认值是None。                                                                     |
|dest:           |  设置用于保存解析期间的选项值的属性名称。名称通常来自选项名称本身。                                                            |
|help:           |  指定特定选项的帮助文本，如果未提供，帮助中列出此项将不带描述，可以使用值optparser.SUPPRESS_HELP隐藏选项特殊关键字'%default'将被帮助字符串中的选项默认值替换。   |
|metavar:        |  指定打印帮助文本时使用的选项参数名称。                                                                                      |
|nargs:          |  为需要的动作指定选项参数的数量。默认值为1.如果使用的数字大于1，选项参数将被收集到一个元组中，处理参数时将包含这个元组。            |
|type:           |  指定选项的类型。有效的类型包括'string'(默认值),'int','long','choice','float'和'complex'。                                   |
|----

参考：《Python参考手册(第四版.修订版)》