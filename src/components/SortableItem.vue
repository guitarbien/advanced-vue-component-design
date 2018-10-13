<script>
export default {
  name: 'SortableItem',
  mounted() {
    this.$el.classList.add('sortable-list-item');
  },
  render() {
    return this.$slots.default[0];
  },
};
</script>
