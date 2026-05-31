# 网文创作工坊

> 一个支持多本小说、跨题材沉淀创作经验的工坊式仓库。

---

## 📚 当前在写的小说

| 编号 | 书名 | 题材 | 状态 | 进度 |
|---|---|---|---|---|
| 01 | [多徒多福仙法：徒儿们别卷了，为师顶不住](novels/01-多徒多福仙法/) | 修仙 / 收徒流 | 🟢 连载中 | 15 / 100 章（第一卷·仙山开宗） |

> 最近进展（第一卷第一幕已成形）：程序员李长生穿越成废柴宗主，收下大弟子殷如焉，
> 用现代思维炼丹脱贫、智斗退魔修，硬抗魔教长老厉无咎并助徒弟筑基，第二位天命之徒李清雪登场。
> 三条暗线（穿越身份 / 共生诀"噬" / 天道既裂）已并行铺设。详见各书 `PROGRESS.md`。

---

## 🏗 仓库架构（四层资产模型）

```
通用层 (universal/)        ← 任何题材都能用
   ↓
题材层 (genres/)            ← 同题材跨书共享（修仙/都市/科幻...）
   ↓
单书层 (novels/)            ← 这本书独有

并行：
拆文层 (analysis/)          ← 经验原料：拆文 → 提炼 → 反哺上面三层
```

**详细架构说明**：[`PROJECT_STRUCTURE.md`](PROJECT_STRUCTURE.md)

---

## 🚀 快速导航

| 我想… | 去哪 |
|---|---|
| 看架构怎么设计的 | [`PROJECT_STRUCTURE.md`](PROJECT_STRUCTURE.md) |
| 查通用写作技法 | [`universal/techniques/`](universal/techniques/) |
| 查每章自检清单 | [`universal/checklists/per-chapter-checklist.md`](universal/checklists/per-chapter-checklist.md) |
| 查修仙题材资源 | [`genres/xianxia-修仙/`](genres/xianxia-修仙/) |
| 查爽点菜谱 | [`analysis/beat-cookbook/`](analysis/beat-cookbook/) |
| 拆某本书 | [`analysis/`](analysis/) |
| 启动一本新书 | 复制 [`universal/templates/_book-skeleton/`](universal/templates/_book-skeleton/) |
| 看具体某本书 | [`novels/`](novels/) |
| 看某本书进度 / 待办 | 各书目录下的 `PROGRESS.md`（如 [`novels/01-多徒多福仙法/PROGRESS.md`](novels/01-多徒多福仙法/PROGRESS.md)） |
| 看某本书角色卡 | 各书 `characters/00-index.md`（主角 / 徒弟 / 反派） |
| 看某本书专属规范 | 各书 `BOOK_GUIDE.md`（爽点配方 / 暗线 / 风格红线） |

---

## 📝 文件命名约定

- 章节大纲：`chXXX-YYY.md`（XXX = 起始章号 3 位补零，YYY = 终章号）
- 章节正文：`chXXX-章节标题.md`
- 角色卡：`NN-角色名.md`（NN = 出场序）
- 卷目录：`volume-NN-卷名/`
- 题材目录：`pinyin-中文/`（如 `xianxia-修仙`）

---

## ✍️ 启动一本新书

```
1. 复制骨架： cp -r universal/templates/_book-skeleton/ novels/02-新书名/
2. 填写 meta.md（题材、继承层、核心亮点）
3. 在 README.md 表格里登记
4. 在本书 BOOK_GUIDE.md 里写专属规范（爽点配方、暗线、风格）
```

---

## 🔀 协作 / 提交约定

- `main` 为受保护主分支，只通过 Pull Request 合入，不直接推送。
- 每批改动从 `main` 拉新分支（如 `feature/chXXX`），推送后开 PR 合入 `main`。
- 写完一章 / 一批章节后更新对应书的 `PROGRESS.md`，保持进度可追溯。
