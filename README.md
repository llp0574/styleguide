# CSS 编码规范

## 1. 介绍

这份规范的目的是提升开发效率，使 CSS 代码风格保持一致，更容易被理解和维护，同时也便于新入职同事更容易开始工作。

这份规范将针对 CSS 进行设计，但是在使用 CSS 的预编译器（如 less 等）时，适用的部分也应尽量遵循本文档的约定。

由于现在各个项目的代码架构差异及历史遗留等原因，部分细节还请根据项目自身情况进行决策，待规范定义经讨论修改完善后，再考虑添加stylelint。

## 2. 规范细则

### 2.1 缩进
使用`2`个空格作为一个缩进层级。

示例:
```css
.selector {
  margin: 0;
  padding: 0;
}
```

### 2.2 类名定义

使用破折号代替驼峰法和下划线

示例：
```css
.first-line {
  ...
}
```

### 2.3 按需使用 `ID` 作为选择器
id在页面是唯一的，不能多次使用，类名选择器可以重复使用，而且id一般会用作js选择器，有时因为js的原因改动，那么对应的css也会失效，所以id选择器不到万不得已尽量不在css里使用。

### 2.4 规则声明格式
* 在一个规则声明中应用了多个选择器时，每个选择器独占一行
* 在规则声明的左大括号 `{` 前加上一个空格
* 在属性的冒号 `:` 后面加上一个空格，前面不加空格
* 规则声明的右大括号 `}` 独占一行
* 规则声明之间用空行分隔开

示例：
```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  ...
}
```

### 2.5 注释
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

### 2.6 属性书写顺序

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

### 2.7 使用缩写属性

CSS 有些属性是可以缩写的，如 `padding`、`margin` 等，这些属性中，如果属性值只有1个或2个，则应该分开写，2个以上的话，应使用合并的缩写形式。

示例：
```css
.selector {
  border-top: 0;
  padding: 0 10px 5px;
}
```

### 2.8 嵌套层级

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

### 2.9 数值 `0` 相关
* 当数值为 0 - 1 之间的小数时，省略整数部分的 `0`。
* 长度为 `0` 时须省略单位。

示例：
```css
panel {
  opacity: .8;
  padding: 0 5px;
}
```

### 2.10 url()
* `url()` 函数中的路径不加引号
* `url()` 函数中的绝对路径可省去协议名

示例：
```css
body {
  background-image: url(//baidu.com/img/bg.png); no-repeat 0 0;
}
```

### 2.11 颜色相关
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

### 2.12 文本相关
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

### 2.13 动画相关
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

### 2.14 JavaScript 钩子
避免在 CSS 和 JavaScript 中绑定相同的类。否则开发者在重构时通常会出现以下情况：轻则浪费时间在对照查找每个要改变的类，重则因为害怕破坏功能而不敢作出更改。

推荐在创建用于特定 JavaScript 的类名时，添加 `.js-` 前缀。

示例：
```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```