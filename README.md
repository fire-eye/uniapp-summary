# uniapp-summary
## 图标库搭建
* 帐号注册[iconfont](https://www.iconfont.cn/)
* 资源管理 - 我的项目 - 新建项目
* 搜索需要的图标库（收藏或加入购物车）
* 将加入购物车图标添加到需要的项目
* 进入项目管理点击生成代码
* 新建目录common，目录下新建文件l-icon.scss
```scss
@font-face {
  font-family: 'lfont';  /* project id 2308608 */
  src: url('//at.alicdn.com/t/font_2308608_11x80mmwqbfd.eot');
  src: url('//at.alicdn.com/t/font_2308608_11x80mmwqbfd.eot?#iefix') format('embedded-opentype'),
  url('//at.alicdn.com/t/font_2308608_11x80mmwqbfd.woff2') format('woff2'),
  url('//at.alicdn.com/t/font_2308608_11x80mmwqbfd.woff') format('woff'),
  url('//at.alicdn.com/t/font_2308608_11x80mmwqbfd.ttf') format('truetype'),
  url('//at.alicdn.com/t/font_2308608_11x80mmwqbfd.svg#lfont') format('svg');
}
/*添加class*/
[class*="lIcon"] {
	font-family: "lfont";
	font-size: inherit;
	font-style: normal;
} 
.lIcon-yourIcon:before { //yourIcon改成你要的图标名称
  content: "\e693";//图标Unicode(16进制)
}
```
* 在app.vue下style引入运用
``` html
<style lang="scss">
@import './common/l-icon.scss'
</style>
```
* 页面使用
``` html
<view class="lIcon-yourIcon"></view>
```

## Flex-弹性布局（Flexible Box）
### 容器属性
* **flex-direction: row | row-reverse | column | column-reverse;**  
属性决定主轴的方向（即项目的排列方向）。  
> row（默认值）：主轴为水平方向，起点在左端。  
> row-reverse：主轴为水平方向，起点在右端。  
> column：主轴为垂直方向，起点在上沿。  
> column-reverse：主轴为垂直方向，起点在下沿。  

* **flex-wrap: nowrap | wrap | wrap-reverse;**  
默认情况项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，进行换行。
> nowrap： 不换行  
> wrap: 换行，第一行在上方  
> wrap-reverse： 换行，第一行在下方  

* **flex-flow: [flex-direction] || [flex-wrap];**  
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。  

* **justify-content: flex-start | flex-end | center | space-between | space-around;**    
justify-content属性定义了项目在主轴上的对齐方式。  
> flex-start（默认值）：左对齐  
> flex-end：右对齐  
> center： 居中  
> space-between：两端对齐，项目之间的间隔都相等。  
> space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。  

* **align-items: flex-start | flex-end | center | baseline | stretch;**  
align-items属性定义项目在交叉轴上如何对齐。  
> flex-start：交叉轴的起点对齐。  
> flex-end：交叉轴的终点对齐。  
> center：交叉轴的中点对齐。  
> baseline: 项目的第一行文字的基线对齐。  
> stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。  

* **align-content: flex-start | flex-end | center | space-between | space-around | stretch;**  
属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。  
> flex-start：与交叉轴的起点对齐。  
> flex-end：与交叉轴的终点对齐。  
> center：与交叉轴的中点对齐。  
> space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。  
> space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。  
> stretch（默认值）：轴线占满整个交叉轴。  

### 项目属性
* **order: integer;**  
order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

* **flex-grow: [number]\; /* default 0 */**  
flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。 

* **flex-shrink: [number]; /* default 1 */**  
flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

* **flex-basis: [length] | auto; /* default auto */**  
在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

* **flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]**  
flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

* **align-self: auto | flex-start | flex-end | center | baseline | stretch**  
align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

[Flex布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)  
[Flex布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)  

