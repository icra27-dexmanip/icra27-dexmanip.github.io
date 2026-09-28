# 紫色版 Workshop 网页使用说明

这是一个不依赖后端和构建工具的静态网页，可直接在浏览器中打开，也可以部署到 GitHub Pages、学校服务器或任意静态网站托管平台。

## 目录结构

```text
workshop-website-v2/
├── index.html                  # 网页内容与结构
├── style.css                   # 紫色主题、排版和响应式样式
├── images/
│   └── organizers/             # 组织者头像
├── organizers-preview.png      # 组织者区域预览截图，可按需重新生成或删除
└── README.md                   # 本说明文档
```

## 本地查看

最简单的方法是直接双击 `index.html`，或在浏览器中打开该文件。

也可以在终端中启动本地静态服务器：

```bash
cd /home/hl/Tools/temp/workshop-website-v2
python3 -m http.server 8000
```

然后访问：

```text
http://localhost:8000/
```

停止服务器时，在运行服务器的终端中按 `Ctrl+C`。

## 修改网页内容

使用文本编辑器打开 `index.html`。主要内容按以下 section 划分：

- `#news`：最新消息
- `#scope`：Workshop 范围和目标
- `#speakers`：邀请报告人
- `#program`：日程安排
- `#organizers`：组织者
- `#contact`：联系方式

修改文字后保存并刷新浏览器即可看到结果。

## 修改组织者顺序或信息

在 `index.html` 中搜索：

```html
<section id="organizers" class="section">
```

每位组织者对应一个完整的 `<div class="person-card">...</div>`。移动整个卡片代码块即可调整顺序；姓名位于 `person-name`，单位位于 `person-affil`。

当前组织者顺序为：

1. Li Huang
2. Yongpeng Jiang
3. Jinzhou Li
4. Haichao Liu
5. Xianyi Cheng
6. Qi Dou
7. Noman Naseer
8. Xiang Li

## 添加或替换组织者照片

建议先将照片裁剪为正方形，尺寸约为 600 × 600 像素，再放入：

```text
images/organizers/
```

有照片时，卡片中的头像代码应为：

```html
<div class="person-photo">
  <img src="images/organizers/example.jpg" alt="Person Name"
       width="600" height="600" loading="lazy" decoding="async">
</div>
```

暂时没有照片时，可以使用首字母占位：

```html
<div class="person-photo initials">PN</div>
```

文件名建议使用小写英文和连字符，例如 `xianyi-cheng.jpg`。替换图片时如果沿用原文件名，通常只需覆盖图片并刷新页面；如果浏览器仍显示旧图，可以进行强制刷新。

## 添加邀请报告人

在 `#speakers` 区域中删除或替换 TBA 卡片，并参照以下结构填写：

```html
<div class="person-card">
  <div class="person-photo">
    <img src="images/speakers/name.jpg" alt="Speaker Name">
  </div>
  <p class="person-name">Speaker Name</p>
  <p class="person-affil">Affiliation, Country</p>
  <p class="person-talk">Talk title</p>
</div>
```

如果使用新的图片目录，需要自行创建 `images/speakers/`。

## 开放 Call for Abstracts

`index.html` 中的 Call for Abstracts 区域和对应导航项目前被 HTML 注释隐藏。搜索 `CfA`，移除包裹相关代码的 `<!--` 和 `-->`，然后补充日期与投稿信息即可显示。

## 修改紫色主题

颜色、字体、卡片和响应式布局均在 `style.css` 中。文件开头的 `:root` 定义了主要颜色变量：

- `--thu-purple`：主紫色
- `--deep`：深紫色
- `--indigo`：蓝紫色
- `--accent`：链接及强调色
- `--bg`：页面背景色

优先修改这些变量，可以统一调整整站配色。

## 部署

部署时应完整上传 `workshop-website-v2` 目录中的 `index.html`、`style.css` 和 `images` 目录，并保持相对路径不变。`README.md` 和预览截图不是网页运行所必需，可选择保留。

使用 GitHub Pages 时，可以把这些文件放到仓库根目录或 `docs/` 目录，再在仓库设置中启用 Pages。发布后请检查导航链接、图片、移动端布局和邮件地址是否正常。
