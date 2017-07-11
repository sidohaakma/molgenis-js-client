molgenis-api-client
-------------------
A javascript wrapper around the [isomorphic-fetch](https://github.com/matthew-andrews/isomorphic-fetch) API.
Simplifies using REST api's by abstracting get, post, and delete and providing default options.

Installation
------------

### CDN
```html
<script src="path/to/dist/main.bundle.js"></script>

<!-- Include a polyfill for ES6 Promises (optional) for IE11, UC Browser and Android browser support -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/core-js/2.4.1/core.js"></script>
```

### NPM
```bash
npm install @molgenis/molgenis-api-client --save
```

### Yarn
```bash
yarn add @molgenis/molgenis-api-client
```

Usage
-----

__Import as ES6 module__
```js
import api from '@molgenis/molgenis-api-client'

api.get(...)
api.post(...)
api.delete_(...)
```

__Named ES6 import__
```js
import { get, post, delete_ } from '@molgenis/molgenis-api-client'

get(...)
post(...)
delete_(...)

```

__CommonJS import__
```js
const api = require('@molgenis/molgenis-api-client/dist/main.bundle.js')
```

Examples
--------

the molgenis-api-client supports three methods: get, post, and delete

__GET__ examples

```js
get('/api/v2/EntityType').then(response => {...}, error => {...}))
get('/api/v2/EntityType', { headers: { 'Content-type': 'text' } }).then(response => {...}, error => {...})
```

__POST__ examples

```js
const data = {
  'items': ['1', '2'],
  'id': 'example'
}

const options = {
  'body': data
}

post('api/v2/PostData', options).then(response => {...}, error => {...})
```

__DELETE__ examples

```js
delete_('/api/v2/deleteById/1').then(response => {...}, error => {...})
```

Methods
-------

| Method | Description |
|--------|-------------|
| api.get() | Performs a fetch with method 'GET' |
| api.post() | Performs a fetch with method 'POST' |
| api.delete_() | Performs a fetch with method 'DELETE' |

Options
-------

The options object that can be supplied to different API methods can contain the following parameters

| Parameter | Description | Default value |
|-----------|-------------|---------------|
| method | `GET, POST, PUT, DELETE, HEAD` | Defaults to GET for get(), POST for post() and DELETE for delete_() |
| headers | associated Headers object | 'headers': { 'Accept': 'application/json', 'Content-Type': 'application/json' } |
| referrer | referrer of the request | undefined |
| mode | `cors, no-cors, same-origin` | undefined |
| credentials | should cookies go with the request? `omit, same-origin` | same-origin | 
| redirect | What to do on redirect. `follow, error, manual` | error | 
| integrity | subresource integrity value | undefined |
| cache | cache mode `default, reload, no-cache` | undefined |

Browser compatibility
---------------------

| IE11* | Edge | Chrome | Firefox | Safari | Opera | Android Browser* | UC Browser* |
|-------|------|--------|---------|--------|-------|------------------|-------------|
|  ✅   |   ✅  |   ✅   |     ✅   |   ✅   |    ✅   |        ✅        |      ✅      |


\* ES6 Promise polyfill should be included, see this [example](#CDN).

Note that this library is used in bleeding edge front end development. We do not and will not provide support on IE8 or lower.

Contributing
------------

This project uses [yarn](https://yarnpkg.com) for development.

To get started: `yarn install`

To build: `yarn build` 

To test: `yarn test`

To lint: `yarn lint`

To check flow types: `yarn flow`

