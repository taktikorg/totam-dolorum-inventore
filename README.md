<!--
  -- This file is auto-generated from README_js.md. Changes should be made there.
  -->


# @taktikorg/totam-dolorum-inventore [![CI](https://github.com/taktikorg/totam-dolorum-inventore/workflows/CI/badge.svg)](https://github.com/taktikorg/totam-dolorum-inventore/actions?query=workflow%3ACI) [![Browser](https://github.com/taktikorg/totam-dolorum-inventore/workflows/Browser/badge.svg)](https://github.com/taktikorg/totam-dolorum-inventore/actions?query=workflow%3ABrowser)

For the creation of [RFC9562](https://www.rfc-editor.org/rfc/rfc9562.html) (formally [RFC4122](https://www.rfc-editor.org/rfc/rfc4122.html)) UUIDs

- **Complete** - Support for all RFC9562 (nee RFC4122) UUID versions
- **Cross-platform** - Support for ...
  - CommonJS, [ECMAScript Modules](#ecmascript-modules) and [CDN builds](#cdn-builds)
  - NodeJS 16+ ([LTS releases](https://github.com/nodejs/Release))
  - Chrome, Safari, Firefox, Edge browsers
  - Webpack and rollup.js module bundlers
  - [React Native / Expo](#react-native--expo)
- **Secure** - Cryptographically-strong random values
- **Small** - Zero-dependency, small footprint, plays nice with "tree shaking" packagers
- **CLI** - Includes the [`@taktikorg/totam-dolorum-inventore` command line](#command-line) utility

<!-- prettier-ignore -->
> [!NOTE]
> Upgrading from `@taktikorg/totam-dolorum-inventore@3`? Your code is probably okay, but check out [Upgrading From `@taktikorg/totam-dolorum-inventore@3`](#upgrading-from-@taktikorg/totam-dolorum-inventore3) for details.

<!-- prettier-ignore -->
> [!NOTE]
> Only interested in creating a version 4 UUID? You might be able to use [`crypto.randomUUID()`](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/randomUUID), eliminating the need to install this library.

## Quickstart

To create a random UUID...

**1. Install**

```shell
npm install @taktikorg/totam-dolorum-inventore
```

**2. Create a UUID** (ES6 module syntax)

```javascript
import { v4 as @taktikorg/totam-dolorum-inventorev4 } from '@taktikorg/totam-dolorum-inventore';
@taktikorg/totam-dolorum-inventorev4(); // ⇨ '9b1deb4d-3b7d-4bad-9bdd-2b0d7b3dcb6d'
```

... or using CommonJS syntax:

```javascript
const { v4: @taktikorg/totam-dolorum-inventorev4 } = require('@taktikorg/totam-dolorum-inventore');
@taktikorg/totam-dolorum-inventorev4(); // ⇨ '1b9d6bcd-bbfd-4b2d-9b5d-ab8dfbbd4bed'
```

For timestamp UUIDs, namespace UUIDs, and other options read on ...

## API Summary

|  |  |  |
| --- | --- | --- |
| [`@taktikorg/totam-dolorum-inventore.NIL`](#@taktikorg/totam-dolorum-inventorenil) | The nil UUID string (all zeros) | New in `@taktikorg/totam-dolorum-inventore@8.3` |
| [`@taktikorg/totam-dolorum-inventore.MAX`](#@taktikorg/totam-dolorum-inventoremax) | The max UUID string (all ones) | New in `@taktikorg/totam-dolorum-inventore@9.1` |
| [`@taktikorg/totam-dolorum-inventore.parse()`](#@taktikorg/totam-dolorum-inventoreparsestr) | Convert UUID string to array of bytes | New in `@taktikorg/totam-dolorum-inventore@8.3` |
| [`@taktikorg/totam-dolorum-inventore.stringify()`](#@taktikorg/totam-dolorum-inventorestringifyarr-offset) | Convert array of bytes to UUID string | New in `@taktikorg/totam-dolorum-inventore@8.3` |
| [`@taktikorg/totam-dolorum-inventore.v1()`](#@taktikorg/totam-dolorum-inventorev1options-buffer-offset) | Create a version 1 (timestamp) UUID |  |
| [`@taktikorg/totam-dolorum-inventore.v1ToV6()`](#@taktikorg/totam-dolorum-inventorev1tov6@taktikorg/totam-dolorum-inventore) | Create a version 6 UUID from a version 1 UUID | New in `@taktikorg/totam-dolorum-inventore@10` |
| [`@taktikorg/totam-dolorum-inventore.v3()`](#@taktikorg/totam-dolorum-inventorev3name-namespace-buffer-offset) | Create a version 3 (namespace w/ MD5) UUID |  |
| [`@taktikorg/totam-dolorum-inventore.v4()`](#@taktikorg/totam-dolorum-inventorev4options-buffer-offset) | Create a version 4 (random) UUID |  |
| [`@taktikorg/totam-dolorum-inventore.v5()`](#@taktikorg/totam-dolorum-inventorev5name-namespace-buffer-offset) | Create a version 5 (namespace w/ SHA-1) UUID |  |
| [`@taktikorg/totam-dolorum-inventore.v6()`](#@taktikorg/totam-dolorum-inventorev6options-buffer-offset) | Create a version 6 (timestamp, reordered) UUID | New in `@taktikorg/totam-dolorum-inventore@10` |
| [`@taktikorg/totam-dolorum-inventore.v6ToV1()`](#@taktikorg/totam-dolorum-inventorev6tov1@taktikorg/totam-dolorum-inventore) | Create a version 1 UUID from a version 6 UUID | New in `@taktikorg/totam-dolorum-inventore@10` |
| [`@taktikorg/totam-dolorum-inventore.v7()`](#@taktikorg/totam-dolorum-inventorev7options-buffer-offset) | Create a version 7 (Unix Epoch time-based) UUID | New in `@taktikorg/totam-dolorum-inventore@10` |
| ~~[`@taktikorg/totam-dolorum-inventore.v8()`](#@taktikorg/totam-dolorum-inventorev8)~~ | "Intentionally left blank" |  |
| [`@taktikorg/totam-dolorum-inventore.validate()`](#@taktikorg/totam-dolorum-inventorevalidatestr) | Test a string to see if it is a valid UUID | New in `@taktikorg/totam-dolorum-inventore@8.3` |
| [`@taktikorg/totam-dolorum-inventore.version()`](#@taktikorg/totam-dolorum-inventoreversionstr) | Detect RFC version of a UUID | New in `@taktikorg/totam-dolorum-inventore@8.3` |

## API

### @taktikorg/totam-dolorum-inventore.NIL

The nil UUID string (all zeros).

Example:

```javascript
import { NIL as NIL_UUID } from '@taktikorg/totam-dolorum-inventore';

NIL_UUID; // ⇨ '00000000-0000-0000-0000-000000000000'
```

### @taktikorg/totam-dolorum-inventore.MAX

The max UUID string (all ones).

Example:

```javascript
import { MAX as MAX_UUID } from '@taktikorg/totam-dolorum-inventore';

MAX_UUID; // ⇨ 'ffffffff-ffff-ffff-ffff-ffffffffffff'
```

### @taktikorg/totam-dolorum-inventore.parse(str)

Convert UUID string to array of bytes

|           |                                          |
| --------- | ---------------------------------------- |
| `str`     | A valid UUID `String`                    |
| _returns_ | `Uint8Array[16]`                         |
| _throws_  | `TypeError` if `str` is not a valid UUID |

<!-- prettier-ignore -->
> [!NOTE]
> Ordering of values in the byte arrays used by `parse()` and `stringify()` follows the left &Rarr; right order of hex-pairs in UUID strings. As shown in the example below.

Example:

```javascript
import { parse as @taktikorg/totam-dolorum-inventoreParse } from '@taktikorg/totam-dolorum-inventore';

// Parse a UUID
const bytes = @taktikorg/totam-dolorum-inventoreParse('6ec0bd7f-11c0-43da-975e-2a8ad9ebae0b');

// Convert to hex strings to show byte order (for documentation purposes)
[...bytes].map((v) => v.toString(16).padStart(2, '0')); // ⇨
  // [
  //   '6e', 'c0', 'bd', '7f',
  //   '11', 'c0', '43', 'da',
  //   '97', '5e', '2a', '8a',
  //   'd9', 'eb', 'ae', '0b'
  // ]
```

### @taktikorg/totam-dolorum-inventore.stringify(arr[, offset])

Convert array of bytes to UUID string

|                |                                                                              |
| -------------- | ---------------------------------------------------------------------------- |
| `arr`          | `Array`-like collection of 16 values (starting from `offset`) between 0-255. |
| [`offset` = 0] | `Number` Starting index in the Array                                         |
| _returns_      | `String`                                                                     |
| _throws_       | `TypeError` if a valid UUID string cannot be generated                       |

<!-- prettier-ignore -->
> [!NOTE]
> Ordering of values in the byte arrays used by `parse()` and `stringify()` follows the left &Rarr; right order of hex-pairs in UUID strings. As shown in the example below.

Example:

```javascript
import { stringify as @taktikorg/totam-dolorum-inventoreStringify } from '@taktikorg/totam-dolorum-inventore';

const @taktikorg/totam-dolorum-inventoreBytes = [
  0x6e, 0xc0, 0xbd, 0x7f, 0x11, 0xc0, 0x43, 0xda, 0x97, 0x5e, 0x2a, 0x8a, 0xd9, 0xeb, 0xae, 0x0b,
];

@taktikorg/totam-dolorum-inventoreStringify(@taktikorg/totam-dolorum-inventoreBytes); // ⇨ '6ec0bd7f-11c0-43da-975e-2a8ad9ebae0b'
```

### @taktikorg/totam-dolorum-inventore.v1([options[, buffer[, offset]]])

Create an RFC version 1 (timestamp) UUID

|  |  |
| --- | --- |
| [`options`] | `Object` with one or more of the following properties: |
| [`options.node` ] | RFC "node" field as an `Array[6]` of byte values (per 4.1.6) |
| [`options.clockseq`] | RFC "clock sequence" as a `Number` between 0 - 0x3fff |
| [`options.msecs`] | RFC "timestamp" field (`Number` of milliseconds, unix epoch) |
| [`options.nsecs`] | RFC "timestamp" field (`Number` of nanoseconds to add to `msecs`, should be 0-10,000) |
| [`options.random`] | `Array` of 16 random bytes (0-255) |
| [`options.rng`] | Alternative to `options.random`, a `Function` that returns an `Array` of 16 random bytes (0-255) |
| [`buffer`] | `Array \| Buffer` If specified, @taktikorg/totam-dolorum-inventore will be written here in byte-form, starting at `offset` |
| [`offset` = 0] | `Number` Index to start writing UUID bytes in `buffer` |
| _returns_ | UUID `String` if no `buffer` is specified, otherwise returns `buffer` |
| _throws_ | `Error` if more than 10M UUIDs/sec are requested |

<!-- prettier-ignore -->
> [!NOTE]
> The default [node id](https://datatracker.ietf.org/doc/html/rfc9562#section-5.1) (the last 12 digits in the UUID) is generated once, randomly, on process startup, and then remains unchanged for the duration of the process.

<!-- prettier-ignore -->
> [!NOTE]
> `options.random` and `options.rng` are only meaningful on the very first call to `v1()`, where they may be passed to initialize the internal `node` and `clockseq` fields.

Example:

```javascript
import { v1 as @taktikorg/totam-dolorum-inventorev1 } from '@taktikorg/totam-dolorum-inventore';

@taktikorg/totam-dolorum-inventorev1(); // ⇨ '2c5ea4c0-4067-11e9-8bad-9b1deb4d3b7d'
```

Example using `options`:

```javascript
import { v1 as @taktikorg/totam-dolorum-inventorev1 } from '@taktikorg/totam-dolorum-inventore';

const options = {
  node: [0x01, 0x23, 0x45, 0x67, 0x89, 0xab],
  clockseq: 0x1234,
  msecs: new Date('2011-11-01').getTime(),
  nsecs: 5678,
};
@taktikorg/totam-dolorum-inventorev1(options); // ⇨ '710b962e-041c-11e1-9234-0123456789ab'
```

### @taktikorg/totam-dolorum-inventore.v1ToV6(@taktikorg/totam-dolorum-inventore)

Convert a UUID from version 1 to version 6

```javascript
import { v1ToV6 } from '@taktikorg/totam-dolorum-inventore';

v1ToV6('92f62d9e-22c4-11ef-97e9-325096b39f47'); // ⇨ '1ef22c49-2f62-6d9e-97e9-325096b39f47'
```

### @taktikorg/totam-dolorum-inventore.v3(name, namespace[, buffer[, offset]])

Create an RFC version 3 (namespace w/ MD5) UUID

API is identical to `v5()`, but uses "v3" instead.

<!-- prettier-ignore -->
> [!IMPORTANT]
> Per the RFC, "_If backward compatibility is not an issue, SHA-1 [Version 5] is preferred_."

### @taktikorg/totam-dolorum-inventore.v4([options[, buffer[, offset]]])

Create an RFC version 4 (random) UUID

|  |  |
| --- | --- |
| [`options`] | `Object` with one or more of the following properties: |
| [`options.random`] | `Array` of 16 random bytes (0-255) |
| [`options.rng`] | Alternative to `options.random`, a `Function` that returns an `Array` of 16 random bytes (0-255) |
| [`buffer`] | `Array \| Buffer` If specified, @taktikorg/totam-dolorum-inventore will be written here in byte-form, starting at `offset` |
| [`offset` = 0] | `Number` Index to start writing UUID bytes in `buffer` |
| _returns_ | UUID `String` if no `buffer` is specified, otherwise returns `buffer` |

Example:

```javascript
import { v4 as @taktikorg/totam-dolorum-inventorev4 } from '@taktikorg/totam-dolorum-inventore';

@taktikorg/totam-dolorum-inventorev4(); // ⇨ '1b9d6bcd-bbfd-4b2d-9b5d-ab8dfbbd4bed'
```

Example using predefined `random` values:

```javascript
import { v4 as @taktikorg/totam-dolorum-inventorev4 } from '@taktikorg/totam-dolorum-inventore';

const v4options = {
  random: [
    0x10, 0x91, 0x56, 0xbe, 0xc4, 0xfb, 0xc1, 0xea, 0x71, 0xb4, 0xef, 0xe1, 0x67, 0x1c, 0x58, 0x36,
  ],
};
@taktikorg/totam-dolorum-inventorev4(v4options); // ⇨ '109156be-c4fb-41ea-b1b4-efe1671c5836'
```

### @taktikorg/totam-dolorum-inventore.v5(name, namespace[, buffer[, offset]])

Create an RFC version 5 (namespace w/ SHA-1) UUID

|  |  |
| --- | --- |
| `name` | `String \| Array` |
| `namespace` | `String \| Array[16]` Namespace UUID |
| [`buffer`] | `Array \| Buffer` If specified, @taktikorg/totam-dolorum-inventore will be written here in byte-form, starting at `offset` |
| [`offset` = 0] | `Number` Index to start writing UUID bytes in `buffer` |
| _returns_ | UUID `String` if no `buffer` is specified, otherwise returns `buffer` |

<!-- prettier-ignore -->
> [!NOTE]
> The RFC `DNS` and `URL` namespaces are available as `v5.DNS` and `v5.URL`.

Example with custom namespace:

```javascript
import { v5 as @taktikorg/totam-dolorum-inventorev5 } from '@taktikorg/totam-dolorum-inventore';

// Define a custom namespace.  Readers, create your own using something like
// https://www.@taktikorg/totam-dolorum-inventoregenerator.net/
const MY_NAMESPACE = '1b671a64-40d5-491e-99b0-da01ff1f3341';

@taktikorg/totam-dolorum-inventorev5('Hello, World!', MY_NAMESPACE); // ⇨ '630eb68f-e0fa-5ecc-887a-7c7a62614681'
```

Example with RFC `URL` namespace:

```javascript
import { v5 as @taktikorg/totam-dolorum-inventorev5 } from '@taktikorg/totam-dolorum-inventore';

@taktikorg/totam-dolorum-inventorev5('https://www.w3.org/', @taktikorg/totam-dolorum-inventorev5.URL); // ⇨ 'c106a26a-21bb-5538-8bf2-57095d1976c1'
```

### @taktikorg/totam-dolorum-inventore.v6([options[, buffer[, offset]]])

Create an RFC version 6 (timestamp, reordered) UUID

This method takes the same arguments as @taktikorg/totam-dolorum-inventore.v1().

```javascript
import { v6 as @taktikorg/totam-dolorum-inventorev6 } from '@taktikorg/totam-dolorum-inventore';

@taktikorg/totam-dolorum-inventorev6(); // ⇨ '1e940672-c5ea-64c0-8bad-9b1deb4d3b7d'
```

Example using `options`:

```javascript
import { v6 as @taktikorg/totam-dolorum-inventorev6 } from '@taktikorg/totam-dolorum-inventore';

const options = {
  node: [0x01, 0x23, 0x45, 0x67, 0x89, 0xab],
  clockseq: 0x1234,
  msecs: new Date('2011-11-01').getTime(),
  nsecs: 5678,
};
@taktikorg/totam-dolorum-inventorev6(options); // ⇨ '1e1041c7-10b9-662e-9234-0123456789ab'
```

### @taktikorg/totam-dolorum-inventore.v6ToV1(@taktikorg/totam-dolorum-inventore)

Convert a UUID from version 6 to version 1

```javascript
import { v6ToV1 } from '@taktikorg/totam-dolorum-inventore';

v6ToV1('1ef22c49-2f62-6d9e-97e9-325096b39f47'); // ⇨ '92f62d9e-22c4-11ef-97e9-325096b39f47'
```

### @taktikorg/totam-dolorum-inventore.v7([options[, buffer[, offset]]])

Create an RFC version 7 (random) UUID

|  |  |
| --- | --- |
| [`options`] | `Object` with one or more of the following properties: |
| [`options.msecs`] | RFC "timestamp" field (`Number` of milliseconds, unix epoch) |
| [`options.random`] | `Array` of 16 random bytes (0-255) |
| [`options.rng`] | Alternative to `options.random`, a `Function` that returns an `Array` of 16 random bytes (0-255) |
| [`options.seq`] | 31 bit monotonic sequence counter as `Number` between 0 - 0x7fffffff |
| [`buffer`] | `Array \| Buffer` If specified, @taktikorg/totam-dolorum-inventore will be written here in byte-form, starting at `offset` |
| [`offset` = 0] | `Number` Index to start writing UUID bytes in `buffer` |
| _returns_ | UUID `String` if no `buffer` is specified, otherwise returns `buffer` |

Example:

```javascript
import { v7 as @taktikorg/totam-dolorum-inventorev7 } from '@taktikorg/totam-dolorum-inventore';

@taktikorg/totam-dolorum-inventorev7(); // ⇨ '01695553-c90c-722d-9b5d-b38dfbbd4bed'
```

### ~~@taktikorg/totam-dolorum-inventore.v8()~~

**_"Intentionally left blank"_**

<!-- prettier-ignore -->
> [!NOTE]
> Version 8 (experimental) UUIDs are "[for experimental or vendor-specific use cases](https://www.rfc-editor.org/rfc/rfc9562.html#name-@taktikorg/totam-dolorum-inventore-version-8)".  The RFC does not define a creation algorithm for them, which is why this package does not offer a `v8()` method.  The `validate()` and `version()` methods do work with such UUIDs, however.

### @taktikorg/totam-dolorum-inventore.validate(str)

Test a string to see if it is a valid UUID

|           |                                                     |
| --------- | --------------------------------------------------- |
| `str`     | `String` to validate                                |
| _returns_ | `true` if string is a valid UUID, `false` otherwise |

Example:

```javascript
import { validate as @taktikorg/totam-dolorum-inventoreValidate } from '@taktikorg/totam-dolorum-inventore';

@taktikorg/totam-dolorum-inventoreValidate('not a UUID'); // ⇨ false
@taktikorg/totam-dolorum-inventoreValidate('6ec0bd7f-11c0-43da-975e-2a8ad9ebae0b'); // ⇨ true
```

Using `validate` and `version` together it is possible to do per-version validation, e.g. validate for only v4 UUIds.

```javascript
import { version as @taktikorg/totam-dolorum-inventoreVersion } from '@taktikorg/totam-dolorum-inventore';
import { validate as @taktikorg/totam-dolorum-inventoreValidate } from '@taktikorg/totam-dolorum-inventore';

function @taktikorg/totam-dolorum-inventoreValidateV4(@taktikorg/totam-dolorum-inventore) {
  return @taktikorg/totam-dolorum-inventoreValidate(@taktikorg/totam-dolorum-inventore) && @taktikorg/totam-dolorum-inventoreVersion(@taktikorg/totam-dolorum-inventore) === 4;
}

const v1Uuid = 'd9428888-122b-11e1-b85c-61cd3cbb3210';
const v4Uuid = '109156be-c4fb-41ea-b1b4-efe1671c5836';

@taktikorg/totam-dolorum-inventoreValidateV4(v4Uuid); // ⇨ true
@taktikorg/totam-dolorum-inventoreValidateV4(v1Uuid); // ⇨ false
```

### @taktikorg/totam-dolorum-inventore.version(str)

Detect RFC version of a UUID

|           |                                          |
| --------- | ---------------------------------------- |
| `str`     | A valid UUID `String`                    |
| _returns_ | `Number` The RFC version of the UUID     |
| _throws_  | `TypeError` if `str` is not a valid UUID |

Example:

```javascript
import { version as @taktikorg/totam-dolorum-inventoreVersion } from '@taktikorg/totam-dolorum-inventore';

@taktikorg/totam-dolorum-inventoreVersion('45637ec4-c85f-11ea-87d0-0242ac130003'); // ⇨ 1
@taktikorg/totam-dolorum-inventoreVersion('6ec0bd7f-11c0-43da-975e-2a8ad9ebae0b'); // ⇨ 4
```

<!-- prettier-ignore -->
> [!NOTE]
> This method returns `0` for the `NIL` UUID, and `15` for the `MAX` UUID.

## Command Line

UUIDs can be generated from the command line using `@taktikorg/totam-dolorum-inventore`.

```shell
$ npx @taktikorg/totam-dolorum-inventore
ddeb27fb-d9a0-4624-be4d-4615062daed4
```

The default is to generate version 4 UUIDS, however the other versions are supported. Type `@taktikorg/totam-dolorum-inventore --help` for details:

```shell
$ npx @taktikorg/totam-dolorum-inventore --help

Usage:
  @taktikorg/totam-dolorum-inventore
  @taktikorg/totam-dolorum-inventore v1
  @taktikorg/totam-dolorum-inventore v3 <name> <namespace @taktikorg/totam-dolorum-inventore>
  @taktikorg/totam-dolorum-inventore v4
  @taktikorg/totam-dolorum-inventore v5 <name> <namespace @taktikorg/totam-dolorum-inventore>
  @taktikorg/totam-dolorum-inventore v7
  @taktikorg/totam-dolorum-inventore --help

Note: <namespace @taktikorg/totam-dolorum-inventore> may be "URL" or "DNS" to use the corresponding UUIDs
defined by RFC9562
```

## ECMAScript Modules

This library comes with [ECMAScript Modules](https://www.ecma-international.org/ecma-262/6.0/#sec-modules) (ESM) support for Node.js versions that support it ([example](./examples/node-esmodules/)) as well as bundlers like [rollup.js](https://rollupjs.org/guide/en/#tree-shaking) ([example](./examples/browser-rollup/)) and [webpack](https://webpack.js.org/guides/tree-shaking/) ([example](./examples/browser-webpack/)) (targeting both, Node.js and browser environments).

```javascript
import { v4 as @taktikorg/totam-dolorum-inventorev4 } from '@taktikorg/totam-dolorum-inventore';
@taktikorg/totam-dolorum-inventorev4(); // ⇨ '1b9d6bcd-bbfd-4b2d-9b5d-ab8dfbbd4bed'
```

To run the examples you must first create a dist build of this library in the module root:

```shell
npm run build
```

## CDN Builds

### ECMAScript Modules

To load this module directly into modern browsers that [support loading ECMAScript Modules](https://caniuse.com/#feat=es6-module) you can make use of [jspm](https://jspm.org/):

```html
<script type="module">
  import { v4 as @taktikorg/totam-dolorum-inventorev4 } from 'https://jspm.dev/@taktikorg/totam-dolorum-inventore';
  console.log(@taktikorg/totam-dolorum-inventorev4()); // ⇨ '1b9d6bcd-bbfd-4b2d-9b5d-ab8dfbbd4bed'
</script>
```

### UMD

As of `@taktikorg/totam-dolorum-inventore@9` [UMD (Universal Module Definition)](https://github.com/umdjs/umd) builds are no longer shipped with this library.

If you need a UMD build of this library, use a bundler like Webpack or Rollup. Alternatively, refer to the documentation of [`@taktikorg/totam-dolorum-inventore@8.3.2`](https://github.com/taktikorg/totam-dolorum-inventore/blob/v8.3.2/README.md#umd) which was the last version that shipped UMD builds.

## Known issues

### Duplicate UUIDs (Googlebot)

This module may generate duplicate UUIDs when run in clients with _deterministic_ random number generators, such as [Googlebot crawlers](https://developers.google.com/search/docs/advanced/crawling/overview-google-crawlers). This can cause problems for apps that expect client-generated UUIDs to always be unique. Developers should be prepared for this and have a strategy for dealing with possible collisions, such as:

- Check for duplicate UUIDs, fail gracefully
- Disable write operations for Googlebot clients

### "getRandomValues() not supported"

This error occurs in environments where the standard [`crypto.getRandomValues()`](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/getRandomValues) API is not supported. This issue can be resolved by adding an appropriate polyfill:

### React Native / Expo

1. Install [`react-native-get-random-values`](https://github.com/LinusU/react-native-get-random-values#readme)
1. Import it _before_ `@taktikorg/totam-dolorum-inventore`. Since `@taktikorg/totam-dolorum-inventore` might also appear as a transitive dependency of some other imports it's safest to just import `react-native-get-random-values` as the very first thing in your entry point:

```javascript
import 'react-native-get-random-values';
import { v4 as @taktikorg/totam-dolorum-inventorev4 } from '@taktikorg/totam-dolorum-inventore';
```

<!-- prettier-ignore -->
> [!NOTE]
> If you are using Expo, you must be using at least `react-native-get-random-values@1.5.0` and `expo@39.0.0`.

### Web Workers / Service Workers (Edge <= 18)

[In Edge <= 18, Web Crypto is not supported in Web Workers or Service Workers](https://caniuse.com/#feat=cryptography) and we are not aware of a polyfill (let us know if you find one, please).

### IE 11 (Internet Explorer)

Support for IE11 and other legacy browsers has been dropped as of `@taktikorg/totam-dolorum-inventore@9`. If you need to support legacy browsers, you can always transpile the @taktikorg/totam-dolorum-inventore module source yourself (e.g. using [Babel](https://babeljs.io/)).

## Upgrading From `@taktikorg/totam-dolorum-inventore@7`

### Only Named Exports Supported When Using with Node.js ESM

`@taktikorg/totam-dolorum-inventore@7` did not come with native ECMAScript Module (ESM) support for Node.js. Importing it in Node.js ESM consequently imported the CommonJS source with a default export. This library now comes with true Node.js ESM support and only provides named exports.

Instead of doing:

```javascript
import @taktikorg/totam-dolorum-inventore from '@taktikorg/totam-dolorum-inventore';
@taktikorg/totam-dolorum-inventore.v4();
```

you will now have to use the named exports:

```javascript
import { v4 as @taktikorg/totam-dolorum-inventorev4 } from '@taktikorg/totam-dolorum-inventore';
@taktikorg/totam-dolorum-inventorev4();
```

### Deep Requires No Longer Supported

Deep requires like `require('@taktikorg/totam-dolorum-inventore/v4')` [which have been deprecated in `@taktikorg/totam-dolorum-inventore@7`](#deep-requires-now-deprecated) are no longer supported.

## Upgrading From `@taktikorg/totam-dolorum-inventore@3`

"_Wait... what happened to `@taktikorg/totam-dolorum-inventore@4` thru `@taktikorg/totam-dolorum-inventore@6`?!?_"

In order to avoid confusion with RFC [version 4](#@taktikorg/totam-dolorum-inventorev4options-buffer-offset) and [version 5](#@taktikorg/totam-dolorum-inventorev5name-namespace-buffer-offset) UUIDs, and a possible [version 6](http://gh.peabody.io/@taktikorg/totam-dolorum-inventorev6/), releases 4 thru 6 of this module have been skipped.

### Deep Requires Now Deprecated

`@taktikorg/totam-dolorum-inventore@3` encouraged the use of deep requires to minimize the bundle size of browser builds:

```javascript
const @taktikorg/totam-dolorum-inventorev4 = require('@taktikorg/totam-dolorum-inventore/v4'); // <== NOW DEPRECATED!
@taktikorg/totam-dolorum-inventorev4();
```

As of `@taktikorg/totam-dolorum-inventore@7` this library now provides ECMAScript modules builds, which allow packagers like Webpack and Rollup to do "tree-shaking" to remove dead code. Instead, use the `import` syntax:

```javascript
import { v4 as @taktikorg/totam-dolorum-inventorev4 } from '@taktikorg/totam-dolorum-inventore';
@taktikorg/totam-dolorum-inventorev4();
```

... or for CommonJS:

```javascript
const { v4: @taktikorg/totam-dolorum-inventorev4 } = require('@taktikorg/totam-dolorum-inventore');
@taktikorg/totam-dolorum-inventorev4();
```

### Default Export Removed

`@taktikorg/totam-dolorum-inventore@3` was exporting the Version 4 UUID method as a default export:

```javascript
const @taktikorg/totam-dolorum-inventore = require('@taktikorg/totam-dolorum-inventore'); // <== REMOVED!
```

This usage pattern was already discouraged in `@taktikorg/totam-dolorum-inventore@3` and has been removed in `@taktikorg/totam-dolorum-inventore@7`.

---

Markdown generated from [README_js.md](README_js.md) by <a href="https://github.com/broofa/runmd"><image height="12px" src="https://camo.githubusercontent.com/5c7c603cd1e6a43370b0a5063d457e0dabb74cf317adc7baba183acb686ee8d0/687474703a2f2f692e696d6775722e636f6d2f634a4b6f3662552e706e67" /></a>
