# mnblzs

**硬件设计 · 电机驱动 · 机器人系统**

围绕机器人与嵌入式设备做板级硬件，关注供电、驱动、传感与通信之间的配合。这里整理我的硬件项目、PCB 设计和调试记录，分享从原理图到样板验证的实践。

[📂 硬件作品集](https://github.com/mnblzs/resume-portfolio/blob/main/portfolio/portfolio.md) · [📄 作品集 PDF](https://github.com/mnblzs/resume-portfolio/blob/main/portfolio/portfolio.pdf) · [🔧 立创开源硬件](https://oshwhub.com/donnan) · [✉️ 邮箱联系](mailto:2030146103@qq.com)

## 关注方向

| 方向 | 主要内容 |
| --- | --- |
| 机器人硬件 | 整机供电、下位机控制、传感器接口、线束与板间连接 |
| 电机驱动 | FOC 驱动硬件、三相功率桥、栅极驱动、电流采样与编码器接口 |
| 电源与储能 | 多路电源树、升降压供电、超级电容储能与保护、电池管理 |
| 通信与接口 | USB 信号调理、CAN / RS485 / 串口、外设接口与系统联调 |
| PCB 与验证 | 原理图设计、布局布线、样板调试、BOM 与生产资料整理 |

## PCB 作品预览

| 机器人电源与下位机控制 | 工训小车控制底板 | RoboMaster 主控板 |
| :---: | :---: | :---: |
| <a href="https://github.com/mnblzs/resume-portfolio/blob/main/portfolio/imgs/full/img_17.png"><img src="https://raw.githubusercontent.com/mnblzs/resume-portfolio/main/portfolio/imgs/img_17.png" width="280" alt="机器人电源与下位机控制 PCB"></a> | <a href="https://github.com/mnblzs/solar-car-hardware"><img src="https://raw.githubusercontent.com/mnblzs/solar-car-hardware/main/images/controller-pcb.webp" width="280" alt="工训小车控制底板 PCB"></a> | <a href="https://github.com/mnblzs/resume-portfolio/blob/main/portfolio/portfolio.md"><img src="https://raw.githubusercontent.com/mnblzs/resume-portfolio/main/portfolio/imgs/img_02.png" width="280" alt="RoboMaster 主控板 PCB"></a> |
| 电源分配与控制接口 | 稳压、电机驱动与外设连接 | 机器人控制与通信 |

点击图片查看对应资料；更多实物与 PCB 图片见[完整作品集](https://github.com/mnblzs/resume-portfolio/blob/main/portfolio/portfolio.md)。

## 开源硬件仓库

完整的原理图、PCB、BOM 与说明都整理在仓库里，可导入嘉立创 EDA 专业版直接查看或复刻。

| 仓库 | 内容 | 关键器件 / 接口 |
| --- | --- | --- |
| [gh125-cable-tester](https://github.com/mnblzs/gh125-cable-tester) | GH125 系列线束通断与线序检测工装 | TP4059 充电、GH125-S02/S04/S07 连接器矩阵、MST22D18G2 拨动开关 |
| [stm32f4-dev-board](https://github.com/mnblzs/stm32f4-dev-board) | 2025 赛季步兵机器人主控开发板 | STM32F407（工程标注 F405RGT6）、ME3121 + AMS1117 供电、SN65HVD232D CAN |
| [mt6835-magnetic-encoder](https://github.com/mnblzs/mt6835-magnetic-encoder) | RM25 工程机器人关节磁编码器模块 | MT6835GT + STM32F103C8T6、MAX3051 CAN、适配大疆 3508 安装孔位 |
| [usb3-redriver-pi3eqx7502](https://github.com/mnblzs/usb3-redriver-pi3eqx7502) | USB 3.0 长线中继板（信号调理） | PI3EQX7502AI、8 位拨码调 EQ / DE、2 层 43.59 × 57.42 mm |
| [solar-car-hardware](https://github.com/mnblzs/solar-car-hardware) | 2024 工训太阳能小车三板方案 | CN3305 升压充电、超级电容单体保护、TPS63070 + DRV8837 控制底板 |

**按需求找**：修线束查线序 → `gh125-cable-tester`；主控板与 CAN 外设 → `stm32f4-dev-board`；关节角度反馈 → `mt6835-magnetic-encoder`；相机等长线 USB 3.0 掉速 → `usb3-redriver-pi3eqx7502`；整机供电与储能 → `solar-car-hardware`。

五个仓库结构一致：`docs/` 放阅读型资料，`hardware/` 放 EDA 工程与器件清单，另附 `LICENSE`、`NOTICE` 与设计文件校验值 `SHA256SUMS`，clone 后可 `sha256sum -c SHA256SUMS` 自检。

### 重点：USB 3.0 ReDriver 中继板

面向 USB 3.0 长线连接中的信号衰减问题，基于 **PI3EQX7502** 搭建信号中继与参数配置标定板，便于在具体线缆和设备组合下调整 EQ / DE 配置。

- **电路设计**：USB 双向信号通路、3.3V 供电及拨码配置电路。
- **设计记录**：仓库包含配置说明、链路测试条件与调试记录，可结合实际使用环境参考。
- **公开资料**：原理图 PDF / SVG、嘉立创 EDA 工程、BOM、Gerber 和 STEP 模型。

[项目说明](https://github.com/mnblzs/usb3-redriver-pi3eqx7502) · [原理图](https://github.com/mnblzs/usb3-redriver-pi3eqx7502/blob/main/hardware/schematic.pdf) · [硬件文件](https://github.com/mnblzs/usb3-redriver-pi3eqx7502/tree/main/hardware)

### 重点：工训太阳能小车硬件

面向 **2024 年工训新能源小车**的早期硬件实践，采用充电板、超级电容板和控制底板分工的三板方案，覆盖能量输入、储能保护与电机驱动。

| 模块 | 设计重点 |
| --- | --- |
| 充电板 | 基于 CN3305 的充电电路 |
| 超级电容板 | 串联超级电容储能及保护电路 |
| 控制底板 | 适配 STM32F103 最小系统板，TPS63070 升降压供电与 DRV8837 有刷电机驱动 |
| 外设连接 | RFID、语音模块、顶部标记灯、状态灯及模式选择接口 |

仓库以 PCB 设计和硬件功能说明为主，提供嘉立创 EDA 工程与板卡预览。电机缓启动、调速及外围模块功能需要配合单片机程序实现。

[项目说明](https://github.com/mnblzs/solar-car-hardware) · [设计工程](https://github.com/mnblzs/solar-car-hardware/tree/main/hardware) · [立创开源页面](https://oshwhub.com/donnan/gong-xun-tai-yang-neng-xiao-che-kong-zhi-di-ban)

## 更多项目实践

以下内容收录在作品集中，可查看项目介绍、PCB 和实物图片。

| 项目 | 硬件工作重点 |
| --- | --- |
| 双臂机器人与可移动底盘 | 整机电源、下位机、传感器接口、线束与系统集成 |
| 下肢外骨骼硬件系统 | 关节电机电调、IMU、磁编码器及 PCB / FPC 模块 |
| RoboMaster 步兵与工程机器人 | 主控板、电源分配、CAN 通信及执行器驱动 |
| 灰度循迹与 IMU 惯性导航小车 | 控制核心、扩展板、电源树与传感器接口 |
| 基于 ODrive 的 FOC 驱动器 | STM32F407、DRV8303 与三相全桥驱动硬件 |

[浏览图文作品集 →](https://github.com/mnblzs/resume-portfolio/blob/main/portfolio/portfolio.md)　[查看 PDF →](https://github.com/mnblzs/resume-portfolio/blob/main/portfolio/portfolio.pdf)

## 设计与调试

平时的硬件实践覆盖方案梳理、器件选型、原理图与 PCB 设计，以及样板调试和系统联调。除了单板功能，也关注电源分配、接口定义、线束装配和后续维护。

- **设计工具**：嘉立创 EDA 专业版、Altium Designer、KiCad。
- **调试工具**：示波器、逻辑分析仪、电子负载。
- **验证内容**：供电与纹波、通信链路、温升及整机配合。
- **资料整理**：根据项目范围整理原理图、BOM、生产文件与调试说明。

## 联系与交流

欢迎交流 PCB 设计、电源、电机驱动和机器人硬件相关问题，也欢迎对已公开的设计提出改进建议。

- **邮箱**：[2030146103@qq.com](mailto:2030146103@qq.com)
- **QQ**：2030146103
- **项目反馈**：请在对应仓库提交 Issue，附上板卡版本、使用条件和问题现象，便于讨论。

---

本主页包含开源设计与作品展示两类资料。可获取的文件、使用范围和授权方式请以各仓库说明及 LICENSE 为准；作品集中的展示内容不代表全部设计文件已开放。

部分项目为早期学习与实践作品，仍有完善空间。感谢社区公开方案与相关作者提供的启发，也感谢每一条反馈与建议。
