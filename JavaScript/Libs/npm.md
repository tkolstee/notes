`npm init` uses prompts and generates a generic package.json file.
`npm install packagename` installs package and adds to json file.
`npm install` installs deps already listed in json file.


File package.json defines dependencies:
```json
{
  "name": "my-vue-app",
  "version": "0.1.0",
  "dependencies": {
    "Datepicker.js": "^0.1.1",
    "validator": "^13.7.0",
    "vue": "^3.2.45",
    "core-js": "^3.26.1",
    "@vue/cli-service": "^5.0.8",
    "@vue/compiler-sfc": "^3.2.45",
    "express": "^4.18.2",
    "mongodb": "^4.12.1",
    "jest": "^29.3.1",
    "supertest": "^6.3.3"
  },
  "scripts": {
    "serve": "vue-cli-service.js serve"
  }
}
```
`name` and `version` define metadata about the app itself.
`dependencies` tells `npm install` what to install
- `^` means version or greater minor number (1.2.x -> 1.3.x)
- ~ means version or greater release number (1.2.3 -> 1.2.4)
`scripts` is a shortcut that can be used to run common shell commands
- `npm run serve` is an alias for `vue-cli-service.js serve`


Split test/dev libs from prod libs:
```JSON
  "dependencies": {
    "Datepicker.js": "^0.1.1",
    "validator": "^13.7.0",
    "vue": "^3.2.45",
    "core-js": "^3.26.1",
    "express": "^4.18.2",
    "mongodb": "^4.12.1",
  },
  "devDependencies": {
    "@vue/compiler-sfc": "^3.2.45",
    "@vue/cli-service": "^5.0.8",
    "jest": "^29.3.1",
    "supertest": "^6.3.3"
  }
```

`npm install --omit=dev` Installs only prod deps

## Packaging Apps

Add unnecessary files to `.npmignore`
`npm pack`

