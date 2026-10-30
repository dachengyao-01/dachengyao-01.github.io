# 个人主页修改指南

网站地址：https://dachengyao-01.github.io/

仓库地址：https://github.com/dachengyao-01/dachengyao-01.github.io

网站由 5 个 HTML 页面和一份共用样式组成。日常更新可直接在 GitHub 网页完成，无需安装软件。

## 先找到要修改的文件

| 要改的内容 | 文件 |
| --- | --- |
| Home：个人简介、研究方向、联系方式 | `index.html` |
| Experience：任职、教育、学术访问 | `background/index.html` |
| Research：Working Papers、Publications | `research/index.html` |
| Students and Teaching：博士生、硕士生、课程 | `teaching-and-students/index.html` |
| Grants and Awards：科研项目、奖励 | `grants/index.html` |
| 全站字体、颜色、页面宽度、日期对齐 | `assets/site.css` |
| 全站个人照片 | `assets/dacheng-yao.jpg` |
| 浏览器标签页小图标 | `assets/favicon.svg` |
| 自动发布设置，一般不用改 | `.github/workflows/pages.yml` |

`EDITING.md` 是本修改指南。它不会随当前发布流程出现在网站页面中。
`.nojekyll` 请保留。现有文件夹名称决定页面网址，日常修改时保持不变。

## 在 GitHub 上修改并发布

1. 登录 GitHub，进入上方仓库地址，确认左上角分支为 `main`。
2. 打开表格中对应文件，点右上角铅笔按钮 **Edit this file**。
3. 找到原有文字后修改；新增条目时，复制附近一个完整条目再改内容。
4. 点 **Commit changes…**，填写简短说明，例如 `Update publications`。
5. 选择 **Commit directly to the main branch**，再点 **Commit changes** 保存。
6. 仓库顶部打开 **Actions**，查看最新的 **Deploy GitHub Pages**。出现绿色勾后，打开网站检查结果。

发布通常需要一两分钟。如果浏览器仍显示旧文字，可强制刷新：Mac 按 `⌘ + Shift + R`，Windows 按 `Ctrl + F5`。

## 常见修改示例

以下代码里的示例文字和链接都应换成自己的实际内容。编辑时保留代码中的标签和引号。

### 修改个人简介

在 `index.html` 中搜索 `About Me` 或 `Research Interests`，修改对应的 `<p>…</p>`：

```html
<p>I am a Professor at the Institute of Applied Mathematics.</p>
```

### 新增论文

在 `research/index.html` 中找到 `Working Papers` 或 `Publications`，把一个完整的 `<li>…</li>` 复制到对应 `<ol>` 内。论文按时间由新到旧排列。

```html
<li data-year="2026">
  <h3><a href="https://doi.org/论文编号" target="_blank" rel="noopener noreferrer">论文标题</a></h3>
  <p class="authors">A. Author and <strong>D. Yao</strong>.</p>
  <p class="venue"><em>期刊名称</em>, 卷(期), 页码, 2026.</p>
</li>
```

在论文标题的链接中填写 DOI、arXiv 或 SSRN 地址即可。Working Paper 的 `venue` 行可写 `Working paper, 2026.`。正式发表后，把该完整条目移至 Publications，并更新期刊信息。

### 修改任职日期

在 `background/index.html` 中搜索职位名称。日期保留在同一条 `<li>` 的 `<time>` 标签内，即可使用现有的右对齐样式：

```html
<li><strong>Professor</strong><time>Apr. 2024 – Present</time></li>
```

Education 的日期在 `<span class="background-dates">…</span>` 内。只改日期文字，保留该标签及其 `class`。

### 新增学生或课程

在 `teaching-and-students/index.html` 中找到对应的 `Ph.D. Students`、`Master Students` 或 `Teaching`，在该部分 `<ul>` 内新增：

```html
<li>Student Name, Sep. 2026 &ndash; present.</li>
```

```html
<li>Course Name, Yanqihu Campus, Spring 2027.</li>
```

### 新增科研项目或奖励

在 `grants/index.html` 中，项目放进 `grants-list` 的 `<ol>` 内，奖励放进 `awards-list` 的 `<ul>` 内：

```html
<li>PI, “Project Title”, Grant No. 项目编号, ￥金额, Funding Agency, Jan. 2027 – Dec. 2030.</li>
```

```html
<li>Award Name, Awarding Organization, 2027.</li>
```

## 更换照片和共用信息

- 照片：打开仓库 `assets` 文件夹，点 **Add file → Upload files**，上传新的 JPEG 照片，文件名保持 `dacheng-yao.jpg`。确认覆盖该文件，再提交。不要仅把 PNG 后缀改成 `.jpg`。
- 发布流程会按照片内容自动添加版本参数，更新后无需逐页修改图片链接。网页显示的照片大小由 `assets/site.css` 中的 `.portrait` 控制。
- 左侧姓名、职称、邮箱、单位，以及顶部导航，在 5 个页面中各有一份；修改这些共用信息时，需要同时修改 5 个 HTML 文件。
- 修改简介时，可一并更新文件顶部的 `description` 和 `og:description`，它们用于搜索和链接分享时的摘要。

## 避免常见问题

- 保留成对标签，例如 `<p>…</p>`、`<li>…</li>`、`<a>…</a>`，以及属性两侧的英文引号。
- 新条目应放在对应的 `<ul>` 或 `<ol>` 内，不要放到结束标签之后。
- 正文或网址中的 `&` 写成 `&amp;`，例如 `May &amp; Aug. 2017`；小于号写成 `&lt;`。
- 保持现有链接路径；子页面使用 `../assets/`，Home 使用 `assets/`。
- 改字号、间距等外观前，先记下原值。保存后分别检查电脑和手机显示。

## 检查或恢复一次修改

Actions 绿色勾表示发布完成；仍需打开修改过的页面检查文字、链接和排版。若出现红色叉，点开该次运行查看失败的步骤。

想恢复某个文件：打开该文件 → **History** → 找到修改前的记录 → 查看当时的文件内容。复制需要恢复的内容，回到 `main` 分支编辑当前文件并提交。这样会保留修改记录，也会自动重新发布。

一次更新涉及多个文件时，按同样方法逐个恢复，并等待最后一次发布完成。
