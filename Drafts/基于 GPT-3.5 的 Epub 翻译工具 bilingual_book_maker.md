# 基于 GPT-3.5 的 Epub 翻译工具 bilingual_book_maker

## 一、介绍

[bilingual_book_maker](https://github.com/yihong0618/bilingual_book_maker) 是一个 AI 翻译工具，使用 ChatGPT 帮助用户制作多语言版本的 epub/txt 文件和图书。

### 使用 bilingual_book_maker 需要准备

1. [openai API key]([https://platform.openai.com/account/api-keys](https://platform.openai.com/account/api-keys))
2. epub/txt books
3. 能正常联网的环境或 proxy
4. python3.8 +

### 逐项解释并说明重点

#### openai API key
  1. openai API key 是在 [openai platform](https://platform.openai.com/login) 注册账号并登陆，在 [api-keys](https://platform.openai.com/account/api-keys) 界面点击 `+ Create new secret key` 按钮生成一个的 API key，通过此 key 可以调用 openai API，注意在点击按钮后弹窗中出现的 key 只会出现一次，保存好。
  2. 在 [usage](https://platform.openai.com/account/usage) 界面可以看使用量。
  3. 有 [rate-limits](https://platform.openai.com/docs/guides/rate-limits)，以 **RPM** (requests per minute) 和 **TPM** (tokens per minute) 作为限制指标，体验金账号就是 Free trial Users, 如果用着用着有 api 调用失败的时候可能是触发了 rate-limits, 绑定了支付信息就是 Pay-as-you-go users，可以看到 RPM 的限额高很多。
	  ![rate-limits](attachments/openai_rate_limits.png)

#### epub/txt books

想要翻译的 epub 或 txt 书籍文件，在 [bilingual_book_maker](https://github.com/yihong0618/bilingual_book_maker) 项目有 [test_books](https://github.com/yihong0618/bilingual_book_maker/tree/main/test_books) 文件夹里的书籍供测试。

#### 联网和 proxy

按照 openai 的政策，在中国的 ip 是不允许调用 API 的，包括香港地区的 ip，否则容易导致 API 或者账号 ban 掉，虽然事实上（2023年3月）是可以在 香港 ip 调用 API 的，但存在的风险就是会被 ban 。

#### python3.8 +

用 [pyenv](https://github.com/pyenv/pyenv) 管理 python 版本就可以，还可以针对项目配置版本，很方便。

## 二、使用

### 调用方法

<span style="background: linear-gradient(to right, violet, indigo, blue, green, yellow, orange, red); -webkit-background-clip: text; -webkit-text-fill-color: transparent; animation: rainbow 2s linear infinite;">Work in Progress</span> <style> @keyframes rainbow { 0% { background-position: 0%; } 100% { background-position: 400%; } } </style>

### 参数说

<span style="background-image: linear-gradient(to right, violet, indigo, blue, green, yellow, orange, red); -webkit-background-clip: text; -webkit-text-fill-color: transparent; animation: bg-colors 10s ease infinite;">Work in Progress</span> <style> @keyframes bg-colors { 0% { background-color: violet; } 14% { background-color: indigo; } 28% { background-color: blue; } 42% { background-color: green; } 56% { background-color: yellow; } 70% { background-color: orange; } 84% { background-color: red; } 100% { background-color: violet; } } </style>

重要参数：`--batch_size`

<!-- todo: 这里给出 issues 和 pr 链接 -->

## 三、实测

《哈利波特》七部完整版共 140 万左右的英文单词，开启 `--batch_size` 参数翻译成双语版本用时大概是 2.5 小时。

<!-- todo: 这里给出 issues 和 pr 链接 -->

<span style="font-size: 48px; background-image: linear-gradient(to right, violet, indigo, blue, green, yellow, orange, red); -webkit-background-clip: text; -webkit-text-fill-color: transparent; text-shadow: 0px 0px 15px rgba(255, 255, 255, 0.8);">Work in Progress</span>
