# What have I learned

- Initializing a next application with template via `--example` flag

- CSS Styling
  - Global CSS
  - CSS Modules
  - Tailwind
  - clsx: toggle class names based on state
  - Sass and CSS in JS libraries

- `next/font`
  - Optimize the font by downloading & hosting the font on the server => no need to make unnecessary network request
  - Can choose subsets to limit the number of characters required => reduce font size
  - Choose the font-weight to import

- antialiased: a technique to render / smooth out the font closer to the initial design

- `next/image`
  - Preventing layout shift automatically when images are loading
  - Resizing images to avoid shipping large images to devices with a smaller viewport (how can they optimize images size so good? from hundreds of KB to merely hundreds of B.)
  - Lazy loading images by default (images load as they enter the viewport)
  - Serving imaegs in modern formats, webP and avif, when the browser supports it

- `layout.tsx`
  - Create a shared UI layout for multiple pages. The layout will be applied for the current page and inner pages nested in the current directory

- `next/link`
  - Client side navigation
  - Prefetching the code of the Link page => page transition near-instant
  - `usePathname()` returns the path absolute to the root (e.g. `/dashboard/invoices`)

- `@vercel/postgres`
  - dashboard => storage => postgres
  - storage => .env.local => show secret => copy snippet
  - Browse data in `Data` section in `storage` tab and we can execute sql statements by running query in `Query` tab
  - Protect against SQL injections
  - await sql`sql query here`

- Fetching data
  - We can skip creating the API to fetch data by using react server component

- React Server Component
  - Execute on the server => make database queries directly
  - can use `async/await` on component

- Request waterfall issue:
  - fix: parallel data fetching (`promise.all` or `promise.allSettled`)
- Static rendering issue:

- Static rendering:
  - Faster websites: cache & globally distributed (maybe through CDN)
  - Reduced server load: No need to dynamically generate content for each user request
  - SEO: content is available when page loads

- Dynamic Rendering:
  - enabled by unstable_noStore from `next/cache`
  - content is rendered on the server for each request
  - real-time data
  - user-specific content: dashboards or user profiles
  - request time information: information can only be known at request time (cookies, URL search params)
  - Cons: Fastest rendering is as fast as your slowest data fetch

- Streaming
  - Prevent slow data requests from blocking your whole page
  - Each component is considered a chunk, chunks are rendered in parallel, reducing the overall load time
  - two ways to implement streaming:
    - At page level, with `loading.tsx`
    - For specific components, with `<Suspense />`

- Route Groups
  - route groups can ensure `loading.tsx` only applies to the `page.tsx` only
  - can use to separate application into sections `(marketing)`, or by teams

- Partial Prerendering
  - Static parts are prerendered at build time or during revalidation
  - Dynamic parts are postponed until the user requests the route

- Optimization
  - Server and database in the same region => reduce latency between server and database
  - Fetch data on server with RSC => expensive data fetches and logic on server => reduces client-side js bundle + prevent leaking database secrets
  - SQL fetch only needed data, reducing the amount of data transferred for each request & js needed to transform data-in-memory
  - Parallelize data fetching with JavaScript
  - Implement Streaming to prevent slow data requests from blocking the page, allow user to start interacting with the UI without waiting for everying to load
  - Move data fetching down to components that need it, use Suspense to mark static and dynamic sections in preparation for Partial Prerendering

- New Search pattern: Implement search by using URL search params as state:
  - Bookmarkable and Shareable URLs
  - Server-Side Rendering & Initial Load
  - Analytics and Tracking

- `useSearchParams`: Get query params
- `usePathname`
- `useRouter`: navigation methods
- "use client" directive
- Debouncing Revisit:
  - Reduce number of requests sent to your server & database
- we can access `searchParams`, `params` prop in the page components

- React Server Action in Nextjs
  - work even if JavaScript is disabled on the client (progressive enhancement)
  - Learn more here: [security with server actions](https://nextjs.org/blog/security-nextjs-server-components-actions)
```ts
async function create(formData: FormData) {
  'use server';

  // Logic to mutate data...
}

// in jsx
// <form action={create}>...</form>;
```

- Revalidate & Redirect
  - Client-side Router Cache: stores the route segments in the user's browser for a time
  - What does `revalidatePath` do? Maybe revalidate immediately, but isn't `unstable_noStore` enough? [Need more research](https://nextjs.org/learn/dashboard-app/mutating-data#6-revalidate-and-redirect)

- Basic zod

- Error handling
- `redirect` from `next/navigation` is an error
- `error.tsx` must be a client component
  - `error`, `reset` props
  - `notFound` from `next/navigation` will throw not found, can catch this by `not-found.tsx`
- read more:
  - [1](https://nextjs.org/docs/app/building-your-application/routing/error-handling), [2](https://nextjs.org/docs/app/api-reference/file-conventions/error), [3](https://nextjs.org/docs/app/api-reference/functions/not-found), [4](https://nextjs.org/docs/app/api-reference/file-conventions/not-found)

- `useFormState` from `react-dom`
  - args: (action, initialState)
  - returns: [state, dispatch]
  - Learn more about accessibility: [web.dev course](https://web.dev/learn/accessibility/)

- Revisit authentication & authorization:
  - Authentication: identify who
  - Authorization: give permissions to parts of the application

- NextAuth
  - `auth.config.js` and `auth.ts`
  - NextJS Middleware
  - Can we move `auth.ts` to api routes to holds other providers? And import it to provide sign in with username and password?
  - Email: user@nextmail.com
  - Password: 123456
