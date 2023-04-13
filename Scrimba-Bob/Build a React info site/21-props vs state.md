# Props 不可修改

### 概念

props指的是传递到一个组件中的属性，保证其可以正常工作，类似于一个函数接受参数的方式（从函数内部接受固定的参数值）

一个组件中的props值是**不允许被修改的**，

### 代码理解

~~~js
function addTwoNumbers(a, b) {
    a = 42
    return a + b
}

console.log(addTwoNumbers(1, 2))
~~~

例如这个函数，当我们从外面传入参数（1和2），但是函数体里面也定义了一个a的值，

此时，传入的a值就是无效值

~~~js
function Navbar(props) {
    props.coverImage = "something else"
}

<Navbar coverImage="some-image2" />
~~~

React当中的Props就相当于函数传递参数，

当我们在组件中定义了一个属性值（ props.coverImage），则通过标签传递进去的属性值也是无效值。

并且，无论传入的props值还是我们在组件中定义的props值，都是**不可修改的**

# State 可以修改

### 概念

State refers to values that are managed by the component, similar to variables declared inside a function. Any time you have changing values that should be saved/displayed, you will likely be using state

### 通俗来说

A way for React to remember saved values from within a component.

# When would you want to use props instead of state?

Anytime you want to pass data into a component so that
component can determine what will get displayed on the
screen.

# When would you want to use state instead of props?

Anytime you want a component to maintain some values from
within the component. (And "remember" those values even
when React re-renders the component)