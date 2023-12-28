---
title: GitHub Discussions 使用与思考
number: 38
slug: discussion-38
url: https://github.com/shenweiyan/Knowledge-Garden/discussions/38
date: 2023-12-06
authors: [shenweiyan]
categories: 
  - 乱弹
labels: []
---

从2023年7月起我的文档都保存在了 GitHub Discussions 上，作为博客、IED 编辑器，以及评论使用，GitHub Discussions 是完全没问题的。

<!-- more -->

## 专业书籍文档

今天忽然想到的一个问题，即如果作为专业性比较强的系列文档写作，如《[Hello 算法](https://www.hello-algo.com/)》 这样专业性和逻辑性非常明确的专业书籍，使用 GitHub Discussions 写作应该是有点不太合适。

但又仔细想了一下，如果只是写作应该是没问题的 —— 我们可以用 sections 或者 categories，甚至是 tags 进行书籍分类，最后在导出的时候借助这些标签把相关的文档整合到一块，再借助 nav 梳理成大纲展现给读者阅读就可以。所以，总的来说**可以用于专业书籍写作，但不太适合用于专业书籍的呈现和阅读** —— 主要是大纲和逻辑性会变得不明显。

## 目录和分类标签

GitHub Discussions 目前[最多支持 25 个 categories](https://github.com/orgs/community/discussions/7960)，这是一个限制。第二个问题是只能通过 section+category 实现最多两级的目录结构，所以对于三级和三级以上的目录结构目前暂时无能为力。

因此，想到一个折中的解决方法：使用 labels 来区分第三级目录结构。
```
1.1-生信
  - 1.1.1-算法
  - 1.1.2-数据
  - 1.1.2-软件
```

然后，导出 Discussions 的时候需要在本地先在本地建立一个 `section+category: dictory` 一一对应的字典，最后通过这个字典把不同的讨论 md 归档至对应的目录。
```
1.1-生信:
    1.1.1-算法: docs/cookbook/生物信息/算法
    1.1.2-数据: docs/cookbook/生物信息/数据
    1.1.2-软件: docs/cookbook/生物信息/软件
    ...
```

<script src="https://giscus.app/client.js"
	data-repo="shenweiyan/Knowledge-Garden"
	data-repo-id="R_kgDOKgxWlg"
	data-mapping="number"
	data-term="38"
	data-reactions-enabled="1"
	data-emit-metadata="0"
	data-input-position="bottom"
	data-theme="light"
	data-lang="zh-CN"
	crossorigin="anonymous"
	async>
</script>
