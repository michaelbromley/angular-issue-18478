# ngc Nested Config Issue

This is a reproduction of https://github.com/angular/angular/issues/18478

In the latest stable Angular, 4.4.6, ngc does not work as expected when the `tsconfig.json` file is not in the root.

### Setup

1. Clone this repo
2. `npm install`
3. `npm run ngc-nested`

### Expected

ngc should output the following files to the `./build` folder:

* test-flat.d.ts
* test-flat.js
* test-flat.metadata.json
* test.d.ts
* test.js

### Actual

ngc only outputs the following files:

* test.d.ts
* test.js

### Notes

* Running `npm run ngc-root`, which uses the root tsconfig.json file results in the expected output. 
* Downgrading the Angular versions in package.json to `4.0.2` and then running `npm run ngc-nested` again will result in the correct output. Therefore this is a regression introduced somewhere between 4.0.2 and 4.4.6.