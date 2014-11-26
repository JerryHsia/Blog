---
author: Jerry Hsia
title: 数据结构小记
excerpt:
layout: post
views:
  - 100
category:
  - 数据结构
tags:
  - 
post_format: [ ]
---

## 1 线性表

### 1.2 顺序存储结构与单链表结构比较

1.2.1 存储方式

- 顺序存储：用一段连续的存储单元依次存储数据元素
- 单链表：采用链式存储结构，用一组任意的存储单元存放元素

1.2.2 时间性能

- 查找

  - 顺序存储：O(1)

  - 单链表：O(n)

- 插入与删除

  - 顺序存储：O(n)
  
  - 单链表：O(1)
  
1.2.3 空间性能

- 顺序存储：需要预分配存储空间，分大了浪费，分小了容易溢出，元素个数受限

- 单链表：不需要分配存储空间，只要有就可以分配，元素个数不受限制


### 1.2 单链表

- 头结点：链表第一个节点
- 头指针：第一个节点的存储位置


### 1.3 静态链表

### 1.4 循环链表

### 双向链表