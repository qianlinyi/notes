# Webpack 知识体系

## 为什么要学习 Webpack

- 理解前端“工程化”概念、工具、目标
- 一个团队总要有那么几个人熟悉 Webpack，某种程度上可以成为个人的核心竞争力
- 高阶前端必经之路

## 什么是 Webpack

![在这里插入图片描述](https://img-blog.csdnimg.cn/31052d381440464fa725e8abcc45cfad.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/63ddd6bc63584ccbb92dbc1eeec51839.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/384d51ceca964f7e86f250ae43369333.png)

Webpack 本质上是一种前端资源编译、打包工具

- 多份资源文件打包成一个 Bundle
- 支持 Babel、Eslint、TS、Less、Sass 等
- 支持模块化处理 css、图片等资源文件
- 支持 HMR+ 开发服务器
- 支持持续监听、持续构建
- 支持代码分离
- 支持 Tree-shaking
- 支持 Sourcemap

## 使用 Webpack

### 示例

![在这里插入图片描述](https://img-blog.csdnimg.cn/63be5da8dee04a2882c51747891dbe3c.png)

### 核心流程

![在这里插入图片描述](https://img-blog.csdnimg.cn/2c833eaa91e14e15b43dfb70e78a76bf.png)

### 模块化 + 一致性

![在这里插入图片描述](https://img-blog.csdnimg.cn/778dc532369b49c8be25d45da2fcee23.png)

### 使用

![在这里插入图片描述](https://img-blog.csdnimg.cn/aec7f1b6ddc94b029d69e224ec5cc560.png)

### 流程类配置

![在这里插入图片描述](https://img-blog.csdnimg.cn/5c43f2c9875a4babbaf8752af1a5eed4.png)

### 配置总览

![在这里插入图片描述](https://img-blog.csdnimg.cn/ed3ebdecf7c24ed8b2625469da311cf5.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/954449c06d024c44a05879fedc2101c7.png)

### 处理 CSS

![在这里插入图片描述](https://img-blog.csdnimg.cn/805161bb5ef74462bcb557bb893cf405.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/5af9ae8573774f4585a9b14d140da367.png)

### 接入 Babel

![在这里插入图片描述](https://img-blog.csdnimg.cn/f54ea057adce4ec39792f527b7724569.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/9e5b2167e7f9472ca3d2807d95d549fc.png)

### 生成 HTML

![在这里插入图片描述](https://img-blog.csdnimg.cn/34392689985640deb7ec49fc440018a4.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/1bf3ede73523488cba2f1c8c2f6d6a39.png)

### 工具线

![在这里插入图片描述](https://img-blog.csdnimg.cn/8b89efb7ac1040b186e63512d36c7bfe.png)

### HMR

![在这里插入图片描述](https://img-blog.csdnimg.cn/b00c57e0782f448aa9a59e4e73d5d7d4.png)

### Tree-Shaking

树摇，用于删除 Dead Code 

![在这里插入图片描述](https://img-blog.csdnimg.cn/a3ef928790ea4503b155e4383159c5a8.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/3a1949e495094a06bbb4112164b0565a.png)

## 理解 Loader

![在这里插入图片描述](https://img-blog.csdnimg.cn/3b2490528f3c42d08c60920a8a717c7d.png)

### 使用 Loader

![在这里插入图片描述](https://img-blog.csdnimg.cn/3022cc3a09014baf89ce4cf5ec5ebdb0.png)

### 认识 Loader：链式调用

![在这里插入图片描述](https://img-blog.csdnimg.cn/c380ef2f3ea64016aa2b93021b31c948.png)

### 认识 Loader：其他特性

![在这里插入图片描述](https://img-blog.csdnimg.cn/eaaff668b09b4ee78eec901c588a0528.png)

### 常见 Loader

![image-20220808161451814](/Users/zaizai/Library/Application Support/typora-user-images/image-20220808161451814.png)

## 理解插件

![在这里插入图片描述](https://img-blog.csdnimg.cn/c35dbf0938824614818bf32f6801c2f6.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/a70bfda928c945c6b80ff5a752b851d1.png)

## 学习方法

![在这里插入图片描述](https://img-blog.csdnimg.cn/a1a329a1311743a4ac98cfa2a3bd1dcc.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/6cf9afd0cc644525924f0395522449d1.png)