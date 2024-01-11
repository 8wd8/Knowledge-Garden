---
title: MkDocs 主题 awesome-pages 使用
number: 51
slug: discussion-51
url: https://github.com/shenweiyan/Knowledge-Garden/discussions/51
date: 2024-01-11
authors: [shenweiyan]
categories: 
  - 好玩
labels: []
---

很长一段时间都在使用 [mkdocs_include_dir_to_nav](https://github.com/mysiki/mkdocs_include_dir_to_nav) 这个插件来自动包含目录下的所有 md 文件，但新需求的出现 —— **如何为某一个指定的子目录使用 `reverse_sort_file`，即升序排列展示相应的内容**。这才开始接触到 [MkDocs Awesome Pages Plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin)。

<!-- more -->

## 开始

可以看到的是 [mkdocs_include_dir_to_nav](https://github.com/mysiki/mkdocs_include_dir_to_nav) 自从 2022-05-01 更新了 [V1.2.0](https://github.com/mysiki/mkdocs_include_dir_to_nav/releases/tag/v1.2.0) 版本后基本就已经停止了更新。

反而是 [MkDocs Awesome Pages Plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin) 一直保持着非常积极的更新频率，而且维护者和关注和使用用户也远远比 [mkdocs_include_dir_to_nav](https://github.com/mysiki/mkdocs_include_dir_to_nav) 多得多。

鉴于这几点背景，开始入手 [MkDocs Awesome Pages Plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin)。不得不说，Awesome-Pages 这个插件的功能很强大，可以很好解决我"指定子目录自定义文档排序"的需求。但不可否认的是 Awesome-Pages 的文档写的的确有点糙，不认真看还真不知道应该如何上手，这也是花费我最多时间的地方。

## 使用

使用 [MkDocs Awesome Pages Plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin) 有两个很重要的前提：

1. 如果你在 `mkdocs.yml` 定义了 `nav` 或 `pages` 条目，则此插件不会执行任何操作。要使用该插件列出的功能，我们必须完全删除该条目或向其中添加 `...` 条目 ([add a `...` entry to it](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin?tab=readme-ov-file#combine-custom-navigation--file-structure))。
2. 自定义导航时，在目录(或者子目录)中创建一个名为 `.pages` 的文件时，使用 `nav` 属性只能自定义**该级别的导航**！



<script src="https://giscus.app/client.js"
	data-repo="shenweiyan/Knowledge-Garden"
	data-repo-id="R_kgDOKgxWlg"
	data-mapping="number"
	data-term="51"
	data-reactions-enabled="1"
	data-emit-metadata="0"
	data-input-position="bottom"
	data-theme="light"
	data-lang="zh-CN"
	crossorigin="anonymous"
	async>
</script>
