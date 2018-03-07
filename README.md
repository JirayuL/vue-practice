# vue-practise by JirayuL
## Declarative Rendering
The v-bind attribute you are seeing is called a **directive**. **Directives** are prefixed with **v-** to indicate that they are special attributes provided by Vue, and as you may have guessed, they apply special reactive behavior to the rendered DOM. Here, it is basically saying “keep this element’s title attribute up-to-date with the message property on the Vue instance.”
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
