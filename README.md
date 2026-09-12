# 内存块读写助手 (memory-access)

Mindustry **v160** 单机辅助 mod。悬停内存块时，在方块上方显示两个可点击图标，快速读写内存块内容。

## 功能

- **读（📋 图标）**：将内存块全部槽位编码复制到剪贴板。
- **写（📄 图标）**：从剪贴板解析数字并写回内存块的数字槽。
- **可配置上限**：设置 → 内存块读写 → 「最大复制长度」，超过上限的块会提示复制失败（默认 16384）。
- **虚拟选中**：鼠标移到图标上不会丢失选中。
- **仅单机运行**：联机（客户端/服务器）时功能自动停用；mod 带 `hidden` 标签，装了它的玩家仍可进入任意服务器。

## 安装

1. 构建（见下）得到 `memory-access.jar`；
2. 放入游戏 `mods/` 目录；
3. 游戏内启用即可。

## 构建

需要 JDK 17+ 与 Gradle（本项目 `build.gradle` 以 jitpack 上的 `core:v160` / `arc-core:v160` 作为 `compileOnly` 依赖）：

```bash
gradle jar
# 产物在 build/libs/memory-access.jar
```

## 说明

- 内存块在 v160 中为多槽结构（默认 32 槽，可被地图/内容改为 512、16384 等）。
- 读写通过反射访问 `MemoryBlock.MemoryBuild` 的私有字段 `objectMemory` / `numberMemory`（见 `MemoryIO.java`）。
- 只操作数字槽；对象槽会被跳过。

## 作者

蓝色大肥鱼

## 许可

[GPL-3.0](LICENSE)
