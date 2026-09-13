# Zeyu Wu — Personal Homepage

一个只有两个板块的静态个人主页：**About** + **Publications**。
纯 HTML + CSS，没有框架、没有构建步骤、没有 JavaScript。

## 文件结构

```
.
├── index.html              # 全部内容 + 样式都在这一个文件里
├── assets/
│   ├── cv.pdf              # 占位 PDF（页面上已无 CV 入口，可删）
│   └── img/
│       ├── photo.png       # 头像（400×400）
│       └── favicon.svg     # 浏览器标签页图标
└── .nojekyll               # 让 GitHub Pages 不要跑 Jekyll
```

## 已经填好的内容

顶部标题区（按用户要求**收成一行**）：

```
Zeyu Wu
Master's Student at the University of Macau
Email · Google Scholar
```

姓名、标题行（`Master's Student at the University of Macau`）、
About 段落（含 University of Macau / Prof. Derek F. Wong / NLP²CT Lab /
Dr. Junchao Wu / Shenzhen Technology University / Prof. Hang Yin 六个链接）、
**Email（`nlp2ct.zeyu@gmail.com`）与 Google Scholar 主页链接**，
以及全部 11 篇论文（7 篇主要论文 + 4 篇项目论文（本科），标题、作者、出处都已核实）
—— 这些都不用再动了。

顶部链接行按用户要求**只保留 Email 和 Google Scholar 两个**，GitHub / ORCID / CV 已移除。

## 还需要改的：无

所有占位内容都已替换完毕，`index.html` 可以直接 push。

**换头像**：把新图片覆盖成 `assets/img/photo.png`（方形图效果最好，
页面会裁成圆形显示，尺寸 110×110，手机上 90×90）即可，HTML 不用动。

`assets/cv.pdf` 是早期 CV 链接用的占位 PDF，现在页面上没有 CV 入口了，可以留着也可以删。


### 改论文列表

论文列表分成**两组**，中间用一条横线（`<hr class="pub-sep">`）隔开，横线下方是
`<p class="pub-group">Project Papers (Undergraduate)</p>` 这个小标题：

- **第一组**：7 篇主要论文（EMNLP / ICLR / ACL / TACL / NLPCC）
- **第二组**：4 篇项目论文（本科）——Frontiers in Plant Science、Agriculture、
  Mathematics、Scientific Reports

每篇论文就是一段 `<li>`，**加一篇 = 复制一整段 `<li>...</li>`**，**删一篇 = 删掉一整段**。

```html
<li>
  <div class="pub-title">论文标题</div>
  <div class="pub-authors">
    <strong>Zeyu Wu</strong>*, 合作者 A*, 合作者 B, Derek F. Wong
  </div>
  <div class="pub-venue">
    期刊/会议全称, 卷(期), 页码, 年份。
  </div>
</li>
```

- 自己的名字已经写成 `<strong>Zeyu Wu</strong>`，会显示成加粗——这是学术主页的通行做法。
- `*` 表示共同一作、`†` 表示通讯作者，页面上 Publications 标题下方已有一行图例说明。
- 论文条目现在**只有标题、作者、出处三行纯文字**，没有 arXiv / PDF / Code 链接。
  标题本身是超链接（指向 arXiv 或期刊 DOI）。想彻底去掉，删掉包在标题外面的 `<a href="...">` 即可。
- 两组都**按时间倒序排列**（新的在上）。同一年的论文按会议/出版时间先后排，
  所以 2026 年那几篇的顺序是 EMNLP 2026 → NLPCC 2026 → ACL 2026 → ICLR 2026。
  想改成由旧到新，把每个 `<ul>` 里的 `<li>` 块整体倒过来即可。
- **例外**：Ngft（Neuron-Guided Fine-Tuning）被单独提到第一位 —— 两篇 EMNLP 2026
  Findings 并列，Ngft 是共同一作的第一篇，所以放在最前。想恢复纯时间序，
  把它和第 2 条对调即可。
- 横线不要了，就删掉 `<hr class="pub-sep">` 和 `<p class="pub-group">…</p>` 两行；
  想把两组合并成一组，把第二组的 `<li>` 挪进第一组的 `</ul>` 之前。

### 现有 11 篇论文的出处（备查）

**主要论文**（页面上的排列顺序）

| 论文 | 出处 | 页面上标题的链接指向 |
| --- | --- | --- |
| Neuron-Guided Fine-Tuning (Ngft) | Findings of EMNLP 2026 | arXiv:2609.05913 |
| Before the Arrest: Benchmarking LLMs on Criminal Profiling from Incomplete Evidence | Findings of EMNLP 2026 | 暂无（论文尚未公开上线，标题为纯文本；上线后把 `<a href="链接">` 包到标题外面即可） |
| Overview of NLPCC 2026 Shared Task 6 | NLPCC 2026 | 无链接 |
| DetectRL-X | ACL 2026 | arXiv:2605.15518 |
| Neuron-Aware Data Selection in Instruction Tuning (Nait) | ICLR 2026 | arXiv:2603.13201 |
| RepreGuard | TACL 2025 | arXiv:2508.13152 |
| Fraud-R1 | Findings of ACL 2025 | arXiv:2502.12904 |

**项目论文（本科）· Project Papers (Undergraduate)**（页面上的排列顺序）

| 论文 | 出处 | 页面上标题的链接指向 |
| --- | --- | --- |
| Incorporating Dataset-Level Semantic Priors into LLMs for Environmental Time-Series Forecasting | Scientific Reports, 2026 | doi:10.1038/s41598-026-57634-8 |
| A Multivariate Soil Temperature Interval Forecasting Method… | Frontiers in Plant Science, 15, 1460654, 2024 | doi:10.3389/fpls.2024.1460654 |
| A Hybrid Medium and Long-Term Relative Humidity Point and Interval Prediction Method… | Mathematics, 11(14), 3247, 2023 | doi:10.3390/math11143247 |
| A Multistep Interval Prediction Method… for Egg Production Rate | Agriculture, 13(6), 1255, 2023 | doi:10.3390/agriculture13061255 |

## 部署到 GitHub Pages

**方式一：用户站**（访问地址就是 `https://你的用户名.github.io`，推荐）

1. 在 GitHub 新建一个仓库，名字必须是 `<你的用户名>.github.io`
2. 把本目录下**所有文件和文件夹**（`index.html`、`assets/`、`.nojekyll`，注意不要把外层文件夹本身传上去）push 到仓库的 `main` 分支
3. 等 1~2 分钟，直接访问 `https://你的用户名.github.io`

**方式二：项目站**（访问地址是 `https://你的用户名.github.io/仓库名/`）

1. 新建一个任意名字的仓库，把文件 push 上去
2. 进仓库 **Settings → Pages** → Source 选 `Deploy from a branch`，分支选 `main`、目录选 `/ (root)` → Save
3. 等 1~2 分钟，访问 `https://你的用户名.github.io/仓库名/`

页面里所有链接都是相对路径，两种方式都不需要改代码。

## 本地预览

直接双击 `index.html` 用浏览器打开即可。想用本地服务器的话：

```bash
python3 -m http.server 8000
# 然后打开 http://localhost:8000
```

## 备注

- 配色在 `index.html` 顶部的 `<style>` 里，改 `--link` 可以换主色。
- 页面是英文的。想改中文，直接把正文文字换成中文即可，字体栈里已经包含苹方和微软雅黑。
