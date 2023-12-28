---
title: GitHub Pages 一些好玩的技巧
number: 33
slug: discussion-33
url: https://github.com/shenweiyan/Knowledge-Garden/discussions/33
date: 2023-12-05
authors: [shenweiyan]
categories: 
  - 资讯
labels: []
---

搜集一下 GitHub Pages 一些好玩的技巧。

<!-- more -->

## 跳转域名

在 [yanlinlin82/yanlinlin82.github.io](https://github.com/yanlinlin82/yanlinlin82.github.io/tree/master) 看到一个通过 <https://yanlinlin82.github.io> 可以直接重定向到 <https://yanlinlin.cn/> 的用法 —— 只需要把 `index.html` 写成这样就可以：
```html
<!DOCTYPE html>
<html>
  <head><meta http-equiv="refresh" content="0; url=https://yanlinlin.cn/"></head>
  <body></body>
</html>
```

<script src="https://giscus.app/client.js"
	data-repo="shenweiyan/Knowledge-Garden"
	data-repo-id="R_kgDOKgxWlg"
	data-mapping="number"
	data-term="33"
	data-reactions-enabled="1"
	data-emit-metadata="0"
	data-input-position="bottom"
	data-theme="light"
	data-lang="zh-CN"
	crossorigin="anonymous"
	async>
</script>
