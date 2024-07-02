# Javascript

Javascript is a high-level, interpreted, lightweight, multi-paradigm and dynamic weak typing. It is most know as a scripting language for the web, but thanks to the runtime environment node, can algo be used on servers.

## Event loop

The event loop is resposable to execute the code. Collecting and processing events.

Priorities:

- Call stack
- Microtask
- Tasks

```js
console.log(1);
// Blocking operation
// Call stack

queueMicrotask(() => {
  // Non-blocking operation
  // Web api
  // Microtask
  console.log(2);
});

setTimeout(() => {
  // Non-blocking operation
  // Web api
  // Task
  console.log(3);
}, 0);

console.log(4);
// Blocking operation
// Call stack

Promise.resolve(true).then(() => {
  // Non-blocking operation
  // Web api
  // Microtask
  console.log(5);
});

///14253
```

## Multiparadigm

That means that javascript can be used in diferents paradigms of programming, like object-oriented, imperative and declarative (functional).

## Dynamic weak typing

Dynamic typed languages check the types and look for type errors during runtime. and statically typed languages do this in compile time.

Weak typing means that JS has notion of types, but it's relaxed about them, and can treat values somewhat arbitrary. The stronger the typing system is, the stricter the rules are.

!["dynamic static weak strong typing"](./dynamic-static-weak-strong-typing.jpg)

## Promises

A Promise is an _object_ representing the eventual completion or failure of an asynchronous operation.

```js
function successCallback(result) {
  console.log(`Audio file ready at URL: ${result}`);
}

function failureCallback(error) {
  console.error(`Error generating audio file: ${error}`);
}

createAudioFileAsync(audioSettings, successCallback, failureCallback);
```

### async/await

An async function is a `asyncFunction` object. Everytime that a async function is called, returns a new Promise, that can be resolved or rejected.

Asyncs functions always returns a promise.

```js
async function foo() {
  return 1;
}

// Even if is not explicity a promise, it will be wrapped.
function foo() {
  return Promise.resolve(1);
}
```

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

Async javascript that uses callbacks, can generate a lot of code like this:

```js
fs.readdir(source, function (err, files) {
  if (err) {
    console.log("Error finding files: " + err);
  } else {
    files.forEach(function (filename, fileIndex) {
      console.log(filename);
      gm(source + filename).size(function (err, values) {
        if (err) {
          console.log("Error identifying file size: " + err);
        } else {
          console.log(filename + " : " + values);
          aspect = values.width / values.height;
          widths.forEach(
            function (width, widthIndex) {
              height = Math.round(width / aspect);
              console.log(
                "resizing " + filename + "to " + height + "x" + height
              );
              this.resize(width, height).write(
                dest + "w" + width + "_" + filename,
                function (err) {
                  if (err) console.log("Error writing file: " + err);
                }
              );
            }.bind(this)
          );
        }
      });
    });
  }
});
```

The pyramid of `})` at the end, is knowed as **callback hell**.

#### Summary

- Don't nest functions, modularize then
- Use hoisting
- Handle every single error in every one of your callbacks.
- Create reusable functions and place them in a module to reduce the cognitive load required to understand your code.

## Scopes

A scope is a set of variables, objects, and functions that you have access to. There are three types of scopes in JavaScript. Which are Global Scope, Function Scope (Local Scope), and Block Scope.

## Map

Map objects are collections of key-value pairs.
A key in the Map may only occur once; It is unique in the Map's collection.

### Objects vs Maps

They are similar, both uses key and value, retrieve those values, delete keys and detech whether something is stored at a key.

#### Diferences

- Accidental Keys
  - Map does not not container default keys.
  - Object has a prototype
- Security
  - Map is safe to use with user-provided keys and values
  - Objects can lead to object injection attacks
- Key types
  - Map keys can be anu value
  - Objects keys must be a String or a Symbol.
- Key Order
  - A map interates entries, keys and values in the order of entry insertion
  - Object are ordered now, the order is complex.
- Size
  - Map size is easily retrived from `size` property
  - In object um neet t transform in a array with `Object.keys()` then get via `length`
- Iteration
  - Map is iterable directly
  - Objects its iterable transformin in array by `Object.keys` or `Objects.entries`
- Performance
  - Maps perform better in frequent additions and removals
  - Objects is not optmized for additions ans removals
- Serialization and parsing
  - Maps has no support for serialization and parsing (needs to build)
  - Objects has native support with `JSON.stringify` or `JSON.parse()`

#### Example

```js
const wrongMap = new Map();
wrongMap["bla"] = "blaa";
wrongMap["bla2"] = "blaaa2";

console.log(wrongMap); // Map { bla: 'blaa', bla2: 'blaaa2' }
```

## Set

Set objects are collections of values. This value in set may only occur once.
It is very useful to create a set of values that are uniques and remove the repetitive values

```js
const a = new Set([1, 2, 3]);
const b = new Map([
  [1, "one"],
  [2, "two"],
  [4, "four"],
]);
console.log(a.union(b)); // Set(4) {1, 2, 3, 4}
```

```js
let set = new Set();
set.add("test");
set.add("test");
set.add("test2");

console.log(set.size); // 2
console.log([...set]); // [ 'test', 'test2' ]
```

## Dynamic function

### Pure function
