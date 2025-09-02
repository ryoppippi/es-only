# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is `es-only`, a lightweight utility library that provides runtime-specific imports for modern JavaScript environments (Browser, Bun, Deno, Node.js, and React Server Components). The library uses conditional exports to either provide an empty module for the target environment or throw runtime errors when used in incorrect environments.

## Architecture

The core architecture is based on **conditional exports** in `package.json`:

- Each environment (`browser`, `bun`, `deno`, `node`, `server-only`) has two possible imports:
  - Target environment: `src/empty.js` (no-op)
  - Other environments: `src/{environment}.error.js` (throws error)

### Key Files

- `package.json` - Defines conditional exports for each environment
- `src/empty.js` - Empty module that does nothing (used in target environments)
- `src/*.error.js` - Error-throwing modules for wrong environment usage
- `tsconfig.json` - TypeScript configuration using latest ESNext features

## Development Commands

This project uses Bun as the package manager with the following scripts:

```bash
# Install dependencies
bun install

# Linting and formatting
bun run lint              # Check code style
bun run format            # Fix linting issues automatically

# Type checking
bun run typecheck         # Uses tsgo --noEmit

# Release workflow
bun run release           # Runs lint + typecheck + bumpp for version bumping
```

## Git Workflow

- Uses custom git hooks in `.githooks/` (configured via `prepare` script)
- Pre-commit hook runs `lint-staged` to automatically lint and format staged files
- `package.json` is automatically sorted on commit via `sort-package-json`

## Testing Strategy

There are currently no automated tests. Testing is done by:

1. Importing modules in different JavaScript runtimes
2. Verifying correct behavior (empty import vs error throwing)
3. Manual verification across Browser/Bun/Deno/Node.js environments

## Important Patterns

- All modules use ES modules (`"type": "module"`)
- Error messages are specific to each environment for better developer experience
- Uses modern conditional exports instead of runtime detection
- Zero dependencies for maximum compatibility
- Uses `@ryoppippi/eslint-config` for consistent code style across projects
