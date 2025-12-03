# 🛡️ Type Checking With PropTypes

**React Course**

### Introduction

Type checking verifies that your code uses the correct data types. In React, **PropTypes** checks the props a component receives, catching potential type errors during development.

-----

### 📝 Lesson Overview

  * Setting up PropTypes.
  * Using common PropTypes features.

-----

### ⚠️ Important Note on React Version

`propTypes` and `defaultProps` are **discontinued from React 19**. This lesson requires React 18 or lower.

**To downgrade a Vite project:**

1.  In `package.json`, change versions for `react`, `react-dom`, `@types/react`, and `@types/react-dom` to `"^18"`.
2.  Run `npm install`.

-----

### 🛠️ Getting Started

1.  **Install the library:**
    ```bash
    npm install --save prop-types
    ```
2.  **Import it** in your component file:
    ```javascript
    import PropTypes from 'prop-types';
    ```

-----

### 🧱 Using PropTypes

You define `propTypes` as a property on your component function.

```javascript
import PropTypes from 'prop-types';

const RenderName = (props) => {
  return <div>{props.name}</div>;
};

RenderName.propTypes = {
  name: PropTypes.string, // Expects 'name' to be a string
};

export default RenderName;
```

If `name` is not a string, a warning will appear in the console.

**Required Props:**
Use `.isRequired` to ensure a prop is provided.

```javascript
RenderName.propTypes = {
  name: PropTypes.string.isRequired,
}
```

-----

### 📦 Using defaultProps

You can define default values for props using the `defaultProps` property.

```javascript
RenderName.defaultProps = {
  name: 'Zach',
};
```

If `RenderName` is called without a `name` prop, it defaults to "Zach". If a prop *is* passed, it overrides the default.

-----

### 🤔 What about TypeScript?

**TypeScript** is a strongly typed language that builds on JavaScript and is very popular for type safety in modern React.

  * **Should I learn it now?** Not yet. It adds overhead while learning React. Focus on JavaScript fundamentals first.
  * **Future path:** Once comfortable with React, you can refactor a project to TypeScript to learn it.

-----

### 📚 Assignment

  * Read the [PropTypes documentation](https://legacy.reactjs.org/docs/typechecking-with-proptypes.html) to see all available types.
  * Read [Validating React Props with PropTypes](https://www.google.com/search?q=https://blog.logrocket.com/validating-react-props-proptypes/) for a comprehensive guide.
  * Check this [StackOverflow post](https://www.google.com/search?q=https://stackoverflow.com/questions/41746028/proptypes-in-react-is-it-deprecated/41746396%2341746396) comparing PropTypes and TypeScript.

-----

### 🤔 Knowledge Check

  * How would we set up a basic implementation of PropTypes?
  * If we pass in a prop to a component that has a `defaultProp` defined, what would happen?
  * What is the difference between PropTypes and TypeScript?