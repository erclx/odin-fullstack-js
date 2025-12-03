### Knowledge Check Answers 🎯

-----

**Question: Why might you want to test your UI?**

**Answer:** You test the UI to ensure the website actually displays the intended content and behaves correctly for the user, not just that the background logic works.

**Why:** Unit tests on logic might pass even if the UI is broken (e.g., a button is hidden or text is missing). UI tests give confidence that the user experience remains intact after code changes.

**Remember:** Logic tests check the **engine**; UI tests check the **dashboard**. 🚗

-----

**Question: What packages are required for React testing?**

**Answer:** You generally need **Vitest** (the test runner), **React Testing Library** (to render components), **jsdom** (to simulate a browser environment), and **user-event** (to simulate clicking/typing).

**Why:**

  * `vitest`: Runs the test files.
  * `@testing-library/react`: Provides the `render` and `screen` tools.
  * `jsdom`: Creates a fake DOM in memory since Node.js doesn't have one.
  * `@testing-library/user-event`: Handles interactions.

-----

**Question: What is the significance of the `user-event` package?**

**Answer:** It simulates user interactions (like clicks, typing, or hovering) more realistically than built-in browser events.

**Why:** It triggers all the micro-events a real browser would. For example, when a user types, it triggers `keydown`, `keypress`, `input`, and `keyup`. `user-event` mimics this full lifecycle, whereas simpler methods might just trigger `change`.

-----

**Question: What does the `render` method do?**

**Answer:** The `render` method generates the component's HTML inside a simulated DOM (jsdom) in memory.

**Why:** It doesn't put anything on your actual computer screen. Instead, it builds the component structure in a virtual space so that your test code can query it (look for buttons, text, etc.) and interact with it.

-----

**Question: What is the most preferred method for querying?**

**Answer:** The **`getByRole`** method is the most preferred.

**Why:** It queries elements the way assistive technologies (like screen readers) see them (e.g., looking for a "button" named "Submit"). This ensures your tests also verify that your app is accessible.

**Example:**

```javascript
// Preferred
screen.getByRole('button', { name: /submit/i });

// Avoid (testing implementation details)
screen.getByTestId('submit-btn');
```

-----

**Question: How would you test for a click event with `userEvent`?**

**Answer:** You first set up the user session, query the element, and then `await` the click action.

**Why:** User events are asynchronous. You must use `await` to ensure the action completes before you check the results.

**Example:**

```javascript
const user = userEvent.setup();
render(<App />);
const button = screen.getByRole("button");

// Don't forget await!
await user.click(button); 

expect(screen.getByRole("heading").textContent).toMatch(/new text/i);
```

-----

**Question: What is the advantage of snapshot tests?**

**Answer:** They are incredibly fast to write and can verify the entire structure of a component with a single assertion.

**Why:** Instead of writing 20 lines of code to check if every button and label exists, `expect(container).toMatchSnapshot()` checks everything at once.

-----

**Question: What are the disadvantages of snapshot tests?**

**Answer:** They can lead to **false positives** (assuming code is correct just because the snapshot matches) and **false negatives** (failing due to trivial changes like fixing a typo).

**Why:** If a snapshot fails, developers might just update it without looking closely at *why* it changed. Conversely, if you fix a simple punctuation mark, the test fails, which can be annoying and reduce trust in the test suite.

**Remember:** Snapshots are good for detecting **unintended** structural changes, but bad for testing **behavior**.
