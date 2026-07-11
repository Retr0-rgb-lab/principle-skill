# principle-skill · 达利欧《原则》的可执行 AI 工具集

从瑞·达利欧《原则:应对变化中的世界秩序》中蒸馏出的 **10 个可独立调用的 AI Skills**,按 4 条方法论轴组织:宏观定位 / 货币金融 / 地缘制度 / 决策保护。

> 📖 **来源**: 193 条微信读书划线 + 2 条想法笔记,经多视角分析提炼
> 🧠 **方法论**: [book2skill pipeline](https://github.com/Retr0-rgb-lab/.agents) — RIA++ 六段结构 + 三重验证
> 🔖 **版本**: v1.0.0 (2026-07-11)

---

## 4 个方法论轴 / 10 个 Skill

### 🎯 轴 1:宏观定位(2)
帮你判断"我们现在在哪里,历史会重演吗?"

| Skill | 中文名 | 一句话 | 典型问题 |
|-------|--------|--------|---------|
| **[`cycle-stage-detector`](./cycle-stage-detector/SKILL.md)** | 周期阶段检测器 | 把国家/行业定位到 6 阶段大周期上 | "美国/中国到周期哪了""X 国像历史上什么时候" |
| **[`cycle-correlation-scenario`](./cycle-correlation-scenario/SKILL.md)** | 三周期交叉推演器 | 分析货币/内部/外部周期耦合,生成 4 情景树 | "三个周期叠加会怎样""未来 10 年推演" |

### 💰 轴 2:货币金融(4)
聚焦货币/债务/资产保护

| Skill | 中文名 | 一句话 | 典型问题 |
|-------|--------|--------|---------|
| **[`debt-risk-triple-ratio`](./debt-risk-triple-ratio/SKILL.md)** | 债务风险三维比率 | 用三维比率评估债务真实风险 | "这笔债能不能借""国债危险吗" |
| **[`currency-regime-classifier`](./currency-regime-classifier/SKILL.md)** | 货币体系分类器 | 判定货币属于硬/纸/法币三类哪一类 | "美元/人民币是什么货币体系""会不会像魏玛" |
| **[`currency-crisis-scanner`](./currency-crisis-scanner/SKILL.md)** | 货币危机信号扫描器 | 6 信号早期预警货币危机 | "货币贬值螺旋开始了吗""央行印钞多危险" |
| **[`purchasing-power-defender`](./purchasing-power-defender/SKILL.md)** | 购买力防御器 | 5 层防御方案应对通胀贬值 | "钱缩水怎么办""该买黄金吗""达利欧世界末日组合" |

### 🌐 轴 3:地缘制度(3)
聚焦国家/权力/制度

| Skill | 中文名 | 一句话 | 典型问题 |
|-------|--------|--------|---------|
| **[`leader-cycle-fit`](./leader-cycle-fit/SKILL.md)** | 领导力-周期匹配度 | 评估国家制度能力是否匹配当前阶段(非领导人个人) | "这个阶段需要什么样的领袖""制度能力评估" |
| **[`redline-mapper`](./redline-mapper/SKILL.md)** | 地缘底线映射器 | 三层利益 X/Y/Z 映射识别红线 | "中美底线是啥""可交换的筹码是什么" |
| **[`post-rival-purge-forecast`](./post-rival-purge-forecast/SKILL.md)** | 战后权力洗牌预测器 | 共同敌人倒下后的内部洗牌 + 外部介入推演 | "共同敌人倒下后呢""联盟会不会散""外部会不会介入" |

### 🛡️ 轴 4:决策保护(1)
跨场景的方法论基础

| Skill | 中文名 | 一句话 | 典型问题 |
|-------|--------|--------|---------|
| **[`worst-case-decision-guard`](./worst-case-decision-guard/SKILL.md)** | 最坏情况决策保护器 | 防淘汰四步法做高风险决策 | "最坏会怎样""我不敢决定""决策底线是什么" |

---

## 怎么用

### 在 Claude / Cursor / OpenCode 中安装

```bash
# 全部安装
git clone https://github.com/Retr0-rgb-lab/principle-skill.git ~/.skills/principle-skill

# 仅安装部分(用 sparse-checkout)
git clone --depth 1 --sparse https://github.com/Retr0-rgb-lab/principle-skill.git
cd principle-skill
git sparse-checkout set cycle-stage-detector debt-risk-triple-ratio
```

### 触发方式

每个 skill 在你说相应的话时被 Claude 激活:

| 你说... | 激活 |
|---------|------|
| "美国现在到周期哪了" | cycle-stage-detector |
| "三个周期叠加会怎样" | cycle-correlation-scenario |
| "这笔债能不能借" | debt-risk-triple-ratio |
| "美元是什么货币体系" | currency-regime-classifier |
| "货币贬值螺旋开始了吗" | currency-crisis-scanner |
| "钱缩水怎么办" | purchasing-power-defender |
| "领导力合不合阶段" | leader-cycle-fit |
| "中美底线是啥" | redline-mapper |
| "共同敌人倒下后呢" | post-rival-purge-forecast |
| "最坏会怎样" | worst-case-decision-guard |

详见 [INDEX.md](./INDEX.md) 的完整调用关系图。

---

## 调用关系图(4 轴全景)

```
宏观定位轴:
  cycle-stage-detector ──┬──────────────┐
                         │              │
                         ▼              ▼
货币金融轴:           ┌──┤         [提供阶段信号]
currency-regime-classifier
        │
        ▼
currency-crisis-scanner ───┐
        │                   │
        ▼                   ▼
purchasing-power-defender  worst-case-decision-guard
        ▲                   ▲
        │                   │
debt-risk-triple-ratio ────┤
        ▲                   │
        │                   │
地缘制度轴:                │
   leader-cycle-fit ───────┤
        │                   │
   redline-mapper ──────────┤
        │                   │
post-rival-purge-forecast ─┘
```

详情见 [INDEX.md](./INDEX.md)。

---

## 哲学原则(整套 skill 共同遵循)

1. **不预测,定位** — 把现在放在历史坐标系里,而不是猜未来
2. **风险隔离,不是消除** — 接受不确定性,管理其边界
3. **防淘汰 > 求高收益** — "在生活或市场的博弈中,最重要的是不要被淘汰出局"
4. **互不相关的分散** — 不是"多买",而是"买不同的因果链"
5. **不靠政府保护钱财** — 历史反复证明政府保护不可靠
6. **历史会重演,但会进化** — "一组特定情况创造一组有限的可能性"

---

## Skill 间的"可组合"模式

| 场景 | 组合调用 |
|------|---------|
| **资产配置决策** | `cycle-stage-detector` → `currency-regime-classifier` → `currency-crisis-scanner` → `purchasing-power-defender` |
| **国家战略评估** | `cycle-stage-detector` → `leader-cycle-fit` → `redline-mapper` |
| **应对衰退** | `cycle-stage-detector` → `cycle-correlation-scenario` → `worst-case-decision-guard` |
| **评估新政权** | `redline-mapper` → `post-rival-purge-forecast` |
| **个人重大决策** | `worst-case-decision-guard`(直接调用,可叠加 `purchasing-power-defender` 评估资产) |

---

## 路线图

| 版本 | 状态 | 内容 |
|------|------|------|
| **v1.0.0** | ✅ 当前 | 完整 10 skill 生态系统 |
| v1.1.0 | 📋 规划 | 添加 `test-prompts.json` 启用 darwin-skill 自动化压力测试 |
| v1.2.0 | 📋 规划 | 添加可视化"周期仪表板"(大周期进度条 + 信号灯) |
| v2.0.0 | 📋 规划 | 国际化(英文版 + 多语言) + 集成到 Claude Skills Marketplace |

---

## 衍生来源

- **书源**: 《原则:应对变化中的世界秩序》(瑞·达利欧)
- **划线来源**: 微信读书 (bookId: 42689053),共 193 条划线 + 2 条想法
- **提炼方法**: book2skill pipeline
  1. **多 agent 并行提取** — 历史 / 决策 / 货币金融 / 地缘 4 视角独立蒸馏
  2. **三重验证** — V1 跨域佐证 / V2 预测力 / V3 独特性
  3. **RIA++ 构造** — 6 段结构 (Reading / Interpretation / Past Application / Future Trigger / Execution / Boundary)

---

## 风险说明

每个 skill 在自己的 `B — 边界` 段都标注了:
- **反场景**:不应触发此 skill 的情况
- **常见失败模式**:典型误用方式
- **作者盲点**:达利欧框架本身的局限

**特别提示**:`leader-cycle-fit` 有潜在的"政治化"风险,产出时应聚焦**国家制度能力评估**而非领导人个人评分。

---

## 许可

MIT — 自由使用、修改、分发。

---

## 引用

```
principle-skill v1.0.0 (2026-07-11)
来源:《原则:应对变化中的世界秩序》(瑞·达利欧)
提炼方法: book2skill pipeline
GitHub: https://github.com/Retr0-rgb-lab/principle-skill
```