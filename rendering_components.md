###### Top
#### [Back to Concepts](README.md)

### Creating a class based component
```JSX
import React, { Component } from 'react';
class ParentComponent extends Component {
    constructor(props){
        super(props);
    }
    render() {
        return (
            <div>
                <h1>I'm the parent component!</h1>
            </div>
        );
    }
}
export default ParentComponent;
```

### Rendering a component in a the default parent component
```JSX
import React from 'react';
import './App.css';
import ParentComponent from './components/ParentComponent'
function App() {
  return (
    <div className="App">
      <h1>I'm the default parent component</h1>
      <ParentComponent/>
    </div>
  );
}
export default App;
```
### Rendering a child component
```JSX
import React, { Component } from 'react';
class ChildComponent extends Component {
    constructor(props){
        super(props);
    }
    render() {
        return (
            <div>
                <h1>I'm the child component!</h1>
                <h3>The parent component told me to say {this.props.message}</h3>
            </div>
        );
    }
}
export default ChildComponent;
```
```JSX
import React, { Component } from 'react';
import ChildComponent from './components/ChildComponent'
class ParentComponent extends Component {
    constructor(props){
        super(props);
    }
    render() {
        return (
            <div>
                <h1>I'm the parent component!</h1>
                <ChildComponent message = "The parent component is super cool"/>
            </div>
        );
    }
}
export default ParentComponent;
```
### Rendering child components using map
```JSX
import React, { Component } from 'react';
import ChildComponent from './components/ChildComponent'
class ParentComponent extends Component {
    constructor(props){
        super(props);
    }
    render() {
        let messageArray = ["You're doing great", "React is cool", "Learning is fun"]
        return (
            <div>
                <h1>I'm the parent component!</h1>
                <div>
                {
                    messageArray.map( (message, index) => {
                        return(
                            <ChildComponent key = {index} message = {message}/>
                        )
                    })
                }
                </div>
            </div>
        );
    }
}
export default ParentComponent;
```
### Rendering content using map
```JSX
import React, { Component } from 'react';
class ParentComponent extends Component {
    constructor(props){
        super(props);
    }
    render() {
        let messageArray = ["You're doing great", "React is cool", "Learning is fun"]
        return (
            <div>
                <h1>I'm the parent component!</h1>
                <div>
                {
                    messageArray.map((message, index) => {
                        return(
                            <div key = {index}>
                                <p>Here's some encouragement : {message}</p>
                            </div>
                        )
                    })
                }
                </div>
            </div>
        );
    }
}
export default ParentComponent;
```
[Assignment](assignments.md#03/11/2020)

[Back to Top](#Top)