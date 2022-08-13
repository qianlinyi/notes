# Web 多媒体入门

## Web 多媒体历史

Flash -> HTML5 -> Media Source Extensions

## 编码格式

![在这里插入图片描述](https://img-blog.csdnimg.cn/918570a3c0f84e4192909c0143dc1f87.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/a2579bb6c16d4ab9bf025a848ff6b47c.png)

### I 帧、P 帧、B 帧

![在这里插入图片描述](https://img-blog.csdnimg.cn/238f36ffa69e4cb2af6bc8be15b33cc7.png)

- I 帧又称帧内编码帧，是一种自带全部信息的独立帧，无需参考其他图像便可独立进行解码
- P 帧又称帧间预测编码帧，需要参考前面的 I 帧或者 P 帧才能进行编码
- B 帧又称双向预测编码帧，也就是 B 帧记录的是本帧与前后帧的差别

### GOP 

两个帧 I 之间的间隔

![在这里插入图片描述](https://img-blog.csdnimg.cn/3d061c3b43a14f6dab0458e0bc75a6cd.png)

### 为什么要编码？

![在这里插入图片描述](https://img-blog.csdnimg.cn/28cc23392b4748a4800fe7128a20d233.png)

#### 空间冗余

![在这里插入图片描述](https://img-blog.csdnimg.cn/ae035d6166d54b79815db7651854144a.png)

#### 时间冗余

![在这里插入图片描述](https://img-blog.csdnimg.cn/047a8516f0c94cc99f5471b441190167.png)

#### 编码冗余

![在这里插入图片描述](https://img-blog.csdnimg.cn/5ad2a0291f024497a67143499d77611a.png)

#### 视觉冗余

![在这里插入图片描述](https://img-blog.csdnimg.cn/85085837c99443409eacd0552d2e32a3.png)

### 编码数据处理流程

![在这里插入图片描述](https://img-blog.csdnimg.cn/473368aa7a9149d9bf46e3d5fcb4c5bb.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/06a194be38744670bcde4b7def3cb5e0.png)

## 封装格式

存储音视频、图片或者字幕信息的一种容器

![在这里插入图片描述](https://img-blog.csdnimg.cn/ea367e8b6132450cb1ca4fca8c320282.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/92589b0fd5e04fe6bfb964dc53f71f89.png)

## 多媒体元素和扩展 API

![在这里插入图片描述](https://img-blog.csdnimg.cn/64b49ff9f0294053b75925e69a9ab4d8.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/e5ced0ea362546aea17aa5d5e0941e6a.png)

1. 创建 mediaSource 实例
2. 创建指向 mediaSource 的 URL
3. 监听 sourceopen 事件
4. 创建 sourceBuffer
5. 向 sourceBuffer 中加入数据
6. 监听 updateend 事件

### 播放器播放流程

![在这里插入图片描述](https://img-blog.csdnimg.cn/9df63e9bf52a4c30aa303719ad086f4c.png)

## 流媒体协议

HLS 全称是 HTTP Live Streaming，是一个由 Apple 公司提出的基于 HTTP 的媒体流传输协议，用于实时音视频流的传输。目前HLS协议被广泛的应用于视频点播和直播领域

![在这里插入图片描述](https://img-blog.csdnimg.cn/ac2d03b1531644869ed2eeef3511847a.png)

## 应用场景

![在这里插入图片描述](https://img-blog.csdnimg.cn/b92a871f74ba4383b828d3b4bae2504f.png)