<script>
export default {
  name: 'SortableHandle',
  mounted() {
    this.$el.classList.add('sortable-list-handle');
  },
  render() {
    return this.$slots.default[0];
  },
};
</script>
