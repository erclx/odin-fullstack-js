### Knowledge Check Answers 🎯

-----

**Question: What is the only required lifecycle method?**

**Answer:** The **`render()`** method is the only required method in a class component.

**Why:** It is responsible for returning the elements (JSX) that represent the component, so React knows what to display on the screen.

**Remember:** If you don't **render**, you don't **exist** on the page.

-----

**Question: What lifecycle method should you use for initial data fetching?**

**Answer:** You should use **`componentDidMount()`**.

**Why:** This method runs immediately *after* the component has been added to the DOM. It's the standard place to trigger API calls because the component is ready to receive and display the data.

**Remember:** **Mount** the frame first, then **fetch** the painting.

-----

**Question: When you want to act upon change of the DOM, or of state, what lifecycle method would you use?**

**Answer:** You would use **`componentDidUpdate()`**.

**Why:** This method runs automatically after the component re-renders due to new props or state. It's perfect for logic that depends on changes, like fetching new user data when a User ID prop changes.

**Example:**

```javascript
componentDidUpdate(prevProps) {
  // Check if the value actually changed to avoid infinite loops!
  if (this.props.userID !== prevProps.userID) {
    this.fetchData(this.props.userID);
  }
}
```

-----

**Question: When performing cleanup actions, what lifecycle method should be used?**

**Answer:** You should use **`componentWillUnmount()`**.

**Why:** This runs right before the component is destroyed and removed from the screen. It's crucial for stopping things that shouldn't run anymore, like canceling network requests or clearing timers.

**Remember:** This is the **cleanup crew** 🧹 clearing the room before the lights go out.

-----

**Question: How does the `useEffect` hook combine some of the lifecycle methods?**

**Answer:** `useEffect` combines **mounting**, **updating**, and **unmounting** into a single API, controlled by the dependency array and the return value.

**Why:**

  * **Mounting:** An empty array `[]` makes it run once (like `componentDidMount`).
  * **Updating:** Adding variables `[prop]` makes it run when they change (like `componentDidUpdate`).
  * **Unmounting:** Returning a function makes that function run on cleanup (like `componentWillUnmount`).