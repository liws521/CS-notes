# [GitHub520](https://github.com/521xueweihan/GitHub520)
- 通过修改hosts文件解决GitHub访问慢的问题
- 在Windows and Mac上都实践可行, 注意修改hosts后刷新DNS
    - Windows, ipconfig /flushdns
    - Mac, sudo killall -HUP mDNSResponder
- 当连不上github.com无法访问上面的网站时, 访问镜像站获取hosts
    - (https://github.com.cnpmjs.org/521xueweihan/GitHub520)