# JavaScript Standards

## Tooling

To ensure we follow all the best practices in writing JavaScript (and also TypeScript), we recommend the industry standard tooling to automate the reporting and fixing of patterns and conventions that are non-idiomatic. The following are the tools:

1. Static analysis
  a. TypeScript: type and control flow checking
  b. ESLint: design patterns and code smells
  c. ESLint plugins: static accessibility analysis
  d. Prettier: syntax and formatter
2. Vitest: unit testing
3. Storybook (UI components only)
  a. Component testing
  b. Integration testing
  c. Interaction testing
  d. Accessibility testing
4. Playwright
  a. End-to-end testing
  b. Functional API testing
  c. Accessibility testing

### TypeScript

Below is the recommended config starter:

```json
{
  "compilerOptions": {
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true
  }
}
```

### ESLint

Below is the recommended config starter:

```json
{
  "parser": "@typescript-eslint/parser",
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier",
    "plugin:storybook/recommended"
  ],
  "plugins": ["@typescript-eslint"],
  "overrides": [
    {
      "files": ["test/**"],
      "plugins": ["plugin:playwright/recommended"]
    }
  ]
}
```

### Prettier

Below is the recommended config starter:

```json
{
  "useTabs": false,
  "singleQuote": true,
  "trailingComma": "all",
  "printWidth": 100,
  "overrides": [
    {
      "files": "*.json",
      "options": {
        "tabWidth": 2,
        "parser": "json"
      }
    }
  ]
}
```

## Design patterns

We follow the Unix design where appropriate, and you will hear us mention different ideas from this approach to software design. You can [read more about that the Unix philosophy in this article](https://cscie2x.dce.harvard.edu/hw/ch01s06.html). Another resource we refer to often is the [classic Design Patterns by the "Gang of Four"](https://www.digitalocean.com/community/tutorials/gangs-of-four-gof-design-patterns).

We also tend toward Functional Purity (as in Functional Programming or FP) at the core of software, and move side-effects and classes toward the edge. You can read more about that in [this article about Pushing Effects to the Edge.](https://thomashoneyman.com/guides/real-world-halogen/push-effects-to-the-edges/).

We also tend toward immutable, decoupled data or state rather than global, mutable data, coupled to other structures. You can read more about that here in [this article from the same series above](https://thomashoneyman.com/guides/real-world-halogen/design-data-pure-functions/).

This means core modules are small, tightly focused and mostly made of pure functions. Data flows in and out of these functions without side-effects or persisted state. This aids in easier testing, maintainability, and "composibility".

User-facing or external modules can be classes that are stateful and impure. These modules are to be composed of the stateless and pure core modules, leading to an abstraction that is clear and well defined.

Note: This is not to say that these are commandments, but more recommendations that can help guide how we solve problems collectively. It also helps centralize technical discussions around the same points of reference, using the same terminology.

## Making decisions

As software engineers, we have to make hundreds of decisions throughout development. When the decision is not clear, refer to our provided requirements and recommendations to help you arrive at a similar decision as anyone else in the team. Don't think of these as mandates or commandments, but guidelines and suggestions that help us build quality, maintainable code as a collaborative collective.

### Requirements

1. **Decoupled** from systems
2. **Agnostic** to frameworks
3. **Testable** by design
4. **Safe** by default
5. **Privacy** of information

### Recommendations

1. **Singular** responsibility
2. **Purity** of operation
3. **Isolation** of side-effects
4. **Transparent** Referentially
5. **Immutable** over mutable
6. **Functional** over object-oriented
7. **Interface** over implementation
8. **Composition** over inheritance
9. **Stateless** over stateful
10. **Clear** over clever

