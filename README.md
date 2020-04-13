# default-config

An opinionated set of tooling and configurations for Babel, ESLint, Prettier, and Git!

TLDR: Copy all or part of this package.json into your package.json for tooling and configuration for [Babel](https://babeljs.io/), [ESLint](https://eslint.org), [Prettier](https://prettier.io), and [Git](https://git-scm.com).

## Why?

It is not uncommon to start a new project only to realize that you need to start copying and pasting all of your favorite configuration tweaks from previous projects. Whether using a boilerplate project like [create-react-app](https://create-react-app.dev) or [Next.js](https://nextjs.org) or starting fresh with [WebPack](https://webpack.js.org), [Parcel](https://parceljs.org), or [Rollup](https://rollupjs.org), it's likely that you may need to make a few tweaks.

Tools like create-react-app have excellent tooling, so you most likely won't be changing anything related to Babel or ESLint. However, it won't include things like [husky](https://github.com/typicode/husky), [lint-staged](https://github.com/okonet/lint-staged), or [Prettier](https://prettier.io) by default, so you will need to set these up yourself. If you're taking a minimal approach with something like Parcel or Rollup, you will be doing far more work to set up the project.

> Note: This project is currently assumes you're using React with prop-types, but these dependencies can be easily removed or ignored. You're welcome to fork the repo and tweak with your own opinions.

---

## Tooling

The following npm scripts are provided:

- `npm run build-babel-config` - Parses package.json and build babel config based on dependencies.
- `npm run format` - Runs prettier on all files in src and scripts directory.
- `npm run lint` - Runs eslint on all files in src and scripts directory.
- `npm run udpate-packages` - Updates all packages.

---

## General Opinions

- All configuration are kept in the package.json. This cuts down on noise and keeps the IDE looking tidy. If preferred, these can all be moved to .babelrc, .eslintrc, and .prettierrc respectively.
- Prettier and lint rules are run before commiting. These can be seen in the **husky** configuration.
- `npm install` is run after checkout, merge, or rebase. This prevents developers from running the project without the incorrect packages.
- Exact versions of packages are used to ensure developers are running code that is as close as possible to one another.

---

## Babel Opinions

- Uses TC39 Stage 3 proposals when available. These proposals are pretty solid at this point and major frameworks like create-react-app are also integrating them into their projects.

---

## ESLint Opinions

- All React recommended rules are enabled.
- Prettier related rules are disabled for ESLint to avoid any clash with the two packages.
- Accessibility (jsx-a11y) are enabled by default.
- Problems are automatically fixed using **--fix**.
- Max warnings are set to zero usig **--max-warnings=0** to ensure code can't be commited without addressing lint rules.
- The following rules are enabled to prevent common problems in production.
  - **no-console**
  - **no-debugger**

---

## Prettier Opinions

All of the defaults are used except the following:

- **jsxBracketSameLine** - Saves some space in markup.
- **printWidth** set to 120 instead of 80 as many developers have reasonably decent sized screens.
- **semi** - Saves a keystroke and needed in rare cases with modern tooling.
- **singleQuote** - No Shift key required which prevents a tiny amount of developer fatigue.

<a target="_blank" rel="noopener noreferrer" href="https://www.johnlivingston.io/blog/default-config" class="d-block text-center">Discuss on Twitter</a>
