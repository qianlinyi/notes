# 响应式系统与 React

## React 的历史与应用

1. 前端应用开发，如 facebook、instagram 等
2. 移动原生应用开发，如 discord，oculus 等
3. 结合 electron 进行桌面应用开发
4. 3D 场景开发

![在这里插入图片描述](https://img-blog.csdnimg.cn/c2b2a49a4fee4f10b7519bf89198efa9.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/3ae666a39e4d49ebb17a68cc7cd8bfa8.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/d3a7667c85c64b6398bf1b074b15e9c8.png)

## React 的设计思路

### UI 编程痛点

1. 状态更新，UI 不会自动更新，需要手动地调用 DOM 进行更新
2. 欠缺基本的代码层面的封装和隔离，代码层面没有组件化
3. UI 之间的数据依赖关系，需要手动维护，如果依赖链路长，则会遇到 “Callback Hell”

### 响应式与转换式

![在这里插入图片描述](https://img-blog.csdnimg.cn/5abed0fbbef94901a66e1ec4d617becf.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/0faaa7f3a3ea47b683c6fe8af3083ce0.png)

1. 状态更新，UI 自动更新
2. 前端代码组件化，可复用，可封装
3. 状态之间的互相依赖关系，只需声明即可

### 组件化

<img src="https://img-blog.csdnimg.cn/081d7296066f4143a671dce556f7fe7a.png" alt="在这里插入图片描述" style="zoom: 150%;" />

1. 组件是组件的组合 / 原子组件
2. 组件内拥有状态，外部不可见
3. 父组件可将状态传入组件内部

### 组件设计

1. 组件声明了状态和 UI 的映射
2. 组件有 Props / State 两种状态
3. “组件”可由其他组件拼装而成

### 状态归属问题

![在这里插入图片描述](https://img-blog.csdnimg.cn/57645292464c4fcd94a4541491c3439e.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/ee455c4c42c24f8491c2261365c2b382.png)

### 生命周期

![在这里插入图片描述](https://img-blog.csdnimg.cn/5c764ace517042faa9b33948702fbb9e.png)

## React 的实现

### 问题一

JSX 不符合 JS 标准语法

![在这里插入图片描述](https://img-blog.csdnimg.cn/49a28e04b1254cee88ac4938ae533e6b.png)

### 问题二

返回的 JSX 发生改变时，如何更新 DOM

![在这里插入图片描述](https://img-blog.csdnimg.cn/b7d683ba551f47348ddb1d3287ad56c0.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/c44d69784435487799ae56760892a442.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/7de9ff45c3c2409b8268a4947afeb910.png)

