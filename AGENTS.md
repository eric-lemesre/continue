# AGENTS.md

## Build instructions
- Frontend builds to `frontend/dist/`
- Build includes optimizations:
  - Code splitting with manual chunks (vendor, analytics, data, store)
  - Terser minification with console removal
  - CSS code splitting enabled
  - Asset optimization with content hashing

## Deployment
- Frontend deploys to https://continue-demo.netlify.app
- Netlify configuration includes:
  - Long-term caching (1 year) for immutable assets
  - Security headers (X-Frame-Options, X-Content-Type-Options, Referrer-Policy)
  - Cache-Control headers for JS, CSS, fonts, and images

## PR instructions
- Always run `npm run build:frontend` before creating PR to ensure TypeScript compilation succeeds
