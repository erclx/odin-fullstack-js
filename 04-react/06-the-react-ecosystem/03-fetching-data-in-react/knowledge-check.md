### Knowledge Check Answers 🎯

-----

**Question: How can you fetch data from an API in React?**

**Answer:** You use the native JavaScript `fetch` function inside a `useEffect` hook.

**Why:** Since fetching data is a "side effect" (it interacts with an external system), placing it in `useEffect` with an empty dependency array `[]` ensures the request runs only when the component first mounts.

**Example:**

```javascript
useEffect(() => {
  fetch("https://api.example.com/data")
    .then(response => response.json())
    .then(data => setData(data));
}, []);
```

-----

**Question: Why should you manually throw errors in fetch requests?**

**Answer:** You must manually check the response status because `fetch` **does not** throw an error for HTTP error codes (like 404 Not Found or 500 Server Error).

**Why:** `fetch` only automatically fails on network errors (like having no internet). To handle server errors (like a bad URL), you need to check if `response.status >= 400` and throw an error yourself so your `.catch()` block can handle it.

**Remember:** `fetch` thinks a **404 error** is a **success** (because the server replied), so you have to correct it.

-----

**Question: How can you avoid waterfalling requests?**

**Answer:** You can avoid waterfalls by **lifting the requests up** to a common parent component.

**Why:** A "waterfall" happens when a child component can't start fetching its data until the parent finishes fetching *its* data. By initiating both requests in the parent at the same time, they run in parallel, making the app load faster.

**Remember:** Don't wait for the parent to finish eating before you start cooking the child's meal; **cook both at once**.