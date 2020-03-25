###### Top
#### [Back to Concepts](README.md)

### What is fetch: [in progress]
The Fetch API provides a JavaScript interface for accessing and manipulating parts of the HTTP pipeline, such as requests and responses. It also provides a global fetch() method that provides an easy, logical way to fetch resources asynchronously across the network.

## Example 
Fetches will be preformed in a method in the a class based component. This method will often be called by a lifecycle method. Calling the method that preforms your fetch in a lifecycle method such as `componentDidMount()` allows your fetch to run when the component mounts and update data held in state accordingly.
```JSX
    // lifecycle method - this method does not have tp be called bc it runs when the component mounts
    componentDidMount() {
        this.loadData(); // method that preforms fetch
    }
```
Fetch using async await requires the method calling the fetch to use the key word async. The key word await proceeds the fetch method and the returned value is set equal to a variable. Calling the `json()` method on that variable returns just the json data. That new value is saved into a second variable and the await key word proceeds it as well.

Be sure to *test* what is returned from you api endpoint by hitting the endpoint (going to the url) or by printing the json data in the console
```JSX
    // method that preforms fetch
    loadData = async () => {
        // fetch from api
        const response = await fetch('https://swapi.co/api/people/');
        // json only
        const json = await response.json();
        console.log(json); // test
        // update array in state
        this.setState({ dataArray : json });
    }
```
Use map to render json data on page
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

export default AppContainer;
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

export default AppContainer;
```
[Reference](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

[Dev.to Fetch Async Await Article](https://dev.to/shoupn/javascript-fetch-api-and-using-asyncawait-47mp)

[Assignment](assignments.md#03/23/2020)

[Back to Top](#Top)