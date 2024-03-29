---
title: sessionStorage中的数据能共享吗？
date: 2023-11-26
tags: [sessionStorage]
---

## 前言

之前面试时，面试官有问到这么一个问题：

> sessionStorage 中的数据能共享吗？

<!-- more -->

众所周知，sessionStorage 是浏览器会话级别的存储机制，它只在单个浏览器标签页（tab）或窗口之间共享数据。每当用户打开一个新的标签页或窗口时，会话存储会被重新初始化，每个标签页或窗口都会有自己的独立的 sessionStorage。

所以我不假思索就答到：不能。

回头复盘想到面试官真的会问这么简单的问题吗，是不是其中有什么玄妙？

难道真的在某种情况下能共享数据吗？

于是带着这么问题去查找了相关资料

根据 MDN 的说法：

> 在新标签或窗口打开一个页面时会复制顶级浏览会话的上下文作为新会话的上下文

然后根据这点进行一些 demo 测试，

发现如果从本页面以新开页签的方式打开一个同域下的新页面，新开的页面会和之前的页面 ‘共享’ sessionStorage

## 总结

sessionStorage 不能在多个窗口或选项卡之间共享数据，但是，当通过 window.open 或链接打开新页面时，新页面会复制上一个页面的 sessionStorage
