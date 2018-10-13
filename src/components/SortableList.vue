<script>
import { Sortable } from '@shopify/draggable';

export default {
  name: 'SortableList',
  mounted() {
    new Sortable(this.$el, {
      draggable: '.sortable-list-item',
      handle: '.sortable-list-handle',
      mirror: {
        constrainDimensions: true,
      },
    });
  },
  render() {
    return this.$slots.default[0];
  },
};
</script>
