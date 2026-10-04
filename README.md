# HWDBY OrangeFox 云端编译

本仓库只做一件事：用 GitHub Actions 编译 **华为 MatePad 11 (DBY-W09 / HWDBY)** 的
**OrangeFox Recovery**。

## 内容

| 文件 | 说明 |
|---|---|
| `.github/workflows/build_ofox.yml` | 编译工作流（释放磁盘 → 装依赖 → 解压设备树 → repo sync → lunch → mka recoveryimage → 上传产物）|
| `HWDBY_device_tree.zip` | 设备树（含预编译内核 `prebuilt/Image` 与 `prebuilt/dtb.img`，故云端**不需要编译内核**）|

## 用法

Actions → **Build OrangeFox Recovery (HWDBY)** → **Run workflow**

- `source`：`orangefox`（默认）
- `branch`：`11.0`

编译完成后在该次运行的 **Artifacts** 区下载：

- **`recovery-HWDBY`** —— 里面是 `recovery.img`（刷入用）
- `build-log` —— 编译日志（出问题看这个）

## 刷入

```
fastboot flash recovery_ramdisk recovery.img
```
