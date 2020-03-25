###### Top
#### [Back to Concepts](README.md)

### What are routes:
React router is a routing library built on top of the react which is used to create the routing in react apps. In single page apps, there is only single html page.we are reusing the same html page to render the different components based on the navigation.
But in multipage apps, you will get an entirely new page from the server when you navigate.

When using router you will always import `BrowserRouter as Router` `Link` and `Route`. These imports come from `react-router-dom` which has to be installed. `react-router-dom` is installed by running the command `npm install react-router-dom` in the terminal inside your react app.

All things associated with routes (routes and link) must be nested under the `Router` tag. The element tag `Link` is a router link and has at least one attribute `to`. This attribute determines which path to match when the link is clicked. The element tag `Route` has at least one attribute `path`. The attribute defines a path that will render referenced component.

## Example 
```JSX
import React, { Component, Fragment } from 'react';
import FilmList from './FilmList'
import DrinkList from './DrinkList';
import { BrowserRouter as Router, Link, Route } from 'react-router-dom' // imports to use Router
class AppContainer extends Component {
// display title with links to home, film list, and drink list
    render() {
        return (
            <Fragment>
                <h1>React Routes Lecture</h1>
                <Router>

                    <Link to="/">Home</Link>
                    <Link to="/films">Films</Link>
                    <Link to="/drinks">Drinks</Link>

                    <Route path="/films">
                        <FilmList />
                    </Route>

                    <Route path="/drinks">
                        <DrinkList />
                    </Route>

                </Router>
            </Fragment>
        )
    }
}
export default AppContainer;
```
[Reference](https://reacttraining.com/react-router/web/example/basic)

[Reference](https://codeburst.io/getting-started-with-react-router-5c978f70df91)

[Assignment](assignments.md#03/24/2020)

[Back to Top](#Top)