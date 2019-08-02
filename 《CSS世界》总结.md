# 《CSS世界》总结 #



## CSS世界大局观 ##

​		张老师在书中使用了一个很有意思的比喻，就是将CSS世界比作了魔法王国。

> 在CSS世界中，HTML是魔法石，选择器就是选择法器，CSS属性就是魔法师，CSS各种属性值就是魔法师的魔法技能，浏览器就是他们所在的“王国”，“王国”会不断更新法律法规（版本升级），决定是否允许使用新的魔法石（HTML5新标签新属性），是否允许新的魔法师入“国籍”（CSS3新属性），或者允许魔法师使用某些新技能（CSS新的属性值），以及是否舍弃某些魔法技能（如display:run-in）；操作系统就是他们所在的世界，不同的操作系统代表不同的平行世界，所以，CSS世界有这么几个比较大的平行世界，即Windows世界、OS X世界以及移动端的iOS世界和Android世界。不同世界的浏览器王国的命运不一样，例如，在OS X世界中，IE王国是不存在的，而Safari王国却异常强大，但在Windows世界中，Safari王国却异常落寞。

​		这样描述让我我们很容易就理解了CSS与浏览器以及操作系统的关系，生动形象。



## 流 ##

​		对于这部分内容，张老师在书中提到了很多，并认为“流”是CSS能够压制SVG的最大武器。

![1564707801993](C:\Users\Temton\AppData\Roaming\Typora\typora-user-images\1564707801993.png)

​		![1564707791024](C:\Users\Temton\AppData\Roaming\Typora\typora-user-images\1564707791024.png)

​		张老师的这两张图实在是很生动形象了，流在不同尺寸的容器中，合理的处理图文信息的这种不确定性，其实就是流动特点，图片可大可小，文字可多可少、字体多变，再辅以尺寸多变，这种不确定性只能通过“流”来解决。

​		并利用“流”的特性，人们创造了流式布局。利用元素“流”的特性实现的各类布局效果。因为“流”本身具有自适应特性，所以“流体布局”往往都是具有自适应性的。但是，“流体布局”并不等同于“自适应布局”。“自适应布局”是对凡是具有自适应特性的一类布局的统称，“流体布局”要狭窄得多。例如，表格布局也可以设置为100%自适应，但表格和“流”不是一路的，并不属于“流体布局”。



## 专业术语 ##

【eg】

```
.vacabulary{
height:99px;color:transparent
}
```

- 属性：css的中文称谓`height`
- 值:大多和数字有关，又有字符串值和位置值等类型。（css3还有别的）`99px` `#999`
- 属性值:冒号后面所有的内容。属性值=值+关键字+功能符 `1px solid rgba(0,0,0,0.5)`
- 变量：css2少见。`currentColor`【css3】

```
.icon {
display: inline-block;
width: 16px; height: 20px;
background-image: url(../201307/sprite_icons.png);
background-color: currentColor; /* 该颜色控制图标的颜色 */
}
```

- 关键字：特指英文单词 `transparent`
- 长度单位:px，em（其他还有时间单位和角度单位）

> %不是长度单位 【eg】2%是一个完整的值 .这样一个特例，应该被叫做百分比值（见第五章5.2.3） 【公式】（数字）+长度单位= （值）
>
> 长度单位=绝对长度单位（px,pt等）+相对长度单位（相对字体长度单位(em，rem)+相对视区长度单位（vh,vw））

- 功能符：值以函数的形式指定（被括号括起来的那种）`rgba(0,0,0,0.5)` `url('地址')`
- 声明:属性名+属性值 `color：transparent`
- 声明块：花括号括起来的声明 `{height:99px;color:transparent }`
- 选择器：瞄准目标元素的东西`.vacabulary `包括（类选择器，id选择器，属性选择器，伪类选择器，微元素选择器）
- 关系选择器：根据与其他元素的关系选择元素的选择器。包括（后代，相邻后代，兄弟，相邻兄弟）
- 规则和规则集:选择器+声明块

```
.vacabulary{
height:99px;color:transparent
}
```

- @规则：以@字符开始的一些规则 `@media`

> **未定义行为** ：规范没有对某种场景的具体描述（表现为浏览器之间的显示差异）。

​		在这些术语中，我最好奇的是@规则，因为之前在很多网页的CSS源代码中又看到这个东西，但是自己也没有去深入了解。



## 元素的尺寸 ##

### width

`width:auto`使用场景很多，表现形式也很多，书中提到以下几种情况：

- 充分利用可用空间，即流动性(fill-available)。例如`<div>`会自动铺满整个父容器。
- 收缩和包裹(fit-content)，例如浮动和绝对定位的“包裹性”，
- 收缩到最小(min-content)，例如表格中每个单元格的文字，会自动收缩
- 超出容器限制，例如其中的内联元素设置了`white-space: nowrap`

其中最常用的就是，让`<div>`铺满父容器时，不要故意设置`width:100%`，因为还可能会有 padding margin border 的宽度影响，让其自适应就好了。

针对盒子模型来说，`width`默认作用域`content-box`上，即内容区域。现在的普遍做法是增加`box-sizing: boxer-box`。不过作者的另外一种解决方案也非常体现“流”特性。

```
.father {
	width: 180px;
}
.son {
	margin: 0 20px;
	padding: 20px;
	border: 1px solid;
}
```

最后作者解释了`box-sizing`设计的初衷，让我读来眼界大开。因为我们专业于一门技术，不仅仅要知道 what 和 how ，还要知道 why 。书中提到，**box-sizing的设计初衷是为了解决替换替换元素宽度自适应问题**。所谓的“替换元素”可以简单的理解为各种表单元素，例如`input` `textarea` `video` `object` 还有 `img` ，这些元素的样式最难控制。

替换元素有一个特点，例如`textarea`，宽度不容易被控制，不具有流动性。即，`div`如果不设置宽度会撑满父容器，而`textarea`则不会。这种情况下，如果没有`box-sizing`的话，我们没法通过控制宽度来实现自适应。例如，如果针对`textarea`设置`width:100%`，是作用域`content-box`，再加上`padding``border`宽度，就超出父元素了。

### height

> CSS 的默认“流”是水平方向的，宽度是稀缺的，高度是无限的

有时候设置`height:100%`无效，**如果父元素是height:auto，只要子元素在文档流中（不是float或者absolute），百分比值会被忽略** ，记住这条原则。要想解决这个问题，就得**让父元素必须有一个可以生效的高度值**，例如：

```
html,body {
  height: 100%;
}
div {
	position: absolute;
	height: 100%;
}
```

当然，直接对`div`设置绝对定位，也可以让`height:100%`生效。不过注意，**绝对定位的宽高百分比计算是相对于padding-box的，而正常情况下的计算则是相对于content-box的**。



### 外部尺寸与流体特性 ###

**外部尺寸和内部尺寸：** 外部尺寸（extrinsic sizing）的尺寸由外部决定。内部尺寸（intrinsic sizing）的尺寸由内部元素决定。（所以上面4种表现，1是外部尺寸（跟着父元素走），剩下的是内部尺寸（跟着自己走））

> - **正常流宽度的情况下，块元素不要设置宽度。**（会失去流动性，无法像水流那样完全利用容器的空间，正确的处理办法是使用盒模型，来自动分配空间）
> - **格式化宽度仅出现在绝对定位模型中。**`position:absolute fixed` 一般来说，**绝对定位元素的宽度是由内部尺寸决定的。**在特例（非替换元素）的情况下，宽度是由外部尺寸决定的。（宽度由最近的，position非static的祖先元素决定）



### 内部尺寸与流体特性 ###

> **内部尺寸和流体特性。** 如何判断这个元素使用的是内部尺寸：**假如这个元素里面没有内容，宽度就是0。** 特性：
>
> - **包裹性**：包裹性=包裹+自适应性（即元素尺寸由内部元素决定，但永远小于包含块的容器的尺寸） 【eg】`display:inline-block` 内容再多，只要正常情况，宽度不会超过容器

> - **首选最小宽度**：元素最适合的最小宽度（中文为单个汉字，英文为单词，替换元素（如img） 为元素内容本身宽度）
> - **最大宽度**：元素可以有的最大宽度。实际等同于包裹性元素设置`white-space：nowrap`申明后的宽度。



### 内联元素

> 块级原则负责结构，内联元素负责内容

**特征：可以和文字一行显示。**

内联元素不仅仅是`display: inline`，`inline-block` `inline-table`也算是内联元素，其表现就是可以和文字在一行显示。

书中提到了“内联盒子模型”，可以对比一下普通的盒子模型。不过这个模型日常使用中基本不会关心到，因此简单列一下，详细内容去看书。

- 内容区域：本质是一个字符盒子（character box）。对于非文字类的替换元素，内容区域为元素本身。
- 内联盒子：让内容排成一行。其实这里的内联盒子是指元素的外在盒子。，用来决定元素是内联还是块级。子类有内联盒子和匿名内联盒子
- 行框盒子：每一行就是一个行框盒子
- 包含盒子：行框盒子+两头标签

最后书中提出了一个非常非常非常重要的概念 —— **幽灵空白节点**（作者起的名字）

在HTML5文档声明中，内联元素的所有解析和渲染表现就如同每个**行框盒子**的前面有一个“**空白节点**”。这个空白节点永远透明，不占宽度，无法获取，但确实存在，表现如文本节点一样。

这是日常开发中实时遇到但却实时被大家忽略的一个问题。该问题触发有一个前提，就是必须是 HTML5 文档声明。

```
<!doctype html>
<html>
```

如下例子，这个`div`的高度并不是 0 ，而是 18px 。命名里面什么内容都没有，为何有高度呢？

```
<div><span></span></div>
```

其实可以这么理解，**在<span>前面有一个宽度为 0 的空白字符（即幽灵空白节点）**，它撑起了整个内联元素的高度，也就撑起了`<div>`的高度。

这个空白节点的影响，会出现于没有文字的内联元素场景中，而且基本是以“坑”的形式来出现的。例如，下面代码执行后，`img`和`div`的下边界会有一个空白区域，这是为何？

```
<div>
	<img src="xxx.png"/>
</div>
```



## 盒模型

盒模型是 CSS 的基础知识，它包含四个盒子：content-box, padding-box, border-box, margin-box ，书中也是按照这个顺序来写的，下面针对一些印象比较深的内容做记录。

### content

**替换元素，通过修改某个属性值呈现的内容，就能被替换的元素，叫替换元素**。常见的有`<img>` `<object>` `<video>``<iframe>` `<textarea>` `<input>` `<select>`。非替换元素：(X)HTML 的大多数元素是不可替换元素，**他们将内容直接告诉浏览器，将其显示出来**。 比如`<p>p的内容</p>`、`<label>label的内容</label>`； 从观点上来看，与非替换元素，**最大的区别在于src属性和content属性**。替换元素的特点有：

- 1).内容的外观不受页面上CSS的影响
-  2).有自己的尺寸（部分替换元素在没有明确尺寸设定的情况下，其默认的尺寸是300×150，比如video,iframe,canvas等） 
- 3).在很多CSS属性上有自己的一套表现规则 vertical-align属性值在替换元素和非替换元素之间的解释是不一样的，非替换元素默认的baseline定义为字符x的下边缘。而替换元素则被硬生生定义为元素的下边缘 

​		尺寸计算规则：

- 固有尺寸：替换内容原本的尺寸（默认尺寸）。css2无法改变替换元素内容的固有尺寸（css3部分可以例如`object-fit`,`background-size`）

```
<canvas id="" width="" height="" style="background: blue;"></canvas>
```

- html尺寸: 只能通过 HTML 原生属性改变，包括`<img>`的width和height属性、`<input>`的size属性，`<textarea>`的cols和rows属性等

```
<canvas id="" width="400" height="300" style="background: red;"></canvas>
```

- css尺寸:可以通过 CSS 的width和height或者max-width/min-width和max-height/min-height设置的尺寸，对应盒尺寸中的content box。

```
.canvasSize{width: 500px;height: 100px;background: yellow;}
<canvas id="" width="" height="" class="canvasSize"></canvas>
```

![](C:\Users\Temton\Pictures\FireShot\tihuanSize.png)

> **在优先级上，css尺寸>html尺寸>固有尺寸。**

### padding

​		块状元素的 padding 比较简单。对于内联元素的 padding ，水平方向会影响布局，而**垂直方向可增加其可视区域却不会影响布局**。这也是好多开发者以为内联元素的垂直 padding 不起作用的原因。此处书中提到了两个例子，都是在不改变布局的情况下，第一是增加链接的可点击区域，第二是对锚点标题设置边距，都很实用。

padding 不支持负值，但是支持百分比。注意，**无论是水平方向还是垂直方向的百分比，都是根据元素的宽度计算的**。

##### 其他细节：

- 有序列表和无序列表的`padding-left`单位是px。
- 很多表单元素（`input`,` textarea`,` button`）都内置`padding`；
- 所有浏览器的单选和复选框无内置padding；
- button的padding最难控制
- 在图像上面的用途，可以绘制打开菜单的三道杠和双层圆点。

### margin

如果该元素是流式填满父容器的元素，则 margin 设置负值可以改变其可视区域，但不影响布局。例如书中 84 页的示例，一行有三个卡片，最后一个和父容器没有间隙，比较常用。

margin 设置百分比值，和 padding 一样，无论是水平还是垂直方向，都是相对于元素宽度做计算的。

**垂直方向的 margin 合并**是开发中常见的“坑”，下面列出三种常见的场景并给出示例：

第一种情况，相邻兄弟元素的 margin 合并，这是最常见的，示例如下。这个问题并不会造成什么困扰，因此不用规避。

```
<style>
	p {margin: 1em 0}
</style>
<p>第一行</p>
<p>第二行</p>
```

第二种情况，父元素和第一个/最后一个子元素，就是经常被问到的`margin-top`失效的问题。示例如下：

```
<div>
	<div style="margin-top:80px">内容</div>
</div>
```

该示例会触发的问题是，子元素的`margin-top`会作用域父元素上，和我们书写的预期完全不一致。解决这个问题，有以下途径：

- 让父元素 BFC
- 给父元素设置`border-top`
- 给父元素设置`padding-top`
- 父元素和子元素之前添加一个内联元素作为分离

第三种情况，空块级元素的 margin 合并。如下例子。

```
<style>
	.father {
		overflow: hidden;
	}
	.son {
		margin: 1em 0;
	}
</style>
<div class="father">
	<div class="son"></div>
</div>
```

该示例中，子元素的`margin-top`和`margin-bottom`会合并在一起，导致子元素的高度只有`1em` —— 前提是子元素是空的，没有任何内容。

其中这种场景，通过下面的例子解释就很清楚了。下面的示例中，`AAA`和`BBB`之间的距离就应该是`10px`，而不是离着很远。

```
<style>
	p {
		margin: 10px 0;
	}
</style>
<p>AAA</p>
<p></p>
<p></p>
<p></p>
<p>BBB</p>
```

margin合并的计算规则是：

1. 正正取大
2. 正负相加
3. 负负最负

再看看`margin: auto`带来的流动性。**margin:auto是为了填充闲置的尺寸而设计的**，规则是：

- 如果一侧定值，一侧 auto ，则 auto 为剩余空间大小
- 如果两侧都是 auto ，则评分剩余空间

例如靠左对齐

```
.son {
	width: 200px;
	margin-right: auto
}
```

例如水平居中对齐

```
.son {
	width: 200px;
	margin: 0 auto;
}
```

例如水平垂直居中对齐

```
.son {
	posotion: absolute;
	top: 0; right: 0; bottom: 0; left: 0;
	width: 200px; height: 100px;
	margin: auto; /**将上下左右的空白区域都均分并自动填充**/
}
```

注：触发`margin：auto`计算有一个前提，width和height不能是auto

##### margin无效的原因

- display计算值inline的非替换元素的垂直margin是无效的。 对于内联替换元素，垂直margin有效，并没有margin合并问题。所以图片永远不会发生margin合并。
- 表格中的`tr`和`td`元素，或者设置`display:table-cell,display:table-row`元素的margin是无效的。设置`display:table-caption,display:inline-table`元素的ok
- margin合并的时候更改margin值是没有效果的。
- 绝对定位元素，非定位方向的margin值无效。

```
img{top:30%,margin-right:10px} //margin-right写了，right没写，无效
```

- 定高容器的子元素的margin-bottom或者，宽度定死的子元素的margin-right定位失效。
- 鞭长莫及，导致margin无效。（需要理解float和overflow ，第六章）
- 内联特性导致margin无效。

### border

良好的兼容性与稳定的特性表现

`border-width`不支持百分比的两个原因：

- 如果内容变大，边框也按比例变大，不符合语义化；
- 容易造成没对齐的假象

**重置：**`border:0`或者`border:none`



## 内联元素

内联元素有两个知识点 —— `line-height`和`vertical-align`

### 基线

​		line-height 是两个基线之间的距离，vertical-aligin 的默认值就是基线 (baseline )，基线到底是什么？**基线，就是一行文字中字母x的下边缘**。

![](C:\Users\Temton\Pictures\FireShot\68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f7468756d622f332f33392f5479706f6772617068795f4c696e655f5465726d732e7376672f34313070782d5479706f6772617068795f4c6.png)

### 内联元素的基石line-height

​		**内联元素的高度是由 line-height 决定的，并不是 font-size** 。而且，对于非替换元素的内联元素，其高度完全由 line-height 决定，跟 fontsize border padding 都没有关系。但是，**line-height 却无法决定替换元素的高度**，例如一行文字中有图片，图片的高度时不受这一行的 line-height 影响的。

> **行距**:列和列之间，明显的间隙叫做行距。 **半行距**:在css中，行距分散在当前文字的上方和下方，即使是第一行文字也是如此分布。 因为这个间隙的高度仅占完整行距高度的一半，因此被称为半行距。 【注意】区别行距和行高

三者的关系：

> 半行距*2=行距=`line-height`(行高)-`font-size`(字号) 所以说行距是可以为**负值**的，效果就是两行文字叠在一起。

​		line-height 可以让单行或者多行文字**近似**的垂直居中。因为 vertical-align 默认是基线对齐，而基线对齐并不一定就是垂直居中对齐。想要实现绝对的垂直居中，还需要 vertical-align 帮忙。



### vertical-align

`vertical-align`属性值分为4类：

1. 线类： `baseline`,`top`,`middle`,`bottom`
2. 文本类： `text-top`,`text-bottom`
3. 上下标类： `sub`,`super`
4. 数值百分比类： 如`20px`,`2em`,`20%`

`vertical-align`作用的前提： 只能应用于内联元素以及`display`值为`table-cell`的元素

`vertical-align`的好处

- 兼容好。（不用写hack）
- 可以控制内联元素的垂直对齐位置。 【注意】 `vertical-align:middle`并非真正意义的垂直居中，理由如上。如果需要精确对齐，用数值。



## 流的破坏和保护

本章讲解的元素没有流动特性，而是对流动特性的破坏，但是这也和“流”有关。主要与`floot` BFC `absolute`相关。

### float

首先，float 是一个很古老的样式属性，**它设计的初衷就是实现简单的图文混排（像报纸一样）**，并没有考虑其他的使用场景。而现在 float 被大家大量的用来做布局使用，做不是它设计初衷的事情，纯浮动布局容错性差，容易出现比较严重的布局问题，也**失去了流动性**。因此，**float 是魔鬼，尽量不要触发它，能躲则躲**。CSS3 慢慢普及之后，我们可以使用 flex grid 来做布局，不要再用 float 了。

元素设置了 float 会有以下几个特性：

- 包裹性。本来元素是自动撑满整个父容器的，设置了 float 之后就会收缩，紧紧包裹住内容。
- 块状化并格式化上下文（除了display为inline-table的元素float后display会变为table，其他都是block）
- 破坏文档流，使父元素塌陷
- 没有任何 margin 合并。都跳出文档流了，肯定也不符合流式布局的特点了。

##### 作用机制

> **块状化**：元素一旦float的属性值不为none，则其display计算值为block或table。 `text-align`对浮动元素无效（无法控制浮动元素的左右对齐）。

> **高度坍塌 ** ：为了实现文字环绕效果 ,float浮动属性让父元素高度坍塌。 【tip】[高度坍塌的代码演示](https://codepen.io/feiaaa/pen/xaPvgz)

> **行框盒子和浮动元素的不可重叠性**：行框盒子如果和浮动元素的垂直高度有重叠，那行框盒子在正常定位下，只会跟随浮动元素，而不会发生重叠。

> **行框盒子区域限制** ：块状盒子中的行框盒子被浮动元素限制，没有任何重叠。不改变布局方式，无法通过其他css来前边区域的大小。

**为了避免高度坍塌，我给这两需要浮动的元素设置高度？**

> 文字环绕效果是由**两个特性（父级高度坍塌和行框盒子区域限制）**共同作用的结果。 定高只能解决父级元素高度坍塌带来的影响，但是对行框盒子区域限制没有任何效果，结果导致的问题是浮动元素垂直区域 一旦超出高度范围，或下面元素margin-top负值上偏移，就很容易使后面的元素发生“环绕效果”。 

最后，和 float 分不开的还有 clear （float的天然克星）。

**clear属性**

`		clear`专门用来处理`float`属性带来的高度坍塌等问题。 **官方对clear 的解释：元素盒子的边不能和前面的浮动元素相邻。（即后面的元素管不到）** 所以清理浮动的时候，clear只能清理前面的，不能清理后面的。

​		clear属性有none,left,right,both both足矣，left和right没有使用的价值

- `none`：默认值，左右浮动
- `left`：左侧抗浮动
- `right`：右侧抗浮动
- `both`：两侧抗浮动

​		`clear`属性只有**块级元素**才有效，而`:after`等伪元素默认都是内联水平，这就是伪元素清除浮动影响时需要设置display属性值的原因。 `clear:both`的作用本质是**让自身不与float元素在一行显示**，并不是真正意义上的清除浮动。

1. 如果`clear:both;`元素前面的元素就是`float`元素，则`margin-top`负值即使设成`-9999px`，也没有效果。
2. `clear:both;`后面的元素依旧可能发生文字环绕的现象。



### BFC

BFC，block formatting context，块级格式化上下文。如果一个元素触发了 BFC ，那其内部元素无论设置什么样式变化，都不会对元素外部产生影响。BFC 元素不能出现 margin 重叠，也不可能收到 float 的影响。

​	能触发 BFC 的条件是：

- `<html>`根元素
- float 的值不是 none
- overflow: auto/scroll/hidden
- display: table-cell/table-caption/inline-block
- position: fixed/absolute

即，只要符合以上条件之一，都不需要使用`clear:both`来清除浮动，因为 BFC 元素不会收到浮动影响布局。、

BFC结界最重要的用途不是去margin重叠或者清除float影响，而是实现更健壮，更智能的自适应布局。 

基于BFC特性的自适应布局有如下优点：

- 自适应内容由于封闭更加健壮，容错性更强。内部设置clear:both;不会与float元素相互干扰而导致错位。

- 自适应内容自动填充浮动以外区域，无需关心浮动元素宽度，可以整站大规模应用。

基于BFC特性的自适应布局有如下缺点（导致有优势却没有大规模应用的原因）

- `float:left;`。浮动元素本身BFC化，然而浮动元素具有破坏性和包裹性，失去了元素本身的流体自适应性，因此无法用来实现自动填满容器的自适应布局。

- `position:absolute;`。脱离文档流，不容易操作。

- \```overflow:hidden;``块状元素的流体特性保存得很好，加上BFC的独立区域特性，而且从IE7开始就支持，兼容性很好。唯一的问题是容器盒子外的元素可能会被隐藏掉。

- `display:inline-block;`让元素尺寸包裹收缩， 不是我们想要的block流动特性

- `display:table-cell` 让元素表现的像单元格，ie8+支持。但会出现第三章一柱擎天的效果

- `display:table-row `无法自适应容器剩余空间

- `display:table-caption`没什么用

#### 最佳结界overflow

要彻底清除浮动的影响，最适合的属性是`overflow`，和BFC组合使用清除浮动。 `overflow:hidden;`声明不会影响元素原先的流体特性或宽度表现。 `overflow`的原本属性是指定块容器元素的内容溢出时是否需要裁剪。结界是衍生效果。 visible：默认值

### absolute

`position:absolute`的特性：包裹性，破坏性，块状化BFC，无依赖性，相对定位特性。 absolute是非常独立的css属性值。样式和行为表现不依赖其他任何css属性就能完成。

absolute和float写在一起，float没有任何效果，所以不要一起用

另外，absolute 和 fixed 在和`overflow:hidden`一起使用时，可能会遇到各种无法隐藏的问题，因此不要一起混用。**如果遇到 absolute 和 fixed 元素需要裁剪时，可使用clip语法，不会出问题**。

**包含块：containing block ** ：普通元素的百分比宽度是相对于父元素的content box宽度计算，而绝对定位元素的宽度是相对于第一个position不为static的祖先元素计算的。 	1. 根元素html被称为“初始包含块”，其尺寸等同于浏览器可视窗口的大小。 

2. 对于其他元素，如果该元素的position是relative或static，则“包含块”由其最近的块容器祖先盒子的content box边界组成。
3. 如果元素position:fixed;，则“包含块”是“初始包含块”。 
4. 如果元素position:absolute;，则“包含块”由最近的position不为static的祖先元素建立，具体方式如下： 如果该祖先元素是纯inline元素，则规则略复杂：

- 给内联元素的前后各生成一个宽度为0的内联盒子，则这两个内联盒子的padding box外面的包围盒子就是内联元素的“包含块”。
- 如果该内联元素被跨行分割，则包含块是未定义的。
- 否则，“包含块”由该祖先的padding box边界组成。

> 和常规元素相比，绝对定位元素的包含块有3个明显的差异： 
>
> 1. 内联元素也可以作为包含块所在的元素； 
> 2. 包含块所在的元素不是父级块元素，而是最近的position不为static的祖先元素或根元素； 
> 3. 边界是padding box而不是content box。



## CSS世界的层叠规则 ##

#### 元素的层叠顺序（stacking order）

(从最优先到最后)

1. （装饰）正z-index，位置在最下面，特指层叠上下文元素的边框和背景色
2. z-index:auto或看成z-index:0，层叠水平一样
3. （内容）inline水平盒子，指的是包括inline/inline-block/inline-table元素的层叠顺序，都是同等级别
4. （布局）float浮动盒子
5. （布局）block块状水平盒子
6. 负z-index
7. 层叠上下文background/border

#### 层叠准则

1. 谁大谁上：层叠水平值大的在上面；
2. 后来居上：当元素的层叠水平一致、层叠顺序相同时，处于后面的元素会覆盖前面的元素。

##### 层叠上下文元素有如下特性：

- 层叠水平要比普通元素高
- 可以阻断元素的混合模式
- 可以嵌套，内部层叠上下文及其子元素均受制于外部的“层叠上下文”
- 每个层叠上下文和兄弟元素独立，当进行层叠变化或渲染时，只需要考虑后代元素
- 当发生层叠时，整个元素被认为是在父层叠上下文的层叠顺序中



## 强大的文本处理能力 ##

#### `line-height`和`font-size`的计算比例

vertical-align百分比值属性是相对于line-height计算 line-height的数值属性和百分比值都是相对于font-size计算。

##### `font-size`和`ex em rem`

1em的计算值等同当前元素所在的font-size计算值。 rem=root em 。根元素em大小。

##### 理解font-size的关键字属性值

1. **相对尺寸关键字**。larger、smaller ，根据当前元素`font-size`计算
2. **绝对尺寸关键字**。`xx-large、x-large、large、medium、small、x-small、xx-small`

实际策略：

- 一般会对html或者body重置font-size大小。
- 容器设置font-size:medium，此时这个局部展示区域的字号跟随浏览器的设置，默认计算值是16px。
- 容器内的文字字号全部使用相对单位，如百分比值或em，然后基于16px进行转换。

##### `font-size:0`与文本的隐藏

中文情况下，chrome的font-size计算值不能小于12 （就算设置了小于12的，按12算）

【用途】隐藏logo对应元素内的文字，除了text-indent缩进隐藏外，还可以使用以下方法：

```
.logo {
    font-size: 0;
}
```

#### 字体属性家族font-family

`font-family`支持两类属性值，一类是字体名，一类是字体族。 如果字体名包含空格，需要用引号包起来，也可以多个设定逗号分隔

```
h1{
font-family:'PingFang SC','Microsoft Yahei'
}
```

##### `font-weight`，粗细

400=normal，700=bold。 注意，取值为100-900之间的整百数（可以取100，200，但是不可以取150）

##### `font-style`,倾斜样式

- `font-style:normal`
- `font-style:italic`，使用当前字体的斜体
- `font-style:oblique`，单纯让文字倾斜 （和上面的区别：有些字体有自己设计的斜体，样式和倾斜的不一样）

##### `font-variant`

对中文没用，`font-variant:small-caps`表现出英文小体型大写字母

#### `font`属性：进行文本相关样式的缩写

完整语法： `[font-style||font-variant||font-weight]?font-size[/line-height]?font-family`，（font-size和font-family是必需项）。

font缩写会破坏部分属性的继承性，必须要带上`font-family`。 对于`font-family`属性值过长的解决方法

- 使用一个系统不存在的字体名字占位，再设置`font-family:inherit`重置占位
- 利用`@font face`规则将字体列表重定义为一个字体。

##### 使用关键字值的font属性

font属性支持关键字属性值， 语法：`font:caption|icon|menu|message-box|small-caption|status-bar` 【注意】 使用关键字作为属性值必须是独立的，不能添加`font-family`或`font-size`等。 考虑chrome的市场占有率，在使用font时，避开`caption,icon,message-box`

##### 应用价值：让字体跟着系统走。

好处1：变成情感化设计，引起用户好感。（有些会自定义字体） 好处2：系统更新字体换掉，与时俱进 【eg】使用系统字体

```
html:{font-family:system-ui}
```

#### `@font face`规则

`@font face`的**本质**上就是一个定义字体或字体集的**变量**，包括字体重命名、默认字体样式设置等。 【博客】[真正了解CSS3背景下的@font face规则](https://www.zhangxinxu.com/wordpress/?p=6063)

##### 推荐使用方法：

```
@font-face {
    font-family: ICON;
    src: url("icon.eot") format('eot');
    src: local('☺'),
    url("icon.woff2") format("woff2"),
    url("icon.woff") format("woff"),
    url("icon.ttf") format("truetype");
}
```

【说明】

> 关于src下各个格式的说明

- eot格式是IE私有的。（舍弃）
- woff是专门为Web开发而设计的字体格式。（次优先使用）
- woff2是比woff尺寸更小的字体，是Web开发首选字体。（优先使用）
- ttf格式作为系统安装字体比较多。（舍弃）



## 总结

CSS 是“流”的世界，这包括：

- 元素尺寸
- 盒子模型
- 内联元素
- 流的破坏和保护（float、BFC、absolute）

而这，就是 CSS2.1 的最核心内容。