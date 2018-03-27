# Class and Style Bindings
A common need for data binding is manipulating an element’s class list and its inline styles. Since they are both attributes, we can use `v-bind` to handle them: we only need to calculate a final string with our expressions. However, meddling with string concatenation is annoying and error-prone. For this reason, Vue provides special enhancements when `v-bind` is used with `class` and `style`. In addition to strings, the expressions can also evaluate to objects or arrays.
## Binding HTML Classes
### Object Syntax
We can pass an object to `v-bind:class` to dynamically toggle classes:
```HTML
<div v-bind:class="{ active: isActive }"></div>
```
The above syntax means the presence of the `active` class will be determined by the **truthiness** of the data property `isActive`.

You can have multiple classes toggled by having more fields in the object. In addition, the `v-bind:class` directive can also co-exist with the plain `class` attribute. So given the following template:
```HTML
<div class="static"
     v-bind:class="{ active: isActive, 'text-danger': hasError }">
</div>
```
And the following data:
```JavaScript
data: {
  isActive: true,
  hasError: false
}
```
It will render:
```HTML
<div class="static active"></div>
```
When `isActive` or `hasError` changes, the class list will be updated accordingly. For example, if `hasError` becomes `true`, the class list will become `"static active text-danger"`.

The bound object doesn’t have to be inline:
```HTML
<div v-bind:class="classObject"></div>
```
```JavaScript
data: {
  classObject: {
    active: true,
    'text-danger': false
  }
}
```
This will render the same result. We can also bind to a **computed property** that returns an object. This is a common and powerful pattern:
```HTML
<div v-bind:class="classObject"></div>
```
```JavaScript
data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
```
