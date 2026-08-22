# opendcdiag-arm-rpm-24.03

OpenDCDiag (ARM64) 离线构建依赖 RPM 包仓库 —— openEuler 24.03 LTS 系列。

按 OS 版本(基准 / SP1 / SP2 / SP3 / SP4)分子目录存放对应版本的 RPM,供无网络目标机离线安装。其中 `openEuler-24.03LTS_SP3` 是 OpenDCDiag ARM64 的基准构建版本。

## 目录结构

```
opendcdiag-arm-rpm-24.03/
├── README.md
├── openEuler-24.03LTS/         # 基准版
├── openEuler-24.03LTS_SP1/
├── openEuler-24.03LTS_SP2/
├── openEuler-24.03LTS_SP3/     # ← 基准构建版本
├── openEuler-24.03LTS_SP4/
    每个子目录:
    ├── .os-version          # 版本标记(内容=目录名,install-deps.sh 严格核对)
    └── *.rpm                # 含完整依赖树
```

## 用法

本仓库作为 [opendcdiag-arm](https://github.com/wangxumarshall/opendcdiag-arm) 的 git submodule,路径 `third-party/rpms/openEuler-24.03`。目标机离线安装时:

```bash
cd third-party/rpms/openEuler-24.03/openEuler-24.03LTS_SP3
../../../../scripts/offline-build/install-deps.sh .
```

## 版本对应

以 `openEuler-24.03LTS_SP3` 包名列表为基准,在对应版本仓库取同名包 + 完整依赖树。

| OS 版本 | RPM 数量 | 基准包名交集 | 来源 |
|---|---|---|---|
| openEuler-24.03LTS | 324 | 324 / 326 | openEuler 24.03 LTS aarch64 仓库 |
| openEuler-24.03LTS_SP1 | 324 | 324 / 326 | openEuler 24.03 LTS SP1 aarch64 仓库 |
| openEuler-24.03LTS_SP2 | 324 | 324 / 326 | openEuler 24.03 LTS SP2 aarch64 仓库 |
| openEuler-24.03LTS_SP3 | 326 | 326 / 326 | openEuler 24.03 LTS SP3 aarch64 仓库 |
| openEuler-24.03LTS_SP4 | 329 | 324 / 326 | openEuler 24.03 LTS SP4 aarch64 仓库 |

> 下载机与目标机必须 openEuler 版本一致,否则离线安装会因降级冲突/glibc-devel 精确版本依赖而失败。
