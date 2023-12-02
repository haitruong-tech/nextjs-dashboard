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
- antialiased: a technique to render / smooth out the font closer to the initial design
- `next/image`
  - Preventing layout shift automatically when images are loading
  - Resizing images to avoid shipping large images to devices with a smaller viewport (how can they optimize images size so good? from hundreds of KB to merely hundreds of B.)
  - Lazy loading images by default (images load as they enter the viewport)
  - Serving imaegs in modern formats, webP and avif, when the browser supports it
