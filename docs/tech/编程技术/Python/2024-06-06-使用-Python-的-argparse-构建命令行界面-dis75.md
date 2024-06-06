---
title: 使用 Python 的 argparse 构建命令行界面
number: 75
slug: discussions-75/
url: https://github.com/shenweiyan/Knowledge-Garden/discussions/75
date: 2024-06-06
authors: [shenweiyan]
categories: 
  - 1.2-编程
labels: ['1.2.3-Python']
---

> 原文：[Build Command-Line Interfaces With Python's argparse](https://realpython.com/command-line-interfaces-python-argparse/)     


命令行应用在普通用户空间中可能并不常见，但它们存在于开发、数据科学、系统管理和许多其他操作中。每个命令行应用都需要一个用户友好的命令行界面 （CLI），以便你可以与应用本身进行交互。在 Python 中，您可以使用标准库中的 `argparse` 模块创建功能齐全的 CLI。

<!-- more -->

在本文中，你将了解如何：    

- 命令行界面入门；
- 在 Python 中组织和布局命令行应用项目；
- 使用 Python `argparse` 创建命令行界面（command-line interfaces）；
- 使用 `argparse` 一些强大的功能深度自定义您的 CLI；

若要充分利用本教程，应熟悉 Python 编程，包括面向对象编程、脚本开发和执行以及 Python 包和模块等概念。如果您熟悉与使用命令行或终端相关的一般概念和主题，这也将很有帮助。

## 了解命令行界面

自从计算机发明以来，人类一直需要并找到与这些机器交互和共享信息的方法。信息交换在人、计算机软件和硬件组件之间流动。其中任意两个元素之间的共享边界通常称为接口([interface](https://en.wikipedia.org/wiki/Interface_(computing)))。

在软件开发中，接口是给定软件的特殊部分，它允许计算机系统组件之间的交互。当涉及到人机交互和软件交互时，这个重要的组件被称为用户界面（[user interface](https://en.wikipedia.org/wiki/User_interface)）。

您会在编程中找到不同类型的用户界面。图形用户界面 （GUI） 可能是当今最常见的。但是，您还可以找到为其用户提供命令行界面 （CLI） 的应用和程序。在本教程中，你将了解 CLI 以及如何在 Python 中创建它们。

## 命令行界面 （CLI）

命令行界面允许您通过操作系统命令行、终端或控制台与应用程序或程序进行交互。

要了解命令行界面及其工作原理，请考虑此实际示例。假设您有一个名为 sample 包含三个示例文件的目录。如果您使用的是类 Unix 操作系统，例如 Linux 或 macOS，请继续在父目录中打开命令行窗口或终端，然后执行以下命令：    
```bash
$ ls sample/
hello.txt     lorem.md      realpython.md
```

Unix 的 `ls` 命令列出目标目录中包含的文件和子目录，该目录默认为当前工作目录。上面的命令调用没有显示有关 的内容 sample 的太多信息。它只在屏幕上显示文件名。

假设你想要获取有关目录及其内容的更丰富信息，那么你不需要寻找其他程序，因为 ls 命令有一个功能齐全的命令行界面，并且提供了一组有用的选项，可以用来定制命令的行为。

例如，继续执行带有 `-l` 选项的 `ls` 命令：    
```bash
$ ls -l sample/
total 24
-rw-r--r--@ 1 user  staff    83 Aug 17 22:15 hello.txt
-rw-r--r--@ 1 user  staff  2609 Aug 17 22:15 lorem.md
-rw-r--r--@ 1 user  staff   428 Aug 17 22:15 realpython.md
```

现在，`ls` 命令的输出完全不同了。该命令显示了有关 sample 目录中文件的更多信息，包括权限、所有者、组、日期和大小。它还显示了这些文件在你计算机磁盘上使用的总空间。

这种更丰富的输出结果是由于使用了 `-l` 选项，这是 Unix `ls` 命令行界面的一部分，它启用了详细的输出格式。

## 命令、参数、选项、参数和子命令

在本教程中，您将深入了解**命令**(commands)及其**子命令**(subcommands)，同时还会学习到**命令行参数**(command-line arguments)、**选项**(options)和**参数**(parameters)的相关知识。因此，建议您将这些术语纳入您的技术词汇库中。

- **命令(Command)**：在命令行或终端窗口中运行的程序或例程。通常，您可以通过其背后的程序(underlying program)或例程(routine)的名称来识别一个命令。     
- **参数(Argument)**：命令在执行其预期操作时所需或可选的信息片段。命令通常接受一个或多个参数，您可以在命令行中以空格分隔或逗号分隔的列表形式提供这些参数。     
- **选项(Option)**，也称为 **flag** 或 **switch**：一种可选的参数，用于修改命令的行为。选项通过特定的名称（如前一个示例中的 `-l`）传递给命令。     
- **参数(Parameter)**：一个选项用于执行其预期操作或动作时所使用的参数。     
- 子命令(Subcommand)**：一个预定义的名称，可以传递给应用程序来执行特定的操作。

参考上一节中的示例命令结构：
```bash
$ ls -l sample/
```

在这个例子中，您组合了命令行界面（CLI）的以下组件：    

- **ls**：命令的名称或应用的名称；
- **-l**：启用详细输出的选项(option)、开关(switch)或标志(flag)；    
- **sample**：为命令执行提供附加信息的参数(argument)；    

现在，让我们来看下面的命令结构，它展示了 Python 包管理器 `pip` 的命令行界面（CLI）：    
```bash
$ pip install -r requirements.txt
```

这是一个常见的 `pip` 命令结构，您可能之前已经见过。它允许您使用 `requirements.txt` 文件来给指定的 Python 项目安装依赖项。在这个例子中，您使用了以下命令行界面（CLI）组件：   
 
- **pip**：命令的名称；
- **install**：`pip` 的子命令(subcommand)名称；
- **-r**：`install` 子命令的选项(option)；
- **requirements.txt**：一个参数，特别是 `-r` 选项的参数。

现在您已经了解了命令行界面（CLI）是什么以及其主要部分或组件有哪些。接下来，是时候学习如何在 Python 中创建自己的 CLI 了。

## Python 中的 CLI 入门

Python 附带了一些工具，这些工具可帮助您为程序和应用程序编写命令行界面（CLI）。若您需要快速为小型程序构建一个简洁的 CLI，那么可以利用 [`sys`](https://docs.python.org/3/library/sys.html#module-sys) 模块中的 [`argv`](https://docs.python.org/3/library/sys.html#sys.argv) 属性。这个属性会自动存储您在命令行中传递给特定程序的参数。

### 使用 `sys.argv` 构建最小的 CLI

以使用 `argv` 创建最小命令行界面（CLI）为例，假设您需要编写一个小程序，该程序类似于 `ls` 命令，能够列出给定目录下的所有文件。在这种情况下，您可以编写如下代码：    
```python
# ls_argv.py

import sys
from pathlib import Path

if (args_count := len(sys.argv)) > 2:
    print(f"One argument expected, got {args_count - 1}")
    raise SystemExit(2)
elif args_count < 2:
    print("You must specify the target directory")
    raise SystemExit(2)

target_dir = Path(sys.argv[1])

if not target_dir.is_dir():
    print("The target directory doesn't exist")
    raise SystemExit(1)

for entry in target_dir.iterdir():
    print(entry.name)
```

该程序通过手动处理命令行提供的参数来实现了一个简单的命令行界面（CLI），这些参数会自动存储在 `sys.argv` 中。`sys.argv` 的第一个元素始终是程序名称，第二个元素则是目标目录。由于应用程序不应接受超过一个目标目录，因此 `args_count` 不得超过 2。

在检查 `sys.argv` 的内容后，您创建一个`pathlib.Path`对象来存储目标目录的路径。如果该目录不存在，您将通知用户并退出程序。接下来的`for`循环将列出目录内容，每行一个条目。

如果从命令行运行该脚本，您将得到以下结果：    
```bash
$ python ls_argv.py sample/
hello.txt
lorem.md
realpython.md

$ python ls_argv.py
You must specify the target directory

$ python ls_argv.py sample/ other_dir/
One argument expected, got 2

$ python ls_argv.py non_existing/
The target directory doesn't exist
```

您的程序接受一个目录作为参数，并列出其内容。如果您运行命令时没有提供参数，您将收到一个错误消息。如果您运行命令时指定了超过一个目标目录，您同样会收到一个错误消息。如果尝试运行命令并指定一个不存在的目录，程序将输出另一个错误消息。

虽然您的程序运行正常，但对于更复杂的 CLI 应用程序来说，使用`sys.argv`属性手动解析命令行参数并不是一个可扩展的解决方案。如果您的应用需要接受更多的参数和选项，那么解析`sys.argv`将变得复杂且容易出错。您需要一个更好的解决方案，这就是 Python 中的`argparse`模块所提供的。

### 使用 `argparse` 创建 CLI

在 Python 中创建 CLI 应用程序的更便捷方法是使用标准库中的 [`argparse`](https://docs.python.org/3/library/argparse.html?highlight=argparse#module-argparse) 模块。该模块首次在 Python 3.2 中随 [PEP-389](https://www.python.org/dev/peps/pep-0389/) 一同发布，是快速创建 Python CLI 应用程序的利器，无需安装如 Typer 或 Click 这样的第三方库。

`argparse` 模块是作为较旧的 [`getopt`](https://docs.python.org/3/library/getopt.html) 和 [`optparse`](https://docs.python.org/3/library/optparse.html) 模块的替代品而发布的，因为它们缺乏一些重要的功能。

Python 的 `argparse` 模块允许您：     

- 解析命令行**参数**(arguments)和**选项**(options)；
- 在一个单一选项中接受**可变数量的参数**(variable number of parameters)；
- 在 CLI 中提供子命令(subcommands)。

这些特性使 `argparse` 成为了一个强大的 CLI 框架，您在创建 CLI 应用程序时可以放心地依赖它。要使用 Python 的 `argparse`，您需要遵循以下四个简单的步骤：

1. 导入 `argparse`；
2. 通过实例化 [`ArgumentParser`](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser) 创建**参数解析器**(argument parser)；
3. 使用 [`.add_argument()`](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser.add_argument) 方法向解析器添加**参数**(arguments)和**选项**(options)；
4. 在解析器上调用 [`.parse_args()`](https://docs.python.org/3/library/argparse.html?highlight=argparse#argparse.ArgumentParser.parse_args) 以获取参数 [`Namespace`](https://docs.python.org/3/library/argparse.html#namespace)。

例如，您可以使用 `argparse` 来改进您的 `ls_argv.py` 脚本。现在，您可以创建一个名为 `ls.py` 的脚本，并编写以下代码：
```python
# ls.py v1

import argparse
from pathlib import Path

parser = argparse.ArgumentParser()

parser.add_argument("path")

args = parser.parse_args()

target_dir = Path(args.path)

if not target_dir.exists():
    print("The target directory doesn't exist")
    raise SystemExit(1)

for entry in target_dir.iterdir():
    print(entry.name)
```

随着 `argparse` 的引入，您的代码发生了显著的变化。与之前的版本相比，最明显的不同是，用于检查用户提供的参数的条件语句已经消失了。这是因为 `argparse` 会自动为您检查参数的存在性。

在这个新的实现中，您首先导入 `argparse` 并创建一个参数解析器。要创建解析器，您可以使用 `ArgumentParser` 类。接下来，您定义一个名为 `path` 的参数，用于获取用户的目标目录。

接下来，您需要调用 `.parse_args()` 方法来解析输入参数，并获取一个包含所有用户参数的 `Namespace` 对象。请注意，现在 `args` 变量保存了一个 `Namespace` 对象，该对象具有从命令行收集的每个参数所对应的属性。

在这个例子中，您只有一个参数，名为 `path`。`Namespace` 对象允许您使用点表示法通过 `args` 来访问 `path`。其余的代码与第一个实现相同。

现在继续从命令行运行这个新脚本：
```bash
$ python ls.py sample/
lorem.md
realpython.md
hello.txt

$ python ls.py
usage: ls.py [-h] path
ls.py: error: the following arguments are required: path

$ python ls.py sample/ other_dir/
usage: ls.py [-h] path
ls.py: error: unrecognized arguments: other_dir/

$ python ls.py non_existing/
The target directory doesn't exist
```

第一个命令的输出与您的原始脚本 `ls_argv.py` 相同。而第二个命令的输出则与 `ls_argv.py` 中的输出大不相同。程序现在会显示一个使用说明消息，并发出错误提示，告诉您必须提供 `path` 参数。

在第三个命令中，您传递了两个目标目录，但应用程序并未为此做好准备。因此，它再次显示使用说明消息，并抛出一个错误，告知您潜在的问题。

最后，如果您运行脚本时传递了一个不存在的目录作为参数，那么您会收到一个错误，告知您目标目录不存在，因此程序无法执行其工作。

现在，您可以使用一个新的隐式特性。现在，您的程序接受一个可选的 `-h` 标志。不妨尝试一下：
```bash
$ python ls.py -h
usage: ls.py [-h] path

positional arguments:
  path

options:
  -h, --help  show this help message and exit
```

太棒了，现在您的程序会自动响应 `-h` 或 `--help` 标志，并为您显示带有使用说明的帮助消息。这真是一个很棒的特性，而且您只需在代码中引入 `argparse` 就能轻松获得！

经过这个快速介绍如何在 Python 中创建 CLI 应用后，您现在就可以深入研究 `argparse` 模块及其所有炫酷特性了。

## 使用 Python 的 argparse 创建 CLI

您可以使用 `argparse` 模块为您的应用程序和项目编写用户友好的命令行界面。该模块允许您定义应用程序所需的参数和选项。然后，`argparse` 将负责为您解析 `sys.argv` 的参数和选项。

`argparse` 的另一个酷炫特性是它可以自动为您的 CLI 应用程序生成使用说明和帮助消息。该模块还会在参数无效时发出错误提示，并具备更多功能。

在深入研究 `argparse` 之前，您需要知道该模块的文档可识别两种不同类型的命令行参数：     

- **位置参数**(Positional arguments)，您称为参数(arguments)；
- **可选参数**(Optional arguments)，即选项(options)、标志(flags)或开关(switches)。

<script src="https://giscus.app/client.js"
	data-repo="shenweiyan/Knowledge-Garden"
	data-repo-id="R_kgDOKgxWlg"
	data-mapping="number"
	data-term="75"
	data-reactions-enabled="1"
	data-emit-metadata="0"
	data-input-position="bottom"
	data-theme="light"
	data-lang="zh-CN"
	crossorigin="anonymous"
	async>
</script>
