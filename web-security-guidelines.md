# Web Security Guidelines

This will be an extension of the General Security Guidelines. Please read that document first.

## DOM

Within non-UI SDKs, libraries or frameworks, do not interact with the DOM. Avoiding reading from it and never write to it. The DOM is considered off limits for these products.

For UI-related SDKs, libraries or frameworks, products that have the explicit purpose of rendering UIs, only interact with the portions of the DOM that is exclusive to the product. Reaching outside of the dedicated DOM is considered unsafe.

When writing to the DOM, always, regardless of source, validate and escape text before applying it to DOM elements. What's more, there should be only one way to write text to the DOM to ensure consistency and safety.

## Cookies

Cookies written from the server should be HTTPOnly, and therefore inaccessible from the JavaScript runtime. Disabling HTTPOnly feature of cookies from the server to make something more convenient or to accomplish some goal is not advised.

## Web Storage API

Only store what's required within `localStorage` or `sessionStorage`. Use `sessionStorage` for high risk data. Only use `localStorage` for data that has to be shared across browser tabs or windows.

It's also important to clean up transient data as to keep memory usage low and potentially risky data from being left in the user's browser.

## URLs

We must avoid reading and writing to the URL. With SDKs, libraries or frameworks, reading or writing to the URL is like reading and writing to the DOM; we avoid it because we don't "own" it. The only exception is following a specification for authorization, like OAuth 2 redirects.

## Importing & Executing External Code

Avoid importing or executing scripts, regardless of its source, from outside the scope of the original codebase. Code coming from outside the package must be treated as dangerous and ignored, if possible.

