# Test Web Monetization

> A website dedicated to testing web monetization. It is running live at [testwebmonetization.com](https://testwebmonetization.com).

The most interesting file here is [the demo html page](https://github.com/TheRoccoB/testwebmonetization/blob/master/static/demo.html) that contains a full implementation of the Web Monetization javascript API.

Regenerate bookmarklet (do this if you modify `/static/bookmarklet/simulateMonetization.js`:

```
npm i -g bookmarklet 

bookmarklet static/bookmarklet/simulateMonetization.js > static/bookmarklet/simulateBookmarklet.txt
```
bookmarklet static/bookmarklet/simulateMonetization.js > simulateBookmarklet.txt

The demo is built with Vue.js and Nuxt.



## Build Setup

``` bash
# install dependencies
$ npm run install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
