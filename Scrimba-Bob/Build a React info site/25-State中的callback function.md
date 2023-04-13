通常用于，我们还需要之前的State值

**返回新的状态**

~~~jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App(){
    const [count, setCount] = React.useState(0)
    
    function plus() {
        setCount(prevCount => prevCount + 1)
    }
    
    function minus() {
        setCount(prevCount => prevCount - 1)
    }
    
    return (
        <div className="counter">
            <button className="counter--minus" onClick = {minus}>–</button>
            <div className="counter--count">
                <h1>{count}</h1>
            </div>
            <button className="counter--plus" onClick = {plus}>+</button>
        </div>
    )
}

ReactDOM.render(<App />, document.getElementById('root'))
~~~

if you ever need the old value of state to help you determine the new value of state, you should pass a callback function to your state setter function instead of using state directly. This callback function will receive the old value of state as its parameter, which you can then use to determine your new value of state.