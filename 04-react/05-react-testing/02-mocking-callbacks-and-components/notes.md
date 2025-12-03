# 🎭 Mocking Callbacks And Components

**React Course**

### Introduction

We’ve covered React testing basics. Now, we'll dive deeper into **mocking**—a technique essential for testing components in isolation and verifying interactions.

-----

### 📝 Lesson Overview

  * Carry out mocks in the context of React testing.

-----

### 🤔 What is Mocking?

Mocking replaces real dependencies (like functions or child components) with simulated versions. This allows you to test a component's behavior without relying on external code or complex logic.

#### Testing Callback Handlers

Callbacks (like `onClick`) are often passed as props. To test them, we don't need the real function logic; we just need to verify it *gets called*.

**Example:**

```javascript
// CustomButton.test.jsx
import { vi, describe, it, expect } from 'vitest';
import { render, screen } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import CustomButton from "./CustomButton";

describe("CustomButton", () => {
  it("should call the onClick function when clicked", async () => {
    const onClick = vi.fn(); // Create a mock function
    const user = userEvent.setup(); 
    
    render(<CustomButton onClick={onClick} />);

    const button = screen.getByRole("button", { name: "Click me" });

    await user.click(button);

    expect(onClick).toHaveBeenCalled(); // Verify the mock was called
  });
});
```

  * **`vi.fn()`**: Creates a mock function that tracks calls.
  * **Best Practice:** Invoke `userEvent.setup()` and render your component inside each test block for better isolation and readability.

-----

### 🧩 Mocking Child Components

When testing a parent component, you might want to mock complex child components to simplify the test. This avoids testing the child's implementation details.

**How to mock:**
You can use `vi.mock()` (or `jest.mock()`) to replace a module with a dummy implementation.

```javascript
vi.mock('./Submission', () => {
  return ({ submission }) => <div data-testid="submission">{submission.id}</div>;
});
```

This replaces the real `Submission` component with a simple `div` containing the submission ID, making it easy to assert that the parent rendered it correctly.

-----

### 🌍 React Testing in the Real World

Real-world tests often follow the **Arrange-Act-Assert** pattern:

1.  **Arrange:** Render the component and set up mocks/props.
2.  **Act:** Simulate user interaction (e.g., clicking a button).
3.  **Assert:** Check if the expected outcome occurred (e.g., mock function called, DOM updated).

-----

### 📚 Assignment

  * Read this article on **[Mocking Child Components](https://www.google.com/search?q=https://medium.com/%40jaryd_34198/seamless-testing-with-jest-mocking-child-components-43e33b666668)**.
  * Watch this **[Testing React Apps tutorial](https://www.youtube.com/watch?v=8Xwq35cPwYg)** by Academind for a great overview, including async code.

-----

### 🤔 Knowledge Check

  * How can you mock a callback handler?
  * How can you mock a child component?