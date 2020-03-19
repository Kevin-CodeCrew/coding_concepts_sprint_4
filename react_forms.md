###### Top
#### [Back to Concepts](README.md)

## React Forms and Controlled Components

### What are React Forms:
HTML form elements work a little bit differently from other DOM elements in React, because form elements naturally keep some internal state.  It’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form. The standard way to achieve this is with a technique called “controlled components”.

In HTML, form elements such as `<input>`, `<textarea>`, and `<select>` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().

We can combine the two by making the React state be the “single source of truth”. Then the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a “controlled component”.

[Source](https://reactjs.org/docs/forms.html)
## Simple Form with Controlled Components
Define your class and set a property of state that you will update via input 
```JSX
import React, {Component} from 'react';
class NameForm extends Component {
  constructor(props) {
    super(props);
    this.state = {
      value: ''
      };
  }
```
Event handler to update state
``` JSX
  handleChange(event) {
    this.setState({value: event.target.value});
  }
```
Event handler for form submission
```JSX
  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }
```
Display form and reference event handlers
```JSX
  render() {
    return (
      <form>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <button onClick = {this.handleSubmit}>Submit</button>
      </form>
    );
  }
}
export default NameForm;
```

[Back to Top](#Top)
## Forms with Multiple Input Fields with Controlled Components
```JSX
import React, { Component } from 'react';

class AddAdoptionForm extends Component {
    constructor(props) {
        super(props);
        // set initial state
        this.state = {
            dogName : "",
            dogAge : 0,
            dogBreed : "",
            dogTraining : false,
            dogColor : "",
        }
    }

    // one event handler to conditionally update state
    handleChange = (event) => {
        if(event.target.name === "dogName"){
            this.setState({dogName : event.target.value})
        } else if(event.target.name === "dogAge") {
            this.setState({dogAge : event.target.value})
        } else if(event.target.name === "dogBreed") {
            this.setState({dogBreed : event.target.value})
        } else if(event.target.name === "dogTraining") {
          // toggle check setting opposite of current value in state
            this.setState({dogTraining : !this.state.dogTraining}) 
            console.log(event.target)
        } else if(event.target.name === "dogColor") {
            this.setState({dogColor : event.target.value})
        }
    }

    handleSubmission = (event) => {
        event.preventDefault(); // keep page from reloading
        // set state to initial values
        this.setState({
            dogName : "",
            dogAge : 0,
            dogBreed : "",
            dogTraining : false,
            dogColor : "",
        })
    }

    // render form
    render() {
        return (
            <div>
                <form action="">
                    <fieldset>
                        <legend>Find Your Dog a Home</legend>

                        <div className="formGroup">
                            <label htmlFor="dogName">Dog Name : </label>
                            <input type="text" name="dogName" id="dogName" 
                            value = {this.state.dogName} onChange = {this.handleChange}/>
                        </div>

                        <div className="formGroup">
                            <label htmlFor="dogAge">Dog Age : </label>
                            <input type="number" name="dogAge" id="dogAge" 
                            value = {this.state.dogAge} onChange = {this.handleChange}/>
                        </div>

                        <div className="formGroup">
                            <label htmlFor="dogBreed">Dog Breed : </label>
                            <input type="text" name="dogBreed" id="dogBreed" 
                            value = {this.state.dogBreed} onChange = {this.handleChange}/>
                        </div>

                        <div className="formGroup">
                            <p>Is your dog potty trained?</p>
                            <label htmlFor="dogTraining">Yes : </label>
                            <input type="checkbox" id="dogTraining" name="dogTraining" 
                            checked = {this.state.dogTraining} onChange = {this.handleChange}/>
                        </div>

                        <div className="formGroup">
                            <label htmlFor="dogColor">Dog Color : </label>
                            <select id="dogColor" name = "dogColor" 
                            value = {this.state.dogColor} onChange = {this.handleChange}>
                                <option value=" ">--</option>
                                <option value="white">white</option>
                                <option value="black">black</option>
                                <option value="brown">brown</option>
                                <option value="spotted">spotted</option>
                                <option value="other">other</option>
                            </select>
                        </div>

                        <button onClick = {this.handleSubmission}>Find Them a Home</button>

                    </fieldset>
                </form>
            </div>
        )
    }
}

export default AddAdoptionForm;
```
### Additional information:
- [Form Components in React Video 1](https://youtu.be/fd4_IEWzYeo)
- [Form Components in React Video 2](https://youtu.be/doshF5Alr-k)

[Back to Top](#Top)