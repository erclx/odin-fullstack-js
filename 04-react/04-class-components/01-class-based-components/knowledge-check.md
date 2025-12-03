### Knowledge Check Answers 🎯

-----

**Question: How do props get used in a class-based component?**

**Answer:** You access them via **`this.props`**.

**Why:** In class components, props are passed to the `constructor` (often handled by `super(props)`). Because the component is an instance of a class, the props are attached to `this` context.

**Example:**

```javascript
class Welcome extends Component {
  render() {
    // Accessed via 'this'
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

-----

**Question: How does JSX get displayed?**

**Answer:** JSX is displayed by returning it specifically from the **`render()` method**.

**Why:** Unlike functional components where you just return JSX from the function body, class components require a specific method named `render()` to tell React what to put in the DOM.

**Example:**

```javascript
class MyComponent extends Component {
  render() {
    return <div>I am being displayed!</div>;
  }
}
```

-----

**Question: How do we deal with state in a class-based component?**

**Answer:** You initialize state as an object in the **`constructor`** and update it using **`this.setState()`**.

**Why:** State in classes is an object stored on the instance (`this.state`). You cannot mutate it directly (e.g., `this.state.count = 1`); you must use the built-in `setState` method to trigger a re-render.

**Example:**

```javascript
constructor(props) {
  super(props);
  // 1. Initialize
  this.state = { count: 0 };
}

updateCount() {
  // 2. Update
  this.setState({ count: 1 });
}
```

-----

**Question: How do you restore the context of `this` in a method?**

**Answer:** You must **bind** the method in the constructor, or use **arrow function** syntax for the method.

**Why:** In JavaScript classes, custom methods generally lose their `this` context when passed as event handlers. Binding them ensures `this` refers to the component instance so you can access `this.state` or `this.setState`.

**Example:**

```javascript
constructor(props) {
  super(props);
  // Binding in constructor
  this.handleClick = this.handleClick.bind(this);
}

// OR use Arrow Function (automatically binds 'this')
handleClick = () => {
  console.log(this.state);
}
```

