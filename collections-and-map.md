###### Top
#### [Back to Concepts](README.md)
# Collections and Map in React

### Using Require:
`require()` is a function that returns exported data from a JS file. The function take one parameter, the file path of the JS file you wish the evaluate. The returned value must be saved in a variable 

## Example 
```JSX
import React, { Component } from 'react';
class DataComponent extends Component {
    constructor(props){
        super(props);
        this.state = {
            dataArray : [],
        }
    }
    componentDidMount(){
        const data = require('./rawData.js')
        this.setState({ dataArray : data})
    }
```
Use map to render data on page
```JSX
    render() {
        return (
            this.state.dataArray.map((item) => {
                return (
                    <div key={item.id}>
                        <p>Item Name: {item.name}</p>
                        <p>Item Price: {item.price}</p>
                        <img src="{item.imgUrl}" alt="{item.name}"/>
                    </div>
                )
            })
        );
    }
}

export default DataComponent;
```
You can also use map to render child component for each object in the json array and render the information from props in the child
```JSX
    render() {
        return (
            this.state.dataArray.map((item) => {
                return (
                    <div key={item.id}>
                        <FormatterChild itemName = {item.name} 
                        itemPrice = {item.price} itemImage = {item.imgUrl}/>
                    </div>
                )
            })
        );
    }
}

export default DataComponent;
```

[Assignment](assignments.md#03/18/2020)
[Back to Top](#Top)
