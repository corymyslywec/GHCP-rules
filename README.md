# LLM Rules

This repository is a growing set of practical rules for AI coding assistants, with the current focus on GitHub Copilot.

The goal is simple: document the extra instructions that help prevent common implementation mistakes caused by outdated training data, deprecated patterns, framework changes, or recurring model habits.

## Why This Exists

AI coding tools are useful, but they still make repeatable mistakes such as:

- using outdated APIs or legacy platform conventions
- choosing deprecated libraries or patterns
- missing project-specific security requirements
- generating code that is technically valid but wrong for the current ecosystem

This repo is meant to capture those corrections in one place so they can be reused and expanded over time.

## Current Scope

Right now this project is centered on [copilot-instructions.md](c:\stuff\work\webDev\LLM Rules\copilot-instructions.md), which contains custom instructions for GitHub Copilot.

The current rules cover:

- Supabase key usage, including avoiding the old anon key pattern in favor of publishable keys
- general code style preferences such as TypeScript and modern React patterns
- Next.js guidance around middleware, input validation, authentication checks, RLS pass-through, and hydration safety

## How To Use

Use the instructions in this repo as a baseline ruleset for Copilot in projects where you want stronger guardrails around modern implementation details.

Typical workflow:

1. Keep [copilot-instructions.md](c:\stuff\work\webDev\LLM Rules\copilot-instructions.md) in the workspace or copy the relevant rules into the target project's Copilot instruction file.
2. Add new rules whenever you notice a model repeatedly making the same mistake.
3. Prefer specific, corrective rules over broad prompting advice.
4. Update rules when platform guidance changes.

## What Makes A Good Rule

A useful rule in this repo should be:

- concrete enough to change model behavior
- tied to a real failure mode or recurring bad output
- current with the framework or platform version you are targeting
- easy to scan and hard to misinterpret

Good examples:

- naming the exact environment variable that should be used
- calling out a deprecated pattern that must not be generated
- requiring a specific auth or security check for a class of routes

Less useful examples:

- vague style advice with no clear action
- generic best practices that do not address a real model failure
- long narrative explanations that bury the actual instruction

## Suggested Structure For New Rules

When adding to [copilot-instructions.md](c:\stuff\work\webDev\LLM Rules\copilot-instructions.md), try to keep each rule:

- grouped by platform, framework, or concern
- written in direct language
- explicit about what to do and what to avoid
- brief enough that the important instruction is obvious on first read

## Project Direction

This is intended to stay a living reference, not a polished framework or package.

As the list grows, the repo can expand to include:

- rules for additional AI tools beyond GitHub Copilot
- framework-specific instruction sets
- examples of bad outputs and the rules that correct them
- versioned guidance for fast-moving platforms

## Contributing To The List

If you add a rule, include it because the model actually got something wrong or because the ecosystem moved and the default model behavior has not caught up yet.

That keeps this repo focused on high-value corrections instead of turning it into a general style guide.