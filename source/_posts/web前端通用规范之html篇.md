title: web前端通用规范之html篇
date: 2016-04-05 23:26:33
tags:
- web前端
- html
- 规范

categories: 
- 规范
---

#### HTML规范

引用html5的文档模式

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的

```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```
<!--more-->

##### 字符编码

通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（约定一致采用UTF-8编码）。

```html
<head>
  <meta charset="UTF-8">
</head>
```

##### 文档模板

```html
<!DOCTYPE HTML>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Sample page</title>
        <link rel="stylesheet" href="css_example_url" />
        <script src="js_example_url"></script>
    </head>
    <body>
        <section id="page">
            <header id="header">
            页头
            </header>
            <section id="body">
            主体
            </section>
            <footer id="footer">
            页尾
            </footer>
        </section>
        <script>
        // 你的代码
        </script>
    </body>
</html>
```
#### IE 兼容模式

IE 支持通过特定的 <meta> 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```
### 元素

#### html5元素
```
1.section 表示文档中的节、区段，可以和h1-h6一起来显示文档结构
2.article 表示一块比较独立的内容或者主题内容，块级元素，比如blog的内容，报纸的文章
3.aside 表示article以外的内容，而且应该和article有一定的关系，块级元素
4.hgroup 表示一个文档、区段(section)的标题组合
5.header 表示页眉,页头
6.footer 表示页脚
7.nav 表示导航内容
8.figure 表示以相对独立的或外引的元素，如img video
9.figcaption 表示 figure内容的标题
```

```html
  <!-- hgroup 示例 -->
  <hgroup>
  <h1>文档主标题</h1>
  <h2>文档副标题</h2>
  </hgroup>

  <!-- figure 示例 -->
  <figure>
   <video src="ogg"></video>
   <figcaption>Example</figcaption>
  </figure>

  <figure>
   <img src="img" alt="Example image" />
   <figcaption>Example image</figcaption>
  </figure>
```
#### 结构性元素
```
1.p 表示段落。只能包含内联元素，不能包含块级元素;
2.div 本身无特殊含义，可用于布局。几乎可以包含任何元素;
3.br 表示换行符;
4.hr 表示水平分割线;
5.h1-h6 表示标题。其中 h1 用于表示当前页面最重要的内容的标题;
6.blockquote 表示引用，可以包含多个段落。请勿纯粹为了缩进而使用 blockquote，大部分浏览器默认将 blockquote 渲染为带有左右缩进;
7.pre 表示一段格式化好的文本;
```
#### 头部元素
```
1.title 每个页面必须有且仅有一个 title 元素;
2.base 可用场景：首页、频道等大部分链接都为新窗口打开的页面;
3.link link 用于引入 css 资源时，可省去 media(默认为all) 和 type(默认为text/css) 属性;
4.style type 默认为 text/css，可以省去;
5.script type 属性可以省去; 不赞成使用lang属性; 不要使用古老的<!– //–>这种hack脚本, 它用于阻止第一代浏览器（Netscape 1和Mosaic）将脚本显示成文字;
6.noscript 在用户代理不支持 JavaScript 的情况下提供说明;
```
#### 文本元素
```
1.a a 存在 href 属性时表示链接，无 href 属性但有 name 属性表示锚点;
2.em,strong em 表示句意强调，加与不加会引起语义变化，可用于表示不同的心情或语调; strong 表示重要性强调，可用于局部或全局，strong强调的是重要性，不会改变句意;
3.abbr 表示缩写;
4.sub,sup 主要用于数学和化学公式，sup还可用于脚注;
5.span 本身无特殊含义;
6.ins,del 分别表示从文档中增加(插入)和删除;
```

#### 媒体元素
```
img 请勿将img元素作为定位布局的工具，不要用他显示空白图片; 必要时给img元素增加alt属性;
```
#### 列表元素
```
1.dl 表示关联列表，dd是对dt的解释; dt和dd的对应关系比较随意：一个dt对应多个dd、多个dt对应一个dd、多个dt对应多个dd，都合法; 可用于名词/单词解释、日程列表、站点目录;
2.ul 表示无序列表;
3.ol 表示有序列表, 可用于排行榜等;
4.li 表示列表项，必须是ul/ol的子元素;
```
#### 表单元素
```
1.推荐使用 button 代替 input，但必须声明 type;
2.表单元素的 name 不能设定为 action, enctype, method, novalidate, target, submit 会导致表单提交混乱
```

#### 属性顺序

HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。
id 、 class 、 name 、data-* 、src 、type、 href 、title、alt;
class用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。如：

```html
<a id="..." class="..." data-modal="toggle" href="#">
 Example link
</a>
 <input class="form_control" type="text">
 <img src="..." alt="...">
```
#### 文件和目录命名约定
```
一律小写，必须是英文单词或者汉语拼音，以英语单词优先，多个单词以连字符 ( _ ) 连接。 只能出现小写引文字母，数字和连字符。
该命令规范适用于所有前端维护的内容和相关目录。(html, css, js, png, gif, jpg, ico)。

对于属性的定义，确保全部使用双引号，绝不要使用单引号；
不要省略可选的结束标签，如：</li>,</body>；
习惯性书写注释，方便日后维护；

```
#### 文件编码约定

`所有文件统一采用UTF-8无BOM编码。`（切记）

#### id和class命名约定
```
id 和 class 的命名基本原则: 内容优先，表现为辅。首先根据内容来命名，如:#header,#footer,.main_nav.如根据内容无法找到合适的命名，可以再结合表现进行命名，如：col_main, col_sub, col_extra,blue_box;
id 和 class 的名称一律小写，多个单词以连字符连接，如： `main_wrap`;
id 和 class 的名称只能出现，小写字母，数字和连字符( _ )(js钩子除外);
id 和 class 的名称尽量使用英文单词命名,如确实找不到合适的单词，可以使用拼音，如：zhidao_com;
在不影响语意的情况下，id 和 class 的名称 可以适当使用缩写，如: col, nav, hd, bd, fd( 缩写只用来表示结构，不允许写任何样式)。不要自造缩写。
id 和 class 的选择，如果只使用一次，使用id,如果使用多次使用class，如果需要和js交互，使用id,如果需要交互并且页面中有大量重复，请参见下一条。
对于作为js钩子的 id 和 class 命名规则为以"J_"开头(J,象形钩子的形状)，后面加上原应有的命名，在使用class的时候需要放在最前面。如:class="J_tab_content some_mod_content"。（注意：钩子，不允许在css中定义任何的样式效果）

```

