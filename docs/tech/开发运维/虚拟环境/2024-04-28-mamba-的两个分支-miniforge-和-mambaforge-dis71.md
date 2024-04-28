---
title: mamba 的两个分支 miniforge 和 mambaforge
number: 71
slug: discussions-71/
url: https://github.com/shenweiyan/Knowledge-Garden/discussions/71
date: 2024-04-28
authors: [shenweiyan]
categories: 
  - 1.3-折腾
labels: ['1.3.22-虚拟环境']
---

在安装 mamba 的时候在 [release](https://github.com/conda-forge/miniforge/releases) 页面和[官方的安装页面](https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html) 总是看到关于 miniforge 和 mambaforge 的选择问题，傻傻搞不明白。

<!-- more -->

参考：<https://github.com/conda-forge/miniforge?tab=readme-ov-file#faq>

> **What's the difference between Mambaforge and Miniforge?**    
> After the release of Miniforge 23.3.1 in August 2023, Miniforge and Mambaforge are essentially identical. The only difference is the name of the installer and subsequently the default installation path.
> 
> Before that release, Miniforge only shipped conda, while Mambaforge added mamba on top. Since Miniconda started shipping conda-libmamba-solver in July 2023, Miniforge followed suit and started shipping it too in August. At that point, since conda-libmamba-solver depends on libmambapy, the only difference between Miniforge and Mambaforge was the presence of the mamba Python package. To minimize surprises, we decided to add mamba to Miniforge too.    
> 
> **Should I choose one or another going forward at the risk of one of them gettting deprecated?**     
> Given its wide usage, there are no plans to deprecate Mambaforge. If at some point we decide to deprecate Mambaforge, it will be appropriately announced and communicated with sufficient time in advance.
> 
> That said, if you had to start using one today, we recommend to stick to Miniforge.

<script src="https://giscus.app/client.js"
	data-repo="shenweiyan/Knowledge-Garden"
	data-repo-id="R_kgDOKgxWlg"
	data-mapping="number"
	data-term="71"
	data-reactions-enabled="1"
	data-emit-metadata="0"
	data-input-position="bottom"
	data-theme="light"
	data-lang="zh-CN"
	crossorigin="anonymous"
	async>
</script>
