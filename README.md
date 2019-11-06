# React Documentation

## React Without ES6

```js
class Greeting extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>
    }
}
```

If you don't use ES6 yet, you may use the `create-react-class` module instead:

```js
var createReactClass = require('create-react-class');
var Greeting = createReactClass({
    render: function() {
        return <h1>Hello, {this.props.name}</h1>
    }
});
```

The API of ES6 classes is similar to `createReactClass()` with a few exceptions.

### Declaring Default Props

with functions and ES6 classes `defaultProps` is defined as a property on the component itself:
```js 
class Greeting extends React.Component {
    /// ...
}

Greeting.defaultProps = {
    name: 'Mary'
};
```
With `createReactClass()`, you need to define `getDefaultProps()` as a function on the passed object:

```js
var Greeting = createReactClass({
    getDefaultProps: function() {
        return {
            name: 'Mary'
        };
    },

    // ...
});
```

### Setting the Initial State

In ES6 classes, you can define the initial state by assigning `this.state` in the constructor:

```js
class Counter extends React.Component {
    constructor(props) {
        super(props);
        this.state = {count: props.initialCount};
    }
    // ...
}
```

With `createReactClass()`, you have to provide a seperate `getInitialState` method that returns the initial state:
```js
var Counter = createReactClass({
    getInitialState: function() {
        return {count: this.props.initialCount};
    },
    // ...
});
```