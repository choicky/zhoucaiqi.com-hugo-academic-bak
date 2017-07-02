+++
date = 2017-07-01T17:11:01+08:00 # 格式为：2017-07-01T20:32:20+08:00
title = "Hugo Academic 主题的小部件" # 文件名为 yyyy-mm-dd-title，所以要去掉 yyyy mm dd
slug = "Hugo-Academic-Widgets" #文件名为 yyyy-mm-dd-title，所以要去掉 yyyy-mm-dd-
# url = "/2017-07-01-Hugo-Academic-Widgets/" # 该设置会覆盖 config.toml 里面的 permalink 
categories = [
    "软件与网络", # IT，建议附加更具体的 tags
]
tags = [
    "hugo", # tag 举例
    "academic", # tag 举例；最后一项也可以有逗号了
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++

Hugo 的 Academic 主题在首页的小部件（widgets）以章节（sections）的方式显示。可单独启用或禁用某个小部件。 Academic 目前可用的小部件包括：

- 关于/简历
- 精选论文
- 最新的论文
- 最新的资讯/博文
- 项目
- 精选演讲
- 最新的演讲
- 联系
- 自定义小部件（例如 *教育*）

Academic 自带的示范页面使用了“演讲”之外的所有小部件。可基于现有的小部件修改成你想要的。<!--more-->

不同的小部件的参数是不一样的。可在 `content/home/` 里面找到对应的小部件的设置。

{{% alert note %}}
论文默认以简单列表的方式显示。如你想显示更多的细节例如摘要图、摘要，需要编辑`content/home/publications.md` 并设置  `detailed_list = true`。
{{% /alert %}}

## 像首页增加小部件

将小部件文件从 `themes/academic/exampleSite/content/home/` 复制到网站根目录的 `content/home/` 即可。

`config.toml` 里面可设置小部件的标识符，所以导航栏的相对链接 `"#about"`  可链接至 `content/home/about.md` 小部件。

因此，同一种小部件可以有多个实例，只要各个实例被分配了基于文件名的唯一的 ID 。

## 使用定制的小部件

可将 `content/home/teaching.md` 的 `teaching.md` 复制到`content/home/` 并重命名，然后编辑。

可在 `config.toml` 增加对应的导航菜单（要小写）。

    [[menu.main]]
        name = "Research"
        url = "#research"
        weight = 10

## 删除首页的小部件

删除 `content/home/` 下面的对应文件，并从 `config.toml` 删除对应的 `[[menu.main]]` 。

## 小部件排序

设置小部件的文件`weight`就能控制小部件之间的排序。