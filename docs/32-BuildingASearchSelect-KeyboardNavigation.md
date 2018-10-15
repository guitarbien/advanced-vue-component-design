在 `v-for` 內的 dom 使用 `ref`，vue 並不保證 `$refs` 取得的 elements 順序和 `v-for` 一致。

可在 `v-for` 的上一層物件上指定 `ref`，並使用 `this.$refs.xxx.children[index]` 來取得指定的 child element，詳見 [ParentNode.children](https://developer.mozilla.org/zh-TW/docs/Web/API/ParentNode/children)

使用 [Element.scrollIntoView()](https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollIntoView) 讓 scrollbar 捲到該元素的位置，可提供參數 `{ block: 'nearest' }` 讓 scrollbar 在有需要時才做滑動
