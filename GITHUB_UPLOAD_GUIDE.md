# GitHub上传指南

本指南将帮助您将Minecraft Forge 1.8.9模组项目上传到GitHub。

## 前提条件

1. 安装Git（如果尚未安装）
   - 访问 https://git-scm.com/downloads 下载并安装Git
   - 安装完成后，重启命令行工具

2. 创建GitHub账户（如果尚未创建）
   - 访问 https://github.com 并注册账户

## 步骤1：初始化Git仓库

1. 打开命令行工具（CMD或PowerShell）
2. 导航到项目目录：
   ```
   cd "e:\我的世界模组开发\forge-1.8.9-11.15.1.2318-1.8.9-mdk"
   ```

3. 初始化Git仓库：
   ```
   git init
   ```

4. 添加所有文件到Git：
   ```
   git add .
   ```

5. 创建初始提交：
   ```
   git commit -m "Initial commit: Minecraft Forge 1.8.9 mod project"
   ```

## 步骤2：创建GitHub仓库

1. 登录GitHub网站
2. 点击右上角的"+"图标，选择"New repository"
3. 填写仓库信息：
   - Repository name: `minecraft-forge-1.8.9-custom-mod`
   - Description: `自定义Minecraft Forge 1.8.9模组开发项目，包含动态岛、快速移动等功能`
   - 选择Public或Private（根据您的需求）
   - 不要勾选"Initialize this repository with a README"（因为我们已经创建了一个）

4. 点击"Create repository"

## 步骤3：将本地仓库推送到GitHub

1. 在创建仓库后，GitHub会显示快速设置页面
2. 复制"…or push an existing repository from the command line"部分的命令
3. 在命令行中执行这些命令（替换为您的GitHub用户名）：
   ```
   git remote add origin https://github.com/YOUR_USERNAME/minecraft-forge-1.8.9-custom-mod.git
   git branch -M main
   git push -u origin main
   ```

## 步骤4：验证上传

1. 刷新GitHub仓库页面
2. 确认所有文件都已成功上传
3. 检查README.md文件是否正确显示

## 可选：添加.gitignore文件

为了防止不必要的文件被提交（如构建输出、临时文件等），您可以创建一个.gitignore文件：

1. 在项目根目录创建.gitignore文件
2. 添加以下内容：
   ```
   # Build output
   build/
   bin/
   out/
   
   # IDE files
   .idea/
   .eclipse/
   .vscode/
   *.iml
   *.ipr
   *.iws
   
   # Gradle
   .gradle/
   gradlew
   gradlew.bat
   
   # Running environment
   run/
   logs/
   crash-reports/
   
   # OS generated files
   .DS_Store
   .DS_Store?
   ._*
   .Spotlight-V100
   .Trashes
   ehthumbs.db
   Thumbs.db
   ```

3. 添加并提交.gitignore文件：
   ```
   git add .gitignore
   git commit -m "Add .gitignore file"
   git push origin main
   ```

## 后续维护

- 每次进行重要更改后，使用以下命令提交并推送：
  ```
  git add .
  git commit -m "描述您的更改"
  git push origin main
  ```

## 常见问题

1. **认证问题**：如果推送时要求输入用户名和密码，请使用GitHub个人访问令牌（Personal Access Token）而不是密码。

2. **分支问题**：如果遇到分支相关错误，可能需要先创建main分支：
   ```
   git branch main
   git checkout main
   ```

3. **大文件问题**：如果项目中有大文件，可能需要使用Git LFS（Large File Storage）。

完成这些步骤后，您的Minecraft Forge 1.8.9模组项目将成功上传到GitHub！