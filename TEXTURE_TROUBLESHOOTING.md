# 纹理加载故障排除

## 问题：显示紫色/洋红色方块

紫色/洋红色是 Minecraft 的"缺失纹理"指示器，表示游戏找不到纹理文件。

## 解决步骤

### 1. 确认文件存在
检查文件是否存在于正确位置：
```
src/main/resources/assets/examplemod/textures/gui/ldd.png
```

### 2. 检查文件名
- 文件名必须是 `ldd.png`（全小写）
- 扩展名必须是 `.png`
- 不能有额外的空格或特殊字符

### 3. 重新构建项目
纹理文件需要被打包到 mod 中：

**Windows (CMD):**
```cmd
gradlew clean
gradlew build
```

**Windows (PowerShell):**
```powershell
.\gradlew clean
.\gradlew build
```

**Linux/Mac:**
```bash
./gradlew clean
./gradlew build
```

### 4. 刷新 IDE
如果使用 IntelliJ IDEA 或 Eclipse：
- IntelliJ: File → Invalidate Caches / Restart
- Eclipse: Project → Clean

### 5. 检查控制台输出
运行游戏时查看控制台，应该看到：
```
[IslandRenderer] 开始加载背景纹理...
[IslandRenderer] 尝试路径: gui/ldd
[TextureValidator] 验证纹理: examplemod:gui/ldd
[TextureValidator] ✓ 纹理加载成功
[IslandRenderer] ✓ 纹理加载成功，使用路径: gui/ldd
```

如果看到错误，会显示详细信息。

### 6. 验证 PNG 文件
确保 PNG 文件有效：
- 使用图像查看器打开文件
- 确认文件没有损坏
- 推荐尺寸：256x64 像素
- 支持透明度（RGBA）

### 7. 检查资源包结构
确认目录结构正确：
```
src/main/resources/
└── assets/
    └── examplemod/
        └── textures/
            └── gui/
                └── ldd.png
```

### 8. 临时使用纯色背景
如果纹理问题持续，可以暂时使用纯色背景：

删除或重命名 `ldd.png`，系统会自动使用纯色圆角矩形。

## 常见错误

### 错误 1: 路径大小写
```
❌ GUI/ldd.png
❌ Gui/ldd.png
✅ gui/ldd.png
```

Windows 不区分大小写，但打包后的 mod 会区分！

### 错误 2: 包含 textures 前缀
```
❌ new ResourceLocation("examplemod", "textures/gui/ldd")
✅ new ResourceLocation("examplemod", "gui/ldd")
```

ResourceLocation 会自动添加 `textures/` 前缀。

### 错误 3: 包含扩展名
```
❌ new ResourceLocation("examplemod", "gui/ldd.png")
✅ new ResourceLocation("examplemod", "gui/ldd")
```

不需要 `.png` 扩展名。

### 错误 4: 文件未打包
如果在开发环境中工作正常，但打包后不工作：
- 确认 `build.gradle` 正确配置资源
- 检查 `build/libs/` 中的 jar 文件是否包含纹理
- 使用 7-Zip 或 WinRAR 打开 jar 查看内容

## 调试命令

### 查看详细日志
在 `IslandConfig` 中启用调试模式：
```json
{
  "debugMode": true
}
```

### 手动测试纹理
在代码中添加：
```java
TextureValidator.validateTexture(new ResourceLocation("examplemod", "gui/ldd"));
TextureValidator.printCommonIssues();
```

## 如果问题仍然存在

1. 检查 Minecraft 版本兼容性（1.8.9）
2. 确认 Forge 版本正确
3. 查看完整的错误堆栈跟踪
4. 尝试使用其他已知有效的纹理文件测试
5. 考虑使用纯色背景作为替代方案

## 联系支持

如果以上步骤都无法解决问题，请提供：
- 完整的控制台输出
- 文件结构截图
- `build.gradle` 内容
- Minecraft 和 Forge 版本
