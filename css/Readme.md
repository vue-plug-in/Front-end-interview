# Css

- [**`1.怎么让一个不定宽高的div垂直水平居中`**](#怎么让一个不定宽高的div垂直水平居中)
- [**`2.清除浮动的方法`**](#清除浮动的方法)


## 怎么让一个不定宽高的div垂直水平居中
### flex
- 只需要在父盒子设置：`display: flex; justify-content: center;align-items: center;`

### 使用CSS3 transform
- 1.父盒子设置: `position:relative`
- 2.Div 设置: `transform: translate(-50%，-50%);position: absolute;top: 50%;left: 50%;`

### 使用 display:table-cell 方法
- 1.父盒子设置:`display:table-cell; text-align:center;vertical-align:middle;`
- 2.Div 设置: `display:inline-block;vertical-align:middle;`


## 清除浮动的方法

### 给父级定高度:不推荐使用

### 使用空元素
