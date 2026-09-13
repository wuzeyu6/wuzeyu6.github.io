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
├── .nojekyll               # 让 GitHub Pages 不要跑 Jekyll
└── .gitignore              # 忽略 .DS_Store
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

## 部署到 GitHub Pages（推荐：用户站）

访问地址就是 **https://wuzeyu6.github.io/**，最干净。仓库名必须是 `<用户名>.github.io`。

**本目录的 git 仓库已经初始化好了**（`main` 分支已提交，`origin` 已指向
`https://github.com/wuzeyu6/wuzeyu6.github.io.git`），所以只剩两步：

**第 1 步｜在 GitHub 上建仓库**

打开 https://github.com/new ，填：

| 字段 | 填什么 |
| --- | --- |
| Repository name | `wuzeyu6.github.io` ← **必须完全一致** |
| Description | 随便，可留空 |
| Public / Private | 选 **Public**（私有仓库的 Pages 需要付费账号） |
| Add a README file | **不要勾**（勾了会和本地提交冲突，得先 pull 一次） |
| .gitignore / license | **都不选**（本地已经有 `.gitignore` 了） |

点 **Create repository**。建好后页面会显示一堆 `git remote add origin …` 的命令，
**不用管**，本地已经配好了。

**第 2 步｜在终端里 push**

```bash
cd /Users/wu/WorkBuddy/2026-09-13-23-32-04/site
git push -u origin main
```

第一次会弹出认证：

- **Username**：`wuzeyu6`
- **Password**：**不能填 GitHub 登录密码**（GitHub 2021 年起已停用密码认证），
  必须填 **Personal Access Token**。

**怎么拿 Token**：GitHub 右上角头像 → Settings → 左侧拉到底 **Developer settings**
→ **Personal access tokens** → **Tokens (classic)** → **Generate new token (classic)**
→ 勾选 **`repo`** 这一个权限 → 有效期自选（建议 90 天）→ Generate
→ 把 `ghp_` 开头的那串**复制下来**（离开页面就再也看不到了）。

下次再 push 时，macOS 的钥匙串（git 已配置 `credential.helper=osxkeychain`）
会自动记住，不用反复输入。

**第 3 步｜等待上线**

推完后等 1~2 分钟，浏览器打开 **https://wuzeyu6.github.io/** 即可。
仓库 **Settings → Pages** 里能看到部署状态（分支应为 `main`、目录 `/ (root)`）。

---

### 方式二：项目站

如果你不想用 `wuzeyu6.github.io` 这个仓库名，可以建任意名字的仓库（比如 `homepage`），
访问地址变成 `https://wuzeyu6.github.io/homepage/`。区别是多一步手动开启：

1. 建仓库时**同样不要**勾 README / gitignore
2. `git remote set-url origin https://github.com/wuzeyu6/<仓库名>.git` 后 push
3. 进仓库 **Settings → Pages** → Source 选 `Deploy from a branch` →
   分支 `main`、目录 `/ (root)` → **Save**
4. 等 1~2 分钟访问 `https://wuzeyu6.github.io/<仓库名>/`

页面里所有链接都是相对路径，两种方式都不用改代码。

### 以后怎么更新

改完 `index.html` 后：

```bash
cd /Users/wu/WorkBuddy/2026-09-13-23-32-04/site
git add -A
git commit -m "Update publications"
git push
```

push 后 1 分钟左右线上自动更新（Pages 有缓存，偶尔要等更久）。
本机没装 `gh`（GitHub CLI），装一个的话 `brew install gh && gh auth login` 之后
可以省掉手工建仓库和 Token 的步骤。

## 本地预览

直接双击 `index.html` 用浏览器打开即可。想用本地服务器的话：

```bash
python3 -m http.server 8000
# 然后打开 http://localhost:8000
```

## 备注

- 配色在 `index.html` 顶部的 `<style>` 里，改 `--link` 可以换主色。
- 页面是英文的。想改中文，直接把正文文字换成中文即可，字体栈里已经包含苹方和微软雅黑。
