<a name="FgLPz"></a>
## 一、DOM简介
<a name="hOIvH"></a>
### DOM定义
文档对象模型（Document Object Model，简称DOM），是W3C组织推荐的处理可拓展标记语言（HTML或者XML）的标准编程接口<br />W3C已经定义了一系列的DOM接口，通过这些DOM接口可以改变网页的内容，结构和样式<br />DOM树<br />文档：一个页面就是一个文档，DOM中使用document表示<br />元素：页面中的所有标签都是元素，DOM中使用element表示<br />节点：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM中使用node表<br />DOM把以上内容都看做是对象
<a name="JOjgn"></a>
## 二、获取元素
根据ID获取，getElementById(‘id名’) 返回匹配id的元素<br />因为我们文档页面从上往下加载，所以先得有标签，所以我们script写到标签的下面<br />get获得,element元素,by通过 驼峰命名法<br />参数 id是大小写敏感的字符串<br />console.dir 打印我们返回的元素对象，更好的查看里面的属性和方法<br />根据标签名获取，getElementsByTagName(‘标签名’) 返回带有指定标签名的对象的集合<br />返回的是，获取过来元素对象的集合，以伪数组的形式存储<br />我们想要依次打印里面的元素对象我们可以采取遍历的方法<br />得到的元素对象是动态的，随页面内的元素变化而变化<br />如果页面中只有一个li，返回的还是伪数组的形式<br />如果页面中没有这个元素，返回的是空的伪数组的形式<br />还可以获得某个元素（父元素）内部所有指定标签名的子元素element.getElementsByTagName('标签名')<br />父元素必须是单个对象（必须指明是哪一个元素对象），获取的时候不包括父元素自己<br />通过H5新增的方法获取，getElementsByClassName(‘类名’)，根据类名获得某些元素的集合<br />querySelector(‘选择器’) 根据指定选择器返回第一个元素对象 ，切记里 面的选择器需要加符号.box #nav<br />querySelectorAll(‘选择器’) 根据指定选择器返回所有元素对象集合<br />获取特殊元素，获取body元素 document.body，<br />获取html元素document.documentElement
<a name="rdKc4"></a>
## 三、事件基础
JavaScript使我们有能力创建动态页面，而事件是可以被JavaScript侦测到的行为（触发-响应机制），网页中每个元素都可以产生某些可以触发JavaScript的事件<br />事件是由三部分组成的，事件源，事件类型，事件处理程序我们也称为事件三要素<br />事件源 事件被触发的对象 谁 按钮<br />事件类型 如何触发 什么事件，比如鼠标点击（onclick）还是鼠标经过还是键盘按下<br />事件处理程序 通过一个函数赋值的方式 完成<br />执行事件的步骤：

1. 获取事件源
2.  注册事件(绑定事件)
3. 通过事件处理程序(采取函数赋值形式）
<a name="E12cS"></a>
## 四、操作元素
JavaScript的DOM操作可以改变网页内容、结构和样式，我们可以利用DOM操作元素来改变元素里面的内容、属性等
<a name="FbOjP"></a>
### 改变元素内容

- element.innerText从起始位置到终止位置的内容，但他去除html标签，同时空格换行也会去掉
- element.innerHTML起始位置到终止位置的全部内容，包括html标签，同时保留空格和换行

书写规范：element.innerHTML = '';<br />二者区别：

1. innerText 不识别html标签，非标准；
2. innerHTML 识别html标签，W3C标准

 这两个属性是可读写的，可以获取元素里面的内容
<a name="NYU5X"></a>
#### 常见元素的属性操作

- 书写规范：标签.属性 = '';
- 表单元素的属性操作
   - 表单里面的值 文字内容通过value来修改 ，书写规范input.value = ''
   - 如果想要某个表单被禁用，不能再点击，btn.disabled = true
   - 表单2个新事件，获得焦点onfocus，失去焦点onblur

- 样式属性操作
   - 行内样式操作，element.style 类名样式操作element.className
   - 通过使用element.style获得修改元素样式，如果样式较少或者功能简单的情况下使用	
   - 书写规范：element.style.样式属性（驼峰命名） = ''
- JS里面的样式采取驼峰命名法
- JS修改style样式操作，产生的是行内样式，css权重比较高
   - 通过className修改元素样式，书写规范：element.className = ''
   - 元素被触发后的样式直接在style中添加对应class名完成修改，事件触发使得当前元素的类名发生改变，适合于样式较多或者功能复杂的情况
   - 如果样式修改较多，可以采取操作类名方式更改元素样式，class因为是个保留字，因此使用className来操作元素类名的属性
   - className会直接更改元素的类名，会覆盖原来的类名
   - 如果想要保留原先的类名，我们可以这么做，多类名选择器element.className = '原 现'
- 自定义属性的操作

程序员自己添加的属性称为自定义属性

- 获取元素的属性值
   - element.属性 获取内置属性值（元素本身自带的属性）
   - element.getAttribute(‘属性’) 主要获得自定义的属性（标准）我们程序员自定义属性
- 设置元素的属性值
   - element.属性 = ‘’ 注意修改class属性时，属性名应为className
   - element.setAttribute(‘属性’,‘值’) 主要针对于自定义属性，注意class特殊，这里面写的就是class，而不是className
- 移除属性
- element.removeAttribute(‘属性’)
- H5自定义属性
   - 自定义属性的目的：为了保存并使用数据，有些数据可以保存到页面中而不用保存到数据库中。
   - 为了避免元素自定义属性和内置属性之前引起歧义，H5新增了自定义属性：
- 设置自定义属性data-开头作为属性名并赋值，或使用JS的setAttribute来设置自定义属性
- 获取H5自定义属性，兼容性获取，使用JS的getAttribute，或者使用H5新增element.dataset.index或者element.dataset[‘index’]，ie11才能使用

- dataset是一个集合里面存放了所有以data开头的自定义属性
- 如果自定义属性里面有多个-链接的单词，我们获取的时候采取驼峰命名法他只能获取data-开头的
<a name="MofTQ"></a>
## 五、节点操作
节点概述：网页中所有的内容都是节点（标签、属性、文本、注释等），在DOM中，节点使用node来表示<br />HTML DOM树中的所有节点均可以通过JavaScript进行访问，所有HTML元素（节点）均可被修改，也可以创建和删除<br />一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个基本属性。<br />元素节点 nodeType为1，属性节点nodeType为2，文本节点nodeType为3（文本节点包含文字、空格、换行等）；实际开发中，节点操作主要操作的是元素节点
<a name="KOXpK"></a>
#### 节点层级

- 利用DOM树可以把节点划分为不同的层级关系，常见的是父子兄层级关系
   - 父级节点：node.parentNode ，
- 得到的是离元素最近的父级节点，如果找不到父节点就返回为null
   - 子节点：parentNode.childNodes
- 返回包含指定节点的子节点的集合（包含元素节点，文本节点 等），该集合为即时更新的集合
- parentNode.children 获取所有的子元素节点，也是我们实际开发常用的
<a name="w1xP4"></a>
#### 节点操作

- 创建节点 document.createElement('tarName')，
- document.createElement()方法创建由tagName指定的HTML元素。因为这些元素原先不存在，是根据我们的需求动态生成的，所以我们也称为动态创建元素节点
- 添加节点node.appendChild(child)
   - node.appendChild()方法将一个节点添加到指定父节点的子节点列表末尾。类似于CSS里面的after伪元素，后面追加元素，类似于数组中的push
- node.insertBefore(child,指定元素)
   - node.insertBefore()方法将一个节点添加到父节点的指定子节点面前。类似于CSS里面的before
- 删除节点 node.removeChild(child)
   - node.removeChild()方法从DOM中删除一个子节点，返回删除的节点
- 阻止链接跳转需要添加javascript:void(0)；或者javascript:;
- 复制节点（克隆节点)node.cloneNode()
   - node.cloneNode()方法返回调用该方法的节点的一个副本，也称为克隆节点/拷贝节点
   - 如果括号参数为空或者为false，则是浅拷贝，即只克隆复制节点本身，不克隆里面的子节点
   - 如果括号参数为true，则是深度拷贝，会复制节点本身以及里面所有的子节点
<a name="jNHOM"></a>
#### 三种动态创建元素的区别

- document.write() 是直接将内容写入页面的内容流，但是文档流执行完毕，则他会导致页面全部重绘。
- innerHTML是将内容写入某个DOM节点，不会导致页面全部重绘
- innerHTML创建多个元素效率更高（不要拼接字符串，采取数组形式拼接），结构稍微复杂
- createElement（）创建多个元素效率稍低一点点，但是结构更清晰
<a name="G2kVK"></a>
## 六、事件高级
<a name="mzC9E"></a>
#### 注册事件（绑定事件）
给元素添加事件，称为注册事件或者绑定事件。<br />注册事件有两种方式：传统方式和方法监听注册方式

- 传统注册方式：利用on开头的事件onclick
   - 特点：注册事件的唯一性，同一个元素同一个事件只能设置一个处理函数，最后注册的处理函数将会覆盖前面注册的处理函数
- 方法监听注册方式：addEvenListener()的方法，ie9之前的浏览器不支持此方法，可使用attachEvent()代替（W3C标准，推荐方式）
   - 特点: 同一个元素同一个事件可以注册多个监听器，按注册顺序依次执行
<a name="rfXPD"></a>
#### addEvenListener事件监听方式

- evenTarget.addEvenListener(type, listener[, useCapture])
- evenTarget.addEvenListener()方法将指定的监听器注册到evenTarget（目标对象）上，当该对象触发指定的事件时，就会执行事件处理函数。

该方法接收三个参数：

- type：事件类型字符串，比如click，mouseover，
- listener：事件处理函数，事件发生时，会调用该监听函数
- useCapture：可选参数，是一个布尔值，默认是false。

注意事项：

- 里面的事件类型是字符串，必定加引号，而且不带on
- 同一个元素，同一个事件可以添加多个侦听器（事件处理程序）
- attachEvent事件监听方式（ie9以前版本支持，慎重使用）
<a name="Nn6dQ"></a>
#### eventTarget.attachEvent(eventNameWithOn, callback)
eventTarget.attachEvent()方法将指定的监听器注册到eventTarget(目标对象)上，当该对象触发指定的事件时，指定的回调函数就会被执行。<br />该方法接收两个参数：

- eventNameWithOn：事件类型字符串，比如onclick，onmouseover
- callback：事件处理函数，当目标触发事件时回调函数被调用
<a name="zsEAo"></a>
#### 删除事件（解绑事件）
删除事件的方式

- 传统方式：eventTarget.onclick = null
- 方法监听注册方式： eventTarget.removeEventListener(type,listener[, useCapture]

与attachEvent相对应的eventTarget.detachEvent(eventNameWithOn,callback)
<a name="KoWQ1"></a>
#### DOM事件流
事件流描述的是从页面中接收事件的顺序。<br />事件发生时会在元素节点之间按照待定的顺序传播，这个传播过程即DOM事件流<br />DOM事件流分为3个阶段：1.捕获阶段，2.当前目标阶段，3.冒泡阶段

- 事件冒泡：IE 最早提出，事件开始时由最具体的元素接收，然后逐级向上传播到DOM最顶层节点的过程
- 事件捕获：网景最早提出，由DOM最顶层节点开始，然后逐级向下传播到到最具体的元素接收的过程

JS代码只能执行捕获或者冒泡其中的一个阶段

- onclick和attachEvent只能得到冒泡阶段
- addEventListener（type，listener[，useCapture]）第三个参数如果是true，表示在事件捕获阶段调用事件处理程序；如果是false（不写默认就是false），表示在事件冒泡阶段调用事件处理程序

实际开发中我们很少使用事件捕获，我们更关注事件冒泡

- 有些事件是没有冒泡的，比如onblur、onfocus、onmouseover、onmouseleave
- 事件冒泡有时候会带来麻烦，有时候又会帮助很巧妙的做某些事情
<a name="sEPfR"></a>
####  事件对象
事件对象：event就是一个事件对象，写在我们侦听函数的小括号里面，当形参来看

- div.onclick = function(event){}
   - event对象代表事件的状态，比如键盘按键的状态、鼠标的位置、鼠标按钮的状态。

简单理解：事件发生后，跟事件相关的一系列信息数据的集合都放到这个对象里面，这个对象就是事件对象event，他有很多属性和方法。<br />比如：谁绑定了这个事件；鼠标触发事件的话，会得到鼠标的相关信息，如鼠标位置；键盘触发事件的话，会得到键盘的相关信息，如按了哪个键。<br />事件对象是我们事件的一系列相关数据的集合，跟事件相关的，比如鼠标点击里面就包含了鼠标的相关信息：鼠标坐标等，如果是键盘事件里面就包含了键盘事件的信息，比如，判断用户按下了那个键<br />使用语法：这个event是个形参，系统帮我们设定为事件对象，不需要传递实参过去。<br />当我们注册事件时，event对象就会被系统自动创建，并以此传递给事件监听器（事件处理函数）<br />事件对象只有有了事件才会存在，他是系统给我们自动创建的，不需要我们传递参数<br />这个事件对象我们可以自己命名，比如event，eve，e
<a name="ZocDc"></a>
#### 常见事件对象的属性和方法
e.target -> 返回触发/点击事件的对象（元素）

- 与this的差别：this返回的是绑定事件的对象（元素），
- 跟this有个非常相似的属性currentTarget，ie678无法使用
- 兼容性问题：ie678使用，e.srcElement

e.type返回事件的类型，比如click，mouseover

- 阻止默认行为（事件），让链接不跳转，或者让提交按钮不提交

监听器注册方式：e.preventDefault(）方法 标准写法

- 传统注册方式：e.preventDefault(）方法 标准写法
<a name="SyYd1"></a>
####  阻止事件冒泡
阻止事件冒泡的两种方式

- 事件冒泡：开始时由最具体的元素接收，然后逐级向上传播到DOM最顶层节点
- 阻止事件冒泡标准写法：利用事件对象里面的stopPropagation（）方法
- 非标准写法：ie678利用事件对象cancelBubble属性

事件委托（代理、委派）

- 事件委托也称为事件代理，在JQuery里面称为事件委派
- 事件委托的原理：不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点；事件委托的作用：只操作了一次DOM，提高了程序的性能
<a name="Uqa61"></a>
#### 常用的鼠标事件
常用的鼠标事件：onclick鼠标点击左键触发，onmouseover鼠标经过触发，onmouseout鼠标离开触发，onfocus获得鼠标焦点触发，onblur失去鼠标焦点触发<br />禁止鼠标右键菜单contextmenu主要控制应该何时显示上下文菜单，主要用于程序员取消静默的上下文菜单<br />禁止鼠标选中（selectstart开始选中）

- 鼠标事件对象，MouseEvent
   - e.clientX返回鼠标相对于浏览器窗口可视区的X坐标	
   - e.clientY返回鼠标相对于浏览器窗口可视区的Y坐标
   - e.pageX返回鼠标相对于文档页面的X坐标，IE9以上支持
   - e.pageY返回鼠标相对于文档页面的Y坐标，IE9以上支持
   - e.screenX返回鼠标相对于电脑屏幕的X坐标
   - e.screenY返回鼠标相对于电脑屏幕的Y坐标
- 鼠标移动事件：mousemove
<a name="hLWL8"></a>
#### 常用的键盘事件

- 常用的键盘事件：onkeyup某个键盘按键被松开时触发，
- onkeydown某个键盘按键被按下时触发（不松开一直触发）
- onkeypress某个键盘按键被按下时触发，但是他不识别功能键，比如Ctrl，shift箭头等 （不松开一直触发）
   - 三个事件的执行顺序：keydown – keypress – keyup
- 键盘事件对象，keyboardEvent
- keycode返回该键的ASCII值，我们可以利用keycode返回的ASCII值来判断用户按下了那个键
   - keyup和keydown事件不区分字母大小写，a 和 A 得到的都是65
   - keypress事件区分字母大小写，a得到的是97，A 得到的是65

![image.png](https://cdn.nlark.com/yuque/0/2023/png/34882321/1677712844511-c2988699-b004-44ac-80bd-158857e50f9f.png#averageHue=%23fcfcfc&clientId=uadc4b7f8-9970-4&from=paste&height=1460&id=ued658f80&name=image.png&originHeight=2920&originWidth=1445&originalType=binary&ratio=2&rotation=0&showTitle=false&size=379804&status=done&style=none&taskId=u29a58ff8-dae8-4428-9583-2a738472eb5&title=&width=722.5)
