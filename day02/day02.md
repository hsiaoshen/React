# 今天小结

babel的存在是为了将es6转为es5
## propTypes

设置组件属性的类型,如果不符合,;浏览器可以显示但是会报错

```html
<script type="text/babel">
  // var data = "BeiJing Cainiao";
  var data = 123;
  var Mytitle = React.createClass({
    propTypes: {
      // title: React.PropTypes.string.isRequired,
      title: React.PropTypes.number.isRequired,
    },
    render: function () {
      return <h1>{this.props.title}</h1>
    }
  })
  ReactDOM.render(
    <Mytitle  title={data} />,
    document.getElementById('example')
  )
</script>
```
## getDefaultProps

```html
<script type="text/babel">
    var data = "BeiJing Cainiao";
    var Mytitle = React.createClass({
        getDefaultProps: function(){
            return{
                title: "HTML5",
            };
        },
        render: function(){
            return <h1>{this.props.title}</h1>
        }
    });
    ReactDOM.render(
        <Mytitle />,
        document.getElementById("example")
    );
</script>
```
## this.state

这是React的组件核心之一,状态的改变会重新渲染组件的UI.只存在于组件内部

***
和this.props的区别:this.props表示那些一旦定义, 就不再改变的特性, 而this.state是会随着用户互动而产生变化的特性.
***
### 获得初始化状态:是一个方法,引用里面的状态使用this.state.liked
```html
getInitialState: function(){
                    return {liked: false};
},
```
### 状态切换

可以采用取反:!this.state.liked

### 修改状态值

每次修改后自动调用this.render方法再次渲染组件UI

```html
handleClick: function(){
    this.setState({liked: !this.state.liked});  //修改状态
},
```

## 表单:采用onChange来监听变化

由于表单是属于动态的,所以采用this.state比较好,值用event.target.value来获取

```html
inputChange: function(event){
  console.log(event.target);      //就是要监听变化的节点
   this.setState({Inputtext: event.target.value});
},
```
