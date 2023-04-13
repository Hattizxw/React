# 学习网站

https://blog.csdn.net/wu_xianqiang/article/details/105181044

# 24中写的是通过一个新的state值更新，25中式通过函数式更新返回新的state

现在这两种写法没有任何区别，但是如果是异步更新的话，那你就要注意了，他们是有区别的，来看下面例子

~~~jsx
function Counter() {
	const [count, setCount] = useState(o) ;
    function handleClick() {setTimeout(() => fsetCount(count + 1)}，3000) ;}
    function handleClickFn() {
        setTimeout(() => {
            setCount((prevCount) =>{return prevCount + 1}）
        }， 3000) ;
    }
    return (
        <>
            Count: {count}
            <button onClick=fhandleClick}>+	</button>
            <button onClick=fhandleClickFn3>+</button>
        </>
    );
}
~~~

当我设置为异步更新，点击按钮延迟到3s之后去调用`setCount`函数，当我快速点击按钮时，也就是说在3s多次去触发更新，但是只有一次生效，因为 `count` 的值是没有变化的

当使用函数式更新 state 的时候，这种问题就没有了，因为它可以获取之前的 state 值，也就是代码中的 `prevCount` 每次都是最新的值。

其实这个特点和类组件中 `setState` 类似，可以接收一个新的 state 值更新，也可以函数式更新。如果新的 state 需要通过使用先前的 state 计算得出，那么就要使用函数式更新。

因为[setState](https://so.csdn.net/so/search?q=setState&spm=1001.2101.3001.7020)更新可能是异步，当你在事件绑定中操作 state 的时候，setState更新就是异步的