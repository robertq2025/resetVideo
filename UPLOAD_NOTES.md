# 《重启》素材库（仅图片与文档）

> 上传范围：**图片 + 文档**。**不含视频（mp4）、音频（wav）、脚本（py）与压缩包**。
> 生成清单：`UPLOAD_MANIFEST.csv`（逐文件字节数与 sha256，可一条命令复核）。

## 先看这三份

| 文件 | 作用 |
|---|---|
| `16_V1.1_缺口清单.md` | **接手先读**：还差什么、谁来做、验收标准；§5.7 是主片少 2 帧的根因与一行修复；§5.6 是 S23/S11 重做要求 |
| `handoff/INDEX.md` | 44 镜逐镜生成包总表：生成顺序、停机规则、每镜四件套说明 |
| `README.md` | 项目总览、文件地图、重建命令、交付自检数字 |

## 目录

```text
01_创作说明.md … 16_V1.1_缺口清单.md   制作文档（剧本、分镜、角色、声音、剪辑、版权、缺口）
README.md / style_guide.yaml / continuity_lock.yaml / asset_manifest.yaml
assets/characters/      定妆图 2 + 角色参考页 2（含成片视角拼版）
assets/keyframes/       关键帧 9 + 派生首帧 29（derived/）+ 落幅帧 9（END/）
assets/scenes/          场景设定卡 10
assets/props/           道具卡 7
assets/overlays/        真实文字贴图 15 + OVERLAYS.md（贴合规则）
assets/textfix/         S32 纸面 / S14 车身 后期贴片
handoff/                逐镜生成包：Sxx_card.png 简报卡、Sxx_frame.png 首帧、Sxx_end.png 落幅、
                        Sxx.json 全字段、Sxx_prompt.txt 可粘贴提示词、REF/ 参考图、OVERLAY/ 文字贴图
exports/                一页创作说明 PDF、字卡/海报、QC 证据图、各类台账 CSV
html/                   statement.html（一页说明）、board.html（制作台）
subtitles/              中文字幕 SRT（主片 72 条 / 路演 40 条 / 预告 44 条）
UPLOAD_MANIFEST.csv     上传清单与哈希
```

## 未上传（按“仅图片和文档”要求排除）

- 视频：`exports/*.mp4`（主片 3:20、路演 1:55.5、短预告 72.5s、animatic）、`shots/**/*.mp4`（11 条已交付镜头 + 3 条采用条）
- 音频：`vo/*.wav`（72 句配音）、`assembly/*.wav`（配乐/音效/混音）
- 脚本：`build*.py`、`tools/*.py`、`data/*.py`
- 压缩包：`REBOOT_V1.2_*.zip`、`REBOOT_handoff_kit_*.zip`

需要其中任何一类，在本地 `D:\AI_Video\reboot` 可取；也可让我单独再推一个分支。

## 复核上传完整性

```bash
python -c "import csv,hashlib;r=list(csv.DictReader(open('UPLOAD_MANIFEST.csv',encoding='utf-8-sig')));bad=[x['path'] for x in r if hashlib.sha256(open(x['path'],'rb').read()).hexdigest()!=x['sha256']];print(len(r),'files, mismatched:',bad or 'none')"
```
