# vue-practise by JirayuL
In this summer, I will internship at [Sellsuki Co. Ltd.](http://www.sellsuki.co.th) They use Vue framework as main framework so I have to learn about this framework before I go to internship there.
## Declarative Rendering
The `v-bind` attribute you are seeing is called a **directive**. **Directives** are prefixed with **v-** to indicate that they are special attributes provided by Vue, they apply special reactive behavior to the rendered DOM. Here, it is basically saying “keep this element’s title attribute up-to-date with the message property on the Vue instance.”
```html
<span v-bind:title="message">
    Hover your mouse over me for a few seconds
    to see my dynamically bound title!
</span>
```
```JavaScript
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: 'You loaded this page on ' + new Date().toLocaleString()
  }
})
```
## Conditionals and Loops
```html
<div id="app-3">
  <span v-if="seen">Now you see me</span>
</div>
```
```JavaScript
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```
You can change make "Now you see me" disappear by type `app3.seen = false` in the console.

The `v-for` directive can be used for displaying a list of items using the data from an Array:
```html
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```
```JavaScript
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
})
```
## Handling User Input
To let users interact with your app, we can use the `v-on` directive to attach event listeners that invoke methods on our Vue instances:
```html
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>
```
```JavaScript
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'Hello Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```
Vue also provides the v-model directive that makes two-way binding between form input and app state a breeze:
```html
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```
```JavaScript
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
```
## Creating a Vue Instance
Every Vue application starts by creating a new **Vue instance** with the `Vue` function:
```JavaScript
var vm = new Vue({
  // options
})
```
## Data and Methods
When a Vue instance is created, it adds all the properties found in its data object to Vue’s reactivity system. When the values of those properties change, the view will “react”, updating to match the new values.
```JavaScript
// Our data object
var data = { a: 1 }

// The object is added to a Vue instance
var vm = new Vue({
  data: data
})

// Getting the property on the instance
// returns the one from the original data
vm.a == data.a // => true

// Setting the property on the instance
// also affects the original data
vm.a = 2
data.a // => 2

// ... and vice-versa
data.a = 3
vm.a // => 3
```
When this data changes, the view will re-render. It should be noted that properties in data are only reactive if they existed when the instance was created. That means if you add a new property, like:
```JavaScript
vm.b = 'hi'
```
Then changes to b will not trigger any view updates. If you know you’ll need a property later, but it starts out empty or non-existent, you’ll need to set some initial value. For example:
```JavaScript
data: {
  newTodoText: '',
  visitCount: 0,
  hideCompletedTodos: false,
  todos: [],
  error: null
}
```
The only exception to this being the use of Object.freeze(), which prevents existing properties from being changed, which also means the reactivity system can’t track changes.
```JavaScript
var obj = {
  foo: 'bar'
}

Object.freeze(obj)

new Vue({
  el: '#app',
  data: obj
})
```
```html
<div id="app">
  <p>{{ foo }}</p>
  <!-- this will no longer update `foo`! -->
  <button @click="foo = 'baz'">Change it</button>
</div>
```
In addition to data properties, Vue instances expose a number of useful instance properties and methods. These are prefixed with `$` to differentiate them from user-defined properties. For example:
```JavaScript
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})

vm.$data === data // => true
vm.$el === document.getElementById('example') // => true

// $watch is an instance method
vm.$watch('a', function (newValue, oldValue) {
  // This callback will be called when `vm.a` changes
})
```
## Instance Lifecycle Hooks
Each Vue instance goes through a series of initialization steps when it’s created - for example, it needs to set up data observation, compile the template, mount the instance to the DOM, and update the DOM when data changes. Along the way, it also runs functions called **lifecycle hooks**, giving users the opportunity to add their own code at specific stages.

For example, the created hook can be used to run code after an instance is created:
```JavaScript
new Vue({
  data: {
    a: 1
  },
  created: function () {
    // `this` points to the vm instance
    console.log('a is: ' + this.a)
  }
})
// => "a is: 1"
```
## Lifecycle Diagram
![alt text](https://vuejs.org/images/lifecycle.png "Lifecycle Diagram")

### Reference
https://vuejs.org/v2/guide/index.html
