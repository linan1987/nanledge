# Node.js Feature

## v20.6

### 原生支持 .env 文件

引入了对.env文件的原生支持，允许开发者直接在Node.js中使用.env文件配置环境变量，无需依赖第三方模块（如dotenv）。

```powershell
node --env-file .env main.js
node --env-file .dev.env main.js
```

## v21.7

### 环境变量功能增强

新增了两个API来加载和解析环境变量process.loadEnvFile(path)用于加载指定路径的.env文件。

如果未指定路径，则会自动加载当前目录下的.env文件。

util.parseEnv(content)用于解析包含环境变量赋值的字符。

## v22.0

### 监听模式

从Node.js 22版本开始，观察模式（node --watch）已经稳定。

在监听模式下，当被监视的文件发生变化时，Node.js进程将自动重新启动，不再需要借助第三方模块（如 nodemon）。

```powershell
node --watch main.js
```

### 内置 WebSocket 客户端（稳定版）

内置 WebSocket 客户端成为于稳定功能，不再需要--experimental-websocket标志来启用。WebSocket的实现遵循了浏览器中WebSocket API的标准，这意味着在Node.js中使用WebSocket的方式将与在JavaScript中使用WebSocket的方式非常相似。

### 支持通过require()引入ESM

打破了CommonJS与ESM之间的界限，允许开发者使用require()函数来导入ESM 模块。这为大型项目和遗留系统提供了一个平滑过渡的方案，因为它们可以逐个模块迁移到ESM，而不是一次性对整个项目进行修改。

### 支持运行 package.json 中的脚本

添加了一个新命令行标志--run，允许直接从命令行执行package.json中定义的脚本。这提供了一个标准化的方式执行脚本，有助于统一不同包管理器在处理脚本时的行为，并且直接使用node执行脚本要比通过npm执行脚本更快。

## v23.0

### 原生支持 ES 模块

> 以下应该是指：可以直接按 ES 模块方式写 export、import，无需额外配置。  
> 而不仅仅可以通过 require() 加载 ES 模块

Node.js v23.0最大的亮点之一是原生支持通过 require() 加载 ES 模块。这意味着开发者可以直接使用require()来加载ES模块，而无需额外的工具或配置。


### 停止支持 32 位Windows系统

不再支持32位Windows，专注于现代环境。