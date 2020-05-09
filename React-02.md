### 组件的数据挂载props和prop-types

```jsx
``ccr起步
class App extends Component {
    render() {
        console.log(this.props)
        return (
            /*必须有一个根标签*/
           /* 可以为空，也可以使用react中的Fragment当作标签*/
            <>
                <TodoHeader title="待办事项">today to do</TodoHeader>
                <TodoInput btn="ADO"/>
                <TodoList/>
            </>
        );
    }
}
```

```jsx
<TodoHeader title="待办事项">today to do</TodoHeader>
// this.props  --->  {title="待办事项",childern="today to do"}
```

传数字的时候需要加大括号，否则变string

```shell
npm install --save prop-types   
```

```jsx
/!检测组件的props 用porp-types
```

```jsx
import React from 'react';
import PropTypes from 'prop-types';
/! Method 1
class MyComponent extends React.Component {
  render() { <h1 title={555}>welecome</h1>}}
MyComponent.propTypes = {
 title: PropTypes.number.isRequired,
 children: PropTypes.string.isRequired,}
```

```jsx
/! Method 2
class App extends Component {
    static propTypes = {
        y : PropTypes.string.isRequired
    };
     render() { <h1 y="555"></h1>}}
 //必须是propTypes    
```

