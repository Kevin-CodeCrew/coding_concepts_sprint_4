###### Top
#### [Back to Concepts](README.md)

### What is Conditional Rendering:
In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application. Conditional rendering in React works the same way conditions work in JavaScript. Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them.

You can use variables to store elements. This can help you conditionally render a part of the component while the rest of the output doesn’t change. You can also return completely different HTML in a component depending on a flag.

[Source](https://reactjs.org/docs/conditional-rendering.html)
## Conditional Rendering Using Element Variables
Set up your class based components and set flags as properties of state for conditional rendering
```JSX
import React, { Component } from 'react';
import Login from './Login';
import SignUp from './SignUp';

class AppContainer extends Component {
    constructor(props) {
        super(props);
        // set initial state
        this.state = {
            isLoggingIn: false, // flag for conditionally rendering log in component
            isSigningIn: false,// flag for conditionally rendering sign in component
        }
    }
```
Event handlers to update flags for conditional rendering
```JSX
    // event handler - tied to onClick to update state of conditional render flags to display log in component
    updateIsLoggingIn = () => {
        this.setState({ isSigningIn: false });
        this.setState({ isLoggingIn: true });
    }
    // event handler - tied to onClick to update state of conditional render flags to display sign in component
    updateIsSigningIn = () => {
        this.setState({ isLoggingIn: false });
        this.setState({ isSigningIn: true });
    }
```
Conditionally set value of element variable based on flags
```JSX
    // display title, buttons, and sign in OR log in form
    render() {
        // declare variable as undefined
        let userForm;
        if (this.state.isLoggingIn) {
            // render the log in component
            userForm = <Login />
        } else if (this.state.isSigningIn) {
            // render the sign up component
            userForm = <SignUp />
        }
        return (
            <div>
                <h1>20-03-19 React Conditional Rendering Lecture</h1>
                <button onClick={this.updateIsLoggingIn}>Log In</button>
                <button onClick={this.updateIsSigningIn}>Sign Up</button>
                <div>
                    {userForm}
                </div>
            </div>
        )
    }
}

export default AppContainer;
```
## Conditional Rendering Using Return
Set up your class based components and set flag as a property of state for conditional rendering
```JSX
import React, { Component } from 'react';

class Login extends Component {
    constructor(props) {
        super(props);
        // setting initial state to be updated by form input
        this.state = {
            userName: "", // form field
            password: "", // form field
            hasBeenSubmitted: false, // flag for conditional render
        }
    }
```
form field event handler
```JSX
    // conditional event handler - tied to onChange event listener to update state
    handleChange = (event) => {
        // define variables to represent event.target properties
        let fieldName = event.target.name;
        let fieldValue = event.target.value;
        // conditionally update state
        if (fieldName === "userName") {
            this.setState({ [fieldName]: fieldValue })
        } else if (fieldName === "password") {
            this.setState({ [fieldName]: fieldValue })
        }
    }
```
form submission event handler - update flag when submitted
```JSX
    // event handler - tied to onClick event listener 
    handleSubmission = (event) => {
        event.preventDefault(); // keeps the page from reloading
        console.log(this.state); // prints form values
        this.setState({ hasBeenSubmitted: true }) // update flag for conditional rendering
    }
```
Render method with conditional return
```JSX
    render() {
        // if the if statement evaluates to true 
        // display a success message
        if (this.state.hasBeenSubmitted) {
            return (
                <div>
                    <h1>You've Logged In</h1>
                    <h2>Welcome Back : {this.state.userName}</h2>
                </div>
            )
        }
```
```JSX
        // if the if statement evaluates to false 
        // display a sign up form using controlled components
        return (
            <div>
                <form action="">
                    <fieldset>
                        <legend>Log In!</legend>

                        <div className="formGroup">
                            <label htmlFor="userName">User Name : </label>
                            <input type="text" name="userName" id="userName" value={this.state.userName} onChange={this.handleChange} />
                        </div>

                        <div className="formGroup">
                            <label htmlFor="password">Password : </label>
                            <input type="password" name="password" id="password" value={this.state.password} onChange={this.handleChange} />
                        </div>
                        <button onClick={this.handleSubmission}>Log In</button>
                    </fieldset>
                </form>
            </div>
        )
    }
}

export default Login;
```
[Back to Top](#Top)