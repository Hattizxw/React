# 练习一

~~~js
const nums = [1, 2, 3, 4, 5]

const squares = nums.map(function (num){
    return num * num
})

console.log(squares);
~~~

也可以使用**箭头函数**

~~~js
const nums = [1, 2, 3, 4, 5]

const squares = nums.map((num)=>{
    return num * num
})

console.log(squares)
~~~

# 练习二

~~~js
const names = ["alice", "bob", "charlie", "danielle"]
// -->        ["Alice", "Bob", "Charlie", "Danielle"]
// Your code here
const capitalized = names.map((name) => {
    return name[0].toUpperCase() + name.slice(1)
})

console.log(capitalized)
~~~

### 代码含义

~~~js
return name[0].toUpperCase() + name.slice(1)
})
~~~

在这个代码中，name代表的是数组中的每一个元素，所以name[0]表示的是每一个字符串中的第一个字母

~~~js
["A", "B", "C", "D"]
~~~

**slice()方法**中应该有两个参数，

第一个参数表示从第几个字母开始提取（包括这个索引）

第二个参数表示到第几个字母结束（不包括所写的索引）

name.slice(1)，则表示，从第一个开始，直到结束

# 练习三

~~~js
const pokemon = ["Bulbasaur", "Charmander", "Squirtle"]
// -->          ["<p>Bulbasaur</p>", "<p>Charmander</p>", "<p>Squirtle</p>"]
// Your code here

const paragraphs = pokemon.map((mon) => {
    return `<p>${mon}</p>`
})

console.log(paragraphs)
~~~

结果

~~~js
["<p>Bulbasaur</p>", "<p>Charmander</p>", "<p>Squirtle</p>"]
~~~

### 注意

是反引号

反引号里面是js的内容，里面加动态标量要有$

### 简化

~~~js
const paragraphs = pokemon.map(mon => `<p>${mon}</p>`)
~~~

**mon为参数，后面为返回值**