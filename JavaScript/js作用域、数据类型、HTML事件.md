<a name="Gy4Tw"></a>
## javaScript作用域
<a name="uwyk0"></a>
#### 1.全局作用域
_**全局**_（在函数之外）声明的变量拥有_**全局作用域**_。

- _**全局**_变量可以在 JavaScript 程序中的任何位置访问。
<a name="AudKk"></a>
#### 2.函数作用域
_**局部**_（函数内）声明的变量拥有_**函数作用域**_。

- _**局部**_变量只能在它们被声明的函数内访问。
```javascript
// 此处的代码不可以使用 carName

function myFunction() {
  var carName = "porsche";
  // code here CAN use carName
}

// 此处的代码不可以使用 carName
```
<a name="N2AWI"></a>
#### <br />3.javaScript块作用域
通过 var 关键词声明的变量没有块作用域。在块 _**{}**_ 内声明的变量可以从块之外进行访问。
```javascript
{ 
  var x = 10; 
}
// 此处可以使用 x
```
使用 var 关键字重新声明变量会带来问题。在块中重新声明变量也将重新声明块外的变量：
```javascript
var x = 10;
// 此处 x 为 10
{ 
  var x = 6;
  // 此处 x 为 6
}
// 此处 x 为 6
```

let 关键词声明拥有块作用域的变量。在块 {} 内声明的变量无法从块外访问：
```javascript
{ 
  let x = 10;
}
// 此处不可以使用 x
```
let在块中重新声明变量不会重新声明块外的变量：
```javascript
var x = 10;
// 此处 x 为 10
{ 
  let x = 6;
  // 此处 x 为 6
}
// 此处 x 为 10
```
<a name="l14vu"></a>
#### const特性
<a name="Sbpuf"></a>
##### 1.在块作用域内使用 const 声明的变量与 let 变量相似。
```javascript
var x = 10;
// 此处，x 为 10
{ 
  const x = 6;
  // 此处，x 为 6
}
// 此处，x 为 10
```
<a name="tlMI8"></a>
##### 2.在声明时赋值
不正确
```javascript
const PI;
PI = 3.14159265359;
```
正确
```javascript
const PI = 3.14159265359;
```
<a name="lTIvS"></a>
##### 不是真正的常数
定义了对值的常量引用。因此，我们不能更改常量原始值，但我们可以更改常量对象的属性。
```javascript
const PI = 3.141592653589793;
PI = 3.14;      // 会出错
PI = PI + 10;   // 也会出错
```
<a name="aUryo"></a>
##### 常量对象可以更改
您可以更改常量对象的属性
```javascript
// 您可以创建 const 对象：
const car = {type:"porsche", model:"911", color:"Black"};

// 您可以更改属性：
car.color = "White";

// 您可以添加属性：
car.owner = "Bill";
```
但是无法重新为常量对象赋值：
```javascript
const car = {type:"porsche", model:"911", color:"Black"};
car = {type:"Volvo", model:"XC60", color:"White"};    // ERROR
```
常量数组可以更改：
```javascript
// 可以创建常量数组：
const cars = ["Audi", "BMW", "porsche"];

// 可以更改元素：
cars[0] = "Honda";

// 可以添加元素：
cars.push("Volvo");
```
但是无法重新为常量数组赋值：
```javascript
const cars = ["Audi", "BMW", "porsche"];
cars = ["Honda", "Toyota", "Volvo"];    // ERROR
```
<a name="cCDIF"></a>
## javaScript数据类型
<a name="uTttY"></a>
#### Undefined与Null的区别
Undefined 与 null 的值相等，但类型不相等：
```javascript
typeof undefined              // undefined
typeof null                   // object
null === undefined            // false
null == undefined             // true
```
<a name="aqpSz"></a>
## 常见的HTML事件
| 事件 | 描述 |
| --- | --- |
| onchange | HTML元素已被改变 |
| onclick | 用户点击了HTML元素 |
| onmouseover | 用户把鼠标移到HTML元素上 |
| onmouseout | 用户把鼠标移开HTML元素上 |
| onkeydown | 用户按下键盘按键 |
| onload | 浏览器已经完成页面加载 |


