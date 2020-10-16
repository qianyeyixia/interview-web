#### 介绍下标准的css的盒子模型? 低版本IE盒子模型有什么不同的

标准盒子模型: 宽度= 内容宽度(content) + border + padding + marign

低版本IE盒子模型: 宽度= 内容宽度(content+border+padding) + margin


####  box-sizing属性?
用来控制元素的盒子模型解析模式，默认为content-box
content-box：w3c标准的盒子模型,设置元素的height/weight 属性指的是content部分的宽高
border-box IE传统盒子模型，设置元素的height/weight指的是border+padding+content部分的宽度


####  css选择器有哪些? 那些属性可以继承?
css 选择器: ID选择器(#my), 类选择器(.my),标签选择器(div,h1,p) ,相邻选择器(h1 + p) ,子选择器(ul > li),后代选择器(li a),通配符选择器(*), 属性选择器(a[rel="val"]),伪类选择器(a:hover,li:nth-child)

可继承的属性：font-size,font-family,color

不可继承的属性: border,padding,margin,width,height

优先级(就近原则) ： !important > id > class > tag
!important 比内联游戏那几更高

####  css优先级算法如何计算?
元素选择符: 1
class选择符：10
id选择符：100
元素标签:1000

!important生命的优先级最高,如果冲突在进行计算
优先级相同，则选择最后出现的样式
集成的得到的样式优先级最低

#### 5. css3新增的伪类有哪些?
p:first-of-type 选择属于其父元素的首个元素
p:last-of-type 选择属于其父元素的最后元素
p:only-oftype 选择属于父元素唯一的元素
p:nth-child(2) 选择其父元素的第二个元素
:enabled :disabled 表单控件的禁用状态
:checked 单选框或复选框被选中

####  如何居中div? 如何居中浮动元素? 如何让绝对定位的div居中?
``` css
div {
  border:1px solid red;
  margin:10px auto;
  height:50px;
  width:80px
}
/* 浮动元素的上下左右居中 */
div {
  border:1px solid red;
  float:left;
  position:absolute;
  width:200px;
  height:100px;
  left:50%;
  top:50;
  margin:-50px 0 0 -100px;
}
/* 绝对定位的左右居中 */

div {
  border:1px solid black;
  position:absolute;
  width:200px;
  height:100px;
  margin:0 auto;
  left:0;
  right:0 ;
}



```




#### display有哪些值并说明他们作用? 
inline --内联
none -- 隐藏
block --块显示
table --表格显示
list-item--项目列表
inline-block 行内块


####  position的值并说明他们的作用?
static(默认) 按照正常文档流进行排列
relative(相对定位) 不脱离文档流,参考自身静态位置通过top,bottom,left,right 定位
absolute(绝对定位) 参考聚其最近一个部位static的父元素通过top，bottom，left,right
fixed(固定定位): 所固定的参照对象为可视窗口


#### css有哪些新特性?

1.RGBA和透明度
2.background-image,background-origin(content-box/padding-box/border-box),background-size,background-repeat
3.word-wrap(对长的不可分割单词换行) word-wrap:break-word
4.文字阴影：text-shadow: 5px 5px 5px #ff000 (水平阴影模糊距离，阴影颜色)
5.font-face:定义自己的字体
6.圆角(边框半径) border-radius 属性用于创建圆角
7.边框图片 border-image:url(border.png)
8.盒阴影 box-shadow：10px 10px 5px #888888
9.媒体查询：定义两套css，当浏览器尺寸变化时采用不同的属性


#### 请解释一下css3的flexbox(弹性盒子布局),以及使用场景?
该布局模型的目的是提供一个更加搞笑的方式来对容器中的条目进行布局，对齐和分配空间。在传统的布局方式中，block布局是把块在垂直方向从上到下依次排列的;而inline布局是在水平方向来排列。
弹性盒子布局并没有这样内在的方向限制，可以由开发人员自由操作
使用场景：弹性盒子布局适合于移动端开发，在Android和ios上完美支持



#### 用纯 css创建一个三角形的原理是什么?
首先把元素的跨度和高度设置为0.然后设置边框样式

``` css
span {
  width:0;
  height:0;
  border-top:40px solid transparent;
  border-left:40px solid transparent;
  border-right:40px solid transparent;
  border-bottom:40px solid #FF0000
}

```
#### 满屏品字布局如何设计
第一种真正的品字
  1.三块的高度是确定的
  2.上面那块用margin:0 auto;居中
  3.下面两块用float或者inline-block不换行
  4.用margin调整位置使他们居中
第二种全屏的品字布局
  上面的div设置为100%，下面的两个div分别宽50%,然后使用float或者inline-block使其不换行

#### 常见的兼容性问题?
1.不同浏览器的标签默认的margin和padding不一样
2.IE6双边距bug:块属性标签float后,又有横行的margin情况下，在ie6显示margin比设置的大
hack:display:inline将其转化为行内属性
3.渐进识别的方式,从总体中逐渐排除局部。首先，巧妙的使用“9”这一标记，将IE浏览器从所有情况中分离出来。接着，再次使用‘+’将ie7和ie8，ie6分离开，这样ie8已经独立识别

``` css
div {
  background-color:#1ee18;/*所有识别*/
  .background-color:#00deff\9;/*ie 6,7,8*/
  +background-color:#a200ff;/*ie 6,7*/
  _background-color:#a200ff;/*ie 8*/
  
}
```
4.设置较小的高度标签，在IE6 ie7中高度超出自己设置高度。
hack:给出超出高度的标签设置overflow：hidden;或者设置行高line-height小于你设置的高度
5.iE下，可以使用获取常规属性的方法来获取自定义属性，也可以使用geAttribute()获取自定义属性
Firefox下，只能使用 getAttribute() 获取自定义属性。解决方法 统一通过getAttribute()获取自定义属性
6. Chrome中文界面下默认会将小于12px的文本强制按照12px 显示，可通过css属性 -webkit-text-size-adjust:none;解决
7.超链接访问过后hover样式就不出现了，呗点击访问过得超链接样式不再具有hover和active。解决方法是改变css属性的排版顺序：l-v-h-a(love hate) a:link{} a:visited{} a:hover{} a:active{}


#### 为什么要初始化css样式
因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没有对css初始化往往会出现浏览器之间的页面显示差异
#### absolute的containning bloclk计算方式跟正常流有什么不同?
无论属于哪种，都首先要找到其祖先元素中最近position值不为static的元素，然后在判断
  1.若此元素位inline元素，则 containing block 位能够包含这个元素生成的第一个和最后一个inline box的padding box(除margin,border外的区域)的最小矩形
  2.否则，则由这个祖先元素的padding box构成

如果都找不到，则为 initial containing block

补充：
  1.static(默认的)/relative :简单说就是他的父元素的内容框(即去掉padding的部分)
  2.absolute：向上找最近的定位为absolute/relative的元素
  3.fixed 他的containing block 一律为根元素(html/body)
#### CSS里面的visibility属性有个collapse属性？在不同浏览器下以后什么区别?
当一个元素的visibility属性被设置成 collapse值后，对于一般的元素，他的表现跟hidden是一样的
  1.在Chrome中，使用collapse值和使用hidden没区别
  2.Firefox,opera与IE,使用collapse值和使用 display：none没什么区别

#### display:none 和 visibility:hidden的区别?
display:none 不显示对应元素，在文档布局中不再分配空间(回流+重绘)
visibility:hidden 隐藏对应的元素.在文档布局中仍保留原来的空间(重绘)


#### position跟 display overflow float这些特性相互叠加后会怎么样?
display属性规定元素应该生成的框的类型
position属性规定元素的定位类型
float属性是一种布局方式，定义元素在那个方向浮动
类似于优先级的机制 position：absolute/fixed优先级最高,他们在世，float不起作用，display值需要调整。float或者absolute定位的元素，只能是块元素或者表格

#### 对BFC规范(跨级格式化上下文：block formatting conttext) 的理解
BFC规定了内部的Block Box如何布局
定位方案:
  1.内部的Box 会在垂直方向上一个接一个放置
  2.Box垂直方向的距离有margin决定，属于同一个BFC的两个相邻BOX得margin会发生重叠
  3.每个元素的margin box的左边，与包含border box的左边相接触
  4.BFC的区域不会与float box重叠
  5.BFC是页面上的一个隔离的容器，容器里面的子元素不会影响到外面的元素
  6.计算BFC的高度时，浮动元素也会参与计算
满足下列条件之一就可触发BFC
  1.根元素，即html
  2.float的值不为none (默认)
  3.overflow的值不为visible(默认)
  4.display的值为inline-block。table-cell,table-caption
  5.position的值为absolute或fixed


#### 为什么会出现浮动和什么时候需要清除浮动? 清除浮动的方式?
浮动元素碰到包含他的边框或者浮动元素的边框停留。由于浮动元素不在文档流中，所以文档的块框表现得就像浮动框不存在一样。浮动元素会漂浮在文档流的块框上。
浮动带来的问题：
  1.父元素的高度无法被撑开，影响与父元素同级的元素
  2.与浮动元素同级的非浮动元素(内联元素)会跟随其后
  3.若非第一个元素浮动，则该元素之前的元素也需要浮动，否则会影响页面显示的结构
清楚浮动的方式
  1.父元素div定义height
  2.最后一个浮动元素后加空div标签并添加样式clear：both
  3.包含浮动元素的父标签添加样式overflow为hidden或auto
  4.父级div定义zoom

#### 上下margin重合的问题?
在重合元素外包裹一层容器，并触发该容器生成一个BFC
``` html
  <div class="aside"></div>
  <div class="text">
    <div class="main"></div>
  </div>
  <style>
  .aside {
    margin-bottom:100px;
    width:100px;
    height:150px;
    background:#f66;
  }
  .main {
    margin-top:100px;
    height:200px;
    background:#fcc;
  }
  .text {
    /* 盒子main外面包一个div,通过改变此div的属性是连个盒子分属于两个不用的BFC */
    overflow:hidden;// 此时已经触发了BFC属性
  }
  </style>


```

#### 设置元素浮动后,该元素的display值是多少?
自动变成display:block

#### 移动端的布局用过媒体查询吗?
通过媒体查询可以为不同的大小和尺寸的媒体定义不同的css，适应形影的设备的显示
1.<head>里边
<link rel="stylesheet" type="text/css" href="xxx.css" media="only screen and (max-device-width:480px;)">
2.css: @media only screen and (max-device-width:480px;){css样式}


#### 使用 css预处理器
less,sass,stylus
#### css优化,提升性能的方法有哪些?
1.避免过度约束
2.避免链式选择符
3.避免后代选择符
4.使用紧凑的语法
5.避免不必要的命名空间
6.避免不必要的重复
7.最好使用表示语义的名字。一个好的类名应该是描述他是什么而不是想什么
8.避免！important ,可以选择其他选择器
9.尽可能的精简规则，你可以合并不同类里的重复规则

#### 浏览器是怎么解析css选择器的?
css选择器的解析是从右向左解析的。所从左向右的匹配，发现不匹配的规则，需要进行回溯，会损失很多性能。若从右向左匹配，先找到所有最右的节点，对于每一个节点，向上寻找其父节点知道找到根元素或满足条件的匹配规则，则结束这个分支的遍历。两种匹配规则的性能差别很大，而从左向右的匹配规则的性能都浪费在了失败的查找上面。
而css解析节奏后，需要解析的结果与DOM Tree的内容一起进行分析简历一颗Render Tree 最终用来进行绘图。在建立Render Tree时（webkit中的 [Attachment]过程），浏览器就要为每个DOM Tree 种的元素根据css解析结果(style Rules) 来确定生成怎样的Render Tree

#### 在网页中应该使用奇数还是偶数字体?请说明原因
使用偶数字体。偶数字体相对更容易和web设计的其他部分构成比例关系。Windows自带的点阵宋体（中易宋体）从Vista开始只提供12.14.16px这三个大小的点阵，而13.15.17px时用的是小号的点（即每个字占的空间大了1px,但点阵没变）,于是略显稀疏

#### margin和padding的使用·分别是和什么场景使用?
何时使用margin:
  1.需要在border 外侧添加空白
  2.空白处不需要背景色
  3.上下相连的两个盒子之间的空白，需要相互抵消时。

何时使用padding：
  1.需要在border内侧添加空包
  2.空白处需要背景颜色
  3.上下相连的两个盒子的空白，希望为两者之和

兼容性问题： 在IE5.IE6中，为float的盒子制定margin时，左侧的margin可能会变成两倍的宽度。通过改变padding或者制定盒子的display为inline是解决

#### 元素竖向的百分比设定是相对于容易高度么？
当按百分比设定一个元素的宽度时，他是相对父容器的宽度计算的，但是，对于一些表示竖向距离的属性，例如 padding-top，margin-bottom，padidng-bottom,margin-top等。当按百分比设定他们时，依据的父容器的宽度，而不是高度

#### 全屏滚动的原理是什么? 用到了css的哪些属性?
1.原理：类似于轮播，整体的要还俗一直排列下去，假设有5个需要展示的全屏页面，那么高度是500%，只是展示100%，剩下的可以通过transform进行Y轴定位，也可以通过margin-top实现
2.overflow:hidden; transition：all 1000ms ease;

#### 什么是响应设计? 相应设计的基本原理是什么? 如何兼容低版本IE?
响应式网站设计（Reponse web design）是一个网站能够兼容多个终端，而不是每一个终端做一个特定的版本。
基本原理使用过媒体查询检测不同的设备屏幕尺寸做处理
页面头部必须有meta声明的viewport
``` html
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
```

#### 视觉滚动差效果?
视觉滚动(Parallax Scrolling)通过乡下滚动的时候，控制北京的移动速度比前景的移动速度慢来创建出令人惊叹的3D效果
1.css实现
  优点：开发时间短，性能和开发效率比较好，确定是不能兼容到低版本的浏览器
2.JQuery 实现
  通过控制不同滚动速度，计算每一层的时间，控制滚动效果。
  优点：能兼容到各个版本的，效果可控性好
  缺点：开发起来对制作者要求高
3.插件实现方式
  例如：parallax-scrolling，兼容性十分好

#### ::befor 和 :after中双冒号和单冒号有什么区别? 解释一下这2个伪元素的作用
1.单冒号用于css伪类， 双冒号用于css3伪元素
2.：：before和：after这两个伪元素，是在css2.1里新出现的。期初，伪元素的前缀的使用用的单冒号语法，但随着web的进化，在css3的规范里，伪元素的语法呗修改成使用双冒号，成为：：before ：：after
#### 你对line-height是如何理解的?
行高是指一行文字的高度，具体说是两行文字间的极限的距离。css中其高度作用是height和line-hegiht，没有定义height属性，最终其表现作用一定是line-height。
单行文本垂直居中：把line-height值设置为height一样大小的值可以实现单行文字的垂直巨宗，其实可以吧height删除
多行文本垂直居中：需要设置display 属性为inline-block

#### 如何让Chrome支持小于12px的文字?
``` css
p {
  font-size:10px;
  -webkit-transform:scale(0.8) //缩放比例
}
```

#### 让页面里的字体变清晰,变细用css怎么做?
-webkit-font-smoothing在window系统下没有起作用，
但是在ios设备上起作用-webkit-font-smoothing:antialiased是最佳的，灰度平滑


#### position:fixed 在Android下无效怎么处理?
``` html
<meat name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no" />

```
#### 如果需要收东西额动画,你认为最小时间间隔是多久，为什么?
多数显示器默认频率60Hz,即1秒刷新60次，理论上最小间隔为1/60*1000ms = 16.7ms

#### li与li之间又看不见的空包是什么原因引起的?怎么解决？
行框的排列会受到中间空包（回车空格）等的影响，因为空格也属于字符，这些空白也会被应用躺尸，占据空间，所以会有间隔，吧字符大小设为0，就没有空格了。
解决方法：
  1.可以将li代码全写在一排
  2.浮动li中float：left
  3.在ul中font-size：0；可以使用letter-space ：-3px
#### display:inline-block什么时候回显示间隙?
1.有空格时候会有间隙 解决：移除空格
2.margin正值的时候 解决：margin使用负值
3.使用font-size时候 解决：font-size：0； letter-spacing，word-spacing

#### 有一个高度自适应的div,里面的div,一个高度100px,希望另一个填满剩下的高度
外层div使用position:relative;高度要求自适应div使用position：absolute：top：100px;bottom:0;left:0;
#### png,jpg,gif这些图片的格式解释一下，分别什么时候用.有没有了解过webp?
1.png是便携式网络图片(portable netword graphics)是一种无损数据塔索位图文格式。
  优点是压缩比高，色彩好。大多数地方都可以用
2.jpg是一种针对相片使用的一种失真压缩方法，是一种破坏性的压缩，在色调及颜色平滑变化做的不错。在www上，呗用来储存和传输照片的格式
3.gif是一种位图文格式，以8位色重现真色彩的图像，可以实现动画效果
4.webp格式是谷歌在2010年推出的图片格式，压缩只有jpg的2/3，大小比png小了45%。
  缺点是压缩的时间更久了，兼容性不好，目前谷歌和Opera支持

#### style标签写在body前与写在body后有什么区别?
页面加载自上而下 当然是先加载样式
写在body标签后由于浏览器以逐行方式对html文档进行解析，当解析到写在尾部的样式表会当值浏览器停止之前的渲染，等待加载且解析样式表完成之后重新渲染，在window是的IE肯能会出现页面闪烁问题
#### css属性overflow属性定义溢出元素会如何处理?
参数是scroll , 必会出现滚动条
参数是auto是. 子元素内容大于父元素时出现滚动条
参数是visible, 溢出的内容出现父元素之外
参数是hidden 溢出隐藏

### 描述一下 css sprites(简称雪碧图)
就是将页面所用到的图片全都放到一张大图中,然后利用css的background-image,background-repeat，background-position 的组合进行背景定位。利用css sprites能减少网页的http请求,从而提高页面的性能。css sprites能减少图片的字符


