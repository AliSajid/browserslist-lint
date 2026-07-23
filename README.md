# Browserslist Lint

<img width="120" height="120" alt="Browserslist logo by Anton Popov"
     src="https://browsersl.ist/logo.svg" align="right">

Check your [Browserslist](https://github.com/browserslist/browserslist/) config
with target browsers for popular mistakes.

```sh
npx browserslist-lint
```

Or try online: [`browsersl.ist`](https://browsersl.ist/)

Rules:

- `missedNotDead`: lack of `no dead` with queries like `last 2 versions`.
- `countryWasIgnored`: bad coverage in some country with >10M Internet users.
- `limitedBrowsers`: ignoring browsers diversity by calling only
  a few browsers directly in config.
- `alreadyDead`: browser with `not` is already in `not dead` or `defaults`.

---

<img src="https://cdn.evilmartians.com/badges/logo-no-label.svg" alt="" width="22" height="16" />  Browserslist Lint is built by <b><a href="https://evilmartians.com/">Evil Martians</a></b>, an American design and engineering consultancy for <b>developer tools, AI, and cybersecurity startups</b>.

---

## Pre-Commit Hook

This project is also available as a [pre-commit hook](https://pre-commit.com/). Please add the following to your pre-commit configuration.

```yaml
repos:
  - repo: https://github.com/browserslist/lint
    id: browserslist-lint
```

## JS API

```js
import { lint } from 'browserslist-lint'

lint('defaults, not ie 11') // => [{
//      id: 'alreadyDead',
//      message: '`not ie 11` already in `defaults`'
//      fixed: 'defaults'
//    }]

// Without option with find Browserslist automatically
lint() // => [{ id, message, fixed }]
```
