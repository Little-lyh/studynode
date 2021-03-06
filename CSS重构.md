## CSS重构

重构是指在不改变代码行为的前提下，重写代码，使其更加简洁、易于复用。

### 优秀的架构

+ 可预测：可以对软件的工作方式和结构做出准确的假设
+ 可复用：在多处使用同一代码，无需重写
+ 可扩展：比较容易的增加新内容
+ 可维护：修改一处代码不用大规模的改动其他代码

### CSS代码重构的目的

书写CSS代码时，不仅仅只是完成页面设计的效果，还应该让CSS代码易于管理，维护。我们对CSS代码重构主要有两个目的：

- 提高代码性能

  - 提高页面的加载性能
    提高页面的加载性能，简单说就是减小CSS文件的大小，提高页面的加载速度，尽可以的利用http缓存
  - 提高CSS代码性能
    不同的CSS代码，浏览器对其解析的速度也是不一样的，如何提高浏览器解析CSS代码的速度也是我们要考虑的，例如CSS选择器是从右侧开始查找。

- 提高代码的可维护性

  - 可重用性
    一般来说，一个项目的整体设计风格是一致的，页面中肯定有几个风格一致但有些许不同的模块，如何在尽可能多地重用CSS代码，尽可能少地增加新代码，这是CSS代码中非常重要的一点。如果CSS代码的重用性高，我们可能只需要写一些不一样的地方，对页面性能和可维护性、提高开发效率都有很大的帮助。

  - 可扩展性
    如果产品增加了某个功能，我们应该保证新增加的CSS代码不会影响到旧的CSS代码和页面，并且尽可能少地增加新代码而重用旧代码。

  - 可修改性
    如果某个模块产品经理觉得要修改样式，或者要删掉它，如果没有规划好相应的CSS代码，过了一段时间之后，开发人员可能已经不记得这段代码作用了几个地方，不敢修改或删除它，怕影响其他的部分，这样下去CSS代码也就越来越多，影响了页面的性能，还造成了代码的复杂度。



### 重构前审查 CSS

+ 所用到的属性列表

+ 颜色数量

+ 使用的最高和最低选择器优先级

+ 选择器长度



### 重构策略

推荐多次小范围重构，避免大范围重构引入错误。

（1）删除僵尸代码：

（2）分离 CSS 和 JavaScript

（3）分离基础样式

（4）删除冗余的 ID

（5）定义可复用的组件，删除重复的 CSS

（6）删除行内 CSS



### CSS代码重构的基本方法

1.   将CSS样式单独写在单独的CSS文件里，在head标签中进行调用
   - 内容样式分离，利于维护
   - 减少html页面体积，加快加载速度
   - CSS文件可以被缓存、重用，维护成本降低
2. 不使用@import，这种形式会影响CSS文件的加载速度
3. 避免使用复杂的选择器，层级越少越好
   + 选择器最好不要嵌套三层以上
   + 但是并不是任何场景都应该遵循该推荐
4. 精简页面样式文件，去掉无用样式
5. 利用CSS的继承性



### 提高代码的可维护性

1. 命名

   **ID和类名要有意义**

   ```
   1)页面结构
   容器: container
   页头：header
   内容：content/container
   页面主体：main
   页尾：footer
   导航：nav
   侧栏：sidebar
   栏目：column
   页面外围控制整体佈局宽度：wrapper
   左右中：left right center
   (2)导航
   导航：nav
   主导航：mainnav
   子导航：subnav
   顶导航：topnav
   边导航：sidebar
   左导航：leftsidebar
   右导航：rightsidebar
   菜单：menu
   子菜单：submenu
   标题: title
   摘要: summary
   (3)功能
   标志：logo
   广告：banner
   登陆：login
   登录条：loginbar
   注册：register
   搜索：search
   功能区：shop
   标题：title
   加入：joinus
   状态：status
   按钮：btn
   滚动：scroll
   标籤页：tab
   文章列表：list
   提示信息：msg
   当前的: current
   小技巧：tips
   图标: icon
   注释：note
   指南：guild
   服务：service
   热点：hot
   新闻：news
   下载：download
   投票：vote
   合作伙伴：partner
   友情链接：link
   版权：copyright
   四、注意事项::
   1.一律小写;
   2.尽量用英文;
   3.不加中槓和下划线;
   4.尽量不缩写，除非一看就明白的单词。
   ```

2. 备注

   注释记录的内容包括：

   1. 文件内容
   2. 选择器的依赖、用法
   3. 使用特定声明的原因（hack等）
   4. 不应继续使用的废弃样式

   ```
   /*
   * 导航链接样式
   *
   * @see templates/nav.html
   */
   .nav-link {
     ...
   }
    
   .nav-link:hover {
     border-bottom: 4px solid #333;
     /* 防止增加了4px下边框导致元素移动 */
     padding-bottom: 0;
   }
    
   /* @deprecated */
   .nav-link {
     ...
   }
   ```

3. 重复样式封装，一次定义多次调用

4. 书写的顺序



### CSS权重

![权重分配](C:\Users\Temton\Desktop\o_specificity-value.png)

1. !important，加在样式属性值后，权重值为 10000

2. 内联样式，如：style=””，权重值为1000

3. ID选择器，如：#content，权重值为100

4. 类，伪类和属性选择器，如： content、:hover 权重值为10

5. 标签选择器和伪元素选择器，如：div、p、:before 权重值为1

6. 通用选择器（*）、子选择器（>）、相邻选择器（+）、同胞选择器（~）、权重值为0

   + 如果样式上加有!important标记，那么始终采用这个标记的样式。例如：

   ```
   p{ 
   color: gray !important
   }
   ```

   + 匹配的内容按照CSS权重排序，权重大的优先；可以看到，CSS权重只是决定应用哪个样式的其中一个步骤，不过这个步骤是最复杂的，上面已经说过了。
   + 如果权重也一样，按照它在CSS样式表里声明的顺序，后声明的优先，例如：

   ```
   h1{color:blue}
   h1{color:red}
   ```

   ​	最终显示出的颜色为red。

### CSS重构应该避免的问题

+ 滥用id

CSS的权重的高低取决于你是用的选择器：id、class类、tags标签。id是三者中区中最高的（id在网页中只能使用一次，所以他的权重是100），其次是class类，最后才是tag标签。

+ 大串的CSS选择器

如果你使用一大串选择器（超过三个层级）你同样会造成过高权重，导致你陷入到高权重和更高权重的汪洋大海之中。那针对这个问题的解决办法有什么呢——精简！一般情况下，我们应该控制选择器在2个，最多3个。

+ inline styles

内联样式是CSS 权重罪恶的源泉，同时也从根本上摧毁了我们使用 CSS的初心（结构样式分离）。

根据 CSS 权重级的特性，内联样式只能被`！important` 所覆盖。一般来说，这就意味着，如果某猿使用了`！important`，他们更多是被逼的没办法才这么用，而不是想这么用。的确`！important`在 CSS 样式表中用起来十分方便，但我们最好是聪明地、小心翼翼地碰她、用他，而不是把他当做救命稻草（救命稻草用多了，迟早也会从救命稻草变成压死骆驼的稻草）。

怎么解决内联样式的问题呢

​		1.复制删除 

​		2.粘贴 。

剔除内联样式，转移到样式表之中吧。

+ 不规范的命名

根据结构从下至上式的命名方式模糊化了 html 结构，工程师常常根据上下结构来命名id 和 class，而不是具体的设计元素，例如`#header`,`content`，这常常会导致长选择器（举个例子如`. menu ul li a｛　｝`），这样的后果是我们的代码变得难以调试和维护。怎么解决这个问题呢？我们应该尝试从网页中分离出设计元素，这同样可以减少我们代码中的冗余。

+ 冗余/重复

冗余意味着你写 CSS 的过程中不断重复某些代码。在使用编程语言的时候， 我们很好理解重复（造轮子）意味着浪费时间，我们在 code 中应该遵循 DRY 原则(Don't repeat yourself)。

+ 精简你的单位

如果你的样式表中混杂着 `px`,`em`,`rem`等等单位，是时候改变了，业内著名的web开发者[Rachel Nabors](http://rachelnabors.com/) 呼吁大家统一使用`em`为字体大小单位，他曾说「我看其他人的样式表第一件事就是看字体样式，然后把所有的`font-size`的单位换成`em`」，这几年用户使用的终端越来越多样（不同的终端、不同的浏览器使用的默认字体大小存在差异），使用绝对字体大小`px`变得越来越不可控，使用`em`等相对大小的字体则避免了这个问题。

+ 向下兼容和无效的规则

在开发的过程中，如果你不需要使用 css3 之类的高大上代码就能实现效果，那再好不过了。可是，作为工程师的你在 Chrome 最新版本上面看到的效果，并不意味着你的用户能在他们的浏览器上看到同样的效果（考虑过 IE 的感受没有），一个十分糟糕的坏习惯就是完全忽略向下兼容性。

解决这个问题，可以使用 [CSS LInt](http://csslint.net/)检测下你的 css 代码，CSS Lint的检测规则包括错误的和不合理的地方。

+ 无意义（不起作用）的样式

Harry Roberts的[Code smells in CSS](http://csswizardry.com/2012/11/code-smells-in-css/)是关于CSS糟糕用法的经典文章。他举了几个可有可无的不起作用样式的栗子：

```
h2{
font-size:2em;
margin-bottom:0.5em;
padding-bottom:0.5em;
border-bottom:1px solid #ccc; 
}

.no-border{
padding-bottom:0;
border-bottom:none;
}
```

Roberts 推荐的重构精简方法是删掉属性为`0`和`none`的属性值。

```
h2{
font-size:2em;
margin-bottom:0.5em; 
}

.headline{ 
padding-bottom:0.5em;
border-bottom:1px solid #ccc; 
}
```



+ 巧而不巧

任何时候你意识到你写了一个 css 的 hack 用法的时候，你直接把这些代码放到这个`hack.css` 之中（或者样式表的特定区域：通过注释跟其他样式区分开），这个专属区域是个好解决方案因为他最终会在用户端隐藏。

当我们养成了这个习惯，我们可以十分清晰地知道我们写了哪些 hack ，同样可以方便我们了解我们使用这些 hack 的情景，让我们可以知道如何避免这些 hack 。我们有许多写 hack 用法的理由，但是如果我们不记录我们为什么 hack，我们将不会从我们这些 hack 中学到我们为什么要错误地这么用。



+ 糟糕的文档和注释

写文档和注释绝对不是一个有意思的事情，但却是一个最重要的事情（尤其是涉及到项目后续可维护性时），文档可以有效地让其他人知道你的代码是干什么的，同时其他人理解你的 CSS。对于大部分语言（HTML,CSS,PHP,JavaScript），开发者可以直接在代码文件中写上注释（文档）。

Nabors曾说「我曾YY：如果我今天写完一个项目的 CSS 但是明儿我却挂掉了，有一个人~~幸运地~~接手我这个项目，那他看得懂我的这些代码是什么意思吗？」。尽量地让我们的样式表中的结构清晰，如果不能让人立马知道你的选择器指的是哪里的样式，可以尝试添加注释。