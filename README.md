# Vue and Matomo Form Analytics Playground

This project demonstrates how dynamic form IDs and Matomo Form analytics
interact.

When testing with our own Matomo installation, you'll have to adapt the
tracker url and site id in `public/index.html`.

How to test:

1. Run on localhost with `npm run serve` or generate page with `npm run
   build` and copy generated files from `dist` to a web server.
2. Go to localhost or web server.
3. Choose different form types and submit.

Expected Result: Different forms are created in Matomo: `dynamic-form-a`, `dynamic-form-b` and `dynamic-form-a`. No form named `dynamic-form-unset` shows up.



## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
