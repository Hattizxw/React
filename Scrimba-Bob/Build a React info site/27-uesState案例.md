# 需求

点击按钮，随机展示图片

# 代码

### jsx

~~~jsx
import React from "react"
import memesData from "../memesData.js"  //存放着照片数据

export default function Meme() {
    const [memeImage, setMemeImage] = React.useState("")
    /**
     * Challenge: Save the random meme URL in state
     * - Below the div.form, add an <img /> and set the
     *   src to the new `memeImage` state you created
     */
    
    function getMemeImage() {   //给按钮添加点击事件
        const memesArray = memesData.data.memes   //获取图片路径所在的数组
        const randomNumber = Math.floor(Math.random() * memesArray.length)   //产生数组的随机索引数
        //memesArray[randomNumber].url数组中图片
        setMemeImage(memesArray[randomNumber].url)   //改变state的值
    }
    
    return (
        <main>
            <div className="form">
                <input 
                    type="text"
                    placeholder="Top text"
                    className="form--input"
                />
                <input 
                    type="text"
                    placeholder="Bottom text"
                    className="form--input"
                />
                <button 
                    className="form--button"
                    onClick={getMemeImage}
                >
                    Get a new meme image 🖼
                </button>
            </div>
            <img src={memeImage} />   //引用最新的state值
        </main>
    )
}
~~~

### css

~~~css
export default {
    "success": true,
    "data": {
        "memes": [
            {
                "id": "181913649",
                "name": "Drake Hotline Bling",
                "url": "https://i.imgflip.com/30b1gx.jpg",
                "width": 1200,
                "height": 1200,
                "box_count": 2
            },
            {
                "id": "87743020",
                "name": "Two Buttons",
                "url": "https://i.imgflip.com/1g8my4.jpg",
                "width": 600,
                "height": 908,
                "box_count": 3
            },
        	{
                "id": "100947",
                "name": "Matrix Morpheus",
                "url": "https://i.imgflip.com/25w3.jpg",
                "width": 500,
                "height": 303,
                "box_count": 2
            }
        ]
    }
}
~~~

# 运行结果

https://react-1316943030.cos.ap-nanjing.myqcloud.com/scrimba-bob/bob09.PNG

# 学习网站

https://scrimba.com/learn/learnreact/project-add-images-to-the-meme-generator-co2e04f5499f85d20fecbdf22