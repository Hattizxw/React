# 需求

点击Yes，可以让数据变为NO

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob07.PNG

# 代码

App.js

~~~jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App(){
    const [isImport, setIsImport] = React.useState("Yes")
    
    function handleClick (){
        setIsImport("No")
    }
    
    return (
       <div className="state">
            <h1 className="state--title">Is state important to know?</h1>
            <div className="state--value" onClick = {handleClick}>
                <h1>{isImportant}</h1>
            </div>
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

.state {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.state--title {
    text-align: center;
}

.state--value {
    background-color: white;
    height: 100px;
    width: 100px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #262626;
}
~~~

# 关于js文件的分析理解

React.useState（）中的内容是一个初始值（“Yes”）

setIsImport是一个函数，setIsImport("No")表示，函数传入的参数是No，

这个函数React已经帮我们设置了功能，改变State中的值（也就是useState数组中第一个参数的值）

# 学习网站

https://scrimba.com/learn/learnreact/changing-state-co85d4a75911c0b43ce5ad623