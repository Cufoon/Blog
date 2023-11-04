---
title: "美化你的powershell"
slug: "make-powershell-beautiful"
date: 2020-03-12T15:56:56+08:00
lastmod: 2020-03-12T15:56:56+08:00
draft: false
tags: ["Windows"]
categories: []
lightgallery: true
code:
  copy: true
---

#### 为什么要美化 PowerShell?

windows 自带的 powershell 的主题色是深蓝色,像下面这样

<img loading="lazy" src="/images/2020/1.png" alt="powershell默认蓝" />

&nbsp;

单从美观度上讲，这个实在是有些丑陋了，所以我们需要美化一下它。

如果你也有点强迫症，正在寻找美化 powershell 的办法，来到这就对了。

_只针对 windows 平台有效_

&nbsp;

#### First: 安装 oh-my-posh 和 posh-git

oh-my-posh 是 powershell 的一个主题引擎或者说是主题框架，不累述，装就完事了

posh-git 是 oh-my-posh 的一个依赖，通过它可以显示文件夹的 git 信息

在 powershell 中执行下面的两条命令

<img loading="lazy" src="/images/2020/2.svg" alt="安装oh-my-posh和posh-git" style="width: 800px" />

执行命令时如果有提示输入 Y 继续执行即可完成 oh-my-posh 和 posh-git 的安装

&nbsp;

#### Second: 设置配置文件 导入主题

通过下面的命令可以创建 powershell 的配置文件，该配置文件只对当前有效

命令执行后会调用 win10 的记事本打开这个配置文件

<img loading="lazy" src="/images/2020/3.svg" alt="创建配置文件" style="width: 800px" />

&nbsp;

在打开的记事本中填入如下内容

<img loading="lazy" src="/images/2020/4.svg" style="width: 800px" />

&nbsp;

然后保存文件即可完成主题的配置

其中 `Set-Theme Paradox` 中的 Paradox 是 oh-my-posh 中自带的主题

oh-my-posh 中默认的主题有

&nbsp;

Agnoster

<img loading="lazy" src="/images/2020/5.png" />

&nbsp;

Paradox

<img loading="lazy" src="/images/2020/6.png" />

&nbsp;

Sorin

<img loading="lazy" src="/images/2020/7.png" />

&nbsp;

Darkblood

<img loading="lazy" src="/images/2020/8.png" />

&nbsp;

Avit

<img loading="lazy" src="/images/2020/9.png" />

&nbsp;

Honukai

<img loading="lazy" src="/images/2020/10.png" />

&nbsp;

Fish

<img loading="lazy" src="/images/2020/11.png" />

&nbsp;

Robbyrussell

<img loading="lazy" src="/images/2020/12.png" />

&nbsp;

#### Third: 配置颜色以及字体

完成上述步骤，不出意外可以得到下图的效果

<img loading="lazy" src="/images/2020/13.png" />

&nbsp;

很明显这完全没有前面的效果

所以我们要改变配色以及字体

&nbsp;

**配色**

配色可以使用微软的官方工具来修改

工具地址：<https://github.com/microsoft/terminal/releases/tag/1904.29002>

由于微软的这个 colortool 工具是兼容 iterm2 的主题的

因此我们可以在 https://iterm2colorschemes.com/ 上找到自己喜欢的主题并下载下来

然后用 colortool 把下载的主题设置到 powershell 中

首先将下载好的 colortool 工具给解压 得到

<img loading="lazy" src="/images/2020/14.png" />

我从 https://iterm2colorschemes.com/ 上下载的主题是 lovelace

下载下来的文件名是 lovelace.itermcolors

首先我们在 powershell 中 cd 到 ColorTool.exe 所在的文件夹 然后执行下面的命令

<img loading="lazy" src="/images/2020/15.svg" style="width: 800px;" />

&nbsp;

然后 powershell 会变成下面这样 已经快接近成功了

&nbsp;

<img loading="lazy" src="/images/2020/16.png" />

&nbsp;

此时在标题栏处右键 进入属性设置

&nbsp;

<img loading="lazy" src="/images/2020/17.png" style="width: 100%;" />

&nbsp;

然后在属性设置里面选择 **颜色** 选项卡

按照图中的要求 选好颜色好 点击保存

&nbsp;

<img loading="lazy" src="/images/2020/18.png" style="width:100%;" />

&nbsp;

点击保存后 重新打开 powershell 不出意外能看到下面的情况

&nbsp;

<img loading="lazy" src="/images/2020/19.png" style="width:100%;" />

&nbsp;

至此也就完成了颜色的改造

&nbsp;

**字体**

正如我们所见上面的还是跟 Paradox 主题的样式相差甚远 这是因为这个字体用了一些 **新宋体** 不支持显示的字符

而我们的控制台默认使用的字体正是 新宋体 ，如果你的语言是中文的话。

而 powershell 对字体的要求又比较苛刻 需要 powerline 型的字体，具体是什么要求不重要，感兴趣的朋友可以自行搜索。

这里我推荐使用 **更纱黑体**

Github 地址：https://github.com/be5invis/Sarasa-Gothic

但是我们不从这里下载 我们到清华大学开源软件镜像站 https://mirrors.tuna.tsinghua.edu.cn/

选择右侧的 <img loading="lazy" src="/images/2020/20.png" />

在字体栏目中选择 **Sarasa Gothic** 然后点击那个 **ttf** 的下载

<img loading="lazy" src="/images/2020/21.png" />

_下载下来的字体的压缩包是 **7z** 压缩格式的 可以到 https://www.7-zip.org/ 下载使用 7-zip 进行解压_

_当然使用你熟知的 360 压缩 快压 好压 等都能正常解压得到字体文件_

解压后得到的字体会比较的多

这里安装 sarasa-mono-sc 开头的字体就好了

sarasa-mono-sc-regular.ttf

sarasa-mono-sc-bold.ttf

sarasa-mono-sc-bolditalic.ttf

sarasa-mono-sc-extralight.ttf

sarasa-mono-sc-extralightitalic.ttf

sarasa-mono-sc-italic.ttf

sarasa-mono-sc-light.ttf

sarasa-mono-sc-lightitalic.ttf

sarasa-mono-sc-semibold.ttf

sarasa-mono-sc-semibolditalic.ttf

然后到 powershell 属性里面字体选项卡里面刚才安装的字体 选一个自己喜欢的字粗（字重）

<img loading="lazy" src="/images/2020/22.png" style="width:100%;" />

&nbsp;

然后点确定保存后会得到下面的效果

&nbsp;

<img loading="lazy" src="/images/2020/23.png" style="width:100%;" />

&nbsp;

到这里 你的 powershell 可以说已经是改造完成了。

&nbsp;
&nbsp;

---

如果你感兴趣，下面的东西你也可以看一看

---

#### 控制台的颜色

<img loading="lazy" src="/images/2020/24.png" style="width:100%;" />

&nbsp;

这 16 个颜色其实都有自己的名字

从左往右它们的名字分别为：

| 第几个 | 颜色名      | 第几个 | 颜色名   |
| :----- | :---------- | :----- | :------- |
| 01     | Black       | 09     | DarkGray |
| 02     | DarkBlue    | 10     | Blue     |
| 03     | DarkGreen   | 11     | Green    |
| 04     | DarkCyan    | 12     | Cyan     |
| 05     | DarkRed     | 13     | Red      |
| 06     | DarkMagenta | 14     | Magenta  |
| 07     | DarkYellow  | 15     | Yellow   |
| 08     | Gray        | 16     | White    |

知道这个之后我们就可以根据自己的喜好自己配置一个自己的主题

如果你比较喜欢白色背景的 PowerShell 那么你就可以借助上面的颜色名称

把 Black 设置为白色

把 White 设置为黑色

这样就实现了 窗口的反色

然后按照自己的习惯更改其他颜色为自己想要的颜色即可。

另外在使用过程中发现什么颜色不易看清的时候 也可以到这里自行修改。

&nbsp;

#### 自定义 oh-my-posh 的主题

首先在 powershell 中运行

```powershell
$ThemeSettings.MyThemesLocation
```

你会得到你的 oh-my-posh 的可以用来存放自定义主题的文件目录

这个目录默认是在 C:\Users\用户名\Documents\WindowsPowerShell\PoshThemes

这个 PoshThemes 目录并不会默认创建

这个目录可自行创建

自定义的主题的格式为 .psm1

主题模板为：

<img loading="lazy" src="/images/2020/25.svg" style="width: 800px;" />

&nbsp;

这里有一点要注意，这个文件本是 powershell 的文件，用 **#** 表示注释，但是若一行注册的内容都是中文，则会出现运行错误的情况，如上图的 `# 这里是自定义主题的渲染逻辑` 这一句就会造成运行错误

所以添加注释的时候 建议 每一行注释以一个英文字符结束，这样不会造成运行错误

一般情况下，面对这么长乱七八糟的 powershell 的命令着实让人头疼，所以到

C:\Users\用户名\Documents\WindowsPowerShell\Modules\oh-my-posh\2.0.385\Themes

中复制一个出来，然后在此基础上修改。

&nbsp;

下面是我自定义的一个主题的源码 文件名是 my.psm1

<img loading="lazy" src="/images/2020/26.svg" style="width: 1200px;" />

&nbsp;

主题效果 比较简约 没有花里胡哨的东西

&nbsp;

<img loading="lazy" src="/images/2020/27.png" />

若要使用自己自定义的主题 一般是可以修改

C:\Users\用户名\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1

文件中的 **Set-Theme** 字段

如果我的主题的文件名是 xxx.psm1 那么 就把 Set-Theme 那一行 改为 `Set-Theme xxx`

比如我的就是 `Set-Theme my`

&nbsp;

下面是源码 可以复制的 😀

```powershell
#requires -Version 2 -Modules posh-git

function Write-Theme {

    param(
        [bool]
        $lastCommandFailed,
        [string]
        $with
    )

    # 第一个符号的颜色 color of the first char
    $firstColor = $sl.Colors.FirstSymbolSuccessColor

    # 上一条命令如果有错误则改变颜色  if last command failed, change the "firstColor"
    If ($lastCommandFailed) {
        $firstColor = $sl.Colors.FirstSymbolFailColor
    }

    # 打印用户名 print the username
    $user = $sl.CurrentUser

    # 是否是管理员模式的命令行 check for elevated prompt
    If (Test-Administrator) {
        $prompt += Write-Prompt -Object "$($user) " -ForegroundColor $sl.Colors.AdminIconForegroundColor
    } else {
        $prompt += Write-Prompt -Object "$($user) " -ForegroundColor $sl.Colors.DriveForegroundColor
    }

    # 打印当前所在目录 print the drive portion
    $prompt += Write-Prompt -Object "$(Get-FullPath -dir $pwd)" -ForegroundColor $sl.Colors.DriveForegroundColor

    # 当前目录为一个git仓库时渲染出git相关信息 print some information about git repository
    $status = Get-VCSStatus
    if ($status) {
        $prompt += Write-Prompt -Object " (git: " -ForegroundColor $sl.Colors.GitForegroundColor
        $prompt += Write-Prompt -Object "$($status.Branch))" -ForegroundColor $sl.Colors.GitForegroundColor
        if ($status.Working.Length -gt 0) {
            $prompt += Write-Prompt -Object (" " + $sl.PromptSymbols.GitDirtyIndicator) -ForegroundColor $sl.Colors.GitDefaultColor
        }
    }

    # 换行输入命令 Writes the postfix to the prompt
    $prompt += Set-Newline
    $prompt += Write-Prompt -Object "> " -ForegroundColor $firstColor
    $prompt
}

# 配置项 local settings
$sl = $global:ThemeSettings
## 字符配置 char settings
$sl.PromptSymbols.HomeSymbol = [char]::ConvertFromUtf32(0xFF5E)
## 颜色配置 color settings
$sl.Colors.GitForegroundColor = [ConsoleColor]::DarkCyan
$sl.Colors.AdminIconForegroundColor = [ConsoleColor]::Cyan
$sl.Colors.FirstSymbolSuccessColor = [ConsoleColor]::Green
$sl.Colors.FirstSymbolFailColor = [ConsoleColor]::Red
```
