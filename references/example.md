# 端到端范例

下面用一段虚构小说走完五段流水线。范例假设用户已选 `超写实真人商业摄影质感`，并要求图片提示词用英文。
本次共 3 个分镜，因此总时长必须落在 7.0-10.0 秒。

## 原文

```text
夜雨。沈砚背着断了半截的赤霄剑走进渡口驿站，湿透的黑发贴在额角。柜台后的掌柜抬眼看了他一下，
把一枚锈蚀的青铜符牌推过柜面。
「南边的船，今夜不走。」掌柜说。
沈砚没有接那枚符牌。他解下背上的赤霄剑，横放在柜台上，剑身上的雨珠一颗一颗滚落下来，在灯下亮得像血。
```

## 阶段 1：分段

```markdown
| 段 | 原文定位 | 情节功能 | 场景 / 时间 | 预计时长 |
|---|---|---|---|---|
| 1 | 「夜雨。……抬眼看了他一下」 | 主角抵达，两人第一次对上视线 | 渡口驿站 · 夜 · 雨 | 3.5s |
| 2 | 「把一枚锈蚀的……今夜不走。」 | 掌柜推符牌并拒船 | 渡口驿站 · 夜 · 雨 | 3.5s |
| 3 | 「沈砚没有接……亮得像血」 | 主角不接符牌，用放剑作答 | 渡口驿站 · 夜 · 雨 | 3.0s |
```

## 阶段 2：分镜元素表

站位、朝向、动作由 AI 按原文推断后直接写进表里（原文的「走进」「抬眼」「推过柜面」「解下……横放」
都是推断依据），不留给用户从空白填。

```markdown
## 分镜 2 ｜ 掌柜推符牌并拒船

- 原文依据：「南边的船，今夜不走。」
- 情节摘要：掌柜把符牌推过柜台，开口拒了南下的船。
- 进入 → 出去：掌柜的手压在账本上 → 符牌停在柜台中线，两人隔柜台对视
- 分镜人物：驿站掌柜（发声）、沈砚（在场沉默）
- 分镜场景：渡口驿站 · 夜 · 雨 · 暖色油灯
- 分镜道具：青铜符牌（特有，理由：锈蚀旧物，铸有渡号纹样，后续靠它认人）
- 站位 / 朝向 / 动作：沈砚在画面右侧前景，侧身站、四分之三背对镜头，视线落在柜面上的符牌；
  驿站掌柜在画面左侧中景柜台后，正对沈砚、只有侧脸给镜头，推符牌的手收回后压在账本上；两人隔一张柜台
- 环境声 / 音效：雨打屋檐、门轴吱呀、铜牌擦过湿木面
- 对白：「南边的船，今夜不走。」（驿站掌柜）
- 预计时长：3.5s
```

三个分镜汇总后的元素（人物 → 场景 → 道具）：沈砚、驿站掌柜；渡口驿站；赤霄剑、青铜符牌。
雨、柜台、油灯、账本都是常见物品，且原文没有特殊描写，不单独立项。

表输出后紧跟一句追问：

```text
上面的站位、朝向、动作是我按原文推断的：哪一镜要改？不改我就按这版写视频提示词。
```

用户回复：

```text
分镜 2 让沈砚正对柜台站，掌柜改成侧身对着柜台；分镜 3 让掌柜往柜台边走近一步，别被挡得看不见。
```

确认后的站位（只改用户点名的两镜，其余保持）：

```text
分镜 1：沈砚从画面下缘推门进来，背对镜头走向中景；掌柜在画面左后景的柜台内，侧身对着柜台，抬眼看向门口。
分镜 2：沈砚在画面中央偏右、正对柜台站，四分之三给镜头；掌柜在画面左侧中景柜台后，侧身对着柜台，
视线落在沈砚身上，推符牌的手收回后压在账本上。
分镜 3：沈砚在画面右侧前景俯身，视线落在剑上；掌柜往前一步到柜台边，半身入画，不再被完全挡住。
```

## 阶段 3：图片提示词

先问风格与语言，得到答复后再写。下面给出三条，其余同法：

```text
Character reference sheet — 沈砚：a man in his early twenties, rain-soaked black hair clinging to his
temples, pale gaunt face, dark grey travel cloak over a coarse linen robe, worn leather sword belt;
ultra-realistic commercial photography, 85mm lens, soft directional lamp light from camera left,
neutral dark backdrop, three-quarter full-body view plus one head-and-shoulders detail;
no text, no watermark, no logo.
```

```text
Empty interior plate — 渡口驿站：low beamed timber ceiling, wet slate floor, long wooden counter with a
single oil lamp, stacked bamboo baskets and coiled rope along the wall, cool blue rain light through the
door opening against warm lamp glow; ultra-realistic commercial photography, eye-level wide shot from the
doorway; no people, no text, no watermark.
```

```text
Prop reference — 赤霄剑：a single-edged blade snapped halfway, corroded brass guard, worn leather-wrapped
grip, dark water beading along the exposed steel; shown at 45 degrees on a plain dark surface with a
hand-width ruler beside it for scale, warm side light; ultra-realistic commercial photography;
no text, no watermark, no logo.
```

## 阶段 4：编号位与站位复核

向用户索取编号，用户回复：

```text
沈砚为1号位、驿站掌柜为2号位、渡口驿站为3号位、赤霄剑为4号位、青铜符牌为5号位
```

校验：5 个元素都有号，号不重复、不跳号；人物是 1-2 号，场景与道具是 3-5 号。
注意人物位号与说话人编号是两套东西：驿站掌柜是 2 号位，但他也是全片第一个发声的人，因此记 `(S1)`；
沈砚是 1 号位却不说话。

按号回填再输出一次，供用户核对：

```text
分镜 1：<Subject 1> 背对镜头走向中景；<Subject 2> 在画面左后景的柜台内，侧身、抬眼看向门口。
分镜 2：<Subject 1> 在画面中央偏右、正对柜台站，四分之三给镜头；<Subject 2> 在左侧中景柜台后侧身，
视线落在 <Subject 1> 身上，手把 <Picture 5> 推过柜台。
分镜 3：<Subject 1> 在右侧前景俯身，视线落在 <Picture 4> 上；<Subject 2> 走到柜台边，半身入画。
```

## 阶段 5：视频提示词

最终交付（实际输出时直接给裸 JSON，不加围栏）：

```json
{
  "subject_definitions": [
    "<Subject 1> is the young swordsman in <Picture 1>, with rain-soaked black hair clinging to his temples, a pale gaunt complexion, a dark grey travel cloak over a coarse linen robe, a worn leather sword belt, and a thin old scar along his left jaw.",
    "<Subject 2> is the middle-aged innkeeper in <Picture 2>, with a weathered face, a thinning grey topknot, a short beard, and a stained grey apron over a padded cotton jacket.",
    "<Picture 3> is the ferry-side inn environment in the reference, featuring a low beamed timber ceiling, a wet slate floor, a long wooden counter with a single oil lamp, and stacked bamboo baskets with coiled rope along the wall.",
    "<Picture 4> is the sword prop in the reference, a single-edged blade snapped halfway with a corroded brass guard, a worn leather-wrapped grip, and water beading along the exposed steel.",
    "<Picture 5> is the bronze tally prop in the reference, a palm-sized rectangular token with a cast river-crest pattern on its face, chipped edges, and a green-grey patina."
  ],
  "summary": "[reference generation] A rain-soaked period wuxia encounter in a riverside inn, where a young swordsman answers a refused river crossing by laying his broken sword on the counter; a 10-second sequence in cinematic realistic style, ending on the blade before the innkeeper answers.",
  "retention_analysis": [
    "<Subject 1> (appears in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - the rain-soaked black hair, pale complexion, dark grey cloak and leather sword belt follow <Picture 1> exactly; only the pose and the wet sheen change.",
    "<Subject 2> (appears in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - the weathered face, thinning grey topknot and stained apron are carried over from <Picture 2>.",
    "<Picture 3> (environment reference in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - the low beamed ceiling, wet slate floor and oil-lamp counter are reproduced without change.",
    "<Picture 4> ([Shot 3] prop reference): partially_preserved - the snapped blade, corroded guard and worn grip follow the reference; the rolling water droplets are new, per the source text.",
    "<Picture 5> ([Shot 2] prop reference): fully_preserved - the cast river-crest pattern and chipped edges are kept."
  ],
  "detailed_description": "Ground-level cinematic realism in the style of a rain-soaked period wuxia drama, cool blue night tones outside against warm oil-lamp pools inside, 35mm lens with shallow depth of field and handheld micro-movement.\n[Shot 1] A Tracking Shot with small amplitude at slow speed follows behind <Subject 1> as he leans into the rattan door and steps through, his back to the camera; <Subject 2> stands behind the long wooden counter in the background on screen left, side-on to the counter, and lifts his eyes toward the door. <Picture 3>'s wet slate floor, low beamed ceiling and long wooden counter fill the frame, an oil lamp burning at the counter. Rain streams off the dark cloak and drums on the eaves, and the door hinge creaks.\n[Shot 2] At 00:03.500, the camera holds a Static Shot framed as a medium two-shot across the counter: <Subject 1> stands just right of center facing the counter in three-quarter view toward the lens, <Subject 2> behind the counter on screen left, side-on to the counter with his eyeline on <Subject 1> and only his profile toward the camera. <Subject 2> lifts his eyes from the ledger, and after a brief beat his palm slides <Picture 5> across the wet countertop toward <Subject 1>. <Subject 2> (S1) says, <d>[Chinese] 南边的船，今夜不走。</d> <Subject 1> does not speak; his lips remain completely closed.\n[Shot 3] At 00:07.000, <Subject 1> bends forward in the right foreground with his eyeline fixed on the blade, reaches back with both hands, swings <Picture 4> off his shoulder and lays it flat across the counter; <Subject 2> steps up to the counter edge, his upper body joining the left midground beside <Subject 1>. Water beads roll down the exposed steel one by one and catch the lamp light. Push In with small amplitude at slow speed from a low three-quarter angle on the countertop, the rain still drumming overhead.",
  "overall_soundscape": "Steady night rain on timber eaves and standing water outside, a creaking rattan door hinge, wet cloth shifting, boots on slate, the soft scrape of metal sliding over wet wood, and a single droplet landing on the countertop.",
  "non_diegetic_music": "One low bamboo flute line at a slow tempo over a sparse sustained drone, dynamics rising slightly as the sword is laid down; no percussion."
}
```

- 站位与朝向只落在 detailed_description 里，不进 subject_definitions——定义段只锁身份。
- 用户要求不要配乐时，最后一段写 `"non_diegetic_music": "N/A"`。
- 站位的左右一律指画面左右；要指人物自身的左右必须写明 `his left hand` 这类说法。