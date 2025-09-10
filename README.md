# 基于Vue3框架的一个互动小说

本项目使用json撰写小说文本

```json
{
  "展示模式":[
    {"text":"本项目基于Vue.js前端框架开发","type":"Left","goto":1},
    {"text":"这是一款可以由json数据驱动的页面应用","type":"Left","goto":2},
    {"text":"本应用利用前端这一“新媒体”技术，对小说进行部分视听化的改编","type":"Left","goto":3},
    {"text":"具有一定的互动性","type":"Left","goto":4},
    {"text":"下面介绍本应用的特色","type":"Left","goto":5},
    {"text":"文字可以按照左右排版","type":"Right","goto":6},
    {"text":"文字也可以放在中间","type":"Center","goto":7},
    {"text":"文字也可以设置颜色","type":"Left","goto":8},
    {"text":"红色","type":"Right","goto":9,"color":"red"},
    {"text":"绿色","type":"Right","goto":10,"color":"green"},
    {"text":"蓝色","type":"Right","goto":11,"color":"blue"},
    {"text":"可以为对话创建头像","type":"Left","goto":12},
    {"text":"头像可以指定内容","type":"Right","goto":13,"avatar":"AVA"},
    {"text":"也可以发送图片","type":"Left","goto":14},
    {"text":"background.jpg","type":"Image Right","goto":15},
    {"text":"可以使用多种事件","type":"Left","goto":16},
    {"text":"触发切换背景事件","type":"Right","goto":17,"event":[{"e":"ChangeBG","val":"background.jpg"}]},
    {"text":"类似的，可以播放歌曲","type":"Left","goto":18},
    {"text":"同时切换背景和音乐","type":"Right","goto":19,"event":[{"e":"ChangeBG","val":""},{"e":"AudioPlay","val":"青空.mp3"}]},
    {"text":"最后展示的是分支功能","type":"Left","goto":20},
    {"text":["点我回到上一句话","点我切换音乐","点我切换背景","点我结束展示"],"type":"Choice","jump":[18,20,21,22]},
    {"text":"切换音乐中","type":"Center","goto":18,"event":[{"e":"AudioPlay","val":"星茶会.mp3"}]},
    {"text":"切换背景中","type":"Center","goto":18,"event":[{"e":"ChangeBG","val":"bg2.jpeg"}]},
    {"text":"下面是我们小说创作的心路历程","type":"Right","goto":-1}
  ]
}
```

json从标题属性开始，表示对话的开始，属性的值为一个列表，列表中的每一个对象代表一句话。  
text是需要显示的内容，当type不为"choice"时，它的值是一个字符串
type是要显示的文字的样式，可以在以下选项中选择

> Left  
> Right  
> Center  
> Image Left  
> Image Right  
> Choice 

当type为Image时，text的值是图片的路径+名字字符串  
当type为Choice时，text的值是一个字符串列表，表示列出的选项  
当type为Choice时，需要另外提供一个jump属性，值为列表，长度与选项数量相等，代表对应选项选择后会跳转到哪里
color是需要显示的文字的颜色，值为有效的颜色字符串，缺省则默认为白色  
avatar是对话中的头像，值为字符串，缺省则不显示  
event表示显示该文本时触发的事件，值为一个列表，列表中的每一项为一对象，对象含有两个属性，一个是"e"，一个是"val"，其中e的可选值为

>ChangeBG  
>AudioPlay  

val为对应的路径字符串，为空时则取消背景&取消音乐

index为这句话的索引，可以缺省

goto为这句话的后一句话的位置，值为index
