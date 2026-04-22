## SukiSU GKI 内核构建仓库

### 最近更新

- 一加骁龙 8 Elite 处理器可使用 6.6 内核(未测试)
- 修复 `5.10.(66、81、101)`、`5.15.(74、94、104)` 编译报错

### 支持

| 功能 | 说明 |
| --- | --- |
| [KernelSU](https://kernelsu.org/zh_CN/) | 包括原版、MKSU、SUKISU、NEXT |
| [SUSFS4](https://gitlab.com/simonpunk/susfs4ksu) | 在内核层面辅助 KSU 隐藏的功能补丁 |
| [BBR](https://blog.thinkin.top/archives/ke-pu-bbrdao-di-shi-shi-me) | TCP 拥塞控制算法，使网络更快 |
| [Wireguard](https://zh.wikipedia.org/wiki/WireGuard) | 参考左侧 wiki 链接 |
| [LZ4KD](https://github.com/ShirkNeko/SukiSU_patch/tree/main/other) | 听说是来自 HUAWEI Source 的 ZRAM 算法，补丁由[云彩之枫](http://www.coolapk.com/u/24963680)移植 |

还支持这几种算法，可在 Scene 的 ZRAM 切换：LZ4K、LZ4HC、deflate、842、lz4k_oplus

### 跨子版本刷机规则

当手机 GKI 主版本为 5.10.x 时（如 5.10.168），可刷写同主版本更高子版本的内核（如 5.10.198）

关于 **X-lts** 版本，以 `android12-5.10.X-lts-AnyKernel3.zip` 为例：
- **X-lts** 表示长期支持版，子版本号最大
- LTS 随着 GKI 源码更新，编译版本号将持续递增，其他如 198 的版本，是永久固定的
- 注意：LTS 虽为最新，但最新版 ≠ 最稳定（如 6.6.x 存在自动重启BUG）

### 编译优化建议

- 删除/注释不需要的 GKI 版本配置（**加速编译**）
- 添加指定 GKI 版本（参考[定制指南](https://www.coolapk.com/feed/62820671?shareKey=OGMxYmZmNTk0YzIxNjgxNzM1MzI~&shareUid=11253396&shareFrom=com.coolapk.market_15.2.2)）
- 内核构建时间，参照 [gki-kernel.yml](.github/workflows/gki-kernel.yml) 文件进行修改

### 内核版本伪装方法

在MT管理器终端执行：

```bash
uname -r | sed 's/^[^-]*//'
```

获取后直接复制，将此版本号填入 Action 编译面板即可实现内核版本伪装。
