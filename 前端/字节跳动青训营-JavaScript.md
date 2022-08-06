# 字节跳动青训营-JavaScript

## 写好 JS 的一些原则

- 各司其责，让 HTML、CSS 和 JavaScript 职能分离
- 组件封装，好的 UI 组件具备正确性、拓展性、复用性
- 过程抽象，应用函数式编程思想

### 例子 1

写一段 JS，控制一个网页，让它支持浅色和深色两种浏览模式。 如果是你来实现，你会怎么做？

版本一

```javascript
const btn = document.getElementById('modeBtn');
btn.addEventListener('click', (e) => {
    const body = document.body;
    if (e.target.innerHTML === '🌞') {
        body.style.backgroundColor = 'black';
        body.style.color = 'white';
        e.target.innerHTML = '🌜';
    } else {
        body.style.backgroundColor = 'white';
        body.style.color = 'black';
        e.target.innerHTML = '🌞';
    }
});
```

版本二

```javascript
const btn = document.getElementById('modeBtn');
btn.addEventListener('click', (e) => {
    const body = document.body;
    if (body.className !== 'night') {
        body.className = 'night';
    } else {
        body.className = '';
    }
});
```

版本三

```html
<input id="modeCheckBox" type="checkbox">
<div class="content">
    <header>
        <label id="modeBtn" for="modeCheckBox"></label>
        <h1>深夜食堂</h1>
    </header>
    <main>
        <div class="pic">
            <img src="https://p2.ssl.qhimg.com/t0120cc20854dc91c1e.jpg">
        </div>
        <div class="description">
            <p>
                这是一间营业时间从午夜十二点到早上七点的特殊食堂。这里的老板，不太爱说话，却总叫人吃得热泪盈
                眶。在这里，自卑的舞蹈演员偶遇隐退多年舞界前辈，前辈不惜讲述自己不堪回首的经历不断鼓舞年轻人，最终令其重拾自信；轻言绝交的闺蜜因为吃到共同喜爱的美食，回忆起从前的友谊，重归于好；乐观的绝症患者遇到同命相连的女孩，两人相爱并相互给予力量，陪伴彼此完美地走过了最后一程；一味追求事业成功的白领，在这里结交了真正暖心的朋友，发现真情比成功更有意义。食物、故事、真情，汇聚了整部剧的主题，教会人们坦然面对得失，对生活充满期许和热情。每一个故事背后都饱含深情，情节跌宕起伏，令人流连忘返
                [6] 。
            </p>
        </div>
    </main>
</div>
```

```css
#modeCheckBox {
    display: none;
}

#modeCheckBox:checked + .content {
    background-color: black;
    color: white;
    transition: all 1s;
}
```

结论

- HTML / CSS / JS 各司其责
- 应当避免不必要的由 JS 直接操作样式
- 可以用 class 来表示状态
- 纯展示类交互寻求零 JS 方案

### 例子 2

用原生 JS 写一个电商网站的轮播图，应该怎么实现？

结构

轮播图是一个典型的列表结构，我们可以使用无序列表`ul`元素来实现。

```html
<div id="my-slider" class="slider-list">
    <ul>
        <li class="slider-list__item--selected">
            <img src="https://p5.ssl.qhimg.com/t0119c74624763dd070.png">
        </li>
        <li class="slider-list__item">
            <img src="https://p4.ssl.qhimg.com/t01adbe3351db853eb3.jpg">
        </li>
        <li class="slider-list__item">
            <img src="https://p2.ssl.qhimg.com/t01645cd5ba0c3b60cb.jpg">
        </li>
        <li class="slider-list__item">
            <img src="https://p4.ssl.qhimg.com/t01331ac159b58f5478.jpg">
        </li>
    </ul>
</div>
```

