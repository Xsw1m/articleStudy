# articleStudy
知识点总结
## HTML 面试知识点总结

本部分主要是笔者在复习 HTML 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录
* [1. 事件委托](#1-事件委托)
* [2. Vue数据双向绑定原理实现](#2-Vue数据双向绑定原理实现)
* [3. BFC/清除浮动](#3-BFC/清除浮动)

### 1. 事件委托
## 一、事件委托
['点击跳转-事件委托详解'](https://segmentfault.com/a/1190000018089355)
``` bush
1.事件流
首先要了解-> 事件捕获，事件冒泡
https://zhuanlan.zhihu.com/p/100831300
3 A1      ||       A1 1
2 B2 捕获 | |  冒泡 B2 2
1 C3      ||       C3 3  <--click  数字从上到下是console打印顺序
addEventListener("click", function(event){},true'捕获'||false'默认冒泡')

2.事件委托是利用事件的冒泡原理。事件代理”即是把原本需要绑定在子元素的响应事件（click、keydown......）委托给父元素，让父元素担当事件监听的职务。
window.onload = function(){
  console.log('开始')
  var div1 = document.getElementById('div1');
  var div2 = document.getElementById('div2');
  var div3 = document.getElementById('div3');
  // div1.addEventListener("click", function (event) {
  //   console.log('div1:', this.id, event)
  // }, true)
  // div2.addEventListener("click", function (event) {
  //   console.log('div1:', this.id, event)
  //   event.stopPropagation()
  // }, true)
  div3.addEventListener("click", function (event) {
    console.log('div1:', event.target, event.target.id, event.target.nodeName.toLocaleLowerCase())
  }, true)  // 获取事件的id 标签 进行判断并绑定函数 id就是具体绑定，nodeName标签div循环出新的也可以绑定
 }
// event.target 获取点击的事件 
 https://blog.csdn.net/qq_38128179/article/details/86293394
```
#### 2. Vue数据双向绑定原理实现
## Vue数据双向绑定
链接推荐：
[vue的双向绑定原理及实现](https://www.cnblogs.com/libin-1/p/6893712.html)
``` bush
1.实现一个监听器Observer，用来劫持并监听所有属性，如果有变动的，就通知订阅者。
2.实现一个订阅者Watcher，可以收到属性的变化通知并执行相应的函数，从而更新视图。
3.实现一个解析器Compile，可以扫描和解析每个节点的相关指令，并根据初始化模板数据以及初始化相应的订阅器。

4. 对象都有 object -> get set 属性 Object.defineProperty( ) 对get set 进行操作
```
#### 3. BFC/清除浮动
## BFC
[BFC/定义原理应用](https://blog.csdn.net/sinat_36422236/article/details/88763187)
```
BFC的布局规则
内部的Box会在垂直方向，一个接一个地放置。

Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠。

每个盒子（块盒与行盒）的margin box的左边，与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。

BFC的区域不会与float box重叠。

BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。

*(重要) 计算BFC的高度时，浮动元素也参与计算。

如何创建BFC
1、float的值不是none。
2、position的值不是static或者relative。
3、display的值是inline-block、table-cell、flex、table-caption或者inline-flex
4、overflow的值不是visible
```
