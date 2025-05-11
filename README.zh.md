<div align="center">
<img alt="logo" height="120" src="./public/favicon.png" width="120"/>
<h2>今日热榜</h2>
<p>汇聚全网热点，热门尽览无余</p>
<br />
<img src="./screenshots/main.jpg" style="border-radius: 16px" />
</div>

## 示例

> 这里是示例站点

- [今日热榜 - https://hot.imsyy.top/](https://hot.imsyy.top/)

## 部署

```bash
# 安装依赖
pnpm install

# 开发
pnpm dev

# 打包
pnpm build
```

### 方法一：使用 npm 安装 pnpm（推荐）

如果你已经安装了 Node.js（附带了 npm），可以通过以下命令安装 pnpm：
```bash
npm install -g pnpm
```
安装完成后，重新运行：
```bash
pnpm install
```

### 方法二：通过 Corepack 使用 pnpm（适用于 Node 16+）

启用 Corepack：
```bash
corepack enable
```
然后尝试再次安装依赖：
```bash
pnpm install
```
如果提示 corepack 不可用，请先更新 Node.js 到 v16 或更高版本。

### 方法三：检查是否真的安装了 pnpm

安装完 pnpm 后，你可以通过下面命令验证是否安装成功：
```bash
pnpm --version
```
如果有输出版本号，说明安装成功。

## 部署过程中可能会遇到的问题与解决方法

### 问题1：pnpm 命令未找到 / 不是内部或外部命令

**原因分析：**

- pnpm 没有正确安装。
- 安装后没有加入系统环境变量。
- 使用了错误的命令行工具（如 cmd、PowerShell、bash 等路径不同）。

**解决步骤：**

确认是否已全局安装 pnpm：
```bash
pnpm --version
```
如果提示命令不存在，请重新安装：
```bash
npm install -g pnpm
```

检查 Node.js 和 npm 是否安装：
```bash
node --version
npm --version
```
若未安装，请前往 [Node.js官网](https://nodejs.org/) 下载并安装 LTS 版本。

对于 Windows 系统，确保安装时勾选了“将 Node.js 添加到系统路径”选项。或者手动将 `C:\Users\用户名\AppData\Roaming\npm` 加入系统环境变量 PATH。

尝试使用 npx pnpm（不推荐长期使用）：
```bash
npx pnpm install
```

### 问题2：corepack enable 提示找不到命令

**原因分析：**

当前使用的 Node.js 版本低于 v16，而 Corepack 是从 Node.js v16 开始引入的功能。

**解决步骤：**

检查 Node.js 版本：
```bash
node --version
```
如果版本低于 v16.x，请升级 Node.js 到最新 LTS 版本。

升级 Node.js 推荐使用 nvm（Windows）或 nvm.sh（macOS/Linux）管理多个 Node.js 版本。或者卸载旧版本，前往官网下载安装新版本。

启用 Corepack：
```bash
corepack enable
```

### Vercel 部署

现已支持 Vercel 一键部署无需服务器。

> 请注意，需要修改环境变量中的 API 地址。

[Powered by Vercel](./public/ico/powered-by-vercel.svg)