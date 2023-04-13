# State只能父组件传给子组件

不能子组件传递给父组件，也不能同级组件直接互相传递

### 父组件传递给子组件通过props来传递

##### 不可传递的情况

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob14.PNG

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob15.PNG

##### 可以传递的情况

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob16.PNG

# 例子

### App.js

~~~jsx
import React from "react"
import Header from "./Header"
import Body from "./Body"

export default function App() {
    
    const [user, setUser] = React.useState("Joe")
    
    return (
        <main>
            <Header userName = {user}/>
            <Body userName = {user}/>
        </main>
    )
}
~~~

### Header.js文件

~~~jsx
import React from "react"

export default function Header(props) {
    
    return (
        <header>
            <p>Current user: {props.userName}</p>
        </header>
    )
}
~~~

### Body.js文件

~~~jsx
import React from "react"

export default function Body(props) {
    return (
        <section>
            <h1>Welcome back, {props.userName}!</h1>
        </section>
    )
}
~~~

在这个例子中，Header和Body属于同级的组件，但是他们都需要用到一样的State，所以，我们可以把state涉及到App.js文件中

# 学习网站

https://scrimba.com/learn/learnreact/passing-data-around-coc1c4e8db27909ac7f804244