
# 语法基础
## C1 JavaScript简介
- 嵌入到HTML页面中的编程语言，由浏览器一边解释一边执行
- 引入
    - 外部js, `<script src="a.js" ></script>`, 与CSS不同的时, js既可以在head中引入, 又可以在body中引入
    - 内部js, 放在script中间的js代码
    - 元素属性js, 在元素的事件属性中直接编写js或调用函数
- document.write(): 在页面输出一个内容
- alert(): 弹出一个对话框
## C2 语法基础
- 变量与常量
    - 标识符, [a-zA-Z0-9_$], 数字不开头
    - var 变量名=值;
    - var 大写常量名=值;
- 数据类型
    - 基本数据类型, 数字, 字符串, 布尔值, 未定义值, 空值
    - 引用数据类型, 对象(数组是对象的一种)
    - 数字不分整型和浮点型
    - 字符串用单引号or双引号括起来
    - 布尔值只有true/false
    - 未定义值, 声明了但是没赋值, 不知道什么类型, 未定义, undefined
    - var n = null; 空值, 没给它分配内存空间
- 运算符
    - num+num=num, str+str=str, num+str=str
    - 其他运算符和Java的没啥区别
- 类型转换
    - 字符串转数字, Number转纯数字, parseInt和parseFloat接收首字母是数字的串
    - 数字转字符串, 与空串相加, toString()
- 转义字符和注释也都和Java一样
## C3 流程控制
- 同Java
## C4 认识函数
- 定义函数的关键字, function
- js的函数调用和Java有区别, 4种调用方式
    - 直接调用
    - 在表达式中调用, 返回值参与表达式运算
    - 在超链接中调用, a元素的href="javascript: 函数名", 点击就调用
    - 在事件中调用, 比如单击按钮, 写在按钮的事件属性里
- 嵌套函数, 闭包, 都是js有的
## C5 字符串对象
- 内置对象, 字符串对象String, 数组对象Array, 日期对象Date, 数值对象Math
- str.length
- str.toLowerCase(), toUpperCase()
- str.charAt(n)
- str.substring(begin, end), 半开半闭
- str.replace(子串, 想要替换子串的串)
- str.replace(正则表达式, 替换串)
- str.split("分隔符"), 返回一个数组
- str.indexOf(串), str.lastIndexOf(串), 不存在返回-1
## C6 数组对象
- var arr = new Array(a1, a2, ..., an);
- var arr = [a1, a2, ..., an]; 语法糖
- arr.length
- arr.slice(begin, end), 切片[begin, end)
- arr.unshift(a1, a2), arr.push(a3, a4), 在开头添加和在结尾添加
- arr.shift(), arr.pop(), 在开头/结尾删一个
- arr.sort(自定义函数名),
- arr.reverse(), 颠倒
- arr.join("连接符"), 把arr连接成str
## C7 时间对象
# 核心技术
## C9 DOM基础
- DOM，全称是“Document Object Model（文档对象模型）”，它是由W3C定义的一个标准
- 树型结构, 我们在操作元素时，其实就是把这个元素看成一个对象，然后使用这个对象的属性和方法来进行相关操作
- nodeType, 元素节点1, 属性节点2, 文本节点3
- 获取元素, getElementBy
    - Id, getElementById（　）获取的是一个DOM对象，我们在给变量命名的时候，习惯性地以英文“o”开头，以便跟其他变量区分开，这可以让我们一眼就看出这是一个DOM对象
    - TagName, 通过标签名获取, 返回多个元素, 注意有s, getElementsByTagName()
    - ClassName, 也是s, 
    - querySelector[All]("选择器")
    - ByName, 表单元素有name
- document.title, document.body
- createElement()创建元素节点, createTextNode()创建文本节点
- a.appendChild(b), 让b成为a的子节点
- a.insertBefore(b, c), 在c前面插入b
- 动态DOM, 以实现动画效果
- a.removeChild(b)

## C10 DOM进阶
- HTML属性操作(对象属性), 使用js来操作一个元素的HTML属性
- class属性用className来代替, 因为class已经作为js的关键字了


## C11 事件基础


- 鼠标事件
    - onclick单击, 并不是只有按钮有, 任何元素都可以添加单击事件
    - onmouseover鼠标移入, onmouseout鼠标移出
    - onmousedown鼠标按下, onmouseup鼠标松开
- 键盘事件
    - onkeydown键盘按下, onkeyup键盘松开

- 表单事件
    - onfocus获取焦点, onblur失去焦点, 比如点文本框想输入东西, 文本框获取光标, 只有表单和超链接有焦点事件

## C12 事件进阶
- 事件监听器, 可以为同一个元素添加多个相同的事件
    - obj.addEventListener(type, fn, false)
    - type是个string, 事件类型, 比如"click", 不需要加on
    - fn是个函数名, 或者是个匿名函数
    - false表示事件冒泡阶段调用
    - ogj.removeEventListener(type, fn, false), 解绑
    - fn一定需要是函数名, 不能是匿名函数

- event对象, 一个事件对应一个event对象
    - event对象在IE8浏览器及以下版本还有一定的兼容性, 可能还需要采取“var e=e||window.event;”来处理
    - type事件类型
    - keyCode 键码值
    - shiftKey 是否按下Shift
    - ctrlkey 是否按下Ctrl
    - altKey 是否按下Alt
- this
    - 
## C13 window对象
- 一个窗口就是一个window对象，这个窗口里面的HTML文档就是一个document对象，document对象是window对象的子对象
- 对于window对象，无论是它的属性，还是方法，都可以省略window前缀
    - window.alert() -> alert()
- window.open(url, target), 返回一个窗口对象
    - url指的是新窗口的地址，如果url为空，则表示打开一个空白窗口。空白窗口很有用，我们可以使用document.write（　）往空白窗口输出文本，甚至输出一个HTML页面
    - target表示打开方式，它的取值跟a标签中target属性的取值是一样的，常用取值有两个：_blank和_self。当target为“_blank（默认值）”时，表示在新窗口中打开；当target为“_self”时，表示在当前窗口中打开
- alert("abc\n"), comfirm("abc\n")用户点确定返回true, 点取消返回false, prompt("abc\n")返回一个用户输入的字符串
