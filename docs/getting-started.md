## Getting Started

[React 入门实例教程](http://www.ruanyifeng.com/blog/2015/03/react.html)

### Requirements

  * Mac OS X, Windows, or Linux
  * [Node.js](https://nodejs.org/) v5.0 or newer
  * `npm` v3.3 or newer (new to [npm](https://docs.npmjs.com/)?)
  * `node-gyp` prerequisites mentioned [here](https://github.com/nodejs/node-gyp)
  * Text editor or IDE pre-configured with React/JSX/Flow/ESlint ([learn more](./how-to-configure-text-editors.md))

### Directory Layout 目录

Before you start, take a moment to see how the project structure looks like:
在你开始之前，花一个时间看看这个项目的结构是怎样的：

```
.
├── /build/                     # The folder for compiled output 编译输出目录
├── /docs/                      # Documentation files for the project 项目相关文档目录
├── /node_modules/              # 3rd-party libraries and utilities 3D部分和工具目录
├── /src/                       # The source code of the application 代码源目录
│   ├── /components/            # React components React 组件目录
│   ├── /content/               # Static pages like About Us, Privacy Policy etc. 静态内容目录
│   ├── /core/                  # Core framework and utility functions 核心组件(Flux dispatcher, base classes, utilities)
│   ├── /data/                  # GraphQL server schema and data models GraphQL服务架构和数据模型
│   ├── /public/                # Static files which are copied into the /build/public folder  静态文件库
│   ├── /routes/                # Page/screen components along with the routing information 路由信息
│   ├── /client.js              # Client-side startup script 客户端启动脚本
│   ├── /config.js              # Global application settings 应用程序设置文件
│   └── /server.js              # Server-side startup script 服务器端启动脚本
├── /test/                      # Unit and end-to-end tests 单元和终端到终端的测试
├── /tools/                     # Build automation scripts and utilities 自动构建脚本及工具
│   ├── /lib/                   # Library for utility snippets 工具提示库
│   ├── /build.js               # Builds the project from source to output (build) folder 从源码编译输出
│   ├── /bundle.js              # Bundles the web resources into package(s) through Webpack 通过Webpack将资源打包
│   ├── /clean.js               # Cleans up the output (build) folder 清理输出文件夹
│   ├── /copy.js                # Copies static files to output (build) folder 拷贝静态文件
│   ├── /deploy.js              # Deploys your web application 发布Web程序
│   ├── /run.js                 # Helper function for running build automation tasks 用于运行生成自动化任务的辅助函数
│   ├── /runServer.js           # Launches (or restarts) Node.js server 启动或重启Node
│   ├── /start.js               # Launches the development web server with "live reload" 启动开发模式，带有时时更新
│   └── /webpack.config.js      # Configurations for client-side and server-side bundles 配置客户端和服务端打包工具
└── package.json                # The list of 3rd party libraries and utilities 3D部分列表
```

**Note**: The current version of RSK does not contain a Flux implementation.
It can be easily integrated with any Flux library of your choice. The most
commonly used Flux libraries are [Flux](http://facebook.github.io/flux/),
[Redux](http://redux.js.org/), and [Relay](http://facebook.github.io/relay/).

**注意**: 当前的RSK版本不包含Flux实现。
它可以很容易的集成任何你选择的Flux库。
最常用的Flux库是Facebook官方库[Flux](http://facebook.github.io/flux/)
[Redux](http://redux.js.org/), and [Relay](http://facebook.github.io/relay/).

### Quick Start 快速上手

#### 1. Get the latest version 获取最新版本

You can start by cloning the latest version of React Starter Kit (RSK) on your
local machine by running:
你可以clone最新的RSK通过运行如下的命令:

```shell
$ git clone -o react-starter-kit -b master --single-branch \
      https://github.com/kriasoft/react-starter-kit.git MyApp
$ cd MyApp
```

Alternatively, you can start a new project based on RSK right from
[WebStorm IDE](https://www.jetbrains.com/webstorm/help/create-new-project-react-starter-kit.html),
or by using [Yeoman generator](https://www.npmjs.com/package/generator-react-fullstack).
或者，你可以通过在WebStrom IDE里面创建一个新RSK工程，也可以使用Yeoman generator脚手架工具创建。

#### 2. Run `npm install`

This will install both run-time project dependencies and developer tools listed
in [package.json](../package.json) file.
通过运行`npm install`将根据配置文件package.json安装好项目运行依赖和开发工具

#### 3. Run `npm start`

This command will build the app from the source files (`/src`) into the output
`/build` folder. As soon as the initial build completes, it will start the
Node.js server (`node build/server.js`) and [Browsersync](https://browsersync.io/)
with [HMR](https://webpack.github.io/docs/hot-module-replacement) on top of it.
运行`npm start`这个命令将构架app把`/src`下的源文件输出到`/build`目录下。一旦初始化完成，将会启动Node服务和Browsersync服务以及HMR（热模块更换）

> [http://localhost:3000/](http://localhost:3000/) — Node.js server (`build/server.js`)<br>
> [http://localhost:3000/graphql](http://localhost:3000/graphql) — GraphQL server and IDE<br>
> [http://localhost:3001/](http://localhost:3001/) — BrowserSync proxy with HMR, React Hot Transform<br>
> [http://localhost:3002/](http://localhost:3002/) — BrowserSync control panel (UI)

Now you can open your web app in a browser, on mobile devices and start
hacking. Whenever you modify any of the source files inside the `/src` folder,
the module bundler ([Webpack](http://webpack.github.io/)) will recompile the
app on the fly and refresh all the connected browsers.
现在你可以在浏览器中打开你的Web应用程序，或者在移动设备上开始。
当你修改任何源文件里面的`/src`文件夹，WebPACK将重编译应用程序，并刷新所有连接的浏览器。

![browsersync](https://dl.dropboxusercontent.com/u/16006521/react-starter-kit/brwosersync.jpg)

Note that the `npm start` command launches the app in `development` mode,
the compiled output files are not optimized and minimized in this case.
You can use `--release` command line argument to check how your app works
in release (production) mode:

请注意， 在开发模式使用`npm start` 命令启动应用程序，
在这种情况下，编译后的输出文件没有优化和压缩。
您可以使用`--release` 的命令行参数，以检查您的应用程序如何工作
在release（生产）模式：

```shell
$ npm start -- --release
```

### How to Build, Test, Deploy 如何建立、测试、部署

If you need just to build the app (without running a dev server), simply run:
如果你只需要构建应用程序（没有运行一个开发服务器），只需运行：

```shell
$ npm run build
```

or, for a production build:
或者，用于生产制造：

```shell
$ npm run build -- --release
```

After running this command, the `/build` folder will contain the compiled
version of the app. For example, you can launch Node.js server normally by
running `node build/server.js`.
运行此命令后， 在`/build` 文件夹里面将包含已编译的
应用程序的版本。例如，您可以启动Node.js服务器通常由
运行`node build/server.js`。

To check the source code for syntax errors and potential issues run:
检查语法错误的源代码和运行中的潜在问题：

```shell
$ npm run lint
```

To launch unit tests:
单元测试

```shell
$ npm test              # Run unit tests with Mocha 运行摩卡单元测试
$ npm run test:watch    # Launch unit test runner and start watching for changes 运行单元测试并监听改变
```

By default, [Mocha](https://mochajs.org/) test runner is looking for test files
matching the `src/**/*.test.js` pattern. Take a look at `src/components/App/App.test.js`
as an example.

[Mocha教程](http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html)

To deploy the app, run:
要部署应用程序，运行：

```shell
$ npm run deploy
```

The deployment script `tools/deploy.js` is configured to push the contents of
the `/build` folder to a remote server via Git. You can easily deploy your app
to [Azure Web Apps](https://azure.microsoft.com/en-us/services/app-service/web/),
or [Heroku](https://www.heroku.com/) this way. Both will execute `npm install --production`
upon receiving new files from you. Note, you should only deploy the contents
of the `/build` folder to a remote server.

部署脚本`tools/deploy.js`将`/build`文件夹下的内容通过git推送到一个远程服务器。
你可以很容易地部署你的应用程序到Azure或Heroku。
在更新源文件后，都将需要执行`npm install --production`。
注意，你应该部署 `/build` 文件夹的内容到远程服务器。

### How to Update 更新升级

If you need to keep your project up to date with the recent changes made to RSK,
you can always fetch and merge them from [this repo](https://github.com/kriasoft/react-starter-kit)
back into your own project by running:
如果你需要最新版本的RSK，你需要经常fetch和merge这个仓库到你自己的项目中，通过运行如下命令:

```shell
$ git checkout master
$ git fetch react-starter-kit
$ git merge react-starter-kit/master
$ npm install
```
