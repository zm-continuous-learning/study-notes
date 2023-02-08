<a name="FgQG7"></a>
# 一、行内样式
行内样式就是直接把css样式添加在HTML标签中,作为style样式的属性值
```html
  <p style="width: 200px; height:100px;background-color: red;">文本内容</p>
  <p style="width: 200px; height:100px;background-color: blue;">文本内容</p>
  <p style="width: 200px; height:100px;background-color: rgb(221, 255, 0);">文本内容</p>
  <p style="width: 200px; height:100px;background-color: #aa0;">文本内容</p>
```
<a name="BPH7q"></a>
# 二、内部样式（内嵌式）
内嵌式是在HTML中创建一个style标签，把css样式写入style标签内，style标签可以写在HTML中的任何位置，但是我们通常写在head标签里面。<br />tips：_书写内部样式的时候,按照书写代码需要把style放在头部的原因是因为希望浏览器加载的时候,先加载css备用,然后到加载html的时候,直接就把相关的css样式给显示出来(类似人做事儿的时候,先准备再做,效率会提高) _
```html
<!-- 第2步:找装修公司 style-->
<style type="text/css">
 
    /* 第3步:书写装修的过程 */
 
    p{
      width: 200px;
      height: 200px;
      background-color: red;
    }
 
    </style>
 
    <!-- 第1步:盖房子 -->
    <p>段落1</p>
    <p>段落2</p>
    <p>段落3</p>

```
<a name="QhIz9"></a>
# 三、外部样式
外部样式的css文件
```html
/* 第2步:找装修公司也就是创建一个新的css文件,且在css文件里面装修就可 */
p{
  width: 200px;
  height: 200px;
  background-color: pink;
}
```
<a name="cwCdq"></a>
## 3.1外链式
外链式是把css样式写入.css文件内，然后通过link标签链接。
```html
<!-- 第3步:就是把html文件和css文件产生关联(给装修公司付钱) -->
<link rel="stylesheet" href="demo.css" type="text/css">
 
  <!-- 第1步:先盖房子 -->
  <p>房子1</p>
  <p>房子2</p>
  <p>房子3</p>

```
<a name="Z5zhK"></a>
## 3.2导入式
导入式和和外链式是差不多的，都是在外部创建一个css文件，然后在style标签内通过@import url(url);导入，但是与外链式不同的是，外链式是先加载css，再显示HTML，而导入式是先显示HTML，再加载css，所以现在基本不推荐使用导入式,推荐使用外链式。
```html
  <style>
    @import url demo.css;
  </style>
 
  <!-- 第1步:先盖房子 -->
  <p>房子1</p>
  <p>房子2</p>
  <p>房子3</p>
```
<a name="r4REV"></a>
# 引入方式的优先级
优先级大小为:行内样式>内部样式>外部样式
