# Template Usage Skills and Explanations

## 2025 新增功能说明

### 作者的话

本项目 (pkuthss-undergraduate-eecs-2025) 在原版基础上根据 2025 年毕业审查要求进行了修改。由于教务通常只提供 word 模板，本项目旨在为不习惯 word 的同学提供一个能在 Overleaf 及本地顺利编译并符合格式审查的 LaTeX 替代方案。
使用此模板时，请先与手中教务下发的最新模板进行比较，确保大致格式没有区别。

如果你偏好 Typst，也可考虑社区中相关的 pkuthss-typst 模板。本模板的全部修改详情和毕设流程提示，请参阅项目的 `README.md`。

### 使用示例

* **水平排列子图**：使用 `\subfloat` 并在子图之间避免空行。
* **表格插入**：使用 `\begin{table}` 环境，结合 `\toprule`, `\midrule`, `\bottomrule` 绘制三线表。
* **伪代码**：使用 `algorithm2e` 环境编写（如果偏向 `algorithm` 宏包，请在 `main.tex` 内注释掉对应包）。
* **代码块显示**：使用 `\begin{lstlisting}` 及相关的 `lstset` 配置呈现格式化的代码块。

---

## 硕士/本科模板基础说明

本模板基于 `pkuthss` 适配而来，主要讲解论文中常见的排版问题：

### 封面及 pkuthssinfo 相关
相关的配置变量与 `pkuthss` 原文档类一致。通过修改 `main.tex` 下的 `\pkuthssinfo` 内容（如 `ctitle`, `cauthor`, `mentorlines` 等），可以控制封面上显示的信息。

### 字体设定
本文档提供多种字体设定（`fontset`）：`windows`, `windows@overleaf`, `mac`, `ubuntu`, `fandol`。
* **推荐**：在 Overleaf 平台下默认且推荐使用 `fandol`。
* **报错处理**：若遇到极个别生僻字无法显示，可切换至 `ubuntu` 模式，或上传对应 `.ttf` 字体后使用 `windows@overleaf`。

### 版权声明与原创页
写作指南要求从门户下载相关 PDF 替换原始的占位文件。由于部分 PDF 浏览器对字体的渲染效果不同，建议最终打印时使用 Acrobat。
另外，电子版必须包含原创答辩签名等内容的扫描件。目前的 PDF 覆盖插入使用了 `textblock` 和 `colorbox` 进行遮掩，确保页码与目录正常。

### 摘要与目录
* 中英文摘要分别在 `cabstract` 和 `eabstract` 环境内撰写。若受基金资助，需在中文摘要第一页页脚标注。
* 目录已通过内部调整实现了章级别的点线，且对间距、字体进行了调优。

### 主要符号对照表
请参考模板中的 `chap/deno.tex`。在 `denotation` 环境中，使用 `\item[X] Y` 追加符号。*注意不要在符号处直接输入英文字符的中括号*。

### 图表相关
* **表格**：学术排版一般需使用三线表，依赖 `booktabs` 宏包。长表格可使用 `longtable` 实现分页。若需表格内容脚注，可以用 `minipage` 嵌套。
* **图片**：多子图排版推荐 `subfloat` 宏包。若需两个独立图片并排（且分别编号），可以使用左右两个 `minipage` 包含单独的 `\includegraphics`。

### 公式
公式排版使用原生的 LaTeX 和 `amsmath` 体系。推荐配合 Mathpix 类的抓取识别工具快速生成长公式。

### 参考文献
本模板依照要求使用了 `biblatex` 宏包的 `gb7714-2015` 格式，支持顺序编码制（或通过修改选项变为著者-出版年制 `gb7714-2015ay`）。在正文中配合 `\cite`, `\citet`, `\citeauthor` 等指令即可正确渲染。

---

## 理论基础与 Overleaf 适配

### Overleaf 适配中的问题
原始的 pkuthss 使用通过 `CTeX` 配合 Windows 商用字体库进行排版，但在 Linux 内核的 Overleaf 等线上环境中可能会出现缺字体等问题。

### Fontset 的选择与实现
为了解决字库问题，模板定义了不同的参数组。
* **Fandol**：由于版权合规与字符覆盖面均衡，设为 Overleaf 的最佳推荐。
* **Ubuntu** 等宽字体作为备用。
为了达到粗体排版效果，当 Windows 下的中易宋体无原生粗体时，本模板会自动通过“伪粗体（FakeBold）”等方式呈现粗体。

请确保所有文件（包括自包含在项目内的 `.def` 或引用的包）均为 **UTF-8 编码**，并使用 **XeLaTeX** 引擎编译。