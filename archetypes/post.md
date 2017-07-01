+++
date = {{ .Date }}
title = "{{ replace .TranslationBaseName "-" " " | title }}"
slug = "{{ .TranslationBaseName | title }}"
categories = [
    "法律", # 如涉及，建议附加更具体的 tags
    "网络", # 如涉及，建议附加更具体的 tags
    "软件", # 如涉及，建议附加更具体的 tags
    "数码", # 如涉及，建议附加更具体的 tags
    "日常" # 如涉及，建议附加更具体的 tags；注意，最后一项没有逗号
]
tags = [
    "Markdown", # tag 举例
    "VPS" # tag举例，注意，最后一项没有逗号
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++
