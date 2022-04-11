轮播的多种设计模式：

animation(动画）:animation 属性用来指定一组或多组动画，每组之间用逗号相隔。

CSS animation 属性是 animation-name，animation-duration, animation-timing-function，animation-delay，animation-iteration-count，animation-direction，animation-fill-mode 和 animation-play-state 属性的一个简写属性形式。

每个动画定义中的属性值的顺序很重要：可以被解析为 <time> 的第一个值被分配给animation-duration， 第二个分配给 animation-delay。
  
  以下属性出现0次或1次：
<single-transition-timing-function> (en-US)
<single-animation-iteration-count>
<single-animation-direction>
<single-animation-fill-mode>
<single-animation-play-state>

  animation 的 name 值可能是：none，<custom-ident>， <string>
<time> 可能会出现0、1 或 2 次
  

每个动画定义中的值的顺序，对于区分 animation-name 值与其他关键字也很重要。解析时，对于除 animation-name 之外的有效的关键字，必须被前面的简写中没有找到值的属性所接受。此外，在序列化时，animation-name 与以及其他属性值做区分等情况下，必须输出其他属性的默认值。
  
<single-animation-iteration-count>
动画播放的次数。该值必须是animation-iteration-count可用的值之一。

<single-animation-direction>
动画播放的方向。该值必须是animation-direction可用的值之一。

<single-animation-fill-mode>
确定动画在执行之前和之后这两个阶段应用的样式。该值必须是animation-fill-mode可用的值之一。

<single-animation-play-state>
确定动画是否正在播放。该值必须是animation-play-state中可用的值之一。



1）slide（滑动）：需要设置from(fromIndex)，to(toIndex)，direction。

当from 大于 to 的时候，向左滑动；当from 小于 to 的时候，向右滑动。到最后一页的时候，仍然向右滑动到第一页。
```
bind() {
this.$pre.onclick = () => {
  let fromIndex = this.getIndex()
  let toIndex = this.getPreIndex()
  this.setPage(fromIndex, toIndex, 'right')
  this.setIndicator(toIndex)
}

this.$next.onclick = () => {
  let fromIndex = this.getIndex()
  let toIndex = this.getNextIndex()
  this.setPage(fromIndex, toIndex, 'left')
  this.setIndicator(toIndex)
}

this.$$indicators.forEach($indicator => $indicator.onclick = (e) => {
  let fromIndex = this.getIndex()
  let toIndex = [...this.$$indicators].indexOf(e.target)
  this.setIndicator(toIndex)
  let direction = fromIndex > toIndex ? 'right' : 'left'
  this.setPage(fromIndex, toIndex, direction)
})
}
```
在设置from 与 to 的位置转换后，需要设置from 与 to 的归位。
```
slide($from, $to, direction) {
$from.style = ''
$to.style = ''
```

2）fade（渐变）：

设置透明度与重叠上下文，实现渐变效果：
```
fade($from, $to) {
$from.style = ''
$to.style = ''

css($from, {
  opacity: 1,
  zIndex: 10
})

css($to, {
  opacity: 0,
  zIndex: 9
})
 setTimeout(() => {
    css($from, {
      opacity: 0,
      zIndex: 10,
      transition: `all 1s`,
    })
    css($to, {
      opacity: 1,
      zIndex: 9,
      transition: `all 1s`,
    })            
  })

  setTimeout(() => {
    css($from, {
      zIndex: 9
    })
    css($to, {
      zIndex: 10
    })  
  }, 1000)
},
```

3）zoom（放大）：

CSS属性 scale 允许你可以分别且独立地指定CSS属性 transform 缩放的比例。这更好地映射到典型的UI（用户界面）用法中，并免去了在指定变换值时必须记住变换函数的精确顺序的麻烦。

none:指定不进行缩放。
scale: none;

单个值:单一的数值即指定了一个缩放系数，同时作用于X轴和Y轴让该元素进行缩放，相当于指定了单个值的scale()(2D缩放)函数。
设定比1大的数值使该元素变大：
scale: 2;
设定比1小的数值使该元素缩小
scale: 0.5;

两个值：两个数值(百分比值)即分别指定了2D比例的X轴和Y轴的缩放系数，相当于指定了两个值的scale()（2D缩放）函数。
scale: 2 0.5;

三个值：三个数值即分别指定了3D比例的X轴、Y轴和Z轴的缩放系数. 相当于一个scale3d()函数。
scale: 2 0.5 2;

