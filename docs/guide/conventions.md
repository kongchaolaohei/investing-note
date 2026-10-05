# 写作规范（AI 必读）

本页是 [AGENTS.md](https://github.com/kongchaolaohei/investing-note/blob/main/AGENTS.md) §3/§4 的细则。新建任何文件前，先从 `docs/templates/` 复制对应模板。

## 1. 词典词条（entry）

**位置**：`docs/knowledge/<market>/<category>/<slug>.md`

- `<market>`：`a-shares` / `hk-stocks` / `shared`
- `<slug>`：小写英文 + 连字符，如 `balance-sheet.md`、`roe.md`

**front-matter schema**（字段全部保留，缺省写 `[]` / `null`）：

```yaml
---
title: 资产负债表          # 词条中文名（必填）
market: A股                # A股 | 港股 | 通用
category: 三大表           # 模块内分类，与目录结构一致
tags: [财报, 三大表]       # 小写中文标签，用于交叉检索
created: 2026-10-05        # 词条创建日
updated: 2026-10-05        # 最近一次实质更新日
source_qa: []              # 催生/更新过本词条的答疑笔记相对路径（docs 内相对 docs/）
---
```

**正文结构**（H2 顺序固定，无内容的小节写"待补充"而非删除）：

1. `## 是什么` —— 一句话定义 + 通俗解释
2. `## 怎么来的 / 在财报哪里看` —— 数据出处：哪张报表哪个科目，或计算公式
3. `## 关键科目 / 关键要点` —— 拆解核心构成
4. `## 分析视角` —— 看这个指标时常见的问题与陷阱
5. `## 相关词条` —— 相对链接列表
6. `## 相关答疑` —— 列表：日期 + 问题摘要 + 指向 `qa/...` 的链接；暂无时写"（暂无，等待首次提问）"

## 2. 答疑笔记（qa）

**位置**：`docs/qa/YYYY-MM/YYYY-MM-DD-<slug>.md`，slug 用简短英文（如 `china-foods-gross-margin.md`）。

**front-matter schema**：

```yaml
---
title: 中国食品桶装水业务毛利率为什么高于整体？
date: 2026-10-05
market: 港股              # A股 | 港股 | 通用
related_entries:          # 涉及/新建的词条（docs 内相对路径）
  - knowledge/hk-stocks/indicators/gross-margin.md
related_filings: []       # 涉及的财报档案路径
status: 已归档
---
```

**正文结构**：`## 问题` → `## 结论`（先给答案）→ `## 分析` → `## 延伸`（可选）。

## 3. 链接规则

- 站内链接一律**相对路径**（同目录 `./balance-sheet.md`，跨目录 `../../filings/中国食品/xxx.pdf`）。
- PDF 用相对链接直链，文件名保持原始名称（可含中文）。
- 不使用绝对站址 `https://...` 做站内链接（本地预览会断）。

## 4. 标签体系

少量、稳定、中文小写。当前约定集合（可增补，增补时更新本节）：

- 报表类：`三大表`、`财报`、`披露规则`
- 指标类：`盈利指标`、`估值指标`、`偿债指标`、`营运指标`、`现金流`
- 场景类：`分红`、`并购`、`审计`、`风险提示`

## 5. 索引维护清单

| 文件 | 何时更新 |
|---|---|
| `docs/qa/index.md` | 每次新增答疑 |
| `docs/knowledge/index.md` | 每次新增词条 |
| 对应模块 `index.md` 词条表 | 新增词条 / 词条实质更新 |
| `docs/index.md` 最近更新 | 每次答疑后（保留 10 条） |
| `docs/filings/index.md` | 每次档案入库 / 补充要点 |
| `mkdocs.yml` nav | **每次新增页面**（否则不上导航） |
