# Python 总结

> author : 刘士
>
> date:2017/11/5

```python
# 单行注释由一个井号开头。
"""
三个双引号（或单引号）之间可以写多行字符串，
通常用来写注释。
"""
```

## 基本数据类型和操作符

* `type()` 查看类型

  ```python
  type(3)
  ```

* 数字就是数字

  ```python
  123
  ```

* 算数运算与常识中的保持一致

  ```python
  1 + 1 #=> 2
  8 - 1 #=> 7
  10 * 2 #=> 20
  5 / 2 #=> 2.5
  ```

  > 整除有一点棘手。对于整除来说，计算结果会自动取整。

  ```python
  5 // 2 #=> 2
  ```

  > 求余用``%``

  ```python
  10 % 3 #=> 1
  ```

  > 求乘方用``**``

  ```python
  3**2 #=>9
  ```

* 使用小括号来强制计算的优先顺序

  ```python
  (1 + 3) * 2 #=> 8
  ```

* 布尔值也是基本数据类型

  ```python
  True
  False
  ```

* 使用 ``not`` 来取反

  ```python
  not True #=> False
  not False #=> True
  ```

* 等式判断用 ``==``

  ```python
  1 == 1 #=> True
  2 == 1 #=> False
  ```

* 不等式判断是用 ``!=``

  ```python
  1 != 1 #=> False
  2 != 1 #=> True
  ```

* 还有更多的比较运算

  ```python
  1 < 10 #=> True
  1 > 10 #=> False
  2 <= 2 #=> True
  2 >= 2 #=> True
  ```

* 居然可以把比较运算串连起来！

  ```python
  1 < 2 < 3 #=> True
  2 < 3 < 2 #=> False
  2 < 3 == 2 #=> False
  2 < 3 >1 #=> True
  ```

* 使用 ``"`` 或 ``'`` 来创建字符串

  ```python
  "这是一个字符串."
  '这也是一个字符串.'
  ```

* 字符串也可以相加！

  ```python
  "Hello " + "world!" #=> "Hello world!"
  ```

* 一个字符串可以视为一个特殊的元祖（后面讲到）

  ```python
  "This is a string"[0] #=> 'T'
  ```

* % 可以用来格式化字符串，就像这样：

  ```python
  "%s 是 %s" % ("字符串", "特殊的元祖")
  ```

* 后来又有一种格式化字符串的新方法：``format`` 方法。我们推荐使用这个方法。

  ```python
  "{0} can be {1}".format("strings", "formatted")
  ```

* 如果你不喜欢数数的话，可以使用关键字（变量）。

  ```python
  "{name} 想要吃 {food}".format(name="李四", food="土豆")
  ```

* None 是一个对象

  ```python
  None #=> None
  ```

* 不要使用相等符号 ``==`` 来把对象和 ``None`` 进行比较，而要用 ``is``。

  ```python
  "etc" is None #=> False
  None is None  #=> True
  '' is None #=> False
  '' is not None #=> True
  # 这个 `is` 操作符用于比较两个对象的标识。
  # （对象一旦建立，其标识就不会改变，可以认为它就是对象的内存地址。）
  # 在处理基本数据类型时基本用不上，
  # 但它在处理对象时很有用。
  ```

* 0 等于 False   1 等于 True

  ```python
  0 == False  #=> True
  1 == True #=> True
  2 == True #=> False
  ```

## 变量和集合

* 打印输出很简单

  ```python
  print("我是Python")
  ```

* 变量命名规则
  * 第一个字符必须是字母表中的字母（大写 ASCII 字符或小写 ASCII 字符或 Unicode 字符）或下划线（_）。
  * 标识符的其它部分可以由字符（大写 ASCII 字符或小写 ASCII 字符或 Unicode 字符）、下划线（_）、数字（0~9）组成。
  * 标识符名称区分大小写。例如，myname 和 myName 并 _不_ 等同。要注意到前者是小写字母 n 而后者是大写字母 N。
  * 有效 的标识符名称可以是 i 或 name_2_3 ， **无效** 的标识符名称可能是 2things，this is spaced out，my-name 和 >a1b2_c3。

* 在赋值给变量之前不需要声明

  ```python
  some_var = 5    # 变量名的约定是使用下划线分隔的小写单词
  some_var #=> 5
  ```

* 访问一个未赋值的变量会产生一个异常。

  ```python
  some_other_var  # 会抛出一个名称错误
  ```

* ``if`` 可以作为表达式来使用

  ```python
  "你好!" if 3 > 2 else 2 #=> "你好!"
  "你好!" if 3 == 2 else 2 #=> 2
  ```

## 列表

* 列表用于存储序列

  ```python
  li = []
  ```

* 我们先尝试一个预先填充好的列表

  ```python
  other_li = [4, 5, 6]
  ```

### 列表常用方法

* 使用 ``append`` 方法把元素添加到列表的尾部

  ```python
  li.append(1)    #li 现在是 [1]
  li.append(2)    #li 现在是 [1, 2]
  li.append(4)    #li 现在是 [1, 2, 4]
  li.append(3)    #li 现在是 [1, 2, 4, 3]
  ```

* 使用 ``pop`` 来移除最后一个元素

  ```python
  li.pop()        #=> 3，然后 li 现在是 [1, 2, 4]
  ```

* 我们再把它放回去

  ```python
  li.append(3)    # li 现在又是 [1, 2, 4, 3] 了
  ```

* 像访问其它语言的数组那样访问列表

  ```python
  li[0] #=> 1
  ```

* 查询最后一个元素

  ```python
  li[-1] #=> 3
  ```

* 越界查询会产生一个索引错误

  ```python
  li[4] # 抛出一个索引错误
  ```

* 你可以使用切片语法来查询列表的一个范围。（这个范围相当于数学中的左闭右开区间。）

  ```python
  li[1:3] #=> [2, 4]
  ```

* 省略开头

  ```python
  li[2:] #=> [4, 3]
  ```

* 省略结尾

  ```python
  li[:3] #=> [1, 2, 4]
  ```

* li【开始：结束：步长】

  ```python
  li = [1, 2, 4, 3]
  li[0:3:2] #=> [1, 4]
  ```

* 使用 del 来删除列表中的任意元素

  ```python
  del li[2] # li 现在是 [1, 2, 3]
  ```

* 可以把列表相加

  ```python
  li + other_li #=> [1, 2, 3, 4, 5, 6] - 请留意 li 和 other_li 并不会被修改
  ```

* 使用 extend 来合并列表

  ```python
  li.extend(other_li) # 现在 li 是 [1, 2, 3, 4, 5, 6]
  ```

* 用 in 来检查是否存在于某个列表中

  ```python
  1 in li #=> True
  ```

* 用 len 来检测列表的长度

  ```python
  len(li) #=> 6
  ```

## 元组很像列表，但它是“不可变”的

```python
tup = (1, 2, 3)
tup[0] #=> 1
tup[0] = 3  # 抛出一个类型错误
```

* 创建只有一个元素的元组

  ```python
  tup1 = (1,)
  ```

* 操作列表的方式通常也能用在元组身上

  ```python
  len(tup) #=> 3
  tup + (4, 5, 6) #=> (1, 2, 3, 4, 5, 6)
  tup[:2] #=> (1, 2)
  2 in tup #=> True
  ```

* 你可以把元组（或列表）中的元素解包赋值给多个变量

  ```python
  a, b, c = (1, 2, 3)     # 现在 a 是 1，b 是 2，c 是 3
  ```

* 如果你省去了小括号，那么元组会被自动创建

  ```python
  d, e, f = 4, 5, 6
  ```

* 再来看看交换两个值是多么简单。

  ```python
  e, d = d, e     # 现在 d 是 5 而 e 是 4
  ```

## 序列的方法

* 下面的内建函数 (built-in function) 可用于序列（列表，元组，字符串）:

> s 为一个序列

| 函数     | 含义                      |
|--------|-------------------------|
| len(s) | 返回：序列中包含元素的个数           |
| min(s) | 返回：序列中最小的元素             |
| max(s) | 返回：序列中最大的元素             |
| all(s) | 返回：True, 如果所有元素都为 True 的话 |
| any(s) | 返回：True, 如果任一元素为 True 的话  |

* 下面的方法主要起查询功能，不改变序列本身，可用于列表和元组：

| 函数     | 含义           |
|--------|--------------|
| sum(s) | 返回：序列中所有元素的和 |

> x 为元素值，i 为下标（元素在序列中的位置）

| 函数         | 含义               |
|------------|------------------|
| s.count(x) | 返回： x 在 s 中出现的次数    |
| s.index(x) | 返回： x 在 s 中第一次出现的下标 |

* 由于元组的元素不可变更，下面方法只适用于列表：
  > A 为一个列表，B 为另一个列表

| 函数          | 含义                        |
|-------------|---------------------------|
| A.extend(B) | 在列表 l 的末尾添加列表 l2 的所有元素        |
| A.append(x) | 在 l 的末尾附加 x 元素                |
| A.sort()    | 对 l 中的元素大小排序                |
| A.reverse() | 将 l 中的元素按照原始顺序倒序排列          |
| A.pop()     | 返回：列表 l 的最后一个元素，并在列表 l 中删除该元素 |
| del l1[i]   | 删除该元素                     |

（以上这些方法都是在原来的列表的上进行操作，会对原来的列表产生影响，而不是返回一个新列表。)

* 下面是一些用于字符串的方法。

  尽管字符串是元组的特殊的一种，但字符串 (string) 类有一些方法是改变字符串的。这些方法的本质不是对原有字符串进行操作，而是删除原有字符串，再建立一个新的字符串，所以并不与元组的特点相矛盾。

  > str 为一个字符串，sub 为 str 的一个子字符串。s 为一个序列，它的元素都是字符串。width 为一个整数，用于说明新生成字符串的宽度。

| 函数                        | 含义                                                                                                  |
|---------------------------|-----------------------------------------------------------------------------------------------------|
| str.count(sub)            | 返回：sub 在 str 中出现的次数                                                                                    |
| str.find(sub)             | 返回：从左开始，查找 sub 在 str 中第一次出现的位置。如果 str 中不包含 sub，返回 -1                                                       |
| str.index(sub)            | 返回：从左开始，查找 sub 在 str 中第一次出现的位置。如果 str 中不包含 sub，返回错误                                                        |
| str.split([sep, [max]])   | 返回：从左开始，以空格为分割符 (separator)，将 str 分割为多个子字符串，总共分割 max 次。将所得的子字符串放在一个列表中返回。可以 str.split(',') 的方式使用逗号或者其它分割符  |
| str.rsplit([sep, [max]])  | 返回：从右开始，以空格为分割符 (separator)，将 str 分割为多个子字符串，总共分割 max 次。将所得的子字符串放在一个列表中返回。可以 str.rsplit(',') 的方式使用逗号或者其它分割符 |
| str.join(s)               | 返回：将 s 中的元素，以 str 为分割符，合并成为一个字符串。                                                                       |
| str.strip([sub])          | 返回：去掉字符串开头和结尾的空格与特殊字符。也可以提供参数 sub，去掉位于字符串开头和结尾的 sub                                                   |
| str.replace(sub, new_sub) | 返回：用一个新的字符串 new_sub 替换 str 中的 sub                                                                        |
| str.capitalize()          | 返回：将 str 第一个字母大写                                                                                      |
| str.lower()               | 返回：将 str 全部字母改为小写                                                                                     |
| str.upper()               | 返回：将 str 全部字母改为大写                                                                                     |
| str.swapcase()            | 返回：将 str 大写字母改为小写，小写改为大写                                                                              |

## 字典用于存储映射关系

```python
empty_dict = {}  # 空字典
```

* 这是一个预先填充的字典

  ```python
  filled_dict = {"one": 1, "two": 2, "three": 3}
  ```

* 使用 [] 来查询键值

  ```python
  filled_dict["one"] #=> 1
  ```

* 将字典的所有键名获取为一个列表

  ```python
  filled_dict.keys() #=> ["three", "two", "one"]

  # 请注意：无法保证字典键名的顺序如何排列。
  # 你得到的结果可能跟上面的示例不一致。
  ```

* 将字典的所有键值获取为一个列表

  ```python
  filled_dict.values() #=> [3, 2, 1]
  ```

* 使用 in 来检查一个字典是否包含某个键名

  ```python
  "one" in filled_dict #=> True
  1 in filled_dict #=> False
  ```

* 查询一个不存在的键名会产生一个键名错误

  ```python
  filled_dict["four"] # 键名错误
  ```

* 所以要使用 ``get`` 方法来避免键名错误

  ```python
  filled_dict.get("one") #=> 1
  filled_dict.get("four") #=> None
  ```

* ``get`` 方法支持传入一个默认值参数，将在取不到值时返回。

  ```python
  filled_dict.get("one", 4) #=> 1
  filled_dict.get("four", 4) #=> 4
  ```

* 修改字典的值

  ```python
  filled_dict["one"] = 111
  ```

* ``Setdefault`` 方法可以安全地把新的名值对添加到字典里

  ```python
  filled_dict.setdefault("five", 5) #filled_dict["five"] 被设置为 5
  filled_dict.setdefault("five", 6) #filled_dict["five"] 仍然为 5
  ```

## set 用于保存集合

```python
empty_set = set()  # 空集合
```

* 初始化只有一个元素的集合

  ```python
  set1 = set([1])
  set2 = {1}
  ```

* 使用一堆值来初始化一个集合

  ```python
  some_set = set([1,2,2,3,4]) # some_set 现在是 set([1, 2, 3, 4])
  ```

* 从 Python 2.7 开始，{} 可以用来声明一个集合

  ```python
  filled_set = {1, 2, 2, 3, 4} # => {1, 2, 3, 4}
  # （注：集合是种无序不重复的元素集，因此重复的 2 被滤除了。）
  # （注：{} 不会创建一个空集合，只会创建一个空字典。）
  ```

* 把更多的元素添加进一个集合

  ```python
  filled_set.add(5) # filled_set 现在是 {1, 2, 3, 4, 5}
  ```

* 使用 & 来获取交集

  ```python
  other_set = {3, 4, 5, 6}
  filled_set & other_set #=> {3, 4, 5}
  ```

* 使用 | 来获取并集

  ```python
  filled_set | other_set #=> {1, 2, 3, 4, 5, 6}
  ```

* 使用 - 来获取补集

  ```python
  {1,2,3,4} - {2,3,5} #=> {1, 4}
  ```

* 使用 in 来检查是否存在于某个集合中

  ```python
  2 in filled_set #=> True
  10 in filled_set #=> False
  ```

## 强制类型转换

* str->int

  ```python
  int('123')
  ```

* int->str

  ```python
  str(123)
  ```

* list->set

  ```python
  set([1,2,3,4,5])
  ```

* set->list

  ```python
  list({1, 2, 3, 4, 5})
  ```

* list->tuple

  ```python
  tuple([1,2,3,4,5])
  ```

* tuple->list

  ```python
  list((1,2,3,4,5))
  ```

## 控制流

* 我们先创建一个变量

  ```python
  some_var = 5
  ```

* 这里有一个条件语句。缩进在 Python 中可是很重要的哦！程序会打印出 `some_var 比 10 小`

  ```python
  if some_var > 10:
      print("some_var 完全比 10 大.")
  elif some_var < 10:    # 这里的 elif 子句是可选的
      print("some_var 比 10 小.")
  else:                  # 这一句也是可选的
      print("some_var 就是 10.")
  ```

* for 循环可以遍历列表

  ```python
  """
  如果要打印出：
      dog 是哺乳动物
      cat 是哺乳动物
      mouse 是哺乳动物
  """
  for animal in ["dog", "cat", "mouse"]:
      print('{} 是哺乳动物'.format(animal))
  """
  'range(数字)' 会返回一个数字列表，
  这个列表将包含从零到给定的数字。
  如果要打印出：
      0
      1
      2
      3
  """
  for i in range(4):
      print(i)
  ```

* while 循环会一直继续，直到条件不再满足。

  ```python
  """
  如果要打印出：
      0
      1
      2
      3
  """
  x = 0
  while x < 4:
      print(x)
      x += 1  # 这是 x = x + 1 的简写方式
  ```

* 跳过或终止循环

  ```python
  continue    #跳过循环的这一次执行，进行下一次的循环操作
  break       # 停止执行整个循环
  ```

* 使用 try/except 代码块来处理异常

  ```python
  try:
      # 使用 raise 来抛出一个错误
      raise IndexError("This is an index error")
      # 抛出一个索引错误：“这是一个索引错误”。
  except IndexError as e:
      pass    # pass 只是一个空操作。通常你应该在这里做一些恢复工作。
  except:
      pass
  else:
      pass
  finally:
      pass
  ```

  >try -> 异常 -> except -> finally
  >
  >try -> 无异常 -> else -> finally

## 函数

* 使用 def 来创建新函数

  ```python
  def add(x, y):
      print("x is {} and y is {}".format(x, y))
      return x + y    # 使用 return 语句来返回值
  ```

* 调用函数并传入参数

  ```python
  add(5, 6) #=> 输出 "x is 5 and y is 6" 并且返回 11
  ```

* 调用函数的另一种方式是传入关键字参数

  ```python
  add(y=6, x=5)   # 关键字参数可以以任意顺序传入
  ```

* 你可以定义一个函数，并让它接受可变数量的定位参数。

  ```python
  def varargs(*args):
      return args

  varargs(1, 2, 3) #=> (1,2,3)
  ```

* 你也可以定义一个函数，并让它接受可变数量的关键字参数。

  ```python
  def keyword_args(**kwargs):
      return kwargs
  ```

* 我们试着调用它，看看会发生什么：

  ```python
  keyword_args(big="foot", loch="ness") #=> {"big": "foot", "loch": "ness"}
  ```

* 你还可以同时使用这两类参数，只要你愿意：

  ```python
  def all_the_args(*args, **kwargs):
      print(args)
      print(kwargs)

  all_the_args(1, 2, a=3, b=4)
  """
    输出:
      (1, 2)
      {"a": 3, "b": 4}
  """
  ```

* 在调用函数时，定位参数和关键字参数还可以反过来用。使用 `*` 来展开元组，使用 `**` 来展开关键字参数。

  ```python
  args = (1, 2, 3, 4)
  kwargs = {"a": 3, "b": 4}
  all_the_args(*args) # 相当于 all_the_args(1, 2, 3, 4)
  all_the_args(**kwargs) # 相当于 all_the_args(a=3, b=4)
  all_the_args(*args, **kwargs) # 相当于 all_the_args(1, 2, 3, 4, a=3, b=4)
  ```

* 函数在 Python 中是一等公民

  ```python
  def create_adder(x):
      def adder(y):
          return x + y
      return adder

  add_10 = create_adder(10)
  add_10(3) #=> 13
  ```

* 还有匿名函数

  ```python
  (lambda x: x > 2)(3) #=> True
  ```

* 还有一些内建的高阶函数

  ```python
  list(map(add_10, [1,2,3])) #=> [11, 12, 13]
  # map 函数会把函数 add_10，作用与列表中的每一个元素上，返回运算的结果
  list(filter(lambda x: x > 5, [3, 4, 5, 6, 7]))
  #=> [6, 7] # filter 函数会将 lambda 函数，作用于列表的每一个元素上，返回为True的元素
  ```

## 类

* 我们可以从对象中继承，来得到一个类。

  ```python
  class Human(object):
      # 下面是一个类属性。它将被这个类的所有实例共享。
      species = "H. sapiens"

      # 基本的初始化函数（构造函数）
      def __init__(self, name):
          # 把参数赋值为实例的 name 属性
          self.name = name

      # 下面是一个实例方法。所有方法都以 self 作为第一个参数。
      def say(self, msg):
          return "{}: {}".format(self.name, msg)

      # 类方法会被所有实例共享。
      # 类方法在调用时，会将类本身作为第一个参数传入。
      @classmethod
      def get_species(cls):
          return cls.species

      # 静态方法在调用时，不会传入类或实例的引用。
      @staticmethod
      def grunt():
          return "*grunt*"
  ```

* 实例化一个类

  ```python
  i = Human(name="Ian")
  print(i.say("hi"))     # 打印出 "Ian: hi"

  j = Human("Joel")
  print(j.say("hello"))  # 打印出 "Joel: hello"
  ```

* 调用我们的类方法

  ```python
  print(i.get_species()) #=> "H. sapiens"
  ```

* 修改共享属性

  ```python
  print(Human.species) #=> "H. species"
  Human.species = "H. chinaman"
  print(i.get_species()) #=> "H. species"
  print(j.get_species()) #=> "H. species"
  ```

* 调用静态方法

  ```python
  print(Human.grunt()) #=> "*grunt*"
  ```

## 模块

* 你可以导入模块

  ```python
  import math
  print(math.sqrt(16)) #=> 4
  ```

* 也可以从一个模块中获取指定的函数

  ```python
  from math import ceil, floor
  print(ceil(3.7))  #=> 4.0
  print(floor(3.7)) #=> 3.0
  ```

* 你可以从一个模块中导入所有函数，

  >警告：不建议使用这种方式

  ```python
  from math import *
  ```

* 你可以缩短模块的名称

  ```python
  import math as m
  print(math.sqrt(16) == m.sqrt(16)) #=> True
  ```

* Python 模块就是普通的 Python 文件。

  >你可以编写你自己的模块，然后导入它们。
  >模块的名称与文件名相同。
  >你可以查出一个模块里有哪些函数和属性

  ```python
  import math
  print(dir(math))
  ```

* 随机数模块

  ```python
  # random 模块有大量的函数用来产生随机数和随机选择元素。
  import random

  # 要想从一个序列中随机的抽取一个元素，可以使用 random.choice()
  values = [1, 2, 3, 4, 5, 6]
  print(random.choice(values))

  # 为了提取出N个不同元素的样本用来做进一步的操作，可以使用 random.sample()
  print(random.sample(values, 2))

  # 生成随机整数，请使用 random.randint()
  print(random.randint(0,10))

  # 为了生成0到1范围内均匀分布的浮点数，使用 random.random()
  print(random.random())
  ```
