# React

MVC框架

##  核心思想

封装组件，各个组件维护自己的状态和UI，当状态变更，自动重新渲染整个组件。

## 组件

React应用都是构建在组件上的，组件的2个核心一个是props属性，一个就是状态state



## 环境配置

### 本地包下载

[官网](https://facebook.github.io/react/docs/installation.html)

### 引入cdn

```html
<!-- 注意按以下顺序 -->
  <script src="http://cdn.bootcss.com/react/15.6.1/react.js"></script>
  <script src="http://cdn.bootcss.com/react/15.6.1/react-dom.js"></script>
  <!-- 不能太高，现在可用5.8.38版本 -->
  <script src="http://cdn.bootcss.com/babel-core/5.8.38/browser.js"></script>
```

## 基本结构

```html
<script type="text/babel">
//组件部分
 var CommentBox = React.createClass({
    render: function(){
      return(
        <h1>Hello</h1>
      )
    }
 })
 // 应用
 ReactDOM.render(
  <CommentBox />,    //调用组件
  document.body
 )
</script> 
```
*****
注意事项:

1. script的类型必须是"text/babel"
1. 由于组件的使用和标签很相似，为了区别必须首字母大写
1. 组件有且仅有一个元素，就是说return里面的元素没有兄弟，但可以有父子，可以多子
1. render这个必须是这个单词不能更换
1. 注释写在标签里面会显示出来
1. 在return里面的js操作用{}包含起来，变量也用{变量名}
*****
