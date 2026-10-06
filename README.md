# xmengju.github.io

用 [Quarto](https://quarto.org) 搭的个人学术网站。推送到 `main` 分支后，GitHub Actions 会自动构建并发布。

## 文件对应关系

| 页面 | 文件 |
|--|--|
| Home | `index.qmd`（照片是 `images/profile.jpg`） |
| Research | `research.qmd` |
| Publications | `publications.qmd`（论文配图放在 `images/pubs/`） |
| Teaching | `teaching.qmd` |
| Supervision | `supervision.qmd` |
| 导航栏、页脚 | `_quarto.yml` |
| 字体、颜色、论文配图排版 | `styles.scss` |

## 常见操作

- **加回 CV**（目前已隐藏）：
  1. 把新的 PDF 存为 `files/cv.pdf`
  2. 删掉 `.gitignore` 里的 `files/cv.pdf` 这一行
  3. 在 `_quarto.yml` 的 `output-dir: _site` 下面加上 `resources:` 和 `- files/` 两行
  4. 在 `index.qmd` 的 `links:` 里加回 CV 按钮（`icon: file-earmark-pdf`，`text: CV`，`href: files/cv.pdf`）
- **换照片**：用新照片覆盖 `images/profile.jpg`，正方形的效果最好。
- **加论文**：在 `publications.qmd` 里复制一个 `::: {.pub}` 块，再把配图放进 `images/pubs/`。
  配图建议用 4:3 的 PNG，800×600 左右。没有配图的话删掉 `![](...)` 那一行就行。
- **本地预览**：在这个目录下运行 `quarto preview`，浏览器里会实时刷新。
- **发布**：执行 `git add -A && git commit -m "update" && git push`，几分钟后网站就会更新。

## 第一次部署

1. 在 GitHub 上新建一个公开仓库，名字叫 `xmengju.github.io`。
2. 在本目录下运行：
   ```
   git init -b main
   git add -A
   git commit -m "Initial site"
   git remote add origin https://github.com/xmengju/xmengju.github.io.git
   git push -u origin main
   ```
3. 在仓库的 **Settings → Pages → Build and deployment → Source** 里选 **GitHub Actions**。
4. 去 Actions 标签页等构建跑完，网站地址是 https://xmengju.github.io
