# Project notes for Claude

A Frontend Mentor challenge: static HTML + Sass, bundled with Parcel, deployed to GitHub Pages.

## Scripts

- `npm start`: Parcel dev server on port 4321. Writes to `dist-dev/`, never `dist/`, so a running dev server can't leak dev bundles into a deploy.
- `npm run build`: clean production build in `dist/` with relative paths (`--public-url ./`).
- `npm run push-gh`: builds, then publishes `dist/` to the `gh-pages` branch. Requires the `origin` remote to use SSH.
- `npm run format`: Prettier over `src/`.
- `package-lock.json` is committed; install with `npm ci`.
- npm 11 `allowScripts` must list packages with install scripts. Parcel's native dependencies are pre-approved. If an install warns about new ones, check what they are before approving them with `npm approve-scripts <pkg>`.

## Sass

- `src/scss/style.scss` is the root stylesheet. Each folder has an `_index.scss` that `@forward`s its partials. Use `@use`/`@forward`, never `@import`.
- `utils/_mixins.scss` provides `breakpoints()` (`sm` 16rem, `md` 48rem, `lg` 62rem, `xl` 75rem). Use it with `@use "../utils/mixins" as *;`.
