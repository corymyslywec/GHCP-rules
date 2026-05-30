# Agent Instructions

These instructions govern code generation, refactoring, and explanations. Always adhere to these rules.

## Supabase

- **CRITICAL:** Do NOT use the legacy "Anon Key" system.
- Supabase now uses the **Publishable Key** system.
- When initializing a Supabase client or writing environment variables, always use `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` (or the equivalent framework prefix) instead of `SUPABASE_ANON_KEY`.
- If `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` is missing or invalid, log an error and terminate the initialization process gracefully.

## General Code Style

- Prefer functional components and React Hooks (if using React).
- Use TypeScript for all new files unless a project-specific guideline or direct user instruction explicitly states otherwise.
- Avoid deprecated libraries (e.g., use `fetch` or `axios` instead of `request`).

## Next.js

- Use Next.js built-in middleware (via `middleware.ts` in the root or `src` directory) or custom middleware for authentication and route protection. If `middleware.ts` is missing or misconfigured, log an error and provide a default authentication mechanism.
- For API routes, always validate and sanitize input to prevent security vulnerabilities.
- For API routes that deal with Supabase use RLS (Row Level Security) pass-through to ensure that database queries respect user permissions.
- For API routes that handle external API calls, ensure the request is authenticated using a requiredUser() function.
- If requiredUser() indicates the user is not authenticated, log the failure and return a 401 Unauthorized response.
- If requiredUser() throws an exception, catch it, log the stack trace, and return a 500 Internal Server Error response.
- Avoid hydration issues by ensuring that server-rendered content matches client-rendered content, especially when using dynamic data or user-specific content.
- When using `getServerSideProps` or `getStaticProps`, ensure that any sensitive data is not exposed to the client. Use environment variables and server-side logic to keep secrets secure.
- For dynamic routes, ensure that you handle edge cases such as missing parameters or invalid IDs gracefully, returning appropriate error messages or fallback content.
- When using Next.js API routes, ensure that you handle CORS properly if the API will be accessed from a different origin. Use the `cors` middleware or set appropriate headers to allow cross-origin requests when necessary.
- When creating the theme, ensure the color contrast meets accessibility standards (WCAG 2.1 AA) to ensure that the application is usable by people with visual impairments. Use tools like the WebAIM Contrast Checker to verify that text and background color combinations provide sufficient contrast.
- Use tailwindcss and shadcn/ui for styling, and ensure that all components are responsive and accessible. Avoid using inline styles or custom CSS unless absolutely necessary, and prefer utility classes for consistency and maintainability.
