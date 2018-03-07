# vue-practise by JirayuL
In this summer, I will internship at [Sellsuki Co. Ltd.](http://www.sellsuki.co.th) They use Vue framework as main framework so I have to learn about this framework before I go to internship there.
## Declarative Rendering
The `v-bind` attribute you are seeing is called a **directive**. **Directives** are prefixed with **v-** to indicate that they are special attributes provided by Vue, and as you may have guessed, they apply special reactive behavior to the rendered DOM. Here, it is basically saying “keep this element’s title attribute up-to-date with the message property on the Vue instance.”
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
### Reference
https://vuejs.org/v2/guide/index.html
