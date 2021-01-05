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

