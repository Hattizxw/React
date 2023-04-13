# 需求

点击方框，方框背景颜色进行变换

# 代码

### box.js

~~~jsx
import React from "react"

export default function Box(props) {
    
    const [on, setOn] = React.useState(props.on)
    
    function toggles (){
        setOn(prevState => !prevState)
    }
    
    const styles = {
        backgroundColor: on ? "#222222" : "transparent"
    }
    
    return (
        <div style={styles} className="box" onClick = {toggles}></div>
    )
}
~~~

其他文件代码不变

这种，在每一个box中都初始化on的值，并且在box组件中对on进行变换，它是指改变了此时on的值，不会对App中的state进行改变，且只是更新了local state

# 学习网址

https://scrimba.com/learn/learnreact/boxes-challenge-part-31-local-state-co0264ad6929a556e38a6a10f

# 37

我们之后将state放到App.js文件中去