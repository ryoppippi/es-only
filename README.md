# es-only


## browser

```ts
import "es-only/browser";

console.log(window.location.href);
```

## bun

```ts
import "es-only/bun";

console.log(Bun.version);
```

## deno

```ts
import "es-only/deno";

console.log(Deno.version);
```

## node

```ts
import "es-only/node";

console.log(process.version);
```

## server-only

```ts
import "es-only/server-only";

// This module can only be used in Server Components
// It will throw an error if imported from Client Components
```

## Inspired by

- [esm-env](https://www.npmjs.com/package/esm-env)
- [server-only](https://www.npmjs.com/package/server-only)
- [bun-only](https://www.npmjs.com/package/bun-only)

