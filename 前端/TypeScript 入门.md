# TypeScript 入门

## TypeScript 介绍

### 发展历史

![在这里插入图片描述](https://img-blog.csdnimg.cn/f604dee6db98443c81738a619232a261.png)

### JS vs TS

| JavaScript | TypeScript |
| ---------- | ---------- |
| 动态类型   | 静态类型   |
| 弱类型语言 | 弱类型语言 |

### TypeScript 特性

#### 静态类型

- 可读性增强：基于语法解析TSDoc，ide增强
- 可维护性增强：在编译阶段暴露大部分错误

多人合作的大型项目中，获得更好的稳定性和开发效率

#### JS 的超集

- 包括于兼容所有 JS 特性，支持共存
- 支持渐进式引入与升级

## 基本语法

### 基础数据类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/0bd9a9339a784ec2a04cd3b9e20ac304.png)

### 对象类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/4fb03e6c134f4d709c3e747717d4f64b.png)

### 函数类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/291026f527344c919c0fab6b776623bf.png)

### 函数重载

![在这里插入图片描述](https://img-blog.csdnimg.cn/2df86f5879a942b68c9803ecf7f9e516.png)

### 数组类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/1ecf78515b684b4e8cdfafdc06dc2822.png)

### TypeScript 补充类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/1df43f55e27a4525984524283e4ee6f1.png)

### TypeScript 泛型

![在这里插入图片描述](https://img-blog.csdnimg.cn/b19dd3f6557a423abc7f282bb04d3c39.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/280955f6b95d4874adba530574dbe09f.png)

### 类型别名 & 类型断言

![在这里插入图片描述](https://img-blog.csdnimg.cn/a0a67e8f49c94581a9c0779cbb851a8f.png)

### 字符串 / 数字 字面量

![在这里插入图片描述](https://img-blog.csdnimg.cn/2b5a64a7132841c4bee92167fe6df3ad.png)

## 高级类型

### 联合 / 交叉类型

- 联合类型：A｜B 联合类型表示一个值可以是几种类型之一
- 交叉类型：A & B 多种类型叠加到一起成为一种类型，它包含了所需的所有类型的特性

![在这里插入图片描述](https://img-blog.csdnimg.cn/b9275fccef0745c1ac081470746c0f29.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/e65986bff60746ce8aef6ef71605f5bd.png)

### 类型保护与类型守卫

![在这里插入图片描述](https://img-blog.csdnimg.cn/7cb8877f6d2246608d038757a2c97a23.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/40c18712df324238a4ba2fe8e15a69ce.png)

### 高级类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/32e708f8a1334318a4a2ab144d9d0095.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/fb811ba7ccfd4d9988cfd5ecf5f67459.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/cf287a6f4215477191e9f000460138f6.png)

### 函数返回值类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/15aa2b2c19e040eb955267df7635edf4.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2471c7089d384e3090a26b49bc53dd72.png)

## 工程应用

### Web

1. 配置 webpack loader 相关配置

2. 配置 tsconfig.js 文件

3. 运行 webpack 启动 / 打包

4. loader 处理 ts 文件时，会进行编译与类型检查

### Node

1. 安装 Node 与 npm
2. 配置 tsconfig.js 文件
3. 使用 npm 安装 TSC
4. 使用 tsc 运行编译得到 js 文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/541929bbe7b24f74af6ad76104dc30e6.png)