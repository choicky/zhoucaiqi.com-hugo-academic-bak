+++
date = 2017-06-22T12:11:25+08:00 # 格式为：2017-07-01T20:32:20+08:00
title = "将 Jekyll 导入 Hugo" # 文件名为 yyyy-mm-dd-title，所以要去掉 yyyy mm dd
slug = "Jekyll-To-Hugo" #文件名为 yyyy-mm-dd-title，所以要去掉 yyyy-mm-dd-
# url = "/2017-06-22-Jekyll-To-Hugo/" # 该设置会覆盖 config.toml 里面的 permalink 
categories = [
    "软件与网络", # IT，建议附加更具体的 tags
]
tags = [
    "hugo", # tag 举例
    "jekyll", # tag 举例；最后一项也可以有逗号了
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++

这篇提供简单的将现有的网站从 Jekyll 平台转入 Hugo 的指南。

## 将 Jekyll 的静态内容移动到 Hugo 的`static`
Jekyll 的规则是，以 `_` 开头的文件都会复制到 `_site` 作为输出。而 Hugo 的规则是静态文件都放在 `static` 。

Jekyll 的文件架构可能是这样的：

    ▾ <root>/
        ▾ images/
            logo.png

而 Hugo 中，应当改为这样：<!--more-->

    ▾ <root>/
        ▾ static/
            ▾ images/
                logo.png

此外，需要保持在部署后的网站根目录的文件例如 `CNAME` 也需要移至 `static` 。

## 修正内容
主要是修正文件头部的内容。然后通过 `hugo server --watch` 预览。

## 发布
Jekyll 的网站文件存放在 `_site` ，而 Hugo 的网站文件存放在 `public` 。

## 实例
Alexandre Normand 将他的网站从 Jekyll 迁移到 Hugo ，用时不足一天。可参考他的文件变化 [diff](https://github.com/alexandre-normand/alexandre-normand/compare/869d69435bd2665c3fbf5b5c78d4c22759d7613a...b7f6605b1265e83b4b81495423294208cc74d610). 不过，请注意，该例子 **没有使用 Academic 主题并且不是最新版的 Hugo**。
