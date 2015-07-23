importStyle(cssText, id?)
=========

> importStyle 方法会创建一个 style 元素，并将其内容设置为 cssText，然后插入到当前文档中。

##参数说明：

- cssText 是文本字符串，存储要添加的样式内容。
- id 可选，如果传入，会给创建的 style 元素添加该 id 值。


##注意事项

1. 传入的 cssText 字符串，如果中间有 \0 等转义字符，需要在传入前提前转义成 \\0 等字符，这样才能确保插入的内容无误。构建工具在实现时要注意这一点。

2. 在 IE 下，当前页面的 style 标签数不能超过 31 个。超过 31 后，插入的 style 无效。这时 seajs 会抛出异常：

		// http://support.microsoft.com/kb/262161
		if (doc.getElementsByTagName('style').length > 31) {
		    throw new Error('Exceed the maximal count of style tags in IE')
		}

##使用方式

	var importStyle = require('importStyle');

	importStyle("body { margin: 0 }")