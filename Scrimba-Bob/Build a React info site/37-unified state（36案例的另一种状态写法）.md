# 原理

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob19.PNG

我们给<App/>组件创建一个toggle（）函数，通过这个函数，给到给到我们每一个box实例，

任何时候，当我们点击box组件，他将通过toggle函数告诉<App/>组件，里面的某一个box的state需要改变，然后，渲染改变之后的<App/>组件。

# 代码

### App.js

~~~jsx
import React from "react"
import boxes from "./boxes"
import Box from "./Box"

export default function App() {
    const [squares, setSquares] = React.useState(boxes)
    
    //这个函数传入id这个参数主要的原因就是为了，当用户点击某一个方框，id于Box.js文件中的onClick点击事件联系就可以知道用户点击的是哪一个id（id的具体数字）
    function toggle(id) {
        setSquares(prevSquares => {
            //创建新的数组，存放新的所有方框的数据
            const newSquares = []
            for(let i = 0; i < prevSquares.length; i++) {
                const currentSquare = prevSquares[i]
                //判断点击是不是此时这个方框
                //如果是
                if(currentSquare.id === id) {
                    //跟新数组中的内容（对象跟新的方法）
                    const updatedSquare = {
                        ...currentSquare,
                        //改变on值
                        on: !currentSquare.on
                    }
                    //跟新完之后将数组添加到新数组中
                    newSquares.push(updatedSquare)
                } else {
                    //如果不是这个方框
                    //那就直接将这个方框对象中的所有数据放到新数组中
                    newSquares.push(currentSquare)
                }
            }
            //一定要记住要返回最后的这个新数组
            return newSquares
        })
    }
    
    //必须写这个，不能直接在return中返回<Box>标签，因为数据是数组的形式存在，那样子，需要引入n（几个数组就是几）个标签，并且引入不同的数值
    //注意，这里是squares.map不是boxes.map
    //因为我们要获取的是最新的状态，而不是boxes.js文件中不变的数值
    const squareElements = squares.map(square => (
        <Box 
            key={square.id} 
            id={square.id}
            on={square.on} 
            toggle={toggle}
        />
    ))
    
    return (
        <main>
            {squareElements}
        </main>
    )
}
~~~

### Box.js

~~~jsx
import React from "react"

export default function Box(props) {
    const styles = {
        backgroundColor: props.on ? "#222222" : "transparent"
    }
    
    return (
        <div 
            style={styles} 
            className="box"
            onClick={()=>props.toggle(props.id)}
        >
        </div>
    )
}
~~~

### boxes.js

~~~jsx
export default [
    {
        id: 1,
        on: true
    },   
    {
        id: 2,
        on: false
    },   
    {
        id: 3,
        on: true
    },   
    {
        id: 4,
        on: true
    },   
    {
        id: 5,
        on: false
    },   
    {
        id: 6,
        on: false
    },   
]
~~~

### style.css

~~~css
* {
    box-sizing: border-box;
}

.box {
    height: 100px;
    width: 100px;
    border: 1px solid black;
    display: inline-block;
    margin-right: 4px;
    border-radius: 5px;
}
~~~

# 简化代码

我们可以对App.js代码进行简化

（if...else...大部分都可以写成三元表达式）

~~~jsx
import React from "react"
import boxes from "./boxes"
import Box from "./Box"

export default function App() {
    const [squares, setSquares] = React.useState(boxes)
    
    function toggle(id) {
        //我们对squares状态进行设置
        setSquares(prevSquares => {
            //新的状态要返回一个数组，我们要对数组中每一项进行操作
            return prevSquares.map((square) => {
                //判断：数组中的每一个对象的id是不是和用户点击到的id（toggle函数中参数的id）一样，如果一样，改变对象中的on值，如果不一样，还是square
                return square.id === id ? {...square, on: !square.on} : square
            })
        })
    }
    
    const squareElements = squares.map(square => (
        <Box 
            key={square.id} 
            id={square.id}
            on={square.on} 
            toggle={toggle}
        />
    ))
    
    return (
        <main>
            {squareElements}
        </main>
    )
}

~~~

# 学习网站

https://scrimba.com/learn/learnreact/boxes-challenge-part-5-cobdb4d3e907fa304af4b9958
