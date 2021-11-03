- 每多学一点知识，就少写一行代码
    - write less, do more

# C1 jQuery简介
- js -> js库, 
- 在三大框架（Vue、React、Angular）非常流行的今天，学习jQuery还有用吗？
- jQuery文档也是个不错的学习地址
- jQuery文件，就是一个“外部JavaScript文件”。所谓的安装jQuery，其实就是把这个外部JavaScript文件引入后，就可以使用jQuery语法了。
- 

## C2 基础选择器
- 在jQuery中, 基础选择器有以下3种: 基本选择器, 层次选择器, 属性选择器
- `$("选择器")`, 把CSS选择器套入进去就成了jQuery选择器

### 基本选择器
- 元素选择器, 元素名
- id选择器, #id名
- class选择器, .类名
- 群组选择器, 对几个选择器执行相同的操作

### 层次选择器
- 以一棵树的视角来看待一个html文件中的所有元素
- 后代选择器, `$("M N") = $(M).find(N)`, M的所有子节点中的N
- 子代选择器, `$("M>N") = $(M).children(N)`, M的相邻子节点中的N
- 兄弟选择器, `$("M~N") = $(M).nextAll(N)`, M后面的所有兄弟N
- 相邻选择器, `$("M+N") = $(M).next(N)`, M后面的兄弟N
    - $("li+li")使用的是相邻选择器，表示“选择li元素后面相邻的（下一个）li元素”。由于最后一个li元素没有下一个li元素，所以对于最后一个li元素，它是没有下一个li元素可以选取的。$("li+li").css("border-top","2px solid red")可以实现在两两li元素之间添加一个边框的效果

### 属性选择器
![1634518661(1).png](https://pic.rmb.bdstatic.com/bjh/981ca3e9c65c4d1c7167450a2bf466d2.png)

## C3 伪类选择器
- M:cond的格式

### "位置"伪类选择器
- 下标和数组一样从0计算
- M:eq(n), 选取M中的下标为n的元素
![1634519132(1).png](https://pic.rmb.bdstatic.com/bjh/7d487b71479f5e64ecc5b34fbb6efdcd.png)

### "子元素"伪类选择器
- M:nth-child(n), 位置从1开始, jQuery中的这个继承了CSS选择器的规范
- 适合用这个给列表的每个子项设置不同的样式

### "可见性"伪类选择器


## C6 事件基础
### 6.1 事件简介
- 事件主角
- 事件类型
- 事件过程
### 6.2 页面事件
- js中window.onload = function(){...} -> jQuery中ready事件$(document).ready(function(){...})
- jQuery的ready事件仅仅是DOM元素加载完成就可以执行，而JavaScript的onload事件在DOM元素加载完成后还需要等所有外部文件也加载完成才可以执行。
    - 很明显，jQuery的ready事件相对于JavaScript的onload事件来说，极大地提高页面的响应速度，有着更好的用户体验
- 四种写法之推荐写法, $(function(){...})
- 在JavaScript中，window.onload只能调用一次，如果多次调用，则只会执行最后一个, 但是在jQuery中，ready事件是可以多次执行的。从这里可以看出jQuery有非常良好的兼容性