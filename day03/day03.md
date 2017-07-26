# 今日小结

## 父子组件

在父组件中调用子组件并作为props给子组件传参

## 表单与事件

可以用onChange来监听input的变化
***
event.preventDefault()将通知 Web 浏览器不要执行与事件关联的默认动作（如果存在这样的动作）。例如，如果 type 属性是 "submit"，在事件传播的任意阶段可以调用任意的事件句柄，通过调用该方法，可以阻止提交表单。注意，如果 Event 对象的 cancelable 属性是 fasle，那么就没有默认动作，或者不能阻止默认动作。无论哪种情况，调用该方法都没有作用。
***
### htmlFor

for 属性规定 label 与哪个表单元素绑定.for属性与input的id一致,作用是将label和input的关联起来,当点击label时input聚焦,在react中要写成htmlFor.(显示关联)

### 事件
[React的官方文档](https://facebook.github.io/react/docs/)

## React Components的生命周期
