# 语法规范

### 1. 定义虚拟DOM时不要写引号

### 2. 标签中混入JS表达式时需要用{}。（也就是将固定内容换成标量代替时）

注意是js表达式

所以{}中不能写js代码（比如for，if代码）

##### js表达式

一个表达式会产生一个值，可以放在任何一个需要值的地方

​	下面这些都是表达式：

1. a
2. a + b
3. demo（1）   //这个是函数调用表达式
4. arr.map()  //将数组加工
5. function test() {}

（简单方法判断，在写表达式之前写一个 const x = ，如果x可以接收到值，则表示他是一个表达式，否则不是）

##### js代码（语句）

控制代码走向

1. if （）{}
2. for（）{}
3. swith（）{case：}

~~~JavaScript
<script type="text/babel">
        //创建虚拟DOM
        const myid = 'Yee'
        const myDate = 'Hello Yee'
        const VDOM = (
            <h2 id = {myid}>
                <span>{myDate}</span>    
            </h2>
        )
        //渲染，将虚拟DOM渲染到页面中
        ReactDOM.render(VDOM,document.getElementById('test'))
</script>
~~~

### 3. 样式的类名指定（标签）不要用class，要用className

~~~css
<style>
        .title {
            background-color: pink;
            width: 200px;
        }
</style>
~~~

~~~JavaScript
<script type="text/babel">
        //创建虚拟DOM
        const myid = 'Yee'
        const myDate = 'Hello Yee'
        const VDOM = (
            <h2 className = "title" id = {myid}>
                <span>{myDate}</span>    
            </h2>
        )
        //渲染，将虚拟DOM渲染到页面中
        ReactDOM.render(VDOM, document.getElementById('test'))
</script>
~~~

### 4. 写标签内置样式（内联样式）

不能直接写style = “”

我们要用js的方法写，style = {{key: value}}

（这里面两个花括号，第一个花括号代表你要写的内容是**js**，第二个花括号表示里面的样式用**对象的方式**表示）

**注意：**如果属性名称是两个单词组成需要用小驼峰的形式eg：fontSize

~~~JavaScript
<script type="text/babel">
        //创建虚拟DOM
        const myid = 'Yee'
        const myDate = 'Hello Yee'
        const VDOM = (
            <h2 className = "title" id = {myid}>
                <span style = {{color: 'white', fontSize: '20px'}}>{myDate}</span>    
            </h2>
        )
        //渲染，将虚拟DOM渲染到页面中
        ReactDOM.render(VDOM, document.getElementById('test'))
</script>
~~~

### 5. 每个虚拟DOM只能有一个根标签

​	如果需要放入多个标签，需要将他们用一个大的div标签给包起来

~~~JavaScript
<script type="text/babel">
        //创建虚拟DOM
        const myid = 'Yee'
        const myDate = 'Hello Yee'
        const VDOM = (
            <div>
                <h2 className="title" id={myid}>
                    <span style={{ color: 'white', fontSize: '20px' }}>{myDate}</span>
                </h2>
                <h2 className="title" id= 'CouYee'>
                    <span style={{ color: 'white', fontSize: '20px' }}>{myDate}</span>
                </h2>
            </div>
        )
        //渲染，将虚拟DOM渲染到页面中
        ReactDOM.render(VDOM, document.getElementById('test'))
    </script>
~~~

### 6. 标签必须闭合

1. 当我们输入input标签时，系统提示是<input type="text">，但是我们需要将标签闭合，在最后输入一个"/" <input type="text"/>

~~~javascript
<script type="text/babel">
        //创建虚拟DOM
        const myid = 'Yee'
        const myDate = 'Hello Yee'
        const VDOM = (
            <div>
                <h2 className="title" id={myid}>
                    <span style={{ color: 'white', fontSize: '20px' }}>{myDate}</span>
                </h2>
                <input type="text"/>
            </div>
        )
        //渲染，将虚拟DOM渲染到页面中
        ReactDOM.render(VDOM, document.getElementById('test'))
</script>
~~~

### 7. 标签首字母

1. **若小写字母开头**，则将标签转为html中同名元素，若html中无该标签对应的同名元素则报错
2. **若大写字母开头**，React就去渲染对应的组件，若组件没有定义，则报错

