# 需求

点击“Show Puchuline” 按钮显示内容，否则隐藏

还是Joke的那个案例

# 代码

### Joke.js

~~~jsx
import React from "react"

export default function Joke(props) {
    
    const [isShown, setIsShown] = React.useState(false)
    
    function toggleShown (){
        setIsShown (prevIsShown => !prevIsShown)
    }
    
    return (
        <div>
            <h3>{props.setup}</h3>
            {isShown && <p>{props.punchline}</p>}
            {isShown && <button onClick={toggleShown}>Hide Punchline</button>}
            {!isShown && <button onClick={toggleShown}>Show Punchline</button>}
            <hr />
        </div>
    )
}
~~~

### App.js

~~~jsx
import React from "react"
import Joke from "./Joke"
import jokesData from "./jokesData"

export default function App() {
    const jokeElements = jokesData.map(joke => {
        return (
            <Joke 
                key={joke.id}
                setup={joke.setup} 
                punchline={joke.punchline} 
            />
        )
    })
    return (
        <div>
            {jokeElements}
        </div>
    )
}
~~~

### jokesData.js

数据内容

~~~jsx
export default [
    {
        id: 1,
        setup: "I got my daughter a fridge for her birthday.",
        punchline: "I can't wait to see her face light up when she opens it."
    },
    {
        id: 2,
        setup: "How did the hacker escape the police?",
        punchline: "He just ransomware!"
    },
    {
        id: 3,
        setup: "Why don't pirates travel on mountain roads?",
        punchline: "Scurvy."
    },
    {
        id: 4,
        setup: "Why do bees stay in the hive in the winter?",
        punchline: "Swarm."
    },
    {
        id: 5,
        setup: "What's the best thing about Switzerland?",
        punchline: "I don't know, but the flag is a big plus!"
    }
]
~~~

# 运行结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob20.PNG



# 简化

~~~jsx
{isShown && <button onClick={toggleShown}>Hide Punchline</button>}
{!isShown && <button onClick={toggleShown}>Show Punchline</button>}
~~~

可以简化为

~~~jsx
<button onClick = {toggleShown}>{isShown ? "Hide" : "Show"} Punchline</button>
~~~

