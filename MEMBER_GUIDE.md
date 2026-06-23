# Member Guide · 成员维护指南

> How to update your own information and personal page on the AI4Rad Lab website.
> 如何更新你在 AI4Rad Lab 网站上的个人信息与个人主页。
>
> **Principle / 原则**：每位成员只修改属于自己的文件，互不冲突；提交 Pull Request，由 PI（张瑞鹏）审核后合并。
> Each member edits **only their own files**, so changes never conflict. Submit a Pull Request; the PI (Ruipeng Zhang) reviews and merges.

---

## What you can edit / 你可以修改的内容

| File / 文件 | Owner / 负责人 | Purpose / 用途 |
|---|---|---|
| `data/members/<your-id>.json` | **You / 你** | Your personal page (bio, news, papers, awards). 你的个人主页内容 |
| `images/members/<your-id>.jpg` | **You / 你** | Your photo and paper figures. 你的照片与论文配图 |
| `data/team.json` | **PI only / 仅 PI** | The team roster. 团队花名册（新增/移除成员、调整顺序由 PI 维护） |

> Your `<your-id>` is the `id` field already assigned to you in `data/team.json` (e.g. `ruipeng-zhang`, `hongda-wan`). 你的 `<your-id>` 即 `data/team.json` 中你那条记录的 `id` 字段。

---

## Quick start / 快速上手

### 1. Get the code / 获取代码
```bash
# Fork on GitHub, then:
git clone git@github.com:<your-fork>/AI4Rad-SSPH.github.io.git
cd AI4Rad-SSPH.github.io
git checkout -b profile/<your-id>
```
> 不熟悉 Git 的同学：也可以直接在 GitHub 网页上编辑文件并提交 PR，或把内容发给 PI 代为提交。

### 2. Create your data file / 创建你的数据文件
Copy the template and rename it to your id:
```bash
cp data/members/_template.json data/members/<your-id>.json
```
Then fill it in. Every section is **optional** — delete the keys you don't need (e.g. no papers yet? remove `publications`). 所有区块均为可选，没有的内容可整段删除。

Field reference / 字段说明:
- `name_en` / `name_cn` — your name in both languages. 中英文姓名。
- `photo` — path to your photo, e.g. `images/members/<your-id>.jpg`. Omit to auto-generate a cartoon avatar. 留空则自动生成卡通头像。
- `title_en` / `title_cn` — one-line role under your name. 姓名下的一行身份。
- `bio_en` / `bio_cn` — short paragraph; `<strong>` and `<a href>` allowed. 简介，可用加粗与链接。
- `links` — `email`, `scholar`, `github`, `homepage` (any can be empty). 联系方式，可留空。
- `scholar` — `citations`, `h_index`, `i10_index` (optional). 谷歌学术数据。
- `interests_en` / `interests_cn` — bullet list of research interests. 研究兴趣列表。
- `news_en` / `news_cn` — list of `{ "date", "text", "highlight" }`. `highlight: true` adds an accent. 动态时间线。
- `publications` — list of groups, each `{ "group_en", "group_cn", "items": [...] }`. See template for an item's fields. 论文分组与条目，见模板。
  - tag `kind` is one of: `ccf`, `jcr`, `cas`, `if`, `venue`, `award` (controls the color). 标签颜色由 `kind` 决定。
- `awards_en` / `awards_cn`, `services_en` / `services_cn` — bullet lists. 奖项与学术服务列表。

### 3. Add your images / 添加图片
Put your photo and any paper figures in `images/members/`:
```
images/members/<your-id>.jpg      # your photo / 你的照片
images/members/<your-id>-paperX.png
```
Reference them in the JSON exactly as `images/members/...` (paths are relative to the site root). JSON 中按 `images/members/...` 引用即可。

### 4. Preview locally / 本地预览
```bash
python3 -m http.server 8000
```
Open `http://localhost:8000/members/?id=<your-id>` and `http://localhost:8000/members/?id=<your-id>&lang=cn`.
打开上述地址检查中英文两种语言。

### 5. Submit / 提交
```bash
git add data/members/<your-id>.json images/members/
git commit -m "profile: update <your-id>"
git push origin profile/<your-id>
```
Open a Pull Request on GitHub. The PI reviews and merges. 在 GitHub 提交 PR，PI 审核后合并。

---

## How your page gets linked / 个人页面如何被链接

Your team card links to `members/?id=<your-id>` once your page is enabled. The first time you add a profile, the PI sets `"page": true` on your entry in `data/team.json` (a one-line change kept on the PI side to avoid roster conflicts).
当你首次创建个人页面后，PI 会在 `data/team.json` 中你的记录上加一行 `"page": true`，团队页的头像即会链接到你的个人主页。

See `data/members/ruipeng-zhang.json` for a complete, real example. 完整示例见 `data/members/ruipeng-zhang.json`。

---

## Do / Don't · 约定

- ✅ Edit only your own `data/members/<your-id>.json` and your images. 只改自己的文件。
- ✅ Keep both languages in sync. 中英文保持同步。
- ✅ Keep it factual — published work only, no unpublished/in-progress project details. 只放已公开内容，不涉及未发表的在研细节。
- ❌ Don't edit other members' files or restructure `css/` / `js/`. 不要改他人文件或站点框架。
- ❌ Don't commit large raw images — keep figures reasonably compressed. 图片请适度压缩。
