# What do we usually use `.map()` for in React?

Convert an array of raw data into an array of JSX elements
that can be displayed on the page.

# 目的

将网页需要用到的数据（数组）进行批量管理

用map（）方法将所有元素都统一成组件的形式

# 实现

### 准备工作

##### 第一步 放数据

我们将数据都放到了

jokesData.js文件中了

~~~js
export default [
    {
        id: 1
        setup: "I got my daughter a fridge for her birthday.",
        punchline: "I can't wait to see her face light up when she opens it."
    },
    {
        id: 2
        setup: "How did the hacker escape the police?",
        punchline: "He just ransomware!"
    },
    {
        id: 3
        setup: "Why don't pirates travel on mountain roads?",
        punchline: "Scurvy."
    },
    {
        id: 4
        setup: "Why do bees stay in the hive in the winter?",
        punchline: "Swarm."
    },
    {
        id: 5
        setup: "What's the best thing about Switzerland?",
        punchline: "I don't know, but the flag is a big plus!"
    }
]
~~~

**注意：**

要将数组暴露

##### 第二步 创建组件

创建好Joke.js组件

~~~js
import React from "react"

export default function Joke(props) {
    return (
        <div>
            {props.setup && <h3>Setup: {props.setup}</h3>}
            <p>Punchline: {props.punchline}</p>
            <hr />
        </div>
    )
}
~~~

##### 第三步 引入文件

将上面两个文件引入到App.js中

~~~js
import React from "react"
import Joke from "./Joke"
import jokesData from "./jokesData"
~~~

##### 第四步 开始将数据写入网页中

~~~js
export default function App() {
    const jokeElements = jokesData.map(joke => {
        return <Joke setup = {joke.setup} punchline = {joke.punchline} />
    })
    return (
        <div>
            {jokeElements}
        </div>
    )
}
~~~

###### 解析

~~~js
const jokeElements = jokesData.map(joke => {
        return <Joke setup = {joke.setup} punchline = {joke.punchline} />
    })
~~~

这里用了map方法，将数组中的所有**对象**都放到了Joke组件中

~~~js
setup = {joke.setup} punchline = {joke.punchline}
~~~

这些是Joke组件中的属性，在Joke.js文件中渲染到页面中去

###### 简化版本的箭头函数

~~~js
const jokeElements = jokesData.map(joke =>  
        <Joke setup = {joke.setup} punchline = {joke.punchline} />
    )
~~~

是对一下代码的简化

~~~js
 			<Joke 
                punchline="It’s hard to explain puns to kleptomaniacs because they always take things literally."
            />
            <Joke 
                setup="I got my daughter a fridge for her birthday." 
                punchline="I can't wait to see her face light up when she opens it." 
            />
            <Joke 
                setup="How did the hacker escape the police?" 
                punchline="He just ransomware!"
            />
            <Joke 
                setup="Why don't pirates travel on mountain roads?" 
                punchline="Scurvy." 
            />
            <Joke 
                setup="Why do bees stay in the hive in the winter?" 
                punchline="Swarm." 
            />
            <Joke 
                setup="What's the best thing about Switzerland?" 
                punchline="I don't know, but the flag is a big plus!" 
            />
~~~

# 写此代码时的思路

在Joke组件中，我们要传入两个属性，setup和punchline，

如何传入呢？

用js方法，

而且数组中存的时对象

所以是 joke.setup

# 每一个信息应该都有独一无二的Key

所以我们最好加上key

~~~js
<Joke key = {joke.id} setup = {joke.setup} punchline = {joke.punchline} />
~~~

# 教学视频网站

https://scrimba.com/learn/learnreact/mapping-components-co20249b69609b9df5473acc7
