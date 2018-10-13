<script>
import { Sortable } from '@shopify/draggable';

export default {
  name: 'SortableList',
  provide() {
    return {
      sortableListItemClass: 'sortable-list-item',
      sortableListHandleClass: 'sortable-list-handle',
    };
  },
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
