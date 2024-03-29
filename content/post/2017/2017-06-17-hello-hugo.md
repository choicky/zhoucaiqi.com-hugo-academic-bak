+++
date = 2017-06-17T21:35:40+08:00 # 格式为：2017-07-01T20:32:20+08:00
title = "使用 hugo 搭建个人网站" # 文件名为 yyyy-mm-dd-title，所以要去掉 yyyy mm dd
slug = "Hello-Hugo" #文件名为 yyyy-mm-dd-title，所以要去掉 yyyy-mm-dd-
# url = "/2017-06-17-Hello-Hugo/" # 该设置会覆盖 config.toml 里面的 permalink 
categories = [
    "软件与网络", # IT，建议附加更具体的 tags
]
tags = [
    "hugo", # tag 举例
    "academic"
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++

### 重建独立博客

我是中国第一代写博客的人，从2003年非典之后就开始写。陆陆续续写了十多年。

时代变迁。博客客逐渐被微博取代；微波逐渐被公众号取代。互联网逐渐收敛成几个大孤岛。汪洋大海中依然存在零星小岛屿，但已逐渐不被世人关注，更加不用说考虑入驻了。<!--more-->

独立博客就如一望无际的海洋上的零星小岛屿。这种小岛屿是否还露在海面上，都没有什么人关注了。有时候甚至连岛主自身都不关注了。我之前的独立博客，就处于这样的状态。

只身在荒无人烟的小岛屿上，实在孤独难耐。但是，那毕竟是自己的岛屿，总归有家的感觉。并且，也许，有一天不幸落水而随浪飘荡的人会因为这个小岛屿而延长了生存时间呢？

这就是重建独立博客的原因。

### 回归 Hugo

之前体验过 [Hugo](https://gohugo.io/)，但后来放弃，放弃的原因是这工具太 geek 。但后来翻来覆去，都没找到更合适的工具了。于是，继续使用 Hugo ，并选用了  [Academic](https://themes.gohugo.io/academic/)。

Hugo 的好处在于，其生成的是静态的 html 文件，因此只需要服务器开启了 web 服务器即可，不要求服务器支持 PHP 等动态语言，不要求服务器开启 Mysql 等数据库服务。