# useState

### 官方学习文档

https://zh-hant.reactjs.org/docs/hooks-state.html

返回的是一个数组

~~~jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App(){
    const result = React.useState("Yes")
    console.log(result)
    return (
        <h1>{result[0]}</h1>
    )
}

ReactDOM.render(<App />, document.getElementById('root'))
~~~

### 运行结果

后台：

~~~js
["Yes", ƒ()]  //f() 为了我们做变化用，
~~~

页面：

Yes

### 语法

~~~jsx
const [state, setState] = useState(initialState)
~~~

返回一个 state，以及更新 state 的函数。

在初始渲染期间，返回的状态 (`state`) 与传入的第一个参数 (`initialState`) 值相同。

`setState` 函数用于更新 state。它接收一个新的 state 值并将组件的一次重新渲染加入队列。

将更新完的状态值重新给了state

# 所以，我们可以这样设置变量

~~~jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App(){
    const [result, setResult] = React.useState("Yes")
    console.log(result)
    return (
        <h1>result</h1>
    )
}

ReactDOM.render(<App />, document.getElementById('root'))
~~~

这样在定义变量的时候就定义成数组，

result表示的是React.useState后面括号中的内容（数组中第一个参数）

setResult表示的是数组第二个索引（函数）

### 运行结果

后台：

Yes

页面

Yes

# useState 数组中的函数

这个函数的功能就是给我们改变state的能力，变化之后的state又被存放到了第一个参数中

### 案例理解见23



