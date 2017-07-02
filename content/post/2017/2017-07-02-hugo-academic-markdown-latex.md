+++
date = 2017-07-02T19:12:09+08:00 # 格式为：2017-07-01T20:32:20+08:00
title = "在 Hugo 中使用 Markdown 和 Latex" # 文件名为 yyyy-mm-dd-title，所以要去掉 yyyy mm dd
slug = "Hugo-Academic-Markdown-Latex" #文件名为 yyyy-mm-dd-title，所以要去掉 yyyy-mm-dd-
# url = "/2017-07-02-Hugo-Academic-Markdown-Latex/" # 该设置会覆盖 config.toml 里面的 permalink 
categories = [
    "软件与网络", # IT，建议附加更具体的 tags
]
tags = [
    "hugo", # tag 举例
    "academic", # tag 举例；最后一项也可以有逗号了
    "markdown",
    "latex"
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++

使用了 Academic 主题框架之后，可用 [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) 、 [LaTeX math](https://en.wikibooks.org/wiki/LaTeX/Mathematics) 以及 [Hugo 短码](http://gohugo.io/extras/shortcodes/) 来写作。此外，还可以使用 HTML 来实现更高级的格式化。

## 标题

    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五极标题
    ###### 六级标题

## 强调

    使用单个星号 `*` 或 下划线 `_` 实现字体倾斜。
    
    使用双星号 `**` 或者 双下划线 `__` 实现字体加粗。
    
    双波浪线 `~~` 实现删除线。

    加粗、斜体可叠加使用。

## 有序列表

    1. 第一项
    2. 第二项

## 无序列表

    * 无序项目1
    * 无序项目2

## 图片

图片可放在 `static/img/` ，然后用下面的其中一种方式：

普通图像：

    ![替换文字](/img/screenshot.png)

A numbered figure with caption:

    {{</* figure src="/img/screenshot.png" title="Figure Caption" */>}}

## 链接

    [I'm a link](https://www.google.com)
    [A post]({{</* ref "post/hi.md" */>}})
    [A publication]({{</* ref "publication/hi.md" */>}})
    [A project]({{</* ref "project/hi.md" */>}})
    [Another section]({{</* relref "hi.md#who" */>}})

## 表情

 [Emoji cheat sheet](http://www.webpagefx.com/tools/emoji-cheat-sheet/) 显示了可用的表情。 语法如下（表情名称前后的分号之间的空格应当去掉）：

    I : heart : Academic : smile :
    
I :heart: Academic :smile:

## 引用

    > 这是引用的文字。

> 这是引用的文字。

## 附注

    我有更多的内容[^1]要说。
    
    [^1]: 附注的内容。

我有更多的内容[^1]要说。
    
[^1]: 附注的内容。

## 代码高亮

在三个 \`\`\` 后面加上语言种类，例如`python`：

    ```python
    # 代码高亮示例
    input_string_var = input("Enter some data: ")
    print("You entered: {}".format(input_string_var))
    ```
上述代码的效果如下：:

```python
# 代码高亮示例
input_string_var = input("Enter some data: ")
print("You entered: {}".format(input_string_var))
```

### 高亮选项

Academic 主题框架使用 [highlight.js](https://highlightjs.org) 实现代码高亮。

配置选项如下：

选项                  | 变量类型| 描述                            | config.toml | preamble
----------------------|---------|---------------------------------|-------------|---------
`highlight`           | boolean | 启用/禁用代码高亮               | yes         | yes
`highlight_languages` | slice   | 选择其他语言                    | yes         | yes
`highlight_style`     | string  | 选择高亮风格                    | yes         | no
`highlight_version`   | string  | 选择 highlight.js 版本|         | yes         | no


#### `highlight` 选项

 `highlight` 选项用来配置启用或禁用 highlight.js 。如该选择未设置，则视为 `highlight = true` 。

config.toml   | page preamble  | 该页面是否启用语法高亮？
--------------|----------------|-------------------------------
unset or true | unset or true  | yes
unset or true | false          | no
false         | unset or false | no
false         | true           | yes

#### `highlight_languages` 选项

 `highlight_languages` 选项用于指定 highlight.js 支持的但默认未支持的语言。例如，如果像全局高亮 Go 和 clojure 语言，则在 `config.toml` 设置 `highlight_languages = ["go", "clojure"]` 。
 
 `config.toml` 中及具体页面中，`highlight_languages` 的值是可以叠加的。例如， `config.toml` 设置了 `highlight_languages = ["go"]` ，具体页面设置了 `highlight_languages = ["ocaml"]` ，那么， go 和 ocaml 都会被高亮。

如设置了 `highlight_languages` ，则对应的脚本将会从 [cdnjs server](https://cdnjs.com/libraries/highlight.js/) 下载过来。可访问 [cdnjs page](https://cdnjs.com/libraries/highlight.js/) 并搜索 "languages" 来查看被支持的语言。

#### `highlight_style` 选项

`highlight_style` 用来控制语法高亮的 css 风格。例如， 如果想使用深黑的风格，可在 `config.toml` 设置 `highlight_style = "solarized-dark"` 。

如果未设定 `highlight_style` 则默认采用 `/css/highlight.min.css` ，也就是 `github` 风格。

如设定了 `highlight_style` 则 `/css/highlight.min.css` 被忽略。系统会从 [cdnjs server](https://cdnjs.com/libraries/highlight.js/) 下载相应的 css 。可访问 [cdnjs page](https://cdnjs.com/libraries/highlight.js/) 并搜索 "styles" 来查看相应的风格。

也可访问 [highlight.js 演示页](https://highlightjs.org/static/demo/) 来查看可用的风格。

{{% alert note %}}
[highlight.js 演示页](https://highlightjs.org/static/demo/) 上的风格不一定都存在 [cdnjs server](https://cdnjs.com/libraries/highlight.js/) ，如果 cdnjs 为存储有你想要的风格，则视为未设定 `highlight_style` 。
{{% /alert %}}

{{% alert note %}}
如果你想使用 Academic 自带的风格，又想从 [cdnjs server](https://cdnjs.com/libraries/highlight.js/) 下载，就在 `config.toml` 设定 `highlight_style = "github"` 。
{{% /alert %}}

`highlight_style` 选项仅在 `config.toml` 中可设置。在具体地页面设置 `highlight_style` 是无效的。

#### `highlight_version` 选项

`highlight_version` 选项用来选择版本，默认的版本是 "9.9.0" 。类似地，该选择仅在 `config.toml` 中可设置。在具体地页面设置 `highlight_version` 是无效的。

## Twitter 的推文

粘贴 推文的 ID 就能引用该推文。可从 URL 找到该 ID 。

    {{</* tweet 666616452582129664 */>}}

## Youtube

    {{</* youtube w7Ft2ymGmfc */>}}

## Vimeo

    {{</* vimeo 146022717 */>}}

## GitHub gist

    {{</* gist USERNAME GIST-ID  */>}}

## Speaker Deck

    {{</* speakerdeck 4e8126e72d853c0060001f97 */>}}

## $\rm \LaTeX$ math

```TeX
$$\left [ – \frac{\hbar^2}{2 m} \frac{\partial^2}{\partial x^2} + V \right ] \Psi = i \hbar \frac{\partial}{\partial t} \Psi$$
```

$$\left [ – \frac{\hbar^2}{2 m} \frac{\partial^2}{\partial x^2} + V \right ] \Psi = i \hbar \frac{\partial}{\partial t} \Psi$$

Alternatively, inline math can be written by wrapping the formula with only a single `$`:

    This is inline: $\mathbf{y} = \mathbf{X}\boldsymbol\beta + \boldsymbol\varepsilon$

This is inline: $\mathbf{y} = \mathbf{X}\boldsymbol\beta + \boldsymbol\varepsilon$

## 表格

Code:

```Markdown
| Command           | Description                    |
| ------------------| ------------------------------ |
| `hugo`            | Build your website.            |
| `hugo serve -w`   | View your website.             |
```

Result:

| Command           | Description                    |
| ------------------| ------------------------------ |
| `hugo`            | Build your website.            |
| `hugo serve -w`   | View your website.             |


## 提示

注意提示的语法如下：

    {{%/* alert note */%}}
    Here's a tip or note...
    {{%/* /alert */%}}

上面的代码的效果如下：

{{% alert note %}}
Here's a tip or note...
{{% /alert %}}

警告提示的语法如下：

    {{%/* alert warning */%}}
    Here's some important information...
    {{%/* /alert */%}}

上面的代码的效果如下：

{{% alert warning %}}
Here's some important information...
{{% /alert %}}
