python试题

1. 关于python的内存管理，下列说法错误的是

   1. 变量无须创建和赋值而直接使用。

2. 关于字符串下列说法错误的是

   1. 字符串以\0标志字符串的结束。
   2. 解析：以”\0”结尾是C/C++中存在，在python中不存在!!!!!!!!

3. a = range(100)，以下哪些操作是合法的？

   1. a[-1]
   2. a[2:13]
   3. a[::3]
   4. a[2-3]

4. 下面代码运行结果？  

   ```
   a = 1
   try:
       a += 1
   expect:
       a += 1
   else:
       a += 1
   finally:
       a += 1
   print a
   ```

   异常捕捉，try和except只执行一个，else和finally都要执行

5. 下列代码执行的结果是什么？

   ```
   x = 1
   def change(a):
   	x += 1
   	print x
   change(x)
   ```

   UnboundLocalError: local variable 'x' referenced before assignment

   即 change(a) 函数内的局部变量 x 在使用前未定义。

6. python中函数是对象，描述正确的事？

   1. 函数可以赋值给一个变量
   2. 函数可以作为元素添加到集合对象中
   3. 函数可以作为参数值传递给其他函数
   4. 函数可以当作函数的返回值

7. 下面哪个不是python合法的标志符 2

   1. int32 
   2. 40XL
   3. self
   4. name

8. python2与python3均不支持复数比较大小，ASCII码中小写字母>大写字母>数字

9. 所有标准对象均可以用于布尔测试，下列对象的布尔值是False:

   - None
   - False
   - 所有值为零的数：0（整型），（浮点型），0L（长整型），0.0+0.0j(复数) “”（空字符串）[ ](空列表) （）（空元祖）{}(空字典)

10. 下列正确的事

    ```
    kvps = { '1' : 1, '2' : 2 }
    theCopy = kvps.copy()
    kvps['1'] = 5
    sum = kvps['1'] + theCopy['1']
    print sum
    选择6
    
    kvps.copy(),相当于复制一份，原来的改变不影响复制后的，理解为独立的
    import copy
    theqian = copy.copy(kvps),这个是真正的浅拷贝，kvps内部对象变，theqian也会跟着变，kvps指向其它对象，theqian不变。
    例如：
    >>> import copy 
    >>> origin = [1, 2, [3, 4]] #origin 里边有三个元素：1， 2，[3, 4]
    >>> cop1 = copy.copy(origin)
    >>> origin[2][0] = "hey!"
    >>> origin 
    [1, 2, ['hey!', 4]] 
    >>> cop1
    [1, 2, ['hey!', 4]]
    theshen = copy.deepcopy(kvps),这个是真正的深拷贝，kvps怎么变，theshen不变。
    
    总结。
    a = object.copy() 等价于 b = copy.deepcopy(object),a和b一样
    copy.copy(object)是浅拷贝，相当于变量引用,等同于下面代码。
    a = [1,2,3]
    b = a
    a = [4,5,6]
    >>>b
    [1,2,3]
    c = b
    b[0] = 20
    >>>c
    [20,2,3]
    ```

11. 下列选择

    ```
    counter = 1 
    def doLotsOfStuff(): 
        global counter
        for i in (1, 2, 3): 
            counter += 1 
    doLotsOfStuff()
    print counter
    
    选择4
    ```

12. 有一段python的编码程序如下：urllib.quote(line.decode("gbk").encode("utf-16")),请问经过该编码的字符串的解码顺序是（ ）

    ```
    字符串编译的过程：gbk==>unicode==>utf16==>url解码
    字符串解码顺序为：url解码==>utf16==>unicode==>gbk
    ```

13. python my.py v1 v2 命令运行脚本，通过 from sys import argv如何获得v2的参数值? 

    ```
    sys.argv是传递给python脚本的命令行参数【字符串】列表
    argv[0]为该脚本自身路径，其余为命令行参数
    ```

14. 下面

    ```
    (python2) What gets printed by the code snippet below?()
    import math
    print math.floor(5.5)
    
    python2 5.0
    python3 5
    ```

15. 运行正确的排版应该为

    ```
    class Person:
        def __init__(self):
            pass
        def getAge(self):
            print __name__
    p = Person()
    p.getAge()
    
    以上代码作为脚本文件运行时（而不是作为模块被引用），将输出
    __main__，详情可参考官方文档：
    ```

16. Python中的复数

    虚部可以为j或者J

    实部和虚部都是浮点数

17. 下列代码运行结果是？ 

    ```
    a = 'a'
    print a > 'b' or 'c'
    c
    ```

18. Python中单下划线_foo与双下划线__foo与__foo__的成员，下列说法正确的是？

    ```
    _xxx 不能用’from module import *’导入  （相当于protected） 
    __xxx__ 系统定义名字   (系统内置的，比如关键字)
    __xxx 类中的私有变量名  （privated），所以更加不能使用from module import进行导入了
    ```

19. __new__和__init__的区别，说法正确的是？ 

    ```
    __new__是一个静态方法，而__init__是一个实例方法
    __new__方法会返回一个创建的实例，而__init__什么都不返回
    只有在__new__返回一个class的实例时，后面的__init__才能被调用
    当创建一个新实例时调用__new__，初始化一个实例时用__init__
    
    根据官方文档：
    __init__是当实例对象创建完成后被调用的，然后设置对象属性的一些初始值。
    __new__是在实例创建之前被调用的，因为它的任务就是创建实例然后返回该实例，是个静态方法。
    
    即，__new__在__init__之前被调用，__new__的返回值（实例）将传递给__init__方法的第一个参数，然后__init__给这个实例设置一些参数。
    ```

20. 解释型语言的特性有什么？

    1. 非独立
    2. 效率低





