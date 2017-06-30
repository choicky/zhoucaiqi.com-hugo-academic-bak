+++
date = 2017-06-30T19:56:46+08:00
title = "Disqus In China"
tags = [
    "post", # 保留，文章归档使用
    "IT", # 如涉及，建议附加更具体的 tags
    "Software", # 如涉及，建议附加更具体的 tags
    "disqus", # 如涉及，建议附加更具体的 tags
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++

现在很多独立博客程序都不带论模块了。所以独立博客往往被迫使用第三方提供的评论服务，例如国外的 [Disqus](https://disqus.com/)、国内的多说、友言、畅言等。遗憾的是，国内的服务要么停止了，要么停止不活的。所以，只能考虑 Disqus。

但是，中国的网络与国外的网络之间竖着一堵墙，而 Disqus 很不幸地被挡在墙外。

偶然间，发现一篇[《科学使用 Disqus》](http://blog.fooleap.org/use-disqus-correctly.html)，其中介绍了一个开源的 [disqus-php-api](https://github.com/fooleap/disqus-php-api) 项目，该项目的原理是借助一个中间服务器中转 Disqus 的数据，从而使国内的网站可以基本正常地使用 Disqus 服务。

这个项目只要求 PHP 以及 web服务器，很容易找到支持的运行环境。

该项目的文件结构如下：
```
├─api
│  ├─emojione
│  │  └─src
│  └─PHPMailer
├─dist
└─src
```
其中，`dist` 里面有一个css文件、一个js文件，这两个文件可放在墙内（为了加快速度）。

当某个页面需要使用这个项目时，就在`<head>`与`</head>`之间加上这两行引入上述的css文件和js文件：

```
<link rel="stylesheet" href="path/to/iDisqus.min.css" />
<script src="path/to/iDisqus.min.js"></script>
```

然后，在需要出现评论框地方，写上下面这段代码即可。
```
<div id="comment"></div>
<script>
    var disq = new iDisqus('comment', {
        forum: 'fooleap',
        api: 'http://api.fooleap.org/disqus',
        site: 'http://blog.fooleap.org',
        mode: 1,
        timeout: 3000,
        init: true
    });
</script>
```

感谢项目作者的付出及技术支持。