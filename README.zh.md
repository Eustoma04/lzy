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



// 安装依赖
pnpm install

// 开发
pnpm dev

// 打包
pnpm build

// 具体步骤：

方法一：使用 npm 安装 pnpm（推荐）
# 如果你已经安装了 Node.js（附带了 npm），可以通过以下命令安装 pnpm：


npm install -g pnpm
# 安装完成后，重新运行：


pnpm install
方法二：通过 Corepack 使用 pnpm（适用于 Node 16+）

# 启用 Corepack：

corepack enable
# 然后尝试再次安装依赖：

pnpm install
# 如果提示 corepack 不可用，请先更新 Node.js 到 v16 或更高版本。

方法三：检查是否真的安装了 pnpm
# 安装完 pnpm 后，你可以通过下面命令验证是否安装成功：

pnpm --部署
# 如果有输出版本号，说明安装成功。


```
//部署过程中可能会遇到的问题与解决方法：

问题1：pnpm 命令未找到 / 不是内部或外部命令

    原因分析：

        pnpm 没有正确安装。
        安装后没有加入系统环境变量。
        使用了错误的命令行工具（如 cmd、PowerShell、bash 等路径不同）。
    解决步骤：

        确认是否已全局安装 pnpm：
        
        
        pnpm --version
        如果提示命令不存在，请重新安装：
        
        npm install -g pnpm
        检查 Node.js 和 npm 是否安装：
    
        node --version
        npm --version
        若未安装，请前往 Node.js官网 下载并安装 LTS 版本。
        如果使用的是 Windows 系统：
        确保安装时勾选了“将 Node.js 添加到系统路径”选项。
        或者手动将 C:\Users\用户名\AppData\Roaming\npm 加入系统环境变量 PATH。
        尝试使用 npx pnpm（不推荐长期使用）：
    
    
        npx pnpm install
 问题2：corepack enable 提示找不到命令

    原因分析：

        当前使用的 Node.js 版本低于 v16，而 Corepack 是从 Node.js v16 开始引入的功能。
    解决步骤：

        检查 Node.js 版本：

        node --version
        如果版本低于 v16.x，请升级 Node.js 到最新 LTS 版本。
        升级 Node.js：
        推荐使用 nvm（Windows）或 nvm.sh（macOS/Linux）管理多个 Node.js 版本。
        或者卸载旧版本，前往官网下载安装新版本。
        启用 Corepack：


    corepack enable
 问题3：依赖安装失败 / 报错（如 ECONNRESET、ETIMEDOUT）

    原因分析：

        网络连接不稳定。
        包镜像源不可用。
        权限问题（特别是在 Linux/macOS 上）。
    解决步骤：

        切换 npm 镜像源为国内加速器（如淘宝源）：

        npm config set registry https://registry.npmmirror.com
        或使用官方方式：

        pnpm config set registry https://registry.npmmirror.com
        清除缓存并重试：

        pnpm cache clean
        pnpm install --force
        使用代理（如有需要）：

        pnpm config set proxy http://your-proxy-url:port
        检查网络连接或更换网络环境（如换 WiFi）
问题4：开发模式启动失败（pnpm dev 出错）

        常见报错信息：

        Error: Cannot find module 'xxx'
        Port already in use
        Failed to load URL ...
    解决步骤：

        确保依赖已成功安装：

        pnpm install
        检查端口是否被占用（默认是 3000 或 5173）：

        lsof -i :3000   # macOS/Linux
        netstat -ano | findstr :3000   # Windows
        找到 PID 后终止进程：

        taskkill /F /PID <PID>   # Windows
        kill -9 <PID>            # macOS/Linux
        查看详细错误日志：
        通常终端会输出具体出错模块名，可针对性地搜索解决方案。
        也可查找项目中的 vite.config.js 或 .env 文件是否有配置错误。
问题5：打包失败（pnpm build 出错）

    可能原因：

        某些依赖未正确安装。
        构建工具（如 Vite、Webpack）配置错误。
        内存不足或路径权限问题。
    解决步骤：

        清理缓存并重新构建：

        pnpm build --modern --clean-cache
        查看错误详情：
        终端通常会显示哪一步骤失败，比如某个插件未正确加载。
        增加 Node.js 内存限制（适用于大项目）：

        node --max-old-space-size=8192 node_modulesite/binite.js build
        检查输出目录权限：
        如果输出目录（如 dist/）无写权限，会导致构建失败。
问题6：部署到服务器后页面空白 / 404

    可能原因：

        静态资源路径配置错误。
        路由模式为 history，但服务器未配置回退到 index.html。
        构建目标平台设置错误（如构建为现代浏览器，但实际运行在老旧浏览器上）。
    解决步骤：

        检查 vite.config.js 中的 base 配置：


        export default defineConfig({
        base: './', // 或根据部署路径调整
        })
        配置服务器回退规则（以 Nginx 为例）：


        location / {
        try_files $uri $uri/ /index.html;
        }
        使用 hash 模式路由（Vue/React Router）：
        如果不想配置服务器，可以改用 hash 模式路由。
        兼容性处理：

        pnpm build --target es2015

总结建议:针对命令未识别问题，建议检查安装、环境变量及Corepack；对于依赖安装失败，可尝试更换镜像源、清除缓存或排查网络问题；启动失败时需检查依赖、端口和配置文件；构建失败可清理缓存、调整内存限制或检查插件配置；页面空白或404则应核查路径配置、服务器设置及路由模式。

<!-- 梁展毓 -->

## Vercel 部署

现已支持 Vercel 一键部署，无需服务器

> 请注意，需要修改环境变量中的 API 地址

![Powered by Vercel](./public/ico/powered-by-vercel.svg)
