Carousel（轮播、走马灯）组件：不同页的切换

1、text-decoration：

1）text-decoration 这个 CSS 属性是用于设置文本的修饰线外观的（下划线、上划线、贯穿线/删除线  或 闪烁）。
如：text-decoration: none;去除下划线。

2）文本修饰属性会延伸到子元素。这意味着如果祖先元素指定了文本修饰属性，子元素则不能将其删除。
如：`<p>This text has <em>some emphasized words</em> in it.</p>，`应用样式`p { text-decoration: underline } `会对整个段落添加下划线，此时再添加样式 `em { text-decoration: none } `则不会引起任何改变，整个段落仍然有下划线修饰。
 然而，新加样式` em { text-decoration: overline }` 则会在`<em>`标记的文字上再添加上这种overline样式。
 
 3）值：
text-decoration-line：文本修饰的位置, 如下划线underline，删除线line-through。
text-decoration-color：文本修饰的颜色。
text-decoration-style：文本修饰的样式, 如波浪线wavy实线solid虚线dashed。
text-decoration-thickness：文本修饰线的粗细。


2、伪类 :link → :visited → :hover → :active （为保证样式生效，伪类先后顺序被称为 LVHA 顺序）

1）:hover ，用于用户使用指示设备虚指一个元素（没有激活它）的情；可以任何伪元素上使用。
使用:hover 伪类可以创建复杂的层叠机制。一个常见用途，比如，创建一个纯CSS的下拉按钮（不使用JavaScript）。
```
div.menu-bar ul ul {
  display: none;
}

div.menu-bar li:hover > ul {
  display: block;
}
```

2）:link ，用来选中元素当中的链接。它将会选中所有尚未访问的链接，包括那些已经给定了其他伪类选择器的链接（例如:hover选择器，:active选择器，:visited选择器）。:focus伪类选择器常伴随在:hover伪类选择器左右，需要根据你想要实现的效果确定它们的顺序。

3）:visited CSS伪类表示用户已访问过的链接。出于隐私原因，可以使用此选择器修改的样式非常有限。
未设置颜色或透明的属性不能使用:visited。 在可以使用此伪类设置的属性中，浏览器可能只有color和column-rule-color两个默认值。 因此，对于其他属性，在使用:visited选择器前，应该先为这些属性设置基础样式。
```
a {
  /* 指定某些属性的默认值，允许他们使用：visited状态进行样式设置 */
  background-color: white;
  border: 1px solid white; 
}

a:visited {
  background-color: yellow;
  border-color: hotpink;
  color: hotpink;
}
```

4）:active ，匹配被用户激活的元素。它让页面能在浏览器监测到激活时给出反馈。当用鼠标交互时，它代表的是用户按下按键和松开按键之间的时间。
:active 伪类一般被用在` <a> `和` <button> `元素中. 这个伪类的一些其他适用对象包括包含激活元素的元素，以及可以通过他们关联的`<label>`标签被激活的表格元素。
```
/* Selects any <a> that is being activated */
a:active {
  color: red;
}
```


3、display：

1）display属性可以设置元素的内部和外部显示类型 display types。元素的外部显示类型 outer display types 将决定该元素在流式布局中的表现（块级或内联元素）；元素的内部显示类型 inner display types 可以控制其子元素的布局（例如：flow layout，grid 或 flex）。

2）语法：display 属性使用关键字取值来指定，关键字取值被分为六类：
```
.container {
    display:  [ <display-outside> | <display-inside> ] | <display-listitem> | <display-internal> | <display-box> | <display-legacy> ;
}
```
Outside：这些关键字指定了元素的外部显示类型，实际上就是其在流式布局中的角色（即在流式布局中的表现）。

Inside：这些关键字指定了元素的内部显示类型，它们定义了该元素内部内容的布局方式（假定该元素为非替换元素 non-replaced element）。

List Item：将这个元素的外部显示类型变为 block 盒，并将内部显示类型变为多个 list-item inline 盒。

Internal：有些布局模型（如 table 和 ruby）有着复杂的内部结构，因此它们的子元素可能扮演着不同的角色。这一类关键字就是用来定义这些“内部”显示类型，并且只有在这些特定的布局模型中才有意义。

Legacy：CSS 2 对于 display 属性使用单关键字语法，对于相同布局模式的 block 级和 inline 级变体需要使用单独的关键字。

是否该继续使用 Legacy 取值？
display 属性的两类取值——显式地指定了外部和内部显示属性的规范——但是还没有被浏览器广泛支持。
```
.container {
    display: inline-flex;
}

.container {
    display: inline flex;
}
```


4、取余%：

当一个操作数除以第二个操作数时，取余运算符（％）返回剩余的余数。它与被除数的符号保持一致。
```
被除数为正数
 12 % 5  //  2
 1 % -2 //  1
 1 % 2  //  1
 2 % 3  //  2
5.5 % 2 // 1.5

被除数为负数
-12 % 5 // -2
-1 % 2  // -1
-4 % 2  // -0

被除数为NaN
NaN % 2 // NaN
```
