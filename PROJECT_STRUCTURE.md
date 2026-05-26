# 仓库架构说明

> 解释这个仓库为什么这样组织、各层之间如何引用。

---

## 四层资产模型

### 1. 通用层 `universal/`
**适用范围**：任何题材任何小说
**典型内容**：
- 网文写作核心原则（反差萌、章末钩子、节奏控制）
- 通用每章自检清单
- 跨书复用的模板（角色卡、卷大纲、章节）

**判定标准**：换一个题材这条规则还成立吗？成立才放这里。

### 2. 题材层 `genres/`
**适用范围**：同一题材的多本书
**典型内容**：
- 题材标准世界观（修仙的境界体系、势力划分）
- 题材常见套路（收徒流、宗门流）
- 题材推荐爽点列表（链接到拆文层的菜谱）

**判定标准**：换书还能用，但换题材就用不上。

### 3. 单书层 `novels/`
**适用范围**：仅这本书
**典型内容**：
- 本书专属世界观（末法时代、太虚仙宗、大衍共生诀）
- 角色卡
- 大纲与正文
- `BOOK_GUIDE.md`：本书的爽点配方、暗线、风格基调

**判定标准**：拿到别的书去用不通的。

### 4. 拆文层 `analysis/`
**适用范围**：经验原料，反哺上面三层
**典型内容**：
- `books/<作品名>/`：单本作品的拆解
- `insights/`：从多本拆文提炼的具体观察
- `beat-cookbook/`：拆文得出的爽点菜谱

**与三层的关系**：
- 拆文 → 提炼 → 写到 `insights/`
- 反复出现的 insight → 晋升为 `universal/techniques/` 或 `genres/*/tropes/`
- 爽点的写法规律 → 沉淀到 `beat-cookbook/`

---

## 引用规范

不同层之间用相对路径引用，避免重复内容。

### 单书引用题材层

```markdown
<!-- novels/01-XXX/worldbuilding/00-overview.md -->

## 境界体系
继承自 [修仙标准境界体系](../../../genres/xianxia-修仙/worldbuilding/境界体系-标准.md)

**本书特殊点**：主角第一卷只到筑基后期。
```

### 单书引用拆文层（爽点）

```markdown
<!-- novels/01-XXX/BOOK_GUIDE.md -->

## 爽点配方
- 战斗爽：参考 [战斗爽菜谱](../../analysis/beat-cookbook/universal/战斗爽.md)
- 收徒爽：参考 [收徒爽菜谱](../../analysis/beat-cookbook/by-genre/xianxia-修仙/收徒爽.md)
```

### 题材层引用拆文层

```markdown
<!-- genres/xianxia-修仙/beat-types/突破爽.md -->

详细写法：[突破爽菜谱](../../../analysis/beat-cookbook/by-genre/xianxia-修仙/突破爽.md)
```

### 拆文之间互相引用

```markdown
<!-- analysis/insights/开局三章必备元素.md -->

## 来源拆文
- [《XXX》总览](../books/XXX/00-总览.md) §爽点拆解
- [《YYY》总览](../books/YYY/00-总览.md) §节奏分析
```

---

## 晋升机制

### 何时把 insight 晋升为 technique？

| 阶段 | 位置 | 触发条件 |
|---|---|---|
| 单点观察 | `analysis/books/<某本书>/` 内一笔带过 | 拆某本书时偶然发现 |
| 凝练观察 | `analysis/insights/<观察名>.md` | 发现这个观察可能在多本书复用 |
| 升级为技法 | `universal/techniques/<技法名>.md` | 该 insight 在 ≥3 本拆文中复现，证明是普适规律 |
| 升级为题材套路 | `genres/<题材>/tropes/<套路名>.md` | 仅在某题材内复现，跨题材不成立 |

晋升时：
- 保留 `analysis/insights/` 中原始版本（不删，作为出处）
- 在新位置添加"出处"段落，链回 insights 和原始拆文
- 在 insights 文件顶部加"已晋升至 ..."标注

---

## 拆文工作流

```
1. 看完一本书
   ↓
2. 复制 analysis/_template-拆文模板.md
   到 analysis/books/<书名>/00-总览.md
   ↓
3. 按章节拆解写到 analysis/books/<书名>/章节拆解/
   ↓
4. 提炼出有价值的观察 → analysis/insights/<观察名>.md
   ↓
5. 提炼出爽点写法 → analysis/beat-cookbook/<层级>/<爽点名>.md
   ↓
6. 反复出现的观察 → 晋升到 universal/techniques/ 或 genres/*/tropes/
   ↓
7. 写新章节时引用这些资产
```

---

## 启动新书

```bash
# 1. 复制骨架
cp -r universal/templates/_book-skeleton/ novels/NN-书名/

# 2. 填写 meta.md
#    - 题材（决定继承哪个 genres/* 子目录）
#    - 核心亮点
#    - 当前阶段

# 3. 写 BOOK_GUIDE.md
#    - 爽点配方（从 beat-cookbook/ 选）
#    - 暗线设计
#    - 风格基调

# 4. 在仓库根 README.md 的小说表格里登记
```

---

## 边界拿不准时怎么办

> 把它先放到 `analysis/insights/`，等下次类似情况出现再决定升到哪一层。
> **延迟决策好过过早分类**。
