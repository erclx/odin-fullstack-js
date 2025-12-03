### Knowledge Check Answers 🎯

-----

**Question: How would we set up a basic implementation of PropTypes?**

**Answer:** First, install the `prop-types` package and import it into your file. Then, assign a `propTypes` object to your component to define the expected type for each prop.

**Why:** This sets up a validation system that warns you in the browser console if you accidentally pass the wrong data type (like a number instead of a string) to a component.

**Example:**

```javascript
import PropTypes from 'prop-types';

function User({ name }) {
  return <h1>{name}</h1>;
}

User.propTypes = {
  name: PropTypes.string.isRequired
};
```

-----

**Question: If we pass in a prop to a component that has a defaultProp defined, what would happen?**

**Answer:** The value you passed in will **take precedence** and override the default value.

**Why:** `defaultProps` acts as a fallback or "safety net" that is only used if the prop is missing or `undefined`. If you provide a value, React uses that instead.

**Remember:** **Explicit** props always win over **default** props.

-----

**Question: What is the difference between PropTypes and TypeScript?**

**Answer:** **PropTypes** is a library specifically for checking React component props at runtime. **TypeScript** is a complete programming language (a superset of JavaScript) that validates types for *all* code (variables, functions, etc.) before the code even runs.

**Why:** PropTypes is easier to add to an existing standard JavaScript project for quick validation, whereas TypeScript requires writing your entire application in a specific language to ensure type safety everywhere.

**Remember:** **PropTypes** checks the **package** (props) on delivery; **TypeScript** checks the **whole factory** (codebase).