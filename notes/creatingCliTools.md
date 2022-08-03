When invoking a CLI tool with Node, the
process.argv contains [1] the absolute path to the
node binary [2] the absolute path to the script that node is
executing and [3...] all of the separate string values
typed after the name of the tool being used.

Running this in the terminal `$ my-cool-tool --name Hannah --age 2 yolo howdy`
would produce something similar to these values:

```
nodePath === "/Users/<USER_NAME>/.nvm/versions/node/<VERSION>/bin/node"
programPath === "/Users/<USER_NAME>/code/foo/node_modules/bar/bin.js"
inputs === [ '--name', 'Hannah', '--age', '2', 'yolo', 'howdy' ]
```

Minimalist takes process.argv and returns us an object of the named
inputs (options) in object form, and a "_" property
on the object for all of the unnamed string inputs.

```js
const minimalist = require('minimalist')
const result = minimalist(process.argv)
// result === { _: [ 'yolo', 'howdy' ], name: 'Hannah', age: 2 }
```
