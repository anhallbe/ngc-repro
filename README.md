# Reproducing strange ngc behavior
1. Run `npm test` (or `./node_modules/.bin/ngc -w`)
2. Notice contents of app.ngsummary.js:
```javascript
    var i4 = require("./node_modules/@angular/common/http/http.ngsummary");
```
3. Save app.ts, which should cause ngc to re-compile
4. Notice contents of app.ngsummary.js again:
```javascript
    var i4 = require("./node_modules/@angular/common/http.ngsummary");
```

The file `node_modules/@angular/common/http.ngsummary` does not exist:
```
$ ls node_modules/@angular/common
bundles      common.metadata.json  esm5      fesm5  http.d.ts           index.d.ts  package.json     README.md  testing       testing.metadata.json
common.d.ts  esm2015               fesm2015  http   http.metadata.json  locales     public_api.d.ts  src        testing.d.ts
```