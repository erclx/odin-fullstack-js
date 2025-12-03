# 🛣️ React Router

**React Course**

### Introduction

For larger-scale applications with multiple pages, we use **React Router** to manage routing on the client-side. This allows navigation without reloading the page.

-----

### 📝 Lesson Overview

  * Understand client-side routing.
  * Learn to use React Router (setup, nested routes, dynamic paths, catch-all routes).
  * Passing data via outlets.
  * Protected routes.
  * Testing with React Router.

-----

### 🏃 Client-Side Routing

Client-side routing allows JavaScript to handle navigation within a **Single Page Application (SPA)**. Instead of the browser requesting a new document from the server (full reload), the URL changes, and React updates the view instantly.

**Benefits:**

  * Faster transitions (no page reload).
  * App-like interactions and animations.
  * **Note:** You must ensure screen readers are notified of content changes manually or via libraries like React Router.

-----

### 🛠️ Setting Up React Router

We typically use the object-based approach with `createBrowserRouter`.

1.  **Install:** `npm install react-router`
2.  **Configure:** Define routes in `main.jsx` (or a separate file) and pass them to `RouterProvider`.

<!-- end list -->

```javascript
import { createBrowserRouter, RouterProvider } from "react-router";
import App from "./App";
import Profile from "./Profile";

const router = createBrowserRouter([
  { path: "/", element: <App /> },
  { path: "profile", element: <Profile /> },
]);

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <RouterProvider router={router} />
  </StrictMode>
);
```

#### The `<Link>` Element

Use `<Link>` instead of `<a>` tags to prevent full page reloads.

```javascript
import { Link } from "react-router";
<Link to="profile">Profile page</Link>
```

-----

### 🪆 Nested Routes & Dynamic Segments

You can nest routes to render a child component inside a parent using the `<Outlet />` component.

**Config:**

```javascript
{
  path: "profile",
  element: <Profile />,
  children: [
    { index: true, element: <DefaultProfile /> }, // Renders at /profile
    { path: "spinach", element: <Spinach /> },    // Renders at /profile/spinach
  ],
}
```

**Parent Component (`Profile.jsx`):**

```javascript
import { Outlet } from "react-router";
// ...
<Outlet /> {/* Child routes render here */}
```

**Dynamic Segments (Params):**
Use `:` to define dynamic parts of the URL (e.g., `profile/:name`). Access them with `useParams`.

```javascript
import { useParams } from "react-router";
const { name } = useParams();
```

-----

### 🚫 Handling Bad URLs

Use the `errorElement` property in your route configuration to render a custom component (like a 404 page) when a user visits a non-existent path.

```javascript
{ path: "/", element: <App />, errorElement: <ErrorPage /> }
```

-----

### 📡 Outlets & Context

To pass data from a parent to a child rendered by an `Outlet`, use the `context` prop. Children access it via `useOutletContext()`.

**Parent:** `<Outlet context={[someData]} />`
**Child:** `const [someData] = useOutletContext();`

-----

### 🔒 Protected Routes & Navigation

To restrict access (e.g., authentication) or redirect users programmatically, use:

  * **`<Navigate to="/" />`**: A component that redirects when rendered.
  * **`useNavigate` hook**: A hook to navigate programmatically (e.g., after form submission).

-----

### 🧪 Testing

When testing components that use Router features (like `Link` or `useParams`), you must wrap them in a router context.

  * **Simple tests:** Wrap in `<MemoryRouter>`.
  * **Complex tests:** Use `createMemoryRouter` with `RouterProvider` to simulate full routing behavior without a browser.

-----

### 📚 Assignment

  * Fix the `/profile` page in the example app and add new routes.
  * Read the **React Router Tutorial** (up to Nested Routes).
  * Browse the **React Router Documentation** for an overview of features.

-----

### 🤔 Knowledge Check

  * What does client-side routing mean?
  * How do you set up a basic router?
  * What should be used in place of “a” tags?
  * How do you create nested routes and dynamic segments?
  * How do you pass data through an `<Outlet />`?
  * How do you create protected routes?