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
- [demo](https://jsfiddle.net/justin3737/v57u1dLg/1/)

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
    - flex-start (default)
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
    - flex-start - 貼齊側軸的起始點 cross-start. (default)
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

![image](https://raw.githubusercontent.com/migocorp-f2e/understanding-flexbox/master/resources/flexbox-align-items-baseline.jpg)


##Flex item 項目屬性
### order
- order屬性是用来控制flex容器中flex項目的排列顺序。
- 預設值 0
- 可以不必重新修改HTML 透過order 指定順序

![image](https://raw.githubusercontent.com/migocorp-f2e/understanding-flexbox/master/resources/flexbox-order.jpg)


###flex-grow 
- 用来指定 flex項目的放大比例
- 預設值 0
- 注意：負數無效

![image](https://raw.githubusercontent.com/migocorp-f2e/understanding-flexbox/master/resources/flexbox-flex-grow-2.jpg)




##學習有賺有賠 詳閱flexbox 公開說明書
- [瀏覽器support](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#browser-support)



## 資源 Resources
[第一次用 CSS - Flexbox 就上手](http://andyyou.github.io/javascript/2015/09/09/understand-flexbox.html)

[筆記：CSS3 Flexbox屬性](http://www.vialley.com/345/%E7%AD%86%E8%A8%98%EF%BC%9Acss3-flexbox%E5%B1%AC%E6%80%A7)

[【前端攻略】最全面的水平垂直居中方案与flexbox布局](http://www.cnblogs.com/coco1s/p/4444383.html)
