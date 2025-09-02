# es-only

Runtime-specific imports for modern JavaScript environments.

## Installation

```bash
npm install es-only
```

## Usage

Import the environment-specific module to ensure your code only runs in the intended environment:

### browser

```ts
import 'es-only/browser';

console.log(window.location.href);
```

### bun

```ts
import 'es-only/bun';

console.log(Bun.version);
```

### deno

```ts
import 'es-only/deno';

console.log(Deno.version);
```

### node

```ts
import 'es-only/node';

console.log(process.version);
```

### server-only

```ts
import 'es-only/server-only';

// This module can only be used in Server Components
// It will throw an error if imported from Client Components
```

## How it works

Each import uses conditional exports to either do nothing (when running in the correct environment) or throw a runtime error (when running in the wrong environment).

## Inspired by

- [esm-env](https://www.npmjs.com/package/esm-env)
- [server-only](https://www.npmjs.com/package/server-only)
- [bun-only](https://www.npmjs.com/package/bun-only)
