# 🧪 Introduction To React Testing

**React Course**

### Introduction

Testing is a powerful tool for writing maintainable and flexible code. We'll switch to **Vitest** as our test runner and use the **React Testing Library (RTL)** for our UI tests.

-----

### 📝 Lesson Overview

  * Why UI testing is valuable.
  * How to set up a React testing environment.
  * How to test UI elements.
  * Understanding snapshot tests.

-----

### 🧐 Why Test UI?

You may have written tests for logic (like a Battleship game), but bugs can still exist in the UI. UI tests ensure your components display intended content and interact correctly. As apps grow, manual checking becomes impossible; automated UI tests catch regressions (e.g., a text change breaking a list, or a condition disabling a drop target).

-----

### 🛠️ Setting Up

We use **Vitest** (test runner) and **React Testing Library (RTL)**.

**Key Packages:**

  * **`vitest`**: The test runner.
  * **`jsdom`**: Simulates the DOM in memory for tests.
  * **`@testing-library/react`**: Provides utilities like `render` and `screen` to interact with components.
  * **`@testing-library/jest-dom`**: Adds custom matchers (e.g., `toBeInTheDocument`).
  * **`@testing-library/user-event`**: Simulates user interactions (clicks, typing).

**Installation:**

```bash
npm install @testing-library/user-event --save-dev
```

-----

### 🔍 Our First Query

We use `render` to load a component into the simulated DOM and `screen` to query it.

```javascript
// App.test.jsx
import { describe, it, expect } from "vitest";
import { render, screen } from "@testing-library/react";
import App from "./App";

describe("App component", () => {
  it("renders correct heading", () => {
    render(<App />);
    // Queries are classified into: getBy, queryBy, findBy
    expect(screen.getByRole("heading").textContent).toMatch(/our first test/i);
  });
});
```

  * **`getByRole`** is the preferred query method as it mirrors how users (including those using assistive tech) perceive the page.

-----

### 🖱️ Simulating User Events

We use `userEvent` to simulate interactions like clicks. Note that these interactions are asynchronous.

```javascript
// App.test.jsx
import { describe, it, expect } from "vitest";
import { render, screen } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import App from "./App";

describe("App component", () => {
  it("renders radical rhinos after button click", async () => {
    const user = userEvent.setup();

    render(<App />);
    const button = screen.getByRole("button", { name: "Click Me" });

    await user.click(button);

    expect(screen.getByRole("heading").textContent).toMatch(/radical rhinos/i);
  });
});
```

-----

### 📸 Snapshot Tests

Snapshot testing compares the rendered component's HTML against a saved "snapshot" file.

**Pros:**

  * Fast and easy to write.
  * Ensures no unexpected changes creep in.

**Cons:**

  * **False Positives:** A passing snapshot doesn't prove the component works correctly (e.g., button logic could be broken).
  * **False Negatives:** Tiny, irrelevant changes (like fixing a typo or changing a class name) break the test, which can lead to "snapshot fatigue."

<!-- end list -->

```javascript
it("renders magnificent monkeys", () => {
  const { container } = render(<App />);
  expect(container).toMatchSnapshot();
});
```

-----

### 📚 Assignment

  * Read **Testing Implementation Details** by Kent C. Dodds (avoid testing implementation details).
  * Check the **React Testing Library Cheatsheet** for query methods.
  * Read about **User Event API** and **Snapshot Testing Pros/Cons**.

-----

### 🤔 Knowledge Check

  * Why might you want to test your UI?
  * What packages are required for React testing?
  * What is the significance of the `user-event` package?
  * What does the `render` method do?
  * What is the most preferred method for querying?
  * How would you test for a click event with `userEvent`?
  * What are the advantages and disadvantages of snapshot tests?