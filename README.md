# principle-skill · 达利欧《原则》的可执行 AI 工具集

从瑞·达利欧《原则:应对变化中的世界秩序》中蒸馏出的 **P0 三件套 AI Skills**,每个 skill 都可以在 Claude 中作为独立的可调用模块使用。

> 📖 **来源**: 193 条微信读书划线 + 2 条想法笔记,经多视角分析提炼
> 🧠 **方法论**: [book2skill pipeline](https://github.com/Retr0-rgb-lab/.agents) — RIA++ 六段结构 + 三重验证
> 🔖 **版本**: v0.1.0 (2026-07-11 首次发布)

---

## 三件套速览

| Skill | 中文名 | 一句话 | 适用场景 |
|-------|--------|--------|---------|
| **[`cycle-stage-detector`](./cycle-stage-detector/SKILL.md)** | 周期阶段检测器 | 把国家/行业定位到 6 阶段大周期上 | "美国/中国现在到周期哪了""X 国像历史上什么时候" |
| **[`debt-risk-triple-ratio`](./debt-risk-triple-ratio/SKILL.md)** | 债务风险三维比率 | 用三维比率评估债务真实风险 | "这笔债能不能借""国债危险吗""要加杠杆吗" |
| **[`worst-case-decision-guard`](./worst-case-decision-guard/SKILL.md)** | 最坏情况决策保护器 | 用防淘汰四步法做高风险决策 | "最坏会怎样""我能承受失败吗""决策底线是什么" |

---

## 怎么用

### 在 Claude / Cursor / OpenCode 中安装

将本仓库克隆到你的 skills 目录,或直接下载单个 skill 目录:

```bash
# 全部安装
git clone https://github.com/Retr0-rgb-lab/principle-skill.git ~/.skills/principle-skill

# 只装其中一个
git clone --depth 1 --sparse https://github.com/Retr0-rgb-lab/principle-skill.git
cd principle-skill
git sparse-checkout set cycle-stage-detector
```

### 触发示例

**cycle-stage-detector** 在你说这些时被激活:
- "美国现在处在周期的哪个阶段?"
- "X 国像历史上的什么时候?"
- "大周期会重演吗?"

**debt-risk-triple-ratio** 在你说这些时被激活:
- "这笔债能不能借?"
- "国债危险吗?"
- "我要不要加杠杆?"

**worst-case-decision-guard** 在你说这些时被激活:
- "最坏会怎样?"
- "风险太大,我不敢决定"
- "我该怎么决策?"

详见各 skill 的 `A2 — 触发场景` 段落。

---

## 调用关系图

```
        ┌─────────────────────────┐
        │  cycle-stage-detector   │  ← 入口:先知道你在哪
        └──────────┬──────────────┘
                   │
       ┌───────────┼───────────┐
       │           │           │
       ▼           ▼           ▼
[阶段定位输出] [债务周期位] [外部对比]
       │           │
       ▼           ▼
debt-risk-triple-ratio
       │
       ▼
worst-case-decision-guard  ← 横切:任何风险评估后可串联
```

详见 [INDEX.md](./INDEX.md)。

---

## 哲学原则

整套 skill 共同遵循达利欧的几个核心方法论:

1. **不预测,定位** — 把现在放在历史坐标系里,而不是猜未来
2. **风险隔离,不是消除** — 接受不确定性,管理其边界
3. **防淘汰 > 求高收益** — "在生活或市场的博弈中,最重要的是不要被淘汰出局"
4. **互不相关的分散** — 不是"多买",而是"买不同的因果链"

---

## 路线图

| 版本 | 计划 |
|------|------|
| **v0.1.0** (当前) | P0 三件套上线 |
| v0.2.0 | + `currency-crisis-scanner` / `purchasing-power-defender` |
| v0.3.0 | + `redline-mapper`(地缘底线映射) |
| v0.4.0 | + `cycle-correlation-scenario`(三周期交叉推演) |
| v1.0.0 | 完整生态系统 + 国际化 + 自动化压力测试 |

---

## 衍生来源

- **书源**: 《原则:应对变化中的世界秩序》(瑞·达利欧)
- **划线来源**: 微信读书 (bookId: 42689053),共 193 条划线 + 2 条想法
- **提炼方法**: book2skill pipeline (多 agent 并行提取 → 三重验证 → RIA++ 构造 → 压力测试)

---

## 许可

MIT — 自由使用、修改、分发。

---

## 引用

如果你在研究或产品中使用了本仓库的 skill,建议引用:

```
principle-skill v0.1.0 (2026-07-11)
来源:《原则:应对变化中的世界秩序》(瑞·达利欧)
提炼方法: book2skill pipeline
GitHub: https://github.com/Retr0-rgb-lab/principle-skill
```