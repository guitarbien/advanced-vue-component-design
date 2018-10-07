Using render function & scoped slots can build components that don't contain HTML, such like a generic FetchJson component.

This component doesn't have `<template>`, and its render function just returning a `VNode` from `this.$scopedSlot.default()`, not from the `createElement()`.

[Object destructing can also reassign variable name](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#Assigning_to_new_variable_names)
