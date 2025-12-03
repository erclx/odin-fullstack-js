### Knowledge Check Answers 🎯

-----

**Question: How can you use CSS Modules in your React app?**

**Answer:** You use CSS Modules by creating CSS files (typically named `Name.module.css`) where the class names are scoped locally to a specific component.

**Why:** This prevents "global scope pollution," meaning you can use common class names like `.btn` or `.container` in multiple different components without them accidentally overriding each other or causing conflicts.

**Example:**

```javascript
import styles from './Button.module.css';

// The class name is accessed like an object property
<button className={styles.btn}>Click Me</button>
```

-----

**Question: What does CSS-in-JS mean?**

**Answer:** CSS-in-JS is a styling approach where you write your CSS directly inside your JavaScript files, rather than in separate `.css` files.

**Why:** It allows you to use the full power of JavaScript to control your styles. You can easily change styles dynamically based on a component's **state** or **props** (e.g., passing a `primary` prop to change a button's color). Libraries like `styled-components` are popular for this.

**Remember:** It's **CSS** logic living inside your **JS** logic.

-----

**Question: What are component libraries?**

**Answer:** Component libraries are collections of pre-built, pre-styled, and accessible UI components (like dropdowns, calendars, and modals) that you can import directly into your project.

**Why:** They save developers massive amounts of time by handling the complex styling, behavior, and accessibility requirements of common UI elements, so you don't have to build them from scratch.

**Example:** Instead of building a date picker from scratch, you import `<DatePicker />` from a library like Material UI or Chakra UI.

