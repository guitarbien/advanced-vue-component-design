若是資料本身存在於 component 內，但想讓外部自由做有限的調整，則可將 property 以 function 傳入

props 單純傳入資料

```vue
<!--app.vue-->
<contact-list :pseudo-slot="'Hello' + ' World'"></contact-list>

<!--component-->
{{ pseudoSlot }}
```

改為傳入 arrow function

```vue
<!--app.vue-->
<contact-list :pseudo-slot="() => 'Hello' + ' World'"></contact-list>

<!--component-->
{{ pseudoSlot() }}
```

在 component 內將資料傳入 props 的 function，讓外部決定資料格式

```vue
<!--app.vue-->
<contact-list :pseudo-slot="(contact) => contact.first.name"></contact-list>

<!--component-->
{{ pseudoSlot(contact) }}
```

closure 內也可以傳入物件

```vue
<!--app.vue-->
<contact-list :pseudo-slot="(props) => props.contact.first.name"></contact-list>

<!--component-->
{{ pseudoSlot({ contact: contact }) }}
```

---

使用 [scoped slot](https://vuejs.org/v2/guide/components-slots.html#Scoped-Slots) 做到同樣效果

```vue
<!--app.vue-->
<contact-list>
    <template slot-scope="props">
      {{ props.contact.name.first }}
    </template>
</contact-list>

<!--component-->
<slot :contact="contact"></slot>
```

若已有 DOM 則不需使用 <template>

```vue
<!--app.vue-->
<contact-list>
    <a slot-scope="props" :href="`/contacts/${props.contact.id}`">
      {{ props.contact.name.first }}
    </a>
</contact-list>

<!--component-->
<slot :contact="contact"></slot>
```

也可將 ES2015 [Object Destructing](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#Object_destructuring) 套用進來 

```vue
<!--app.vue-->
<contact-list>
    <a slot-scope="{ contact }" :href="`/contacts/${contact.id}`">
      {{ contact.name.first }}
    </a>
</contact-list>

<!--component-->
<slot :contact="contact"></slot>
```

---

__slot__ 就是 value， __scoped slot__ 就是 function
