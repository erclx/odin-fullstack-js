# 🧠 Managing State With The Context API

### Introduction

As applications grow, passing data through multiple layers of components (prop drilling) becomes repetitive and difficult to manage. The **Context API** solves this by allowing you to share data and functionality across components, regardless of their location in the component tree.

-----

### 📉 Why do we need the Context API?

The main problem Context solves is **prop drilling**—passing data through intermediate components that don't need it, just to get it to a deeply nested child.

**Without Context:**
`App` -\> `Header` -\> `Links` (passing `cartItemsCount`)

  * `Header` doesn't need `cartItemsCount` but must accept it as a prop to pass it to `Links`.

**With Context:**
`App` -\> `Context` -\> `Links`

  * `Links` can access the data directly from the Context, bypassing `Header`.

-----

### 🛠️ Implementing Context API

There are three key elements to using Context:

#### 1\. `createContext`

Creates the context object. It takes a **default value** (static) which is used if a component attempts to access the context without a matching Provider.

```javascript
import { createContext } from "react";

// Setting a default value shape helps with auto-completion and testing
export const ShopContext = createContext({
  products: [],
  cartItems: [],
  addToCart: () => {},
});
```

#### 2\. Context Object (Provider)

To make the context available to components, you wrap them in the Context object. You pass the data you want to share via the `value` prop.

  * **Note:** Prior to React 19, you had to use `ContextObject.Provider` (e.g., `<ShopContext.Provider>`). In React 19+, you can use the Context object directly.

<!-- end list -->

```javascript
export default function App() {
  // ... state logic ...

  return (
    // The value prop overwrites the default value
    <ShopContext value={{ cartItems, products, addToCart }}>
      <Header />
      <ProductDetail />
    </ShopContext>
  );
}
```

#### 3\. `useContext`

A hook used inside a child component to consume the data.

```javascript
import { useContext } from "react";
import { ShopContext } from "./App";

function Links() {
  const { cartItems } = useContext(ShopContext);
  // Now we can use cartItems directly!
}
```

-----

### ⚠️ Drawbacks of using Context API

While powerful, Context has downsides:

  * **Performance Issues:** Updating the state in a context causes **all** consuming components to re-render, even if the specific data they use hasn't changed.
  * **Complexity:** It can make code harder to follow by hiding the data flow compared to explicit props.

-----

### 💡 Potential Solutions

  * **Multiple Smaller Contexts:** Instead of one giant global state, use smaller contexts for related pieces of state to minimize unnecessary re-renders.
  * **Component Composition:** Sometimes passing components as children is a better solution than Context.
  * **External Libraries:** For complex state management with built-in optimizations, libraries like **Zustand** or **Redux** might be better, though they come with a learning curve.

-----

### 📚 Assignment

  * Read the [React documentation for `useContext`](https://www.google.com/search?q=%5Bhttps://react.dev/reference/react/useContext%5D\(https://react.dev/reference/react/useContext\)) and try the examples.
  * Read the article ["Prop Drilling"](https://kentcdodds.com/blog/prop-drilling) by Kent C. Dodds.

-----

### 🤔 Knowledge Check

  * What problems can prop drilling cause?
  * How can we avoid problems with prop drilling?
  * What are the benefits of using the Context API over passing props?
  * What are the drawbacks of using the Context API?