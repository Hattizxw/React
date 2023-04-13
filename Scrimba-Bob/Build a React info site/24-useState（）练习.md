# 需求

点击 + 按钮，数字加一

点击 - 按钮，数字减一

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob08.PNG

# 代码

~~~jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App(){
    const [count, setCount] = React.useState(0)
    
    function plus() {
        setCount(count+1)   //最好用回调函数写
    }
    function minus() {
        setCount(count-1)
    }
    
    return (
        <div className="counter">
            <button className="counter--minus" onClick = {minus}>–</button>
            <div className="counter--count">
                <h1>{count}</h1>
            </div>
            <button className="counter--plus" onClick = {plus}>+</button>
        </div>
    )
}

ReactDOM.render(<App />, document.getElementById('root'))
~~~

css

~~~css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: 'Inter', sans-serif;
    background-color: #262626;
    color: #D9D9D9;
    padding: 20px;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.counter {
    display: flex;
    align-items: flex-end;
}

.counter > button {
    height: 50px;
    width: 50px;
    border-radius: 50%;
    border: none;
    cursor: pointer;
    background-color: #737373;
    color: #D9D9D9;
    font-size: 1.5rem;
}

.counter > button:hover {
    background-color: #404040;
    color: #D9D9D9;
}

.counter > button:focus {
    outline: none;
}

.counter--count {
    background-color: white;
    height: 100px;
    width: 100px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #262626;
}

.counter--plus {
    margin-left: -20px;
}

.counter--minus {
    margin-right: -20px;
    z-index: 1;
}
~~~

