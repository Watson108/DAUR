
# 软件准备

本节主要介绍R与RStudio的基础知识、安装方式与相关资源。这里所有的示例均以Windowns 10系统下的R 3.4.2版本为例进行，适用于任何R 3.0.0以上版本。RStudio说明适用于以RStudio 1.0以上版本。

## R安装与设置


### R简介

R是一个免费自由且跨平台通用的统计计算与绘图软件，它有Windows、Mac、Linux等版本，均可免费下载使用。R项目(The R Project for Statistical Computing)最早由新西兰奥克兰大学（Auckland University）的Robert Gentleman（1959-） 和 Ross Ihaka（1954-） 开发，故软件取两人名字的首字母命名为R。该项目始于1993年，2000年发布了首个官方版本R 1.0.0，后期维护由R核心团队[（R Core Team）](https://www.r-project.org/contributors.html)负责。截止2017年10月，已发布到 3.4.2版本。凭借其开源、免费、自由等开放式理念，R迅速获得了流行，目前已成为学术研究和商业应用领域最为常用的数据分析软件之一。

从[R主页](https://www.r-project.org/)中选择[download R](https://cran.r-project.org/mirrors.html)链接可下载到对应操作系统的R安装程序。打开链接后的网页会提示选择相应的[CRAN](https://cran.r-project.org/mirrors.html) ^[CRAN是Comprehensive R Archive Network（R综合典藏网）的简称，它提代R核心开发者提供的主程序、源代码和说明文件，也收录其他用户撰写的软件包。]镜像站 ^[镜像站(mirror sites)是网站的复制版本，将网站中的部分网页按原来的结构复制出来，即所谓“镜像”；再将这些镜像放置于具有独立网址的服务器中，以便缓解主站服务器的流量负荷，从而提升访问速率或作为备选网站在主站服务器出现意外时提供正常访问功能。]。目前全球有超过一百个CRAN镜像站 ，用户可选择就近下载。Windows平台下也可直接点击此链接 <http://cran.r-project.org/bin/windows/base/release.htm> 直接下载最新版的R进行安装。


### R的安装与初步尝试

程序下载完毕后，双击安装程序、选择对应的32位或64位程序（若不明白这其中的区别，可选择同时安装）即可安装。初学者可按默认设置安装在系统盘，并选择一切默认设定完成安装程序。高级用户可参考[谢益辉](https://yihui.name/)等人的[安装经验](https://bookdown.org/yihui/r-ninja/setup.html#r)进行相关设置，如安装时去掉版本号以便于日后更新R包。初学者可先略过某些技术细节，将注意力集中于数据分析本身。


安装完毕后，打开R，可看到R的操作界面，称为R控制台（R console）。类似其他以编程语言为主要工作方式的软件，R的界面简洁而朴素，类似一个空白的写字板。但在这一朴素的外表下，是丰富而复杂的运算功能。

在R命令提示符`>`后输入相关命令，并摁回车键即可展示相关结果。在不知道任何R命令的情况下，你也可将R作为一个高级的科学计算器使用。

通过一些简单的R命令，可更好地了解R的风格。例如
```r
data()
```
这一命令可展示R自带的所有数据集，R数据的后缀名为`.RData`。注意命令中的`()`是不可缺少的，是R命令的有机组成部分。可以发现其中有一个`mtcars`数据集。欲了解这一数据集的内容，可输入如下命令
```r
?mtcars
```

`?`表示求助。此时会在默认浏览器 ^[建议使用Chrome浏览器。]中打开一个新的网页，介绍此数据的来源及各变量的具体定义与测量单位。查阅文档可知，`mtcars`数据是从1974年美国汽车趋势（Motor Trend）杂志中抽取了32辆汽车的基本性能数据，并对各变量的含义与单位进行了详细说明。以后会利用该数据进行基本展示，读者应自行花一分钟的时间去了解该数据中各变量的具体含义。

直接键入`mtcars`会在R中直接展示整个数据。若数据太长，则可能占据太多空间或消耗大量时间。如只想直观了解数据的基本形式，使用`head()`命令即可展示某一数据的前几行（默认6行），也可通过以下方式展示指定数据的前若干行
```{r}
head(mtcars, 5)
```
如此即可展示`mtcars`数据前5行。结果中的两个`##`号，表示默认的命令结果提示。

相信你很快就能猜出`tail(mtcars, 5)`是何功能。


## R包安装与加载

R的初始安装程序只包含少数几个基础模块和若干基础安装包（base packages），使用它们虽已能完成诸多统计分析与可视化呈现的工作，但往往需要安装并加装其他开放性的软件包来实现更多功能或简化相关的操作流程。这些附加包通常通过CRAN镜像站下载安装，并在加载后可调用相关函数执行计算或绘图功能。一般而言，安装R包的方式有三种。

### 在线安装


在线安装R包命令为`install.packages(" ")`，`""`中填入软件包的名称 ^[遵从R开发者的书写惯例，在描述R命令的名称时也应带上小括号`()`，以表示这是一个R命令。]。例如，在R命令窗口（即所谓的R控制台）中的`>`符号后输入如下命令：
```r
install.packages("dplyr")
```
确保电脑联网，选择镜像后点击确定即可在线安装软件包`dplyr`。其中的双引号`""`也可使用单引号`''`替换。安装成功后应出现如下提示：
```r
package ‘dplyr’ successfully unpacked and MD5 sums checked
```

在`install.packages()`命令中不能省略双引号或单引号，否则会出现如下错误提示：

```r
Error in install.packages : object 'dplyr' not found
```

若想一次性安装多个包，可使用如下方式：
```r
install.packages(c("Package A", "Package B"))
```
即使用`c()`将不同的包加以联接，中间加上逗号。字母`c`的含义其实正是联结（concatenate，或理解为combine更容易记忆）。

如此，可使用如下方式安装常用的数据分析包和RStudio文档写作与展示相关包：
```r
install.packages(c("ggplot2", "dplyr", "tidyr", "stringr", "lubridate", "readr", "readxl", "haven", "httr", "rvest", "xml2", "devtools", "tidyverse"))
```

读者不妨将此命名拷走并运行。由于一次性安装的包比较多，可能需要几分钟左右的时间才能安装完毕上述所有包。

### 离线安装

由于网络问题，在线安装有时可能出错，此时可选择离线安装。

离线安装首先要求有相关R包的压缩包。如已确定所想安装的包名，在CRAN网站上选定镜像站后，点击左侧的Packages一栏，可看到所有在该网站上储存的R包。点击R包名称进入相关页面，找到Windows Binaries一行对应的`.zip`文件，下载到本地电脑（Mac系统选择`.tgz`文件）。该文件无需解压缩，打开R后，遵循以下路径安装该压缩包`Packages-->Install package(s) from local files`，点击后选择安装包即可完成安装。

离线安装的问题在于，有些 R 包的功能依赖于另外一些包，因此需要同时安装其所依赖的其他它。采用离线安装时无法加载这些包。

### GitHub安装

存放于CRAN上的包通常是较为成熟、某种程度上讲也是相对滞后的包。包在维护和更新过程中会增加一些新的功能，或者总会有一些新的试验性的包出现，以满足用户的功能。这些旧包的更新版、或者是未曾公开推出的新包，通常会以开发版（development version）的形式储存于类似[GitHub](https://github.com)这样的代码托管平台 ^[GitHub 是一个面向开源及私有软件项目的托管平台，于 2008 年 4 月 10 日正式上线，是目前全球规模最大的社会化编程及代码托管网站。]，而并未提交到CRAN。甚至有开发者本人并无意向将自身开发的R包提交至CRAN镜像。此时，前述两种安装方式就不再有效。

若想直接从GitHub安装相关包，建议通过Hadley开发的`devtools`包完成安装。以下是基本步骤：

1. 安装`devtools`包（请复习并实践第一种安装法）。
2. 加载该包，即输入`library(devtools)`。
3. 使用其中的`install_github()`函数完成安装。

以下是示例。
```r
install.packages("devtools")
library(devtools)
install_github("hadlley/dplyr")
```
`install_github()`命令要求先给出开发者名字再给出包名。这对于只知道包名而不知道开发者名字的用户是不利的。好在使用这一安装方式的通常为中高级用户，他们自可从GitHub页面找到相关包并阅读其安装说明后安装。

为更好地利用GitHub及R的相关功能，同时建议Windows用户安装[`Rtools`工具](https://cran.r-project.org/bin/windows/Rtools/)。这是用于在Windows平台下开发 R 包和 R 本身的软件插件。

### R包加载

使用R基础安装包中的函数进行数据分析时，直接调用函数即可，无需先加载这些包。


若要引入附加包中的函数进行数据分析，首先要加载这些包。这有两种方式。

一是使用加载命令`library()`，此时包的名称不需要加引号。例如：
```r
library(dplyr)
```
此时会出现如下显示：
```r
载入程辑包：‘dplyr’

The following objects are masked from ‘package:stats’:

    filter, lag

The following objects are masked from ‘package:base’:

    intersect, setdiff, setequal, union
```

此中内容先不加过多解释，其基本要点是：加载此包之后，即可使用此包中的`filter()`、`lag()`等函数，而原基础安装包中的同名函数则会被最近一次引入的包中的函数所覆盖（即失效）。


二是使用双冒号`::`的形式调用某一函数，其用法为`package_ name::function_name`，即先写包名，双冒号后写入函数名称，即可调用该包中的这一函数。

```{r}
dplyr::sample_n(mtcars, 2)
```

上述命令表示，使用`dplyr`包中的`sample_n()`函数，从`mtcars`数据中任取两行。

退出R时无需先“退出”包再退出R，保存数据对象后直接关闭R即可。

### 工作目录设置

R 默认读入和写出的数据对象都存储在当前工作目录（working directiory）中。若要读入其他目录中对象，则需要指定工作路径。一般而言，开始某个数据分析项目时，即可新建一个目录并将其设定为当前工作目录。此后所有的数据对象均储存其中。

对使用中文操作系统的分析者而言，为避免因汉字编码问题而在读入文件和分析数据时发生莫名的错误，首先需要明确一条**基本命名规则**：R 中的目录名和文件名不能有中文，也不要出现除中划线 `-` 和下划线 `_` 之外的特殊字符，而只使用英文字母、数字以及 `-` 和 `_` 的组合。

对普通用户而言，建议在非系统盘（如D盘、E盘等）的根目录下建立数据分析目录。创建新目录可直接在操作系统中进行，也可在R 中使用命令`dir.creat(" ")`建立新目录，`" "`中输入路径名和目录名，例如：

```r
dir.create("D:/R2017")
```

此时即可在D盘根目录下找到名为 R2017 的目录。

**注意**：R 中的路径分隔符为正斜杠（forward slash）`/`，而不是反斜杠（backward slash）`\`。正反斜杠的译法多少有些令人费解，不妨取名为撇斜杠（/）和捺斜杠（\\），更适合中国人的理解方式。

如目录已创建，可通过命令`setwd()`将该目录设为当前工作路径，例如：

```r
setwd("D:/R2017")
```
其中`wd`即working directory的首字母缩写。


设置完毕后，可通过`getwd()`命令查看当前工作路径，此时括号中不需要填入任何内容。


### 语言选项设置

也许你已注意到前面提示中出现了“程辑包”而不是“程序包”这种古怪的翻译。这是因为 R 的相关中文提示最早并非由中国大陆人士翻译所致。实际上，按照其默认的中文提示（如错误提示）进行网络搜索，通常不能找到很好的资源。这一方面是由于翻译质量与翻译习惯问题，另一方面是由于国内的中文R社区在活跃度和技术水平上与国外的成熟社区还有较大距离。因此，安装完R后的第一项设置，可考虑修改默认语言选项，将其设为英文。

若想使修改后的语言选项仅对此次打开的R有效，可使用如下命令：
```r
Sys.setenv(LANG = "en")
```
`Sys.setenv()`是修改环境变量函数，`Lang`表示语言（language），`en`表示英语（English）。这样在将来出现错误提示时，可使用搜索引擎检索到相关解答资源。注意应当使用英文搜索引擎来搜索英文资源，以提高效率。

这种做法的劣势在于关闭R而重新打开后，其默认语言选项仍是中文。严格来说，这并不是R本身的设置，而是它默认采用Windows系统的默认语言。对于大陆人士而言，其所使用的Windows操作系统通常默认语言为中文，因此R会使用中文提示。为一劳永逸地改变此版本下的R的默认语言，可采用如下方式：

1. 找到安装路径下`etc`文件夹中的`Rconsole`文件。如选择默认安装方式，R通常安装在C盘的Program Files目录下。以本人写作此文档时的R版本为例，其路径为：`C:\Program Files\R\R-3.3.3\etc`。
2. 用文本编辑器打开`Rconsole`文件。建议安装[Notepad++软件](https://notepad-plus-plus.org/)而不是使用Windows自带的记事本软件打开^[Notepad++也是一个免费的自由开源软件。之所以推荐使用它而不是记事本，原因比较复杂，涉及计算机的字符编码问题，暂不必深究。仅了解一点即好：如有可能，Windows平台下尽可能使用Notepad++而不是其自带的记事本软件创建或修改文本文件。]。找到以下文字：
```r
## Language for messages
language = 
```
3. 通常来说，`=`号后面默认是空白，以便调用Windows的默认语言。在 `=`后填入指定的语言缩写，保存修改后关闭该文档，即可永久性修改默认语言设置。例如：
```r
## Language for messages
language = en
```

其中`en`就表示English。保存后关闭（Windows系统可能会提醒需要管理员权限方可修改，点击确定），重新打开R，应当可以看到所
有提示文字已变为英文:

```r

R version 3.4.2 (2017-09-28) -- "Short Summer"
Copyright (C) 2017 The R Foundation for Statistical Computing
Platform: x86_64-w64-mingw32/x64 (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

[Previously saved workspace restored]
```

使用R，即意味着基本告别中文操作与提示。请尽快转向并熟练英文环境下的相关操作，这对提升R的使用效率至关重要。


ti
