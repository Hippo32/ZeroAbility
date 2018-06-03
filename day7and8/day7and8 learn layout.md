# 第七天到第八天，学习布局 #
## 课程目标 ##
学习布局的各种方式

## 阅读 ##
- [MDN 定位](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/%E5%AE%9A%E4%BD%8D)
- [MDN 定位实战](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Practical_positioning_examples)
- [MDN Flexbox](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox)
- [学习CSS布局](http://zh.learnlayout.com/)
- [CSS布局(三) 布局模型](http://www.cnblogs.com/chaixiaozhi/p/8481253.html)
- [CSS布局(四) Float](http://www.cnblogs.com/chaixiaozhi/p/8481778.html)
- [CSS布局(五) 网页布局方式](http://www.cnblogs.com/chaixiaozhi/p/8486647.html)
- [CSS布局(六) 对齐方式](http://www.cnblogs.com/chaixiaozhi/p/8490725.html)
- [七种实现左侧固定，右侧自适应两栏布局的方法](https://segmentfault.com/a/1190000010698609)
- [圣杯布局](http://alistapart.com/article/holygrail)
- [双飞翼布局](http://www.imooc.com/wenda/detail/254035)
- [圣杯布局和双飞翼布局](https://www.jianshu.com/p/f9bcddb0e8b4)
- [CSS深入理解流体特性和BFC特性下多栏自适应布局](http://www.zhangxinxu.com/wordpress/2015/02/css-deep-understand-flow-bfc-column-two-auto-layout/)

## 阅读笔记 ##
 **外边距折叠**：块级元素的上外边距和下外边距有时会合并（或折叠）为一个外边距，其大小取其中的最大者。注意浮动元素和绝对定位元素的外边距不会折叠。会发生外边距折叠的三种情况：

- 相邻元素之间：毗邻的两个元素之间的外边距会折叠（除非后一个元素需要清除之前的浮动）
- 父元素与其第一个或最后一个子元素之间：如果在父元素与其第一个子元素之间不存在边框、内边距、行内内容，也没有创建块格式化上下文、或者清除浮动将两者的margin-top分开；或者在父元素与其最后一个子元素之间不存在边框、内边距、行内内容、height、min-height、max-height将两者的marin-bottom分开，那么这两对外边距之间会产生折叠。此时子元素的外边距会“溢出”到父元素的外面。
- 空的块级元素

**`box-sizing`**：当你设置一个元素为`box-sizing: border-box;`时，此元素的内边距和边框不再会增加它的宽度。这个属性支持IE8+

## Position ##
2. 静态定位：每个元素获取的默认值——将元素放入它在文档布局流中的正常位置`position:static;`
3. 相对定位`position: relative;`：与静态定位相似，占据在正常的文档流中，可以修改它的最终位置，让它与页面上的其他元素重叠。修改元素的位置：使用`top`,`bottom`,`left`,`right`。在使用相对定位时，就算元素被偏移了，但是他仍然占据着它没偏移前的空间。
4. 绝对定位`position: absolute;`：绝对定位的元素不再存在于正常文档布局流中。
5. `z-index`：网页上有一个Z轴——一条从屏幕表面到你的脸的虚线。`z-index`值影响定位元素位于该轴上的位置——正值将它们移动到堆栈上方，负值将它们向下移动到堆栈中。z-index只接受无单位索引值。
6. 固定定位：`fixed`，不会保留它原本页面应有的空隙（脱离文档流）。与绝对定位的工作方式完全相同，只有一个区别——绝对定位固定元素是相对于`<html>`元素或其最近的定位祖先，而固定定位固定元素则是相对于浏览器视口本身。
7. `position: sticky;`相对位置和固定位置之间的混合，其允许定位的元件像它被相对定位一样动作，直到其滚动到某一阀值点，之后它变得固定。
8. 所谓的“单页应用”正在变得非常流行，尤其是移动网页UI，因为把一切的服务放在一个单独的文件上可以减少HTTP请求的数量来浏览所有内容，从而提高性能。


 `checkbox hack`技术：可以提供无JS的方法来控制一个元素，通过一个按钮的联系。

		// 核心代码，将表单元素的状态与其他标签绑定在一起
		input[type="checkbox"]:checked + aside {
	      
	    }

## 弹性盒子display: flex ##
1. 弹性盒子能方便且灵活实现的：
	- 在父内容里面垂直居中一个块内容
	- 使容器的所有子项占用等量的可用宽度/高度，而不管有多少宽度/高度可用
	- 使多列布局中的所有列采用相同的高度，即使它们包含的内容量不同
2. 假如你想设置行内元素为fleible box，也可以设置`display`属性的值为`inline-flex`
3. flex模型

	![](https://i.imgur.com/rRuBMc6.png)

	- **主轴（main axis）**是沿着flex元素放置的方向延伸的轴（比如页面上的横向的行、纵向的列）。该轴的开始和结束被称为**main start** 和 **mian end**。
	- **交叉轴（cross axis）**是垂直于flex元素放置方向的轴。该轴的开始和结束被称为**cross start** 和 **cross end**。
	- 设置了`display: flex`的父元素被称之为**flex容器（flex container）**。
	- 在flex容器中表现为柔性的盒子的元素被称之为**flex项（flex item）**

4. `flex-direction`：指定主轴的方向（弹性盒子子类放置的地方），默认值是`row`

		.box {
			flex-direction: row | row-reverse | column | column-reverse;
		}
5. `flex-wrap`：如果一条轴线排不下，如何换行

		.box {
			flex-wrap: nowrap (默认，不换行) |  wrap (换行，第一行在上方) | wrap-reverse (换行，第一行在下方)
6. `flex-flow`：是`flex-direction`属性和`flex-wrap`属性的简写
7. `flex: 1;`：这是一个无单位的比例值，表示每个flex项沿主轴的可用空间大小
8. `flex: 1 200px;`表示每个flex项将首先给出200px的可用空间，然后，剩余的可用空间将根据分配的比例共享。
9. flex：是一个可以指定最多三个不同值的缩写属性：
	- `flex-grow`：无单位比例，定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大，如果所有的`flex-grow`属性都为1，则它们将等分剩余空间。如果一个项目的`flex-grow`属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。
	- `flex-shrink`：无单位比例，定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。如果所有项目的`flex-shrink`属性都为1，当空间不足时，都将等比例缩小。如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小。负值对该属性无效。
	- `flex-basis`：定义了在分配多余空间之前，项目占据的主轴空间。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小。
10. `align-items`：定义项目在交叉轴上如何对齐
	- `stretch`：默认，是所有flex项沿着交叉轴的方向拉伸以填充父容器。如果父容器在交叉轴方向上没有固定宽度（即高度），则所有flex项将变得与最长的flex项一样长（即高度保持一致）。
	- `flex-start`：交叉轴的起点对齐
	- `flex-end`：交叉轴的终点对齐
	- `center`：交叉轴的中点对齐
	- `baseline`：项目的第一行文字的基线对齐
11. `align-self`：允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承`align-items`属性，如果没有父元素，则等同于`stretch`
12. `justify-content`：定义项目在主轴上的对齐方式
	- `flex-start`：默认值，左对齐
	- `flex-end`：右对齐
	- `center`：居中
	- `space-between`：两端对齐，项目之间的间隔都相等，不会在两端留空间。
	- `space-around`：每个项目两侧的间隔相等。会在两端留空间。
13. `order`：定义项目的排序顺序，数值越小，排列越靠前，默认为0。相同order值的flex项按源顺序显示。
14. 兼容性：IE10+

## Display ##
1. `block`：块级元素
2. `inline`：行内元素
3. `none`：一些特殊元素的默认display值是它，例如`script`。`display: none`通常被JS用来在不删除元素的情况下隐藏或显示元素。它和`visibility`属性不一样。把`display`设置成`none`元素不会占据它本来应该显示的空间，但是设置成`visibility: hidden`还会占据空间
4. `inline-block`
	- `vertical-align`属性会影响到`inline-block`元素，你可能会把他的值设置为`top`
	- 你需要设置每一列的宽度
	- 如果HTML源代码中元素之间有空格，那么列与列之间会产生空隙

## Float ##
1. 清除浮动
	- `overflow: auto;`想支持IE6，加上`zoom: 1;`
	- `<br clear = "all"/>`
	- 为父元素添加`overflow: hidden;`：这样父元素就有高度了，父元素的高度便不会被破坏。
	- `clear: both;`：通过在所有浮动元素下方添加一个`clear: both;`的元素，可以消除float的破坏性
	- 浮动父元素
	- `clearfix`：定义一个`.clearfix`类，然后对float元素的父元素应用这一样式即可

			.clearfix:after {
				content: '';
				display: block;
				clear: both;
			}
			.clearfix {
				*zoom: 1;
			}
2. float的特性
	- 破坏性：被设置了float的元素会脱离文档流
	- 包裹性：div设置了float之后，其宽度会自动调整为包裹住内容宽度，而不是撑满整个父容器。
	- 清空格：根本原因是由于float会导致节点脱离文档流结构。它都不属于文档流结构了，那么它身边的什么换行、空格就都和它没关系的，它就尽量的往一边去靠拢，能靠多近就靠多近，这就是请空格的本质
3. 浮动的应用
	- 设置float属性后，元素实际上会inline-block块状化
	- 可以去掉排列间的空格
	- 实现文字的环绕效果


## BFC ##
BFC全称“Block Formatting Context”，中文为“块级格式化上下文”。BFC元素特性表现原则就是，内部子元素再怎么翻江倒海，翻云覆雨都不会影响外部的元素。

什么时候会触发BFC呢？常见的如下：

- `float`的值不为`none`。
- `overflow`的值为`auto`，`scroll`或`hidden`。
- `display`的值为`table-cell`，`table-caption`，`inline-block`中的任何一个。
- `position`的值不为`relative`和`static`。

## 媒体查询 ##
“响应式设计”是一种让网站针对不同的浏览器和设备“呈现”不同显示效果的策略

媒体查询就是做此事所需的最强大的工具。

## 水平居中 ##
1. 块级元素
	- 定宽
			
			margin： 0 auto;
	唯一的问题是：当浏览器窗口比元素的宽度还要窄时，浏览器会显示一个水平滚动条来容纳页面
	<br>改进方案：使用`max-width`替代`width`可以使浏览器更好地处理小窗口的情况。所有的主流浏览器包括IE7+在内都支持`max-width`
	- 不定宽
		1.  加入<font color="blue">table</font>标签：利用table标签的长度自适应型——即不定义其长度也不默认父元素body的长度（table其长度根据其内文本长度决定），因此可以看做是一个<font color="red">定宽度块元素</font>，然后再利用定宽度块状居中的<font color="red">margin</font>的方法，使其水平居中。
			- 为需要设置的居中元素外面加入一个table标签（包括`<tbody>`、`<tr>`、`<td>`）。
			- 为这个table设置“左右margin居中”（这个和定宽块状元素的方法一样）。 
		2.  设置<font color="blue">display:inline</font>：改变块级元素的display为inline类型（设置为行内元素显示），然后使用`text-align:center`来实现居中效果。
		-  设置<font color="blue">position:relative</font>和<font color="blue">left:50%</font>：利用相对定位的方式，将元素向左偏移50%，即达到居中的目的
2. 行内元素：如果被设置元素为文本、图片等**行内元素时**，在父元素中设置`text-align: center;`实现行内元素水平居中

## 垂直居中设置 ##
- **父元素高度确定的单行文本**<p>通过设置父元素的height和line-height高度一致来实现的。（height：该元素的高度，line-height：顾名思义，行高（行间距），指在文本中，行与行之间的基线间的距离）。</p><p>弊端：当文字内容的长度大于块的宽时，就有内容脱离了块。</p>
- **父元素高度确定的多行文本**
	- 方法一：使用插入<font color="blue">table</font>（包括tbody、tr、td）标签，同时设置<font color="blue">vertical:middle</font>
	- 方法二：在chrome、firefox及IE8以上的浏览器下可以设置块级元素的<font color="blue">display为table-cell</font>（设置为表格单元显示），激活vertical-align属性，但注意IE6、7并不支持这个样式，兼容性比较差。
- **不知道自己高度和父容器高度的情况**，利用<font color="red">绝对定位只需要以下三行：</font>

	    parentElement {
    		position: reletive;
    	}
    	childElement {
    		position: absolute;
    		top: 50%;
    		transform: translateY(-50%);
    	}


- 若父容器下只有一个元素，且父元素设置了高度，则只需要使用相对定位即可

        prentElement {
    		height: xxx;
    	}
    
    	childElement {
    		position: reletive;
    		top: 50%;
    		transform: translateY(-50%);
    	}

- 不考虑兼容老式浏览器的话，用Flex布局简单直观一劳永逸：

	    parentElement{
	    	display:flex;/*Flex布局*/
	    	display: -webkit-flex; /* Safari */
	    	align-items:center;/*指定垂直居中*/
	    }
## 水平垂直居中 ##
1. 单行文本
		
		text-align: center;
		line-height: 100px;
		
2. 子元素是`div`

		<div class="parent">
	        <div class="child">
	          Smile
	        </div>
	    </div>

		// text-align + vertical-align

		.parent {
	        border: 1px solid black;
	        display: table-cell;
	        text-align: center;
	        vertical-align: middle;
	        height: 100px;
	        width: 200px;
	      }
	      .child {
	        display: inline-block;
	      }

		// 相对 + 绝对定位
		.parent {
			position: relative;
			width: 200px;
			height: 100px;
		}
		.child {
			position: absolute;
			top: 0;
			left: 0;
			right: 0;
			bottom: 0;
			height: 50px;
			width: 80px;
			margin: auto;
		}
3. 子元素是图像：可不是用`table-cell`，而是其父元素用行高代替高度，且`font-size: 0;`。子元素本身设置`vertical-align: middle;`
4. 如果要居中的<font color="blue">元素的宽/高是不变的或者说是确定的</font>，比如width/height=100px，那么<font color="red">设置absolute的top/left=50%，然后margin-left/margin-top=-50px</font>即可
5. 如果要居中的元素的宽/高是不确定的，这时margin负值就不能使用具体的px了，可以使用百分比。但由于margin的百分比都是相对于包含块的宽度，所以这里限制了只能设置宽高相同的居中元素。包含块的宽度如何获得呢？利用absolute的包裹性，在需要居中的元素外面套一个空的`<div>`元素即可。或者：

		.parent {
			position: relative;
		}
		.child {
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
		}
6. 如果可以使用flexbox

		.parent {
			display: flex;
			justify-content: center;
			align-items: center;
		}

7. 如果可以使用grid

		body, html {
			height: 100%;
			display: grid;
		}
		span { /* thing to center */
			margin: auto;
		}

## 布局模型 ##
1. 流动模型（Flow）默认
2. 浮动模型（Float）
3. 层模型（Layer）
	- 相对定位
	- 绝对定位
	- 固定定位

## 常见的布局 ##
1. **一列布局**：一般都是固定的宽高，设置`margin: 0 auto`来水平居中，用于界面显著标题的展示等
2. **两列布局**：左侧固定，右侧自适应。常用的宽度自适应的方法通常是利用了`block`水平的元素宽度能随父容器调节的流动特性。另外一种思路是利用CSS中的`calc()`方法来动态设定宽度。还有一种思路是，利用CSS中的新型布局`flex layout`与`grid layout`。

	基本的HTML布局

		<div class = "wrapper" id = "wrapper">
			<div class = "left">
				左边固定宽度，高度不固定。高度可能很小，也可能很大。
			</div>
			<div class = "right">
				这里的内容可能比左侧高，也可能比左侧低。宽度需要自适应
			</div>
		</div>
	基本的样式：两个盒子相距20px，左侧盒子宽120px，右侧盒子宽度自适应

	- **双`inline-block`方案**：通过`width: calc(100% - 140px)`来动态计算右侧盒子的宽度。需要知道左侧盒子的宽度，两个盒子的距离，还要设置各个元素的`box-sizing`；需要消除空格字符的影响；需要设置`vertical-align: top;`满足顶端对齐

			.wrapper-inline-block {
			    box-sizing: content-box;
			    font-size: 0;    // 消除空格的影响
			}
			
			.wrapper-inline-block .left,
			.wrapper-inline-block .right {
			    display: inline-block;
			    vertical-align: top;    // 顶端对齐
			    font-size: 14px;
			    box-sizing: border-box;
			}
			
			.wrapper-inline-block .right {
			    width: calc(100% - 140px);
			}
	- **双`float`方案**：浮动的`block`元素在有空间的情况下会依次紧贴，排列在一行

			.wrapper-double-float {
			    overflow: auto;        // 清除浮动
			    box-sizing: content-box;
			}
			
			.wrapper-double-float .left,
			.wrapper-double-float .right {
			    float: left;
			    box-sizing: border-box;
			}
			
			.wrapper-double-float .right {
			    width: calc(100% - 140px);
			}

	- **`float + margin-left`方案**：`block`级别的元素会认为浮动的元素不存在，但是`inline`级别的元素能识别到浮动的元素。这样，`block`级别的元素就可以和浮动的元素同处在一行了。

			.wrapper-float {
			    overflow: hidden;        // 清除浮动
			}
			
			.wrapper-float .left {
			    float: left;
			}
			
			.wrapper-float .right {
			    margin-left: 150px;
			}
	- **使用`absolute + margin-left`方法**：使用了绝对定位，若是用在某个div中，需要更改父容器的`position`；没有清除浮动的方法，若左侧盒子高于右侧盒子，就会超出父容器的高度。因此只能通过设置父容器的`min-height`来放置这种情况

			.wrapper-absolute .left {
			    position: absolute;
			}
			
			.wrapper-absolute .right {
			    margin-left: 150px;
			}
	- **使用`float + BFC`方法**：左侧浮动，右侧盒子通过`overflow: auto;`形成了BFC，因此右侧盒子不会与浮动的元素重叠，父元素需要清除浮动

			.wrapper-float-bfc {
			    overflow: auto;
			}
			
			.wrapper-float-bfc .left {
			    float: left;
			    margin-right: 20px;
			}
			
			.wrapper-float-bfc .right {
			    margin-left: 0;
			    overflow: auto;
			}
	- **`flex`方案**：可以说是最好的方案了，`flex`容器的一个默认属性值：`align-items: stretch;`，这个属性导致了列等高的效果，为了让两个盒子高度自动，需要设置`align-items: flex-start;`

			.wrapper-flex {
			    display: flex;
			    align-items: flex-start;
			}
			
			.wrapper-flex .left {
			    flex: 0 0 auto;
			}
			
			.wrapper-flex .right {
			    flex: 1 1 auto;
			}
	- **`grid`方案**：可以满足需且，但这并不是它发挥用处的真正地方。注意：`grid`布局也有列等高的默认效果，需要设置`align-items: start;`

			.wrapper-grid {
			    display: grid;
			    grid-template-columns: 120px 1fr;
			    align-items: start;
			}
			
			.wrapper-grid .left,
			.wrapper-grid .right {
			    box-sizing: border-box;
			}
			
			.wrapper-grid .left {
			    grid-column: 1;
			}
			
			.wrapper-grid .right {
			    grid-column: 2;
			}
	- 极限情况：
		- 动态计算宽度的情况：两种方案：双`inline-block`方案和双`float`方案。宽度极限小时，右侧的div宽度会非常小，由于遵循流动布局，所以右侧div会移动到下一行
		- 动态计算右侧`margin-left`的情况：两种方案：`float + margin-left`方案和`absolute + margin-left`方案。宽度极限小时，由于右侧的div忽略了文档流中左侧div的存在，所以其依旧会存在于这一行，并被隐藏
		- `float + BFC`方案的情况下：由于BFC与float的特殊关系，右侧div在宽度减小到最小后，也会掉落到下一行
		- `flex`和`grid`情况：默认两种布局方式都不会放下div移动到下一行，不过`flex`布局可以通过`flex-flow: wrap;`来设置多余的div移动到下一行。`grid`布局暂不支持。
3. **三列布局**：两侧定宽中间自适应
	- 首先设置父级元素的宽度，可以左左右设置浮动，然后中间设置margin调整间距，也可以都设置左浮动，设置margin，调整间距。同样注意清除浮动的影响。
	- **绝对定位法**：左右两栏采用绝对定位，分别固定于页面的左右两侧，中间的主体栏用左右`margin`值撑开距离。

			代码：
		
			// HTML
			<body>
				<div id="left"></div>
				<div id="center"></div>
				<div id="right"></div>
			</body>
		
			// CSS
			<style type="text/css">
				* { margin:0; height:100%;}
				#left,#right {
					position: absolute;
					top: 0;
					width: 200px;
					height: 100%;
				}
				#left {
					left: 0;
					background: red;
				}
				#right {
					right: 0;
					background: blue;
				}
				#main {
					margin: 0 210px;
					background: yellow;
					height: 100%;
				}
		这里的左中右三个`div`的顺序是可以任意调整的。

		此方法的优点是，理解容易，上手简单，受内部元素影响而破坏布局的概率低，即使比较经得起折腾。
		<br/>缺点在于：如果中间栏含有最小宽度限制，或是含有宽度的内部元素，当浏览器小到一定程度，会发生层重叠的情况，然而，一般情况下，除非用户显示器分辨率宽度`>=1600`像素，否则用户不会把浏览器缩小到1000像素以下的。
	- **margin负值**：中间的主体要使用双层标签。外层`div`宽度`100%`显示，并且浮动，内层`div`为真正的主体内容，含有左右20像素的`margin`值。左栏与右栏都是采用`margin`负值定位的，左栏左浮动，`margin-left`为`-100%`，由于前面的div宽度为100%与浏览器，所以这里的`-100%``margin`值正好使左栏`div`定位到了页面的左侧；右侧栏也是左浮动，其`margin-left`也是负值，大小为其本身的宽度即200像素。

		代码示例：
		
			<div class="three">
				<div class="main">
					<div class="center">center</div>
				</div>
				<div class="left">left</div>
				
				<div class="right">right</div>
			</div>
		
			.left{
				margin-left: -100%;
				float: left;
				width: 200px;
				height: 100%;
				background: blue;
			}
			.right {
				float: left;
				margin-left: -200px;
				width: 200px;
				height: 100%;
				background: yellow;
			}
			.main {
				width: 100%;
				float: left;
			}
			.center {
				background-color: red;
				margin: 0 20px;
			}

		需要注意的是几个div的顺序，无论是左浮动还是右浮动，先是主体部分div，这是肯定的，至于左右两栏谁先谁后，都无所谓。

		此方法的优点：三栏相互关联，可谓真正意义上的自适应，有一定的抗性——布局不易受内部影响。缺点在于：相对比较难理解些，上手不容易，代码相对复杂。出现百分比宽度，过多的负值定位，如果出现布局的bug，排查不易。
	- **自身浮动法**：左栏左浮动，右栏右浮动，主体直接放后面，就实现了自适应。

			<div class="left"></div>
			<div class="right"></div>
			<div class="main"></div>
		
			.main {
				height: 100%;
				margin: 0 20px;
				background: red;
			}
			.left {
				width: 200px;
				height: 100%;
				background: yellow;
				float: left;
			}
			.right {
				width: 200px;
				height: 100%;
				background: blue;
				float: right;
			}

		这里三个div标签的顺序的关键是要把主体div放在最后，左右两栏div顺序任意。

		此方法的优点是：代码足够简洁与高效。不足在于：中间主体存在克星，clear:both属性。如果要使用此方法，需避免明显的clear样式。
4. **混合布局**：在一列布局的基础上，保留top和foot部分，将中间的main部分改造成两列或三列布局，小的模块可以再逐级同理划分
5. **圣杯布局**：两边的盒子宽度固定，中间盒子自适应。写结构的时候要注意，父元素的三栏务必先写中间盒子。因为中间盒子要被优先渲染，并且设置自适应，也就是`width: 100%;`。一开始中间的盒子在上面width为100%，左右两个盒子被挤下来，要让左边的盒子上去，需要设置其左边距为负的中间盒子的宽度，也就是`.left {margin-left: -100%;}`。要让右边的盒子上去，需要设置其左边距为负的自己的宽度，也就是`.right {margin-left: -180px;}`，这样右盒子才可以在一行的最右边显示出自己。但是这样左右盒子会把中间的盒子挡住一部分，所以为了让中间自适应的盒子安全显示，利用父级元素设置左右内边距的值，把父级的三个子盒子往中间挤`.container { padding: 0 200px; }`，接着给左右两个盒子加一个定位，加了定位之后左右两个盒子就可以设置left和right值。`.left {position: relative; left: -200px;} .right {position: relative; right: -210px;}`PS：数值可以随便写的，按照实际情况修改。

		<div id="header"></div>
		<div id="container">
  			<div id="center" class="column"></div>
  			<div id="left" class="column"></div>
  			<div id="right" class="column"></div>
		</div>
		<div id="footer"></div>

		body {
		  min-width: 630px;      /* 2x (LC fullwidth + CC padding) + RC fullwidth */
		}
		#container {
		  padding-left: 200px;   /* LC fullwidth */
		  padding-right: 190px;  /* RC fullwidth + CC padding */
		}
		#container .column {
		  position: relative;
		  float: left;
		}
		#center {
		  padding: 10px 20px;    /* CC padding */
		  width: 100%;
		}
		#left {
		  width: 180px;          /* LC width */
		  padding: 0 10px;       /* LC padding */
		  right: 240px;          /* LC fullwidth + CC padding */
		  margin-left: -100%;
		}
		#right {
		  width: 130px;          /* RC width */
		  padding: 0 10px;       /* RC padding */
		  margin-right: -190px;  /* RC fullwidth + CC padding */
		}
		#footer {
		  clear: both;
		}/*** IE Fix ***/
		* html #left {
		  left: 150px;           /* RC fullwidth */
		}
- **双飞翼布局**：两边的盒子宽度固定，中间盒子自适应，源于淘宝的UED。圣杯布局和双飞翼布局解决问题的方案在前一半是相同，也就是三栏全部float浮动，但左右两栏加上负margin让其跟中间栏div并排，以形成三栏布局。不同在于解决“中间栏div内容不被遮挡”的问题的思路不一样。
        
		<div id="container">        
			<div class="main">
				<div class="content">main</div>
			</div>      
			<div class="left">left</div>        
			<div class="right">right</div>    
		</div>   

		.left, .main, .right {
			float: left;
			min-height: 130px;
		}
		.left {
			background: green;
			width: 200px;
			margin-left: -100%;
		}
		.main {
			background: blue;
			width: 100%；
		}
		.right {
			background: red;
			width: 300px;	
			margin-left: -300px;
		}
		.content {
			margin: 0 300px 0 200px;
		}
## z-index ##
`z-index`属性使用于定位元素（position属性值为relative或absolute或fixed的对象），用来确定定位元素在垂直于显示屏方向（称为z轴）上的层叠顺序，也就是说如果元素是没有定位的，对其设置的z-index会是无效的。

如果父元素z-index有效，那么子元素无论是否设置z-index都和父元素一致，会在父元素上方
<br>如果父元素z-index失效（未定位或者使用默认值），那么定位子元素的z-index设置生效。

如果两个元素都没有设置z-index，使用默认值，一个定位一个没有定位，那么定位元素覆盖未定位元素。
<br>如果两个元素都没有定位发生位置重合现象或者两个都已定位元素且z-index相同发生位置重合现象，那么按文档流顺序，后面的覆盖前面的。
	

## calc() ##
`calc()`：用于动态计算长度值

- 使用`+`、`-`、`*`和`/`四则运算
- 可以使用百分比、px、em、rem等单位
- 可以混合使用各种单位进行计算
- 表达式中有`+`和`-`时，其前后必须要有空格
- 表达式中有`*`和`/`时，其前后可以没有空格，但建议留有空格

`calc()`能让你给元素做计算，你可以给一个div元素，使用百分比、em、px和rem单位制计算出其宽度或者高度，比如说`width: calc(50% + 2em)`，这样一来就不用考虑DIV的宽度值到底是多少，而把这个烦人的任务交由浏览器去计算。

浏览器对calc()的兼容性还算不错，在IE9+、Firefox4.0+、Chrome19+、Safari6+都得到较好支持

## 验证 ##
- Position相关概念及使用Postion进行布局的场景和方法
- Flexbox相关概念及使用Flexobx进行布局的场景和方法
- 掌握常用的两栏、三栏布局的各种方式


github 源码：[https://github.com/Hippo32/ZeroAbility/tree/master/day7and8](https://github.com/Hippo32/ZeroAbility/tree/master/day7and8)

github demo：[https://hippo32.github.io/ZeroAbility/day7and8/day8.html](https://hippo32.github.io/ZeroAbility/day7and8/day8.html)

