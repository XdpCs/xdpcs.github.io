---
title: "8-以太币单位"
description: "Welcome to XdpCs’s blog!"
date: "2022-09-18"
tags: ["Solidity"]
showComments: true
---

## 基础知识

* 以太币单位

|         单位          | Wei                       | Wei值     |
|:-------------------:|---------------------------|----------|
|         Wei         | 1                         | 1 Wei    |
|   Kwei (babbage)    | 1,000                     | 1e3 Wei  |
|   Mwei (lovelace)   | 1,000,000                 | 1e6 Wei  |
|   Gwei (shannon)    | 1,000,000,000             | 1e9 Wei  |   
| microether (szabo)  | 1,000,000,000,000         | 1e12 Wei |
| milliether (finney) | 1,000,000,000,000,000     | 1e15 Wei |
|        ether        | 1,000,000,000,000,000,000 | 1e18 Wei |

* 交易需要支付`ether`
* 在`Solidity`中，单位之间的换算是在数字后加上 `wei`，`gwei` 或 `ether` 来实现的
* 在`Solidity`中，后面没有单位，缺省为 `wei`
* 从`Solidity0.7.0`版本开始， `finney` 和 `szabo` 被移除了
* `gwei` 在`solidity 0.6.11`版本中添加，因此在`0.6.11`之前的版本中不可用

## 例子

[例子](https://github.com/XdpCs/Solidity-Learning/blob/master/contracts/EtherAndWei/EtherUnits.sol)

该例子是测试以太币的单位换算

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract EtherUnits {
    uint public oneWei = 1 wei;
    bool public isOneWei = 1 wei == 1;

    uint public oneEther = 1 ether;
    bool public isOneEther = 1 ether == 1e18;

    uint public oneGwei = 1 gwei;
    bool public isOneGwei = 1 gwei == 1e9;
}

```

## 程序解析

```solidity
uint public oneWei = 1 wei;
bool public isOneWei = 1 wei == 1;
```

* `1 wei` 等于 `1`，若没填写单位，默认是以`wei`为单位

```solidity
uint public oneEther = 1 ether;
bool public isOneEther = 1 ether == 1e18;
```

* `1 ether` 等于 `10^18 wei`

```solidity
uint public oneGwei = 1 gwei;
bool public isOneGwei = 1 gwei == 1e9;
```

* `1 gwei` 等于 `10^9 wei`

