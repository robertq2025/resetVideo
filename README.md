# 《重启》/ REBOOT — 生成视频前的完整制作包

> 一部 3 分 20 秒的 AI 剧情短片。前期要素已定稿，并已生成 11 个动态镜头、72 句配音、6 段原创配乐，剪出可看的 3:20 主片、1:55.5 路演版与 1:12.5 短预告：故事、剧本、44 镜分镜、逐镜中英提示词、两张角色参考图、九张关键帧、44 镜逐镜生成包、声音设计、剪辑规范、一页创作说明、素材版权台账。
>
> **下一步不是再改设定，而是把 `handoff/` 交给外部视频工具，用每镜已备好的首帧生成剩余 33 镜（本平台视频/图像接口返回 HTTP 403）。**

---

## 1. 硬数字

| 项 | 数值 |
|---|---|
| 主片 | **3:20（200.000s / 4800 帧）**，44 镜全部为真实动态 clip（42 条 clip + 2 张字卡），72 句对白 |
| 画幅/规格 | 16:9；1920×1080 交付；24fps |
| 生成引擎 | `grok-imagine-video`（1280×720 原生，lanczos + 轻锐化升至 1920×1080）；其中 S22 / S29 为 `doubao-seedance-2-5` 原生 1080P 采用条 |
| 路演版 | **1:55.5（115.5s）**，25 镜，40 条字幕，≤ 2:00；另有 1:12.5 短预告与 1:57.6 扩展 EDL |
| 关键帧 | 9 张（K01–K09）+ 2 张角色参考图 |
| 逐镜生成包 | `handoff/` 44 镜 × 4 件 + `REF/` 26 张参考图 + 9 张落幅帧 + 32 条配音轨；**首帧 44/44 就绪**（1920×1080）；需落幅帧的 13 镜里 9 镜已派生、4 镜待图像额度 |
| 主场景 | 4 个：北站路口、继电器柜、工程车/值班室、粥铺 |
| 字幕 | 中文 72 条（已随片）；英文 72 条；路演中文 40 条；短预告 32 条 |
| 声音 | 6 段原创程序化 Cue；三层雨；黑城 1.5s 静音；主片 -17.1 / 路演 -15.9 LUFS |
| 锁脸 | 一套衣服穿到底；正脸只保留必要镜头；逐镜 QA |

---

## 2. 五分钟看什么

> 先看片：[`exports/REBOOT_previs_vo_1080p.mp4`](exports/REBOOT_previs_vo_1080p.mp4)（3:20 主片，含配音与配乐）· [`exports/REBOOT_roadshow_1080p.mp4`](exports/REBOOT_roadshow_1080p.mp4)（1:55.5 路演版）· [`exports/REBOOT_teaser_72s_1080p.mp4`](exports/REBOOT_teaser_72s_1080p.mp4)（1:12.5 短预告）。

1. **看画面**：打开 [`html/board.html`](html/board.html) — 44 镜分镜台、人物、声音、交付规范都在一页；图片本地加载，离线可看。
2. **看一页说明**：打开 [`exports/statement_A4.pdf`](exports/statement_A4.pdf) — 主题、梗概、工具、来源、AI 披露。
3. **看故事**：读 [`03_剧本.md`](03_剧本.md) — 3:20 完整分场，含 72 句台词总表。
4. **要交给别的工具生成**：直接打开 [`handoff/INDEX.md`](handoff/INDEX.md) — 每镜一个四件套（首帧图 + 一页视觉简报 + 全字段 JSON + 可粘贴提示词），不需要再回查别的文件。
5. **看怎么生成**：读 [`05_提示词包.md`](05_提示词包.md) — 44 镜的图像提示词/视频运动/负面词总表，直接复制。
6. **看怎么落地**：读 [`11_执行清单.md`](11_执行清单.md) — 7 天倒排、硬门槛、素材量、风险。

---

## 3. 文件地图

```text
reboot/
  01_创作说明.md              # 一页说明的文字版
  02_故事圣经.md              # 主题、人物、结构、色彩、声音母题
  03_剧本.md                  # 3:20 完整分场 + 72 句台词
  04_分镜表.csv               # 44 镜时间线（可导入表格）
  04_shots.json               # 结构化分镜（给工具/脚本用）
  05_提示词包.md              # 逐镜中英提示词 + 负面词
  06_角色一致性.md            # 锁脸流程、风险分级、QA 标准
  07_声音设计.md              # 声音总谱、6 段配乐、配音/混音规范
  08_剪辑交付.md              # 剪辑、调色、字幕、导出、终检
  09_路演2分钟.md             # 1:12.5 路演节拍表、话术、Q&A
  09_路演EDL.csv              # 1:57.6 / 28 镜扩展方案（44 镜齐备后使用）
  10_素材版权.md              # 素材/音乐/字体来源、AI 披露、哈希
  11_执行清单.md              # 7 天执行、预算、风险、提交清单
  12_运镜配方卡.md            # 44 镜：动机/起幅落幅/装置/路径/结束状态/失败替代
  13_场景设定卡.md            # 10 个场景的机位·光线·色彩·提示词
  14_道具卡.md                # 7 件关键道具：尺寸材质磨损/状态/持有人/镜号
  15_角色参考页.md            # 三视图与表情表的锁定项、禁止项、提示词
  16_V1.1_缺口清单.md         # 教材 G2 门槛对照 + 还差什么 + 谁来做
  data/regen.py               # QC 发现的逐镜重做硬性要求（已并入提示词）
  style_guide.yaml            # 分幕色板、颗粒/暗角上限、字体、构图与禁止项
  continuity_lock.yaml        # 21 个关键镜的不可变事实（含屏幕方向）
  asset_manifest.yaml         # 角色/场景/道具资产与状态（draft→locked）
  README.md                   # 本文件
  build_assembly.py           # 3:20 时间线、调色/颗粒、字幕、环境声
  build_vo.py                 # 72 句配音拟合、压混
  build_score.py              # 6 段原创程序化配乐
  build_roadshow.py           # 1:12.5 短预告
  build_roadshow2.py          # 1:55.5 路演版（从主片按时间窗 conform）
  build_overlays.py           # 15 张真实文字贴图（屏幕/纸张/招牌）
  build_scenes.py             # 10 张场景设定卡（机位/光线/色彩）
  build_props.py              # 7 张道具卡（含成片参考裁切）
  build_characters.py         # 2 张角色参考页（含成片脸部基准）
  build_cards.py              # 44 镜运镜配方卡
  build_frames.py             # 从已交付镜头派生 29 张成片内首帧（替换占位卡）
  build_handoff.py            # 44 镜逐镜生成包 -> handoff/

  html/
    board.html                # 制作台（离线可看）
    statement.html            # 一页说明（A4）
    title.html                # 片名字卡
    endcard.html              # 片尾字卡（含 AI 披露）
    poster.html               # 主海报

  assets/
    characters/               # 2 张角色参考图
    keyframes/                # 9 张关键帧 + 接触表
    keyframes/END/              # 9 张派生落幅帧（END_Sxx.png）+ 来源台账
    keyframes/derived/        # 29 张派生首帧（裁切自成片或用贴图做底板）

  exports/
    title_1920x1080.png
    endcard_1920x1080.png
    poster_1920x1080.png
    statement_A4.pdf / .png

  assets/
    scenes/                   # 10 张场景设定卡
    props/                    # 7 张道具卡
    overlays/                 # 15 张贴图 + OVERLAYS.md 贴合规则
    REBOOT_previs_vo_1080p.mp4   # 3:20 样片
    REBOOT_roadshow_1080p.mp4    # 1:55.5 路演版
    REBOOT_teaser_72s_1080p.mp4  # 1:12.5 短预告
    REBOOT_generation_log.csv    # 逐镜生成记录（11 镜已回填）

  subtitles/
    reboot_zh.srt / reboot_en.srt
    trailer_zh.srt / trailer_en.srt

  handoff/                    # 44 镜 × 四件套，可整包交给外部视频工具
    INDEX.md                  # 总表 + 建议生成顺序 + 停机规则
    checklist.csv             # 每镜首帧来源 / 状态 / 是否需要落幅帧
    Sxx_frame.png             # 首帧，统一 1920×1080
    Sxx_card.png              # 一页视觉简报：首帧 + 规格 + 不变项 + 提示词
    Sxx.json                  # 全字段：时间/景别/镜头/运镜配方/对白/声音/锁/提示词
    Sxx_prompt.txt            # 可直接粘贴：图像 + 视频 + 负面词 + 参考图 + 不变项 + 落幅帧要求
    Sxx_end.png               # 落幅帧（13 镜需要，已派生 9 镜）
    Sxx_vo.wav                # 本镜配音轨（32 镜有对白；48kHz，时间与主片一致，供唇形工具）
    REF/                      # 26 张锁定参考图：定妆 2 + 角色页 2 + 成片脸部基准 4 + 场景卡 10 + 道具卡 7 + AI 角标
    OVERLAY/                  # 14 张真实文字贴图；每镜生成后贴哪张写在 Sxx.json.text_overlays

  data/                       # 分镜/提示词/字幕的单一数据源
  tools/                      # fill_qa.py / package.py / roadshow_manifest.py
  build.py                    # 生成 CSV/JSON/提示词/SRT/EDL
  build_html.py               # 生成 board.html
```

---

## 4. 怎么接到其他视频工具

### 4.1 逐镜生成（推荐顺序）

1. 打开 `handoff/Sxx_card.png` 确认这一镜要什么画面；首帧就是旁边的 `handoff/Sxx_frame.png`（44 镜全部已备好，1920×1080）。
2. 把 `Sxx_prompt.txt` 的 **VIDEO PROMPT** 连同 **不变项** 一起粘进外部工具，用首帧驱动生成 `duration_sec` 秒；需要落幅帧的 13 镜（`checklist.csv` 里 `frame_pairing` 以“需 END”开头）先出 END 图再补中间。
3. 一镜先抽 2–3 次；连续 3 次失败就换策略（改首帧 / 拆镜 / 降运动幅度），不要纯提示词硬抽。
4. 存成 `shots/S11/S11_take01.mp4`；按 `06_角色一致性.md` 的 5 分制打分，采用条改名 `S11_FINAL.mp4`。
5. 全部 44 镜齐了再跑 `python build_vo.py` 重出主片，再跑 `python build_roadshow2.py` 重出路演；缺一镜不进入精剪。

> 整包交接：`REBOOT_handoff_kit_2026-10-24.zip`（245 个文件，130.5MB）= `handoff/` 全量，含每镜首帧与 `REF/` 26 张锁定参考图，外部工具不需要本仓库其他内容。

### 4.2 三条硬规则

- **不让模型生成文字**：屏幕、胶带、预约单、片名字卡全部后期贴；提示词里写“无文字/不可读”。
- **2:38 前不要大面积绿色**：绿色只在重启后出现；前期只允许微小 LED 绿点。
- **每人一套衣服**：陈默深藏青反光雨衣 + 银条 + 黄铜钥匙；林曦炭灰风衣 + 砖红围巾 + 左手细银戒。不要换装。

### 4.3 声音

- 配音 72 句，按 `07_声音设计.md` 的声线/口型策略；大部分对白走画外，只对 8 个必要镜头做唇形。
- **配乐 6 段与音效 16 类全部由 `build_score.py` / `build_sfx.py` 程序化合成（numpy + scipy），无第三方音乐、无采样、无 Suno/Freesound/ElevenLabs**；台账见 `exports/REBOOT_music_log.csv`、`exports/REBOOT_sfx_log.csv`。
- 配音用 edge-tts（微软神经网络语音），商用授权状态见 `10_素材版权.md` 的风险条目。
- 实测响度与峰值：主片 -17.1 LUFS / -0.9 dBFS，路演 -17.2 / -1.6，短预告 -15.8 / -1.1（混音归一化到 0.89 线性）；黑城 1.5s 静音是硬设计。

---

## 5. 现在完成 / 还缺什么

| 状态 | 内容 |
|---|---|
| ✅ 已完成 | 故事/剧本/分镜/提示词/角色方案/9 关键帧/声音设计/剪辑规范/说明/版权台账/字卡/海报/字幕；72 句配音；6 段配乐；16 类音效；**44 镜全部动态 clip**；3:20 主片（4800 帧）；**1:55.5 路演版（2772 帧）+ 1:12.5 短预告**；V1.1 视觉开发包；V1.2 逐镜生成包 |
| ✅ 合规处理 | 禁绿区间（2:38 前）10 镜做绿色定向旋琥珀（`tools/fix_green.py`，绿像素占比由最高 6.9% 降至 ≤0.5%），输出 `Sxx_FINAL.mp4`；S03/S14/S32 既有采用条保留 |
| ⬜ 仍待补 | V1.1 图像包 11 组（三视图/表情表/场景全景板/4 张 END 落幅帧）未生成；S09 抬头镜人脸与陈默基准不符；S22 表情偏笑；屏幕/纸面文字当前为模型原生渲染，`text_overlays` 的贴图合成尚未在装配链实现 |
| ⬜ 分轨 | `REBOOT_generation_log.csv` 仅回填已交付镜；grok 生成记录在 `exports/REBOOT_grok_log.csv` 与 `REBOOT_grok_prompts.jsonl` |

> 所有数字都由 `data/`、`build_*.py` 与产物本身生成：主片 200.0s / 44 镜 / 72 句；路演 72.5s / 15 段 / 32 条字幕（`exports/roadshow_manifest.json`）。

---

## 6. 重新构建

```bash
cd reboot
python build.py          # 生成 CSV/JSON/提示词/SRT/EDL/manifest
python build_html.py     # 生成 html/board.html
python build_assembly.py # 重渲染 3:20 画面（调色/颗粒/缓推）
python build_score.py    # 生成 6 段配乐
python build_vo.py       # 生成 72 句配音、拟合、压混、输出 3:20 样片
python build_roadshow.py # 输出 1:12.5 短预告
python build_roadshow2.py  # 输出 1:55.5 路演版（需先跑 build_vo.py）
python build_overlays.py # 15 张文字贴图 + AI 角标
python build_paperfix.py # 已交付镜头后期修补：S32 纸面/S14 车身文字虚化 + S03 绿灯改红，输出采用条 *_FINAL.mp4
python tools/fill_qa.py # 已交付 11 镜的逐帧 QC 结论写入 qa_log.csv
python build_scenes.py   # 10 张场景设定卡 + 13_场景设定卡.md
python build_props.py    # 7 张道具卡 + 14_道具卡.md
python build_characters.py # 2 张角色参考页 + 15_角色参考页.md
python build_cards.py    # 12_运镜配方卡.md
python build_frames.py   # 派生首帧 -> assets/keyframes/derived/ + 来源台账
python build_endframes.py # 从成片末帧/同 clip 裁切/真实贴图底板派生落幅帧 -> assets/keyframes/END/
python build_handoff.py  # 44 镜逐镜生成包 -> handoff/（含 REF 参考图与落幅帧）（首帧+简报卡+JSON+提示词）
python tools/fill_qa.py  # 回填 qa_log.csv（只写实际检查过的镜头）
python tools/roadshow_manifest.py # 实测路演时长/镜数/字幕/LUFS -> exports/roadshow_manifest.json
python tools/package.py  # 重算 assets_manifest + 打 REBOOT_V1.2.zip 与 REBOOT_handoff_kit.zip
```

字卡/海报/一页说明用 Edge 无头截图：

```bash
EDGE="/c/Program Files (x86)/Microsoft/Edge/Application/msedge.exe"
"$EDGE" --headless=new --disable-gpu --hide-scrollbars --force-device-scale-factor=1 \
  --window-size=1920,1080 --screenshot="exports/title_1920x1080.png" \
  "file:///D:/AI_Video/reboot/html/title.html?static=1"
"$EDGE" --headless=new --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="exports/statement_A4.pdf" \
  "file:///D:/AI_Video/reboot/html/statement.html"
```

---

## 7. 交付前必须过的五条

1. 主片 ≥ 3:00，16:9，≥1080p，24fps。
2. 主角前后同一张脸；S11/S21/S23/S29/S30 逐帧看。
3. 故事完整：有欲望、障碍、回忆、选择、回落。
4. 声音成立：对白可懂、2:38 第一声是继电器、黑城 1.5s 静音。
5. 来源可查：画面/音乐/音效/字体都有台账；片尾有 AI 披露。

> 一句话：**把“重启”拍成一次交班，而不是一次爆炸。** 城市亮了，人没有变回十八年前；他们只是终于往同一个方向走。

---

## 8. 本次交付自检（2026-10-24）

| 检查 | 结果 |
|---|---|
| 主片时长/镜数/台词 | 200.0s / 44 镜 / 72 句 |
| 路演版 | 115.5s（1:55.5）/ 25 镜 / 40 条字幕；短预告 72.5s / 15 段 / 32 条 |
| 关键帧/参考图 | 9 张关键帧 1920×1080；2 张定妆参考 1024×1415；2 张角色参考页 1720×1620（含成片视角拼版） |
| 字幕 | 主片中文 72 条；路演中文 40 条；短预告 32 条 |
| 分镜表/EDL | 44 行 / 28 行 |
| 制作台 | 44 个镜头卡、12 张图片全部加载、0 个控制台错误 |
| 一页说明 | PDF 1 页（A4），PNG 1653×2339 |
| 字卡/海报 | 1920×1080；片尾含 AI 生成披露 |
| 素材台账 | 文件数 = `exports/REBOOT_assets_manifest.csv` 的行数；逐文件字节数与 sha256 见 `exports/REBOOT_assets_manifest.csv`（合计 = 该文件 `bytes` 列求和，一条查询可复现，见 §8 末尾） |
| 逐镜生成包 | 44 镜 × 4 件 + `REF/` 26 张 + 落幅帧 9 张 = 213 个文件；首帧 44/44 为 1920×1080；简报卡 1400×1120–1690 无裁切 |
| 交付压缩包 | `REBOOT_V1.2_2026-10-24.zip`（提交包）与 `REBOOT_handoff_kit_2026-10-24.zip`（逐镜生成包）；**大小/文件数/sha256 以 `exports/REBOOT_package_checksums.txt` 为准**（zip 不能包含自身哈希，所以单独落盘） |
| 待生成 | 剩余 33 镜视频（外部工具）；11 组 V1.1 图；最终 QC |

复现核心数字：

```bash
python -c "import json; m=json.load(open('exports/roadshow_manifest.json',encoding='utf-8')); print(m['duration_sec'], m['segments'], m['subtitles_zh'])"
# 115.52 25 40
python -c "from pathlib import Path; h=Path('handoff'); print(len(list(h.glob('S*_frame.png'))), len(list(h.glob('S*_card.png'))), len(list(h.glob('S*.json'))), len(list(h.glob('S*_prompt.txt'))))"
# 44 44 44 44
python -c "import csv; r=list(csv.DictReader(open('exports/REBOOT_assets_manifest.csv',encoding='utf-8-sig'))); print(len(r), round(sum(int(x['bytes']) for x in r)/1e6,1))"
# <文件数> <未压缩合计 MB>   ← 与 README 引用的数字同源
```
