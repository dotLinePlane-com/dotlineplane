<p align="center">
  <img src="logo/logo.png" alt="DotLinePlane Logo" width="128" height="128">
</p>

<h1 align="center">点线面 Code (DotLinePlane Code)</h1>

<p align="center">
  AI 嵌入式开发IDE —— 内置串口通信、协议解析、多总线调试、AI 技能系统，打通从编码到硬件调试的全流程
</p>


---

## ✨ 亮点特性

- 🔌 **内置串口工具** — 无需额外插件，开箱即用的串口监视器、协议解析器、波形图表
- 🤖 **AI 嵌入式技能系统** — 25+ 专用 Skill，覆盖编译、烧录、调试、协议调试全流程
- 🎨 **协议帧高亮** — 自定义帧格式，数据自动着色、数值实时提取，支持图形化波形
- 📡 **多总线调试** — 串口 / Modbus RTU&TCP / CAN 总线 / VISA 仪器一站式调试
- 🔗 **MCP 协议桥接** — AI Agent 可直接通过 MCP 读写串口数据，实现"对话式硬件调试"
- 📐 **原理图网表提取** — 内置 sch-rnd 引擎，从原理图自动提取 MCU 引脚映射
- ⚡ **高性能数据流** — 环形缓冲 + WebSocket + 二进制序列化，10 万条数据流畅渲染

---


> 📺 **视频介绍**：B站搜索「点线面Code」查看完整功能演示 → [前往](https://space.bilibili.com/1670315857)



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

## 🔗 MCP 串口工具集

AI Agent（如 Kilo Code）可通过 [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) 直接操作串口，实现 **"对话式硬件调试"**。

### 可用工具

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

### 工作原理

```
AI Agent (Kilo Code / Claude)
    ↓ MCP stdio
serial-mcp-server.js (独立进程)
    ↓ HTTP
SerialMcpBridge (Extension Host)
    ↓ 直接调用
SerialService (串口 I/O)
    ↓
物理串口设备
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
| 🔜 | **网络调试助手** | 内置 TCP / UDP Client & Server，支持 WebSocket，替代第三方网络调试工具 |
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
