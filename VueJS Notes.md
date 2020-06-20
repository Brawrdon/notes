# Vue.js Notes

## Introduction

### Directives

- Vue attributes are called **directives**.
- `v-` p(ref)ix define Vue attributes.
- They apply reactive behaviour to the rendered DOM.
- Can define text, attributes and structure of DOM.
  
- `v-for` works the same as a foreach loop in C#.
- `v-on` is used to attach event listeners.
- `v-model` can be used to create a two way binding between the app's state and a user input.

### Components

> A component is essentially a Vue instance with pre-defined options.

- You can define a component like so:
  
```js
// Define a new component called todo-item
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})

var app = new Vue(...)
```

- You can pass data into a component with `prop`.
  
```js
Vue.component('todo-item', {
  // The todo-item component now accepts a
  // "prop", which is like a custom attribute.
  // This prop is called todo.
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})

```

### Quotes

> The data and the DOM are now linked, and everything is now reactive.
 
> A Vue app attaches itself to a single DOM element (#app in our case) then fully controls it.

>  Vue also provides a powerful transition effect system that can automatically apply transition effects when elements are inserted/updated/removed by Vue.

> Note that in this method we update the state of our app without touching the DOM - all DOM manipulations are handled by Vue, and the code you write is focused on the underlying logic.

## The Vue Instance

### Data and Methods

- It makes a tree of components from the root element.
- When an instance is created, all the properties found in the data object are added to the reactivity system. The view "reacts" when values of these properties change.
  - Setting the property on the instance also affects the original data and vise versa.
- Properties in data are only reactive if they existed when the instance was created.
- You'll need to set a property you expect to use later with some initial value.
- There are also instance properties and methods defined by Vue which can be accessed via `$`.

### Instance Lifecycle Hooks

- **Lifecycle hooks** let you run functions during different stages of intialisation.
- Lifecycle hooks are called with their this context pointing to the Vue instance invoking it.
> Don’t use arrow functions on an options property or callback!

### Quotes

> Just know that all Vue components are also Vue instances, and so accept the same options object (except for a few root-specific options).

> Object.freeze(), which prevents existing properties from being changed, which also means the reactivity system can’t track changes.

## Template Syntax

### Interpolations [(ref)](https://vuejs.org/v2/guide/syntax.html#Interpolations)

- The most basic form of data binding is text interpolation using the “Mustache” syntax.
- `v-html` is required to output HTML since `{{ }}` outputs plain text, e.g. `<p>Using v-html directive: <span v-html="rawHtml"></span></p>`.
  - The contents of the span will be replaced with the value of the rawHtml property, interpreted as plain HTML - data bindings are ignored.
- Mustaches **cannot** be inside HTML attributes, use `v-bind` instead for this.
- Boolean attributes won't work just by existing, they need a value. [(ref)](https://vuejs.org/v2/guide/syntax.html#Attributes)
- Expressions will be evaluated as JavaScript in the data scope of the owner Vue instance.
- They can only contain single line expressions, so no regular if statements for example.

### Directives [(ref)](https://vuejs.org/v2/guide/syntax.html#Using-JavaScript-Expressions)

> Directive attribute values are expected to be a single JavaScript expression.

> A directive’s job is to reactively apply side effects to the DOM when the value of its expression changes.

- Arguments can be included by using a colon after directives name, like with `v-bind:data` with `data` being the argument.
- Dynamic arguments are a thing, think back to JavaScript notes on how and why this works!
- Dynamic arguments will evaluate to a string with the exception of null which removes the binding all together.
- Dynamic argument expressions are limited to valid HTML syntax, i.e they can't have speech marks in them.
- Modifiers exist to tell a directive to be bound in a special way. [(ref)](https://vuejs.org/v2/guide/syntax.html#Using-JavaScript-Expressions)

### Shorthands [(ref)](https://vuejs.org/v2/guide/syntax.html#Using-JavaScript-Expressions)

## Computed Properties and Watchers [(ref)](https://vuejs.org/v2/guide/computed.html)

### Computed Properties

- These should be used for complex logic and are a part of the component instance.

```js
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // a computed getter
    reversedMessage: function () {
      // `this` points to the vm instance
      return this.message.split('').reverse().join('')
    }
  }
})
```

- Computed properties are cached based on their reactive dependencies. That means if the dependencies doesn't change, the computed property is returned instantly. This can be seen when using `Date.now()` as a computed property.
- Functions will always run the function whenever a re-render happens.
- Computed properties are read only by default, but setters can be created. Here the dependencies can be updated.

### Watchers [(ref)](https://vuejs.org/v2/guide/computed.html#Watchers)

- More generic computer properties that let you do more advanced things?

## Class and Style Bindings [(ref)](https://vuejs.org/v2/guide/class-and-style.html)

### Binding HTML Classes [(ref)](https://vuejs.org/v2/guide/class-and-style.html#Binding-HTML-Classes)

- `v-bind:class` can be passed an object.
  - `v-bind:class="{ active: isActive }"`, this doesn't use double mustaches as it's referencing a JavaScript object.
  - The active class is only rendered if the `isActive` property has a value of true.
- `v-bind:class` can exists at the same time as the standard html `class` tag.
- Bound objects don't have to be inline, you can reference the data property which contains an object.
- You can also bind a computed property, which is common and really good apparently.
- `v-bind:class` also accepts arrays. ternary operators can be used in arrays, as well as including object syntax, e.g. `<div v-bind:class="[{ active: isActive }, errorClass]"></div>`

## Component Basics [(ref)](https://vuejs.org/v2/guide/components.html)

- Components' data option has to be a function, this way every instance carries an separate copy of the data.
- Components can be global or local.
  - `Vue.component` registers a global component.
- I'm probably gonna mostly use single file components... [(ref)](https://vuejs.org/v2/guide/single-file-components.html)