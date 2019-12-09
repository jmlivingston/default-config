# default-configs

An opinionated set of configurations for Babel, ESLint, and Prettier.

TLDR: Copy all or part of these into your package.json for tooling and configuration for Babel, ESLint, and Prettier.

## Why?

It is very common to start a new project only to realize that you need to copy over several configurations from previous projects. Whether using a boilerplate project like create-react-app or Next or starting fresh with WebPack, Parcel, or Rollup, it's While projects like create-react-app do a great job with things like

> Note: This project is currently based on React using prop-types, but these dependencies can be easily removed or ignored.

## Tooling

The following npm scripts are provided

- `npm run build-babel-config` - Parses package.json and build babel config based on dependencies.
- `npm run format` - Runs prettier on all files in src and scripts directory.
- `npm run lint` -

## General Opinions

- All configuration are kept in the package.json. This cuts down on noise and keeps the IDE looking tidy. If preferred, these can all be moved to .babelrc, .eslintrc, and .prettierrc respectively.
- Prettier and lint rules are run before commiting. These can be seen in the **husky** configuration.
- `npm install` is run after checkout, merge, or rebase. This prevents developers from running the project without the incorrect packages.
- Exact versions of packages are used to ensure developers are running code that is as close as possible to one another.

### Babel Opinions

- Uses TC39 Stage 3 proposals when available. These proposals are pretty solid at this point and major frameworks like create-react-app also use this approach.

### ESLint Opinions

- All React recommended rules are enabled.
- Prettier related rules are disabled for ESLint to avoid any clash with the two packages.
- Accessibility (jsx-a11y) are enabled by default.
- Problems are automatically fixed using **--fix**.
- Max warnings are set to zero usig **--max-warnings=0** to ensure code can't be commited without addressing lint rules.
- The following rules are enabled to prevent common problems in production.
  - **no-console**
  - **no-debugger**

### Prettier Opinions

All of the defaults are used except the following:

- **jsxBracketSameLine** - Saves some space in markup.
- **printWidth** set to 120 instead of 80 as many developers have reasonably decent sized screens.
- **semi** - Saves a keystroke and needed in rare cases with modern tooling.
- **singleQuote** - No Shift key required which prevents a tiny amount of developer fatigue.
