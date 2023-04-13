# 给元素绑定事件

### 1. 小驼峰命名法

### 2. 引用函数的时候只写函数名，不写（）

因为

~~~jsx
<button onClick={handleClick()}>Click me</button>
~~~

如果这样写，代表着只要代码一运行到这里就会调用handleClick这个函数，不会在乎前面添加的点击事件

# 例子

~~~jsx
import React from "react"

export default function App() {
    function handleClick() {
        console.log("I was clicked!")
    }
    
    function handleOnMouseOver() {
        console.log("MouseOver")
    }
    
    return (
        <div className="container">
            <img 
                src="https://picsum.photos/640/360" 
                onMouseOver={handleOnMouseOver} 
            />
            <button onClick={handleClick}>Click me</button>
        </div>
    )
}
~~~

### 步骤

1. 添加事件（**小驼峰命名法**）
2. 定义函数
3. 引用函数，注意**不要写小括号**