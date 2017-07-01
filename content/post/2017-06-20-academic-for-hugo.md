+++
date = 2017-06-20T21:35:40+08:00 # 格式为：2017-07-01T20:32:20+08:00
title = "使用 Hugo 的 Academic 主题" # 文件名为 yyyy-mm-dd-title，所以要去掉 yyyy mm dd
slug = "academic-for-hugo" #文件名为 yyyy-mm-dd-title，所以要去掉 yyyy-mm-dd-
url = "/2017-06-20-academic-for-hugo/" # 该设置会覆盖 config.toml 里面的 permalink 
categories = [
    "软件与网络", # IT，建议附加更具体的 tags
]
tags = [
    "hugo", # tag 举例
    "academic", # tag 举例
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++

Hugo 的 Academic 具有以下特点：

- 可以管理主页、博文、论文、演讲、项目等；
- 可以配置简介、论文、项目、博文、演讲、联系方式等；
- 可以自定义不同的内容种类（section）；
- [Markdown](post/writing-markdown-latex.md) 语法高亮，支持 [LaTeX](https://en.wikibooks.org/wiki/LaTeX/Mathematics) ；
- 支持社交链接、[Google 统计](https://analytics.google.com)、[Disqus 评论](https://disqus.com) 等，可惜国内用不了；
- 界面自适应不同的屏幕尺寸，包括手机屏幕尺寸；
- 单页式设计；
- 易于定制。

## 安装

1. [安装 Hugo](https://georgecushen.com/create-your-website-with-hugo/#installing-hugo) 并使用以下命令创建新的站点文件夹 `my_website`：

        hugo new site my_website
        cd my_website

2. 安装 Academic 主题：

        git clone https://github.com/gcushen/hugo-academic.git themes/academic

    替换方式是 [下载 Academic](https://github.com/gcushen/hugo-academic/archive/master.zip) 并解压至站点文件夹的 `themes/academic`。

3. 可以把主题自带的`exampleSite`文件夹内的示范文件复制到站点文件夹。

        cp -av themes/academic/exampleSite/* .

4. 在站点文件夹运行以下命令测试：

        hugo server --watch

    该命令将在本地的`1313`端口开启 web 服务，可访问 [localhost:1313](http://localhost:1313) 来查看效果。

5. 可根据下面的 **入门指南** 来设置相关的内容。

6. 如对预览效果满意，可运行 `hugo` 命令来生成静态 html 文件于`public`文件夹内。静态文件可放在 [Github Pages](https://georgecushen.com/create-your-website-with-hugo/)；或者，把所生成的`public/`文件夹上传到服务器。


## 入门指南

### 核心参数

可编辑`config.toml`来定义核心参数：

- `baseurl` 是网站 URL，要以`/`结尾，例如 https://zhoucaiqi.com/ ；
- `title` 是网站名称；
- 如要启用 [Disqus](https://disqus.com/) 则需要设置`disqusShortname`；如不启用，就将其设置为空值，即：`disqusShortname = ""`；
- `[params]`下面的参数可根据需要编辑；这些内容会显示在首页的；如不想显示，就将其设置为空值`""`。 
- 肖像照片可放在`static/img/`里面，文件名为`portrait.jpg`；
- 如需要启用 LaTeX 数学公式，需要设置`math = true`；
- 社交链接在`[[params.social]]`定义。

### 个人简介

把`themes/academic/exampleSite/content/home/about.md`复制到`content/home/about.md`，然后编辑。

### 定制首页

可参考 [widgets](post/widgets.md) 来定制首页。

### 增加内容

可参加靠 [managing content](post/managing-content.md) 来创建论文、博文、演讲、项目等。

### 删除未用的 widgets 和 页面

[How to remove unused widgets and content pages](post/managing-content.md#removing-content").

## 高级定制

### 导航菜单

`config.toml`里面的`[[menu.main]]` 定义导航菜单。

如需要创建下拉的子菜单，需要在父级菜单定义`identifier = "something"`，并在子级菜单定义 `parent = "something"` ，从而是两者关联起来。

### 网站图标（icon）

网站根目录的`static/img/`里面，`icon.png` and `apple-touch-icon.png`分别对应PC端、移动端的 icon 图标。

### 主题颜色

可在`config.toml`定义`custom_css = ["custom.css"]`，如此，将加载`/static/css/custom.css`)。

例如，定义 `custom_css = ["green.css"]`，然后将 [green theme](https://gist.github.com/gcushen/d5525a4506b9ccf83f2bce592a895495) 下载到 `/static/css/green.css` （注意，是网站根目录，不是主题的目录）。

### 统计分析

在`config.toml`设置`googleAnalytics`，例如`googleAnalytics = "UA-12345678-9"`即可使用[Google Analytics](http://www.google.com/analytics), 可惜中国用不了。

### 第三方脚本 (JS)

可在`/layouts/partials/head_custom.html` 定义加载第三方脚本。该文件的内容将会加载至网站文件的`<head>`区域。

也可以将 js 存在在本地`/static/js/`里面，并在`config.toml` 使用`custom_js  = ["custom.js"]`加载。

### 语言与翻译

界面语言存储在`/themes/academic/i18n/` ，可将对应的语言复制到 `/i18n/` 然后编辑修改。

可翻译或创建新的语言文件，文件名称为 `/i18n/X.yaml`，其中 `X` 是 [ISO/RFC5646 语言标识符](http://www.w3schools.com/tags/ref_language_codes.asp) 里面的代号。接着在 `config.toml` 设置 `defaultContentLanguage` 。

如需要编辑导航菜单，需要编辑`config.toml`里面的 `[[menu.main]]` 。不过，如需要创建多语言站点，需要将`[[menu.main]]`改为 `[[languages.X.menu.main]]`，其中，`X` 语言标识符，例如`[[languages.zh.menu.main]]`。

如要翻译`content/`里面的文件的内容，需要将文件`filename.md` 复制为`filename.X.md` ，其中，`X` 语言标识符，然后翻译。

可参考[associated Hugo documentation](https://gohugo.io/content/multilingual/)。

### 固定连接

*固定连接* 或 *永久连接* 是页面或文章的 URL ，下面的设置将博文链接地址定义为 *yourSiteURL/2016/05/01/my-post-slug*：

    [permalinks]
        post = "/:year/:month/:day/:slug"

其中，`:slug` 默认为博文的文件名（不含后缀）。不过，可在文件里面设置 `slug = "my-short-post-title"` 来定义该文件的  slug 。


## 升级

可加星关注 [Github](https://github.com/gcushen/hugo-academic/) 并监控相关的 [commits](https://github.com/gcushen/hugo-academic/commits/master) 。

升级之前，要将主题的 *origin* 仓库改名为 *upstream*：

    $ cd themes/academic
    $ git remote rename origin upstream

下面的命令显示出相关的更新（如有）：

    $ cd themes/academic
    $ git fetch upstream
    $ git log --pretty=oneline --abbrev-commit --decorate HEAD..upstream/master

接着，下面的命令执行更新：

    $ git pull upstream

如升级后遇到问题，可对比[example site](https://github.com/gcushen/hugo-academic/tree/master/exampleSite) 查看是否需要修改设置。


## 反馈与贡献

可用 [issue tracker](https://github.com/gcushen/hugo-academic/issues) 反馈 bug 或者建议特征，当然，也可以开 pull request 。

常见的问题，可见 [Hugo discussion forum](http://discuss.gohugo.io)。


## 许可

版权所有：[George Cushen](https://georgecushen.com)，2016

[MIT](https://github.com/gcushen/hugo-academic/blob/master/LICENSE.md) 协议。
