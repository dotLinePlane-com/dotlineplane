<p align="center">
  <img src="logo/logo.png" alt="DotLinePlane Logo" width="128" height="128">
</p>

<h1 align="center">点线面 Code (DotLinePlane Code)</h1>

<p align="center">
  AI 嵌入式开发IDE —— 内置串口通信、协议解析、多总线调试、AI 技能系统，打通从编码到硬件调试的全流程
</p>


---

## ✨ 亮点特性

- 🔌 **内置串口与网络工具** — 无需额外插件，开箱即用的串口监视器、TCP/UDP/WebSocket 网络调试助手，支持协议解析与波形图表
- 📊 **逻辑分析仪系统** — 深度整合 sigrok-cli，支持 131+ 协议解码与波形自动诊断，一键联动 VaporView 渲染高清波形
- 🤖 **AI 嵌入式技能与MCP系统** — 25+ 专用 Skill 配合独立 MCP 桥接，让 AI agent 可直接读写串口、操作网络连接、控制逻辑分析仪，实现"对话式硬件调试"
- 🎨 **协议帧高亮** — 自定义帧格式，数据自动着色、数值实时提取，支持图形化波形
- 📡 **多总线调试** — 串口 / CAN 总线 / VISA 仪器一站式调试
- 📐 **原理图网表提取** — 内置 sch-rnd 引擎，从原理图自动提取 MCU 引脚映射
- ⚡ **高性能数据流** — 环形缓冲 + WebSocket + 二进制序列化，10 万条数据流畅渲染

---

## 🛠️ 兼容的开发环境与调试硬件

点线面 Code 深度整合了嵌入式开发主流工具链与硬件接口，支持以下开发环境及调试工具的开箱即用与 AI agent 自动化协作：

### 💻 支持的开发环境与编译系统
* **Keil MDK** — 完美解析 `.uvproj` / `.uvprojx` 工程，支持一键构建与烧录
* **IAR EWARM** — 支持 `.eww` / `.ewp` 工程构建与适配
* **ESP-IDF** — 支持乐鑫 ESP32 系列芯片的 CMake 构建与 `esptool.py` 烧录调试
* **PlatformIO** — 完美支持 PlatformIO CLI 的跨平台工程编译、烧录与 GDB 调试
* **CMake / Makefile** — 支持基于标准工具链的通用 C/C++ 嵌入式工程构建

### 🔌 支持的调试器与烧录器
* **SEGGER J-Link** — 深度集成，支持 Flash 烧录、J-Link GDB Server 调试及高性能 **RTT 实时日志** 捕获
* **ST-Link** — 支持通过 ST-Link CLI 或 OpenOCD 进行编译产物烧录、复位及 **SWO/SWV** 追踪
* **OpenOCD** — 兼容通用 **CMSIS-DAP**、DAP-Link、FTDI 等主流调试器，提供底层硬件抽象

### 📊 支持的逻辑分析仪（经典 8 款，从入门到高端）
支持从入门教学级到高端工业级的经典逻辑分析仪，实现即插即用采集与自动诊断：
* **Saleae Logic 8 (克隆版)** [入门级] — 市面上最普及的 CY7C68013A 芯片方案（24MHz / 8通道），学习调试首选。
* **LHT00SU1** [入门级] — 基于 fx2lafw 固件的多功能虚拟仪器，集成 8 通道逻辑分析仪与简易双通道示波器。
* **Kingst LA1010 / LA2016** [中端款] — 高性价比的 16 通道数字逻辑分析仪，最高支持 100MHz / 200MHz 采样率。
* **DSLogic Basic / Plus** [中端款] — 采用 FPGA 架构的 16 通道逻辑分析仪，支持最高 400MHz 采样率与 256Mbit 硬件大缓存。
* **Openbench Logic Sniffer (OLS)** [中端款] — 经典的开源硬件 FPGA 逻辑分析仪，支持最高 32 个通道的输入捕获。
* **Saleae Logic Pro 8 / 16 (原装)** [高端款] — 旗舰便携式数字 + 模拟混合分析仪，采样率最高可达 500MS/s。
* **Digilent Digital Discovery** [高端款] — 专业高带宽嵌入式开发工具，配备 32 个高速通道与最高 800MS/s 采样率。
* **HP / Agilent 16700 系列** [高端款] — 工业级台式大型多通道逻辑分析仪系统，sigrok 适配后端，支持复杂时序和总线分析。

---

## ⚡ 嵌入式工程师专属硬核特性

针对嵌入式调试的痛点，系统提供了以下深度优化的专业级特性：

* **智能波形诊断与自动波特率探测**：集成 `sigrok-cli`，逻辑分析仪在解码失败时能自动诊断信号引脚的电平状态（恒高、恒低或噪声）。对于 UART 信号，可在未指定波特率时自动计算并推荐最合适的波特率。
* **物理接口排他与 Mutex 状态锁**：针对逻辑分析仪、串口等独占性物理硬件，引入了进程级互斥锁，协调 AI agent 自动测试与开发人员手动操作之间的硬件冲突，避免设备抢占引起崩溃。
* **原理图网表引脚自动提取**：无需反复翻阅多页 PDF 原理图。内置 `sch-rnd` 原理图引擎，可直接从 Altium Designer (`.SchDoc`)、OrCAD (`.DSN`)、KiCad 等源文件中秒级提取 MCU 引脚所连接的网表和外设关系。

---


> 📺 **视频介绍**：B站搜索「点线面 Code」查看完整功能演示 → [前往](https://space.bilibili.com/1670315857)



点线面调试助手提供 **5 种视图模式**：

| 模式 | 说明 |
|---|---|
| 📤 发送 | 发送面板 + Hex/String 数据显示 |
| 🔍 解析 | 协议解析面板 + 帧字段高亮 |
| 📊 图形 | 数值实时波形图 |
| 💻 终端 | 原生终端交互模式 |
| 🎨 设计 | 协议帧编辑器 |

---

## 🔌 串口通信系统

### 核心能力

| 功能 | 说明 |
|---|---|
| 串口收发 | 支持 Hex / String / 协议帧三种发送模式 |
| 自动分包 | 基于超时 / 固定大小 / 换行符的智能分包 |
| 协议高亮 | 自定义帧头、帧ID、帧尾和数据字段，自动着色解析 |
| 数值提取 | 支持 number / enum / bit / float 四种类型，大小端字节序 |
| 波形图表 | 3 通道实时波形，支持系数换算 |
| 硬件流控 | RTS/CTS/DTR/DSR 硬件信号控制 |
| 分屏监视 | 支持双实例分屏，独立端口 & 独立配置 |
| 串口热插拔 | 自动检测串口设备变化（2s 轮询） |
| 循环发送 | 自定义间隔循环发送数据 |
| 配置持久化 | 工作区级别 `.dotlineplane/serialtool.settings.json` |

### 协议帧配置示例

```json
{
  "functionName": "温度传感器",
  "enabled": true,
  "data": [
    { "label": "帧头", "content": "AA 55", "byteLength": 2, "color": "#FF6B6B" },
    { "label": "帧ID", "content": "03",    "byteLength": 1, "color": "#4ECDC4" },
    { "label": "2Byte", "name": "温度",    "byteLength": 2, "color": "#45B7D1",
      "showOnPanel": true, "coefficient": 0.1,
      "variableType": { "type": "number", "number": { "signed": true, "coefficient": 0.1 } }
    },
    { "label": "帧尾", "content": "3B",    "byteLength": 1, "color": "#96CEB4" }
  ]
}
```

渲染效果：
```
[12:30:45.123] RX: AA 55 03 1E 00 C8 3B
                    ─────  ──  ─────  ──
                    帧头    ID  温度    帧尾
                   (红色) (青) =20.0°C (绿)
```

---

## 🌐 网络调试系统

点线面网络调试助手内置了 TCP/UDP/WebSocket 客户端与服务端，提供多通道并发连接管理，支持协议解析与数值波形图。

### 核心能力

| 功能 | 说明 |
|---|---|
| 协议支持 | 支持 TCP Client/Server、UDP Client/Server (单播/组播/广播)、WebSocket Client/Server |
| 多连接管理 | 支持同时管理和激活多个并发的网络连接，随时查看连接状态与客户端列表 |
| 协议高亮 | 支持自定义协议帧结构，与串口共用高亮着色引擎，根据特征字段自动高亮并显示协议名称 |
| 波形图表 | 3 通道实时波形渲染，提取网络包中的数值变量进行 uPlot 高频绘制 |
| 独立显示 | 专用的 VirtualNetworkWindows 组件，可按 IP、协议（TCP=紫色，UDP=橙色，WebSocket=青色）以及客户端 ID 进行多维标签标记 |
| 配置持久化 | 工作区级别网络配置保存与加载 |

---

## 📊 逻辑分析仪系统

点线面逻辑分析仪深度整合了开源硬件调试利器 `sigrok-cli`，配合 `VaporView` 实现了物理采集与波形可视化的无缝衔接。

### 核心能力

| 功能 | 说明 |
|---|---|
| 硬件驱动支持 | 支持 fx2lafw 固件兼容逻辑分析仪（如 Saleae Logic、Kingst LA）及 80+ 种 sigrok 硬件驱动，内置固件包（check_firmware） |
| 131+ 协议解码 | 内置支持 131 种协议解码器（I2C、SPI、UART、CAN、Modbus、1-wire、USB 等），支持高级协议堆叠（Stacked Protocol） |
| 智能信号诊断 | 解码结果为空时自动分析信号是否恒高、恒低，计算信号跳变次数，诊断波特率匹配与采样率是否不足 |
| 自动波特率探测 | 使用 `guess_bitrate` 模块分析 UART 通道输入，自适应探测信号特征并推荐合适波特率 |
| VaporView 联动 | 采集完成后自动进行 VCD 非标准令牌消毒（Sanitize），并在编辑器中一键拉起 VaporView 渲染高清波形 |
| 互斥锁控制 | 内部引入 mutex 互斥锁，协调 Agent 自动测试与用户手动操作之间的硬件冲突，防止端口抢占 |

---

## 🤖 AI 嵌入式技能系统 (Embed AI Tool)

内置 **25 个专用技能模块**，让 AI 编程助手具备嵌入式开发全流程能力。支持自然语言触发或 `/skill` 命令调用。

### 技能清单

#### 🔨 构建
| 技能 | 说明 |
|---|---|
| `build-cmake` | CMake 工程构建 |
| `build-keil` | Keil MDK 工程构建 |
| `build-iar` | IAR EWARM 工程构建 |
| `build-platformio` | PlatformIO 工程构建 |
| `build-idf` | ESP-IDF 工程构建 |
| `build-makefile` | Makefile 工程构建 |

#### ⚡ 烧录
| 技能 | 说明 |
|---|---|
| `flash-keil` | Keil MDK 内置调试器烧录 |
| `flash-openocd` | OpenOCD 烧录 ELF/HEX/BIN |
| `flash-platformio` | PlatformIO 上传烧录 |
| `flash-idf` | ESP-IDF 工具链烧录 |
| `flash-jlink` | SEGGER J-Link 烧录 + RTT 日志 |

#### 🔍 调试
| 技能 | 说明 |
|---|---|
| `debug-gdb-openocd` | GDB + OpenOCD 在线调试 |
| `debug-platformio` | PlatformIO 内置 GDB 调试 |
| `debug-jlink` | J-Link GDB Server 调试 |
| `rtos-debug` | FreeRTOS/RT-Thread/Zephyr 线程感知调试 |

#### 📡 通信 & 协议调试
| 技能 | 说明 |
|---|---|
| `serial-monitor` | 串口监视（支持 MCP 工具集） |
| `modbus-debug` | Modbus RTU/TCP 寄存器读写 & 从站扫描 |
| `can-debug` | CAN 总线帧监听、发送 & 节点扫描 |
| `visa-debug` | VISA 仪器 SCPI 通信 & 波形捕获 |

#### 🛠️ 分析 & 辅助
| 技能 | 说明 |
|---|---|
| `memory-analysis` | .map / ELF 内存分析 & 符号排名 |
| `static-analysis` | cppcheck / clang-tidy / MISRA-C 合规检查 |
| `peripheral-driver` | 开源 BSP 外设驱动搜索 & 适配 |
| `stm32-hal-development` | STM32 HAL 库开发最佳实践 |
| `netlist-extract` | 原理图网表提取 & MCU 引脚映射 |
| `workflow` | 多技能流水线编排（编译→烧录→监控） |

### AI 对话示例

```
👤 编译烧录
🤖 检测到 Keil 工程 Project.uvprojx，目标芯片 STM32F103C8。
   ✅ 编译成功，产物: build/Project.axf (48.2 KB)
   检测到 ST-Link V2，烧录中...
   ✅ 烧录成功，已校验并复位。

👤 看串口
🤖 检测到 COM3 (115200)，抓取日志：
   [00:00.000] System Start
   [00:00.012] UART initialized

👤 PA5 连接了什么？
🤖 从原理图中提取网表，PA5 连接了 SPI1_SCK → U3-6 (W25Q64 Flash)。
```

---

## 🔗 MCP 硬件调试工具集

软件内置的 AI Agent 可通过 [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) 直接操控串口、网络和逻辑分析仪硬件，实现全方位的 **"对话式硬件调试"**。

### 🔌 串口 MCP 工具 (serial-mcp-server)

| MCP Tool | 说明 |
|---|---|
| `list_serial_ports` | 列出所有可用串口及状态 |
| `open_serial_port` | 打开串口（配置波特率、数据位等） |
| `close_serial_port` | 关闭串口 |
| `read_serial_buffer` | 读取缓冲数据（支持 hex / string / highlighted 模式） |
| `send_serial_data` | 发送数据（hex 或 string 格式） |
| `get_serial_status` | 获取 Rx/Tx 统计 & 连接状态 |
| `get_protocol_config` | 获取当前协议高亮配置 |
| `update_protocol_config` | 更新协议配置（立即生效） |
| `set_display_flags` | 设置显示标志（hex/时间戳/方向过滤等） |

### 🌐 网络 MCP 工具 (network-mcp-server)

| MCP Tool | 说明 |
|---|---|
| `list_connections` | 列出当前已建立的所有网络连接及状态 |
| `connect` | 开启新的网络连接（指定 TCP/UDP/WS 协议、客户端/服务端角色、IP与端口） |
| `disconnect` | 断开指定的网络连接（包含释放监听端口或终止客户端连接） |
| `get_clients` | 获取特定网络服务端下所有已连接的客户端列表 |
| `disconnect_client` | 强制断开网络服务端的指定客户端 |
| `read_buffer` | 读取网络接收/发送缓冲区数据（支持 hex / string / highlighted 分段高亮） |
| `write_network` | 发送网络数据，支持 Hex/String 格式，支持单播向特定客户端发送 |
| `update_protocol_config` | 动态热更新网络协议高亮解析配置 |
| `get_protocol_config` | 读取当前网络协议的高亮配置详情 |
| `clear_screen` | 清除网络连接对应的接收数据显示区 |

### 📊 逻辑分析仪 MCP 工具 (logic-analyzer-mcp)

| MCP Tool | 说明 |
|---|---|
| `show_version` | 获取 sigrok-cli 版本、支持的驱动 and 协议解码器列表 |
| `scan_devices` | 扫描当前主机上物理连接的逻辑分析仪硬件（如 fx2lafw、Saleae 等） |
| `capture_data` | 控制硬件进行波形采集（支持采样率、样点数/时间、触发配置，可自动用 VaporView 渲染波形） |
| `decode_protocol` | 对已采集的波形文件进行 131+ 协议的结构化解码，解码失败自动诊断，支持自适应波特率探测 |
| `read_channel_level` | 读取指定通道的电平脉冲摘要，以快速确认引脚电平变化 |
| `list_supported_decoders` | 查询 sigrok 支持的全部协议解码器列表（如 UART、I2C、SPI、CAN） |
| `show_decoder_details` | 查看指定协议解码器的详细物理通道要求、选件配置及堆叠依赖 |
| `list_supported_hardware` | 列出 sigrok 支持的 80+ 种物理驱动与适配设备 |
| `check_firmware_status` | 检查并管理用于物理硬件启动的固件包加载情况 |

### 双进程桥接工作原理

```
AI Agent
            ↓ MCP stdio
  [mcp-server.js] (独立进程)
            ↓ HTTP
  [McpBridge] (Extension Host)
            ↓ 直接调用
  [Service] (串口 I/O / 网络 socket / sigrok-cli)
            ↓
       物理硬件设备
```

---

## 📐 原理图网表提取

内置 **sch-rnd** 原理图引擎（已编译为各平台二进制），支持从主流 EDA 工具的原理图中提取网表。

### 支持的原理图格式

| 格式 | 文件后缀 |
|---|---|
| Altium Designer | `.SchDoc` |
| OrCAD Capture | `.DSN` |
| KiCad (v5/v6+) | `.sch` / `.kicad_sch` |
| PADS ASCII | `.TXT` |
| sch-rnd 原生 | `.lht` |

### 输出示例

```
| 引脚 | 网络名    | 连接器件         | 功能推断    |
|------|----------|-----------------|-----------|
| PA5  | SPI1_SCK | U3-6 (W25Q64)   | SPI 时钟   |
| PA6  | SPI1_MISO| U3-2 (W25Q64)   | SPI 数据输入|
| PA7  | SPI1_MOSI| U3-5 (W25Q64)   | SPI 数据输出|
```

---

## 🚀 快速开始

### 使用串口工具

1. 打开点线面调试助手
2. 侧边栏选择串口设备（自动检测 CH340、CP210x、ST-Link 等）
3. 设置波特率（默认 115200）
4. 点击「打开」开始监视
5. 在中央数据区查看实时数据

### 配置协议解析

1. 切换到「解析」视图模式
2. 在侧边栏添加协议配置
3. 定义帧头、帧ID、数据字段和帧尾
4. 设置字段颜色和数值类型
5. 数据自动高亮解析并提取数值


---

## 🗺️ Roadmap

| 状态 | 功能 | 说明 |
|---|---|---|
| 🔜 | **SCPI 仪器控制** | 增强 AI Agent 对台式万用表、示波器等测量仪器的操作能力，支持通过标准 SCPI 指令读取测量值并自动绘制波形 |
| 🔜 | **CAN 通信调试** | 原生 CAN 总线收发面板（类似串口工具），支持 DBC 文件解析、帧过滤、信号图表 |
| 🔜 | **RTT 实时日志** | 支持 SEGGER RTT（J-Link）、openOCD 、和 SWO/SWV（ST-Link）实时日志流，零开销替代 UART 打印 |
| 🔜 | **MCP 在线调试** | AI 通过 MCP 直接操控调试器 —— 设置断点、单步执行、查看变量和寄存器，支持 J-Link / ST-Link / CMSIS-DAP / openOCD |

> 💡 **愿景**：让 LLM 不仅能写代码，还能直接操控硬件调试器 —— 用自然语言说「在 main.c 第 42 行设个断点，单步运行到 HAL_UART_Init 看看 BaudRate 的值」，AI 即可自动完成。

---

## 🤝 社区 & 反馈

- 💬 **QQ**: 50260563
- 🌐 **官网(待发布)**: [dotlineplane.com](https://www.dotlineplane.com)

---



Copyright © DotLinePlane
