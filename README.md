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

* `missedNotDead`: lack of `no dead` with queries like `last 2 versions`.
* `countryWasIgnored`: bad coverage in some country with >10M Internet users.
* `limitedBrowsers`: ignoring browsers diversity by calling only
  a few browsers directly in config.
* `alreadyDead`: browser with `not` is already in `not dead` or `defaults`.

<a href="https://evilmartians.com/?utm_source=browserslist-lint">
  <img src="https://evilmartians.com/badges/sponsored-by-evil-martians.svg"
       alt="Sponsored by Evil Martians" width="236" height="54">
</a>

## Pre-Commit Hook

This project is also available as a pre-commit hook. Please add the following to your pre-commit configuration.

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
