# React

MVC框架，采用JSX语法

##  核心思想

封装组件，各个组件维护自己的状态和UI，当状态变更，自动重新渲染整个组件。

## 组件

React应用都是构建在组件上的，组件的2个核心一个是props属性，一个就是状态state

### props

可以把 props 看成组件的配置属性，在组件内部是不变的，只是在调用这个组件的时候传入不同的属性来定制显示这个组件。

### 虚拟DOM

好处：需要渲染的少，性能优化

原理：React的DOM结构会映射当前最新的DOM结构。当state改变时，会现在虚拟DOM上进行操作，然后和真实的DOM进行diff算法比较寻找到对应的节点，

然后调用组件渲染到实际节点处，其实不是渲染整个DOM树

## 环境配置

### 本地包下载

[官网](https://facebook.github.io/react/docs/installation.html)

### 引入cdn

```html
<!-- 注意按以下顺序 -->
  <script src="http://cdn.bootcss.com/react/15.6.1/react.js"></script>      // react核心库
  <script src="http://cdn.bootcss.com/react/15.6.1/react-dom.js"></script>   //Dom操作
   <!-- 不能太高，现在可用5.8.38版本 -->
  <script src="http://cdn.bootcss.com/babel-core/5.8.38/browser.js"></script>   
  //Browser.js的作用是将JSX语法转为Javascript语法.
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
  document.body       //要加入节点的位置
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
1. 在return()里面不要用分号
1.  ReactDOM.render中有2个参数，中间用逗号隔开
*****


## JSX的语法规则
1. js和html的搭配使用:js代码和html中需用变量用{}包含，遇到<>开头的用html规则解析，遇到{}开头用js规则解析,三种写法

```html
     render(){
       return (
         <div>
         {
           names.map(function(name){
             return <h1>{name}</h1>
           })
           /*
           names.map( (name) => {
            return <h1>{name}</h1>
           })
           */
           /*
           names.map( (name) => (<h1>{name}</h1>))
           */
         }
         </div>
       )
     }
```
2. JSX允许直接在模板插入JS变量. 如果这个变量是一个数组, 则会展开这个数组的所有成员. 

```html
<script type="text/babel">

      var arr = [
        <h1>欢迎来到北京菜鸟在线</h1>,
        <h2>我们现在学习的是React的语法知识.</h2>
      ];

   ReactDOM.render(
     <div>{arr}</div>,
     document.body
   )
</script>
```
3. 利用this.props传参数(添加组件属性, 需要注意就是class属性需要写成className, for属性需要写成htmlFor, 因为class和for是JavaScript的保留字.)
```html
<script type="text/babel">

  var HMessage = React.createClass({
    render: function(){
      return (
        <div>
        <h1 key={}>{this.props.name}</h1>
        <h1>{this.props.age}</h1>
        </div>
      );
    }
  })

   ReactDOM.render(
     <HMessage name="ZhaoSi" age="23" />,
     document.body
   );
</script>

```

4. this.props.children

****
需要注意, this.props.children 的值有三种可能, 如果当前组件没有子节点, 它就是undefined; 如果有一个子节点, 数据类型是object; 如果有多少个子节点, 数据类型就是array. 所以, 处理this.props.children的时候要小心.

React提供一个工具方法React.Children来处理this.props.children. 我们可以用React.Children.map来遍历子节点, 而不用担心this.props.children的数据类型是undefined还是object.
****
```html
      <script type="text/babel">
            var NoteList = React.createClass({
                render: function(){
                    return (
                        <ol>
                        {
                            React.Children.map(this.props.children, function(child){
                                return <li>{child}</li>
                            })
                        }
                        </ol>
                    );
                }
            });

            ReactDOM.render(
                <NoteList>
                <span>hello</span>
                <span>world</span>
                </NoteList>,
                document.body
            );
        </script>
```

