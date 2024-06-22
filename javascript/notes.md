# Javascript

Javascript is a high-level, interpreted, lightweight, multi-paradigm and dynamic weak typing. It is most know as a scripting language for the web, but thanks to the runtime environment node, can algo be used on servers.

## Multiparadigm

## Dynamic weak typing

## Promises

### async/await

## Callback

A callback function is a function passed into another function as an argument, which is then invoked inside to outer function to complete some king of routine or action.

```js
// Example of sync callback
function greeting(name) {
  alert("Hello " + name);
}

function processUserInput(callback) {
  var name = prompt("Please insert your name.");
  callback(name);
}

processUserInput(greeting);
```

callbacks are normally used to execute after a async operation is finished. A good example of callback functions executed inside a scope is `.then()`

### Callback hell

## Map

## Set
