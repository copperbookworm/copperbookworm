# 你好，我是 copperbookworm 👋

独立开发者。两条主线：给 **Squad（50v50 战术射击）** 做一整套**离线战术工具链**，以及自己用 **Godot 4** 做战术射击游戏《解域》。

交付习惯一致：**纯本地计算、离线可用、单文件 / 单 APK 双击就能跑**，每个版本都要在真机上验一遍再发。

![Godot](https://img.shields.io/badge/Godot_4.7-GDScript-478CBF?logo=godotengine&logoColor=white)
![Python](https://img.shields.io/badge/Python-tkinter-3776AB?logo=python&logoColor=white)
![C%23](https://img.shields.io/badge/C%23-.NET_9-512BD4?logo=dotnet&logoColor=white)
![Android](https://img.shields.io/badge/Android-minSdk_26-3DDC84?logo=android&logoColor=white)

## 项目

| 项目 | 是什么 | 技术 | 现状 |
|---|---|---|---|
| [Yehorivka-Passability](https://github.com/copperbookworm/Yehorivka-Passability) | Squad 25 张官方地图的**离线战术地形分析 + 标绘** App | 单页 Canvas + Android WebView | [v0.34.0](https://github.com/copperbookworm/Yehorivka-Passability/releases/latest) · APK 51.6 MB |
| [map-water-bridge-annotator](https://github.com/copperbookworm/map-water-bridge-annotator) | 地图图层**标注器**：水域 / 桥梁 / 边界 / 道路 / 障碍掩膜 | Python · tkinter · PyInstaller | [v1.1.0](https://github.com/copperbookworm/map-water-bridge-annotator/releases/latest) · exe 30.7 MB |
| [Yehorivka-MapData](https://github.com/copperbookworm/Yehorivka-MapData) | 上面那个 App 的**地图数据源**（manifest + 25 个单图包） | JSON + PNG | 26 个文件 · 约 63 MB |
| [PRTSC_App_Squad](https://github.com/copperbookworm/PRTSC_App_Squad) | SquadShot：PrtSc 一键截图，按地图与层级自动命名 | C# · .NET 9 WinForms | [v1.0.0](https://github.com/copperbookworm/PRTSC_App_Squad/releases/latest) · exe 45.7 MB |
| [jieyu-tactics](https://github.com/copperbookworm/jieyu-tactics) | 《解域》：2D 垂直俯视 **20v20 小队战术射击** | Godot 4.7.1 · GDScript | [架构站](https://copperbookworm.github.io/jieyu-tactics/) · APK 30.3 MB |

## Squad 战术工具链

**Yehorivka-Passability** —— 把 25 张官方地图的高程、坡度、树冠、建筑、围墙、道路、水域、桥梁、旗点全部栅格化，在手机上算载具路线、可达区、通视、伏击点、架枪位、火力支援阵位，并在图上直接标绘。

- 载具：A\* 路线（长度 / 累计爬升 / 最大坡度 / ETA）、可达区、四类载具参数、直升机着陆地
- 步兵：伏击推荐、区域入口与架枪位、隐蔽推进、区域分区观察点、载具火力支援时间轴
- 通视：2 km 三色着色、沿线并集 / 交集、测距、逐格查询（高程 / 坡度 / 树冠 / 世界坐标）
- 标绘：110 个敌情图标、自由路线、区域标注、AAS / RAAS / Invasion 真实占领区、300 m 游戏网格
- **没有 INTERNET 权限**：数据全部打进 APK，飞行模式照用；同一份 HTML 也是桌面版

**map-water-bridge-annotator** —— 上面那些图层的人工标注端：六个图层、五种工具，输出 2048×2048 的 PNG 掩膜，再交给地图生成器合成数据包。最近给它加了「**一键上传数据到 GitHub**」：面板里显示连通性（RTT / API 配额）、比对进度、传输速度与剩余时间，只推变过的文件，图包先传、manifest 最后传。

**Yehorivka-MapData** —— 数据包的分发仓库，App 的「地图数据 · 在线更新」直接读它的 manifest。

**SquadShot** —— 托盘常驻，按 PrtSc 自动截图、读游戏日志取当前地图与层级命名，单文件 exe，免安装免运行时。

## 《解域》· jieyu-tactics

1 km × 1 km 的丘陵草原上，带 2 个小队（5 组 × 4 人）与 20 人规模的敌方争夺五个节点；15 分钟一局，RAAS 五节点，第一版没有服务器，AI 填满对局。

| 指标 | 数值 |
|---|---|
| GDScript | 205 个文件 / 38,578 行（不含 addons） |
| 单元测试 | 62 个脚本、2,205 项断言，headless 全绿 |
| 集成冒烟 | 317 项断言，失败 0 |
| Android | 30.3 MB APK，gradle 自定义构建 + 真机验证 |

## 工作方式

- **AI 辅助，但要有门禁**：把重复流程固化成可执行的检查——headless 测试、真机安装与截图、UI 几何断言（按钮重叠 / 出屏 / 点击目标）、性能采样、文档对账。每次提交都要有能复现的输出，不是「看起来没问题」。
- **数据来源与算法口径写清楚**：地图数据来自 SquadCalc 公开的高程图与关卡资源实例；坡度用 5 m 网格高程做 Sobel，郁闭度是 25 m 窗口内树冠占比，路线是 A\* 近似而不是游戏内物理模拟——这些阈值和口径都写在各自 README 里。

## 其他

- [Coolweather](https://github.com/copperbookworm/Coolweather) —— 早期的开源 Android 天气应用

---

<p align="center"><sub>最近更新：2026-10-27</sub></p>
