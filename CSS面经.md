# articleStudy/CSS
知识点总结
## CSS 面试知识点总结

本部分主要是笔者在复习 CSS 相关知识和一些相关面试题时所做的笔记，如果出现错误，希望大家指出！

### 目录

#### 1.样式优先级权重
```
<style>
.main{
color:blue
}
span{
color:green
}
</style>
<div style="color:red !important"
class=""main"">
<span>123</span>
</div>
```
```
首先，优先级顺序：
！important>行内样式>id选择器>类选择器>标签选择器>通配符>继承
在这道题目：
对于span有两种种影响样式的方式，
 (1)继承自父div的color
     而对于color而言，它受到类选择器和一个内联样式的影响，并且在这个内联样式中又有一个！important，最为最高级影响 (！important>内联>类选择器)，这就使得div的颜色为red,而作为其子元素的span也应该继承自父元素的color
 (2)标签选择器span
但比较这两种影响，（1）作为样式继承的优先级为0,（2）作为标签选择器的优先级为1，所以（2）的优先级以微弱优势高于（1），所以最终采用标签选择器定义的green
```
