组件化的优点：

当页面有多个轮播时，代码数量不变，功能同样：
将
```
  let $carousel = document.querySelector('.carousel')
  new Carousel($root))
  ```
改成：
```
  let $$carousel = document.querySelectorAll('.carousel')   //获取页面上所有的轮播
  $$carousel.forEach($root => new Carousel($root))   //对所有的root结构进行foreach循环（每个元素执行一次）
  ```
