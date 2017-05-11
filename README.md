<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [NODE-Cheat-Sheet](#node-cheat-sheet)
  - [When to use Node.js](#when-to-use-nodejs)
  - [When NOT to use Node.js](#when-not-to-use-nodejs)
  - [Always be non-blocking](#always-be-non-blocking)
  - [Some of the most popular npm modules](#some-of-the-most-popular-npm-modules)
  - [SQL and node](#sql-and-node)
  - [Links](#links)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# NODE-Cheat-Sheet
Hopefully best practices in Node.js.

## When to use Node.js
API's or something that consists of small chunks of work per request which is non-blocking.

If it should act as a webserver, better use Ngingx or Apache for serving the files and Node.js just for API calls etc.

## When NOT to use Node.js
When heavy work has to be done. Node.js is a single thread which handels ALL requests. If one (or more) request creates much CPU work or something that blocks, ALL other requests are blocked to!

If node has to be used at all, outsource the work and pass the result back to node.

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

## Some of the most popular npm modules
`express` — Express.js, a Sinatra-inspired web development framework for Node.js, and the de-facto standard for the majority of Node.js applications out there today.

`hapi` — a very modular and simple to use configuration-centric framework for building web and services applications

`connect` — Connect is an extensible HTTP server framework for Node.js, providing a collection of high performance “plugins” known as middleware; serves as a base foundation for Express.

`socket.io` and sockjs — Server-side component of the two most common websockets components out there today.

`pug` (formerly Jade) — One of the popular templating engines, inspired by HAML, a default in Express.js.

`mongodb` and `mongojs` — MongoDB wrappers to provide the API for MongoDB object databases in Node.js.

`redis` — Redis client library.

`lodash` (underscore, lazy.js) — The JavaScript utility belt. Underscore initiated the game, but got overthrown by one of its two counterparts, mainly due to better performance and modular implementation.

`forever` — Probably the most common utility for ensuring that a given node script runs continuously. Keeps your Node.js process up in production in the face of any unexpected failures.

`bluebird` — A full featured Promises/A+ implementation with exceptionally good performance

`moment` — A lightweight JavaScript date library for parsing, validating, manipulating, and formatting dates.

## SQL and node
`sequelize` - An easy-to-use multi SQL dialect ORM for Node.js (http://www.sequelizejs.com)

## Links
https://medium.com/the-node-js-collection/why-the-hell-would-you-use-node-js-4b053b94ab8e
