# 需求

点击按钮，添加事件

# 运行结果

### 初始状态

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob10.PNG

### 运行状态

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob11.PNG

# 学习网址

https://scrimba.com/learn/learnreact/complex-state-arrays-co8f0498bb502fff29cbc8ee5

# 代码

### jsx

~~~jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App() {
    //状态设置
    //注意数组初始化状态
    const [thingsArray, setThingsArray] = React.useState(["Thing 1", "Thing 2"])
    
    function addItem() {
        // Build from scratch :)
        //要用箭头函数，不能直接设置状态，因为我们还需要之前的状态
        //这里不能直接写prevState.push()因为这个函数返回值是数组的个数，并不是数组里面的内容
        setThingsArray(prevState => [...prevState, `Thing ${prevState.length + 1}`])
    }
    
    //将内容放到p标签中渲染到页面中
    const thingsElement = thingsArray.map(thing => <p key = {thing}>{thing}</p>)
    
    return (
        <div>
            <button onClick = {addItem}>Add Item</button>
            {thingsElement}
        </div>
    )
}

ReactDOM.render(<App />, document.getElementById('root'));
~~~

### css

~~~css
* {
    box-sizing: border-box;
}

body {
    background-color: #70B85D;
    color: white;
    padding: 20px;
    font-family: 'Karla', sans-serif;
    font-size: 1.3rem;
}

button {
    width: 100%;
    background-color: transparent;
    padding: 1rem;
    color: white;
    border: 2px solid white;
    border-radius: 50px;
    cursor: pointer;
    font-family: 'Karla', sans-serif;
    margin-bottom: 20px;
}

button:hover {
    background-color: #FFFEF1;
    color: #2C5E2E;
}

button:focus {
    outline: 0;
}
~~~

