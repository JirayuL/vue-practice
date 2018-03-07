# vue-practise by JirayuL
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
