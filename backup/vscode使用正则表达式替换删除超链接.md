在VSCode中编写Markdown时，您可以使用正则表达式来批量删除超链接但保留文本。以下是一个简单的步骤，可以帮助您完成这个任务：

打开VSCode中的搜索替换功能（使用快捷键Ctrl + H）。
在“查找”框中输入以下正则表达式：`\[([^\]]+)\]\([^)]+\)`

## 删除文本超链接保留文本
`\[([^\[\]]+)\]\(([^\(\)]+)\)`
这个正则表达式可以找到`[显示文本](链接地址)`
替换成$1就ok了

## 删除图片超链接
`\[!\[(.*?)\]\((.*?)\)\]\((.*?)\)`
这个正则表达式会匹配 `[![标题](https://hello.html)](/helloworld.html)` 中的 `https://hello.html` 和 `/helloworld.html`。
替换成`![]($2)`这个之后就可以删除图片的超链接
或者替换成`Gmxxk-html<img src="$2" alt="$1" loading="lazy">`将xx改为ee，就可以适配Gmeek最新的img标签。

在“替换”框中输入：$1
确保选中“使用正则表达式”的选项（这通常是一个.*的图标）。
点击“全部替换”。
这样，所有的格式为链接文本的Markdown超链接都会被替换为仅包含链接文本的格式。例如，“乔治敦”会被替换为“乔治敦”。

如果要识别`![](超链接)图片名`  
`!\[[^\]]*\]\(([^)]+)\)([^\\n]*)`

请注意，执行此操作前建议您备份文档，以防万一替换出现不预期的结果。希望这能帮助到您！