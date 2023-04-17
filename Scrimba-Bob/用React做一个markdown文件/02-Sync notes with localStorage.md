# localStorage

**`localStorage`**接口的只读属性允许[`window`](https://developer.mozilla.org/en-US/docs/Web/API/Window)您访问[`Storage`](https://developer.mozilla.org/en-US/docs/Web/API/Storage)对象[`Document`](https://developer.mozilla.org/en-US/docs/Web/API/Document)的[来源](https://developer.mozilla.org/en-US/docs/Glossary/Origin)；存储的数据跨浏览器会话保存。

`localStorage`类似于[`sessionStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage)，不同之处在于虽然`localStorage`数据没有过期时间，但是`sessionStorage`当页面会话结束时数据会被清除——也就是说，当页面关闭时。（`localStorage`当最后一个“私人”选项卡关闭时，在“私人浏览”或“隐身”会话中加载的文档数据将被清除。）

### 作用

[`Storage`](https://developer.mozilla.org/en-US/docs/Web/API/Storage)可用于访问当前源的本地存储空间的对象。

# 语法

localStorage.getItem("key")   

key: 项目获取保存在local Storage中数据路径的一种方式，我们通常用notes来称呼key

localStorage.setItem("key", value)

如果我们想要储存数据在local storage中，将路径保存在key中，value是我们想要保存的值

**value必须是一个字符串**

如果我们想要保存比较复杂的value，例如对象和数组，我们需要用：

**`JSON.stringify（value）`**（将数组和对象转完成字符串，保存在local Storage）

取出数据我们需要用

**`JSON.parse（stringifiedValue）`**

这两个的使用规则如下

1. Every time the **array changes**, save it  in localStorage. You'll need to use JSON.stringify()  to turn the array into a string to save in localStorage.

2. **When the app first loads**, initialize the notes state  with the notes saved in localStorage. You'll need to  use JSON.parse() to turn the stringified array back into a real JS array.

# 案例

我们用localStorage的两种语法给一个笔记软件添加功能：

刷新页面，数据不会被跟新

且，两个挑战如下

1. Every time the **array changes**, save it  in localStorage. You'll need to use JSON.stringify()  to turn the array into a string to save in localStorage.

2. **When the app first loads**, initialize the notes state  with the notes saved in localStorage. You'll need to  use JSON.parse() to turn the stringified array back into a real JS array.

### 完整代码

~~~jsx
import React from "react"
import Sidebar from "./components/Sidebar"
import Editor from "./components/Editor"
import { data } from "./data"
import Split from "react-split"
import {nanoid} from "nanoid"

export default function App() {
    
    const [notes, setNotes] = React.useState(
        JSON.parse(localStorage.getItem("notes")) || []
    )
    const [currentNoteId, setCurrentNoteId] = React.useState(
        (notes[0] && notes[0].id) || ""
    )
    
    React.useEffect(() => {
        localStorage.setItem("notes", JSON.stringify(notes))
    }, [notes])
    
    function createNewNote() {
        const newNote = {
            id: nanoid(),
            body: "# Type your markdown note's title here"
        }
        setNotes(prevNotes => [newNote, ...prevNotes])
        setCurrentNoteId(newNote.id)
    }
    
    function updateNote(text) {
        setNotes(oldNotes => oldNotes.map(oldNote => {
            return oldNote.id === currentNoteId
                ? { ...oldNote, body: text }
                : oldNote
        }))
    }
    
    function findCurrentNote() {
        return notes.find(note => {
            return note.id === currentNoteId
        }) || notes[0]
    }
    
    return (
        <main>
        {
            notes.length > 0 
            ?
            <Split 
                sizes={[30, 70]} 
                direction="horizontal" 
                className="split"
            >
                <Sidebar
                    notes={notes}
                    currentNote={findCurrentNote()}
                    setCurrentNoteId={setCurrentNoteId}
                    newNote={createNewNote}
                />
                {
                    currentNoteId && 
                    notes.length > 0 &&
                    <Editor 
                        currentNote={findCurrentNote()} 
                        updateNote={updateNote} 
                    />
                }
            </Split>
            :
            <div className="no-notes">
                <h1>You have no notes</h1>
                <button 
                    className="first-note" 
                    onClick={createNewNote}
                >
                    Create one now
                </button>
            </div>
            
        }
        </main>
    )
}

~~~

### 重点代码

~~~jsx
const [notes, setNotes] = React.useState(
        JSON.parse(localStorage.getItem("notes")) || []
    )

    React.useEffect(() => {
        localStorage.setItem("notes", JSON.stringify(notes))
    }, [notes])
~~~

### 重点代码解析

1. 为什么要用useEffect
   - 因为这个功能属于side effect，和渲染没有关系的一个功能，我们要满足的是：在每次改变**notes数组**的时候，我们要将数据保存在localStorage中，所以要将数据输入进去
   - 因为每次notes数组更新就需要存入数据，所以我们useEffect需要第二个参数[notes]
2. 初始化notes数组的时候为什么这样写
   - 因为我们要先获取原有的notes，如果原来的notes为空，那localStorage.getItem("notes")返回的就是null，然后 JSON.parse(localStorage.getItem("notes"))返回的也是null，那就变成了false || []，只能执行后面的，给notes创建空数组
3. 为什么加JSON.parse，
   - 因为localStorage.getItem("notes")返回的是stringifiedValue

### 运行结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob35.PNG

刷新之后还是这个

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob35.PNG

# 学习网站

https://scrimba.com/learn/learnreact/notes-app-sync-notes-with-localstorage-co3c5495b8d7949e81b79988a