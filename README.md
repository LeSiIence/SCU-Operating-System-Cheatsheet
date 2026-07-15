# OS Exam Reference Sheet of Sichuan University

## 2026 春季学期四川大学操作系统课程半开卷考试参考资料

本仓库提供一份面向 **四川大学 2026 年春季学期操作系统课程** 的半开卷考试参考资料。

资料使用 LaTeX 编写，采用 A4 横向四栏紧凑排版。主要内容以英文表述，并为重要概念附有中文检索提示，便于考前复习和考试时快速查找。

> [!IMPORTANT]
> 本仓库为个人整理的非官方学习资料。考试是否允许携带资料，以及允许携带的页数、纸张尺寸、单双面和打印方式，请以任课教师及当学期考试通知为准。

---

## How to use

### 1. 直接使用 PDF

仓库中的 [`cheatsheet.pdf`](./cheatsheet.pdf) 是已经编译完成的参考资料，可以直接下载、查看或打印。

建议打印设置：

* A4 纸张
* 横向打印
* 100% 或“实际大小”
* 打印前确认图片、公式和四栏内容显示完整

不建议使用“适合页面”进行大幅缩放，否则正文可能过小。

### 2. 修改 LaTeX 源文件

完整源文件为 [`cheatsheet.tex`](./cheatsheet.tex)。

推荐使用 XeLaTeX 编译：

```bash
xelatex cheatsheet.tex
```

也可以使用 LuaLaTeX：

```bash
lualatex cheatsheet.tex
```

如果交叉引用或链接没有及时更新，可以连续编译两次：

```bash
xelatex cheatsheet.tex
xelatex cheatsheet.tex
```

### 3. 在 Overleaf 中使用

1. 下载本仓库 ZIP，或者将 GitHub 仓库导入 Overleaf。
2. 将主文档设置为 `cheatsheet.tex`。
3. 将编译器设置为 **XeLaTeX**。
4. 确认仓库中的配图文件已一并上传。
5. 编译并下载生成的 PDF。

---

## Covered topics

当前资料覆盖以下内容：

| Chapter    | Topic                              |
| ---------- | ---------------------------------- |
| Chapter 1  | 计算机系统概述、寄存器、中断、存储层次、缓存与 DMA        |
| Chapter 2  | 操作系统目标、服务、ISA / ABI / API、系统调用与双模式 |
| Chapter 3  | 进程、进程映像、PCB、五状态与七状态模型、挂起和进程切换      |
| Chapter 4  | 线程、进程与线程的区别、ULT、KLT 和混合线程模型        |
| Chapter 5  | 并发、竞态条件、临界区、互斥、信号量与生产者—消费者         |
| Chapter 6  | 死锁条件、预防、避免、检测、银行家算法与安全状态           |
| Chapter 7  | 内存管理、分区、碎片、伙伴系统、分页与地址转换            |
| Chapter 8  | 虚拟内存、TLB、缺页、页面置换、工作集与抖动            |
| Chapter 9  | 单处理器调度、FCFS、RR、SPN、SRT、HRRN 与反馈调度  |
| Chapter 10 | 多处理器、多核调度与实时系统                     |
| Chapter 12 | 文件组织、目录、B-tree、记录分块与文件分配           |

资料中还包括：

* 英文核心术语与中文检索提示
* 各章快速索引和重点回顾
* 教材复习题及简要答案
* 典型计算题的公式与结论
* 页面置换算法对比
* 银行家算法与死锁检测
* CPU 调度甘特图
* 分页和分段地址转换
* 文件分配与 B-tree 相关题目

---

## Layout and macros

资料采用：

* A4 横向页面
* 6 mm 页边距
* 四栏排版
* 紧凑字号与行距
* 绿色关键词和浅色提示框
* 中英文混排

源文件中定义了若干便于编写速查表的宏。

### 一级标题

```latex
\cheatsection{Process Management}
```

### 二级标题

```latex
\cheatsubsection{Process States}
```

### 带中文提示的术语

```latex
\term[就绪]{Ready}
```

显示效果近似为：

```text
Ready（就绪）
```

### 行内代码或符号

```latex
\code{semWait()}
```

### 重点提示框

```latex
\note{Ready waits for the CPU; Blocked waits for an event.}
```

### 紧凑题目条目

```latex
\begin{stemlist}
  \stemrow[死锁四条件]{R6.3}{
    Mutual exclusion, hold and wait,
    no preemption, and circular wait.
  }
\end{stemlist}
```

---

## Requirements

推荐安装较完整的 TeX 发行版。

### Windows

可以使用：

* TeX Live
* MiKTeX

### macOS

推荐安装 MacTeX。

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install texlive-full
```

检查 XeLaTeX 是否可用：

```bash
xelatex --version
```

---

## Repository structure

当前仓库的核心文件为：

```text
OS_cheatsheet/
├── README.md        # 仓库说明
├── cheatsheet.tex   # 完整 LaTeX 源文件
├── cheatsheet.pdf   # 编译完成的参考资料
└── *.png            # 进程状态图和资源分配图等配图
```

---

## Contributing

欢迎通过 Issue 或 Pull Request：

* 纠正概念、公式或题目答案
* 补充遗漏知识点
* 改进中英文表述
* 优化 LaTeX 排版
* 修复文字溢出、图片缺失或编译问题
* 补充更清晰的图示和快速检索提示

推荐工作流：

```bash
git switch main
git pull
git switch -c docs/update-cheatsheet
```

修改后进行编译检查：

```bash
xelatex cheatsheet.tex
git diff
```

提交并推送：

```bash
git add cheatsheet.tex cheatsheet.pdf README.md
git commit -m "docs: add repository README"
git push -u origin docs/update-cheatsheet
```

然后在 GitHub 创建 Pull Request。

---

## Accuracy and academic integrity

本资料不是四川大学或课程教学团队发布的官方资料，可能存在遗漏、简化或错误。使用时请结合：

* 课程教材
* 教师课件
* 课堂笔记
* 作业与习题
* 当学期考试通知

请勿将本仓库用于违反考试纪律、课程规定或学术诚信要求的行为。

## License

## License

本仓库中的教材内容、课程资料、习题、图表及其他引用材料，其著作权归原作者、出版社、课程教师或其他相关权利人所有。

本仓库仅对相关内容进行学习性整理、摘录和排版，目的在于课程复习与个人学习，不主张对第三方材料享有著作权，也不用于商业用途。

除第三方材料外，本仓库中由维护者原创的排版代码、整理结构、中文提示、索引及补充说明，可在注明来源的前提下用于非商业学习与交流。

如本仓库中的内容侵犯了您的合法权益，请通过 Issue 或 Email 联系维护者，相关内容将在核实后及时修改或删除。
