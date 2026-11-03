# UniXNU-ruby

**English** | [中文](#中文)

Catalog entry for **ruby**, the Xiaomi Redmi Note 12 Pro 5G (MediaTek Dimensity 1080 / MT6877),
running **XNU 8796 + iPhone X iOS 16.7.16 (20H392) userland** from the stock LK bootloader.

> This repository is an identity/catalog entry, not a UniXNU build tree.
> The implementation, build recipe, hashes and device evidence live in
> **[lky005/ruby-ios-bringup](https://github.com/lky005/ruby-ios-bringup)**.
> This repository contains no Apple firmware, iOS images, device dumps or diff data.

## Status

Public `main` documents the verified 0155 line:

| Area | State |
|---|---|
| Boot | stock LK → 128 MiB boot image → XNU 8796 → HFS+ root |
| CPU | 6× Cortex-A55, 16K pages, GICv3, timers |
| Display | IOSurface/IOMFB → LK framebuffer, 1080×2400 |
| Userland | launchd → lsd → backboardd → SpringBoard |
| Input | real Goodix GT9916R over bit-bang SPI3; volume/power keys |
| Power | MT6360 battery/charger read-only; no charger control |
| Storage | UFS LUN 2, read/write HFS+ on `iosroot`; `md0` rescue root |
| Not yet | Wi-Fi, Bluetooth, cellular, audio, camera, GPU, RTC, sleep/wake, USB host/OTG, charger control |

The development branch `p3-eint-hal` (0160, `ruby_eint` / EINT14) is in development.
Its CI builds are green, but this repository does not claim a 0160 device gate.

## UniXNU relationship

- **UEFI: not applicable.** This port boots XNU directly from the stock LK bootloader through a
  128 MiB Android boot image. It does not use the UniXNU UEFI framework, DarwinBoot, or a
  format-2 kernel/package/firmware build.
- This repository therefore carries only the catalog identity: `board.toml`, `porting.toml`,
  this README and the license. It has no CI and no build inputs.
- `porting.toml` is the authoritative status table. Its statuses describe the linked
  `ruby-ios-bringup` work, not a build from this repository.

## Links

| Link | Contents |
|---|---|
| [lky005/ruby-ios-bringup](https://github.com/lky005/ruby-ios-bringup) | source, patches, build recipe and current pins |
| [STATUS.md](https://github.com/lky005/ruby-ios-bringup/blob/main/STATUS.md) | verified device results and limits |
| [VERIFICATION.md](https://github.com/lky005/ruby-ios-bringup/blob/main/VERIFICATION.md) | what each hash/claim does and does not prove |
| [docs/README.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/README.md) | English/Chinese bring-up chapters |

## License

The original code and documentation are MIT-licensed; patches against Apple XNU remain under
the Apple Public Source License 2.0. See [LICENSE](LICENSE) for the exact text.

---

## 中文

**ruby**（Xiaomi Redmi Note 12 Pro 5G，联发科天玑 1080 / MT6877）的目录条目，
从原厂 LK 直接启动 **XNU 8796 + iPhone X iOS 16.7.16（20H392）用户态**。

> 本仓库只用于目录身份登记，不是 UniXNU 构建树。
> 实现、构建配方、哈希和设备证据都在
> **[lky005/ruby-ios-bringup](https://github.com/lky005/ruby-ios-bringup)**。
> 本仓库不包含任何 Apple 固件、iOS 镜像、设备转储或 diff 数据。

### 状态

公开 `main` 记录的是已验证的 0155 线：

| 领域 | 状态 |
|---|---|
| 启动 | 原厂 LK → 128 MiB 启动镜像 → XNU 8796 → HFS+ 根卷 |
| CPU | 6× Cortex-A55，16K 页，GICv3，定时器 |
| 显示 | IOSurface/IOMFB → LK framebuffer，1080×2400 |
| 用户态 | launchd → lsd → backboardd → SpringBoard |
| 输入 | 真实 Goodix GT9916R（bit-bang SPI3）；音量/电源键 |
| 电源 | MT6360 电池/充电器只读；无充电控制 |
| 存储 | UFS LUN 2，`iosroot` 上 HFS+ 读写；`md0` 救援根 |
| 未完成 | Wi-Fi、蓝牙、蜂窝、音频、相机、GPU、RTC、睡眠/唤醒、USB host/OTG、充电控制 |

开发分支 `p3-eint-hal`（0160，`ruby_eint` / EINT14）仍在开发中。
其 CI 构建为绿色，但本仓库不声称 0160 设备门已通过。

### 与 UniXNU 的关系

- **UEFI：不适用。** 本项目从原厂 LK 通过 128 MiB Android 启动镜像直接启动 XNU，
  不使用 UniXNU UEFI 框架、DarwinBoot 或 format 2 的内核/package/固件构建。
- 因此本仓库只保留目录身份所需的 `board.toml`、`porting.toml`、README 和许可证，
  没有 CI，也没有构建输入。
- `porting.toml` 是权威状态表；其中的状态描述的是所链接的 `ruby-ios-bringup`
  工作，而不是从本仓库构建的结果。

### 链接

| 链接 | 内容 |
|---|---|
| [lky005/ruby-ios-bringup](https://github.com/lky005/ruby-ios-bringup) | 源码、补丁、构建配方和当前固定版本 |
| [STATUS.md](https://github.com/lky005/ruby-ios-bringup/blob/main/STATUS.md) | 已验证的设备结果和限制 |
| [VERIFICATION.md](https://github.com/lky005/ruby-ios-bringup/blob/main/VERIFICATION.md) | 每个哈希/声明的证明边界 |
| [docs/README.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/README.md) | 中英文 bring-up 文档 |

### 许可证

原创代码和文档使用 MIT 许可证；针对 Apple XNU 的补丁仍遵循 Apple Public Source
License 2.0。完整文本见 [LICENSE](LICENSE)。
