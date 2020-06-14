# articleStudy
知识点总结

## 一、事件委托
``` bush
1.事件流
首先要了解-> 事件捕获，事件冒泡
https://zhuanlan.zhihu.com/p/100831300
3 A1      ||       A1 1
2 B2 捕获 | |  冒泡 B2 2
1 C3      ||       C3 3  <--click  数字从上到下是console打印顺序
addEventListener("click", function(event){},true'捕获'||false'默认冒泡')
<span id="jump">https://segmentfault.com/a/1190000018089355</span>
[点击跳转-事件委托详解](#jump)
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
