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
  - content is rendered on the server for each request
  - real-time data
  - user-specific content: dashboards or user profiles
  - request time information: information can only be known at request time (cookies, URL search params)
  - Cons: as fast as your slowest data fetch