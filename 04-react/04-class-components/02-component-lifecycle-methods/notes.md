# ♻️ Component Lifecycle Methods

**React Course**

### Introduction

A component's lifecycle consists of three main stages: **mounting**, **updating**, and **unmounting**. While functional components use the `useEffect` hook to manage these, class components use specific **lifecycle methods**.

-----

### 📝 Lesson Overview

  * Learn how to use lifecycle methods in a class component.

-----

### 🛠️ Key Lifecycle Methods

#### 1\. `render()`

  * **When:** Runs on mount and update.
  * **Role:** The **only required method** in a class component.
  * **Rules:** It must be **pure** (does not modify state, returns the same result for same inputs, does not interact directly with the browser).

#### 2\. `componentDidMount()`

  * **When:** Runs *immediately after* the component is mounted (inserted into the DOM tree).
  * **Role:** The ideal place to **fetch data** (API calls) or perform operations reliant on the component being present in the DOM.

#### 3\. `componentDidUpdate()`

  * **When:** Runs after a component re-renders.
  * **Role:** Used to update the DOM or state in response to changes (e.g., refetching user data if the user ID changes).
  * **⚠️ Warning:** Be careful updating state here. If you update state indiscriminately, it causes a re-render, triggering this method again, leading to an **infinite loop**. Always use conditional statements to compare previous and current props/state.

#### 4\. `componentWillUnmount()`

  * **When:** Runs *immediately before* a component is unmounted and destroyed.
  * **Role:** Used for **cleanup actions**, such as canceling network requests or clearing timers (e.g., `clearInterval`).

-----

### 🔗 How `useEffect()` Relates

In functional components, the `useEffect` hook combines the functionality of these class methods.

| Class Method | `useEffect` Equivalent |
| :--- | :--- |
| **`componentDidMount`** | `useEffect(..., [])` (Empty dependency array) |
| **`componentDidUpdate`** | `useEffect(..., [prop])` (Dependency array with values) OR `useEffect(...)` (No dependency array) |
| **`componentWillUnmount`** | `return () => { ... }` (The return/cleanup function inside `useEffect`) |

**Example:**

```javascript
useEffect(() => {
  placeholderFunction(); // Acts like componentDidMount
  return () => cleanupFunction(); // Acts like componentWillUnmount
}, []) // Empty array prevents re-running (avoids componentDidUpdate behavior)
```

-----

### 📚 Assignment

  * Check out this [React lifecycle methods diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/) for a visual representation.
  * Read the [React.Component documentation](https://react.dev/reference/react/Component) (specifically from `constructor` to `componentWillUnmount`).

-----

### 🤔 Knowledge Check

  * What is the only required lifecycle method?
  * What lifecycle method should you use for initial data fetching?
  * When you want to act upon change of the DOM, or of state, what lifecycle method would you use?
  * When performing cleanup actions, what lifecycle method should be used?
  * How does the `useEffect` hook combine some of the lifecycle methods?