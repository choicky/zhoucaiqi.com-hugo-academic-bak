+++
date = {{ .Date }} # 格式为：2017-07-01T20:32:20+08:00
title = "{{ replace .TranslationBaseName "-" " " | title }}" # 文件名为 yyyy-mm-dd-title，所以要去掉 yyyy mm dd
slug = "{{ .TranslationBaseName | title }}" #文件名为 yyyy-mm-dd-title，所以要去掉 yyyy-mm-dd-
url = "/{{ .TranslationBaseName | title }}/" # 该设置会覆盖 config.toml 里面的 permalink 
categories = [
    "法律与案例", # Laws，建议附加更具体的 tags
    "软件与网络", # IT，建议附加更具体的 tags
    "数码与日常", # Life，建议附加更具体的 tags；最后一项也可以有逗号了
]
tags = [
    "Markdown", # tag 举例
    "VPS", # tag 举例；最后一项也可以有逗号了
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++
