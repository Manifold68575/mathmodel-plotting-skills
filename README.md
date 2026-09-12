# mathmodel-plotting-skills

数学建模绘图技能四件套——专门用于数学建模竞赛论文配图的 Agent Skills 集合。

## 技能清单

| 技能 | 角色 | 说明 |
|---|---|---|
| `mma-figure` | 路由入口 | 不直接作图，按需求把任务分派给下面三个技能；保证图片落到项目 `figures/` 目录，项目含 `document.tex` 时附赠可粘贴的 LaTeX 插图片段 |
| `nature-figure` | 数据图表 | Nature 级投稿级图表工作流（Python: matplotlib/seaborn；R: ggplot2/patchwork/ComplexHeatmap），先定结论与证据逻辑再作图，导出 SVG/PDF/TIFF |
| `mathmodel-figure-templates` | 模板复刻 | 用内置模板生成可复现科研图：模型评估、统计分布、多变量分析、特征归因、构成、网络、空间网格、时间序列，附 Python 脚本与 PNG/PDF/SVG 导出 |
| `paper-diagram` | 示意图 | 可编辑 draw.io（.drawio XML）示意图，产出 .drawio + PNG/PDF：技术路线图、研究框架图、算法流程图、模型/系统架构图，支持内置模板、手写 XML、参考图高保真复刻 |

## 典型流程

```
用户需求 ──> mma-figure（判断图类型）
              ├─ 数据生成的图（折线/柱状/热力图/ROC…） ──> nature-figure
              ├─ 套用现成科研绘图模板                    ──> mathmodel-figure-templates
              └─ 技术路线/框架/流程示意图                ──> paper-diagram
```

一次请求混有多类图时逐类分派，最后统一汇总产物清单。

## 安装

把四个技能文件夹复制到所用 Agent 的 skills 目录即可，例如：

```bash
# ZCode / Claude Code 等（Windows）
cp -r */ "$HOME/.agents/skills/"
```

| 技能 | 依赖 |
|---|---|
| nature-figure | Python（matplotlib、seaborn）或 R（ggplot2 等） |
| mathmodel-figure-templates | Python |
| paper-diagram | draw.io / diagrams.net（.drawio XML 导出 PNG/PDF） |

## 用法示例

- "画一张各方案误差对比图" → nature-figure
- "用绘图模板画一张 SHAP 特征归因图" → mathmodel-figure-templates
- "把这道题的技术路线做成一张图" → paper-diagram
- "补几张图" / "复刻某个绘图模板" → mma-figure 自动路由

## 来源与使用范围声明

本仓库的技能提取自 mathmodel 桌面应用（对应开源项目 [jihe520/MathModelAgent](https://github.com/jihe520/MathModelAgent) 的桌面版内置技能 `builtin-skills`）。该项目声明**个人使用免费、商用需联系作者**，因此本仓库仅供个人学习与建模使用，请勿公开再分发或用于商业用途。
