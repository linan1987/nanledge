# Node.js

## 在 CentOS 8 上使用 NodeSource 仓库安装

### 1. 更新系统包

```powershell
sudo dnf update -y
```

### 2. 安装必要的开发工具（可选）

虽然不是必须的，但安装一些开发工具可以避免后续可能出现的问题

```powershell
sudo dnf update -y
```

### 3. 添加 NodeSource 仓库

访问 NodeSource 的 GitHub 页面 获取最新的安装脚本链接。假设你想安装 Node.js 18.x 版本，可以使用以下命令：
(https://github.com/nodesource/distributions#deb)

```powershell
curl -fsSL https://rpm.nodesource.com/setup_lts.x -o nodesource_setup.sh
bash nodesource_setup.sh
```
或
```powershell
curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash -
```

注意：如果你想安装其他版本的 Node.js，请将 setup_18.x 替换为相应的版本号，例如 setup_16.x。


### 4. 验证仓库是否添加成功

```powershell
sudo dnf repolist
```

### 5. 安装 Node.js 和 npm

```powershell
sudo dnf install nodejs -y
node -v
npm -v
```