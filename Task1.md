# Task1

### web语义化该如何理解 ###

​		**web语义化**是指使用恰当语义的标签，让页面具有良好的结构，页面元素有含义，从而让人和机器都能快速理解页面中的内容。简单来说就是使用便于理解的特定语言来定义特定的事物。

​		web语义化的优点有很多

  - 有利于SEO[^1]（Search Engine Optimization），有助于爬虫抓取更多的有效信息，爬虫是依赖于标签来确定上下文和各个关键字的权重。[^1](Search Engine Optimization,指搜索引擎优化。通过站内优化比如网站机构调整、网站内容建设、网站代码优化等以及站外优化，比如网站站外推广、网站品牌建设等，使网站满足搜索引擎收录排名需求没在搜索引擎中提高关键词排名，从而吸引精准用户进入网站，获得免费流量，产生直接销售或者品牌推广。) 
  - 语义化的HTML在没有CSS的情况下也能呈现较好地内容结构与代码结构
  - 方便其他设备的解析（如屏幕阅读器、盲人阅读器、移动设备）以有意义的方式来渲染网页
		- 便于团队开发和维护，语义化更具有可读性。

​		web语义化包含两个方面，一个是HTML标签语义化，另一个是CSS命名语义化。

​		对于人们来说，我们可以通过视觉的划分来判定内容，但是对于搜索引擎来说，他们看到的只有界面的代码部分。如果我们在合适的位置使用了恰当的标签，那么写出来的界面就会语义明确，结构清晰，搜索引擎也可以认出哪些是页面的重要内容，并给予较高的权值。h1~h6这几个标签在搜索引擎中的权值非常高，使用他们作为界面标题就是一个简单地SEO优化了。

​		对于HTML语义化来说，Web语义化是指使用语义恰当的标签，使页面有良好的结构，让页面元素有含义，便于被浏览器、搜索引擎解析、利于SEO。

​		举个例子，HTML中的<h1>标签，一篇文章应该只有一个总标题即h1，然后根据文章内容，会有若干个h2以及嵌套的h3。

```
<table>
        <tr>
            <td colspan="2">Student List</td>
        </tr>
        <tr>
            <td>Name</td>
            <td>Age</td>
        </tr>
        <tr>
            <td>Byron</td>
            <td>24</td>
        </tr>
        <tr>
            <td>Vincent</td>
            <td>25</td>
        </tr>
        <tr>
            <td>Casper</td>
            <td>27</td>
        </tr>
    </table>
```

​		对于上面的代码中，我们可以理解这个表格描述的内容，但是计算机却并不清楚，因为计算机不内从你的代码中得知表格的title以及内容。所以为了让计算机清楚我们在表达什么，我们要对代码进行修改。

```
<table>
        <caption>Student List</caption>
        <thead>
            <tr>
                <th>Name</th>
                <th>Age</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Byron</td>
                <td>24</td>
            </tr>
            <tr>
                <td>Vincent</td>
                <td>25</td>
            </tr>
            <tr>
                <td>Casper</td>
                <td>27</td>
            </tr>
        </tbody>
</table>
```

​		这样不仅我们能够清楚，计算机也能理解表格所表示的意义了

​		还有就是CSS语义化，CSS语义化是class和ID命名的语义。class属性作为HTML与CSS衔接的纽带，其本意是用来描述元素内容的。指的是用易于理解的名称对HTML标签附加的class或id命名。如果说HTML语义化标签是给机器看的，那么CSS命名的语义化就是给人看的了。良好的CSS命名方式可以减少沟通调试成本，易于理解。

​		CSS命名首先要满足W3C的命名规范和团队的命名规范。其次就是高效和可重用性。

```
<!-- 以表现为中心 -->
<div class="ft margin10">
    <span>用户名：ToT</span>
<div>

<!-- 以信息为中心 -->
<p class="user_info">
    <em>用户名:ToT</em>
<p>
```

![](C:\Users\Temton\Pictures\html5-layout.jpg)



### W3C最新规范下的HTML标签都有哪些？ ###

<div class="article-body">
<div class="article-intro" id="content">
<h1>HTML 参考手册- <span class="color_h1">(HTML5 标准)</span></h1>
<hr>
<table class="reference notranslate">
<tbody>
<tr>
<th align="left" width="25%">标签</th>
<th align="left" width="75%">描述</th>
</tr>
<tr>
<td>  &lt;!--...--&gt; </td>
<td>定义注释</td>
</tr>
<tr>
<td> &lt;!DOCTYPE&gt; </td>
<td>定义文档类型</td>
</tr>
<tr>
<td> &lt;a&gt; </td>
<td>定义超文本链接</td>
</tr>
<tr>
<td>&lt;abbr&gt; </td>
<td>定义缩写</td>
</tr>
<tr>
<td>&lt;acronym&gt; </td>
<td>定义只取首字母的缩写，不支持HTML5</td>
</tr>
<tr>
<td> &lt;address&gt; </td>
<td>定义文档作者或拥有者的联系信息</td>
</tr>
<tr>
<td>&lt;applet&gt; </td>
<td>HTML5中不赞成使用。定义嵌入的 applet。</td>
</tr>
<tr>
<td>&lt;area&gt; </td>
<td>定义图像映射内部的区域</td>
</tr>
<tr>
<td> &lt;article&gt;</td>
<td>定义一个文章区域</td>
</tr>
<tr>
<td>&lt;aside&gt;</td>
<td>定义页面的侧边栏内容</td>
</tr>
<tr>
<td> &lt;audio&gt;</td>
<td>定义音频内容</td>
</tr>
<tr>
<td>&lt;b&gt; </td>
<td>定义文本粗体</td>
</tr>
<tr>
<td> &lt;base&gt; </td>
<td>定义页面中所有链接的默认地址或默认目标。</td>
</tr>
<tr>
<td>&lt;basefont&gt;</td>
<td>HTML5不支持，不赞成使用。定义页面中文本的默认字体、颜色或尺寸。</td>
</tr>
<tr>
<td>&lt;bdi&gt; </td>
<td>允许您设置一段文本，使其脱离其父元素的文本方向设置。</td>
</tr>
<tr>
<td> &lt;bdo&gt; </td>
<td>定义文字方向</td>
</tr>
<tr>
<td>&lt;big&gt; </td>
<td>定义大号文本，HTML5不支持</td>
</tr>
<tr>
<td>&lt;blockquote&gt; </td>
<td>定义长的引用</td>
</tr>
<tr>
<td>&lt;body&gt; </td>
<td>定义文档的主体</td>
</tr>
<tr>
<td>&lt;br&gt; </td>
<td>定义换行</td>
</tr>
<tr>
<td>&lt;button&gt; </td>
<td>定义一个点击按钮</td>
</tr>
<tr>
<td>&lt;canvas&gt;</td>
<td>定义图形，比如图表和其他图像,标签只是图形容器，您必须使用脚本来绘制图形</td>
</tr>
<tr>
<td> &lt;caption&gt; </td>
<td>定义表格标题</td>
</tr>
<tr>
<td>&lt;center&gt; </td>
<td>HTML5不支持，不赞成使用。定义居中文本。</td>
</tr>
<tr>
<td> &lt;cite&gt; </td>
<td>定义引用(citation)</td>
</tr>
<tr>
<td> &lt;code&gt; </td>
<td>定义计算机代码文本</td>
</tr>
<tr>
<td> &lt;col&gt; </td>
<td>定义表格中一个或多个列的属性值</td>
</tr>
<tr>
<td>&lt;colgroup&gt; </td>
<td>定义表格中供格式化的列组</td>
</tr>
<tr>
<td> &lt;command&gt; </td>
<td>定义命令按钮，比如单选按钮、复选框或按钮</td>
</tr>
<tr>
<td>&lt;datalist&gt; </td>
<td>定义选项列表。请与 input 元素配合使用该元素，来定义 input 可能的值。</td>
</tr>
<tr>
<td> &lt;dd&gt; </td>
<td>定义定义列表中项目的描述</td>
</tr>
<tr>
<td> &lt;del&gt; </td>
<td>定义被删除文本</td>
</tr>
<tr>
<td> &lt;details&gt;</td>
<td>用于描述文档或文档某个部分的细节</td>
</tr>
<tr>
<td> &lt;dfn&gt; </td>
<td>定义定义项目</td>
</tr>
<tr>
<td>&lt;dialog&gt; </td>
<td>定义对话框，比如提示框</td>
</tr>
<tr>
<td>&lt;dir&gt; </td>
<td>HTML5不支持，不赞成使用。定义目录列表。</td>
</tr>
<tr>
<td> &lt;div&gt; </td>
<td>定义文档中的节</td>
</tr>
<tr>
<td> &lt;dl&gt; </td>
<td>定义列表详情</td>
</tr>
<tr>
<td>&lt;dt&gt; </td>
<td>定义列表中的项目</td>
</tr>
<tr>
<td>&lt;em&gt; </td>
<td>定义强调文本</td>
</tr>
<tr>
<td> &lt;embed&gt; </td>
<td>定义嵌入的内容，比如插件。</td>
</tr>
<tr>
<td> &lt;fieldset&gt; </td>
<td>定义围绕表单中元素的边框</td>
</tr>
<tr>
<td> &lt;figcaption&gt;</td>
<td>定义&lt;figure&gt; 元素的标题</td>
</tr>
<tr>
<td> &lt;figure&gt; </td>
<td>规定独立的流内容（图像、图表、照片、代码等等）。</td>
</tr>
<tr>
<td>&lt;font&gt; </td>
<td>HTML5不支持，不赞成使用。定义文字的字体、尺寸和颜色。</td>
</tr>
<tr>
<td> &lt;footer&gt;</td>
<td>定义 section 或 document 的页脚。</td>
</tr>
<tr>
<td>&lt;form&gt; </td>
<td>定义了HTML文档的表单</td>
</tr>
<tr>
<td>&lt;frame&gt; </td>
<td>定义框架集的窗口或框架</td>
</tr>
<tr>
<td>&lt;frameset&gt; </td>
<td>定义框架集</td>
</tr>
<tr>
<td>&lt;h1&gt; to &lt;h6&gt; </td>
<td>定义 HTML 标题</td>
</tr>
<tr>
<td> &lt;head&gt; </td>
<td>定义关于文档的信息</td>
</tr>
<tr>
<td>&lt;header&gt;</td>
<td>定义了文档的头部区域</td>
</tr>
<tr>
<td> &lt;hr&gt; </td>
<td>定义水平线</td>
</tr>
<tr>
<td> &lt;html&gt; </td>
<td>定义 HTML 文档</td>
</tr>
<tr>
<td>&lt;i&gt; </td>
<td>定义斜体字</td>
</tr>
<tr>
<td>&lt;iframe&gt; </td>
<td>定义内联框架</td>
</tr>
<tr>
<td>&lt;img&gt; </td>
<td>定义图像</td>
</tr>
<tr>
<td>&lt;input&gt; </td>
<td>定义输入控件</td>
</tr>
<tr>
<td>&lt;ins&gt; </td>
<td>定义被插入文本</td>
</tr>
<tr>
<td>&lt;kbd&gt; </td>
<td>定义键盘文本</td>
</tr>
<tr>
<td>&lt;keygen&gt; <span class="new">New</span></td>
<td>规定用于表单的密钥对生成器字段。</td>
</tr>
<tr>
<td>&lt;label&gt; </td>
<td>定义 input 元素的标注</td>
</tr>
<tr>
<td>&lt;legend&gt; </td>
<td>定义 fieldset 元素的标题。</td>
</tr>
<tr>
<td>&lt;li&gt; </td>
<td>定义列表的项目</td>
</tr>
<tr>
<td>&lt;link&gt; </td>
<td>定义文档与外部资源的关系</td>
</tr>
<tr>
<td>&lt;map&gt; </td>
<td>定义图像映射</td>
</tr>
<tr>
<td>&lt;mark&gt; <span class="new">New</span></td>
<td>定义带有记号的文本。请在需要突出显示文本时使用 &lt;m&gt; 标签。</td>
</tr>
<tr>
<td>&lt;menu&gt; </td>
<td>不赞成使用。定义菜单列表。</td>
</tr>
<tr>
<td>&lt;meta&gt; </td>
<td>定义关于 HTML 文档的元信息。</td>
</tr>
<tr>
<td>&lt;meter&gt; <span class="new">New</span></td>
<td>定义度量衡。仅用于已知最大和最小值的度量。</td>
</tr>
<tr>
<td>&lt;nav&gt; <span class="new">New</span></td>
<td>定义导航链接的部分</td>
</tr>
<tr>
<td>&lt;noframes&gt; </td>
<td>定义针对不支持框架的用户的替代内容。HTML5不支持</td>
</tr>
<tr>
<td>&lt;noscript&gt; </td>
<td>定义针对不支持客户端脚本的用户的替代内容。</td>
</tr>
<tr>
<td>&lt;object&gt; </td>
<td>定义内嵌对象</td>
</tr>
<tr>
<td>&lt;ol&gt; </td>
<td>定义有序列表。</td>
</tr>
<tr>
<td>&lt;optgroup&gt; </td>
<td>定义选择列表中相关选项的组合。</td>
</tr>
<tr>
<td>&lt;option&gt; </td>
<td>定义选择列表中的选项。</td>
</tr>
<tr>
<td>&lt;output&gt;</td>
<td>定义不同类型的输出，比如脚本的输出。</td>
</tr>
<tr>
<td> &lt;p&gt; </td>
<td>定义段落。</td>
</tr>
<tr>
<td> &lt;param&gt; </td>
<td>定义对象的参数。</td>
</tr>
<tr>
<td>&lt;pre&gt; </td>
<td>定义预格式文本。</td>
</tr>
<tr>
<td>&lt;progress&gt;</td>
<td>定义运行中的进度（进程）。</td>
</tr>
<tr>
<td>&lt;q&gt; </td>
<td>定义短的引用。</td>
</tr>
<tr>
<td> &lt;rp&gt; </td>
<td>&lt;rp&gt; 标签在 ruby 注释中使用，以定义不支持 ruby 元素的浏览器所显示的内容。</td>
</tr>
<tr>
<td>&lt;rt&gt;</td>
<td>&lt;rt&gt; 标签定义字符（中文注音或字符）的解释或发音。</td>
</tr>
<tr>
<td> &lt;ruby&gt;</td>
<td>&lt;ruby&gt; 标签定义 ruby 注释（中文注音或字符）。</td>
</tr>
<tr>
<td> &lt;s&gt; </td>
<td>不赞成使用。定义加删除线的文本。</td>
</tr>
<tr>
<td> &lt;samp&gt; </td>
<td>定义计算机代码样本。</td>
</tr>
<tr>
<td> &lt;script&gt; </td>
<td>定义客户端脚本。</td>
</tr>
<tr>
<td> &lt;section&gt;</td>
<td>&lt;section&gt; 标签定义文档中的节（section、区段）。比如章节、页眉、页脚或文档中的其他部分。</td>
</tr>
<tr>
<td> &lt;select&gt; </td>
<td>定义选择列表（下拉列表）。</td>
</tr>
<tr>
<td> &lt;small&gt; </td>
<td>定义小号文本。</td>
</tr>
<tr>
<td>&lt;source&gt;</td>
<td>&lt;source&gt; 标签为媒介元素（比如 &lt;video&gt; 和 &lt;audio&gt;）定义媒介资源。</td>
</tr>
<tr>
<td> &lt;span&gt; </td>
<td>定义文档中的节。</td>
</tr>
<tr>
<td>&lt;strike&gt; </td>
<td>HTML5不支持，不赞成使用。定义加删除线文本。</td>
</tr>
<tr>
<td>&lt;strong&gt; </td>
<td>定义强调文本。</td>
</tr>
<tr>
<td>&lt;style&gt; </td>
<td>定义文档的样式信息。</td>
</tr>
<tr>
<td>&lt;sub&gt; </td>
<td>定义下标文本。</td>
</tr>
<tr>
<td>&lt;summary&gt;</td>
<td>&lt;summary&gt; 标签包含 details 元素的标题，"details" 元素用于描述有关文档或文档片段的详细信息。</td>
</tr>
<tr>
<td>&lt;sup&gt; </td>
<td>定义上标文本。</td>
</tr>
<tr>
<td>&lt;table&gt; </td>
<td>定义表格。</td>
</tr>
<tr>
<td>&lt;tbody&gt; </td>
<td>定义表格中的主体内容。</td>
</tr>
<tr>
<td>&lt;td&gt; </td>
<td>定义表格中的单元。</td>
</tr>
<tr>
<td>&lt;textarea&gt; </td>
<td>定义多行的文本输入控件。</td>
</tr>
<tr>
<td>&lt;tfoot&gt; </td>
<td>定义表格中的表注内容（脚注）。</td>
</tr>
<tr>
<td>&lt;th&gt; </td>
<td>定义表格中的表头单元格。</td>
</tr>
<tr>
<td>&lt;thead&gt; </td>
<td>定义表格中的表头内容。</td>
</tr>
<tr>
<td> &lt;time&gt; </td>
<td>定义日期或时间，或者两者。</td>
</tr>
<tr>
<td>&lt;title&gt; </td>
<td>定义文档的标题。</td>
</tr>
<tr>
<td>&lt;tr&gt; </td>
<td>定义表格中的行。</td>
</tr>
<tr>
<td>&lt;track&gt; </td>
<td>&lt;track&gt; 标签为诸如 video 元素之类的媒介规定外部文本轨道。</td>
</tr>
<tr>
<td>&lt;tt&gt; </td>
<td>定义打字机文本。</td>
</tr>
<tr>
<td>&lt;u&gt; </td>
<td>不赞成使用。定义下划线文本。</td>
</tr>
<tr>
<td>&lt;ul&gt; </td>
<td>定义无序列表。</td>
</tr>
<tr>
<td> &lt;var&gt; </td>
<td>定义文本的变量部分。</td>
</tr>
<tr>
<td>&lt;video&gt;</td>
<td>&lt;video&gt; 标签定义视频，比如电影片段或其他视频流。</td>
</tr>
<tr>
<td> &lt;wbr&gt;</td>
<td>规定在文本中的何处适合添加换行符。</td>
</tr>
</tbody>
</table>



### 语义化标签 ###

+ **header元素**

  header代表“网页”或者“section”的页眉，通常包含h1-h6 元素或者 hgroup, 作为整个页面或者一个内容快的标题。也可以包裹一节的目录部分，一个搜索框，一个nav，或者相关logo。

  代码示例：

  ```
  <header>
  	<hgroup>
  		<h1>网站标题</h1>
  		<h2>网站副标题</h2>
  	</hgroup>
  </header>
  ```

  注意事项：

  1. 可以是“网页”或者任意“section”的头部部分
  2. 没有个数限制
  3. 如果hgroup或者h1-h6自己就能工作得很好，那么就没必要用header。

+ **hgroup元素**

  hgroup元素代表“网页”或“section”的标题，当元素有多个层级时，该元素可以将`h1`到`h6`元素放在其内，譬如文章的主标题和副标题组合

  代码示例：

  ```
  <hgroup>
  		<h1>网站标题</h1>
  		<h2>网站副标题</h2>
  </hgroup>
  ```

  注意事项：

  1. 如果只需要一个h1-h6标签就不用hgroup
  2. 如果有连续多个h1-h6标签就用hgroup
  3. 如果有连续多个标题和其他文章数据，h1-h6标签就用hgroup包住，和其他文章元数据一起放入header标签

+ **footer元素**

  `footer`元素代表“网页”或任意“section”的页脚，通常含有该节的一些基本信息，譬如：作者，相关文档链接，版权资料。如果`footer`元素包含了整个节，那么它们就代表附录，索引，提拔，许可协议，标签，类别等一些其他类似信息。

  代码示例：

  ```
  <footer>
      COPYRGHT@ToT
  </footer>
  ```

  注意事项：

  1. 可以是“网页”或者任意“section”的底部部分
  2. 没有个数限制，除了包裹的内容不一样，其他跟header类似

+ **nav元素**

  nav 元素代表页面的导航链接区域。用于定义页面的主要导航部分。 代码示例：

  ```
  <nav>
      <ul>
          <li>HTML语义化</li>
          <li>CSS 语义化</li>
      </ul>
  </nav>
  ```

  侧边栏上目录、面包屑导航、搜索样式、或者下一篇上一篇文章我们可能会想要用到nav，但是事实上规范上说nav只能用在页面主要导航部分上。页脚区域中的链接列表，虽然指向不同网站的不同区域，譬如服务条款，版权页等，这些footer元素就能够用了。

  注意事项：

  1. 用于整个页面的主要导航部分，不适合就不要用nav元素了

+ **article元素**

  article 代表一个在文档，页面或者网站中自成一体的内容，其目的是为了让开发者独立开发或重用。
  除了它的内容，article会有一个标题(通常会在`header`里)，一个`footer`页脚。

  代码示例：

  ```
  <article>
      <h1>你好，我是这边文章的标题</h1>
      <p>你好，我是文章的内容</p>
      <footer>
          <p>最终解释权归XXX所有</p>
      </footer>
  </article>
  ```

  这是一个最简单的例子，如果在article内部再嵌套article，那就代表内嵌的article是与它外部的内容有关联的，如博客文章下面的评论，如下：

  ```
  <article>
  
      <header>
          <h1>web 语义化</h1>
          <p><time pubdate datetime="2018-03-23">2018-03-23</time></p>
      </header>
  
      <p>文章内容..</p>
  
      <article>
          <h2>评论</h2>
  
          <article>
              <header>
                  <h3>评论者: 专业水军</h3>
                  <p><time pubdate datetime="2018-03-23T15:10-08:00">~1 min ago</time></p>
              </header>
              <p>还行</p>
          </article>
  
          <article>
              <header>
                  <h3>评论者: 大水怪</h3>
                  <p><time pubdate datetime="2018-03-23T15:10-08:00">~1 hour ago</time></p>
              </header>
              <p>楼上说的对</p>
          </article>
  
      </article>
  
  </article>
  ```

  article 内部可以嵌套article，表示评论或者其他跟文章有关联的内容。article内部还可以嵌套section，如下：

  ```
  <article>
  
      <h1>web语义化</h1>
      <p>什么是语义化？</p>
  
      <section>
          <h2>语义化详解</h2>
          <p>语义化就是。。。</p>
      </section>
  
      <section>
          <h2>语义化特点</h2>
          <p>语义化特点就是。。。</p>
      </section>
  
  </article>
  ```

  文章内section是独立的部分，但是它们只能算是组成整体的一部分，从属关系，article是大主体，section是构成这个大主体的一个部分。

  注意事项：

  1. 自身独立情况下：用article
  2. 是相关内容： 用section
  3. 没有语义的： 用div

+ **section元素**

  `section` 元素代表文档中的“节”或“段”，“段”可以是指一片文章里按照主题的分段；“节”可以是指一个页面里的分组。`section`通常还带标题，虽然html5中section会自动给标题h1-h6降级，但是最好手动给他们降级。

  代码示例：

  ```
  <section>
      <h1>section是啥？</h1>
      <article>
          <h2>关于section</h2>
          <p>section的介绍</p>
          <section>
              <h3>关于其他</h3>
              <p>关于其他section的介绍</p>
          </section>
      </article>
  </section>
  ```

  注意事项：

  1. 一张页面可以用section划分为简介、文章条目和联系信息。不过在文章内页，最好用article。section不是一般意义上的容器元素，如果想作为样式展示和脚本的便利，可以用div。
  2. 表示文档中的节或者段。
  3. acticle、nav、aside可以理解为特殊的section，如果可以用article、nav、aside就不要用section，没有实际意义的就用div

+ **aside元素**

  `aside` 元素被包含在`article`元素中作为主要内容的附属信息部分，其中的内容可以是与当前文章有关的相关资料，标签，名词解释等。
  在`article`元素之外使用作为页面或站点全局的附属信息部分。最典型的是侧边栏，其中的内容可以是日志串连，其他组的导航，甚至广告，这些内容相关的页面。

  代码示例：

  ```
  <article>
      <p>内容</p>
      <aside>
          <h1>作者简介</h1>
          <p>小维,哈哈哈</p>
      </aside>
  </article>
  ```

  注意事项：

  1. aside 在 article 内表示主要内容的附属信息。
  2. 在article之外侧可以做侧边栏，没有article与之对应，最好不用
  3. 如果是广告，其他日志链接或者其他分类导航也可以用。





### 什么是[块状元素]和[行内元素],它们之间的具体区别是什么 ###

​		在CSS中，HTML中的标签元素大体被分为三种不同的类型：块状元素、内联元素（又称行内元素）和内联块状元素。但是这三者通过display属性是可以相互转换的

​		对于三者的转换：

1. display:inline;转换为行内元素
2. display:block;转换为块状元素
3. display:inline-block;转换为行内块状元素

​		常见的**块状元素**有:

​		<div>、<p>、<h1>...<h6>、<ol>、<ul>、<dl>、<table>、<address>、<blockquote>、 <form>......

​		常见的**内联元素**(行内元素)有：

​		<a>、<span>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<br>、<code>......

​		常见的**内联块元素**有：

​		<img>、<input>......

​		对于块状元素来说，每个块状元素默认占一行高度，一行内添加一个块状元素后一般无法添加其他元素（float浮动后除外)。两个块级元素连续编辑时，会在页面自动换行显示，并且宽度、高度、内边距以及外边距都可控制。块状元素一般可以嵌套块状元素或者行内元素；

​		而对于内联元素来说，行内元素一般都是基于语义级(semantic)的基本元素，只能容纳文本或其他内联元素，常见内联元素 “a”。比如span元素，IFRAME元素和元素样式的display : inline的都是行内元素。例如文字这类元素，各个字母之间横向排列，到最右端自动折行。它与相邻的内敛元素在同一行，宽度、高度、内边距的top/bottom、外边距的top/bottom不可变。



**内联元素和块状元素的区别**

**区别一：**
块级：块级元素会独占一行，默认情况下宽度自动填满其父元素宽度
行内：行内元素不会独占一行，相邻的行内元素会排在同一行。其宽度随内容的变化而变化。

**区别二：**
块级：块级元素可以设置宽高
行内：行内元素不可以设置宽高

**区别三：**
块级：块级元素可以设置margin，padding
行内：行内元素水平方向的margin-left; margin-right; padding-left; padding-right;可以生效。但是竖直方向的margin-bottom; margin-top; padding-top; padding-bottom;却不能生效。

**区别四：**
块级：display:block;
行内：display:inline;
可以通过修改display属性来切换块级元素和行内元素					