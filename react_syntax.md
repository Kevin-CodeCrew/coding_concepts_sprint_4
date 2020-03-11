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
```JavaScript
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
```JavaScript
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
