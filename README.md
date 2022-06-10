# Getting Started

This project showcases a simple use of environement variables for a dockerized React application.

## What problem does this solve?

React compiles environment variables directly into the page which goes against the portability of Docker images. Although there is no such thing as environment variables in the browser, this solution proposes to inject them though the [`window`](https://developer.mozilla.org/en-US/docs/Web/API/Window) object, which is supported by all browsers.

## How does it work?

### Requirements
* A file named `.env` shoud be created containing all environement variables names with default. This file can be checked out as it should not contain condidential no secret information.
* You should add `<script src="%PUBLIC_URL%/env.js"></script>` to `public/index.html` so the file can be picked up during the build time.

1. A bash script (`env.sh`) reads `.env` and creates a new `env.js` that injects the `window._env_` variable, which is then read by the code.
2. Docker -e options and docker-compose `environment` are then passed to the `window` object.
