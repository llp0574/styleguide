# CSS 规范 <!-- omit in toc -->

- [1. 介绍](#1-%E4%BB%8B%E7%BB%8D)
- [2. CSS 代码规范细则](#2-css-%E4%BB%A3%E7%A0%81%E8%A7%84%E8%8C%83%E7%BB%86%E5%88%99)
  - [文件命名](#%E6%96%87%E4%BB%B6%E5%91%BD%E5%90%8D)
  - [代码风格](#%E4%BB%A3%E7%A0%81%E9%A3%8E%E6%A0%BC)
    - [代码易读性](#%E4%BB%A3%E7%A0%81%E6%98%93%E8%AF%BB%E6%80%A7)
    - [类名定义](#%E7%B1%BB%E5%90%8D%E5%AE%9A%E4%B9%89)
    - [选择器](#%E9%80%89%E6%8B%A9%E5%99%A8)
    - [权重优先级相关](#%E6%9D%83%E9%87%8D%E4%BC%98%E5%85%88%E7%BA%A7%E7%9B%B8%E5%85%B3)
    - [注释](#%E6%B3%A8%E9%87%8A)
    - [属性书写顺序](#%E5%B1%9E%E6%80%A7%E4%B9%A6%E5%86%99%E9%A1%BA%E5%BA%8F)
    - [属性值引号](#%E5%B1%9E%E6%80%A7%E5%80%BC%E5%BC%95%E5%8F%B7)
    - [使用缩写属性](#%E4%BD%BF%E7%94%A8%E7%BC%A9%E5%86%99%E5%B1%9E%E6%80%A7)
    - [嵌套层级](#%E5%B5%8C%E5%A5%97%E5%B1%82%E7%BA%A7)
    - [数值 `0` 相关](#%E6%95%B0%E5%80%BC-0-%E7%9B%B8%E5%85%B3)
    - [url()](#url)
    - [颜色相关](#%E9%A2%9C%E8%89%B2%E7%9B%B8%E5%85%B3)
    - [文本相关](#%E6%96%87%E6%9C%AC%E7%9B%B8%E5%85%B3)
    - [动画相关](#%E5%8A%A8%E7%94%BB%E7%9B%B8%E5%85%B3)
    - [CSS3浏览器私有前缀写法](#css3%E6%B5%8F%E8%A7%88%E5%99%A8%E7%A7%81%E6%9C%89%E5%89%8D%E7%BC%80%E5%86%99%E6%B3%95)
    - [JavaScript 钩子](#javascript-%E9%92%A9%E5%AD%90)
- [3. Less 规范细则](#3-less-%E8%A7%84%E8%8C%83%E7%BB%86%E5%88%99)
    - [代码组织顺序](#%E4%BB%A3%E7%A0%81%E7%BB%84%E7%BB%87%E9%A1%BA%E5%BA%8F)
    - [`@import` 语句](#import-%E8%AF%AD%E5%8F%A5)
    - [混合（Mixin）](#%E6%B7%B7%E5%90%88mixin)

## 1. 介绍

这份规范的目的是提升开发效率，使 CSS 相关的文件和代码风格保持一致，更容易被理解和维护，同时也便于新入职同事更容易开始工作。

规范将针对 CSS 和 less 进行设计。

由于现在各个项目的代码架构差异及历史遗留等原因，部分细节还请根据项目自身情况进行决策，待规范定义经讨论修改完善后，再考虑添加 stylelint。

## 2. CSS 代码规范细则

### 文件命名
确保文件命名总是以字母开头而不是数字，且字母一律小写，以下划线连接且不带其他标点符号。

示例：
```
index.less
index_list.less
index_detail.less
```

### 代码风格

#### 代码易读性
* 使用 **2** 个空格作为一个缩进层级。
* 在一个规则声明中应用了多个选择器时，每个选择器独占一行
* 在规则声明的左大括号 `{` 前加上一个空格
* 在属性的冒号 `:` 后面加上一个空格，前面不加空格
* 规则声明的右大括号 `}` 独占一行
* 规则声明之间用空行分隔开

示例：
```css
.avatar {
  border-radius: 50%;
  border: 2px solid #fff;
}

.one,
.selector,
.per-line {
  ...
}
```

#### 类名定义

使用破折号代替驼峰法和下划线

示例：
```css
.first-line {
  ...
}
```

常用类名推荐

| ClassName | 含义 |
| ------------ | ------------- | 
| about | 关于 |
| account | 账户 |
| arrow | 箭头图标 |
| article | 文章 |
| aside | 边栏 |
| audio | 音频 |
| avatar | 头像 |
| bg,background | 背景 |
| bar | 栏（工具类）|
| branding | 品牌化 |
| crumb,breadcrumbs | 面包屑 |
| btn,button | 按钮 | 
| caption | 标题，说明 |
| category | 分类 |
| chart | 图表 |
| clearfix | 清除浮动 |
| close | 关闭 |
| col,column | 列 |
| comment | 评论 | 
| community | 社区 |
| container | 容器 |
| content | 内容 | 
| copyright | 版权 | 
| current | 当前态，选中态 | 
| default | 默认 | 
| description | 描述 | 
| details | 细节 | 
| disabled | 不可用 | 
| entry | 文章，博文 | 
| error | 错误 | 
| even | 偶数，常用于多行列表或表格中 | 
| fail | 失败（提示） | 
| feature | 专题 | 
| fewer | 收起 | 
| field | 用于表单的输入区域 | 
| figure | 图 | 
| filter | 筛选 | 
| first | 第一个，常用于列表中 | 
| footer | 页脚 | 
| forum | 论坛 | 
| gallery | 画廊 | 
| group | 模块，清除浮动 | 
| header | 页头 | 
| help | 帮助 | 
| hide | 隐藏 | 
| hightlight | 高亮 | 
| home | 主页 | 
| icon | 图标 | 
| info,information | 信息 | 
| last | 最后一个，常用于列表中 | 
| links | 链接 | 
| login | 登录 | 
| logout | 退出 | 
| logo | 标志 | 
| main | 主体 | 
| menu | 菜单 | 
| meta | 作者、更新时间等信息栏，一般位于标题之下 | 
| module | 模块 | 
| more | 更多（展开） | 
| msg,message | 消息 | 
| nav,navigation | 导航 | 
| next | 下一页 | 
| nub | 小块 | 
| odd | 奇数，常用于多行列表或表格中 | 
| off | 鼠标离开 | 
| on | 鼠标移过 | 
| output | 输出 | 
| pagination | 分页 | 
| pop,popup | 弹窗 | 
| preview | 预览 | 
| previous | 上一页 | 
| primary | 主要 | 
| progress | 进度条 | 
| promotion | 促销 | 
| rcommd,recommendations | 推荐 | 
| reg,register | 注册 | 
| save | 保存 | 
| search | 搜索 | 
| secondary | 次要 | 
| section | 区块 | 
| selected | 已选 | 
| share | 分享 | 
| show | 显示 | 
| sidebar | 边栏，侧栏 | 
| slide | 幻灯片，图片切换 | 
| sort | 排序 | 
| sub | 次级的，子级的 | 
| submit | 提交 | 
| subscribe | 订阅 | 
| subtitle | 副标题 | 
| success | 成功（提示） | 
| summary | 摘要 | 
| tab | 标签页 | 
| table | 表格 | 
| txt,text | 文本 | 
| thumbnail | 缩略图 | 
| time | 时间 | 
| tips | 提示 | 
| title | 标题 | 
| video | 视频 | 
| wrap | 容器，包，一般用于最外层 | 
| wrapper | 容器，包，一般用于最外层 | 

**注意：** ad、banner、gg、guanggao 等有机会和广告挂勾的字眼不建议直接用来做类名，因为有些浏览器插件（Chrome 的广告拦截插件等）会直接过滤这些类名。

#### 选择器
* 少用 `*`，少用标签选择器
* 避免使用属性选择器
* 按需使用 `ID` 作为选择器

CSS的渲染方式是“从右往左”渲染的，就拿 `.header a {}` 举例，引擎会先渲染页面上所有的 a 标签，再去寻找类名为 header 的元素。

id 在页面是唯一的，不能多次使用，类名选择器可以重复使用，而且 id 一般还会用作 js 选择器，有时因为 js 的原因改动，那么对应的 css 也会失效，所以 id 选择器不到万不得已尽量不在 css 里使用。

示例：
```css
* {
  /* 会去遍历所有标签，影响性能 */
  padding:0 .3rem;
}

.header a {
  /* 同样会去遍历所有<a>标签，影响性能 */
  font-size:0.28rem;
}
```

#### 权重优先级相关

> CSS 权重优先级：!important > 内联 > # > . > 属性选择器 input[name=''] > 标签选择器 input > *
> 
> CSS 执行顺序：行内 > 内联 > 外部引用

除去某些极特殊的情况，尽量不要使用 `!important`。

`!important` 的存在会给后期维护以及多人协作带来噩梦般的影响。
当存在的样式覆盖层叠时，如果你发现新定义的一个样式无法覆盖一个旧的样式，只有加上 `!important` 才能生效时，是因为你新定义的选择器的优先级不够旧样式选择器的优先级高。所以，合理的书写新样式选择器，是完全可以规避一些看似需要使用 `!important` 的情况的。

#### 注释
* 使用行注释代替块注释
* 注释独占一行，避免行末注释
* 给没有自注释的代码写上详细说明，比如：
  - 为什么用到了 z-index
  - 兼容性处理或者针对特定浏览器的 hack

示例：
```css
/* 我是注释1 */
.selector {
  /* 我是注释2 */
  z-index: 1;
  /* 我是注释3 */
  color: #333;
}
```

#### 属性书写顺序

1. 布局方式、位置（`position`, `top`, `right`, `z-index`, `display`, `float`等）
2. 尺寸（`width`, `height`, `padding`, `margin`）
3. 文本相关（`font`, `line-height`, `letter-spacing`, `color`, `text-align`等）
4. 视觉相关（`background`, `border`, `transition`等）

另外，如果包含 `content` 属性，应放在最前面。

示例：
```css
.selector {
  z-index: -1;
  display: inline-block;
  font-size: 1.5em;
  color: #333;
  background-color: #f1f1f1;
}
```

#### 属性值引号
css 属性值需要用到引号时，统一使用单引号。

示例：
```css
.selector {
  font-family: 'Hiragino Sans GB';
}
```

#### 使用缩写属性

CSS 有些属性是可以缩写的，如 `padding`、`margin` 等，这些属性中，如果属性值只有 1 个或 2 个，则应该分开写，2 个以上的话，应使用合并的缩写形式。

示例：
```css
.selector {
  border-top: 0;
  padding: 0 10px 5px;
}
```

#### 嵌套层级

选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确。

示例：
```css
/* 推荐 */
.username input {
  ...
}
.comment .avatar {
  ...
}

/* 不推荐 */
.page .header .login .username input {
  ...
}
.comment div * {
  ...
}
```

#### 数值 `0` 相关
* 当数值为 0 - 1 之间的小数时，省略整数部分的 `0`。
* 长度为 `0` 时需省略单位。

示例：
```css
panel {
  color: rgba(255, 255, 255, .5);
  opacity: .8;
  padding: 0 5px;
}
```

#### url()
* `url()` 函数中的路径不加引号
* `url()` 函数中的绝对路径可省去协议名

示例：
```css
body {
  background-image: url(//baidu.com/img/bg.png); no-repeat 0 0;
}
```

#### 颜色相关
* 颜色值可缩写时，尽量采用缩写
* 颜色值不使用命名色值
* 颜色值中的英文字符采用小写

示例：
```css
.selector {
  background-color: #aca;
  color: #90ee90;
}
```

#### 文本相关
* `font-weight` 属性使用数值方式描述
* `line-height` 在定义文本段落时，应使用数值

字重如果使用 `bold`、`lighter` 之类的值会涉及到继承计算的问题，直接使用数值能更明确，一般情况下 400 等价 `normal`，700 等价 `bold`。

将 `line-height` 设置为数值，浏览器会基于当前元素设置的 `font-size` 进行再次计算。在不同字号的文本段落组合中，能达到较为舒适的行间间隔效果，避免在每个设置了 `font-size` 的段落都去设置 `line-height`。

但当 `line-height` 用于控制垂直居中时，还是应该设置成与容器高度一致。

示例：
```css
.selector {
  font-weight: 700;
  line-height: 1.5;
}
```

#### 动画相关
* 使用 `transition` 时应指定 `transition-property`

示例：
```css
/* 推荐 */
.box {
  transition: color 1s, border-color 1s;
}

/* 不推荐 */
.box {
  transition: all 1s;
}
```

* 尽可能在浏览器能高效实现的属性上添加过渡和动画，在可能的情况下应选择这样四种变换：

  - `transform: translate(tx, ty)`
  - `transform: scale(n)`
  - `transform: rotate(ndeg);`
  - `opacity: 0..1;`

典型的，可以使用 translate 来代替 left 作为动画属性。
示例：
```css
/* 推荐 */
.box {
  transition: transform 1s;
}
.box:hover {
  /* 向右移动20px */
  transform: translate(20px);
}

/* 不推荐 */
.box {
  left: 0;
  transition: left 1s;
}
.box:hover {
  /* 向右移动20px */
  left: 20px;
}
``` 

#### CSS3浏览器私有前缀写法
CSS3 浏览器私有前缀在前，标准前缀在后。

示例：
```css
.selector {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -o-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```

#### JavaScript 钩子
避免在 CSS 和 JavaScript 中绑定相同的类。否则开发者在重构时通常会出现以下情况：轻则浪费时间在对照查找每个要改变的类，重则因为害怕破坏功能而不敢作出更改。

推荐在创建用于特定 JavaScript 的类名时，添加 `.js-` 前缀。

示例：
```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

## 3. Less 规范细则

#### 代码组织顺序

代码按以下顺序组织：

1. @import
2. 变量声明
3. 样式声明

```less
@import "mixins/size.less";

@default-text-color: #333;

.page {
  width: 960px;
  margin: 0 auto;
}
```
#### `@import` 语句

`@import` 语句引用的文件需要写在一对引号内，.less 后缀不得省略。引号使用 ' 和 " 均可，但在同一项目内需统一。

示例：
```css
/* 不推荐 */
@import "mixins/size";
@import 'mixins/grid.less';

/* 推荐 */
@import "mixins/size.less";
@import "mixins/grid.less";
```

#### 混合（Mixin）
1. 在定义 `mixin` 时，如果 `mixin` 名称不是一个需要使用的 className，必须加上括号，否则即使不被调用也会输出到 CSS 中。
2. 如果混入的是本身不输出内容的 `mixin`，需要在 `mixin` 后添加括号（即使不传参数），以区分这是否是一个 className。

示例：
```less
/* 不推荐 */
.big-text {
  font-size: 2em;
}

h3 {
  .big-text;
  .clearfix;
}

/* 推荐 */
.big-text() {
  font-size: 2em;
}

h3 {
  /* 1 */
  .big-text(); 
  /* 2 */
  .clearfix(); 
}
```