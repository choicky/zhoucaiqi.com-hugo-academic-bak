+++
date = 2017-06-21T11:33:27+08:00 # 格式为：2017-07-01T20:32:20+08:00
title = "在 academic 框架下管理 hugo 的内容" # 文件名为 yyyy-mm-dd-title，所以要去掉 yyyy mm dd
slug = "Hugo-Academic-Content" #文件名为 yyyy-mm-dd-title，所以要去掉 yyyy-mm-dd-
# url = "/2017-06-01-Hugo-Academic-Content/" # 该设置会覆盖 config.toml 里面的 permalink 
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

首先要理解， academic 不是普通的 hugo 主题，它实质上是框架级别的 hugo 组件。

在 academic 下，hugo 的内容可分为论文、项目、演讲、资讯/博文等。这些内容可以使用 Markdown 、 LaTeX 等去撰写。如需要使用 LaTeX 语言，需要定义 `math = true` 。<!--more-->

如要语法高亮，需要设置 `highlight = true` ；如不需要，则 `highlight = false`。

如需要给文章指定主题图片，可先把图片保存在`/static/img/`，然后在文件头部的 `image=""`指定图片路径；该图片的连接地址。该图片的脚注及连接可在`caption`设置，例如：

```toml
[header]
image = "headers/getting-started.png"
caption = "Image credit: [**Academic**](https://github.com/gcushen/hugo-academic/)"

```

{{% alert note %}}
如果想避免主题图片被自动用作缩略图，可在 `[head]` 区增加 `preview = false` 。
{{% /alert %}}

## 创建论文

可用以下命令创建论文：

    hugo new publication/my-paper-name.md

然后编辑 `content/publication/my-paper-name.md` ，其中 `url_` 变量用于生成该论文的链接，例如 PDF 。举例如下：

```
+++
abstract = "An abstract..."
authors = ["First author's name", "Second author's name"]
date = "2013-07-01"
image = ""
image_preview = ""
math = false
publication = "The publishing part of the citation goes here. You may use *Markdown* for italics etc."
title = "A publication title, such as title of a paper"
url_code = ""
url_dataset = ""
url_pdf = "pdf/my-paper-name.pdf"
url_project = ""
url_slides = ""
url_video = ""
+++

Further details on your publication can be written here using *Markdown* for formatting. This text will be displayed on the Publication Detail page.
```

`url_` 可指向本地或网络的地址，本地的 PDF 可复制到 `static/pdf/` 然后设定 `url_pdf = "pdf/my-paper-name.pdf"`.

也可以自定义链接按钮，例如：

```
[[url_custom]]
    name = "自定义 Link"
    url = "http://www.example.org"
```

如果`config.toml`启用了 `detailed_list` ，论文模板中的选项会更多。例如可用 `abstract_short = "friendly summary of abstract"` 、 `publication_short = "abbreviated publication details"` 以显示更友好的摘要、论文信息。此外，还可以通过 `image_preview = "my-image.jpg"` 来设置显示不同的图像。

{{% alert warning %}}
注意，英文的双引号`"`、反斜杠（例如 LaTeX 的`\times`）需要使用反斜杠`\`进行转义。可访问[TOML documentation](https://github.com/toml-lang/toml#user-content-string) 了解。
{{% /alert %}}

## 创建博文

创建博文的命令：

    hugo new post/my-article-name.md

然后编辑 `content/post/my-article-name.md` ，设定其中的 `title` 和 `date` 以及内容。

Hugo 会自动生成博文的摘要以显示在首页上。如对自动生成的摘要不满意，可手工插入摘要的分节符  <code>&#60;&#33;&#45;&#45;more&#45;&#45;&#62;</code> 。或者定义博文的 `summary` ：

    summary = "Summary of my post."

如要禁止某篇博文的评论，可在该博文设定 `disable_comments = true` 。如要全站禁止评论， 在 `config.toml` 中将 `disqusShortname` 设为空值，或者设定 `disable_comments = true` 。

## 创建项目

创建项目的命令：

    hugo new project/my-project-name.md

然后编辑 `content/project/my-project-name.md` 。项目可链接到外部，例如 `external_link = "http://external-project.com"` 。

## 创建演讲

创建演讲的命令：

    hugo new talk/my-talk-name.md

然后编辑 `content/talk/my-talk-name.md` 。

## 管理节点的索引页

节点索引页（例如 `/post/` ）用于显示内容列表。这个索引页是自动生成的，但是，也可以创建并编辑`_index.md`，例如：

    hugo new post/_index.md
    hugo new publication/_index.md
    hugo new talk/_index.md
    
创建后，移除 `title`, `math`, `highlight`, and `date`. Edit the `title` 之外的变量，并增加想要的内容，例如：

```toml
+++
title = "List of my posts"
date = "2017-01-01T00:00:00Z"
math = false
highlight = false
+++

下面是自动生成的博文列表：

```

## 删除内容

从 `content/post` 、 `content/publication` 、 `content/project` 、 `content/talk` 等文件夹内删除相应的文件即可。

## 预览更新后的网站

在网站根目录运行  `hugo server --watch` 后，可访问 [localhost:1313](http://localhost:1313) 来预览网站。

## 部署网站

运行 `hugo` 命令后生成的 `public/` 文件夹，就是网站文件，将该文件夹部署到 web 服务器即可。

需要注意的是， `hugo` 命令不会删除原来的旧文件。所以，最好先删除 `public/` 文件夹然后再运行 `hugo` 。