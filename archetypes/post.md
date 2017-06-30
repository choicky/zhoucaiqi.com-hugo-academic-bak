+++
date = {{ .Date }}
title = "{{ replace .TranslationBaseName "-" " " | title }}"
slug = "{{ .TranslationBaseName | title }}"
tags = [
    "post", # 保留，文章归档使用
    "IT", # 如涉及，建议附加更具体的 tags
    "Software", # 如涉及，建议附加更具体的 tags
    "法律", # 如涉及，建议附加更具体的 tags
    "数码", # 如涉及，建议附加更具体的 tags
    "日常" # 如涉及，建议附加更具体的 tags
]
math = false
highlight = true

# Optional featured image (relative to `static/img/` folder).
[header]
image = ""
caption = ""

+++
