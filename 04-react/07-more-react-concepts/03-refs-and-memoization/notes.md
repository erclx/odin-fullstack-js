# 🧠 Refs And Memoization

**React Course**

### Introduction

How can we do DOM manipulations in React? What about performance optimization? Since components re-render when state changes, does this slow down the app if expensive calculations are re-executed?

-----

### 📝 Lesson Overview

  * Explore `useRef` hook and its use cases.
  * Explain memoization and how `useCallback` and `useMemo` can be used.

-----

### 🔗 The useRef Hook

The `useRef` hook lets you manage a value that’s not needed for rendering. It is an **alternative to state** when you want a component to "remember" something without triggering a re-render.

#### DOM Manipulation

`useRef` is often used to access specific elements in the DOM directly (e.g., focusing an input).

```javascript
import { useRef, useEffect } from "react";

function ButtonComponent() {
  const buttonRef = useRef(null); // Initial value is null

  useEffect(() => {
    buttonRef.current.focus(); // Access the DOM element via .current
  }, []);

  return <button ref={buttonRef}>Click Me!</button>;
}
```

  * **Why not `querySelector`?** Manipulating the DOM directly defeats the purpose of React. Let React handle the DOM wherever possible.
  * **Persisting Values:** Refs persist through the component's lifecycle and re-renders, unlike normal variables which are reset.

-----

### 💾 The useMemo Hook

`useMemo` caches the result of a calculation between re-renders. It only recalculates when its dependencies change.

**Use Case: Expensive Calculations**
If you calculate something heavy (like iterating over thousands of items) inside a component, it runs on every render. `useMemo` prevents this.

```javascript
import { useMemo } from "react";

function Cart({ products }) {
  const totalPrice = useMemo(() => {
    return products.reduce((total, product) => total + product.price, 0);
  }, [products]); // Only recalculate if 'products' changes

  return <p>Total Price: ${totalPrice}</p>;
}
```

**Use Case: Referential Equality**
If you pass an object or array as a prop to a child component, it is recreated on every render, causing the child to re-render (even if the contents are the same). `useMemo` keeps the reference stable.

> **Premature Optimization:** "Premature optimization is the root of all evil." Don't memoize everything. Only optimize when you notice performance issues.

-----

### 📞 The useCallback Hook

`useCallback` is similar to `useMemo`, but it is specifically for **memoizing functions**.

  * **Without `useCallback`:** A function is recreated on every render. If passed to a child component, the child sees a "new" prop and re-renders.
  * **With `useCallback`:** The function reference remains the same unless dependencies change.

<!-- end list -->

```javascript
import { useCallback } from "react";

const handleClick = useCallback(() => {
  setCount((prev) => prev + 1);
}, []); // Dependencies
```

| Hook | Returns | Use Case |
| :--- | :--- | :--- |
| **`useMemo`** | The **result** of a function | Caching expensive values, stable object references. |
| **`useCallback`** | The **function itself** | Stable function references (e.g., event handlers passed to children). |

-----

### 🛑 React.memo

`React.memo` is a higher-order component that wraps a component. It skips re-rendering the component if its props have not changed. This works hand-in-hand with `useMemo` and `useCallback` to prevent unnecessary renders of child components.

```javascript
const ButtonComponent = memo(({ onClick, children }) => {
  return <button onClick={onClick}>{children}</button>;
});
```

-----

### 📚 Assignment

  * Read **When to useMemo and useCallback** by Kent C. Dodds.
  * Check out the **React Docs interactive guide for useRef**.
  * Read **useRef instead of querySelector in React**.

-----

### 🤔 Knowledge Check

  * Why should you prefer `useRef` over `querySelector`?
  * What is the difference between `useMemo` and `useCallback`?
  * How do `useMemo` and `useCallback` help optimize performance?
  * When should you memoize a value?