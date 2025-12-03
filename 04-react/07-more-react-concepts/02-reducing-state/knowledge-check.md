### Knowledge Check Answers 🎯

-----

**Question: What are reducers?**

**Answer:** Reducers are **pure functions** that take the **previous state** and an **action** object as arguments, and return the **new state**.

**Why:** They allow you to consolidate complex state update logic into a single function, often separated from the component itself. This makes the code easier to test, debug, and read because the logic isn't scattered across multiple event handlers.

**Remember:** `(Current State + Action) => New State`

-----

**Question: How would you declare a reducer?**

**Answer:** You declare it as a JavaScript function that accepts `state` and `action`, typically using a `switch` statement to handle different `action.type` cases.

**Why:** The `switch` statement checks the "type" of action that occurred (e.g., "increment", "decrement") and executes the specific logic required to produce the new state for that action.

**Example:**

```javascript
function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    default:
      throw new Error();
  }
}
```

-----

**Question: What does the dispatch function do?**

**Answer:** The `dispatch` function sends (or "dispatches") an **action object** to the reducer function to trigger a state update.

**Why:** Instead of updating the state directly, `dispatch` announces *what* happened (e.g., `{ type: "clicked_button" }`). The reducer then listens for this announcement and decides *how* to update the state.

**Remember:** `dispatch` is the **messenger** 📩 that delivers the action to the reducer.

-----

**Question: What steps can you follow to migrate from `useState` to `useReducer`?**

**Answer:**

1.  **Move** the state update logic from your event handlers into a new reducer function.
2.  **Replace** the `useState` hook with the `useReducer` hook.
3.  **Swap** the `setState` calls in your component with `dispatch` calls that pass an action type.

**Why:** This refactoring pattern moves the complexity out of your component. Your event handlers become simple messengers ("User clicked delete"), and the heavy lifting ("How do I delete this item from the array?") moves to the reducer.
