# CSS 总结

## 布局

### 1.两栏布局

float

```css
.clearfix::after{
content:'';
display:block;
clear:both;
}
.container>aside {
width:200px;
float:left;
}
.container>main {
margin-left:200px;
}
```

flex:

```
.container{
display:flex;
}
.container>aside{
width:200px;
}
.comtainer>main{
flex-grow:1;
}

```

grid:

```
.container{
  display:grid;
  grid:auto auto/ 200px 1fx;
}
.container>aside{
	height:600px;
	grid-area:1/
}
```



### 2. 三栏布局

float:

```
<body>
<div class="clearfix">
<div class="aside left">左侧边栏固定宽度</div>
<div class="aside right">右侧边栏固定宽度</div> //tip
<div class="main">内容区块大小自适应</div>
</div>
<style>
	.clearfix::after{
	content:'';
	display:block;
	clear:both; 
	}
  .aside{
    width:150px;
    height:400px;
    background:red;
  }
  .main{
    margin-left:150px;
    margin-right:150px;
    background:blue;
    height:500px;
  }
  .left{
    float:left;
  }
  .right{
    float:right;
  }
</style>
```



### 3.平均布局



## 层叠上下文？

1. 一个多方参与构建的、遵循一定规则的、独立的环境；

2. 子项可能创建新的上下文，与外层上下文有同样的规则，且与外层上下文隔绝
   上下文形成条件：
   1.根节点HTML 自带上下文
   2.z-index不为auto的positon=absoluted &&position=relative
   3.position=fixed&&position=sticky
   4.z-index!=auto的flex item
      z-index!=auto的grid item
   5.opacity<1

   - opcacity VS background:rgbd(0 0 0  0.5)
   - 一个所有都透明 一个只有背景色透明

   6.transform!=none
   层叠顺序
   1.未设置z-index
   position元素按HTML出现顺序>未定位的块级元素按HTML出现顺序>root
   2.带float
   后代中的定位按HTML>float>未定位后代块级元素按HTML>root

   

   ## BFC

   block formatting context 块级格式化上下文

   块级元素参与构建、遵循一定规则的独立环境

   1. 形成BFC

      根元素

      float！=none

      positon=absolute、fixed、sticky

      display=inline-block、table-cell

      display=flow-root/flow-root/list-item

      overflow=hidden、scroll、auto

      - 推荐使用display=flow-root

   2. BFC使用场景

      阻止父子外边距合并

      阻止块级元素与浮动元素的覆盖

      清楚浮动

   

## 渲染机制

**All:dom+cssom=renderObject->layout->renderLayer->>rendering!!(还能选择渲染方式)**

```
关键渲染路径：
1.html生成dom tree
2.当生成dom时候遇上link，开始请求css.style,css生成cssom tree
3.dom+cssom合成渲染树
4.根据渲染树进行布局
5.开始渲染
```
1.DOM tree
`bytes->character->token->node->dom tree`
- html字节码（例如按照UTF-8进行编码）->字符化->tokenizing(W3C标准的TOKEN)->lexing(token转化为定义其属性和规则的object)->dom（创建树装数据结构，包含父子关系）

2.CSSOM tree
`bytes->character->token->node->cssom tree`
- 构建dom tree时候遇上link 引用style.css ，立刻向该资源发送请求
- 同上构建cssom tree
- csson tree 确定节点对象的计算样式

3.renderObject tree

`DOM tree与CSSOM tree合成render tree`
- render object tree保存了dom上的可见节点

4.根据创建的render object tree进行布局
- 布局是个递归过程
- 从根节点（root）开始布局

5.生成renderLayer tree
_renderLayer类似于图层_
- 浏览器不直接使用renderObject进行绘制
- 浏览器会为一些特殊的renderObject生成对应的renderLayer,并构建renderLayer tree
- renderObject没有直接对应的renderLayer就从属其父节点的

6.renderLayer Tree决定网页绘制的层次顺序，从属renderlayer的RenderObject决定绘制内容

[参考掘金](https://juejin.im/post/5aec8f5a518825671c0e6ed9#heading-5
)

## 白屏原因

白屏：一般指页面空白，突然出现完整有样式的内容
可能的原因：
1.css阻塞渲染

- CSS是阻塞渲染的资源，在CSSOM完全解析完成之前，浏览器不可能开始屏幕的绘画。
  2.js阻塞渲染也会出现白屏
- js还会阻塞html解析生成dom
  当构建dom tree时候如果碰到js ,将会去立刻执行js代码，js可以操作dom和cssom，dom构建阻塞，不能渲染
- 当js操作cssom时候css未构建完成，将会形成阻塞

优化：
1.将css放在head里，将js放在body尾部
2.减少关键资源的大小 14kb是tcp协议可一次发送的资源
3.控制页面首次渲染需要的关键资源数量
4.减少关键渲染路径的往返次数

## CSS动画的两种做法

   mdn自查-练习
   1. 跳动的心
   2. 一键三连

