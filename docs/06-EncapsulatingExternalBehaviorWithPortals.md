以 modal component 為例

```vue
<div style="opacity: .5">
  <announcement-modal></announcement-modal>
</div>
```

`announcement-modal` 放在 `<div>` 內基本上沒有問題，理想上也該如此，讓 components 之間高內聚。不過若該 `<div>` 有自己的 style，且不希望此 style 套用到 component 上，則需要做些設計來達成。

Use the portal pattern to avoid leaking implementation details to other components and cause unnecessary coupling.

[`portal-vue`](https://linusborg.github.io/portal-vue/#/) : 

> A Portal Component for Vuejs, to render DOM outside of a component, anywhere in the document.

`Vue.use(PortalVue);`

[https://vuejs.org/v2/api/#Vue-use](https://vuejs.org/v2/api/#Vue-use)

---

[JavaScript Template Literals](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Template_literals)

`string text ${expression} string text`

