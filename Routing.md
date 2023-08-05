# Routing in NextJS

Next.js provides a powerful and straightforward routing system for building Single Page Applications (SPAs) with React. The routing in Next.js is file-based, which means that the file structure inside the "pages" directory determines the routes of your application. Here are some important notes on Next.js routing:

1. Pages Directory: In Next.js, all your pages are stored in the "pages" directory. Each file inside this directory represents a route in your application.

2. Automatic Routing: Next.js automatically sets up routing based on the file system. For example, a file named `about.tsx` in the "pages" directory will create a route for `/about`.

3. Nested Routes: You can create nested routes by organizing files within subdirectories of the "pages" directory. For example, a file named `projects/project1.tsx` will create a route for `/projects/project1`.

4. Dynamic Routing: Next.js supports dynamic routes using square brackets `[]` in the filename. For example, a file named `[id].tsx` will match routes like `/1`, `/2`, etc., and you can access the `id` parameter in your component.

5. Catch-All Routes: You can use the `...` syntax to define catch-all routes. For example, a file named `[...slug].tsx` will match routes like `/user/1/posts`, and you can access the `slug` parameter as an array.

6. Link Component: For client-side navigation, Next.js provides the `Link` component from the `next/link` module. It allows you to create links between pages without full page reloads, resulting in faster transitions.

7. Routing Using `useRouter`: In addition to the `Link` component, Next.js provides the `useRouter` hook from the `next/router` module, allowing you to access and manipulate the current route programmatically.

8. Redirects: Next.js supports redirecting from one route to another using the `redirect` property in `getServerSideProps` or `getStaticProps`.

9. API Routes: Next.js allows you to create serverless API endpoints using the "pages/api" directory. Requests to these API routes are handled server-side.

10. Custom 404 Page: You can create a custom 404 page by creating a file named `404.tsx` in the "pages" directory. Next.js will use this page when a route is not found.

11. Custom Error Page: To handle errors other than 404, you can use the `_error.tsx` file in the "pages" directory. This page will be used for server-side errors.

12. Custom App and Document: For advanced customization, you can use `_app.tsx` and `_document.tsx` files to extend the default behavior of the Next.js app and document components.

Next.js routing is designed to be intuitive and developer-friendly, allowing you to create complex SPAs with ease. It seamlessly integrates with React components, and the file-based approach makes it easy to organize and maintain your application's routes.


## Here are code examples of different routing techniques in Next.js:

### 1. Basic Routing:

```jsx
// pages/index.js

const HomePage = () => {
  return (
    <div>
      <h1>Welcome to the Home Page!</h1>
    </div>
  );
};

export default HomePage;
```

### 2. Nested Routing:

```jsx
// pages/products/index.js

const ProductsPage = () => {
  return (
    <div>
      <h1>Products Page</h1>
    </div>
  );
};

export default ProductsPage;
```

```jsx
// pages/products/laptops.js

const LaptopsPage = () => {
  return (
    <div>
      <h1>Laptops Page</h1>
    </div>
  );
};

export default LaptopsPage;
```

### 3. Dynamic Routing:

```jsx
// pages/posts/[postId].js

import { useRouter } from 'next/router';

const Post = () => {
  const router = useRouter();
  const { postId } = router.query;

  return (
    <div>
      <h1>Post ID: {postId}</h1>
    </div>
  );
};

export default Post;
```

### 4. Catch-All Routes:

```jsx
// pages/products/[...slug].js

import { useRouter } from 'next/router';

const ProductDetails = () => {
  const router = useRouter();
  const { slug } = router.query;

  return (
    <div>
      <h1>Product Details: {slug.join('/')}</h1>
    </div>
  );
};

export default ProductDetails;
```

### 5. Link Component:

```jsx
// pages/index.js

import Link from 'next/link';

const HomePage = () => {
  return (
    <div>
      <h1>Welcome to the Home Page!</h1>
      <Link href="/about">
        <a>About Us</a>
      </Link>
      <Link href="/products">
        <a>Products</a>
      </Link>
    </div>
  );
};

export default HomePage;
```

These examples cover various routing techniques in Next.js, including basic routes, nested routes, dynamic routes, catch-all routes, and using the `Link` component for client-side navigation. You can copy and paste these code examples into your Next.js project to see how they work.
