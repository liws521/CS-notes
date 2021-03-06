# Meta
- 从0到1系列, 前端开发路线最好的教程之一, 这本是入门之作, 也是写的几乎最好的入门之作(这也有一部分前端入门框架比较清晰的原因), 几乎不需要什么前置基础知识, 不过具备一定的英语基础更好, 建议看这个之前可以先多熟悉一下Markdown, 用Markdown记笔记极致体验, 了解了Markdown后再看这本书就level 0了.
- 而且作者的学习理念我很喜欢, 对于初学者来说，千万别想着精通了一门技术，再去精通另一门技术, 只有“通”十行才可能做到“精”一行, 我不是做前端的, 但是多对其他领域通一通终归是有益的, 不要报着吹毛求疵的心, 完美是幸福的敌人.
- 学习过程中的一个重要问题就是记忆的压力, 尽管作者已经尽可能的告知哪些在开发中常用, 哪些无需记忆, 但常用的罗列下来还是数量不菲. 计算机的学习从来不是靠头脑记忆, 计算机是一门"做中学"学科, 不需要把知识点背下来再动手, 而是先去做, 忘了一个查一个, 才最符合记忆曲线.
- 这里可能会涉及到一个疑问, "既然我能在不会一个东西的时候去查, 那我为什么还要这种系统的读书学习过程呢?" 在这里给出一份解答, 我们对知识的掌握, 分为已知, 对未知的已知, 对未知的未知, 也就是说有一些知识我们是不知道我们不知道的, 对于这部分我们往往无能为力, 所以系统读书学习上课的过程, 就是尽可能的将对未知的未知转化为对未知的已知, 我们可以记不下来具体的语句怎么写, 但要知道有这么一个东西可以解决这样的问题, 查询的时候有所方向, 这也和前些年主流的"无需记忆知识, 只需记忆知识存储的位置"观点有相似之处, 但还是有所不同的, 我的CS方法论最终是需要记忆知识的, 只不过是通过一次一次"用-学-用"反馈进行记忆, 而非大块记忆, 也并非前述观点的只记忆知识的位置.
- 在Mac下取名`从0到1: HTML+CSS快速入门`, 从Win端git pull时出现invalid path error, 因为是跨系统工作, 所以对文件命名时还是尽量注意一点, 英文优先于汉字, 不要使用特殊符号
## 后序学习顺序
- 《从0到1：HTML+CSS快速上手》→《从0到1：CSS进阶之旅》→《从0到1：JavaScript快速上手》→《从0到1：jQuery快速上手》→《从0到1：HTML5+CSS3修炼之道》→《从0到1：HTML5 Canvas动画开发》→未完待续
- 1．仿照百度首页，自己动手还原出来。说明：模仿还原网站是初学者最佳的实践方式，而百度首页往往是最适合初学者练习的第一个页面
- 2．打造一个属于自己的博客网站。
- 前言
    - 如果你需要的不是大而全，而是恰到好处的前端开发教程，那么不妨试着看一下这本书
    - [绿叶学习网](www.lvyestudy.com)

# HTML基础
## C1 HTML简介
- 前端技术简介
- 网页制作, 静态网页, 工具还是Flash等旧三剑客
- 前端开发, 新三剑客
    - HTML，全称是“Hyper Text Markup Language”（超文本标记语言），HTML是一门描述性标记语言
        - <标签符>内容</标签符>
    - CSS，即“Cascading Style Sheets”（层叠样式表），是用来控制网页外观的一种技术。
    - JavaScript是什么？JavaScript是一种嵌入到HTML页面中的脚本语言，由浏览器一边解释一边执行
    - “HTML用于控制网页的结构，CSS用于控制网页的外观，而JavaScript控制着网页的行为, HTML建房子, CSS装修, JS开灯
- 后端开发, 与服务器进行交互
- 学习路线, HTML->CSS->JS->jQuery->HTML5->CSS3->ES6->移动Web->Vue.js
- 对于初学者来说，千万别想着精通了一门技术，再去精通另一门技术, 只有“通”十行才可能做到“精”一行
## C2 开发工具
- 通过软件等图形界面开发网页, no!
    - 你学到的根本就不是技术，而只是软件操作
    - 可读性和可维护性，是Web开发中极为重要的两个东西, 点点点点出来的网页这两点很差
- VSCode yyds
## C3 基本标签
- `<!--注释-->`
- 标签和元素是一个概念, 叫什么都行
### html结构
    - 文档声明`<!DOCTYPE html>`
    - html标签对, head标签对, body标签对
### head的子标签
- title, 定义网页的标题, 这个标题不是文章的标题 而是显示在浏览器栏目的那个标题
- meta, meta标签一般用于定义页面的特殊信息，如页面关键字、页面描述等。这些信息不是提供给用户看的，而是提供给搜索引擎蜘蛛（如百度蜘蛛、谷歌蜘蛛）看的。简单地说，meta标签就是用来告诉“搜索蜘蛛”这个页面是做什么的。
    - name属性, keywords and description 为常用值
    - http-equiv属性, 定义网页所使用的编码，定义网页自动刷新跳转, 这里自己动手试了一下, 页面跳转很舒服
    - `<meta charset="utf-8" />`的作用是防止页面出现乱码，在每一个HTML页面中，我们都要加上这句代码。此外这一句必须放在title标签以及其他meta标签前面，这一点大家要记住
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8"/>
        <meta http-equiv="refresh" content="6;url=http://www.lvyestudy.com"/>
    </head>
    <body>
        <p> 这个页面将在6秒后跳转到绿叶学习网</p>
    </body>
</html>
```
- style, style标签用于定义元素的CSS样式，在HTML中不需要深入研究，等学到了CSS时我们再详细介绍
- script, 在HTML中，script标签用于定义页面的JavaScript代码，也可以引入外部JavaScript文件
- link, 在HTML中，link标签用于引入外部样式文件（CSS文件）
- base, 毫无意义
## C4 文本
- 不是“会动”的页面就叫动态页面。静态页面和动态页面的区别在于是否与服务器进行数据交互
- h1-h6六级标题, 段落标签p, 换行标签`<br/>`(自闭和标签)
- 粗体标签：strong、b, 斜体标签：i、em、cite, 上标标签：sup, 下标标签：sub, 中划线标签：s, 下划线标签：u, 大字号标签：big, 小字号标签：small
    - 上述标签, 记strong, em, sup, sb即可, 其他的用CSS实现
- `<hr/>`水平线
- div, 在HTML中，我们可以使用“div标签”来划分HTML结构，从而配合CSS来整体控制某一块的样式
- 自闭和标签, 单个出现, 自己就是一个整体, 一般标签, 成对出现
- 块元素, 在HTML中，块元素在浏览器显示状态下将占据整一行，并且排斥其他元素与其位于同一行。一般情况下，块元素内部可以容纳其他块元素和行内元素
    - h, p, div, hr, ol, ul .etc
- 行内元素, 行内元素可以与其他行内元素位于同一行, 行内元素内部可以容纳其他行内元素，但不可以容纳块元素
    - strong, em, a, span .etc
- 空格, 代码中的空格无效, `&nbsp;`, 一个汉字约等于3个nbsp
    - 除此之外还有很多特殊符号都可以通过这种代码实现, 感兴趣可以查一查
## C5 列表
- 有序列表, ol, li, 默认数字, type属性该成字母
- 无序列表, ul, li, 开发中用的最多
- 定义列表, dl标记和/dl标记分别定义了定义列表的开始和结束，dt标签用于添加要解释的名词，而dd标签用于添加该名词的具体解释
## C6 表格
- 表格：table标签。行：tr标签。单元格：td标签
- 表格标题caption, 表头单元格th
- thead、tbody和tfoot把表格划分为3部分：表头、表身、表脚, 更好的配合CSS分块控制
- 合并行rowspan, 合并列colspan
## C7 图片
- img标签, 三个属性
    - src
    - alt属性用于图片描述，这个描述文字是给搜索引擎看的。当图片无法显示时，页面会显示alt中的文字。
    - title属性也用于图片描述，不过这个描述文字是给用户看的。当鼠标指针移到图片上时，会显示title中的文字
- 图片格式
    - 位图
        - 位图，又叫作“像素图”，它是由像素点组成的图片。对于位图来说，放大图片后，图片会失真；缩小图片后，图片同样也会失真。
        - 在实际开发中，最常见的位图的图片格式有3种（可以从图片后缀名看出来）：jpg（或jpeg）、png、gif。深入理解3种图片适合在哪种情况下使用，在前端开发中是非常重要的
        - jpg格式可以很好地处理大面积色调的图片，适合存储颜色丰富的复杂图片，如照片、高清图片等。此外，jpg格式的图片体积较大，并且不支持保存透明背景
        - png格式是一种无损格式，可以无损压缩以保证页面打开速度。此外，png格式的图片体积较小，并且支持保存透明背景，不过不适合存储颜色丰富的图片
        - gif格式的图片效果最差，不过它适合制作动画。实际上，小伙伴们经常在QQ或微信上发的动图都是gif格式的
        - 这里来总结一下：如果想要展示色彩丰富的高品质图片，可以使用jpg格式；如果是一般图片，为了减少体积或者想要透明效果，可以使用png格式；如果是动画图片，可以使用gif格式
    - 矢量图
        - 矢量图，又叫作“向量图”，是以一种数学描述的方式来记录内容的图片格式。举个例子，我们可以使用y=kx来绘制一条直线，当k取不同值时可以绘制不同角度的直线，这就是矢量图的构图原理
        - 矢量图最大的优点是图片无论放大、缩小或旋转等，都不会失真。最大的缺点是难以表现色彩丰富的图片
        - 矢量图的常见格式有“.ai”“.cdr”“.fh”“.swf”。其中“.swf”格式比较常见，它指的是Flash动画，其他几种格式的矢量图比较少见，可以忽略
    - 位图的组成单位是“像素”，而矢量图的组成单位是“数学向量”
    - 位图受分辨率影响，当图片放大时会失真；而矢量图不受分辨率影响，当图片放大时不会失真
## C8 超链接 hyperlink
- `<a href="链接地址“>文本或图片</a>`
- target属性, _blank值: 在新窗口打开链接
- 外部链接, 内部链接(同一网站的另一html文件), 锚点链接 #abc, 跳到id为abc的标签位置
## C9 表单
- form标签, 各种表单标签放在其内部
    - 一些属性, name表单名称, method提交方式, action提交地址, target打开方式, enctype编码方式
    - method, get的安全性较差，而post的安全性较好。所以在实际开发中，大多数情况下我们都是使用post
- input标签, `<input type="表单类型" />`
    - text单行文本框
        - value默认值, size长度, maxlength最大字符数
    - password密码文本框, 属性同上
        - 密码文本框只能使周围的人看不见你输入的内容是什么，实际上它并不能保证数据的安全。为了保证数据安全，我们需要在浏览器与服务器之间建立一个安全连接，不过这属于后端技术，这里了解一下就行
    - radio单选框, name组名, value取值, checked默认勾选
        - 组名相同的几个单选框, 彼此互斥
        - 规范写法 `<label><input type="raido" name="sex" value="男“ />男</label>` 用一组label把input和后面的文字内容关联起来
    - checkbox复选框, 属性同上, 可以同时有多个选项被选中
    - button普通按钮, submit提交按钮, reset重置按钮
        - 普通按钮一般情况下都是配合JavaScript来进行各种操作的
        - 提交按钮一般都是用来给服务器提交数据的
        - 重置按钮一般用来清除用户在表单中输入的内容
    - file, 文件上传
- 多行文本框不用input, 用textarea
    - `<textarea rows="2" cols="3" value="abc">默认内容</textarea>`
- select+option, 下拉列表, 
    - select
        - multiple属性, 允许多选, Ctrl+鼠标左键进行多选
        - size, 同时显示几个
    - option
        - selected是否选中
        - value选项的值
- 表单元素不一定都要放在form标签内。对于要与服务器进行交互的表单元素，必须放在form标签内才有效。如果表单元素不需要与服务器进行交互，那就没必要放在form标签内
## C10 框架
- 在HTML中，我们可以使用iframe标签来实现一个内嵌框架。内嵌框架，是指在当前页面再嵌入另外一个网页

# CSS基础
- `/*CSS注释*/`
## C11 CSS简介
- CSS2.1 + CSS3
- CSS引入方式
    - 外部样式表是最理想的CSS引入方式。在实际开发中，为了提升网站的性能速度和可维护性，一般都会使用外部样式表。所谓的外部样式表，指的是把CSS代码和HTML代码单独放在不同文件中，然后在HTML文件中使用link标签来引用CSS文件。
        - `<link rel="stylesheet" type="text/css" href="my_path" />`
    - 内部样式表，指的是把HTML代码和CSS代码放到同一个HTML文件中。其中，CSS代码放在style标签内，style标签是放在head标签内部的, `<style type="text/css">`
    - 行内样式表与内部样式表类似，也是把HTML代码和CSS代码放到同一个HTML文件。但是两者有着本质的区别：内部样式表的CSS是在“style标签”内定义的，而行内样式表的CSS是在“标签的style属性”中定义的
## C12 CSS选择器
- 元素的id和class, 同一页面id各不相同, class把一些归类
- 元素选择器, id选择器(#), class选择器(用.)
- 后代选择器, 群组选择器
## C13 字体样式
- font-family字体类型, 默认宋体, 可以指定多个字体, 电脑没安装前面的就用后面的, font-family: 字体1,字体2,字体3;
- font-size:像素值; 字体大小, 以px为单位
- font-weight:bold; 字体粗细, bold是较粗
- font-sytle, 控制斜体
- color:颜色值; 填关键字或十六进制RGB, 字体颜色
## C14 文本样式
- text-indent:像素值; 首行缩进, 设置像素值为font-size的2倍就能做到空2个字符了
- text-align:取值; 水平对齐, 取值center居中对齐
- text-decoration:underline; 装饰, 控制上下中划线, 用HTML也能做划线, 但前端开发中外观用CSS来做, 遵守结构和样式分类的原则, 提高代码的可读性and可维护性.
    - 还可以用none值去除超链接a自带的下划线
- text-transform:uppercase; 大小写转换, capitalize是首字母大写
- line-height:像素值; 行高
- letter-spacing:像素值; 字母间距, 汉字间距
- word-spacing:像素值; 单词间距, 只针对英文单词
## C15 边框样式
- 几乎所有的元素都可以定义边框
- border-width:像素值; 边框宽度
- border-style:solid; 边框外观, 实线虚线
- border-color:red; 边框颜色, 关键字or十六进制RGB
- 简写 border:1px solid red;
- 上边框border-top, 下border-bottom, 左border-left, 右border-right, 单独设置局部的一条边, 用法同整体边框border一样
## C16 列表样式
- list-style-type, 控制ol或ul, 有时用none去除自带的样式
- list-style-image:url(图片路径); 用图片来代替列表项符号, 这个可能很好看(花里胡哨)
    - 一般情况下我们都不会用liststyle-image属性来实现，而是使用更为高级的iconfont图标技术来实现，这个我们在本系列的《从0到1：CSS进阶之旅》这本书中再详细介绍
## C17 表格样式
- caption-side:bottom; 把表格标题放下面
- border-collapse:collapse; 去除单元格空隙
- border-spacing:像素值; 表格边框间距
## C18 图片样式
- width, height, 像素值
- border:1px solid reg; 图片边框
- text-align:center/left/right; 图片水平对齐
- vertical-align:top/bottom/middle/baseline; 图片垂直对齐
- float:left/right; 图文混排, 字体环绕
## C19 背景样式
- background-color:颜色; 背景颜色
- background-image:url(图片路径); 
- background-repead:repeat-x; div能放好几个图片的时候如何重复
- background-position:2px 3px; 从左上角为原点, 2,3 位置放图片, 也可以用关键字
- background-attachment:scroll; 随元素滚动, 或者fixed固定不动.
## C20 超链接样式
- 超链接伪类, a:link未访问, a:visited访问后, a:hover鼠标经过, a:active鼠标单击激活
    - 按顺序写, love-hate
- 任意元素:hover{}, 定义该元素在鼠标经过的样子
- 鼠标样式
    - 浏览器鼠标样式, cursor:default/pointer/text;
    - 自定义鼠标样式, cursor:url(图片地址), 属性值; 一般是.cur后缀名的图片, 搜一搜
## C21 盒子模型
- 所有的元素都可以看成一个盒子
![1634094037(1).png](https://pic.rmb.bdstatic.com/bjh/9ff6c58b4fea41c7cbb3ccb4d58f8e97.png)
- 内容区content, width/height/overflow属性
    - 只有块元素才可以设置width和height，行内元素是无法设置width和height的
- 内边距padding
- 外边距margin, "负margin技术"
- 边框border
- padding:1px 2px 3px 4px; 上右下左
- margin也是上右下左
- 使用浏览器控制台辅助开发，是前端开发必备的一项基础技能
## C22 浮动布局
- 正常文档流, 通过浮动float:left/right; 脱离正常文档流, 达到浮动布局的效果
- clear:both; 清除浮动
## C23 定位布局
- CSS定位使你可以将一个元素精确地放在页面上指定的地方
- position:fixed; 固定定位, 被固定的元素不会随滚动条的拖动而改变位置
    - top, bottom, left, right四个属性, 参考对象是浏览器的四条边, 
- position:relative; 相对定位, 相对其原始位置
- position:absolute; 绝对定位, 使用广泛. 脱离文档流, 前后元素会认为这个元素不存在, 这个元素就可以浮在其他元素上面
    - 默认情况, 参考对象是浏览器的四条边
- position:静态定位; 默认是静态的
