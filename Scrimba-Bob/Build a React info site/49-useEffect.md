# 作用

useEffect是一种替代类组件生命周期方法的方式，它允许我们告诉React在组件渲染时需要执行那些副作用操作，

useEffect接受两个参数：第一参数是函数，它会在每次渲染后执行。第二个参数是一个数组，它是可选的，它告诉React依赖项是否发生变化，如果依赖项没有变化，React就不会重复执行函数

# 第二个参数

### 不传递第二个参数

useEffect不传递第二个参数会导致每次渲染都会运行useEffect。然后，当它运行时，它获取数据并更新状态。然后，一旦状态更新，组件将重新呈现，这将再次触发useEffect，这就是问题所在。

我们每次set状态之后，他都会进行渲染，然后下面的代码就会一直运行

##### 代码

~~~jsx
import React from "react"

export default function App() {
    const [starWarsData, setStarWarsData] = React.useState({})
    const [count, setCount] = React.useState(0)
    
    console.log("Component rendered")
    
    React.useEffect(() => {
        console.log("Effect function ran")
    })
    
    return (
        <div>
            <pre>{JSON.stringify(starWarsData, null, 2)}</pre>
            <h2>The count is {count}</h2>
            <button onClick={() => setCount(prevCount => prevCount + 1)}>Add</button>
        </div>
    )
}

~~~

##### 效果图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob30.PNG

### 传递空参数

仅在挂载和卸载的时候运行函数（第一个参数）

如果第二个参数是空数组的话，就相当于告诉React，只需要在第一次运行的时候进行渲染，所以他将会停止，当组件进行第一次运行之后

对于这个代码来说，系统只会运行一次“Effect ran”，之后无论我们点击几次Add按钮，也只会有一个

##### 代码

~~~jsx
import React from "react"

export default function App() {
    const [starWarsData, setStarWarsData] = React.useState({})
    const [count, setCount] = React.useState(0)
    
    console.log("Component rendered")
    
    React.useEffect(() => {
        console.log("Effect function ran")
    },[])
    
    return (
        <div>
            <pre>{JSON.stringify(starWarsData, null, 2)}</pre>
            <h2>The count is {count}</h2>
            <button onClick={() => setCount(prevCount => prevCount + 1)}>Add</button>
        </div>
    )
}
~~~

##### 效果图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob31.PNG

### 传递一个值

count更新时执行

如果我们想让count每次改变的时候都运行这个代码，我们就[count]

最开始第二个参数的数组是[0]，点一次Add按钮之后变成了[1]，然后函数会将[0]和[1]进行比较，如果两次的值不一样，系统将会再次运行这个函数（再次渲染）

##### 代码

~~~jsx
import React from "react"

export default function App() {
    const [starWarsData, setStarWarsData] = React.useState({})
    const [count, setCount] = React.useState(0)
    
    console.log("Component rendered")
    
    React.useEffect(() => {
        console.log("Effect function ran")
    },[count])
    
    return (
        <div>
            <pre>{JSON.stringify(starWarsData, null, 2)}</pre>
            <h2>The count is {count}</h2>
            <button onClick={() => setCount(prevCount => prevCount + 1)}>Add</button>
        </div>
    )
}

~~~

##### 效果图

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob33.PNG
