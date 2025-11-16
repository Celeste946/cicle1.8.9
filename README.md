# Minecraft Forge 1.8.9 模组开发项目

这是一个基于Minecraft Forge 1.8.9的模组开发项目。

## 项目结构

- `src/main/java` - Java源代码目录
- `src/main/resources` - 资源文件目录
- `build.gradle` - Gradle构建配置文件
- `run/` - 运行时目录，包含配置文件和日志

## 开发环境设置

1. 确保已安装JDK 8
2. 运行 `gradlew setupDecompWorkspace` 设置开发环境
3. 运行 `gradlew eclipse` 或 `gradlew idea` 生成IDE项目文件
4. 运行 `gradlew build` 构建项目

## 功能特性

本项目包含以下功能：
- 动态岛显示
- 快速移动模块
- GUI渲染优化
- 健康卡片显示
- 物品栏白屏修复
- OpenGL渲染框架

## 许可证

本项目基于Forge许可证发布。详见LICENSE文件。