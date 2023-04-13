# 需求

在33的基础上进行优化

我们在index.js中的<App/>中传入一个属性（布尔值），这个属性决定背景颜色

如果属性值是真，则颜色为：\#222222，若是假，颜色为：\#cccccc

# 代码

### index.js

~~~jsx
import React from "react"
import ReactDOM from "react-dom"
import App from "./App"

ReactDOM.render(<App darkMode={false} />, document.getElementById("root"))
~~~

### App.js

~~~jsx
import React from "react"
import boxes from "./boxes"

export default function App(props) {
    
    const[squares, setSquares] = React.useState(boxes)
    
    const styles = {
        backgroundColor: props.darkMode ? "#222222" : "#cccccc"
    }
    
    const boxesElement = squares.map(box =>
        <div style = {styles} className = "box" key = {box.id}></div>
    )
    
    return (
        <main>
            {boxesElement}
        </main>
    )
}

~~~

# 学习网站

https://scrimba.com/learn/learnreact/dynamic-styles-co57845e4a49eb86d4414b0fd