# UniXNU-ruby

**English** | [中文](#中文)

Catalog entry for **ruby**, the Xiaomi Redmi Note 12 Pro 5G (MediaTek Dimensity 1080 / MT6877),
running **XNU 8796 + iPhone X iOS 16.7.16 (20H392) userland** from the stock LK bootloader.

> This repository is an identity/catalog entry, not a UniXNU build tree.
> The implementation, build recipe, hashes and device evidence live in
> **[lky005/ruby-ios-bringup](https://github.com/lky005/ruby-ios-bringup)**.
> This repository contains no Apple firmware, iOS images, device dumps or diff data.

## Status

Public `main` documents the verified 0179 line (`v0.5.0` is anchored at
`22cdb29`; current main is `b3c704f`):

| Area | State |
|---|---|
| Line | 0179: patchset `10b1e2e8…` (175 files), exec-data `a4fb021e…`, image `d438ba47…` |
| Boot | stock LK → 128 MiB boot image → XNU 8796 → HFS+ root |
| CPU | 6× Cortex-A55, 16K pages, GICv3, timers |
| Display | IOSurface/IOMFB → LK framebuffer, 1080×2400 |
| Userland | launchd → lsd → backboardd → SpringBoard |
| Input | real Goodix GT9916R from EINT14 through a child controller and a dedicated oneshot WorkLoop (0179); volume/power keys |
| Power | MT6360 battery/charger read-only; no charger control |
| Storage | UFS LUN 2, read/write HFS+ on `iosroot`; `md0` rescue root |
| Not yet | Wi-Fi, Bluetooth, cellular, audio, camera, GPU, RTC, sleep/wake, USB host/OTG, charger control; P2b G7/G8 and a full 10 min repeat were not run; no ESD timer |

G7 (0177 rollback) and G8 (USB re-plug), plus the remaining 5 min of the
repeat, were cancelled by decision. The 8-failure soft reset logged
`no-ack` and the `ok` path is not proven.

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
| [STATUS.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/records/STATUS.md) | verified device results and limits |
| [VERIFICATION.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/records/VERIFICATION.md) | what each hash/claim does and does not prove |
| [GUARANTEE.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/records/GUARANTEE.md) | success-path scope and deferred tests |
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

公开 `main` 记录的是已验证的 0179 线（`v0.5.0` 锚在 `22cdb29`；
当前 main 为 `b3c704f`）：

| 领域 | 状态 |
|---|---|
| 线 | 0179：patchset `10b1e2e8…`（175 文件）、exec-data `a4fb021e…`、镜像 `d438ba47…` |
| 启动 | 原厂 LK → 128 MiB 启动镜像 → XNU 8796 → HFS+ 根卷 |
| CPU | 6× Cortex-A55，16K 页，GICv3，定时器 |
| 显示 | IOSurface/IOMFB → LK framebuffer，1080×2400 |
| 用户态 | launchd → lsd → backboardd → SpringBoard |
| 输入 | 真实 Goodix GT9916R，0179 起由 EINT14 经子 controller + 专用 oneshot WorkLoop 驱动；音量/电源键 |
| 电源 | MT6360 电池/充电器只读；无充电控制 |
| 存储 | UFS LUN 2，`iosroot` 上 HFS+ 读写；`md0` 救援根 |
| 未完成 | Wi-Fi、蓝牙、蜂窝、音频、相机、GPU、RTC、睡眠/唤醒、USB host/OTG、充电控制；P2b G7/G8 与完整 10 min 复跑未跑；无 ESD timer |

G7（0177 回退）、G8（USB re-plug）和补测的 5 min 按决定取消。
8 连败软重置记录为 `no-ack`，`ok` 路径未证。

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
| [STATUS.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/records/STATUS.md) | 已验证的设备结果和限制 |
| [VERIFICATION.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/records/VERIFICATION.md) | 每个哈希/声明的证明边界 |
| [GUARANTEE.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/records/GUARANTEE.md) | 成功路径范围与暂缓测试 |
| [docs/README.md](https://github.com/lky005/ruby-ios-bringup/blob/main/docs/README.md) | 中英文 bring-up 文档 |

### 许可证

原创代码和文档使用 MIT 许可证；针对 Apple XNU 的补丁仍遵循 Apple Public Source
License 2.0。完整文本见 [LICENSE](LICENSE)。
