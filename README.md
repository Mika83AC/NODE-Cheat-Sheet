<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [NODE-Cheat-Sheet](#node-cheat-sheet)
  - [When to use Node.js](#when-to-use-nodejs)
  - [When NOT to use Node.js](#when-not-to-use-nodejs)
  - [Always be non-blocking](#always-be-non-blocking)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# NODE-Cheat-Sheet
Hopefully best practices in Node.js.

## When to use Node.js
API's or something that consists of small chunks of work which are non-blocking.

## When NOT to use Node.js
When heavy work has to be done. Node.js is a single thread which handels ALL requests. If one (or more) request creates much CPU work or something that blocks, ALL other requests are blocked to!

## Always be non-blocking
Blocking because synchronous:
```
const fs = require('fs');
const data = fs.readFileSync('/file.md'); // blocks here until file is read
```

Here the non-blocking equivalent because asynchronous:
```
const fs = require('fs');
fs.readFile('/file.md', (err, data) => {
   if (err) throw err;
});
```
