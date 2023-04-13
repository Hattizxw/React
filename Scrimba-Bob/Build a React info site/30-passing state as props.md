# 需求

还是24中的那个练习，

我们需要做的是通过props来传递state

# 原来的代码写法

### app.js

~~~jsx
export default function App() {
    const [count, setCount] = React.useState(0)
    
    function add() {
        setCount(prevCount => prevCount + 1)
    }
    
    function subtract() {
        setCount(prevCount => prevCount - 1)
    }
    
    return (
        <div className="counter">
            <button className="counter--minus" onClick={subtract}>–</button>
            <div className="counter--count">
                <h1>{count}</h1>
            </div>
            <button className="counter--plus" onClick={add}>+</button>
        </div>
    )
}
~~~

# 修改之后的代码

### App.js

~~~jsx
import React from "react"
import Count from "./Count.js"

export default function App() {
    const [count, setCount] = React.useState(0)
    
    function add() {
        setCount(prevCount => prevCount + 1)
    }
    
    function subtract() {
        setCount(prevCount => prevCount - 1)
    }
    
    return (
        <div className="counter">
            <button className="counter--minus" onClick={subtract}>–</button>
            <div className="counter--count">
                <Count number = {count}/>
            </div>
            <button className="counter--plus" onClick={add}>+</button>
        </div>
    )
}
~~~

Count.js

~~~jsx
import React from "react"

function Count (props){
    return (
        <div className="counter--count">
            <h1>{props.number}</h1>
        </div>
    )
}

export default Count
~~~

### 解析

这样做可以提高代码的复用率，

将count当作属性传递给了Count组件