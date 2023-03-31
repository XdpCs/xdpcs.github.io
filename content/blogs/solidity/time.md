---
title: "9-时间单位"
description: "Welcome to XdpCs’s blog!"
date: "2022-09-19"
tags: ["Solidity"]
showComments: true
---

## 基础知识

* `Solidity`中自带时间单位，它们分别是
    - `seconds`
    - `minutes`
    - `hours`
    - `days`
    - `weeks`
* 基本换算关系如下：
    - `1` == `1 seconds`
    - `1 minutes` == `60 seconds`
    - `1 hours` == `60 minutes`
    - `1 days` == `24 hours`
    - `1 weeks` == `7 days`
* 秒为缺省时间单位

## 例子

[例子](https://github.com/XdpCs/Solidity-Learning/blob/master/contracts/Time/Time.sol)

该例子是判断当前时间是否大于合约部署后的一分钟

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Time {
    uint public start;
    constructor(){
        start = block.timestamp;
    }

    function judge() public view returns (bool) {
        if (block.timestamp >= start + 1 minutes)
            return true;
        return false;
    }
}
```

## 程序解析

```solidity
 function judge() public view returns (bool) {
    if (block.timestamp >= start + 1 minutes)
        return true;
    return false;
}
```

* 这些时间单位是不能直接用在变量后面
* 想要使用，必须将输入变量换算为时间
