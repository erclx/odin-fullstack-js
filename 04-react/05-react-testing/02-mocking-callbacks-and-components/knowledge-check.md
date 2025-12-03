### Knowledge Check Answers 🎯

-----

**Question: How can you mock a callback handler?**

**Answer:** You create a mock function using `vi.fn()` (in Vitest) or `jest.fn()` (in Jest) and pass it as a prop to the component you are testing.

**Why:** This allows you to spy on the function to verify it was called when a specific event occurred (like a button click) without needing to define the actual logic of the function.

**Example:**

```javascript
const onClickMock = vi.fn();
render(<CustomButton onClick={onClickMock} />);
const button = screen.getByRole("button");
await userEvent.click(button);
expect(onClickMock).toHaveBeenCalled();
```

-----

**Question: How can you mock a child component?**

**Answer:** You use `vi.mock()` (or `jest.mock()`) to replace the child component module with a simplified dummy version that returns basic HTML.

**Why:** As component trees get deep and complex, you want to test the parent in isolation. Mocking children ensures that errors inside a child component don't cause the parent's test to fail and keeps the output clean.

**Example:**

```javascript
vi.mock('./ChildComponent', () => {
  return () => <div data-testid="mock-child">Mocked Child</div>;
});
```

**Remember:** Mocking children is like using **stunt doubles**; they look right from a distance, but they don't do the dangerous work.