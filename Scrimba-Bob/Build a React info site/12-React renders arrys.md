# 方法的作用

Returns a new array. Whatever gets returned from the callback function provided is placed at the same index in the new array.
Usually we take the items from the original array and modify themin some way.

# 例子

~~~jsx
export default function App() {
    const colors = [
            <h3>Red</h3>, 
            <h3>Orange</h3>, 
            <h3>Yellow</h3>,
            <h3>Green</h3>,
            <h3>Blue</h3>,
            <h3>Indigo</h3>,
            <h3>Violet</h3>
        ]
    return (
        <div>
            {colors}
        </div>
    )
}
~~~

# 结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob04.PNG

### 注意

自我理解，在jsx中写入js就需要加花括号，所以在div组件中写的是{colors}