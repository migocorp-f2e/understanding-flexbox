# understanding-flexbox
-

## 在學flexbox 之前
還記得CSS3 四種佈局模式
 - block
 - inline
 - table
 - positioned
 
在 Flexbox, 開發者大量濫用 float 來排版, 所以應 該有過使用 float 搭配 clearfix 的經驗吧.

[clearfix](http://zh-tw.learnlayout.com/clear.html)
 
 
 
## 共有3種  flex 規格？ 
 - 2009 年的版本: display: box 現在已經不再跟 Flexbox 有任何關係
 - 2011 過渡期版本: display: flexbox 只是草稿, 只被 IE10 實作, 如果可能的話應該避免使用
 - 2012 最終版: display: flex
 
 PS. 如果你看到的文章不是 display: flex 那麼你可以不看了
 
## 簡介
- flex container 與 flex items
![image](https://raw.githubusercontent.com/migocorp-f2e/understanding-flexbox/master/resources/1-5rqfzizVze5BEstfXNKnfQ.png)

- main axis 與 cross axis
![image](https://raw.githubusercontent.com/migocorp-f2e/understanding-flexbox/master/resources/1-xo0yJQCryqinH2PhvVMwkw.png)

## Flex container 容器屬性
###display (佈局)
- 使用Flexbox布局只要在父容器元素上設置display屬性：

``` css
.container {
  display: flex;
}
```
- container 會成為一個 flex container
- 內部第一層的子元素會變成 flex item
- [demo](https://jsfiddle.net/justin3737/4g1kgkxf/2/)

###flex-direction (方向)
- 四種方向設定
    - row (default)
    - row-reverse
    - column
    - column-reverse
- [demo](https://jsfiddle.net/justin3737/stkc7ee7/2/)

``` css
.container{
  flex-direction: row;
}
```

###flex-wrap (包裹)
- 三種屬性
    - nowrap(default)
    - wrap
    - wrap-reverse
- [demo](https://jsfiddle.net/justin3737/v57u1dLg/)

``` css
.container{
  flex-wrap: wrap;
}
```

###flex-flow
- 是 flex-direction 和 flex-wrap 的縮寫版預設值是 row nowrap
``` css
.container{
  flex-flow: <‘flex-direction’> || <‘flex-wrap’>
}
```

###justify-content
- 設定主軸的對齊方式
- 這個屬性可以協助我們分配容器中扣除 item 的空間
    - flex-start
    - flex-end
    - center
    - space-around
    - space-between
``` css
.container {
  justify-content: flex-start;
}
```

- [demo - center](https://jsfiddle.net/justin3737/trmfmryb/1/)

- [demo - flex-start](https://jsfiddle.net/justin3737/trmfmryb/2/)
 
- [demo - space-between](https://jsfiddle.net/justin3737/trmfmryb/4/)
 
- [demo - space-around](https://jsfiddle.net/justin3737/trmfmryb/3/)




###align-items
- 這個屬性用來設定 item 該如何沿著側軸(cross axis)對齊排列
- 把它想成用來處理垂直置中的屬性比較好記. 是指每個個別的 item 跟怎麼跟側軸對齊
- 注意：這個屬性只有當flex容器有多行flex項目時才生效
    - flex-start - 貼齊側軸的起始點 cross-start.
    - flex-end - 貼齊側軸 cross-end 排列
    - center - 置放於側軸的中央
    - baseline - item 會對齊 baseline
    - stretch - 預設值, 自動把 item 的高長滿 container
``` css
.container {
  align-items: flex-start;
}
```

[demo - flex-start](https://jsfiddle.net/justin3737/ak6raxtc/2/)

[demo - flex-end](https://jsfiddle.net/justin3737/ak6raxtc/3/)

[demo - center](https://jsfiddle.net/justin3737/ak6raxtc/4/)

[demo - baseline](https://jsfiddle.net/justin3737/ak6raxtc/5/)

![image](data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjwhLS0gR2VuZXJhdG9yOiBBZG9iZSBJbGx1c3RyYXRvciAxNi4wLjQsIFNWRyBFeHBvcnQgUGx1Zy1JbiAuIFNWRyBWZXJzaW9uOiA2LjAwIEJ1aWxkIDApICAtLT4NCjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+DQo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4Ig0KCSB3aWR0aD0iMzE5cHgiIGhlaWdodD0iMzc3cHgiIHZpZXdCb3g9IjAgMCAzMTkgMzc3IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAzMTkgMzc3IiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCjxyZWN0IHk9IjI0IiBmaWxsPSIjODk0NzlCIiB3aWR0aD0iMTQ4Ljg5NSIgaGVpZ2h0PSI5OCIvPg0KPHJlY3QgeT0iMjQiIGZpbGw9IiNFODgwMjQiIHdpZHRoPSIyOS41NDciIGhlaWdodD0iNDguNSIvPg0KPHJlY3QgeD0iMzkuMTE5IiB5PSIyNCIgZmlsbD0iI0U4ODAyNCIgd2lkdGg9IjI5LjU0NyIgaGVpZ2h0PSI1OS41Ii8+DQo8cmVjdCB4PSI3OS4zNTUiIHk9IjI0IiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iMjkuNTQ3IiBoZWlnaHQ9IjI5Ljc1Ii8+DQo8cmVjdCB4PSIxMTkuMzQ3IiB5PSIyNCIgZmlsbD0iI0U4ODAyNCIgd2lkdGg9IjI5LjU0NyIgaGVpZ2h0PSI0OC41Ii8+DQo8dGV4dCB0cmFuc2Zvcm09Im1hdHJpeCgxIDAgMCAxIDggMjQpIiBmaWxsPSIjODk0NzlCIiBmb250LWZhbWlseT0iJ0dvdGhhbVJvdW5kZWQtQm9vayciIGZvbnQtc2l6ZT0iMTYiPmZsZXgtc3RhcnQ8L3RleHQ+DQo8cmVjdCB5PSIxNTUiIGZpbGw9IiM4OTQ3OUIiIHdpZHRoPSIxNDguODk1IiBoZWlnaHQ9Ijk4Ii8+DQo8cmVjdCB5PSIxNzguMjgxIiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iMjkuNTQ3IiBoZWlnaHQ9IjQ4LjUiLz4NCjxyZWN0IHg9IjM5LjExOSIgeT0iMTcyLjc4MSIgZmlsbD0iI0U4ODAyNCIgd2lkdGg9IjI5LjU0NyIgaGVpZ2h0PSI1OS41Ii8+DQo8cmVjdCB4PSI3OS4zNTUiIHk9IjE4Ny42NTYiIGZpbGw9IiNFODgwMjQiIHdpZHRoPSIyOS41NDciIGhlaWdodD0iMjkuNzUiLz4NCjxyZWN0IHg9IjExOS4zNDciIHk9IjE3OC4yODEiIGZpbGw9IiNFODgwMjQiIHdpZHRoPSIyOS41NDciIGhlaWdodD0iNDguNSIvPg0KPHRleHQgdHJhbnNmb3JtPSJtYXRyaXgoMSAwIDAgMSA4IDE1NSkiIGZpbGw9IiM4OTQ3OUIiIGZvbnQtZmFtaWx5PSInR290aGFtUm91bmRlZC1Cb29rJyIgZm9udC1zaXplPSIxNiI+Y2VudGVyPC90ZXh0Pg0KPHJlY3QgeT0iMjc5IiBmaWxsPSIjODk0NzlCIiB3aWR0aD0iMzA4LjM5NSIgaGVpZ2h0PSI5OCIvPg0KPHJlY3QgeT0iMjg3LjQwNiIgZmlsbD0iI0U4ODAyNCIgd2lkdGg9IjY0IiBoZWlnaHQ9IjY4Ljg3NSIvPg0KPHJlY3QgeD0iNzAuMTIxIiB5PSIyOTMuNTYyIiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iNjQiIGhlaWdodD0iNDMuNDM4Ii8+DQo8cmVjdCB4PSIxNDIuMjczIiB5PSIyODYuNDA2IiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iNzguNzI3IiBoZWlnaHQ9IjYzLjU5NCIvPg0KPHJlY3QgeD0iMjI5LjAzOSIgeT0iMjkwLjA0NyIgZmlsbD0iI0U4ODAyNCIgd2lkdGg9Ijc4LjcyNyIgaGVpZ2h0PSI3Ni45NTMiLz4NCjx0ZXh0IHRyYW5zZm9ybT0ibWF0cml4KDEgMCAwIDEgOCAyNzkpIiBmaWxsPSIjODk0NzlCIiBmb250LWZhbWlseT0iJ0dvdGhhbVJvdW5kZWQtQm9vayciIGZvbnQtc2l6ZT0iMTYiPmJhc2VsaW5lPC90ZXh0Pg0KPHJlY3QgeD0iMTU5LjUiIHk9IjE1NSIgZmlsbD0iIzg5NDc5QiIgd2lkdGg9IjE0OC44OTUiIGhlaWdodD0iOTgiLz4NCjxyZWN0IHg9IjE1OS41IiB5PSIxNTQuMDMxIiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iMjkuNTQ3IiBoZWlnaHQ9Ijk4Ljk2OSIvPg0KPHJlY3QgeD0iMTk4LjYxOSIgeT0iMTU1IiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iMjkuNTQ3IiBoZWlnaHQ9Ijk4Ii8+DQo8cmVjdCB4PSIyMzguODU1IiB5PSIxNTUiIGZpbGw9IiNFODgwMjQiIHdpZHRoPSIyOS41NDciIGhlaWdodD0iOTgiLz4NCjxyZWN0IHg9IjI3OC44NDgiIHk9IjE1NSIgZmlsbD0iI0U4ODAyNCIgd2lkdGg9IjI5LjU0NyIgaGVpZ2h0PSI5OCIvPg0KPHRleHQgdHJhbnNmb3JtPSJtYXRyaXgoMSAwIDAgMSAxNjcuNSAxNTUpIiBmaWxsPSIjODk0NzlCIiBmb250LWZhbWlseT0iJ0dvdGhhbVJvdW5kZWQtQm9vayciIGZvbnQtc2l6ZT0iMTYiPnN0cmV0Y2g8L3RleHQ+DQo8cmVjdCB4PSIxNTkuNSIgeT0iMjQiIGZpbGw9IiM4OTQ3OUIiIHdpZHRoPSIxNDguODk1IiBoZWlnaHQ9Ijk4Ii8+DQo8cmVjdCB4PSIxNTkuNSIgeT0iNzMuNSIgZmlsbD0iI0U4ODAyNCIgd2lkdGg9IjI5LjU0NyIgaGVpZ2h0PSI0OC41Ii8+DQo8cmVjdCB4PSIxOTguNjE5IiB5PSI2Mi41IiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iMjkuNTQ3IiBoZWlnaHQ9IjU5LjUiLz4NCjxyZWN0IHg9IjIzOC44NTUiIHk9IjkyLjI1IiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iMjkuNTQ3IiBoZWlnaHQ9IjI5Ljc1Ii8+DQo8cmVjdCB4PSIyNzguODQ4IiB5PSI3My41IiBmaWxsPSIjRTg4MDI0IiB3aWR0aD0iMjkuNTQ3IiBoZWlnaHQ9IjQ4LjUiLz4NCjx0ZXh0IHRyYW5zZm9ybT0ibWF0cml4KDEgMCAwIDEgMTY3LjUgMjQpIiBmaWxsPSIjODk0NzlCIiBmb250LWZhbWlseT0iJ0dvdGhhbVJvdW5kZWQtQm9vayciIGZvbnQtc2l6ZT0iMTYiPmZsZXgtZW5kPC90ZXh0Pg0KPHRleHQgdHJhbnNmb3JtPSJtYXRyaXgoMSAwIDAgMSA1IDMwOCkiIGZvbnQtZmFtaWx5PSInR290aGFtUm91bmRlZC1Cb29rJyIgZm9udC1zaXplPSIxMyI+dGV4dCB0ZXh0PC90ZXh0Pg0KPHRleHQgdHJhbnNmb3JtPSJtYXRyaXgoMSAwIDAgMSAyNDMgMzA4KSIgZm9udC1mYW1pbHk9IidHb3RoYW1Sb3VuZGVkLUJvb2snIiBmb250LXNpemU9IjEzIj50ZXh0IHRleHQ8L3RleHQ+DQo8dGV4dCB0cmFuc2Zvcm09Im1hdHJpeCgxIDAgMCAxIDgxLjY2NiAzMDguNzI5NSkiIGZvbnQtZmFtaWx5PSInR290aGFtUm91bmRlZC1Cb29rJyIgZm9udC1zaXplPSIxMCI+dGV4dCB0ZXh0PC90ZXh0Pg0KPHRleHQgdHJhbnNmb3JtPSJtYXRyaXgoMSAwIDAgMSAxNDkuMTk3MyAzMDcuMjcxNSkiIGZvbnQtZmFtaWx5PSInR290aGFtUm91bmRlZC1Cb29rJyIgZm9udC1zaXplPSIxNiI+dGV4dCB0ZXh0PC90ZXh0Pg0KPGxpbmUgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjRjdFQzFEIiBzdHJva2UtbWl0ZXJsaW1pdD0iMTAiIHgxPSIwIiB5MT0iMzA4IiB4Mj0iMzA4LjM5NSIgeTI9IjMwOCIvPg0KPC9zdmc+DQo=)


##Flex item 項目屬性
### order
- order屬性是用来控制flex容器中flex項目的排列顺序。
- 預設值 0
- 可以不必重新修改HTML 透過order 指定順序

￼

###flex-grow 
- 用来指定 flex項目的放大比例
- 預設值 0
- 注意：負數無效






##學習有賺有賠 詳閱flexbox 公開說明書
- [瀏覽器support](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#browser-support)



## 資源 Resources
[第一次用 CSS - Flexbox 就上手](http://andyyou.github.io/javascript/2015/09/09/understand-flexbox.html)

[筆記：CSS3 Flexbox屬性](http://www.vialley.com/345/%E7%AD%86%E8%A8%98%EF%BC%9Acss3-flexbox%E5%B1%AC%E6%80%A7)

[【前端攻略】最全面的水平垂直居中方案与flexbox布局](http://www.cnblogs.com/coco1s/p/4444383.html)
