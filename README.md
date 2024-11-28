[合集 \- 从零开始的Python世界生活(2\)](https://github.com)[1\.从零开始的Python世界生活——内置模块篇（Math）11\-20](https://github.com/666-777-eto/p/18558729)2\.从零开始的Python世界生活——基础篇（Python字典）11\-27收起
# 从零开始的Python世界生活——基础篇（Python字典）


## 1\.Python字典是什么?


​ Python字典是python中非常重要的非常灵活和强大的内置数据结构，用于存储键值对（key\-value），Python中的字典等价于数学中的映射，也就是key(键)与value(值) 一 一 对应。我们可以通过查找key(键)来获得key(键)所对应value(值)。


## 2\.Python字典的特点


2\.1 `字典中key(键)唯一,不能相同,但value(值)可以相同`


2\.2 `字典中key(键)必须为不可变类型(如:字符串（常用）、元组、数字等),但value(值)可以是任意类型`


2\.3 `字典是可变的，可以在创建后修改`


2\.4 `字典中的元素没有固定顺序（在Python 3.7及以后的版本中，插入顺序会被保留）`


2\.5 `字典的查找操作,平均时间复杂度为O(1)`


## 3\.怎样创建一个字典？


### 3\.1 创建一个空字典:



```
p = {}#方法1
p = dict()#方法2

```

### 3\.2 创建一个字典:


#### 3\.2\.1 使用大括号`{}`



```
p = {
    "name":"Python",
    "age":33,
    "type": "programming language"
}

print(p)#运行结果:{'name': 'Python', 'age': 33, 'type': 'programming language'}

```

#### 3\.2\.2 使用`dict()`函数



```
p = dict(name = "Python",age = 33,type = "programming language")

p1 = dict()
print(p)#运行结果:{'name': 'Python', 'age': 33, 'type': 'programming language'}
print(p1)

```

##### 3\.2\.3 使用`zip()`函数压缩列表



```
p1 = ["name","age","type"]
p2 = ["Python",33,"programming language"]
p = dict(zip(p1,p2))

print(p)#运行结果:{'name': 'Python', 'age': 33, 'type': 'programming language'}

```

#### 3\.2\.4 使用列表推导式



```
p = {x: x**2 for x in range(5)}  # 创建一个包含0到4的平方的字典

```

根据使用场景的不同，选择合适的方法创建字典


## 4\.字典的基础操作


### 4\.1 访问值



```
p = dict(name="Python", age=33, type="programming language") 

print(p["name"])  # 运行结果: Python  
print(p.get("age"))  # 运行结果: 33  

```

### 4\.2 修改值



```
p = dict(name="Python", age=33, type="programming language")

p["age"] = 34  
print(p["age"])  # 运行结果: 34  

```

### 4\.3 添加新的键值对



```
p = dict(name="Python", age=33, type="programming language")

p["creator"] = "Guido van Rossum"  
print(p)  
# 运行结果:{'name': 'Python', 'age': 34, 'type': 'programming language', 'creator': 'Guido van Rossum'}

```

### 4\.4 删除键值对


4\.3\.1 使用`del`



```
p = dict(name="Python", age=33, type="programming language")

del p["type"]  # 删除type键
print(p)
#运行结果:{'name': 'Python', 'age': 33}

```

4\.3\.2 使用`pop()`



```
p = dict(name="Python", age=33, type="programming language")

y = p.pop("type") # 删除type键
print(p)#运行结果:{'name': 'Python', 'age': 33}
print(y)#运行结果:programming language

```

### 4\.5 获取所有键值对


#### 4\.5\.1 获取所有键`keys()`



```
p = dict(name="Python", age=33, type="programming language")

keys = list(p.keys())  
print(keys)  
# 运行结果: ['name', 'age', 'type']

```

#### 4\.5\.2 获取所有值`values()`



```
p = dict(name="Python", age=33, type="programming language")

values = list(p.values())  
print(values)  

```

#### 4\.5\.3 获取键值对 `items()`



```
p = dict(name="Python", age=33, type="programming language")

items = list(p.items())  
print(items)  

```

### 4\.6 检查键是否存在



```
p = dict(name="Python", age=33, type="programming language")

print("name" in p)  # 输出: True  
print("creator" in p)  # 输出: False  

```

### 4\.7 合并字典(你知道茴香豆的‘茴’字有几种写法吗\_)


#### 4\.7\.1 使用`|`运算符


`注意:该方法适用于python3.9及以上版本`



```
dict1 = {"a": 1, "b": 2}  
dict2 = {"c": 3, "d": 4}  
dict1 = dict1 | dict2  
print(dict1)# 运行结果: {'a': 1, 'b': 2, 'c': 3, 'd': 4}

```

#### 4\.7\.2 使用`**`解包


`注意:该方法适用于python3.5及以上版本`



```
dict1 = {"a": 1, "b": 2}  
dict2 = {"c": 3, "d": 4}  
dict1 = {**dict1, **dict2}   
print(dict1)# 运行结果: {'a': 1, 'b': 2, 'c': 3, 'd': 4}

```

#### 4\.7\.3 使用 `update()` (传统方法)



```
dict1 = {"a": 1, "b": 2}  
dict2 = {"c": 3, "d": 4}  
dict1.update(dict2)
print(dict1)# 运行结果: {'a': 1, 'b': 2, 'c': 3, 'd': 4}

```

#### 4\.7\.4 性能对比


为了更好地选择合适的合并方法，下面是对三种方法的简单性能对比：



```
# 性能测试代码  
import timeit  
# 合并运算符  
print(timeit.timeit("dict1 | dict2",   
    setup="dict1={'a':1}; dict2={'b':2}",   
    number=100000))  
# 解包方法  
print(timeit.timeit("{**dict1, **dict2}",   
    setup="dict1={'a':1}; dict2={'b':2}",   
    number=100000))  
# update() 方法  
print(timeit.timeit("dict1.copy().update(dict2)",   
    setup="dict1={'a':1}; dict2={'b':2}",   
    number=100000))

```

##### 运行结果示例：



```
0.004538799985311925
0.004827399970963597
0.006663299980573356

```

根据性能测试结果，推荐使用的合并方法依次为：


1. 使用 `|` 运算符（Python 3\.9\+）
2. 使用 `**` 解包（Python 3\.5\+）
3. 使用 `update()` 方法（传统方法）


在选择合并方法时，请`务必`考虑自身的 Python 版本兼容性。


## 结语


恭喜你，已经成功踏入了 Python 字典的世界！现在你不仅知道字典是如何工作的，还掌握了如何创建、修改和合并它们的技巧。就像在生活中，我们常常需要找到合适的钥匙来打开不同的门，字典也为我们提供了快速查找的“钥匙”。无论是存储用户信息、配置参数，还是处理复杂的数据结构，它都能派上用场。


Happy coding！😄



> 入门之道，就在其中


  * [从零开始的Python世界生活——基础篇（Python字典）](#%E4%BB%8E%E9%9B%B6%E5%BC%80%E5%A7%8B%E7%9A%84python%E4%B8%96%E7%95%8C%E7%94%9F%E6%B4%BB%E5%9F%BA%E7%A1%80%E7%AF%87python%E5%AD%97%E5%85%B8)
* [1\.Python字典是什么?](#tid-DkB5pQ)
* [2\.Python字典的特点](#tid-r7A7kc)
* [3\.怎样创建一个字典？](#tid-YpCidR)
* [3\.1 创建一个空字典:](#tid-JrxK58)
* [3\.2 创建一个字典:](#tid-HRdKTP)
* [3\.2\.1 使用大括号{}](#tid-3pneWh)
* [3\.2\.2 使用dict()函数](#tid-Sjn3XR)
* [3\.2\.3 使用zip()函数压缩列表](#tid-QbESdc)
* [3\.2\.4 使用列表推导式](#tid-MDMNTP)
* [4\.字典的基础操作](#tid-MYwFzr)
* [4\.1 访问值](#tid-jxWc74)
* [4\.2 修改值](#tid-DPxf4E)
* [4\.3 添加新的键值对](#tid-wdrEtp)
* [4\.4 删除键值对](#tid-Fbtm26)
* [4\.5 获取所有键值对](#tid-CeFNxx):[FlowerCloud机场节点订阅](https://dahelaoshi.com)
* [4\.5\.1 获取所有键keys()](#tid-zKpjEH)
* [4\.5\.2 获取所有值values()](#tid-wfRpde)
* [4\.5\.3 获取键值对 items()](#tid-SYi3T2)
* [4\.6 检查键是否存在](#tid-Tca2R7)
* [4\.7 合并字典(你知道茴香豆的‘茴’字有几种写法吗\_)](#tid-MxTmA2)
* [4\.7\.1 使用\|运算符](#tid-8wADyH)
* [4\.7\.2 使用\*\*解包](#tid-zhNa2C)
* [4\.7\.3 使用 update() (传统方法)](#tid-d6f4Mm)
* [4\.7\.4 性能对比](#tid-xwCyer)
* [运行结果示例：](#%E8%BF%90%E8%A1%8C%E7%BB%93%E6%9E%9C%E7%A4%BA%E4%BE%8B)
* [结语](#%E7%BB%93%E8%AF%AD)

   ![](https://github.com/cnblogs_com/blogs/832194/galleries/2424134/t_241001140621_%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20231111221642.png)    - **本文作者：** [MPyGF](https://github.com)
 - **本文链接：** [https://github.com/666\-777\-eto/p/18573193](https://github.com)
 - **关于博主：** 评论和私信会在第一时间回复。或者[直接私信](https://github.com)我。
 - **版权声明：** 本博客所有文章除特别声明外，均采用 [BY\-NC\-SA](https://github.com "BY-NC-SA") 许可协议。转载请注明出处！
 - **声援博主：** 如果您觉得文章对您有帮助，可以点击文章右下角**【[推荐](javascript:void(0);)】**一下。
     
