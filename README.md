# 黄鹤楼 · PICO VibeLab 提交工程

本仓库为独立 Unity Android Gradle 导出，应用 ID 为 `com.bujiaban.huanghelou.pico`，仅包含 ARM64 发布所需内容。

| 配置 | 值 |
| --- | --- |
| Unity / 导出模板 | 6000.4.6f1 / 23 |
| Java / Gradle / AGP | 17 / 9.1.0 / 9.0.0 |
| Android SDK | min 29 / target、compile 36 |
| NDK | 27.2.12479018（r27c） |
| IL2CPP | 本地强制重编并预置于 jniLibs |

按 VibeLab v1.5 配置工具链路径及 `ANDROID_HOME`、`ANDROID_SDK_ROOT` 后构建：

```sh
gradle :launcher:assembleRelease --console=plain --no-daemon
```

`buildIl2Cpp` 保留原任务体，并在末尾禁用；生成的 C++ 已移除。`.vibelab-prebuilt.json` 记录 IL2CPP、metadata 和实际 jniLibs 的 SHA-256。构建缓存、APK、符号目录与本机 local.properties 均不提交。无需 Git LFS、submodule 或额外资源下载。

采用文档默认的 `page_size_policy: warn`。PICO 插件中仍有 LOAD 对齐为 0x1000 的库；本工程不声明 16 KB 页兼容。最终云端构建和审核结果以 PICO 平台为准。

提交时需将 PICO 表单生成的 deploy key 配置为本私有仓库的只读访问密钥。
