**Run tests**

Tests are executed e.g. using `yarn test`, which mean run the corresponding script in `package.json` of the same folder.

    {
      ...
      "scripts": {
        ...
        "test": "NODE_ENV=testing TESTING=true mocha \"test/**/*.js\" \"src/**/*-test.js\" \"tools/**/*-test.js\"",



**Specify a test to run**

Use `only`

    describe('api', _ => {
      // ...
    })

becomes

    describe.only('api', _ => {
      // ...
    })
