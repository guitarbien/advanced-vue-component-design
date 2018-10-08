```vue
<div v-model="searchText"></div>
```

equals

```vue
<div v-bind:value="searchText" v-on:input="searchText = $event.target.value"></div>
```

equals

```vue
<div :value="searchText" :input="searchText = $event.target.value"></div>
```

You can use `v-model` inside a component but you still emit a event to tell the consumer outside to handle the value.

透過 scoped slot 可以讓外部自行決定要如何 render，但暴露過多細節會讓職責交待不清：

```vue
<div slot-scope="inputValue, onInput, handleBackspace, addTag">
    <input :value="inputValue"
           @input="onInput"
           @keydown.backspace="handleBackspace"
           @keydown.enter.prevent="addTag"
    >
</div>
```

---

AND,

```vue
<input :value="inputValue">
```

equals

```vue
<input v-bind:value="inputValue">
```

equals

```vue
<input v-bind="{ value: inputValue}">
```

[使用 `v-bind` binding 整個物件屬性](https://vuejs.org/v2/api/#v-bind)

```vue
<input v-bind="{ value: inputValue, foo: bar, aaa, bbb}">
```

也可把由 component 提供整個 object 來讓外部直接 binding

---

使用 arrow function 要回傳物件時，要用 `()` 包起

[Returning Object Literals from Arrow Functions in JavaScript](https://blog.mariusschulz.com/2015/06/09/returning-object-literals-from-arrow-functions-in-javascript)
