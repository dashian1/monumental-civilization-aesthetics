# 08｜跨智能体交接与按需动态扩展

## 可移植运行方式

本技能为纯文本工作流，无必须安装的第三方库、服务或专属工具。具备读文件能力的智能体先读SKILL.md，再按任务读取同目录references文件。支持技能发现机制的宿主使用name/description触发；不支持的宿主可把入口和所需参考直接放入上下文。完整包应保留相对目录，不仅复制入口却丢掉参考。

不承诺所有平台都有统一“安装”方法。由所在平台决定技能放置路径和调用语法。本技能本身不要求联网；只有核验当前模型参数或真实文化事实时才需要外部资料。没有图像生成器也能完成风格开发和提示词交付，但不能宣称已出图。

## 最小交接状态

在完整项目交接时填写以下结构；只要十条提示词的普通请求不强制输出。字段为约定示例，可按宿主转为JSON、YAML或自然语言。

```yaml
project:
  mode: new_style
  deliverable: prompt_series
  count: 10
  aspect_ratio: '4:5'
  language: zh_titles_en_prompts
  medium: stylized_cinematic_concept_art
  target_model: midjourney_unspecified_version
  compatibility_verified: false
locked:
  invariants: [tiny_readable_human, colossal_subject, purposeful_action, coherent_materials]
  style_name: 磁暴蓝铜文明
  material_rules: [matte_verdigris_copper, dark_basalt, exposed_copper_edges]
  structure_rule: 分段巨构依靠虚构场力悬浮
  lighting: 可读的冷天光，断口局部电弧
  palette: [teal_patina, storm_gray, basalt_black, ivory_accent]
  exclusions: [rainbow_neon, conventional_combat_mecha, unreadable_darkness]
history:
  rejected_directions: [潮汐圣骸文明整套组合]
  used_styles: []
  used_subject_composition_pairs: []
  user_feedback: []
characters:
  continuity_required: false
  identity_anchors: []
  reference_assets: []
progress:
  style_card: complete
  series_matrix: complete
  prompts: complete
  image_generation: not_requested
validation:
  text_preflight: passed
  images_inspected: false
  unresolved: [实际生成效果尚未验证]
next_action: 按最新请求延展或修订，先保留locked字段
```

上例中的passed仅示范字段格式；使用时必须按实际检查结果填写。历史列表填真实已知数据。角色引用只记录真实可访问文件/ID，不编造图像地址。

## 角色与资产连续性

“同美学”不等于“同一个人”。用户要求同角色时，额外锁定发型、脸部可辨特征、服装轮廓、配色、标志物，并使用目标工具真实支持的参考机制。文案重复和随机种子都不能保证身份一致。人物极远时优先锁定剪影与服装锚点；不要声称几像素脸部已验证一致。

场景复用时锁定地平线、路径方向、主结构数量、关键连接、光源方向。建立资产名和真实引用映射；设计新视角时不得凭空移动桥、开门或改变巨物朝向。只提供文字、没有三维场景时，把无法验证的空间关系标为待确认。

## 图像到视频：仅在用户要求时执行

先保留主体拓扑、人物位置、材料、色谱和空间；再增加一个主要相机动作、一个人物行为、1—2层环境运动。静图里“巨物巨大”转成慢速视差、低频位移、有限结构变化；不要巨舰高速甩动，破坏质量感。

动态交接字段：

- 真实首帧引用或明确的文生视频设定。
- 总时长、画幅、镜头是否连续。
- 主体和构图锁定项。
- 相机起点、移动方向、终点，变化幅度。
- 人物在时间段中的单一动作及停顿。
- 近景/中景/远景各自运动，不把全部层一起平移。
- 材料运动规则：铜板刚性不融化；液态金属可流动但保持整体轮廓；薄膜按风向变化。
- 光线/声音：只有用户要求音频时扩展，不擅自补旁白。
- 禁止变形、角色替换、无依据切镜、无依据新增结构。

例：6秒磁暴巨环单镜头；相机从远处缓慢前推，保持小人物和巨环完整轮廓；旅者迈出一步后停住，披风同向摆动；一处蓝白电弧跨过接缝，远云缓慢横移；环体保持刚性、位置稳定；冷天光与铜绿保持。它是动态交接例，不是对任何视频模型的兼容性保证。

## 最小调用范例

1. “使用巨物文明美学导演。保留极小人物和巨构，换一个和液汞、蓝铜不同的风格，统一9:16，给10条完整MJ提示词。”
2. “沿用当前风格，01—10只要参数，顺序和数值不要改。”
3. “这一组太黑，只修光线与人物可读性，结构和色谱不变，给全部修订提示词。”
4. “把这套美学交给另一个智能体继续，附锁定项、已用方向、拒绝项和未验证事项。”

## 接手完成标准

新智能体无需知道原对话就能说明世界规则；能遵守画幅与媒介；知道哪些是用户要求、技能默认和未验证假设；能生成独立可用的条目；知道什么情况下只提取参数；能避免已否定组合；在没有工具时准确说明交付停在哪一层。
