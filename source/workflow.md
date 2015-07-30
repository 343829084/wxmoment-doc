title: "自定义详情页前端工作流"
date: "2014-03-16 18:17:16"
---

WxMoment-Workflow 是由微信朋友圈广告团队基于 Gulp 面向广告详情页开发者提供的工作流。工作流集成了详情页开发中的常见任务，可以简化开发工作，并在打包环节对资源进行压缩合并优化。

> 工作流包含了批处理文件，Windows 用户可直接双击执行。Mac 用户可以执行相应的命令。

### 下载安装

前往 [NodeJS 官网](https://nodejs.org/) 下载安装包并按指南安装 NodeJS，安装完成后请下载最新的 [工作流压缩包](https://github.com/TmT/WxMoment-Workflow/releases) 并解压。

双击工作流目录中的 `安装.bat` 文件（windows用户请右键使用管理员身份打开）即可开始安装依赖，若出现问题建议直接在命令行执行以下命令（windows用户管理员身份打开cmd，mac用户请加sodu）：

```bash
$ cd WxMoment-Workflow
$ npm install gulp -g --registry=https://r.cnpmjs.org
$ npm install --registry=https://r.cnpmjs.org
```

### 目录说明

所有的开发都在 `src` 目录下进行，你只需要按约定好的放置相应文件，并按自己的项目需求编写代码即可。

```text
├── package.json
├── tasks                           //工作流任务配置（一般不需要修改）
└── 20150514-promo-vivo             //示例项目，项目目录
    ├── .tmtworkflowrc              //工作流的项目配置文件（一般不需要修改）
    ├── gulpfile.js                 //工作流的任务配置文件（一般不需要修改）
    └── src                         //源文件目录，所有的开发在此目录下进行
        ├── css                     //样式表目录，使用 Less，只有 style-*.less 的文件名会被编译
        │   └── style-promo.less
        ├── html                     //HTML目录
        │   └── index.html            
        ├── img                      //图片目录 
        └── slice                    //雪碧图目录，此目录下的图片会进行合并，同名的 @2x 图片会被识别并进行合并
```

### 创建项目

从 `20150514-promo-vivo` 复制一个文件夹，重命名为自己的项目。

> 命名规则：YYYYMMDD-promo-品牌名称。
> YYYYMMDD 为 4 位年份，2 位月份，2 位日期数字组成，品牌名称为全小写英文字母。


### 任务介绍

**开发任务**

执行 `开发.bat` 开始执行任务，或执行命令：

```bash
$ cd WxMoment-Workflow/project
$ gulp build_dev
```

此任务将启动一个 HTTP Server，并自动在浏览器打开 `http://localhost:8080/html/index.html` 这样的地址。

**打包任务**

开发完成后，执行 `打包.bat`，或执行命令：

```bash
$ cd WxMoment-Workflow/project
$ gulp zip
```

此任务将在项目目录下生成一个压缩包，压缩包以项目名命名。

### 更多功能介绍

**JavaScript 合并**

在 HTML 中，使用注释的方式前面包含起来即可。

```html
<!-- build:js ../js/lib.js -->
<script src="../js/kalok.js"></script>
<script src="../js/main.js"></script>
<!-- endbuild -->
```
以上代码，在打包的时候，会将 kalok.js 与 main.js 合并压缩为 lib.js，并替换 html 中的引用。