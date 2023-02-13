<a name="yLBwd"></a>
## 字符串方法
<a name="ZIKem"></a>
#### 1.length

1. length返回字符串长度
<a name="kvD6f"></a>
#### 2.indexOf()和lastIndexOf()

1. indexOf（）方法返回字符串中指定文本首次出现的索引（位置），js从0开始计算位置。
2. lastIndexOf（）方法返回指定文本中最后一次出现的索引。
3. indexOf（）和lastIndexOf（）未找到文本，均返回-1。
4. 两种方法都接受作为检索起始位置的第二个参数。str.indexOf("string",18)
5. search() 方法搜索特定值的字符串，并返回匹配的位置

两indexOf() 与 search()，区别在于：

- search() 方法无法设置第二个开始位置参数。
- indexOf() 方法无法设置更强大的搜索值（正则表达式）。
<a name="XNAKA"></a>
#### 3.提取部分字符串
<a name="MZ4KP"></a>
##### 1.slice（start，end）

- 如果某个参数为负，则从字符串的结尾开始计数。
- 如果省略第二个参数，则该方法将裁剪字符串的剩余部分：
<a name="hsD7l"></a>
##### 2.substring（start，end）

- substring() 类似于 slice()，不同之处在于 substring() 无法接受负的索引。
- 如果省略第二个参数，则该 substring() 将裁剪字符串的剩余部分。
<a name="GrrVE"></a>
##### 3.substr（start，length）

- substr() 类似于 slice()。不同之处在于第二个参数规定被提取部分的长度。
- 如果省略第二个参数，则该 substr() 将裁剪字符串的剩余部分。
<a name="ITyef"></a>
#### 替换字符串内容
<a name="Ozdft"></a>
##### 1.replace（）
replace() 方法用另一个值替换在字符串中指定的值：
```javascript
str = "Please visit Microsoft!";
var n = str.replace("Microsoft", "W3School");
```
replace() 方法不会改变调用它的字符串。它返回的是新字符串。

- replace() 只替换首个匹配。
- replace() 对大小写敏感。
- 如需执行大小写不敏感的替换，请使用正则表达式 /i（大小写不敏感）：
```javascript
str = "Please visit Microsoft!";
var n = str.replace(/MICROSOFT/i, "W3School");
```

- 请注意正则表达式不带引号。如需替换所有匹配，请使用正则表达式的 g 标志（用于全局搜索）：
```javascript
str = "Please visit Microsoft and Microsoft!";
var n = str.replace(/Microsoft/g, "W3School");
```
<a name="HS1cv"></a>
##### 2.转换为大写和小写
通过 toUpperCase() 把字符串转换为大写：
```javascript
var text1 = "Hello World!";       // 字符串
var text2 = text1.toUpperCase();  // text2 是被转换为大写的 text1
```
通过 toLowerCase() 把字符串转换为小写：
```javascript
var text1 = "Hello World!";       // 字符串
var text2 = text1.toLowerCase();  // text2 是被转换为小写的 text1
```
<a name="uSEVB"></a>
##### 3.concat（）方法
concat() 连接两个或多个字符串：Hello World!
```javascript
var text1 = "Hello";
var text2 = "World";
text3 = text1.concat(" ",text2);
```

- 所有字符串方法都会返回新字符串。它们不会修改原始字符串。
- 正式地说：字符串是不可变的：字符串不能更改，只能替换。
<a name="hw1Kz"></a>
##### 3.String.trim()
trim() 方法删除字符串两端的空白符：str.trim()
<a name="PyqzM"></a>
##### 4.提取字符串字符
<a name="o079l"></a>
###### 4.1charAt()方法
charAt() 方法返回字符串中指定下标（位置）的字符串
```javascript
var str = "HELLO WORLD";
str.charAt(0);            // 返回 H
```
<a name="Qk8bK"></a>
###### 4.2charCodeAt() 方法
charCodeAt() 方法返回字符串中指定索引的字符 unicode 编码：
```javascript
var str = "HELLO WORLD";

str.charCodeAt(0);         // 返回 72
```
<a name="BJ8sg"></a>
##### 5.属性访问（Property Access）
```javascript
var str = "HELLO WORLD";
str[0] = "A";             // 不产生错误，但不会工作
str[0];                   // 返回 H
```

- 不适用 Internet Explorer 7 或更早的版本
- 它让字符串看起来像是数组（其实并不是）
- 如果找不到字符，[ ] 返回 undefined，而 charAt() 返回空字符串。
- 它是只读的。str[0] = "A" 不会产生错误（但也不会工作！）
<a name="svwtX"></a>
##### 6.把字符串转换为数组
可以通过 split() 将字符串转换为数组：
```javascript
var txt = "a,b,c,d,e";   // 字符串
txt.split(",");          // 用逗号分隔
txt.split(" ");          // 用空格分隔
txt.split("|");          // 用竖线分隔
```
<a name="uyYhd"></a>
## 字符串搜索
用于搜索字符串的 JavaScript 方法：

- String.indexOf()
- String.lastIndexOf()
- String.startsWith()
- String.endsWith()
<a name="iZgqm"></a>
##### String.search()
search() 方法在字符串中搜索指定值并返回匹配的位置：
```javascript
let str = "Please locate where 'locate' occurs!";
str.search("locate")     // 返回 7
```
这两种方法并不相等。差别如下：

- search() 方法不能接受第二个起始位置参数。
- indexOf() 方法不能采用强大的搜索值（正则表达式）。
<a name="Yb7KU"></a>
##### String.match()
match() 方法根据正则表达式在字符串中搜索匹配项，并将匹配项作为 Array 对象返回。
```javascript
let text = "The rain in SPAIN stays mainly in the plain";
text.match(/ain/gi)   // 返回数组 [ain,AIN,ain,ain]
```
string.match(regexp)

| _regexp_ | 必需。需要搜索的值，为正则表达式。 |
| --- | --- |
| 返回： | 数组，包含匹配项，每个匹配项对应一个项目，若未找到匹配项，则为 null。 |

对 "ain" 执行不区分大小写的全局搜索。
<a name="sw9Os"></a>
##### String.includes()
如果字符串包含指定值，includes() 方法返回 true。
```javascript
let text = "Hello world, welcome to the universe.";
text.includes("world")    // 返回 true
```
string.includes(searchvalue, start)
<a name="o2S5g"></a>
##### String.startsWith()
如果字符串以指定值开头，则 startsWith() 方法返回 true，否则返回 false.startsWith() 方法区分大小写。
<a name="QYAGR"></a>
##### String.endsWith()
如果字符串以指定值结尾，则 endsWith() 方法返回 true，否则返回 false：
