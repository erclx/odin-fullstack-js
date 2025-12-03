# 📜 Class Based Components

**React Course**

### Introduction

Before functional components became standard, React used class-based components. You will likely encounter them in legacy codebases. This lesson explores how to write them and use concepts like props and state within them.

-----

### 📝 Lesson Overview

  * Learn the structure of a class component.
  * How to use props and state in class components.
  * Highlight the uses of `this` in class components.

-----

### 🏛️ The Structure of a Class Component

To create a class component, you must extend `React.Component`.

```javascript
import { Component } from "react";

class ClassInput extends Component {
  constructor(props) {
    super(props);
    // Initialize state here
  }

  // Lifecycle methods and custom methods here

  render() {
    return (
      // JSX goes here
    );
  }
}

export default ClassInput;
```

-----

### 📦 Props and Constructor

Props are passed to the class constructor. You must call `super(props)` to use `this.props` inside the constructor.

  * In the `render()` method and other methods, you access props using **`this.props`**.

<!-- end list -->

```javascript
constructor(props) {
  super(props);
}

render() {
  return <h1>{this.props.name}</h1>;
}
```

-----

### 💾 State in Class Components

In class components, state is an **object** initialized in the constructor. You cannot use the `useState` hook here.

  * **Initialize State:** `this.state = { ... }` in the constructor.
  * **Update State:** Use **`this.setState(...)`**. React merges the object you provide with the current state.

<!-- end list -->

```javascript
constructor(props) {
  super(props);
  this.state = {
    todos: [],
    inputVal: "",
  };
}
```

-----

### 🔗 Binding Methods and `this`

Unlike functional components, methods in a class are not bound by default. If you try to use `this.setState` inside a method called by an event handler, `this` will be undefined.

**Solution 1: Bind in Constructor**

```javascript
constructor(props) {
  super(props);
  // ... state init
  this.handleInputChange = this.handleInputChange.bind(this);
}

handleInputChange(e) {
  this.setState({ inputVal: e.target.value });
}
```

**Solution 2: Arrow Functions (Class Fields)**
Arrow functions automatically bind `this` to the class instance.

```javascript
handleInputChange = (e) => {
  this.setState({ inputVal: e.target.value });
}
```

-----

### 🖼️ Rendering JSX

Class components must have a **`render()`** method. This is where you return your JSX.

```javascript
render() {
  return (
    <section>
      <h3>{this.props.name}</h3>
      {/* ... rest of your JSX */}
    </section>
  );
}
```

-----

### 📚 Assignment

1.  **Implement a delete button** for each task in the class component example. It should remove the task from the state array.
2.  **Implement a `Count` class component** that displays the total number of todos.
3.  **Implement an edit button** that replaces a todo with an input field to update the task.

-----

### 🤔 Knowledge Check

  * How do props get used in a class-based component?
  * How does JSX get displayed?
  * How do we deal with state in a class-based component?
  * How do you restore the context of `this` in a method?