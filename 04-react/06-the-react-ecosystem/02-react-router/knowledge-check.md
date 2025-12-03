### Knowledge Check Answers 🎯

**Question: What does client-side routing mean?**

**Answer:** Client-side routing means that JavaScript running in the browser handles the navigation and URL updates, rather than the server.

**Why:** This allows for Single Page Applications (SPAs) where the user moves between "pages" without the browser triggering a full refresh. It feels faster and more app-like because only the necessary content is swapped out.

**Remember:** It brings the "microwave" (routing logic) to the table so you don't have to get up (reload) for every meal.

-----

**Question: How do you set up a basic router?**

**Answer:** You use the `createBrowserRouter` function to define an array of route objects (paths and elements) and pass that router to the `RouterProvider` component.

**Why:** `createBrowserRouter` creates the data structure that maps your URLs to specific React components, and `RouterProvider` injects that logic into your app's rendering tree.

**Example:**

```javascript
const router = createBrowserRouter([
  { path: "/", element: <App /> },
  { path: "profile", element: <Profile /> },
]);

createRoot(root).render(<RouterProvider router={router} />);
```

-----

**Question: What should be used in place of “a” tags to enable client-side routing?**

**Answer:** You should use the `<Link>` component instead of standard `<a>` tags.

**Why:** An `<a>` tag causes the browser to make a network request and reload the page (server-side routing). The `<Link>` component intercepts the click and updates the URL via JavaScript (client-side routing) without a reload.

**Example:**

```jsx
// Updates URL without refreshing
<Link to="profile">Profile page</Link>
```

-----

**Question: How do you create nested routes?**

**Answer:** You define a `children` array inside a parent route's configuration object and place an `<Outlet />` component inside the parent's JSX.

**Why:** The `children` array tells the router which paths belong under the parent. The `<Outlet />` tells the parent component exactly *where* on the screen to render those matching children.

**Remember:** The **`Outlet`** is the **window** where the child looks out.

-----

**Question: What do you mean by dynamic segments or URL params?**

**Answer:** Dynamic segments are placeholders in a route path that can match any value, denoted by a colon (e.g., `:name`).

**Why:** They allow you to use one component to handle many similar URLs (like `/profile/popeye` and `/profile/spinach`). You access the actual value inside the component using the `useParams` hook.

**Example:**

```javascript
// Route definition
path: "profile/:name"

// Inside component for url '/profile/popeye'
const { name } = useParams(); // name is "popeye"
```

-----

**Question: How do you handle errors from bad URLs?**

**Answer:** You add an `errorElement` property to your route configuration.

**Why:** If a user navigates to a non-existent path (404) or if a component crashes during loading, React Router will render this custom error component instead of crashing the whole app or showing a blank screen.

-----

**Question: How do you pass data from parent to child through an `<Outlet />` component?**

**Answer:** You pass data into the `context` prop of the `<Outlet />` component, and the child accesses it using the `useOutletContext()` hook.

**Why:** Since the child component isn't rendered directly by the parent (it's rendered by the router), you can't pass standard props. The `context` prop bridges this gap.

**Example:**

```javascript
// Parent
<Outlet context={[user, setUser]} />

// Child
const [user, setUser] = useOutletContext();
```

-----

**Question: How do you create protected routes?**

**Answer:** You conditionally render a `<Navigate />` component if the user is not authorized.

**Why:** If the condition (like `isLoggedIn`) is false, `<Navigate />` immediately redirects the user to a different page (like `/login`), preventing them from seeing the protected content.

**Example:**

```javascript
// If no user, bounce them to login. Otherwise, show content.
return user ? <Dashboard /> : <Navigate to="/login" />;
```

-----

**Question: How do you test components that use React Router?**

**Answer:** You must verify them inside a routing context, typically by wrapping the component in a `MemoryRouter` or using `createMemoryRouter`.

**Why:** Standard React tests don't run in a browser, so they don't have a URL history stack. `MemoryRouter` simulates this history in memory so hooks like `useNavigate` or components like `<Link>` don't throw errors.