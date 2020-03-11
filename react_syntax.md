#### [Back to Concepts](README.md)

### How to create a react app
- Be sure that you are in the correct directory or repository
- Run `npx-create-react-app app-name` 
- If your app was created successfully the message `Happy Hacking` will print in your terminal
- `cd` into the react app that was created by the above command
- Run `npm start`
- If you app was run successfully it should automatically open in the browser at `localhost:3000`
- If you are already running something (like another react app) on port 3000 you will be prompted to run this app on the next open port


### App.js File
The App.js file in `app-name > src > app.js` is the default parent component. This component is rendered when the page is loaded as specified in the index.html file in  `app-name > public > index.html` by the `reactRender.DOM` in `app-name > src > index.js` using document selectors.

When `create-react-app` is run by `npx` this file is generated with a default image and text.
```JavaScript
import React from 'react';
import logo from './logo.svg';
import './App.css';
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}
export default App;
```

We will always delete just about everything in the `App.js` so it will look more like this
```JSX
import React from 'react';
import './App.css';
import AnyComponentYouWantToRender from `Any-Component-You-Want-To-Render file path`
function App() {
  return (
    <div className="App">
        <AnyComponentYouWantToRender/>
    </div>
  );
}
export default App;
```
Any component you want to render must be imported into the parent component and referenced by the alias.

### Function Based Components
```JSX
import React from 'react';
function ComponentName() {
    // Any JS you want to run
  return (
    <div className="CSS-Class">
        {/* Any content you want to render */}
    </div>
  );
}
export default ComponentName;
```

### Class Based Components
```JSX
import React, { Component } from 'react';
class ComponentName extends Component {
  constructor(props){
        super(props);
    }
    render() {
        // Any JS you want to run
        return (
            <div className="CSS-Class">
                {/* Any content you want to render */}
            </div>
        );
    }
}
export default ComponentName;
```

### Passing Properties to Components
Values can be passed from a parent component to a child component when that component is referenced. 

Parent Component

Values are passed to child components in the component reference. The basics syntax is `propertyName = propertyValue`
```JSX
import React from 'react';
import './App.css';
import ChildClassComponent from `./component/ChildClassComponent`;
import ChildFunctionComponent from `./component/ChildFunctionComponent`;
function App() {
    let studentName = "Autumn";
    return (
        <div className="App">
            <ChildClassComponent myName = {studentName}/>
            <ChildFunctionComponent myName = {studentName}/>
        </div>
    );
}
export default App;
```
Child Class Based Component

Properties passed from a parent component are referenced in a child class based component by `this.props.propertyName`. `props` is an object.

Class based components `extend` the base `Component` class which is exported at the beginning of every file. This base class gives you access to `this.props`
```JSX
import React, { Component } from 'react';
class ChildClassComponent extends Component {
  constructor(props){
        super(props);
    }
    render() {
        return (
            <div className="CSS-Class">
                <h1>Hello {this.props.myName}</h1>
            </div>
        );
    }
}
export default ChildClassComponent;
```
Child Function Based Component

Properties passed from a parent component are referenced in a child function based component by `props.propertyName`. `props` is an object.

`props` is accepted as a parameters for function based components.
```JSX
import React from 'react';
function ChildFunctionComponent(props) {
  return (
    <div className="CSS-Class">
        <h1>Hello {props.myName}</h1>
    </div>
  );
}
export default ChildFunctionComponent;
```
