- [roadmap](https://www.bilibili.com/read/cv5650633)

# 1
https://www.bilibili.com/video/BV1XJ411X7Ud
- 客户端和服务器
    - Node.js是一门服务器语言, 用js写服务器
- 网页源代码 -> 浏览器渲染
- VSCode中的LiveServer插件
- 实体, 源代码中的多个空格自动被浏览器解析成一个空格, 把<>误解析成标签, 转义, &实体名字; &nbsp;
- href="#", 回到顶部, 
- 内联框架, iframe, frameborder/width/src
- audio
    - autoplay的问题, 大部分浏览器为了用户体验(吓一跳), 会屏蔽自动播放, 需要配合js解决
    - src的ie8不行, source方式, 可以写提示文字
    - embed在老版本中引入音视频, 会自动播放, 但是太丑了, 还要指定type/width/height
- 伪类用来描述元素的特殊状态, 例如hover
- less是一门css的预处理语言, 是css的增强版
    - css存在的问题
        - css中也有变量, 但兼容性不好, 很多浏览器不行, ie不行
        - calu()函数也是很多浏览器不支持
    - less是按简单的写, 有很多新特性, 写完通过工具编译为css
    - VSCode, easyless插件, 舒服

# JS
- https://www.bilibili.com/video/BV1YW411T7GX
- alert(), document.write(), console.log()
- 动态语言, 一行一行执行, alert()会阻塞
- 从上往下逐行加载, 脚本写在上面对象还加载, 就不行
    - onload, 完成加载的事件
