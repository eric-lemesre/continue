# AGENTS.md

## Build instructions
- Frontend builds to `frontend/dist/`

## Deployment
- Frontend deploys to https://continue-demo.netlify.app

## PR instructions
- Always run `npm run build:frontend` before creating PR to ensure TypeScript compilation succeeds

## Sentry Configuration

### Source Maps for Production Debugging
- Sentry is configured in `frontend/src/lib/sentry.ts` with browser tracing and session replay
- **Source maps must be uploaded** to Sentry during builds for readable stack traces in production errors
- Without source maps, production errors show minified function names (`ak`, `bk`, etc.) instead of actual code locations

### Required Environment Variables
- `VITE_SENTRY_DSN` - Sentry project DSN (runtime)
- `VITE_SENTRY_ENVIRONMENT` - Environment name (runtime, defaults to 'development')
- `SENTRY_AUTH_TOKEN` - Auth token for uploading source maps during build (build-time only)

### Setting Up Source Map Uploads
To enable source map uploads to Sentry:

1. **Create Sentry Auth Token**
   - Go to Sentry organization settings → Auth Tokens
   - Create token with scopes: `project:releases`, `project:write`, `org:read`

2. **Configure Build Tool**
   - For Vite: Install `@sentry/vite-plugin` and add to `vite.config.ts`
   - For Next.js: Use `@sentry/nextjs` which handles source maps automatically

3. **Add to Deployment Platform**
   - Set `SENTRY_AUTH_TOKEN` environment variable in Netlify/Vercel
   - Apply to all environments (Production, Preview, Development)

4. **Verify After Deployment**
   - Check build logs for "Uploading source maps" message
   - Verify Sentry releases page shows uploaded artifacts
   - Future errors should show readable file names and line numbers
