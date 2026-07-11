# DATA_SOURCES · 外部数据源速查表

> 本仓库所有 skill 在执行时,应从这里查询真实数据,而非仅依赖内部知识。
> 数据快照时间: 2026-07-11。各源免费、API 公开、无需付费订阅。

---

## 使用约定

1. **优先用 API** (返回 JSON/CSV),其次用可访问页面 (返回 HTML/table)
2. **必须标注快照日期** (eg. "2025-12-31 数据"),不假设永远最新
3. **找不到时**才回退到 skill 内部知识,并明确告诉用户"未实时核实"
4. **多源交叉验证**:关键数字至少 2 个独立来源

---

## 1. 宏观经济指标

### 中国
- **国家统计局 NBS**: https://data.stats.gov.cn/
  - 指标: GDP / CPI / PPI / 失业率 / 固投 / 工业增加值 / 人口
  - 格式: HTML 表格 + 关联 API (需构造 query)
- **中国人民银行 PBOC**: http://www.pbc.gov.cn/
  - 指标: M0/M1/M2 / 社融 / 利率 / 外汇储备 / LPR
  - 关键数据系列: 货币当局资产负债表 (月度)
- **财政部**: http://www.mof.gov.cn/
  - 指标: 财政收支 / 国债发行 / 地方政府债余额 / 赤字率

### 美国
- **FRED (圣路易斯联储)**: https://fred.stlouisfed.org/  ← 最常用 API
  - API 端点: `https://api.stlouisfed.org/fred/series/observations?series_id={CODE}&api_key={KEY}&file_type=json`
  - 关键 series:
    - `GDPC1` 实际 GDP
    - `CPIAUCSL` CPI
    - `M2SL` M2 货币供应
    - `GFDEBTN` 联邦债务总额 (名义)
    - `GFDEGDQ188S` 联邦债务/GDP
    - `DGS10` / `DGS2` 10年/2年期国债收益率
    - `FEDFUNDS` 联邦基金利率
    - `PAYEMS` 非农就业
- **BEA (经济分析局)**: https://www.bea.gov/
  - 指标: GDP 分项 / 个人收入与支出 / 国际投资头寸
- **BLS (劳工统计局)**: https://www.bls.gov/
  - 指标: 失业率 / 非农 / CPI / PPI / 时薪

### 欧盟
- **Eurostat**: https://ec.europa.eu/eurostat
  - 指标: 欧元区 GDP / HICP / 失业率 / 政府债务
- **ECB (欧洲央行)**: https://www.ecb.europa.eu/
  - 指标: 政策利率 / M3 / 资产购买计划 / 通胀预期

### 全球
- **World Bank Open Data**: https://data.worldbank.org/
  - API: `https://api.worldbank.org/v2/country/{国家}/indicator/{指标}?format=json`
  - 关键指标:
    - `NY.GDP.MKTP.CD` GDP (现价美元)
    - `NY.GDP.MKTP.KD.ZG` GDP 增长率
    - `GC.DOD.TOTL.GD.ZS` 中央政府债务/GDP
    - `FP.CPI.TOTL.ZG` CPI 通胀
    - `SI.POV.GINI` 基尼系数
    - `SP.POP.TOTL` 总人口
    - `NY.GNP.PCAP.CD` 人均 GNI
- **IMF Data**: https://data.imf.org/
  - WEO (World Economic Outlook): GDP / 通胀 / 失业率 预测与历史
  - API: `https://www.imf.org/external/datamapper/api/v1/{indicator}/{country}`
- **OECD Data**: https://data.oecd.org/
  - 指标: GDP / 失业率 / 贸易 / 政府债务

---

## 2. 货币 / 债务专项

- **BIS (国际清算银行)**: https://www.bis.org/statistics/
  - 实际有效汇率 (REER)
  - 跨境银行债权 (Locational Banking Statistics)
  - 全球信贷/GDP gap (Credit-to-GDP gap)
  - Debt service ratio
- **IMF Debt Sustainability Analysis (DSA)**: https://www.imf.org/external/np/pubs/ft/dsa/
  - 主权债务可持续性评估 (国家分报告)
- **World Bank International Debt Statistics**: https://datatopics.worldbank.org/debt/
  - 外债总额 (DOD, present value)
  - 短期外债 / 长期外债 / 公共/私人外债

---

## 3. 政治 / 社会指标

- **V-Dem (民主指数)**: https://www.v-dem.net/
  - V-Dem 分数 (0-1, 越高越民主)
  - 公民自由 / 司法独立 / 媒体自由 子项
- **Freedom House**: https://freedomhouse.org/
  - Freedom in the World 报告 (年度)
  - Internet Freedom 报告
- **Polity IV / Polity V**: https://www.systemicpeace.org/
  - Polity score (-10 威权 ~ +10 民主)
- **SIPRI (军费开支)**: https://www.sipri.org/databases/milex
  - 各国军费 / GDP / 军费全球占比
- **UN Human Development Index**: http://hdr.undp.org/
  - HDI (寿命 + 教育 + 收入)

---

## 4. 地缘 / 冲突

- **Uppsala UCDP/PRIO 武装冲突数据**: https://ucdp.uu.se/
  - 武装冲突事件 / 死亡数 / 行为体
- **Global Peace Index**: https://www.visionofhumanity.org/
- **Political Stability Index (Worldwide Governance Indicators)**: https://info.worldbank.org/governance/wgi/

---

## 5. 市场 / 资产

- **黄金价格**:
  - LBMA: https://www.lbma.org.uk/prices-and-data/precious-metal-prices
  - World Gold Council: https://www.gold.org/goldhub/data
- **汇率**: 各央行公布 / XE.com (聚合)
- **主权债利差 (EMBI / CEMBI)**:
  - JPMorgan EMBI Global (付费)
  - 世界银行 WB EMBI (无版本)
- **大宗商品**: IMF Primary Commodity Prices
- **股市**: Yahoo Finance / Bloomberg / Wind (付费)

---

## 6. 数据查询模板(伪代码)

```
[Skill 调用流程]
1. 收到用户问题
2. 列出本 skill 需要的指标清单 (见各 SKILL.md "数据源指引" 段)
3. 并行 WebFetch 数据源:
   - 关键指标 → 优先 API
   - 历史趋势 → 时间序列
   - 跨国对比 → 同时拉多国
4. 验证:
   - 至少 2 个独立来源
   - 数据日期 < 6 个月
5. 缺失数据时:
   - 报告数据缺口
   - 用相邻指标或历史趋势推断,标注假设
6. 输出结论时:
   - 引用具体数字 + 数据源 + 日期
   - 不假设"所有人知道"
```

---

## 7. WebFetch 调用约定

```
URL: 数据源 URL
prompt: 提取哪个指标的最新值 + 历史 5-10 年 + 同比环比
format: 表格优先,然后 JSON
extract_main: true (只看主体内容,跳过导航)
```

---

## 8. 局限与降级策略

| 局限 | 降级策略 |
|------|---------|
| 数据源访问失败 | 用历史趋势 + skill 内部知识,标注"实时数据未核实" |
| 单源数据 | 必须找到至少 1 个交叉验证源 |
| 数据 > 6 个月陈旧 | 提示用户数据新鲜度,建议查实时数据 |
| 货币体系崩溃历史 | 用 IMF / BIS / 学术数据库综合 |
| 加密货币 | 主要用 CoinGecko / Glassnode,本框架不强制覆盖 |

---

## 9. 各 Skill 数据源优先级速查

| Skill | 必查 | 备用 |
|-------|------|------|
| `cycle-stage-detector` | NBS / FRED / World Bank | IMF / OECD / V-Dem / Polity |
| `cycle-correlation-scenario` | 同上聚合 + 时间序列对齐 | + BIS / SIPRI |
| `debt-risk-triple-ratio` | FRED / World Bank IDS / BIS | 央行年报 / 财政部 |
| `currency-regime-classifier` | 央行资产负债表 / IMF 货币统计 | 历史案例库 |
| `currency-crisis-scanner` | FRED M2 / 实际利率 / CDS 利差 | BIS REER / 黄金溢价 |
| `purchasing-power-defender` | CPI / 实际利率 / 黄金价格 / World Bank GDP 平减指数 | 历史对照 |
| `leader-cycle-fit` | V-Dem / Polity / WGI / SIPRI | Freedom House |
| `redline-mapper` | 用户提供的公开立场文件 | 历史事件库 |
| `post-rival-purge-forecast` | UCDP / 政治稳定指数 / SIPRI | 历史洗牌案例库 |
| `worst-case-decision-guard` | (无需外部数据,用户输入即可) | — |

---

## 10. 更新日志

- 2026-07-11  v1.0  初版,~30 个数据源,按 5 类组织(宏经/货币/政治/地缘/市场)
