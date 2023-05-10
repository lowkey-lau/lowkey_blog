---
title: Solidity - 常用语法、变量
date: 2023-01-05 16:00:00

tags:
  - 区块链
  - Solidity
  - Web3

categories:
  - [区块链]

reward: true
comment: true
---

> 目前工作职责已经不局限于单纯的 web 开发了，既然已经踏上 `区块链` 这条大船，`智能合约` 当然得安排上，而我先入手 `以太坊` 的开发路线，使用 `solidity` 编写智能合约。

[Solidity 中文文档](https://solidity-cn.readthedocs.io/zh/master/)
[remix - 编写智能合约的在线软件](http://remix.ethereum.org)

<!-- more -->

---

# 最基础的范例

```solidity
contract test {
    uint256 num;

    function add(uint256 _num) public {
        num += _num;
    }
}
```

`contract` 代表将要创建一个 XXX 的合约
`test` 为自定义命名
`function xxx()` 代表智能合约里面的方法，智能合约是通过一个一个方法来实现逻辑的搭建的。
`public` 范例用了这个属性，代表了此方法所有人可用。

---

# 常用的数据类型

`address` 地址类型，此属性为区块链的独有属性
`string` 文本类型
`int` 数值类型，显示范围是-2\*\*255 到 2\*\*255 - 1
`uint` 无符号整数（指的正整数），最大是 2\*\*256 -1;
`bool` 布尔值，true 或 false
`bytes` 字节类型

---

# 常用的属性标签

## constructor

`构造函数 给合约创建初始值`

```solidity
uint256 _num;
bool _bool;

constructor {
  _num = 1;
  _bool = true;
}
```

## constant

`常量 不可更改`

```solidity
uint256 constant NUM; //表示NUM为一个常量，合约一启动就要定义好值，后续不可更改（常用于配置）;
```

## public

`可视范围 公开可见的`

```solidity
uint256 public num; //默认给num提供一个get()方法，可以通过外部调用提取数据。

function xxx() public {}; //表明此方法所有人都可调用。
```

## private

`私有属性，不能继承，不能重构`

```solidity
uint256 private num; //表示num只能在当前合约使用

function xxx() private {}; //表明此方法只能在当前合约使用
```

## external

`外部调用函数`

```solidity
function xxx() external {}; //表明此方法只能通过外部函数触发
```

## internal

`内部调用函数`

```solidity
function xxx() internal {}; //表明此方法只能通过内部函数触发
```

## view

`只读方法，能够读取局部变量的属性，读取链上信息必须使用`

```solidity
uint256 val = 666;

function xxx() view returns(uint256) {
  return val;
};
```

## pure

`纯函数 不能读不能写，不消耗gas，只能拥有局部变量，不对链上有任何的读写操作`

```solidity
function xxx(uint256 a, uint256 b) pure returns(uint256) {
  return a + b;
};
```

## payable

`定义此属性表明此变量或者方法可以接收主链币`

```solidity
address payable _address = '0xxxxxxxxx';

function xxx() payable {}
```

## modifier

`函数修改器，用于多个错误重复判断的东西`
`_;相当于让其他函数在修改器的后面运行`

```solidity
bool _bool = true;

modifier isTrue(){
    require(_bool, 'false');
    _;
}

function xxx() isTrue {
    doing. //如果条件通过即可继续运行此方法
}
```

## event 与 emit

```solidity
//Solidity 中，要定义事件，可以使用 event 关键字(在用法上类似于 function 关键字)。然后可以在函数中使用 emit 关键字触发事件。
//按照惯例，事件名称以大写字母开头，以区别于函数。
//之前是没有 emit 的，是用大写字母开头用以标识触发事件，但是经常容易与方法混淆，之前著名的以太坊硬分叉以太经典的 DAO 事件就是由这个导致的，所以就有了 emit


// 声明一个事件
event Deposit(address indexed _from, bytes32 indexed _id, uint _value);

// 触发事件
emit Deposit(msg.sender, _id, msg.value);
```

## indexed

`索引参数值，方便Web3使用topic[]来进行过滤筛选`

## memory 与 storage

`memory` 值类型
`storage` 引用类型

|            | storage                        | memory                         |
| ---------- | ------------------------------ | ------------------------------ |
| 储存的变量 | 函数外部声明的变量，即状态变量 | 函数内部声明的变量，即局部变量 |
| 存储的位置 | 区块链上，永久存在             | 内存中，运行完之后销毁         |
| 运行的位置 | 区块链网络上                   | 单个节点                       |
| 传递属性   | 指针传递                       | 值传递                         |

---

# function 内的常用方法

## addres(this)

`可以指向当前地址`

```solidity
function xxx(_address) onlyOwner {
  addres(this).transfer(_address); //此方法为合约的提取，一般需要加权限
}
```

## for 循环

```solidity
uint256[] ddd = [1, 2, 3];
uint256 txt = 0;

for (uint256 i = 0; i < ddd.length; i++) {
  if(i == 1) {
    continue;
  }else if(i == 2){
    txt += i;
    break;
  }
}

//txt: 2;
```

`continue` for 循环的时候跳过循环
`break` 满足条件直接跳出循环

---

## immutable

`部署的时候才使用`

---

# library

`modules 的概念，能重复使用方法的集合在一起`

---

# 继承

```solidity
//继承了单个
contract B is A {}

//继承了多个
contract B is (A, C) {}
```

## virtual、override

`继承中 表明这个方法是可以被重写的`

```solidity
//A合约
contract A {
  function xxx() virtual {} //virtual 表明这个方法是可以被重写的
  function func() {}
}

//B合约
contract B is A {
  function xxx() override {} //override 表明这个方法是重写的

  function test() {
    super.func(); //super，指向上级的方法
  }
}
```
