# 需求

拖动窗口大小，页面上窗口大小数字自动变换

### 改进之前的代码

App.js

~~~jsx
import React from "react"
import WindowTracker from "./WindowTracker"

export default function App() {
    /**
     * Challenge:
     * 1. Create state called `show`, default to `true`
     * 2. When the button is clicked, toggle `show`
     * 3. Only display `<WindowTracker>` if `show` is `true`
     */
    
    const [show, setShow] = React.useState(true)
    
    function toggle() {
        setShow(prevShow => !prevShow)
    }
    
    return (
        <div className="container">
            <button onClick={toggle}>
                Toggle WindowTracker
            </button>
            {show && <WindowTracker />}
        </div>
    )
}

~~~

WindowTracker.js

~~~jsx
import React from "react"

export default function WindowTracker() {
    return (
        <h1>Window width: {window.innerWidth}</h1>
    )
}
~~~

style.css

~~~css
* {
    box-sizing: border-box;
}

body {
    background-color: #FF7C43;
    color: white;
    margin: 0;
    padding: 2rem;
}

.container{
    display: flex;
    flex-direction: column;
}

button {
    border: none;
    border-radius: 5px;
    padding: 1rem;
    cursor: pointer;
}

h1 {
    text-align: center;
}
~~~

现在代码呈现出来的是：当我们拖动页面大小，Window width: 后面的值并不会自动变换，需要我们人工点击刷新页面才可以，（因为，当我们刷新页面，组件才会被重新渲染，新的数字才会显示）

现在我们用useEffect解决这个问题

让它满足改变页面大小，Window width:的值自动变换

# 分析

~~~jsx
<h1 onResize>Window width: {window.innerWidth}</h1>
~~~

直接在WindowTracker上面添加onResize事件是不行的，因为这样问题得不到解决，我们要想展示数据，还是需要刷新页面，组件重新被渲染之后才会显示

# 修改之后的代码

WindowTracker.js

~~~jsx
import React from "react"

export default function WindowTracker() {
    
    const [windowWidth, setWindowWidth] = React.useState(window.innerWidth)
    
    //当组件被渲染第一次的时候，就给window绑定了一个事件，所以我们每次改变大小的时候resize就会发挥作用，setWindow大小都会改变，所以里面的值自然就会改变
    //即使是show = false，事件还是会被绑定，window的大小还是会被测量，只不过页面没有被渲染，无法显示出来
    
    React.useEffect( ()=> {
        window.addEventListener("resize", function() {
            setWindowWidth(window.innerWidth)
        })
    }, [])
    
    
    return (
        <h1>Window width: {windowWidth}</h1>
    )
}

~~~

# 再次升级

### 上次存在的问题

当show的值为false是，会有警告产生（就是组件不被渲染，但是给window注册的resize事件还在）

### 这次解决

这次我们要在当show 的值为false的时候，给window移除resize事件

### 代码

~~~jsx
import React from "react"

export default function WindowTracker() {
    
    const [windowWidth, setWindowWidth] = React.useState(window.innerWidth)
    
    React.useEffect(() => {
        function watchWidth() {
            console.log("Setting up...")
            setWindowWidth(window.innerWidth)
        }
        
        window.addEventListener("resize", watchWidth)
        
        return function() {
            console.log("Cleaning up...")
            window.removeEventListener("resize", watchWidth)
        }
    }, [])
    
    return (
        <h1>Window width: {windowWidth}</h1>
    )
}
~~~

当show的值为false的时候，useEffect执行return里面的函数，所以resize事件会被解绑

