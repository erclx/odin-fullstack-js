# 📡 Fetching Data In React

**React Course**

### Introduction

To create full-fledged web applications, we need to get data from external sources. This lesson explores fetching data in React, managing component state, and handling asynchronous operations.

-----

### 📝 Lesson Overview

  * Understand how to make fetch requests in React components.
  * Catching and handling errors.
  * Lifting requests up the component hierarchy.

-----

### ⚙️ Using `fetch` in React Components

A common use case is to fetch data when a component mounts. We use the `useEffect` hook for this side effect.

```javascript
import { useEffect, useState } from "react";

const Image = () => {
  const [imageURL, setImageURL] = useState(null);

  useEffect(() => {
    fetch("https://picsum.photos/v2/list")
      .then((response) => response.json())
      .then((response) => setImageURL(response[0].download_url))
      .catch((error) => console.error(error));
  }, []); // Empty dependency array ensures this runs only once on mount

  return (
    imageURL && (
      <>
        <h1>An image</h1>
        <img src={imageURL} alt={"placeholder text"} />
      </>
    )
  );
};
```

-----

### ⚠️ Handling Errors & Loading States

Network requests are unreliable. We must handle errors and loading states to provide a good user experience.

1.  **Add State:** Add `error` and `loading` states.
2.  **Check Response:** Manually check `response.status` because `fetch` only rejects on network failures, not HTTP errors (like 404).
3.  **Update UI:** Conditionally render based on these states.

<!-- end list -->

```javascript
const Image = () => {
  const [imageURL, setImageURL] = useState(null);
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("https://picsum.photos/v2/list")
      .then((response) => {
        if (response.status >= 400) {
          throw new Error("server error");
        }
        return response.json();
      })
      .then((response) => setImageURL(response[0].download_url))
      .catch((error) => setError(error))
      .finally(() => setLoading(false)); // Always turn off loading
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>A network error was encountered</p>;

  return <img src={imageURL} alt="placeholder" />;
};
```

-----

### 🪝 Using Custom Hooks

We can extract fetching logic into a reusable **custom hook**. Custom hooks must start with `use`.

```javascript
const useImageURL = () => {
  const [imageURL, setImageURL] = useState(null);
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    // ... fetch logic ...
  }, []);

  return { imageURL, error, loading };
};

const Image = () => {
  const { imageURL, error, loading } = useImageURL();
  // ... render logic ...
};
```

-----

### 🌊 Managing Multiple Requests (Waterfalls)

A "waterfall" occurs when a child component waits for a parent's request to finish before starting its own request. This slows down the app.

**Solution:** Lift the request up the component tree. Fire both requests in the parent component and pass the data down as props. This allows requests to run in parallel.

-----

### 📚 Assignment

  * Read **Modern API data fetching methods** (up to Axios).
  * Read **How to fetch data in React with performance in mind**.

-----

### 🤔 Knowledge Check

  * How can you fetch data from an API in React?
  * Why should you manually throw errors in fetch requests?
  * How can you avoid waterfalling requests?