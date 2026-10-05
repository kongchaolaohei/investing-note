# investing-note · 投资笔记

个人投资学习知识库：一个随时可搜索的「**投资指标字典 + 答疑笔记**」网站。内容按 **A股 / 港股 / 通用** 分模块组织，并附带财报 PDF 档案库供下载与快速阅读。

- 🌐 **在线站点**：<https://kongchaolaohei.github.io/investing-note/>
- 📖 **知识字典**：每个指标 / 报表 / 概念一个词条——是什么、在财报哪里看、怎么算、由哪次提问催生
- 💬 **答疑笔记**：每次提问的完整归档，按时间倒序索引
- 📎 **财报档案**：年报、业绩公告等 PDF 原文件，站点内直接下载

## 这个仓库如何运作

```
你提问（任何设备、任何 AI 助手）
   │
   ▼
AI 按 AGENTS.md 的流程：写答疑笔记 → 新建/更新词典词条 → 更新索引
   │
   ▼
git push 到 main
   │
   ▼
GitHub Actions 自动构建（MkDocs Material）→ 2~3 分钟后站点更新
```

任何 AI 助手（或人类协作者）接手本仓库，**请先阅读 [AGENTS.md](AGENTS.md)**。

## 目录结构

```
├── AGENTS.md               # AI 协作总纲（接手必读）
├── mkdocs.yml              # 站点配置（导航 + 中文搜索）
├── requirements.txt        # 构建依赖
├── .github/workflows/      # 自动部署工作流
└── docs/
    ├── index.md            # 站点首页
    ├── guide/              # 使用指南与写作规范
    ├── templates/          # 词条 / 答疑模板（新建文件必须从此复制）
    ├── knowledge/          # 知识字典：shared 通用 / a-shares A股 / hk-stocks 港股
    ├── qa/                 # 答疑笔记（按年月归档）
    └── filings/            # 财报 PDF 档案 + 下载索引
```

## 本地预览

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve          # 打开 http://127.0.0.1:8000
```

详见 [docs/guide/local-preview.md](docs/guide/local-preview.md)。
