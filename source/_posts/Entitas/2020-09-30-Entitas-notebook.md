---
title: Entitas笔记
---

### Code Generation [代码自动生成]

#### CodeGenerated的项目基本结构
在导入Entitas插件并配置好相关设置之后，在Unity面板中按下快捷键`Ctrl+Shift+G`得到下面截图这样的CodeGenerated项目结构。
看下来总共分为三个部分：`Game` `Input` `全局类`

![](https://cdn.jsdelivr.net/gh/longshilin/images/20200930170318.png)

其中，`Game`和`Input`文件夹结构简直太相似了，包含`Attribute`, `ComponentsLookup`, `Context`, `Entity`, `Matcher`。

`Contexts.cs`是全局的上下文，整个项目中就一个，可以通过`Contexts.sharedInstance`访问到，并管理所有的`Context`



>sealed和partial关键字的含义：
sealed关键字表示不能继承该类，对类代码的结构没有影响。
partial关键字允许将一个类拆分到多个文件中，编译后它们就会合并为一个类。