#### [Back to Concepts](README.md)

In applications with many components, it’s very important to free up resources taken by the components when they are destroyed.
We can declare special methods on the component class to run some code when a component mounts and unmounts.

The componentDidMount() method is called after the component is rendered.
This is where you run statements that requires that the component is already placed in the DOM.
```JSX
componentDidMount(){

}
```

```JSX
componentWillUnmount(){
    
}
```

[Reference - React Docs](https://reactjs.org/docs/state-and-lifecycle.html#adding-lifecycle-methods-to-a-class)
[Reference - W3Schools](https://www.w3schools.com/react/react_lifecycle.asp)