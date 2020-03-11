#### [Back to Concepts](README.md)

### What is JSX:
React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both. React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects. This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions. You can put any valid JavaScript expression inside the curly braces in JSX.

## Example JSX in Function Based Component
```JSX
function ComponentName() {
    let myName = "Autumn"
    return (
        <div>
            <h1>Hello {myName}<h1>
        </div>
  );
}
```
## Example JSX in Class Based Component
```JSX
class ComponentName extends Component {
    render() {
        let myName = "Autumn"
        return (
            <div>
                <h1>Hello {myName}<h1>
            </div>
        );
    }
}
```

When rendering HTML with JSX you MUST nest elements in a parent element.
```JSX
// INCORRECT
class IncorrectComponent extends Component {
    render() {
        return (
            <h1>Learning JSX is Fun<h1>
            <h3>JSX is a syntax extension for JS<h3>
        );
    }
}
```

```JSX
// CORRECT
class CorrectComponent extends Component {
    render() {
        return (
            <div>
               <h1>Learning JSX is Fun<h1>
                <h3>JSX is a syntax extension for JS<h3>
            </div>
        );
    }
}
```
[Reference](https://reactjs.org/docs/introducing-jsx.html)