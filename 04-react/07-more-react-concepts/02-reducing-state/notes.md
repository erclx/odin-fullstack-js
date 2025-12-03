# 📉 Reducing State

### Introduction

Reducers are a powerful way to manage state in React. This lesson covers what they are, when to use them, and how to implement them using the `useReducer` hook.

-----

### 📝 Lesson Overview

  * What are reducers.
  * When to use reducers.
  * What is the `useReducer` hook.

-----

### 🔧 What are Reducers?

Reducers are **pure functions** that take a **previous state** and an **action** to return a **new state**.

**The Action Object:**
This object contains a `type` property describing what the user did. It can also contain other properties (payloads) needed to compute the new state.

**Example Reducer:**

```javascript
function reducer(state, action) {
  switch (action.type) {
    case "incremented_count": {
      return { count: state.count + 1 };
    }
    case "decremented_count": {
      return { count: state.count - 1 };
    }
    case "set_count": {
      return { count: action.value };
    }
    default: {
      throw new Error("unknown action: " + action.type);
    }
  }
}
```

> **Important:** Reducers must be pure functions. Never mutate the state directly.

-----

### 🚦 When to Use Reducers?

  * **Simple State:** If a component updates state in a few simple ways, stick to `useState`.
  * **Complex State:** Use reducers when a component becomes too large, hard to read, or difficult to debug due to complex state logic.

**Benefits of Reducers:**

  * **Separation of Concerns:** Logic can be stored in separate files/directories.
  * **Debugging:** State bugs can be tracked back to specific dispatched actions.
  * **Testing:** Pure functions allow for isolation testing.

-----

### ⚓ The useReducer Hook

React provides the `useReducer` hook to integrate reducers into components.

**Syntax:**
It takes a reducer function and an initial state, returning an array with the current state and a dispatch function.

**The Dispatch Function:**
This function sends an action object to the reducer. The reducer calculates the return value, which React uses to update the state.

```javascript
const [state, dispatch] = useReducer(reducer, { count: 0 });
function handleClick() {
  dispatch({ type: "incremented_count" });
}
```

**Key Behaviors:**

  * Updates happen in the **next render** (similar to `useState`).
  * Uses `Object.is()` to detect changes. If the state hasn't changed, the component won't re-render.
  * `useState` and `useReducer` are equivalent; the choice depends on complexity and preference.

-----

### 📚 Assignment

  * Read the React docs on **Extracting state logic into a reducer** (and complete the challenges).
  * Read the **useReducer** React docs (focus on the troubleshooting section).

-----

### 🤔 Knowledge Check

  * What are reducers?
  * How would you declare a reducer?
  * What does the dispatch function do?
  * What steps can you follow to migrate from `useState` to `useReducer`?

-----

### 🔗 Additional Resources

  * **Web Dev Simplified:** Learn useReducer In 20 Minutes (Video).