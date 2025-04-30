# JavaScript Style Guide

Although most of the stylistic items are covered in ESLint or Prettier, there are a few things that are not. This will attempt to cover aspects to writing JavaScript/TypeScript as a unified organization.

## Naming

All names are either camelCase or PascalCase. No symbols are to be used unless a strong convention of doing so is recommended by framework or library.

We also don't use single letter names unless there's a strong convention for doing so, like `i` within a `for` loop.

### Functions

Functions should start with verbs, and end with a noun. The noun should be explicit about what it returns. 

Don't forget to match the plurality of the returned value. If the function returns a collection, make sure the name reflects that by being plural. If it returns an single item, it should be a singular noun.

```js
// Good
// Gets collection; "names" matches collection
function getUsernames() {}
// Gets first name of one user; singular noun
function getFirstName() {}

// Bad
// This sounds like a value, rather than a function
function usernames() {}
// This is not specific enough
function names() {}
```

### Methods

Methods should follow conventions of functions. But, due to their context, they can be simplified at time, dropping the noun from the verb if possible without loss of readability.

```js
// Good
let user = {
  // Needs context as to what this gets
  getFirstName: () => {},
  // This, on the other hand, could be a simple verb
  delete: () => {},
};

user.getFirstName(); // clear
user.delete(); // also clear
```

### Properties

Properties should always be nouns and reflect the proper plurality.

```js
// Good
const users = [];
let origin = 'https://example.com';

// Bad
const address = [];
let favorites = 'Dubstep';
```

### Primitive values

1. Strings: noun and descriptive
2. Numbers: noun and descriptive
3. Boolean: a short question, starting with an auxiliary verb; e.g. `isEnabled`, `hasSubscribed`, `canDelete`

## Comments

All modules, classes, and first level exports should be documented with comments that follow the JSDoc standard, complete with types. This information is used to generate our API documentation.

```js
/**
 * @function getUsernames - this function returns the full collection of users
 * @param {Status} status - filters the user by status: "active" or "inactive"
 * @returns {User[]} - returns users matching the status filter, if present
 */
```

Note: even if TypeScript is used, the types are important for our developer facing API documentation.

Short notes, TODO comments or small helper comments can be inline style, e.g. `// TODO: ...`. These should be used sparingly as the code should "speak for itself", or be "self documenting".

## Filenames

Filenames are always lowercase, and multiple words are separated by a dash. We also use a dot notation style to identify specific intention: `auth.test.js`, `auth.mock.js` or `username.interfaces.ts`. We avoid the use of `index.js` or `index.ts` as much as possible. Doing so requires knowing what directory in file is in to understand context.

```text
// Good
user-authentication.js
header.ts
stage-metadata.mock.js
central-login.test.ts

// Bad
index.js
embeddedLogin.ts
main.ts
session_management.js
```

## Copyright Statement

The following copyright statement should be included at the top of every source file:

```
/*
 * Copyright (c) 2020 - 2025 Ping Identity Corporation. All rights reserved.
 *
 * This software may be modified and distributed under the terms
 * of the MIT license. See the LICENSE file for details.
 */
 ```

## Organization

### Statement types

Within files, declarations/statements are organized by type and then alphabetized in the following manner:

```js
// imports
// alphabetized by module name, not import name
import external from 'modules';

// alphabetized by file name, not import name
import internal from './files';

// exports
// alphabetized by variable, property or function name
export const a = 'a';
export const b = 'b';

export let c = 'c';

export function getItem() {}

// variables
const d = 'd';
const e = 'e';

let f = 'f';

// functions
function g() {}

// logic and conditions
if (thing === true) {
  f = 'active';
}
```

## Functions

Standalone functions are to be written with the keyword `function`. Methods are written as method definitions. Lambdas or "inline functions" can be written as arrow functions.

```js
// Good
// Standalone
function getUser() {}
// Inline or lambda
const inactiveUsers = users.find((user) => user.inactive === true);
// Method definition
let user = {
  delete() {},
};

// Bad
const getEmail = () => {};
```

