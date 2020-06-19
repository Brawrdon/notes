# JS Course Notes

## Key Principles

- Arrays are not confined to one type.
- Assign a variable with `var` or `let`
  - We shouldn't be using `var` anymore (as of ES6)!
  - `var` has global scope whilst `let` has block scope.
- Constants are set with `const`.
  - You can't reassign the entire variable, but you can reassign properties inside an object.
- A way to organise variables that you know are going to be used is to declare them at the top of the file. Just a standard.
- **Coercion:** JS is a dynamically typed language, so it will figure out what you're trying to do.
- Everything in JavaScript is an object.

## The Browser

- The `window` object in the browser houses all the objects we can access.
- Calling `document` directly is the same as saying `window.document`, the window can be omitted.

## Types

- `undefined`: variable has been created by no value has been assigned.
- `null`: null means there's no value.
- `NaN`: not a number.
- `typeof()` can be used to find a value's type.

### Objects

- Created by curly braces and can contain properties.

```javascript
const user = {
    name: 'Brandon',
    username: 'Brawrdon'
};
```

- You can access properties with square brackets, e.g. `person['name']`.
  - This is useful if you want to access a property via a value stored in a variable.
  
```javascript
const user = {
    name: 'Brandon',
    username: 'Brawrdon'
};

const propertyToLookFor = 'name';
console.log(user.name); // Prints out the value within the name property
console.log(user[propertyToLookFor]); // Prints out the value within the name property
console.log(user.propertyToLookFor); // Results in undefined because the property 'propertyToLookFor' does not exist
```

- Functions are defined within properties. A function within a property is called a method.
  - `this` keyword refers to the current object.

```javascript
const user = {
    name: 'Brandon',
    username: 'Brawrdon'
    talk: function (speach) {
      return `${this.name} says ${speach}`;
    }
};
```

## Operators

- `+` can be used to concatenate strings.
- Adding a string to a number results in concatenation.
  - Coercion evaluates the number as a string.

## Comparisons

- `==` comparison with strings is case sensitive.
- `==` allows for coercion.
  - numbers compared to strings will convert the number into a string to evaluate it.
- `===` checks that the types are the same as well as being equal, basically saying don't allow coercion.
  - `!=` allows coercion, `!==` doesn't allow coercion etc.
- `Boolean(x)` lets us check if a value is true or not (truthy / falsey).
  - Empty objects and arrays will evaluate to `true`.
- Equality, of any kind, for identical arrays and objects results in false, e.g. `[1,2,3] == [1,2,3] -> false`.
  - JS treats each value as its own object, comparing its referencing point.

## Loops

- `.forEach(function)` is a method for the `Array` object. It calls the function argument once for each element in an array, in order.

## Functions

- defined by `function name(arguments)`.
- Functions in JS accept defaults.
- You don't need to specific the return type.
- Functions can be stored in variables through anonymous functions.

```js
const squared = function(a) {
  return a * a;
}
```

- ES6 array functions can be used to defined anonymous functions.

```js
const squared = (a) => {
  return a * a;
}
```

- Functions are hoisted (brought to the top of the page) when defined, but not when assigned to variables.



## Event Listeners

- The DOM emits events, such as an item has been click. Functions listen to these events and activate when needed.
  - I personally prefer this way than using HTML attributes.
  - Apparently assigning method properties directly in JavaScript allows you to use the `this` keyword.
  - The issue with this method is that only one function can be assigned to an event, using an event listener (via `addEventListener`) fixes this though.

```js
// Just a reference to a function is used with event
// propeties. Not "loose" code. And, because the function
// is actually being stored with the DOM element, this binding
// works as expected.
document.querySelector("input").onclick = foo;

function foo(){
  // This function is invoked by clicking the HTML input element
  // so, we may reasonably expect that "this" would reference that
  // element. But, as you'll see, it doesn't.
  alert("You clicked the " + this.nodeName + " element.");
}
```
  
## Cool Tricks

- Group specific outputs neatly in the console:

```js
console.group('Title')
    console.log('Hey');
    console.log('Hey Again');
console.groupEnd();
```

- Variables can be written directly inside of strings (template string):

```js
let ouput = `${person.name} is a cool name`;
```
