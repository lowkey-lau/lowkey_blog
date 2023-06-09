---
title: Python学习笔记
date: 2023-05-09 15:00:00

tags:
  - python
  - 笔记

categories:
  - [笔记]

reward: true
comment: true
---

> 学习 **Python** 从我做起

<!-- more -->

---

## 定义简单类的方法

```python
class 类名:
    def 方法1(self, 参数列表):
       pass

    def 方法2(self, 参数列表):
       pass
```

> _注意：_ **类名** 的命名规则要符合 **大驼峰命名法**，第一个参数必须为 **self**

---

## 初始化方法

`__init__` 初始化方法，变量在这里初始化

```python
class A:
    def __init__(self, num2):
        self.num = 100
        self.num2 = num2


a = A(200)
print(a.num) #100
print(a.num2) #200
```

## 内置方法

`__del__` 代码全部执行完运行此方法

`__str__` 制定输出信息

```python
class A:
    def __init__(self, name):
        self.name = name
        print('name is %s' % name)

    def __del__(self):
        print('end')

    def __str__(self):
        print('666')


a = A('cat')
print(a.name) #cat
print(a) #666
```

## 私有属性和方法

```python
class A:
    def __init__(self):
        self.num1 = 100
        self.__num2 = 200 #私有

    def test(self):
        print('test')

    def __test(self):
        print('test')

a = A()
print(a.num1) #100
print(a.__num2) #报错
a.test() #test
a.__test() #报错
```

## 单继承

```python
class A:
    def test(self):
        print('test')

class B(A):
    def run(self):
        print('run')

b = B()
b.test() #test
b.run() #run
```

## 重写

> 具体实现即直接写一个同名方法即可实现

```python
class A:
    def test(self):
        print('test')

class B(A):
    def test(self):
        print('run')

b = B()
b.test() #run
```

## 扩展父类方法

> **super()** 可以使用父类的方法

```python
class A:
    def test(self):
        print('test')

class B(A):
    def test(self):
        print('run')
        super().test()

b = B()
b.test() #run #test
```

## 多继承

```python
class A:
    def test1(self):
        print('test1')

class B:
    def test2(self):
        print('test2')


class C(A, B):
    def test3(self):
        print('test3')

c = C()

c.test1() #test1
c.test2() #test2
c.test3() #test3
```

> _注意：_ 尽量不要写同样的方法名，否则使用的时候会按先后顺序调用

## 多态

> 不同的 **子类对象** 调用相同的 **父类方法**，产生不同的执行结果

```python
class Dog(object):
    def __init__(self, name):
        self.name = name

    def game(self):
        print('%s 正在玩耍' % self.name)


class Xiaotianquan(Dog):
    def game(self):
        print("%s 飞到天上去" % self.name)
        super().game()


class Person(object):
    def __init__(self,name) -> None:
        self.name = name

    def game_with_dog(self, dog):
        print('%s 和 %s 玩耍' % (self.name, dog.name) )

        dog.game()


wangcai = Xiaotianquan('旺财')
xiaoming = Person('小明')
xiaoming.game_with_dog(wangcai)
```

## 类

> 类是一个特殊的对象

- **类属性** 就是给 **类对象** 种定义的 **属性**
- 通常用来记录 **与这个类相关** 的特征
- **类属性** 不会用于记录 **具体对象** 的特征

```python
class Tool(object):
    count = 0

    def __init__(self, name):
        self.name = name
        Tool.count += 1


a = Tool('锤子')
b = Tool('斧头')

print(Tool.count)
```

## 类方法

> **@classmethod** 是必带的
>
> 方法的第一个 **参数** 一定是 **cls** `class`的缩写，**哪一个类** 调用的方法，方法内的 class 就是 **哪一个类的引用**

```python
@classmethod
def 类方法(cls):
    pass
```

## 单例

`__new__` 创建对象时，new 方法会被自动调用

```python
class Test:
    instance = None

    def __new__(cls):
        print('创建对象，分配空间')

        if cls.instance == None:
            cls.instance =  super().__new__(cls)

        return cls.instance

test1 = Test()
print(test1) #...456
test2 = Test()
print(test2) #...456
```

## 异常

##### `捕获异常` 处理方法时捕获错误信息

**Exception** 捕获所有异常错误

```python
try:
    num = int(input('请输入一个整数：'))
    result = 8 / num
except ZeroDivisionError:
    print('除0错误')
except ValueError:
    print('请输入正确的整数')
    # 捕获所有错误类型
except Exception as result:
    print('未知错误 %s' % result)
else:
    print('正确输入，结果为 %s' % result)
finally:
    print('无论是否有异常，都会执行次代码')
```

**异常的传递**

```python
def demo1():
    return int(input('输入整数：'))

def demo2():
    return demo1()

try:
    print(demo2())
except Exception as result:
    print('未知错误 %s' % result)
```

**抛出 raise 异常**

```python
def input_password():
    pwd = input("请输入密码：")

    if len(pwd) >= 8:
        return pwd

    print('主动抛出异常')
    ex = Exception('密码长度不够')
    raise ex

try:
    print(input_password())
except Exception as result:
    print(result)
```

