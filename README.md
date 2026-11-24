<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/banner.svg" alt="sixpencecn // AI engineer · computer vision · LLM applications" width="100%" />
</p>

<p align="center">
  <img alt="STATUS ONLINE · FOCUS rotating · MODE LOCAL FIRST · BUILD STABLE" src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/badges.svg" />
</p>

<p align="center">
  <a href="https://github.com/sixpencecn"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-sixpencecn-181717?style=for-the-badge&logo=github&logoColor=white" /></a>
  <img alt="Followers" src="https://img.shields.io/github/followers/sixpencecn?style=for-the-badge&logo=github&logoColor=white&color=2F81F7&label=followers" />
  <img alt="Profile views" src="https://komarev.com/ghpvc/?username=sixpencecn&style=for-the-badge&color=2F81F7&label=VIEWS" />
</p>

```console
sixpencecn@github:~$ whoami
AI 工程师 — 工业视觉 / LLM 应用 / 能落地的产品工具

sixpencecn@github:~$ cat focus.txt
› 能在真实光照下活下来的视觉算法，不是只会跑 demo 的
› 指标可以复现、可以追溯、可以被人挑刺
› 交付物要能直接上产线，或者直接打开就能玩

sixpencecn@github:~$ ls projects/
glue-defect-detection-yolov8/   PCB-Defect-Detection-YOLOv8/
qingxu-workbench/               neon-snake/
tcp-debug/                      item-snake/
```

---

### ▍01 // GLUE DEFECT DETECTION · 工业胶路缺陷检测

> 锂电池封装打胶工序的 YOLOv8 质检系统。针对 2.5D 光源下的胶面反光与光照波动，
> 从图像采集、预处理、标注、训练、推理到 Excel 追溯，完整工程闭环。

**4 类判定**：`OK` / `断胶` / `缺胶` / `溢胶` —— 对应产线实际判定标准。

<table>
  <tr>
    <td width="50%" align="center">
      <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/sample_synthetic.png" alt="四类胶路样本：OK / 断胶 / 缺胶 / 溢胶" width="100%" />
      <br/><sub>合成样本：四类胶路形态</sub>
    </td>
    <td width="50%" align="center">
      <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/detect_preview.png" alt="断胶检测推理结果，置信度 0.98" width="100%" />
      <br/><sub>推理结果：断胶 0.98</sub>
    </td>
  </tr>
</table>

真实基线（合成数据集，YOLOv8n / imgsz 320 / CPU / 3 轮冒烟测试）：

| 指标 | 数值 |
| :--- | ---: |
| Precision | 0.9202 |
| Recall | 0.8972 |
| mAP@0.5 | 0.9739 |
| mAP@0.5:0.95 | 0.6718 |

评测口径：每类 60 张、共 240 张合成图，按 168/48/24 划分，`--seed 42`。
该结果用于验证数据标注正确、模型可收敛；正式精度需将 epochs 提升至 100 重新训练。

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/training_results.png" alt="3 轮冒烟测试的损失与指标曲线" width="88%" />
  <br/><sub>训练曲线：box/cls/dfl loss 与 precision / recall / mAP（3 轮冒烟测试）</sub>
</p>

<p align="center">
  <a href="https://github.com/sixpencecn/glue-defect-detection-yolov8"><img src="https://img.shields.io/badge/%E6%9F%A5%E7%9C%8B%E6%BA%90%E7%A0%81-glue--defect--detection--yolov8-0B1020?style=for-the-badge&logo=github&logoColor=2F81F7" alt="repo" /></a>
  <img src="https://img.shields.io/badge/YOLOv8-Ultralytics-2F81F7?style=for-the-badge&logo=ultralytics&logoColor=white" alt="yolov8" />
  <img src="https://img.shields.io/badge/PyQt5-GUI-22D3EE?style=for-the-badge&logo=python&logoColor=white" alt="pyqt" />
</p>

---

### ▍02 // PCB DEFECT DETECTION · PCB 电路板缺陷检测

> 基于 YOLOv8 与 DeepPCB 数据集的 PCB 缺陷检测系统。覆盖 **6 类**真实缺陷：
> 开路 / 短路 / 针孔 / 毛刺 / 鼠咬 / 伪铜，含 PyQt5 可视化界面、批量检测与 Excel 质检报表。

<table>
  <tr>
    <td width="50%" align="center">
      <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/demo_open_12100003.jpg" alt="PCB 检测结果：短路/伪铜/针孔/鼠咬" width="100%" />
      <br/><sub>多类同帧：短路 0.44 / 伪铜 0.91 / 针孔 0.68 / 鼠咬 0.91</sub>
    </td>
    <td width="50%" align="center">
      <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/demo_mousebite_12100023.jpg" alt="PCB 检测结果：开路/短路/毛刺/伪铜/针孔" width="100%" />
      <br/><sub>多类同帧：开路 0.52 / 毛刺 0.35 / 伪铜 0.85 / 针孔 0.94</sub>
    </td>
  </tr>
</table>

真实测试指标（YOLOv8n / CPU / 30 epochs / batch 16 / imgsz 320）：

| 指标 | 数值 |
| :--- | ---: |
| Precision | 0.8934 |
| Recall | 0.7825 |
| mAP@0.5 | 0.8763 |
| mAP@0.5:0.95 | 0.6024 |

<p align="center">
  <a href="https://github.com/sixpencecn/PCB-Defect-Detection-YOLOv8"><img src="https://img.shields.io/badge/%E6%9F%A5%E7%9C%8B%E6%BA%90%E7%A0%81-PCB--Defect--Detection--YOLOv8-0B1020?style=for-the-badge&logo=github&logoColor=2F81F7" alt="repo" /></a>
  <img src="https://img.shields.io/badge/YOLOv8-Ultralytics-2F81F7?style=for-the-badge&logo=ultralytics&logoColor=white" alt="yolov8" />
  <img src="https://img.shields.io/badge/PyQt5-GUI-22D3EE?style=for-the-badge&logo=python&logoColor=white" alt="pyqt" />
</p>

---

### ▍03 // QINGXU WORKBENCH · 轻序个人工作台

<p align="center">
  <a href="https://github.com/sixpencecn/qingxu-workbench">
    <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/qingxu-workbench.svg" alt="Qingxu workbench — dashboard preview" width="88%" />
  </a>
</p>

| | |
| :--- | :--- |
| **本地优先** | 数据仅存浏览器，不上传；离线可用，安装为 PWA |
| **一站式** | 日程 · 待办 · 打卡 · 专注 · 记账 · 相册日记 |
| **多端交付** | 桌面安装 + Android APK（v1.1） |
| **设计克制** | 青绿单色系、响应式，移动端底部导航 |

<p align="center">
  <a href="https://github.com/sixpencecn/qingxu-workbench"><b>▸ 查看源码</b></a>
</p>

---

### ▍04 // NEON SNAKE · 有手感的贪吃蛇

<p align="center">
  <a href="https://sixpencecn.github.io/neon-snake/">
    <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/neon-snake.png" alt="Neon Snake gameplay" width="88%" />
  </a>
</p>

| | |
| :--- | :--- |
| **零依赖** | Canvas + ES modules，三个文件，无构建步骤 |
| **手感细节** | 插值移动、两级输入缓冲、运行时合成音效、触控支持 |
| **可测试** | `game.js` 无 DOM、可设种子；19 条断言在浏览器直接运行 |
| **有规格** | [PRD v2.0](https://github.com/sixpencecn/neon-snake/blob/main/docs/PRD-v2.0.md)：17 节，含指标树、验收标准与终止条件 |

<p align="center">
  <a href="https://sixpencecn.github.io/neon-snake/"><b>▶ 立即试玩</b></a> · <a href="https://github.com/sixpencecn/neon-snake">源码</a>
</p>

---

### ▍05 // TOOLING · 小工具

| 项目 | 是什么 |
| :--- | :--- |
| **[tcp-debug](https://github.com/sixpencecn/tcp-debug)** | 浏览器 TCP 调试助手：客户端/服务端双模式，UTF-8/GBK/ASCII/HEX 编解码，SSE 实时日志 |
| **[item-snake](https://github.com/sixpencecn/item-snake)** | PRD 3.0 道具贪吃蛇：苹果 / 减速 / 加速 / 减身 / 毒药 / 双倍分数 |

---

### ▍SYS.MONITOR · 数据面板

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@f6d06ff/assets/stats.svg" alt="repository metrics" width="100%" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-0B1020?style=flat-square&logo=python&logoColor=2F81F7" alt="python" />
  <img src="https://img.shields.io/badge/PyTorch-0B1020?style=flat-square&logo=pytorch&logoColor=22D3EE" alt="pytorch" />
  <img src="https://img.shields.io/badge/OpenCV-0B1020?style=flat-square&logo=opencv&logoColor=2F81F7" alt="opencv" />
  <img src="https://img.shields.io/badge/JavaScript-0B1020?style=flat-square&logo=javascript&logoColor=F7DF1E" alt="javascript" />
  <img src="https://img.shields.io/badge/React-0B1020?style=flat-square&logo=react&logoColor=22D3EE" alt="react" />
  <img src="https://img.shields.io/badge/PWA-0B1020?style=flat-square&logo=pwa&logoColor=8B5CF6" alt="pwa" />
  <img src="https://img.shields.io/badge/Docker-0B1020?style=flat-square&logo=docker&logoColor=2F81F7" alt="docker" />
  <img src="https://img.shields.io/badge/Git-0B1020?style=flat-square&logo=git&logoColor=F05032" alt="git" />
</p>

---

### ▍ABOUT · 关于我

- **走 AI 主线** — 从胶路 / PCB 工业缺陷检测到 LLM 应用，不做只会跑 demo 的研究
- **工程闭环** — 数据、训练、推理、报表、界面，交付物要能被真实使用
- **产品意识** — 本地优先、零依赖、可离线，写成能双击打开的小工具
- **重视度量** — 评测口径、失败模式、单帧耗时，比 demo 的华丽更重要

---

### ▍NOW · 正在做

- 搭一个小型 agent runtime：工具调用、有界循环、trace 日志
- 写一套自己敢信的评测框架，再考虑加新功能
- 把工业视觉项目从原型推向部署

---

<p align="center">
  <a href="https://github.com/sixpencecn"><img src="https://img.shields.io/badge/GitHub-sixpencecn-181717?style=for-the-badge&logo=github&logoColor=white" alt="github" /></a>
  <a href="https://github.com/sixpencecn/sixpencecn/issues/new"><img src="https://img.shields.io/badge/Open%20an%20issue-2F81F7?style=for-the-badge&logo=github&logoColor=white" alt="issue" /></a>
</p>

<details>
<summary><b>EN · Read in English</b></summary>

<br>

**sixpencecn** — AI engineer. Industrial vision, LLM applications, and tools that actually ship.

- **Glue Defect Detection** — YOLOv8 QC for lithium-battery sealing lines. 4 defect classes, full loop from data to PyQt5 GUI and Excel traceability. Smoke-test baseline: Precision 0.9202, Recall 0.8972, mAP@0.5 0.9739 (3 epochs on 240 synthetic images — a convergence check, not final accuracy).
- **PCB Defect Detection** — YOLOv8 on the DeepPCB dataset: 6 classes (open / short / pinhole / burr / mousebite / spurious copper), PyQt5 GUI, batch inference and Excel reports. Test metrics: Precision 0.8934, Recall 0.7825, mAP@0.5 0.8763 (30 epochs on CPU).
- **Qingxu Workbench** — a local-first personal dashboard: calendar, todos, habits, pomodoro, finance and photo journal. Offline PWA, data stays in the browser, installable on desktop and Android.
- **Neon Snake** — a dependency-free canvas Snake with interpolated motion, a two-deep input buffer, synthesised audio, touch controls and a 19-assertion browser test suite. [Play it](https://sixpencecn.github.io/neon-snake/).
- **tcp-debug / item-snake** — a browser TCP debugging assistant, and a PRD-driven Snake with power-ups.

I care about evaluation, failure modes, and tools that work offline. Always measuring, rarely guessing.

</details>

<p align="center"><sub>BUILD 2026.11 · LOCAL-FIRST · EVALUATION-FIRST · NO CLOUD REQUIRED</sub></p>
