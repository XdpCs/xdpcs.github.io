---
title: "7-读取和写入状态变量"
description: "Welcome to XdpCs’s blog!"
date: "2022-09-17"
tags: ["Solidity"]
showComments: true
---

## 基础知识

* 写入和更新状态变量需要发送一笔交易
* 读取状态变量是免费的，无需任何交易费用

## 例子

[例子](https://github.com/XdpCs/Solidity-Learning/blob/master/contracts/ReadAndWriteState/SimpleStorage.sol)

该例子是读写一个状态变量的例子

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint public num;

    function set(uint _num) public {
        num = _num;
    }

    function get() public view returns (uint) {
        return num;
    }
}
```

## 程序解析

```solidity
uint public num;
```

* 存储一个`uint`的状态变量

```solidity
 function set(uint _num) public {
    num = _num;
}
```

* 需要发送一笔交易才能写入状态变量

```solidity
function get() public view returns (uint) {
    return num;
}
```

* 读取状态变量时，不需要发送一笔交易
