### How does `v-model` really work under the hood ?

A `v-model` is a shortcut for 2 different bindings on the input.

```vue
<input :value="email" @input="email = $event.target.value">
```

The `$event.target` is the input itself.

> Although a bit magical, v-model is essentially syntax sugar for updating data on user input events, plus special care for some edge cases.
-- https://vuejs.org/v2/guide/forms.html

You pass a prop into a component, and the component wants to tell you what happened, it fires a event back, and parent can make decision about what to do. 

The `props` is a immutable value.

[Using `model` in components can customize the prop and event names.](https://vuejs.org/v2/api/#model)
