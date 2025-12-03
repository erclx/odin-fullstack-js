### Knowledge Check Answers 🎯

***

**Question: Why should you prefer the `useRef` hook over other DOM manipulation methods like `querySelector`?**

**Answer:** You should prefer `useRef` because it aligns with React's lifecycle and keeps DOM interactions within the React ecosystem, rather than bypassing it.

**Why:** React uses a Virtual DOM to manage updates efficiently. Direct manipulation via `querySelector` can conflict with React's internal state management and lead to unpredictable bugs. `useRef` gives you safe access to the element without triggering unnecessary re-renders.



[Image of React Virtual DOM vs Direct DOM manipulation]


**Remember:** `useRef` is the **authorized backstage pass** to the DOM; `querySelector` is jumping the fence.

***

**Question: What is the difference between `useMemo` and `useCallback`?**

**Answer:** `useMemo` caches the **result** of a function (a value), while `useCallback` caches the **function definition** itself.

**Why:** `useMemo` is used when you want to avoid recalculating a value (like a total price). `useCallback` is used when you want to prevent a function from being recreated on every render, which is important for preserving referential equality when passing functions as props.



**Remember:** `useMemo` remembers the **answer**; `useCallback` remembers the **formula**.

***

**Question: How do `useMemo` and `useCallback` help optimize the performance of React components?**

**Answer:** They optimize performance by preventing **expensive calculations** from running on every render and by preventing **unnecessary re-renders** of child components.

**Why:**
1.  **Expensive Logic:** They cache results so complex math isn't repeated unless inputs change.
2.  **Referential Equality:** They keep object/function references stable. If a parent re-renders but passes the *exact same* prop reference to a child wrapped in `memo`, the child skips its re-render.



***

**Question: When should you memoize a value?**

**Answer:** You should only memoize a value if the calculation is **expensive** (slow) or if it is being passed as a dependency/prop to a component that relies on **referential equality** (like `memo`).

**Why:** Memoization comes with its own performance cost (memory and comparison logic). If a function is fast, memoizing it is "premature optimization" and can actually make your app slower.

**Remember:** Don't buy a safe (memoization) to store a penny (cheap calculation).