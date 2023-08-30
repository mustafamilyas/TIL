# Loading Data Using "loader" & "useLoaderData"

In Remix, there are two APIs for loading data, `loader` and `useLoaderData`. `loader` (server layer) can return anything and we can get the data through `useLoaderData`(client layer). `loader` only runs on the server, which is on the initial server render and when the client requests the data using `fetch` on browser's navigation (this is done by Remix).

```typescript
const data = {
  posts: [
    {
      slug: "my-first-post",
      title: "My First Post",
    },
    {
      slug: "90s-mixtape",
      title: "A Mixtape I Made Just For You",
    },
  ],
};

export async function loader() {
  return data.posts;
}

export default function Posts() {
  const posts = useLoaderData<typeof loader>();

  return (
    <main>
      <h1>Posts</h1>
      <ul>
        {posts.map((post) => (
          <li key={post.slug}>
            <Link to={post.slug} className="text-blue-600 underline">
              {post.title}
            </Link>
          </li>
        ))}
      </ul>
    </main>
  );
}
```

This is okay, but we should return `Response` instead or use `json` wrapper to reduce the boilerplate.

```typescript
export async function loader() {
  // ...
  return new Response(JSON.stringify(data), {
    status: 200,
    headers: {
      "Content-Type": "application/json",
    },
  });
}

// basically the same, just using a wrapper
import { json } from "@remix-run/node";

export async function loader() {
  // ...
  return json(data, {
    status: 200, // we can omit this if 200
  });
}
```

### Notes

- `loaders` on all routes run in parallel, so there's no way to have middleware attached to parent `loaders`. The reason is to make the apps as fast as possible. Take a look [here](https://remix.run/docs/en/1.19.3/pages/faq#how-can-i-have-a-parent-route-loader-validate-the-user-and-protect-all-child-routes).
