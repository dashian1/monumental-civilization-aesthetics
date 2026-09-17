# 05｜提示词编译与参数适配

## 自然语言结构

人物与单一动作→巨物及空间关系→主材料行为与结构→尺度证据→景别机位与层次→有来源的光→色谱→媒介→必要排除→模型参数。

把最重要的主体和关系放前面。句序是可读性与意图优先级，不是宣称模型必然按位置分配权重。

母模板（生成时替换字段，不把占位符交给用户）：

```text
a tiny [person] [single action] on [human-scale path] beneath/before/across [one colossal subject], [primary material with visible optical behavior], [structural rule], [second scale cue], [camera and layered space], [motivated lighting], [restricted palette and localized accent], sculptural volumes with painterly surface detail, cinematic monumental concept art, no text, no logo --ar [ratio] --stylize [value] --chaos [value]
```

## 具体词优先

保留：tiny solitary figure / colossal / scale contrast，但同时给出实物证据。用weathered copper plates with matte verdigris and exposed warm edges代替“luxurious advanced material”；用a descending service stair dwarfed by the tower代替第五次“epic”。

删减：masterpiece、best quality、insanely detailed等不承担画面决策的词。不要为了“电影感”同时添加所有电影镜头和器材名。

静态图用“披风偏向一侧”“裂缝间可见电弧”冻结瞬间，不写0—3秒、推拉环绕等时间流程。slowly rotating本身不保证静图表现运动；改用错位环片、弯曲云带或被风拉直的衣料表达状态。

## 参数规则

以下数值来自参考集，作为创作起点保留，不声称官方推荐、最优值、精密标定或适用于所有MJ版本。新项目可先用统一基线；不要装作245与248有确定美学区别。

| 设计意图 | 起点 | 使用理由 |
| --- | --- | --- |
| 克制构图与较稳系列 | `--stylize 220 --chaos 4` | 优先布局与系列可控性 |
| 默认巨物文明 | `--stylize 250 --chaos 6` | 承接历史中间区间 |
| 更开放的奇观探索 | `--stylize 275 --chaos 8` | 可尝试更大变化；不等于更美 |

- 默认每条完整附上`--ar`、`--stylize`、`--chaos`。
- 用户提供精确参数时保留；修改须由任务授权或明确反馈驱动。
- “只要参数”是提取任务：原来是多少就给多少，不能为了统一把4:5改成9:16。
- 历史液汞01—10依次为：4:5/255/6，9:16/245/5，4:5/265/7，4:5/250/6，9:16/260/6，16:9/245/5，4:5/270/7，16:9/255/7，4:5/275/7，4:5/280/8。此表仅用于明确引用原液汞组的提取，不覆盖新作。
- 不自动加`--v`、`--raw`、`--seed`、`--sref`、`--sw`、质量参数。没有真实参考图/编号就不编造引用。
- 用户要求当前版本（包括任何“v8.x”等表述）的兼容语法时查官方文档。无法查证时标记[uncertain]，给模型无关正文和保守参数候选，不称“官方适配完成”。
- 参数不保证实际输出尺寸、角色一致性或构图执行，实际结果需看图。

## 从MJ迁移其他模型

保留主体、材料、光色、空间与动作；去掉MJ旗标。将画幅映射到目标工具实际支持的尺寸/比例字段。不要把`--ar`直接塞进不支持MJ语法的API参数。目标模型不明且用户只是要通用提示词时，可给模型无关正文；不要因未安装MJ阻塞文本交付。

英文概念应保持具体：镜黑是mirror-black，哑黑是matte black；不能同一表面同时要求完全哑光和完美镜面。液体巨物不应又叫粗糙多孔铜锈，除非明确分区。

## 输出模式

标准：中文标题，下一行一个代码块，含完整英文正文及末尾参数。所有条目独立可复制，不用“同上”“延续之前”。

完整开发：先提供风格卡和十条矩阵，再交全部提示词、母句、排除项与质检结论。母句是扩展辅助，不代替完整条目。

极简：若用户说只要提示词，删除前后解释；只要参数则仅编号和参数。不要擅自追加继续推荐。
