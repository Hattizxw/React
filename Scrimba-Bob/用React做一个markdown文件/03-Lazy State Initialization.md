对于const[... , set...] = React.useState来说，每次对状态进行重新设置之后，组件将会被重新渲染，但是有些初始化的内容将会被无数次的初始化

例如

~~~jsx
const [state, setState] = React.useState(console.log("State initialization"))
~~~

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob36.PNG

但是，如果我们把

~~~jsx
const [state, setState] = React.useState(console.log("State initialization"))
~~~

变成完整的函数，或者箭头函数，他也会变成**lazy State Initialization**，只被运行一次

~~~jsx
 const [state, setState] = React.useState(
        function() { 
            return console.log("State initialization")
        }
    )
~~~

~~~jsx
const [state, setState] = React.useState(
        () => console.log("State initialization")
    )
~~~



# 解决02中的问题

所以，我们只想要页面在初次加载的时候加载notes数组（只需要初始化一次，）

我们需要给useState加上箭头函数

~~~jsx
const [notes, setNotes] = React.useState(
        () => JSON.parse(localStorage.getItem("notes")) || []
    )
~~~

Lazily initialize our `notes` state so it doesn't reach into localStorage on every single re-render of the App component