# GitHub Copilot Custom Instructions

These instructions govern code generation, refactoring, and explanations. Always adhere to these rules.

## 1. Supabase
- **CRITICAL:** Do NOT use the legacy "Anon Key" system. 
- Supabase now uses the **Publishable Key** system. 
- When initializing a Supabase client or writing environment variables, always use `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` (or the equivalent framework prefix) instead of `SUPABASE_ANON_KEY`.

## 2. General Code Style
- Prefer functional components and React Hooks (if using React).
- Use TypeScript for all new files unless explicitly told otherwise.
- Avoid deprecated libraries (e.g., use `fetch` or `axios` instead of `request`).

## 3. NEXT.JS
- Use middleware for authentication and route protection.
- For API routes, always validate and sanitize input to prevent security vulnerabilities.
- For API routes that deal with Supabase use RLS (Row Level Security) pass-through to ensure that database queries respect user permissions.
- For API Routes that handle external API calls, use a requiredUser() function to ensure that the user is authenticated before making the call.
- Avoid hydration issues by ensuring that server-rendered content matches client-rendered content, especially when using dynamic data or user-specific content.