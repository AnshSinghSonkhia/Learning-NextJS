## Next.js Metadata: Static & Dynamic

In Next.js, metadata refers to information that provides additional context and instructions for web pages, such as page titles, descriptions, and custom data needed for SEO and social sharing. Next.js allows you to manage metadata in two ways: statically and dynamically.

### Static Metadata

Static metadata involves setting page metadata at build time, which means the values are fixed during the build process and remain the same for all users. This approach is suitable for pages with constant metadata that doesn't change based on user interactions or dynamic data.

To set static metadata in Next.js, you can use the `Head` component from the `next/head` module. The `Head` component allows you to define various metadata tags inside your page component.

```jsx
// pages/index.tsx

import Head from 'next/head';

const HomePage = () => {
  return (
    <>
      <Head>
        <title>My Static Homepage</title>
        <meta name="description" content="Welcome to my static homepage!" />
        <meta property="og:title" content="My Static Homepage" />
        <meta property="og:description" content="Welcome to my static homepage!" />
      </Head>
      <div>
        {/* Page content */}
      </div>
    </>
  );
};

export default HomePage;
```

In this example, we set the static metadata for the page title, description, and Open Graph (og) properties. This information will be used by search engines and social media platforms when users share the page.

### Dynamic Metadata

Dynamic metadata, on the other hand, allows you to set page metadata based on dynamic data or user interactions. This approach is useful when the metadata depends on variables, database content, or user-specific information.

To achieve dynamic metadata, you can use Next.js's `getServerSideProps` or `getStaticProps` functions to fetch the dynamic data and pass it as props to your page. Then, you can use these props to set the metadata using the `Head` component.

```jsx
// pages/post/[slug].tsx

import Head from 'next/head';

const PostPage = ({ post }) => {
  return (
    <>
      <Head>
        <title>{post.title}</title>
        <meta name="description" content={post.description} />
        <meta property="og:title" content={post.title} />
        <meta property="og:description" content={post.description} />
      </Head>
      <div>
        {/* Display post content */}
      </div>
    </>
  );
};

export async function getServerSideProps({ params }) {
  // Fetch the post data based on the slug from the API or database
  const post = await fetchPostBySlug(params.slug);
  return {
    props: {
      post,
    },
  };
}

export default PostPage;
```

In this example, we dynamically set the page title and description based on the fetched post data. The `getServerSideProps` function retrieves the post data from the API or database based on the slug in the URL, and then we use this data to set the metadata.

With static and dynamic metadata, you can effectively manage the information presented to users and search engines, improving SEO and enhancing the overall user experience in your Next.js application.
